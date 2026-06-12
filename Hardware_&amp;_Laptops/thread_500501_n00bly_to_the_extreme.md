---
title: "n00bly to the extreme"
date: 2007-07-13
forum: Hardware &amp; Laptops
---

### Post by ErusGuleilmus on 2007-07-13
This is an ultra n00bish question, but I got to ask it. I have an AMD 64 Athlon x2. Does this mean that I should install the 64 version of ubuntu or the regular x 86 types? What are the advantages of the 64 type? And since I’m asking, how do I partition my drive so that it does not interfere with Vista?? Thank you for tolerating my petulant question!

---

### Post by scxtt on 2007-07-14
use 32bit if you have less than 4gb of memory; 64bit is reported to be useful if you're doing a lot of video (and audio?) editing as well ...

there's a million threads about 64 v. 32 ...

---

### Post by ErusGuleilmus on 2007-07-14
Thanks! Fortunately im not big into media editing (Ive got two gigs anyway). As far as the partitioning goes, should I ask else where? Im petrified of messing up vista. It is usefull for running work applications. Thanks again!

---

### Post by merlinus on 2007-07-14
Re: vista.  Clean up by deleting temporary files and anything else not needed, defrag several times, backup vital data, and use its disk manager to shrink the vista partition and create one for installing ubuntu.

-merlin

---

### Post by bdtgp on 2007-07-14
Partitioning for Ubuntu from Vista (I've done it, hence me being here now on Ubuntu):

-In Vista's search box type in Computer Management.  
-Then on the left hand side of the Computer Management Window, click Disk Management.  -Youll see your drive information in the bottom of the main part of the window. 
-Right click on it and go to Shrink Volume...
-Shrink it the amount that you want to install Ubuntu on.  Most people use around 20 or 30 gigs if its not their main OS.  
-Restart your machine and boot from the Ubuntu CD/DVD
-Follow the install steps.

---

### Post by ErusGuleilmus on 2007-07-14
This information is extremely helpfull. Thank you so much.

---

### Post by bdtgp on 2007-07-14
No problem.  Good luck!

---

### Post by ErusGuleilmus on 2007-07-14
I created a separate portion for ubuntu and booted up the live cd. Some text ran through the screen showing it load the pieces of ubuntu. In the middle of this it shows that it failed to load the firmware for an unknown device. It then continues successfully loading other modules and successfully loads the last thing I see, the GNOME environment. My computer then emits a beep and the screen stays blank. The laptop I am trying to install Ubuntu on is a Compaq Presario F500. Thank you for all the help.

---

### Post by volkswagner on 2007-07-14
did you have any issues running the live cd on the laptop?

did you run the check sum to verify the cd?

You could burn a new cd.

---

### Post by volkswagner on 2007-07-14
after resizing i would suggest creating additional partitions as described in many tutorials

a fat32 will read and write on both vista and ubuntu so files can be used on both, a big plus imho.

here are a couple links

[http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html]("http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html")

[http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/]("http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/")

although these are for xp your difference is vista is able to resize which you did.

good luck

---

### Post by ErusGuleilmus on 2007-07-14
Thank you for the advice on the partitioning. As far as booting the live CD goes, no, I did not even get that far. The problem I described above is the problem I have trying to boot the live CD. Thank you for tolerating me, I must be like a mosquito in your ear

---

