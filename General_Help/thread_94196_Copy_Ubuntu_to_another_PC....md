---
title: "Copy Ubuntu to another PC..."
date: 2005-11-23
forum: General Help
---

### Post by thermopyl on 2005-11-23
Hi
I have setup Ubuntu on a test pc (and I love it!)

Now I would like to install it on my main PC, but do not want to go through the pain (and time) of installing and configuring it.

Is it possible for me to restore a full backup/copy (using this thread: Howto: Backup and restore your system) to a fresh partition on the new pc? How would i install & configure grub? What about hardware config/drivers (or is this a M$Windows issue only)?

Bit of a noob to this so any help is thankfully received!

---

### Post by lysis on 2005-11-23
UNLESS this is going onto a system with the EXACT same configuration I wouldn't recommend doing this. I know Windows freaks out transferring a hard drive from one system to another (it won't even boot half the time) so I'm unsure how well Linux distros will do with this. 

Safest bet; just re-install so it installs based off of YOUR hardware.

---

### Post by Cannedbread on 2005-11-23
Ive never had that problem with windows.

i think ubuntu would flip out though.
you could probably copy the files over, but then you would have to go through and manually edit the config files to match your new hardware, which would be a pain in the ass.

---

### Post by thermopyl on 2005-11-23
Thanks guys, as i suspected...

Can I export my list of installed apps (poss as a repository of my own) so i can reinstall all my apps in one go???

---

### Post by lysis on 2005-11-23
[QUOTE=Cannedbread]Ive never had that problem with windows.

[/QUOTE]
i work in the computer industry . . . we see that problem several times a week.  customers who's motherboards die and whatnot, if you replace the board windows freaks out and won't boot due to the drivers not being near correct (sometimes the chipset is no longer available, or just different drivers on the new boards)

---

### Post by tmeier on 2005-11-23
I use a program called DriveCopy that allows me to copy whole disks or partitions from one to the other (both drives on the same system).  If your two computers are similar you could use a program like this to make it work.  It is similar to Norton Ghost, but boots off of a CD.

You could take HD out of your computer put it in as a Slave in your TEST computer, boot off of Drive Copy or some similar program, Replicate the TEST drive to your HD of your computer.  Move it back to your computer and see what happens.  It may or may not work, especially with the ext3 file structure, or the change of hardware.

If all else fails a fresh install may be the ticket to a smooth running Ubuntu

---

