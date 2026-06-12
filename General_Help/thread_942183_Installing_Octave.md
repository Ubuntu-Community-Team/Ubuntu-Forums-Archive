---
title: "Installing Octave"
date: 2008-10-08
forum: General Help
---

### Post by MajinSaha on 2008-10-08
Hello everyone. 
I recently downloaded the source for Octave from [www.gnu.org](www.gnu.org) but have no idea how to compile and make it. In the README it says I need GNU Make for compiling Octave. Where can I get it and how to install it ?
I'm new to Ubuntu. Your answer will be really helpful. Thanks.

---

### Post by eldragon on 2008-10-08
octave is in the repositories, software in the repositories doesnt need compiling..

just open synaptic, and search for it.

or open a terminal and tipe
```

$sudo apt-get install octave

```

and supply your password when prompted.

---

### Post by MajinSaha on 2008-10-12
Thanks, I did as you said. Octave works prettyr well, but graphing function plot is not working. What packages should I install in addition ? Or should I configure Octave somehow ? Here's the example of the output :

octave:23> plot(x,y);
sh: gnuplot: not found
sh: gnuplot: not found
error: compare_versions: version numbers must be a single row
error: evaluating if command near line 78, column 3
error: called from `compare_versions' in file `/usr/share/octave/3.0.0/m/miscellaneous/compare_versions.m'
error: if: error evaluating conditional expression
error: evaluating if command near line 209, column 5
error: evaluating if command near line 206, column 3
error: called from `drawnow:enhanced_term' in file `/usr/share/octave/3.0.0/m/plot/drawnow.m'
error: evaluating assignment expression near line 169, column 14
error: evaluating if command near line 138, column 3
error: called from `drawnow:init_plot_stream' in file `/usr/share/octave/3.0.0/m/plot/drawnow.m'
error: evaluating assignment expression near line 125, column 14
error: evaluating if command near line 117, column 3
error: called from `drawnow:open_gnuplot_stream' in file `/usr/share/octave/3.0.0/m/plot/drawnow.m'
error: evaluating if command near line 78, column 8
error: evaluating if command near line 77, column 6
error: evaluating if command near line 74, column 4
error: evaluating if command near line 72, column 2
error: evaluating for command near line 71, column 7
error: evaluating if command near line 45, column 5
error: called from `drawnow' in file `/usr/share/octave/3.0.0/m/plot/drawnow.m'

---

### Post by Embiggens on 2008-10-16
Hey, if you're still working on this, check this link- you need gnuplot. 

[https://help.ubuntu.com/community/Octave](https://help.ubuntu.com/community/Octave)

---

