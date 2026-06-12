---
title: "Frustrated Beyond Belief, what is it with ATI and Ubuntu?"
date: 2008-08-03
forum: Hardware
---

### Post by JulienPDX on 2008-08-03
Okay first of all, I don't consider myself a Linux newbie.

I have spent the better part of today following at least 5-6 different sets of instructions (verbatim) on attempting to install working 3D drivers for my ATI x1650 Pro card and to no avail--neither set of instructions works for me.

I'm excited beyond belief that Ubuntu, straight out of the box, with very little effort, works beautifully on my rather late-model laptop.  For once, I finally have an installation of Linux working on a computer and it's been working solidly for months.  For once, I can play games, and do everything I've been able to do with windows.  

Okay, so now i want to switch completely and I still can't do it on my desktop because of this freaking problem.  Anyone have any advice? All I'm getting is either a blackscreen when it boots or I'll get the gdm, and then a white screen with a mobile mouse cursor. 

These "stickies" where people attempt to post instructions that work and then leave them up there for a year aren't really helpful, btw.  I think it's best if you create a sticky to not let people post on top of it.  Also, the OP should continue to keep it updated by editing it eh?

---

### Post by tuxxy on 2008-08-03
I have the ATI X1250, 1650 chips running on 8.04, just enable the ATI driver from **system > admin > hardware drivers**

If its not listed try and install them through **Envy**, you can find this in synaptic,  when you do get the driver installed I dont know if you should expect flawless performance either.  That chip will run effects to an extent, however for me I couldnt get flawless or detailed effects and 3D could be an isssue also due to the poor ATI drivers

I upgraded to an nvidia card for my main system and it solved all the issues I had with the ATI drivers.

---

### Post by JulienPDX on 2008-08-03
1) I've attempted to simply use the "restricted driver's available" (ubuntu's automatic proprietary driver installer).  This results in a black screen upon login.

2) I have attempted to use envyng, this also creates a black screen upon login and never completely "uninstalls itself" either.

3) I have followed the instructions given in the sticky at the top of this page, this gives me a gdm, but upon login--white screen with mobile cursor.

4) I have followed the instructions on ATI's "unofficial" forum, but I get errors that start with "cannot open display" when attempting to gedit my xorg.conf file, and result in a black screen upon login.

What else can I do?

---

### Post by tuxxy on 2008-08-03
Funny, it ran on mine im certain, although I have the x1250 board in the right now and that also runs out of the box for me.

You could try this link, it was for gutsy but maybe worth a look

[http://ubuntuforums.org/showthread.php?t=603595](http://ubuntuforums.org/showthread.php?t=603595)

EDIT:  [http://ubuntuforums.org/showthread.php?t=611492](http://ubuntuforums.org/showthread.php?t=611492)

---

### Post by Sef on 2008-08-03
Moved to Hardware and Laptops.

---

### Post by Dark Hornet on 2008-08-04
I used to have an ATI card back in the day, and I had so many driver issues with it, that I finally just broke down and upgraded to nVidia.  I know thats probably not what you want to hear, or maybe what you are in a position to do right now, but....currently nVidia has much better support for the Open Source/Linux community.

At any rate, good luck!

---

### Post by tuxxy on 2008-08-04
I went through the same process hornet, glad I did upgrade though in the end :)

---

