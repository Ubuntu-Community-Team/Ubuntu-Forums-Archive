---
title: "video problem - screen 'rolls' / blinks in console (Intel 855GM/Toshiba Sat. J16)"
date: 2010-08-30
forum: Hardware
---

### Post by Koohiisan on 2010-08-30
This is weird.  I have a Japanese Toshiba Satellite J16 (or J12, can't recall right now).  I have tried Xubuntu, Kubuntu, and Mint and get this same issue.

During boot up, my console text looks fine.  I turned off the splash screen, and I can clearly read everything that scrolls by.  At a certain point the font changes, and it still is quite visible.  But, when X starts (I assume that is the trigger), I lose my console ability.  If I do CTRL-ALT-F1~6 I get a weird blinking/rolling/flashing line at the top of the screen.  (It reminded me of how old TVs with their vertical sync messed up would roll.)

Basically each line of the console output is displayed one after the other at the top of the screen, then it erases it and does it again.  If I log in (by guessing what it says on the screen), I see the text change, but it still flips endlessly through each line at the top of the screen.  

X itself displays fine.  I've tried a few options on the grub command line, like: nomodeset, vga=0x31a, vga=normal, noapic, noacpi, irqpoll.  I know some of those may not apply, but I wanted to let you know what I have done.

I read that some users have had trouble with the Intel 855GM chipset.  Is this a problem that anyone else has experienced??

Thanks!!

---

