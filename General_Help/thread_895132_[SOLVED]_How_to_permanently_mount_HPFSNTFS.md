---
title: "[SOLVED] How to permanently mount HPFS/NTFS?"
date: 2008-08-19
forum: General Help
---

### Post by HousieMousie2 on 2008-08-19
Hi,

Not sure what to do here, newbie and all...

Have read several threads on this topic, but I am running into a serious lack of knowledge... mine.

I didn't have gedit, so I installed it, using apt-get.

Have tried sudo mount /dev/hda2... but it reports:

"mount: can't find /dev/hda2 in /etc/fstab or /etc/mtab"


I do have /etc/fstab or /etc/mtab directories/files in root (using Dolphin to look.) I get an output for them using sudo gedit /etc/fstab and sudo gedit /etc/mtab.

In addition, the results of those two commands do NOT include the drive I am trying to mount (and have automount upon restart.)  It IS a separate physical hard drive, not just a partition on the same drive that Linux is on.  It contains my Windows XP and Recovery Partition, obviously I do not need/want the Recovery Partition to be mounted.

I have deleted the proceeding entries for the cdrom, as well as the ending entries for the USB, video card, ethernet card and so on, from the *collection* of outputs that I have attached.

Can someone help me with this, walk me through it?  Please remember I am using Kubuntu, Gutsy.

Thank you for taking the time to read this thread and thank you even more for any advice/instructions you might have to offer.

Just to stave off this possible line of questioning... I have never put my XP into hibernate and the last shut down was successful... and Gutsy was loaded from the Grub screen... I don't have Wubi either.

---

### Post by HousieMousie2 on 2008-08-19
Nevermind... I was saved from a whole lot of Konsole work by a VERY simple GUI action!

MANY MANY Thank yous to drs305!!!

The instruction was...

Install "ntfs-config" (I used Synaptic, as recomended) then, in a terminal (Konsole) type "ntfs-config" it will open up a GUI box, you click the drive you want to enable, then OK, then I think it asks you about internal and external drives... pick the one you are trying to use, click OK and you are done!

drs305, you are a life saver!  Thank you!

---

### Post by slimb on 2008-08-29
i had the exact issue and this thread was perfect.  ntfs-config worked like a champ

thanks

---

### Post by HousieMousie2 on 2008-08-30
> **slimb said:**
> i had the exact issue and this thread was perfect.  ntfs-config worked like a champ

thanks

So glad to be of assistance!  I spent hours reading threads looking for a permanent solution, luckily I have that time to spend as I choose, so I am happy for any part I may have/have had in cutting that time down for other users!

Happy computing! :KS

---

