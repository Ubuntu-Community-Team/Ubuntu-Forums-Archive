---
title: "Upgrade to 9.0.4"
date: 2009-10-20
forum: Installation &amp; Upgrades
---

### Post by shazzer on 2009-10-20
I just did a partial upgrade on all but one of my systems and now find that all displays have poor res. Im only getting an option in display preferences to select 800x600 (4:3) and when I try to detect monitor again doesnt let me. Just keeps showing pink  message monitor unknown. Im using EEPC 1000h. Do I need to reinstall my monitor and if so how pls? Ive been using Ubuntu for about a year and love it compared to windows and manage to sort out most practical issues but installation wise, I always prefer to check what Im doing? Any help appreciated.

---

### Post by kvarley on 2009-10-20
Sounds like you need to install your graphics card driver again.

Use envy to install it, you'll have to reboot after install and that should fix it. Only install the driver which has (Recommended) next to it.

> sudo apt-get install envy-ng

Let us know how it goes.

---

### Post by shazzer on 2009-10-20
says couldn't find package envy-ng. I used synaptic package manager and found something for envy-ng core so installed that. Says its to install ATI or NVIDIA driver. When I open Envy from the menu now, it shows me some drivers but all have red crosses with compatabilty and recommendation. none are highlighted as recommended so don't know which one to choose?

---

### Post by kvarley on 2009-10-20
Install the compatable one, choose the one which it says is the best for you.

---

### Post by shazzer on 2009-10-20
Thats the problem there are no recommended drivers. none are recommended they all show red crosses which means none are recommended. Shall I just pick one? Also I have selection of ATI and NVIDIA. Which one should I select as it only allows you to select from one or the other? Sorry.. I know Im being thick but it simply doesn't offer a recommended one?

---

### Post by kvarley on 2009-10-20
It should recommend one. Do you have a graphics card?

What make is your graphics card?

---

### Post by shazzer on 2009-10-21
I don't know where to find out about the graphics card. Where should I look using Ubuntu?

Envy definitely doesn't offer a recommended driver. Don't know whether to use NVIDIA or ATI. Now since the upgrade my panel has even changed layout. Now icons that were on the left such as the drop down menu have relocated to the middle and I don't know how to reset them?  Its very annoying now since everything changed after the upgrade. Can I run using an older version that was previously installed. If so, how do I do that?

---

### Post by shazzer on 2009-10-21
Now im really in a mess. In the absence of any replies to help me with the display fault, I went ahead and installed an ATI driver which now appears is incompatible. My screen is frozen and cant login to my desktop.  How do I sort this out from the start up point? Simple language please as I don't have that much technical knowledge. Need to know what to do urgently as now cant use my netbook!

HELP PLEASE!

---

### Post by raprap30 on 2009-10-21
Do you have any other OS installed in the computer? e.g Windows, OSX, or another functional OS? You should be able to find your graphics card there. And if you said that you upgraded, the older linux kernel should be at the grub menu.

---

### Post by shazzer on 2009-10-21
Tried the older kernel but its still 9.0.4 dont know why I dont have an older version! No other OS. just this one. Need to know how to uninstall 9.0.4 if possible or how to install a display driver for an EEPC 1000h either from the USB or using the recovery menu. Im now really stuck as nothing I try works and I basically cant use my netbook.

Can I get a driver and install using the usb stick? On another thread somebody said how to login using the recovery menu when I get the root prompt but I cant get it to do that and even find the desktop just tells me no such file or directory????

---

### Post by raprap30 on 2009-10-21
Yes, e.g if its a NVIDIA driver i think you can run the file thru command line. I think.

---

### Post by kvarley on 2009-10-21
Look inside the computer and find out what graphics card you have. It will show the brand on the card itself.

---

