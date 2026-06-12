---
title: "Octave or Matlab or Scilab"
date: 2008-08-19
forum: General Help
---

### Post by 7raTEYdCql on 2008-08-19
How similar or Octave and Matlab. I mean since i use Ubuntu i would prefer using Octave, but the study material we use always make the reference with matlab. Haven't found any difference yet, but just how similar are the two. Are there many differences in the command language, or are they just the same. The GNU Octave i downloaded from the repos, just seems to initiate a terminal. Isn't there any GUI for Octave.

Anyway this is slightly urgent. Am an engineering srudent and will need to learn Octave because next year there will be immense use of it.

How is Scilab anyway? How close is it to Matlab.

---

### Post by eldragon on 2008-08-19
the terminal is the equivalent to the matlab prompt.

i like it better.

octave is far behind matlab, so i ended up using matlab. gnuplot wasnt as good as the matlab plotter.

its meant to be a replacement (one day). 

ive never used scilab.

you can edit m files with gedit or your editor of choice and run them through the terminal. this felt quite cumbersome too. much nicer the run button in the matlab editor.

matlab can be quite expensive too. and gtk1.0 UGGHH

---

### Post by helmingstay on 2008-09-10
I'm still new at this and searching, but my observations are as such:

1.
Scilab goes against my feel of what a commandline interpreter should do.  It opens its own window, looks terrible, etc.  I used scicos for some time, and it's pretty amazing and totally unique.  Scilab's UI appears to be in the middle of a total rewrite into java?  My verdict is come back in a year unless you're looking for a dynamic systems simulator, in which case use scicos and save often.

2.  Octave - true, it works. Yes, it's free like lunch and free like speech.  It does lack major functionality - ode solvers, for example.  However, octave functionality appears to be greatly improved in the new ubuntu release, intrepid.  

3.  Matlab - the off-the-shelf version lacks core functionality.  You must buy very expensive add-on packs to get decent functionality like proper null handling, making "unofficial" versions popular.  If given the choice, I'd rather use R ( [http://cran.r-project.org/](http://cran.r-project.org/) ).

---

### Post by Vivaldi Gloria on 2008-09-10
A previous discussion:

[http://ubuntuforums.org/showthread.php?t=247049](http://ubuntuforums.org/showthread.php?t=247049)

---

### Post by muteXe on 2008-09-10
These were reviewed in Linux Format magazine about two months ago.  I vaguely remember Scilab getting 9 out of 10.  It even has some features in it that cost you extra to get in matlab (i.e. on top of the the cost of purchasing matlab).

---

### Post by kaspar_silas on 2008-09-10
If you are going to include expensive programs like Matlab you should also include Mathematica. 

I use both at work but prefer Mathematica. This is due to an the ability to work symbolically, an amazing help section and it being much much faster (especially in loops) than Matlab. However Mathematica eats memory like a champion. Plus exporting pretty graphs takes longer than Matlab. 

To be honest the cost means I will never  buy either (I use R and Octave at home), but if I had to buy one I would buy Mathematica.

---

### Post by rraj.be on 2008-09-10
i am too having matlab programs in my DSP lab. . .  i am using octave for ubuntu . . . . 


but i have a dual boot with windows, so that i can use matlab itself. . 

i feel octave is fine for me

---

### Post by kaspar_silas on 2008-09-15
> **rraj.be said:**
> i am too having matlab programs in my DSP lab. . .  i am using octave for ubuntu . . . . 

but i have a dual boot with windows, so that i can use matlab itself. . 

i feel octave is fine for me

I think you can run matlab under wine. For example see [http://www.kerrywong.com/2007/12/01/matlab-7-under-wine/]("http://www.kerrywong.com/2007/12/01/matlab-7-under-wine/")
thou admittedly this might make it even slower.

---

### Post by jpkotta on 2008-10-10
[http://www.gnu.org/software/octave/FAQ.html#MATLAB-compatibility](http://www.gnu.org/software/octave/FAQ.html#MATLAB-compatibility)
> There are still a number of differences between Octave and Matlab, however in general differences between the two are considered as bugs. Octave might consider that the bug is in Matlab and do nothing about it, but generally functionality is almost identical.

Matlab runs on Linux.  In fact, it ran on Unix before Windows existed.  

I find Octave to be a mostly adequate replacement.  If you write your code correctly, it can be run on both Matlab and Octave.  We're using Octave at work for critical calculations.  We have a single Matlab license, but due to the onerous terms and expense of additional licenses, we can't justify using it.

---

### Post by tropicflite on 2008-10-10
I'd just like to put my 2 cents in for wxmaxima.  As I've said in other posts, you'd have to be into some pretty heavy stuff to exceed it's capabilities, plus it works seemlessly with gnuplot, as well as generates latex code for your papers.  I've been quite satisfied with it.

---

### Post by XxX_VLAD_XxX on 2008-11-13
There is also a Mathematica 6.0 version for GNU/LINUX users, I'm yet to try it, I really would like to see some program who takes the Symbolical power of Mathematica, combine with the easy handle of big amounts of data that MATLAB provides. I think a way of doing so is using Excel, 'cause both programs have these outputs

---

