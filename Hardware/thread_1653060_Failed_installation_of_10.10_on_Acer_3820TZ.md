---
title: "Failed installation of 10.10 on Acer 3820TZ"
date: 2010-12-26
forum: Hardware
---

### Post by phyzik on 2010-12-26
I tried to install Maverick on my new laptop without much success.

It's an Acer TimeLine 3820TZ with a P6100 processor and an Intel HD Graphics.

In live mode, it works pretty good (a part from som Fn-buttons and sound) and the installation plays out without any (visible) errors, but when I try to boot into my new installation, I get left with a blank screen.

There seems to be some fatal error with X.org. Any ideas? Should I try the 32-bit edition? I really don't want to be stuck with Windows 7!!

---

### Post by erniejunior on 2010-12-26
Did you look after the checksums of the downloaded .iso and of the burned CD?
I had the same issues like you just with a bad copy of the iso file.

---

### Post by phyzik on 2010-12-26
So I managed to solve this issue - unfortunately with a 32-bit installation, but I think the solution would have worked on a 64-bit, too.

I connected to the internet via ethernet cable, and used a command line (I had access to command line but no X) to install all the available updates.

I had to do it 3 times (screen would freeze), but the third time it pulled up Gnome :D

Now most of the stuff is working - wireless, touchpad (scroll is working, but no 2-finger middleclick :( ), compiz and sound.
I still have no internal microphone (but I see there are some threads about it out there) and I didn't test bluetooth...

---

