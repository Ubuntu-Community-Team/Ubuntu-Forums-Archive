---
title: "Installation help needed - Failed to unmount partitions"
date: 2009-08-07
forum: Installation &amp; Upgrades
---

### Post by WhatsInAUsername on 2009-08-07
Hi,

I'm having trouble installing Ubuntu on my laptop..

I'm installing from my hard disk using UNetbootin and keep receiving the following error when the installer is attempting to partition the disk:

Failed to unmount partitions

The installer needs to commit changes to partition tables, but cannot do so becaue partitions on the following mount points could not be unmounted:

/cdrom

Please close any applications using these mount points

Would you like the installer to try to unmount these partitions again?

There is an exisiting XP install on the drive, and I have tried various combinations of new partition tables and deleting existing partitions, to be reformated by the installer, to no avail and keep receiving the same error.

Any help welcome!

---

### Post by iigeli on 2009-08-08
I have the exact same problem, trying to install Linux for the first time... I have an existing XP installation on my C:\ drive and am trying to install Ubuntu to a separate partition. First time I just figured that alright, I'll unplug the DVD-ROM drive (shutdown and restart) and try again - but the problem still exists. I'm running from hard disk too.

---

### Post by iigeli on 2009-08-10
I have just tried using a regular CD installation and it still says the same thing. Maybe it has some problems with the Windows on the first partition or something...

Edit: Ok so I've done more googling now, and found similar threads everywhere... Using a hard disk install again, I now got past this point by starting the console (upper left corner, Accessories -> Terminal) and typing "sudo umount -l -r -f /cdrom" (I first tried stuff like /dev/sda7, /dev/sr0 and /dev/cdrom, but I guess those are always different for every computer so I just went ahead and put /cdrom, and then it presented me with yet another partitioning screen, a different one this time, and then proceeded to install. No idea if the whole thing is successful though, will update in a bit...

---

### Post by stlsaint on 2009-08-10
have you ensured that your partitions are setup correctly...are they formatted is what i mean?

---

### Post by merlinus on 2009-08-10
A suggestion is that after setting up the partitions for ubuntu, rightclick (or edit) each one and look at the dropdown mountpoint menu to ensure that none are /cdrom.

---

### Post by iigeli on 2009-08-10
In my case I had three partitions: one for Windows (not to be used), one for swap and one mounted as /. (Well they were originally the Windows partition and then a data partition.)

Unmounting /cdrom manually helped me for good, the installation went fine (apart from some jre package problems but I guess that's minor). 

Too bad now I'm getting constants reboots when Grub or whatever tries to launch memtest upon first boot (and memtest runs fine from the CD), I guess I should post another thread about that... Maybe I'm just not supposed to mess with Linux, heh. 

Anyhow, the unmounting problem is solved for me, I hope the same helps the original poster too.

Edit: I feel a little stupid now... I decided to do a clean install again, and wanted to partition the disk for Linux only. Well, I ran into the /cdrom problem again, and what got me through was the realization that I couldn't touch the drive that was being used for installation (e.g. /dev/sda1). It basically says so in the very screen, I just didn't fully understand it until now. So I just left all the partitions as defaults, made one of them ext3 + mounted as /, and then just let it ran. No problems and it's now up and running just fine.

---

### Post by michaeloleary on 2010-11-13
I ran into this problem on Maverick recently it, I'm not sure what version you are using but in my case I was install from a USB key, and I was receiving the error "Failed to unmount partitions" and it refered to the /cdrom.  I could work around this issue by ejecting the CD ROM drive on the laptop and leaving it out.  However I ran into another issue where APT would fail configuration.  I tracked the issue back to the fact that I had accidently created a new folder in the root of the USB key.  Deleting the folder seemed to rectify the problem as I'm currently finised installing.  I can only assume that the installer does some sort of check to insure the directory structure hasn't been compromised.  I hope this help if anyone runs into this issue on Ubuntu 10.10.

---

