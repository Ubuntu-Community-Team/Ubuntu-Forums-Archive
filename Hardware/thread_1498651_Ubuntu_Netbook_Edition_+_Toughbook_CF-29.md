---
title: "Ubuntu Netbook Edition + Toughbook CF-29 ?"
date: 2010-06-01
forum: Hardware
---

### Post by tenbbs on 2010-06-01
Can anyone think of any reason why UNE would or would not work on a Toughbook CF-29? I want to be able to do all of the normal things like Skype calls and webcam, watch Divx movies, browse the web, etc.

I don't think there will be any problems, but I know the UNE build is aimed at the Atom processors and the graphics chipsets that usually accompany them.

I know that XPSP3 is a bit of a bear for a machine that only turns a Pentium M at 1.4Ghz and can't hold more than 1.2GB of RAM.

So - any thoughts?

Thanks,
-Ford

---

### Post by tenbbs on 2010-06-08
Well... that didn't go so well. This is a Panasonic Toughbook CF-29 H3 model. Non-touchscreen, Pentium 1.4 M, 1.5 GB RAM, 40 GB HD, CD-ROM drive.

The machine boots off of the Ubuntu NBE 10.04 CD-ROM, goes to the splash-screen (the Ubuntu Logo and 4 orange/grey dots) and after a few seconds the splash screen clears, the screen goes blank, and the CD-ROM drive stops reading. That's it. I ran the Check CD-ROM utility from the boot menu of the cd-rom and it checked good. I ran the check RAM (MemTest) utility and that was good as well. I put the CD-ROM in my Dell Inspiron and it ran just fine letting me into the LiveCD environment.

I've tried Alt-Ctl-F1 to see if there's a command prompt, but that doesn't work. I can't find any special key combination that does anything for me.

I also burned a copy of Puppy Linux 5.0, and that meets with pretty much the same results. It gets to "Setting up the layered filesystem... Done" and then "Performing a 'switch_root' to the layered filesystem...Kernel Panic - not syncing: Attempted to kill init!

And that's the end of the show... she will go no further.

Any suggestions? The thing has Win XP installed on it and functional, so the machine works... I'm a little lost.

-Ford

---

### Post by lepar_m on 2010-12-05
I cant believe nobody jumped on this one. Five months ago, so I guess you figured out 10.10 installs perfectly on the CF-29. Then you still need to make some changes to grub to prevent the black screen. I was also able to get my ouch pad resolution working pretty well but I have the touch screen and cant get it working quite right.

Heres a tutorial by Gork! for GRUB fix and mouse resolution/touch screen
[http://forum.notebookreview.com/panasonic/496467-cf-29-ubuntu-10-4-success.html](http://forum.notebookreview.com/panasonic/496467-cf-29-ubuntu-10-4-success.html)

for some reason after you update 10.10 again you will need to hold down shift and either coose failsafe or enter a tty screen to redo the fix manually. Goodluck

ps I know this is way old im just linking to the fix for 10.4 and trying to explain a little of how it varries in 10.10 so somebody like me might stumble opon it.

---

