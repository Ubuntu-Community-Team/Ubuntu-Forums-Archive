---
title: "Ubuntu Uninstall on non-dual boot system"
date: 2009-02-09
forum: Installation &amp; Upgrades
---

### Post by cautiouschris on 2009-02-09
You guys will probably cringe while reading this post, but here’s my (self-induced) problem. Installed the latest version of Ubuntu right over (i.e. not a dual boot) my original OS (Vista) on a Compaq Presario laptop. LOVED IT! Wireless, Graphics, Sound all worked right out of the box. Well now I’m thinking I’d like to go back to a dual boot system. So I figured I could just pop my HP system recovery disks I made into the drive and format HD, re-install Vista, then re-re-install Ubuntu using the dual boot option. Problem is that my HP recovery disks will not work (error: "This PC is not supported by the System Recovery Discs. You will not be able to continue to recover this system with these discs"). I’ve done some Googling and it seems like my best bet is to use Gparted to delete my current Ubuntu partition, then try the recovery disks again. There was also something about “fixmbr” command to change the master boot record to recognize the new partition. Can anyone out there point me in the right direction on this one? Does the HD have to be NTFS formatted for my Vista recovery disks to work? (In the old’n days (pre-Vista) I would just boot DOS from a floppy, run fdisk, and re-install OS.)

Thanks in advanced for any help!

cc

---

### Post by Mark Phelps on 2009-02-09
Recovery disks exist in a couple of different flavors.  There are some that contain compressed files such that the entire contents of the hard drive are restored; there are others that only boot you into a recovery mode and restore the OS partition from a "hidden" recovery partition on the drive.

If you have the second, and you wiped or overwrote the recovery partition on the HP, that could produce the error message you're getting.

It may be possible to obtain complete recovery media from HP (most probably a DVD containing everything you will need) that will restore the entire drive.  But you would need to check with HP to see about that, and to find out what your self-made disks are designed to do.

---

### Post by cautiouschris on 2009-02-09
Thanks for the info.

---

### Post by ahddm on 2009-02-09
You have a copy do i dont think youll have any legal trouble downloading iso and using windows key included with your laptop

---

### Post by cautiouschris on 2009-02-10
> **ahddm said:**
> You have a copy do i dont think youll have any legal trouble downloading iso and using windows key included with your laptop

interesting...I might give this a try. Still no luck w/ HP's "recovery" disks. Which bring me to a whole 'nother rant on why they don't ship the actual software that I PAID FOR w/ the computer. So now it's my job to not only buy the software, but also make my own copy of it? What's next having to bring my own cup to Starbucks?

---

### Post by Mark Phelps on 2009-02-10
> **ahddm said:**
> You have a copy do i dont think youll have any legal trouble downloading iso and using windows key included with your laptop

Their images contain HP software and all the drivers needed for the machine. You can't download an HP "ISO" (from HP) -- unless they have suddenly started making their proprietary images available, which I doubt.

And yeah, I know LOTS of places where you can get ISOs of various flavors, some original MS format, some OEM format, others customized -- and you can probably install Windows afresh from any of these.

The "legal problem" will come when you try to activate the version you installed.  Since this is an OEM box (HP), it most probably uses BIOS-locked activation.  So, while it MAY work with anything you install, it's most likely to work with an OEM version.  But then, it also might not work -- depending on what HP embedded into their custom BIOS.

The "safest" thing to do would be to use HP disks --but you'd have to contact HP to get those, and they'll charge you for them.

---

### Post by cautiouschris on 2009-02-10
Quick Update...
Found my old Windows XP disk from a couple computers ago and it fired right up. Now I'm running XP & Ubuntu dual boot. HP recovery disks were useless and basically will cost me $20-$30 or whatever HP will charge to ship me new ones. I still have a question about if even the HP disks will work since the recovery partition is gone. It's striking to me how easy Ubuntu is to get, how easy to install, and how few issues I've had w/ drivers, meanwhile Microsoft and HP have probably lost a customer for good. (I might still try the ISO route as I seem to have found a HP recovery ISO online).

---

### Post by Mark Phelps on 2009-02-11
cautiouschris:

If the old XP version activated and your devices are working OK, the only thing you're missing from an HP version is the HP-specific software -- which isn't much!

Unless you really want that stuff, you're probably best to stick with what works.

Good Luck

---

