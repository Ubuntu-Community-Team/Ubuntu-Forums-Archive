---
title: "Issues with Radeon HD 3200 Graphics Card"
date: 2009-01-22
forum: Hardware
---

### Post by adamsu on 2009-01-22
Hello all, just a couple of quick questions. I have an HP tx2509 with a Radeon HD 3200 graphics card. (This is a tablet PC.) I have everything I want working including the digitizer, but I have two issues with the graphics card drivers. I would like to have both the ability to rotate the screen and a connection to a VGA projector from the same driver. Right now I can only get the radeon driver to rotate, but it won't connect to the projector. I can get the proprietary fglrx driver to connect to the projector, but it won't rotate the screen. So, here are my questions:

1. Is it possible to rotate the screen (using xrandr or another method) while using the fglrx driver? Can anyone point me to a script or other method to do this?

2. How do you connect to an external monitor/projector while using the radeon driver? Under System>Preferences>Screen Resolution I can see the projector, but pressing function F4 or restarting X will not make the display appear on the projector screen. 

3. (Just out of personal interest) Has anyone found a better OneNote alternative than BasKet, Tomboy notes, or ZOHO notebook? I am running OneNote 2007 now under crossover (wine), but it does not support ink. I would much rather use a native linux or java application, but xournal, gournal, jarnal, basKet, and tomboy notes, while all nice apps, are not the same as OneNote, and ZOHO notebook is really good, but I'd like something installed locally. 

Thanks for any help you can provide for any of these three questions.

---

### Post by Favux on 2009-01-22
Hi adamsu,

It may be there is a new "fglrx" that supports rotation.  I don't know if the TX2z has the same ATI card as you do.  But gurgle on this thread claims rotation:

[http://ubuntuforums.org/showthread.php?t=995885&highlight=tablet+pc]("http://ubuntuforums.org/showthread.php?t=995885&highlight=tablet+pc")

Maybe he'll answer my last questions, but he hasn't answered yet.  Looking at his blog and the link to the latitude HOW TO shows a patch to linuxwacom to get the N-trig digitizer to work.  I don't think this affects rotation.  But looking at the ATI site shows a new Linux Catalyst 8.12.  Maybe there is a new "fglrx" that supports rotation..  I can't tell what's in the repository through Synaptic.  Since I don't have a TX2500 it is hard for me to tell.  You may have to download it through ATI.

---

### Post by adamsu on 2009-02-06
I've discovered the solution! The newest ATI driver, available [here]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/64bit/ati-driver-installer-9-1-x86.x86_64.run"), supports rotation! To install it, just run the script as sudo in a terminal.

The trick to rotation is that it has lots of strange errors if the screen is composited (using compiz). The method I have worked out is to switch from Compiz to Metacity when I need to rotate the screen using the compiz icon (fusion-icon) in the tray, and then switch back to compiz when done rotating. The new driver supports output to projectors just like the old, so my problem is solved. :KS By the way, the rotation scripts I use come from [this page]("http://ubuntuforums.org/showthread.php?t=996830&highlight=intrepid+tx2500+screen+rotation"). 

Now if there were a good open source alternative to OneNote and a decent pinyin input for traditional Chinese, Ubuntu would be heaven! (I'm using a combination of OneNote installed by Crossover, Tomboy Notes, and Xournal to make up for OneNote.)

---

