---
title: "g77 in Ubuntu 9.04 Jaunty"
date: 2009-06-04
forum: Installation &amp; Upgrades
---

### Post by astropunkin on 2009-06-04
Hi everyone!

I have seen a couple posts about this for 8.10 but I didn't see any concerning 9.04.  If it has already been posted then point me in the direction of the thread.

I have a program that someone else wrote that compiles using g77.  Unfortunately this doesn't appear to be available in 9.04.  gfortran and fort 77 do not work with this code :(  Does anyone know where the source code is for g77.  There was a .deb file for 8.10 but it has the wrong architecture for 9.04.  I have a 64-bit processor and again am running 9.04 Jaunty.  

Thank you for helps!!!! :)

So if you use gfortran and add the option -std=legacy, it built and compiled my program.  Problem solved!!!

---

