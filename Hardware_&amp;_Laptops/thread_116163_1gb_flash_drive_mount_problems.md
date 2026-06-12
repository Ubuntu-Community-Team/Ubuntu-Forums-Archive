---
title: "1gb flash drive mount problems"
date: 2006-01-12
forum: Hardware &amp; Laptops
---

### Post by thefamousnomo on 2006-01-12
hello people! hope you can help (if terminology is off, still learning, please correct me!)

i have 2 flash drives (flashget i think). no problems in any of my windoze boxes and no problems for my 256mb in ubuntu. however the 1gb drive will not mount stating the following in a message box:

 - udi not a mountable device (or similar, im posting from work!)

logged onto the great irc #ubuntu and got some advice, the following:

 - dmesg (resulting message shows an invalid partition type), so,

 - i need to update pmount, and was referred to [http://www.ubuntux.org/node/201](http://www.ubuntux.org/node/201). followed instuctions on page only to find out i had to apt-get a few other packages first. tried to do this but couldnt seem to locate 3 or 4 packages. stopped this, and tried entering synaptic which told me i had a broken package which i couldnt find!

bottom line, after a restart i had screwed the kernel somehow and had to reinstall. any ideas a.why this happened, and b. how to get my big drive to mount?

thanx

---

### Post by tim15856 on 2006-01-12
I'm going to try this out to fix my USB problem. [http://ubuntuforums.org/showthread.php?t=90643&referrerid=40811](http://ubuntuforums.org/showthread.php?t=90643&referrerid=40811) Since he got it to work, maybe he'll be able to help us out if we don't get it to work.

---

### Post by thefamousnomo on 2006-01-30
not having any joy with this issue at all! would still appreciate any help.

thanx

---

### Post by skwid on 2006-01-30
I'm not an expert but have you tried to backup your drive to your windows machine and reformat / initialize the USB Drive?

---

