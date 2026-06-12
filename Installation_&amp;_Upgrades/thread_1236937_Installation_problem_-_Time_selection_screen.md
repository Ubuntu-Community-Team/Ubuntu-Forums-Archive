---
title: "Installation problem - Time selection screen"
date: 2009-08-10
forum: Installation &amp; Upgrades
---

### Post by gozzy345 on 2009-08-10
First of all, I am new to the Forum, but not entirely new to Linux. And I thought this more appropriate here than in the Absolute Beginner section.
I have installed two other distros on my PC before very successfully while experimenting to find a distro which best suits me (a version of Red Hat, and Mandriva). I have also successfully installed Ubuntu version 9.04 on my friend's laptop. However, when I tried installing (with exactly the same disc,) onto my PC, I couldn't finish the process.
After a very slow start up, which I expected to some extent, as my computer isn't exactly state-of-the-art, I finally got to the graphic installation. I clicked my language off the list, and it took me to the next screen, after a long time (10-20 minutes) of waiting. The next screen asked me to select my time zone. After selecting it off the map, I clicked next, and then the installation stalled. I left it for a long, long time with the 'working' cursor, but it did not move on. After two days, I turned off the computer, and tried again. It again stalled at the same screen. I gave up on the third time of failing.
I also borrowed another disk, in case there was a problem with the one I tried, but exactly the same thing happened. The disc scan thing also said that the disc was fine.
Can anybody help?

---

### Post by snowpine on 2009-08-10
Hi Gozzy, what are the specs of the computer? Make sure that you have enough ram (384mb minimum). Another good idea is to check the CD for errors--you can do this from the menu that first appears when you boot the CD (right after you choose the language).

---

### Post by presence1960 on 2009-08-10
[alternate text based installer]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate") if your cd has no errors!

---

### Post by gozzy345 on 2009-08-11
I'd like to say, those were extremely quick replies. This seems to be an exceptionally good forum.
I can't get the specs at the moment, as I am away from the computer, but I definately have at least 1 gb RAM, so it isn't that.
The checking for errors was what I meant by scanning the disc, and it was fine.
Text-based? Is it simple questions, or will it require commands to be typed in, and stuff to be compiled? I think it would probably be best to stick to graphic installation, for me though.

---

### Post by presence1960 on 2009-08-11
> **gozzy345 said:**
> I'd like to say, those were extremely quick replies. This seems to be an exceptionally good forum.
I can't get the specs at the moment, as I am away from the computer, but I definately have at least 1 gb RAM, so it isn't that.
The checking for errors was what I meant by scanning the disc, and it was fine.
Text-based? Is it simple questions, or will it require commands to be typed in, and stuff to be compiled? I think it would probably be best to stick to graphic installation, for me though.

No compiling or commands, just old fashioned text based. But the text based installer has more options than the Live Cd. It is just that the Live CD is fancier because it is graphical and you can run the Ubuntu OS off it that makes it more popular, but in terms of support for a bunch of installation options the alternate text based installer is far superior to the Live CD. It has options the Live Cd does not have such as support for LVM and RAID.

P.S. You may want to look at [Boot Options]("https://help.ubuntu.com/community/BootOptions") for the Live CD

---

### Post by gozzy345 on 2009-08-11
Thank you for explaining that, presence1960. I'll have to burn another disc, but I will try.
I have my computer's specifications:
Intel Pentium 4 2.4GHz
1GB RAM
and I have a Radeon 9000 Graphics card, if that may be the problem. I have had a few problems with it before, but I wouldn't think that would be it.
I was actually going to ask about the boot options. What does 'Safe Graphics Mode' actually do? I will try it before the Text-based version.

---

### Post by phillw on 2009-08-11
Safe Graphics mode, reduces to chances of your card not being able to display the graphical instal [it uses a low screen resolution] (the default one with a Ubuntu installation).

Regards,

Phill.

---

### Post by gozzy345 on 2009-08-11
Edit; I tried the safe graphics mode, and it did the usual things until just after the Ubuntu screen with the bar that goes from the left to the right of the screen and back, I got this message, which I had not got before:
[413.205041] usb1-1:device descrptor read/64, error - 110
I don't remember having this before, and it still had just that after 15 minutes of waiting.

---

### Post by gozzy345 on 2009-08-13
Well, I'd like to thank everyone who helped. The text-based installer worked perfectly, and I am writing this from within Ubuntu. However, it is a lot slower than I expected, but that is a problem for another post.

---

