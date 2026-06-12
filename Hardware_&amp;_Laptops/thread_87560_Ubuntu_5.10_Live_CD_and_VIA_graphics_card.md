---
title: "Ubuntu 5.10 Live CD and VIA graphics card"
date: 2005-11-08
forum: Hardware &amp; Laptops
---

### Post by kir on 2005-11-08
When running 5.10 live cd on CNAB 510 (VIA graphics card) the screen is totally garbaged during the boot process, but after the X starts, everything is ok.
I'd like to made an "real" Ububtu installation also, but I can't perform it in completely blind way :(
Please help

Boris

---

### Post by jml on 2005-11-08
Hi, Boris, I've installed several Debian based distros including Ubuntu on laptops with the VIA video chip set and experienced the same problem.  The solution I've found is to not do a default boot of Ubuntu, but after the disc loads, press F1 for other options.  There are several options to choose from, if you are booting the live cd boot with the command live vga=771.  If you are booting the regular install cd boot with the command linux vga=771.  This should allow you to see the installation screens without the tearing artifact a standard install causes.  Hope this helps.

Joe

---

### Post by kir on 2005-11-18
Hello J and thanks for your answer
Unfortunately, I can not proceed the setup with the "vga=771" option - I get a "no kernel vga=771 found" message :(
Should I use some particalar distribution/live version for getting this kernel into image?


Thanks,
Boris

---

### Post by jml on 2005-11-18
I'm afraid you have me stumped on this one.  I've never had that command fail, and I have used it on at least three different laptops.:???: 
At the risk of insulting your intelegence, did you type the command as "linux vga=771"  without the quotes of course.  If you just type "vga=771" at the boot prompt you will get the kernal not found error.  The command requires the name of the kernal prior to the vga=771 option.  Hope this helps.

Joe

---

### Post by kir on 2005-11-20
Yes, thank you, it was my stupid mistake I figured out this evening :0

I'm proceeding to install, hope it will be ok now.

Thank you a lot for your help.

---

### Post by grunion on 2005-11-27
Thank you!  This is JUST the answer I came looking for today!

Now to repartition the new laptop (well, new as of a couple of months ago) and have it "just work".

Thanks again!

---

