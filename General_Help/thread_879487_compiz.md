---
title: "compiz"
date: 2008-08-04
forum: General Help
---

### Post by jgordon6633 on 2008-08-04
I have open source Radeon driver, and xserver-xgl installed..

but when i type 'compiz' sans quotes into terminal I get:

Checking for Xgl: not present. 
Found laptop using ati driver. 
aborting and using fallback: /usr/bin/metacity

my goal is to have the avant window manager display - as of now it just disappears into a gray box in the top left corner when i open it. i typed in 'avant-window-manager' into terminal and it said i have to have compiz running. thus I am here...


/by the way if you noticed my other post please ignore - I am a dumbass

---

### Post by armageddon08 on 2008-08-04
Try compiz --replace......

---

### Post by PmDematagoda on 2008-08-04
I think the fault might be because you are using the ati driver, did you try installing the fglrx driver through System>Administration>Hardware Drivers and seeing if that fixes it?

---

### Post by handsomeDave on 2008-08-04
ATI's not a fan of compiz...

Are you running a clean install of hardy?

You have to make sure that your kernel is up to date, or else the ATI drivers won't load properly.
If
```
uname -r
```
gives you 2.6.22 or lower, you're going to need to update your kernel first.

I'd suggest going to here and following method 2
[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide")

---

### Post by jgordon6633 on 2008-08-04
thanks for all the responses - I will try, but i cant use fglrx because my video card is not new enough- that driver was meant for Radeon 9500 and later. I have the 9000.

---

### Post by jgordon6633 on 2008-08-05
ok, i typed in compiz --replace, 

and got:

aborting and using fallback: /usr/bin/metacity 

and my kernel is 6.24.XX so no luck there

---

### Post by armageddon08 on 2008-08-06
Well....try this tutorial and see if it helps:
[http://ubuntuforums.org/showthread.php?t=764633&highlight=compiz+fusion+ATI%2FRadeon]("http://ubuntuforums.org/showthread.php?t=764633&highlight=compiz+fusion+ATI%2FRadeon")

---

