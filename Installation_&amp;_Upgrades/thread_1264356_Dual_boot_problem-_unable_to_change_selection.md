---
title: "Dual boot problem- unable to change selection"
date: 2009-09-12
forum: Installation &amp; Upgrades
---

### Post by stretcho on 2009-09-12
Hi,
 
I'm a newbie to Ubuntu however have been running GoPC for quite a while. (gopc.net)
 
Have just installed Jaunty onto my Vista machine without any problems except for the following.
 
I have Vista on one drive, and Jaunty on another, so two separate drives, no partitions.
 
Got Ubuntu up and running, no problems, however when I want to change at startup and select windows, I am unable to make the selection, it is almost as if it is not recognising the keyboard or input.
 
Also, I'm unable to enter my BIOS, same thing, as if GRUB has locked me out??
 
Any suggestions on a fix?
 
Cheers
 
Stretcho

---

### Post by oboedad55 on 2009-09-12
> **stretcho said:**
> Hi,
 
I'm a newbie to Ubuntu however have been running GoPC for quite a while. (gopc.net)
 
Have just installed Jaunty onto my Vista machine without any problems except for the following.
 
I have Vista on one drive, and Jaunty on another, so two separate drives, no partitions.
 
Got Ubuntu up and running, no problems, however when I want to change at startup and select windows, I am unable to make the selection, it is almost as if it is not recognising the keyboard or input.
 
Also, I'm unable to enter my BIOS, same thing, as if GRUB has locked me out??
 
Any suggestions on a fix?
 
Cheers
 
Stretcho

Grub doesn't affect the BIOS. You should be able to get into the BIOS before grub starts up. Usually it's the F-2 or F-12, something like that. You may have to experiment. On old desktops it's usually the "delete" key.

---

### Post by rob-ward on 2009-09-12
Are you using a USB keyboard, one of my older computers that I use as a server will not register any key presses from a USB keyboard until the OS has booted, this means that I have to plug in a ps/2 keyboard to access my bios or a grub menu, you may be having the same problem.

---

### Post by arigoja on 2009-09-12
yap that's right use ps2 keyboard...

---

### Post by stretcho on 2009-09-13
Thanks for your input, the screen says to go F2 or F11, I've tried every key including delete.
 
Another of the posts suggested a PS2 Keyboard, and that is exactly what I already have.
 
It's really weird, and I was only into the bios just before I loaded Ubuntu, now all locked out.
 
Do you think maybe something might have happened to my Nvidia driver? I see the graphics card is detected first. Im thinking the graphics card boots, then the bios boots next?? I'm not to sure on that process at start-up.
 
Cheers

---

### Post by confused57 on 2009-09-13
I have an Intel mobo that I have to hold down the F2 key to enter bios, you could try that.

---

### Post by stretcho on 2009-09-13
No didnt work, you know I even tries changing the drives over to see if vista would boot ina  different mobo port.
There is absolutely no response from the computer, i reckon could almost be jumping on the keyboard and it wouldnt matter!!

---

### Post by rob-ward on 2009-09-13
If you think something has gone wrong with your bios then you could try reseting the bios back to defaults, the instructions should be in your motherboard book.

Still not sure why there should be anything wrong with your bios though.

---

### Post by stretcho on 2009-09-13
Hi Rob,
 
I reset the CMOS on the mobo as per Asrock's instruction manual. Noticed at the first startup that another function was offered being F1. So had F1, F2 and F11 on offer.
 
Still same issue, keyboard is now working, computer is non-responsive.
 
Ive noticed the keyboard lights (caps, num, scroll) etc light up momentarily during boot, however then the buttons wont work to turn the functions on, ie caps lock etc.
 
Once Ubuntu is fully booted, the keyboard works fine.
 
I'm wondering if I disconnect the harddrives and then try and boot of a USB? I wonldnt have a clue what to use.
 
I rememeber seeing in the BIOS there is a setting for PS2 keyboard, not sure what setting it was on, is there any other way into the BIOS? like through Ubuntu once we've loaded it up?
 
Cheers

---

### Post by newsoft on 2009-09-13
use PS2 keyboard and mouse :)

---

### Post by stretcho on 2009-09-13
Yes I do have a PS2 Keyboard connected.

---

### Post by rob-ward on 2009-09-13
I'm not sure why you would be having this problem, your keyboard obviously works and has power at the boot stage, your bios obviously isn't the problem. I'm running out of ideas. It may be worth while trying a live CD to see if its menu responds to your keyboard.

---

### Post by stretcho on 2009-09-13
Hi Rob,
 
In terms of a "live CD" what would be on this CD?
 
Another BIOS or a copy of Ubunutu or Windows?
 
Cheers

---

### Post by ceciliaFX on 2009-09-13
> **stretcho said:**
> Hi Rob,
 
In terms of a "live CD" what would be on this CD?
 
Another BIOS or a copy of Ubunutu or Windows?
 
Cheers
the Live CD for your Ubuntu

didn't you install Ubuntu using a Live CD??

---

### Post by ceciliaFX on 2009-09-13
> **stretcho said:**
> Hi Rob,
 
In terms of a "live CD" what would be on this CD?
 
Another BIOS or a copy of Ubunutu or Windows?
 
Cheers
have you tried using another keyboard (borrow a friends) just in case there's something wrong with the one you are using?

---

