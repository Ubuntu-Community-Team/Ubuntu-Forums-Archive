---
title: "Ubuntu studio: every app crashes"
date: 2008-11-09
forum: General Help
---

### Post by Corectanus on 2008-11-09
Hello!
 I have recently installed Ubuntu Studio 8.10 for 64 bit platforms. My PC is an Amd 3800+ X2 with 2 Gb of ram. 
 My problem is the following: Every time I try to browse for(open) a file, in any given program(i.e. open a picture with Gimp), that specific program automatically ends without warning or error exactly in the moment I select to open a certain directory. I thought it was because Nautilus file manager, so I replaced it with Thunar, but that didn't solve anything.
 Does anybody know why this is happening?

---

### Post by Corectanus on 2008-11-10
Also, I can't run the GDM login settings. The program starts but ends immediately. And if I connect my nokia phone to Usb, nothing shows up.
What can I say, the drivers work well and the rest of applications are really nice, but I'm sad because I can't fully use them.

---

### Post by Corectanus on 2008-11-14
I still cannot resolve the main problem and some help would be much appreciated :D

---

### Post by Kevbert on 2008-11-14
Welcome to Ubuntu.
First thing. Have you run memtest ? It should be a boot menu item. Let it run for a couple of passes so we can be sure it's not a memory problem.
Next can you open a terminal (in Ubuntu it's under Applications-Accessories - don't know about studio as I've never tried it). Enter the following
```
sudo apt-get install -f
sudo dpkg --configure -a
```
This will look for and try to repair any damaged packages.
Do you get any error messages when you boot the PC ?

---

### Post by Corectanus on 2008-11-23
Thank you for your help!
I had memtest running for about 2 hours and no errors were found. Then I updated all the packages and also there was no damaged package. I do get a sort of error at boot: "Apperture beyond 4 Gb. Ignoring". It's displayed for a very short time, then the system continues to boot normally.

---

