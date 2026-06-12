---
title: "Hard disk test tool"
date: 2008-07-23
forum: Hardware
---

### Post by PaladinOfKaos on 2008-07-23
I've got an old-ish Thinkpad T40, and I think the harddrive may be dying - although it may be the disk controller.

I've got a desktop system and a laptop drive adaptor, so I can plug the disk into my desktop and see if it works or not.

I was wondering if anyone could suggest a good tool for verifying the drive. I've already backed up the data I need from it, so a destructive test is OK.

Thanks!
Branan

BTW, I've been running off of a Xubuntu livecd on the laptop for a couple weeks now, no reboots, and no harddrive swap space, (saving to a network drive) and it's still running smooth and stable. 81MB out of 1GB free, and that's with 490MB being used for the disk cache. Linux is just awesome that way =)

---

### Post by nick_h on 2008-07-23
You could start by looking at the smart data using the *smartctl* command.  You could also use *fsck* and *badblocks* - see the following link:

[https://help.ubuntu.com/community/FaultyHardware](https://help.ubuntu.com/community/FaultyHardware)

Disk manufacturers also supply diagnostic utilities.

---

### Post by evets25 on 2008-07-23
Also, you might want to look around the internet for something called the "uiltimate boot CD". I have one lying around here somewhere in the IT dept. where I work. It's basically a collection of hardware diagnostic tools, including HD diagnostic utilities from almost every HD manufacturer under the sun, as well as a half-dozen partitioners, and a sprinkling of other invaluable programs. No idea where it came from, but I know it's been an invaluable tool for me in diagnosing computers that are brought in.

---

### Post by nick_h on 2008-07-23
> Also, you might want to look around the internet for something called the "uiltimate boot CD".

A good suggestion.

[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

---

### Post by Darkspark on 2008-07-23
You could also download "Drive Fitness". That is the tool I use to check the dependability of a hard drive.

---

### Post by evets25 on 2008-07-23
hey yeah, that's the one! neat, now I know where it is on the internet! :D

---

### Post by phoinx on 2009-12-02
> **nick_h said:**
> You could start by looking at the smart data using the *smartctl* command.  You could also use *fsck* and *badblocks* - see the following link:

[https://help.ubuntu.com/community/FaultyHardware](https://help.ubuntu.com/community/FaultyHardware)




Nice tips! Thanks!

---

