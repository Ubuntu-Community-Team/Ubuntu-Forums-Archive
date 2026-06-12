---
title: "PLEASE HELP!  - Need simple mount/copy commands"
date: 2009-08-11
forum: Installation &amp; Upgrades
---

### Post by M4D88 on 2009-08-11
Hey Guys, 

Ive made a custom live-cd that runs off a USB stick, Using "Reconstructor" ( a simple program that lets you edit the ISO then recompile it again with your own custom settings).

All i need this boot stick to do is...

Copy files from the FAT32 partition of the USB stick (thats already automaticly mounted) to the ext3 partition on the local drive. (not mounted)

I'm in the process of editing the ISO now, and i need to know what commands to add in /etc/init.d/rc.local in order to mount the ext3 drive and copy the files. (if thats what needs to be done)

once this is done i need the machine to shutdown (the PC's I'll be using this USB stick on have no screens/keyboards, just set to boot from USB in BIOS, so its need to be fully automated.

One last thing, the files that are being copyed already exsist in the target folder, so they need to be overwritten.

Can anyone help me please, I've been pulling my hair out on this one. LOL

---

### Post by slakkie on 2009-08-11
I suppose the livecd has a fstab entry somewhere?

---

### Post by M4D88 on 2009-08-11
umm yeah I'd say so, Im a bit of a Linux n00b so i dont know all the paths.

Its just a default Ubuntu 8.10 live CD, so i dunno where its located on the filesystem.

---

### Post by pastalavista on 2009-08-11
...never mind

---

### Post by slakkie on 2009-08-11
> **M4D88 said:**
> umm yeah I'd say so, Im a bit of a Linux n00b so i dont know all the paths.

Its just a default Ubuntu 8.10 live CD, so i dunno where its located on the filesystem.

fstab is found in /etc

---

