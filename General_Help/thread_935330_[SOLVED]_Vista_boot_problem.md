---
title: "[SOLVED] Vista boot problem"
date: 2008-10-01
forum: General Help
---

### Post by food789 on 2008-10-01
I installed the newest Ubuntu just a few days ago, and I think its awesome.

I have a problem though. I have my Acer Aspire 5315 dual-booting between Vista and Ubuntu. So far I've only been using Ubuntu, but when I noticed most of my games wont work, I wanted to boot into Vista to play.

On the boot loader thing that starts up, I have the options basically Ubuntu and Vista, except the Vista option is Windows Vista/Longhorn(Loader). When I select it (there are 2...) it goes to "Acer eRecovery" screen with options to return to factory default, one other one, and exit.

Is there a way to actually boot into Vista without getting into the eRecovery manager? Do I have to delete Ubuntu? Will the "Return to factory default" work w/o deleting my files?

---

### Post by briandu on 2008-10-01
Ok so boot into ubuntu and open terminal session - then

sudo update-grub and you should be good to go - in Vista/XP

---

### Post by food789 on 2008-10-01
Thaks. Going to test now, I'll get back to you.

Update: I tried that, nothing. Switching to XP is a reasonable soulution though, would that work?

---

### Post by Hydrohs on 2008-10-01
Since there are two, just pick the other one. On mine the first one is the one that boots into Windows, it might be ddifferent for yours.

---

### Post by food789 on 2008-10-01
Wow. It actually works! Thanks, I thought that I messed my lappy up.

I want to know, if I do change to XP, all I have to do to boot through GRUB is "sudo update-grub"? XP should work though, right?

---

