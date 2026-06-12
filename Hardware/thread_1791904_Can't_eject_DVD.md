---
title: "Can't eject DVD"
date: 2011-06-27
forum: Hardware
---

### Post by TimmyK. on 2011-06-27
Hi, I put in a DVD hoping to burn some pictures and videos to it. I left it overnight, but when I came back, there was some notice that said something like "Error - cannot unlock DVD". Now it doesn't seem to recognize the blank DVD, and the button on the DVD drive isn't opening it. Can someone please tell me what to do?

---

### Post by haqking on 2011-06-27
> **TimmyK. said:**
> Hi, I put in a DVD hoping to burn some pictures and videos to it. I left it overnight, but when I came back, there was some notice that said something like "Error - cannot unlock DVD". Now it doesn't seem to recognize the blank DVD, and the button on the DVD drive isn't opening it. Can someone please tell me what to do?


in nautilus right click and choose eject or from terminal

eject cdrom

or if that wont work then try

sudo eject /dev/cdrom

from the terminal assuming it is mounted as so.

Or reboot.

If still stuck then there should be small hole on the device next to the button to open, you can slide a straightened paper clip into that to push it open (dont worry the hole is meant for that ;-)

---

### Post by TimmyK. on 2011-06-27
I never appears anywhere in nautilus, so there is no way to eject it from there. The terminal commands didn't work either. I'll have to try again after I reboot. Thanks for you help.

---

### Post by haqking on 2011-06-27
> **TimmyK. said:**
> I never appears anywhere in nautilus, so there is no way to eject it from there. The terminal commands didn't work either. I'll have to try again after I reboot. Thanks for you help.

ok well if it doesnt work after reboot which it should do then the paper clip will definately work ;-) it wont do it any harm

---

### Post by Maheriano on 2011-06-27
I came in just to post the paper clip idea, must be an old school thing.

---

### Post by dFlyer on 2011-06-27
Have you tried opening a terminal and entering the following command:

eject

press enter and if there is an error message please post it.

---

### Post by haqking on 2011-06-27
> **Maheriano said:**
> I came in just to post the paper clip idea, must be an old school thing.


ha ha yeah i know, we must be old ;-)

I have lost track at how many times people didnt know it was there, or even better is they thought it was a microphone or speaker (my sister springs to mind ;-)

---

### Post by TimmyK. on 2011-06-27
When I type in 'eject', there is no error message (doesn't make me type in my password or anything), it just seems to ignore the command. But the paper clip thing worked fine, thanks. I wonder why it didn't come out. I think this is an old school thing, as my brother's new i3 laptop doesn't have it. I'm glad I have an old school laptop then.

---

### Post by TimmyK. on 2011-06-27
Now I've got a problem. The optical drive won't open at all. Will rebooting fix this, or do I have to get a new optical drive? :(

---

### Post by Maheriano on 2011-06-27
> **haqking said:**
> there should be small hole on the device next to the button to open, you can slide a straightened paper clip into that to push it open
> **haqking said:**
> the paper clip will definately work
> **Maheriano said:**
> I came in just to post the paper clip idea
> **haqking said:**
> I have lost track at how many times people didnt know it was there

If only there were some way of manually opening it....maybe with a device like a paper clip. Maybe if you smashed it with a hammer it might work?

---

### Post by TimmyK. on 2011-06-27
Hmm, that sounds like something my brother would say. But if it doesn't work when I reboot, do I need to buy a new DVD drive?

---

### Post by Yellow Pasque on 2011-06-27
Perhaps the button has broken. I have to press mine really hard to get it to eject.:lolflag:

---

### Post by Yellow Pasque on 2011-06-27
> **Temüjin said:**
> Perhaps the button has broken. I have to press mine really hard to get it to eject.:lolflag:
Dirty mind..

---

### Post by TimmyK. on 2011-06-28
Nope, the button wasn't broken. I have no idea what exactly was wrong, but after the reboot it was fine. Thank you for your help.

---

### Post by Maheriano on 2011-06-28
> **TimmyK. said:**
> Nope, the button wasn't broken. I have no idea what exactly was wrong, but after the reboot it was fine. Thank you for your help.

I have to know why you didn't manually open it with a paper clip. It was posted at least 10 times.

---

