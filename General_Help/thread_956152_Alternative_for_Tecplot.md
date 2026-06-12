---
title: "Alternative for Tecplot"
date: 2008-10-22
forum: General Help
---

### Post by subjugater on 2008-10-22
Hi, folks,

I am wondering if there is any free software in Linux can do the same job as Tecplot, such as MAKING PLOTS and MAKING MOVIES/ANIMATIONS?

BTW, some guys may argue that by referring to GNUplot. But I am not happy with GNUplot. 'Coz it is kinda old-fashioned. The graphs are not as neat as those made by Tecplot. It can not make a movie as far as I know.

Perhaps the worst is that I am not rich enough to afford Tecplot. T_T

---

### Post by JC Cheloven on 2008-10-23
Hi, I don't know tecplot really, and it isn't totally clear to me what you are looking for. I think you mean making plots from scientific data and the like. My tentative answer would be:

- Rplot. Makes "publication quality" graphs from your data. Somehow better than gnuplot.

- matplotlib. If you're used to python, this can do the job.

- octave. Have you considered it? It's almost a mathlab clone, perhaps it can suit your needs.


As for the films: I don't know if you want a general editor for videos (in such case cinelerra, pitivi, avidemux ... would do), or something different, as making a movie from your screen. In such case you could try something as deskscribe, pyvnc2swf, recordmydesktop, or perhaps wink. And for animations blender is gerat. Most of them are in the repositories. 

Hope this helps.
JC

---

### Post by subjugater on 2009-05-13
> **JC Cheloven said:**
> Hi, I don't know tecplot really, and it isn't totally clear to me what you are looking for. I think you mean making plots from scientific data and the like. My tentative answer would be:

- Rplot. Makes "publication quality" graphs from your data. Somehow better than gnuplot.

- matplotlib. If you're used to python, this can do the job.

- octave. Have you considered it? It's almost a mathlab clone, perhaps it can suit your needs.


As for the films: I don't know if you want a general editor for videos (in such case cinelerra, pitivi, avidemux ... would do), or something different, as making a movie from your screen. In such case you could try something as deskscribe, pyvnc2swf, recordmydesktop, or perhaps wink. And for animations blender is gerat. Most of them are in the repositories. 

Hope this helps.
JC

Thanks, man. Anybody know how Rplot? Is this plot package a mature enough product? It seems that it can not be captured by synaptic, which perhaps implies it is not well-developed, I guess.

---

### Post by satk1983 on 2010-06-12
I was using Tecplot for about 2 years. The best alternative for tecplot that i've found and use, for a year now, is Paraview. Remember to convert your  data  to .vtk format.

---

### Post by StuartN on 2010-06-12
I use the graphs created by the statistical package R, which is in the repositories. There are samples and documentation at [http://cran.r-project.org/](http://cran.r-project.org/)

---

### Post by Roth NRK on 2010-11-17
I recently had to cut my ties with Tecplot because my new lab doesn't have a license. For complex visualization (such as CFD data) paraview seems to be a nice alternative and for making nice clean plots try GLE. GLE is not in the ubuntu repositories but you can download it from the GLE website which has detailed information on how to install it on linux machines.

---

### Post by amirfluid on 2012-06-17
I tried VisIt ([https://wci.llnl.gov/codes/visit/](https://wci.llnl.gov/codes/visit/)) and found it a good alternative.

---

### Post by oldos2er on 2012-06-17
Please don't bump old threads.

---

