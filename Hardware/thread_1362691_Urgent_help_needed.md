---
title: "Urgent help needed"
date: 2009-12-23
forum: Hardware
---

### Post by iceblizz on 2009-12-23
Just installed Linux Ubuntu on my laptop, all installed right but now when I start my laptop up I get 4 options:

Ubuntu, Linux 2.6.31-14-generic
same as above but recovery mode
memorys test
etc

I click the top one and nothing happens, just goes to a black screen with the  _ flashing..

when it does work and i finally get onto my desktop after about 50seconds the mouse freezes and i cant do anything, keyboard still works tho...but like i said thats when it finally does decide to take me to my desktop which doesnt happen alot...


any help please...?

---

### Post by HeadHunter00 on 2009-12-23
what mouse do you have? try other options.

---

### Post by iceblizz on 2009-12-23
its a laptop...and I highly doubt the laptop mouse is causing the problem for the laptop to not even boot up

---

### Post by K.J. on 2009-12-23
Do you have any USB drives attached? Check to make sure the right partition and disk are being selected in grub.

---

### Post by iceblizz on 2009-12-23
and how do I do that?

---

### Post by K.J. on 2009-12-23
Hit "e" when grub loads. You'll see something like hd(0,0) which it should probably be. Although try different values like hd(0,1) and hd(1,0) if you aren't sure what it should be. The first number is which disk and the second number is which partition.

Also, if you have any USB drives attached, remove them and try again.

Do you have any other operating systems installed?

---

### Post by iceblizz on 2009-12-23
nope I dont have any other OS installed, tryed the 0.1 and 1.0 aswell, still doesnt boot up just get a flashing _ on a black screen

---

### Post by K.J. on 2009-12-23
Check your bios for a HDD self test. Run and report back with the results.

When you say the keyboard continues to work, is the whole OS working (besides the mouse)?

Sounds pretty bizarre. I would also try reinstalling, but before installing run the "Check Media" option to make sure it was a good burn.

---

