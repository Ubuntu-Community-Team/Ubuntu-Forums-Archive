---
title: "A question just for reassurence."
date: 2009-04-10
forum: Installation &amp; Upgrades
---

### Post by Taj1993 on 2009-04-10
Hello,

Recently I decided to go to Ubuntu.

I just wanted to ask the forums to see if this was ok. Because I've done this before but alas I lost my data in the process.


Currently I have one Sata 750 gig drive with lots of precious data. And a 320 gig IDE hard drive that I wanted to have Ubuntu on.

What I wanted to do was Dual Boot XP and Ubuntu but I wanted to do it in this boot format. 

I currently have it like so:

C:
WinXP only


F:
WinXP Only

Instantly booting into C: with the option of booting into F: via BIOS.

My Goal
______________________________

C:
WinXP only

F:
Ubuntu
XP

Instantly boot into C:, then if I wanted to boot into F: go into the bios and then have it prompt me for Ubuntu or XP.

Im guessing I would have to install GRUB in F: while not even touching C: ? Because right now it instantly boots in C: and if I wanted to boot into F: I'd have to do it in the bios.

I have a good idea of what is supposed to be done. I just wanted to get some input of what you would do, to see if I am doing this right. Seeing as last time I did I lost the C: drive and the XP partition on F:.

Thank you.

---

### Post by cariboo on 2009-04-10
I would suggest you backup all your important data, before doing anything. Then install Ubuntu, what you are planning to do will get realy old fast. Install grub and have the choice to boot either OS from a menu. Be sure you read every step before proceeding.

Jim

---

### Post by Therion on 2009-04-10
> **cariboo907 said:**
> ... what you are planning to do will get realy old fast.
Confirmed.  Been there, done this.

Not trying to dissuade you though...

---

### Post by dE_logics on 2009-04-10
Yeah you can do that.

You just need to see which partition is the d:

Then install ubuntu on it.

Technically (I'm not sure though) GRUB will be installed on c: (or the first sectors of the HDD) which will give you the options for which OS to start.

---

### Post by Mark Phelps on 2009-04-10
To be totally safe, as in risk NO CHANCE of anything being overwritten or corrupted in your XP install, simply do the following:
1) Disconnect the XP drive
2) Set your BIOS to boot from the other drive
3) Install Ubuntu on the other drive
4) Reconnect your XP drive but continue to boot from the Ubuntu drive and use GRUB's menu to select XP.

---

