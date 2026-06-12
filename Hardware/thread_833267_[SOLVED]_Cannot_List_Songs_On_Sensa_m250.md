---
title: "[SOLVED] Cannot List Songs On Sensa m250"
date: 2008-06-18
forum: Hardware
---

### Post by cmnorton on 2008-06-18
My Sensa m250 will not list its songs in Kubuntu 7.10, but will on Windows XP. What configuration steps do I need to take? Amarok recognizes the device.

---

### Post by stchman on 2008-06-18
> **cmnorton said:**
> My Sensa m250 will not list its songs in Kubuntu 7.10, but will on Windows XP. What configuration steps do I need to take? Amarok recognizes the device.

With the Sansa players you need to put the USB into MSC mode.  This  will allow Ubuntu to see the player.

---

### Post by newtanker on 2008-06-20
This is correct, about the MSC mode.  However, in some recent update there has been a change to hardy which changes the loading of the sansa when it is plugged in.  Formerly (in feisty and gutsy) I would plug the player in (a sansa e250, not rhapsody) and would get the rhythmbox player, as well as a nautilus file manipulation panel with the drive of the player in it.  I would manually add or remove the files i wanted on to the drive.  Since the update, the nautilus panel does not appear, only an icon for the drive, briefly, then it disappears and rhythmbox appears and hangs.  The player is fine, I can mount it perfectly under windows xp (thanks to this problem the first time inmonths ive booted into windows).. I thought perhaps that it was an incompatability with the rockbox firmware i had on it, so i reformatted the drive (and kinda messed it up, i have to bypass the bootloader, but thats really not a problem, ill reinstall rockbox in a bit) but that has not changed the issue.

I am of the opinion this is due to the hal subsystem, but cannot find the issue in the fdi files--they look ok and more than looking is a bit beyond my level....perhaps it is in the new permissions subsystem that hardy has....any ideas?

---

