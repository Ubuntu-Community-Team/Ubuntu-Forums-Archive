---
title: "x11 term"
date: 2008-10-06
forum: General Help
---

### Post by astrojd on 2008-10-06
I installed gnuplot and the gnuplot-x11 terminal in ubuntu.  However, when I try to set my terminal it does not recognize x11.  On the list of available terminals, x11 does not even appear, but I know it is installed.  Any thoughts on how to get around this?

Cheers

---

### Post by jpkotta on 2008-10-10
Weird.  I'm running 8.04, and the x11 terminal works fine in gnuplot.

```
$ dpkg -l gnuplot*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                     Version                  Description
+++-========================-========================-================================================================
ii  gnuplot                  4.2.2-1                  A command-line driven interactive plotting program
un  gnuplot-doc              <none>                   (no description available)
ii  gnuplot-nox              4.2.2-1                  A command-line driven interactive plotting program
ii  gnuplot-x11              4.2.2-1                  X11-terminal driver for gnuplot

```

I did just build gnuplot from CVS today, because there is a bugfix that affects octave+gnuplot.  See quick instructions at [https://help.ubuntu.com/community/Octave](https://help.ubuntu.com/community/Octave)

---

