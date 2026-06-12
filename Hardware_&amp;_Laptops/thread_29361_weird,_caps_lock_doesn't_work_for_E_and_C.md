---
title: "weird, caps lock doesn't work for E and C"
date: 2005-04-24
forum: Hardware &amp; Laptops
---

### Post by silvan on 2005-04-24
I've run on a pretty good variety of hardware, and this is a new one on me.  I've got a box whose caps lock does not work correctly.  If I put caps lock on (the LED comes on) and type the alphabet, I get

ABcDeFGHIJKLMNOPQRSTUVWXYZ

I have to use the shift keys to get a capital C or a capital E.  Weird!

I'm seeing this at all layers of interaction with the box, so it's not an X keyboard config problem  I have no idea how keyboard config works on the non-X level.  I can see this at a text login: prompt too, and on any of the ttys.

My first thought was a bum keyboard, but I've ruled that out by swapping keyboards around.  The problem is with this particular machine.

How does caps lock work under the hood?   Since the key can be diverted to other uses, I assume the keyboard doesn't generate capital letter keycodes when it's in caps lock mode.  I'm thinking this must take place at a low level of system config, at a kernel level, or maybe even in the BIOS.

I'm not sure where to look.  It's annoying.  I use the caps lock key all the time.  I used it to type the word BIOS for example.  It doesn't mean I'm SCREAMING at the world or anything.  This little quirk is driving me nuts.   ](*,) 

I don't have access to the box from here to post detailed hardware config.  I can only be vague for the moment.  It's a new P4-2.6 with an ASUS mobo; the mobo has an Intel chipset and a recent AMI BIOS.  I've got the 2.6.10-5-686 kernel on there.

Any insight would be wonderful.  I realize this is likely not specifically an Ubuntu problem, but I'm not currently involved with any "general Linux" fora, as I spend all my time in Rosegarden Land.

---

### Post by Mat10 on 2005-04-24
Probably a silly question, but do you or have you used this machine with another operating system ?  My thinking is on the keyboard controller on the motherboard.
Point is if it is the controller it would do the same on any  operating system  !!

The keyboard has its own BIOs on the board separate from the system BIOs, at least it did 13 years ago.   Who knows now.

Tom

---

### Post by silvan on 2005-04-26
[QUOTE=Mat10]Probably a silly question, but do you or have you used this machine with another operating system ?  My thinking is on the keyboard controller on the motherboard.
Point is if it is the controller it would do the same on any  operating system  !![/QUOTE]That's a good point, and no, I haven't.  I live in a 100% Linux world now, and have since about the first quarter of 2002.  However, I think it's software-related because I'm 80% certain I saw this before I moved the hard drive into the new computer.  I should get out the old one and test that.  After I moved the hard drive, I moved its install onto a bigger drive, so I can pull the old one back into the old box.> The keyboard has its own BIOs on the board separate from the system BIOs, at least it did 13 years ago.   Who knows now.Yeah, I know exactly what you mean.  I don't even try to keep up anymore.

---

