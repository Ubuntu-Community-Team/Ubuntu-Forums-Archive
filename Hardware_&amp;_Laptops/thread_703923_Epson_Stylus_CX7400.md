---
title: "Epson Stylus CX7400"
date: 2008-02-21
forum: Hardware &amp; Laptops
---

### Post by computergee on 2008-02-21
I got this printer free from Microcenter with a rebate, but I cannot for the life of me get it to print right from Ubuntu! 

I followed this thread:
[http://ubuntuforums.org/showthread.php?t=631781](http://ubuntuforums.org/showthread.php?t=631781)

But none of their solutions work for me. I've got the 7400 driver installed, I can print a test page and the colors look right, but when I try to print from any other program, I get a stopped status in the jobs menu. When I use some of the built in drivers, it prints, but the colors are messed up. Even in the test page the colors are mixed up. Can any of you guys help me out?

---

### Post by notbitmonk on 2008-03-05
On Ubuntu 7.10, the printer is detected and installed automatically.  The colors are not entirely correct and the images are darker than they should be.  Some programs just won't be able to print using your printer.  I prepared a photo layout using Scribus but was able to print just a page full of black ink.  I also had problems with (I think) Eye of Gnome which sent the job to the printer but there was no printout.  There is basically no difference between the driver provided by Epson (Avasys) and the one provided by CUPS.  I also tried other drivers but the output was the same.  Try uninstalling the printer and having Ubuntu detect it automatically.  Otherwise follow the italian version of the thread within the thread that you already searched.

---

### Post by fredbird67 on 2008-03-27
I'm having a problem with this, too.  My old Epson Stylus CX-5400 bit the dust, so I found another one on Craig's List, which I just bought this morning and just installed.  Everything is detected, and it prints, but I'm getting some strange output when running a test page, as follows:

1) There's no difference between the orange and red portions of the Ubuntu logo.

2) In the red, green, and blue lines, the "10%" segment looks a bit light compared to its neighboring samples.

3) In the green line, it's coming out orangish-yellow until the 100% segment, which is green, like it should be, but nothing in the rest of that line is.

4) In the blue line, it's coming out as various shades of teal, and then at the 100% segment, it's a really light shade of blue

5) In the magenta line, it starts out OK, but the 80% segment is light blue, kinda like the cyan line's 50% segment, and the 100% segment is flat-out purple.

6) In the yellow line, the 70% segment is pure white, and the 80% segment, right next to it, is a bit unsaturated -- it should be more saturated than that.  Also, the 40%, 50%, 60%, 90%, and 100% segments appear to be more or less fully saturated.

7) In the black line, the 90% segment is a bit lighter than the neighboring segments, and in fact, the 60% segment appears to be the darkest segment in that line, and that's not right.

Anyone else getting results similar to this?  Better yet, has anyone found a fix for this?

Thanx in advance,
Fred in St. Louis

---

