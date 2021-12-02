# Simplified solution of Provotorov equation for the pair of nulcei: one strongly coupled, one weakly coupled

## Intial equations

Here I am trying to solve the following equation [(<i>Bosigner-1978</i>)](https://doi.org/10.1103/PhysRevA.18.671)

$$
\begin{gathered}
    \frac{d\beta_1}{dt} = -\frac{1}{\tau_1}\left(\beta_1 - \beta_{SS}\right), \\
    \frac{d\beta_2}{dt} = -\frac{1}{\tau_2}\left(\beta_2 - \beta_{SS}\right), \\
    \frac{d\beta_{SS}}{dt} = -\frac{c_1}{c_{SS}}\frac{1}{\tau_1}\left(\beta_{SS} - \beta_{1}\right)
                             -\frac{c_2}{c_{SS}}\frac{1}{\tau_2}\left(\beta_{SS} - \beta_{2}\right) 
                             -\frac{1}{\tau_{SS}}\left(\beta_{SS}-\beta_L\right),
\end{gathered}
$$

where $\beta_{i}$ - the inverse temperature of i-th nuclei or dipolar reservoir (*alias - SS*), $\tau_{i}$ - characteristic interaction time, and $c_{i}$ - heat capacities. Also, $L$ subscript means thermal environmental reservoir.

## Simplified solution

Through trials and errors with numerical simulation, it was noticed that the behavior of <sup>1</sup>H and DD reservoirs don't depened on the <sup>31</sup>P reservoir. The main idea then is to solve this $2 \times 2$ system (here I rewrite $1 / \tau_{i} = k_{i}$ and $c_1/c_{ss} = \kappa$):
$$
\frac{d\beta_1}{dt} = - k_1 \left(\beta_1 - \beta_{SS}\right),
$$
$$
\frac{d\beta_{SS}}{dt} = - \kappa \cdot k_1 \left(\beta_{SS} - \beta_{1}\right) 
                         - k_{ss} \left(\beta_{SS}-\beta_L\right),
$$

and then one can use the solution $\beta_{ss}(t)$ of previous system to substitute it to the <sup>31</sup>P equation:

$$
\frac{d\beta_2}{dt} = - k_2 \left(\beta_2 - \beta_{SS}(t)\right)
$$
<hr>

The solution of this equations is tedious but quite trivial. Here I present only the final result:
$$
\beta_1(t) = C_1 e^{\lambda_{+}t} 
           + C_2 e^{\lambda_{-}t} 
           + \beta_L,
$$
$$
\beta_{ss}(t) = \frac{k_1 + \lambda_{+}}{k_1} C_1 e^{\lambda_{+}t} 
              + \frac{k_2 + \lambda_{-}}{k_2} C_2 e^{\lambda_{-}t} 
              + \beta_L,
$$
$$
\beta_{2}(t) = C_0 e^{-k_2 t}
                + \frac{k_2}{k_1} \frac{\lambda_{+} + k_1}{\lambda_{+} + k_2} C_1 e^{\lambda_{+}t}
                + \frac{k_2}{k_1} \frac{\lambda_{-} + k_1}{\lambda_{-} + k_2} C_2 e^{\lambda_{-}t} 
                + \beta_L,
$$

where different constatnts are:

$$
\lambda_{\pm} = \frac{1}{2} \left(-(k_1 (1 + \kappa) + k_{ss}) \pm \sqrt{(k_1 (1 + \kappa) + k_{ss})^2 - 4 k_1 k_{ss}} \right)
$$
$$
C_2 = \frac{k_1}{\lambda_{-} - \lambda{+}} \left( \beta_{ss}^0 
                                                 -\beta_{1}^0 \frac{k_1 
                                                 +\lambda_{+}}{k_1} 
                                                 +\beta_L \frac{ \lambda_{+}}{k_1} 
                                                 \right)
   = \frac{k_1}{\lambda_{-} - \lambda{+}} \beta_{ss}^0
   - \frac{k_1 + \lambda_{+}}{\lambda_{-} - \lambda_{+}} \beta_{1}^0
   + \frac{\lambda_{+}}{\lambda_{-} - \lambda{+}} \beta_{L}
$$
$$
C_1 = \beta_{1}^0 - \beta_L - C_2
    = - \frac{k_1}{\lambda_{-} - \lambda{+}} \beta_{ss}^0
    + \frac{k_1 + \lambda_{-}}{\lambda_{-} - \lambda{+}} \beta_{1}^0
    - \frac{\lambda_{-}}{\lambda_{-} - \lambda{+}} \beta_{L}
$$
$$
C_0 = \beta_2^0 - C_1 \frac{k_2}{k_1} \frac{\lambda_{+} + k_1}{\lambda_{+} + k_2} 
                - C_2 \frac{k_2}{k_1} \frac{\lambda_{-} + k_1}{\lambda_{-} + k_2} 
                - \beta_L
$$

*I'm pretty sure these constants may be wrtitten prettier*. One things we may notice is $|\lambda_{-}| > |\lambda_{+}|$, so the minus constant correspond to the faster evolution.

##  $^{31}$P depolarization experiment

One can see later that during <sup>1</sup>H depolarization experiment $\beta_{ss} \rightarrow \beta_L$ very fast in comparison with <sup>31</sup>P evolution. This gives us an oportunity to simplify $\beta_2$ evolution as:

$$
\frac{d\beta_2}{dt} = - k_2 \left(\beta_2 - \beta_{SS}(t)\right) \rightarrow - k_2 \left(\beta_2 - \beta_L\right) 
$$

that leads to

$$
\beta_2(t) = \beta_L - (\beta_L + \beta_2^0) \cdot e^{-k_2 t}
$$

The last formula will be used for <sup>31</sup>P depolarization experiment.