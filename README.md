# Wilsonloop.jl [![CI](https://github.com/akio-tomiya/Wilsonloop.jl/actions/workflows/CI.yml/badge.svg)](https://github.com/akio-tomiya/Wilsonloop.jl/actions/workflows/CI.yml)




# What is this?
In the Lattice Quantum chrono dynamics (QCD), the action is constructed so-called Wilson loops in discretized space-time. 
Wilsonloop.jl helps us to treat with the Wilson loops. 

# This is the package for Lattice QCD codes. 

This is used in [Gaugefields.jl](https://github.com/akio-tomiya/Gaugefields.jl) and [LatticeQCD.jl](https://github.com/akio-tomiya/LatticeQCD.jl)


# What this package can do:
- Generating Wilson lines
- Constructing Staples from given Wilson lines
- Constructing derivatives of given Wilson lines

# How to install 

```julia
add https://github.com/akio-tomiya/Wilsonloop.jl
```

# How to use

## Plaquette and its staple
We can easily generate the plaquette. 

```julia
println("plaq")
plaq = make_plaq()
display(plaq)
```
The output is 

```
plaq
1-st loop
L"$U_{1}(n)U_{2}(n+e_{1})U^{\dagger}_{1}(n+e_{2})U^{\dagger}_{2}(n)$"	
2-nd loop
L"$U_{1}(n)U_{3}(n+e_{1})U^{\dagger}_{1}(n+e_{3})U^{\dagger}_{3}(n)$"	
3-rd loop
L"$U_{1}(n)U_{4}(n+e_{1})U^{\dagger}_{1}(n+e_{4})U^{\dagger}_{4}(n)$"	
4-th loop
L"$U_{2}(n)U_{3}(n+e_{2})U^{\dagger}_{2}(n+e_{3})U^{\dagger}_{3}(n)$"	
5-th loop
L"$U_{2}(n)U_{4}(n+e_{2})U^{\dagger}_{2}(n+e_{4})U^{\dagger}_{4}(n)$"	
6-th loop
L"$U_{3}(n)U_{4}(n+e_{3})U^{\dagger}_{3}(n+e_{4})U^{\dagger}_{4}(n)$"
```

The staple of the plaquette is given as 

```julia
    for μ=1:4
        println("μ = $μ")
        staples = make_plaq_staple(μ)
        display(staples)
    end
```

The output is 

```
μ = 1
1-st loop
L"$U_{2}(n+e_{1})U^{\dagger}_{1}(n+e_{2})U^{\dagger}_{2}(n)$"	
2-nd loop
L"$U^{\dagger}_{2}(n+e_{1}-e_{2})U^{\dagger}_{1}(n-e_{2})U_{2}(n-e_{2})$"	
3-rd loop
L"$U_{3}(n+e_{1})U^{\dagger}_{1}(n+e_{3})U^{\dagger}_{3}(n)$"	
4-th loop
L"$U^{\dagger}_{3}(n+e_{1}-e_{3})U^{\dagger}_{1}(n-e_{3})U_{3}(n-e_{3})$"	
5-th loop
L"$U_{4}(n+e_{1})U^{\dagger}_{1}(n+e_{4})U^{\dagger}_{4}(n)$"	
6-th loop
L"$U^{\dagger}_{4}(n+e_{1}-e_{4})U^{\dagger}_{1}(n-e_{4})U_{4}(n-e_{4})$"	
μ = 2
1-st loop
L"$U^{\dagger}_{1}(n-e_{1}+e_{2})U^{\dagger}_{2}(n-e_{1})U_{1}(n-e_{1})$"	
2-nd loop
L"$U_{1}(n+e_{2})U^{\dagger}_{2}(n+e_{1})U^{\dagger}_{1}(n)$"	
3-rd loop
L"$U_{3}(n+e_{2})U^{\dagger}_{2}(n+e_{3})U^{\dagger}_{3}(n)$"	
4-th loop
L"$U^{\dagger}_{3}(n+e_{2}-e_{3})U^{\dagger}_{2}(n-e_{3})U_{3}(n-e_{3})$"	
5-th loop
L"$U_{4}(n+e_{2})U^{\dagger}_{2}(n+e_{4})U^{\dagger}_{4}(n)$"	
6-th loop
L"$U^{\dagger}_{4}(n+e_{2}-e_{4})U^{\dagger}_{2}(n-e_{4})U_{4}(n-e_{4})$"	
μ = 3
1-st loop
L"$U^{\dagger}_{1}(n-e_{1}+e_{3})U^{\dagger}_{3}(n-e_{1})U_{1}(n-e_{1})$"	
2-nd loop
L"$U_{1}(n+e_{3})U^{\dagger}_{3}(n+e_{1})U^{\dagger}_{1}(n)$"	
3-rd loop
L"$U^{\dagger}_{2}(n-e_{2}+e_{3})U^{\dagger}_{3}(n-e_{2})U_{2}(n-e_{2})$"	
4-th loop
L"$U_{2}(n+e_{3})U^{\dagger}_{3}(n+e_{2})U^{\dagger}_{2}(n)$"	
5-th loop
L"$U_{4}(n+e_{3})U^{\dagger}_{3}(n+e_{4})U^{\dagger}_{4}(n)$"	
6-th loop
L"$U^{\dagger}_{4}(n+e_{3}-e_{4})U^{\dagger}_{3}(n-e_{4})U_{4}(n-e_{4})$"	
μ = 4
1-st loop
L"$U^{\dagger}_{1}(n-e_{1}+e_{4})U^{\dagger}_{4}(n-e_{1})U_{1}(n-e_{1})$"	
2-nd loop
L"$U_{1}(n+e_{4})U^{\dagger}_{4}(n+e_{1})U^{\dagger}_{1}(n)$"	
3-rd loop
L"$U^{\dagger}_{2}(n-e_{2}+e_{4})U^{\dagger}_{4}(n-e_{2})U_{2}(n-e_{2})$"	
4-th loop
L"$U_{2}(n+e_{4})U^{\dagger}_{4}(n+e_{2})U^{\dagger}_{2}(n)$"	
5-th loop
L"$U^{\dagger}_{3}(n-e_{3}+e_{4})U^{\dagger}_{4}(n-e_{3})U_{3}(n-e_{3})$"	
6-th loop
L"$U_{3}(n+e_{4})U^{\dagger}_{4}(n+e_{3})U^{\dagger}_{3}(n)$"	
1-st loop
L"$U^{\dagger}_{1}(n-e_{1})U_{4}(n-e_{1})U_{1}(n-e_{1}+e_{4})$"	
2-nd loop
L"$U_{1}(n)U_{4}(n+e_{1})U^{\dagger}_{1}(n+e_{4})$"	
3-rd loop
L"$U^{\dagger}_{2}(n-e_{2})U_{4}(n-e_{2})U_{2}(n-e_{2}+e_{4})$"	
4-th loop
L"$U_{2}(n)U_{4}(n+e_{2})U^{\dagger}_{2}(n+e_{4})$"	
5-th loop
L"$U^{\dagger}_{3}(n-e_{3})U_{4}(n-e_{3})U_{3}(n-e_{3}+e_{4})$"	
6-th loop
L"$U_{3}(n)U_{4}(n+e_{3})U^{\dagger}_{3}(n+e_{4})$"
```

## Input loops
The arbitrary Wilson loop is constructed as 

```julia
loop = [(1,+1),(2,+1),(1,-1),(2,-1)]
println(loop)
w = Wilsonline(loop)
println("P: ")
show(w)
```
Its adjoint is calculated as 

```julia
println("P^+: ")
show(w')
```

Its staple is calculated as 

```julia
println("staple")
for μ=1:4
    println("μ = $μ")
    V1 = make_staple(w,μ)
    V2 = make_staple(w',μ)
    show(V1)
    show(V2)
end
```

## Derivatives
The derivative of the lines $dw/dU_{\mu}$ is calculated as 

```julia
println("derive w")
for μ=1:4
    dU = derive_U(w,μ)
    for i=1:length(dU)
        show(dU[i])
    end
end
```
Note that the derivative is a rank-2 tensor. 

The output is 

```
L"$I  \otimes U_{2}(n+e_{1})U^{\dagger}_{1}(n+e_{2})U^{\dagger}_{2}(n)\delta_{m,n}$"	
L"$U_{1}(n-e_{1}) \otimes U^{\dagger}_{1}(n-e_{1}+e_{2})U^{\dagger}_{2}(n-e_{1})\delta_{m,n+e_{1}}$"
```


The derivatives are usually used for making the smearing of the gauge fields (STOUT smearing can be used in Gaugefields.jl). 

