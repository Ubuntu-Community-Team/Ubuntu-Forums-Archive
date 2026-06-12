---
title: "Ubuntu won't install - CD check is fine"
date: 2009-01-29
forum: Installation &amp; Upgrades
---

### Post by acialk on 2009-01-29
Hey there, 

I've downloaded Ubuntu, burnt to disc using nero and attempted to install it on my other system.

I can boot from the disc fine and I get the menu options and when I attempt to install I just get a blank screen. It just sits there. Also the Live boot doesn't work either, it does exactly the same thing.

I've checked the CD using the option available in the menu and it says it's fine.

My system specs :
Intel P4 2.4 Ghz on an intel motherboard
1 gb ram
40 gb maxtor hard drive

Any idea what's up? I was running XP fine on this system prior to attempting to install ubuntu.

---

### Post by merkourio on 2009-01-29
i had the same problem too:(...
I know i am new, but did you check that the cd is an image?
Hope I Help!!:p;)

---

### Post by dagriff on 2009-01-29
Whilst this is just a guess, have you checked that you are using the correct architecture?

You can install 32bit on 64bit machines but not vice versa.


Are there any messages at all when it fails to install?

When it fails, do your keyboard lights flash at all?

Can you toggle numlock?

Can you try Alt+F1, Alt+F2 etc and verify that there are no messages on other virtual consoles (1st console is accessed via Alt+F1, second via Alt+F2 etc)

---

### Post by avtolle on 2009-01-29
Have you tried running the Live CD under Safe Graphics mode to see if that helps? I believe you press F4 at the opening menu, and select that option (it has been a very long time since I've run a Live(Desktop) CD; due to my hardware, I use the alternate install always). BTW, which intel mobo do you have, and which release are you trying to install/run?

---

### Post by acialk on 2009-01-29
All is well!

First I tried another distro and I had exactly the same problem. I could see the initial welcome screen, I begin the installation process then it just goes blank. I can hear the cd drive and hard drive working away but I can't see shizzle.

Here's how I fixed it.

My graphics card is a Radeon 9700 PRO and it has a VGA and DVI port. I was initially using the DVI port, I then switched to VGA and it fixed my problem.

I don't understand why but it solved it.

I'm using an old CRT monitor which uses a VGA to DVI converter because my newer system only has two DVI ports.

Thanks for the recommendations people.

---

### Post by boof1988 on 2009-01-29
> **dagriff said:**
> Whilst this is just a guess, have you checked that you are using the correct architecture?

It has been my experience that the 64bit will not even go through the error check on a 32bit system.  Since the OP says that the error check went okay, I don't think there is a problem of wrong architechture...

Just wanted to put this out there.

---

