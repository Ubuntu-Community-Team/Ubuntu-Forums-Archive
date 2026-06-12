---
title: "Cannot get graphics to work on Toshiba Satellite 4090XDVD"
date: 2012-04-14
forum: Hardware
---

### Post by doctor casey on 2012-04-14
I have an old Toshiba Satellite 4090XDVD running WinME.  It has a Trident Cyber 9525 graphics chip, 192MB RAM, 6GB HD.  Runs well, but slowly.  Some time ago, I installed Wary Puppy 5.2 on a DELL c800, then upgraded to Slacko 5.3.1.  All runs well on the DELL and faster than WinXP.  I'd like to run Linux on the Toshiba, but I cannot get graphics to work at all with any version of Puppy.  I have tried all the XORG options and VESA options.  I have tried to install LUBUNTU 11.10 with similar graphics issues.  I have tried a couple other variants of Linux.  None work out of the box.  I have tried changing horizontal and vertical freqs--no help.  I am not familiar with digging into the kernel or libraries in order to make changes, but wouldn't know where to change or what.  Any help would be greatly appreciated, especially for a Linux newbie.  Thanks.

PS.  I have a  system I built running Ubuntu 11.10, and I am 72, with about 45 years of experience with computer systems, including machine language on a CDC 160A that probably very few of you have ever heard of.  It had a 12 microsecond add time on a 12 bit word.

---

### Post by papibe on 2012-04-14
Hi doctor casey.

Xorg generates a log that can give us some clues. It is this file:
```
/var/log/Xorg.0.log
```
Could you paste its content here: [http://paste.ubuntu.com/]("http://paste.ubuntu.com/") and post back the link?

Also, could you describe what kind of problem are you having. For example, low resolution, black screen, black bar on one side, etc.

Regards.

---

### Post by aforalbert on 2012-05-23
its odd that someone else has one of these but...
i had an old puppy linux cd and xorg works just fine at 1024x768@60.0
its version 5.11, if that helps
it didn't want to give me the full graphic interface until i saved the lupu file to the hard drive (mine is 512mb, but you can choose from like, 28? to a little over 1gb)
then i rebooted the computer, and it led me into the zorg setup, and i chose the 1024x768, despite the warning it may not be ok for the card, and it has been working since

if you have any questions feel free to ask or pm or whatever
this is my first post here, but i hope i can help you

^~^

---

