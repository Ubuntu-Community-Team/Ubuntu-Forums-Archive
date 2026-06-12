---
title: "ext4 partition corrupted"
date: 2010-09-11
forum: Hardware
---

### Post by m.dr on 2010-09-11
I have a box with 3 scsi disks with /, /usr and /opt on the 3 separate disks - all ext4.

I also have XP on this box.

My disk with /opt had 'fallen off' the scsi chain once while booting and now /opt is behaving weird. I have several dev apps on /opt such as Eclipse, Matlab and such.

Now when I try to launch them they fail to launch and I get error msgs from them.

When I boot I have no errors and I also tested the disk (/opt on /dev/sdc1) from the SCSI (Adaptec) card bios and disk verifies fine.

Again this disk has the XP partition for 'Program Files' meaning all major software is installed there as in d:/Program Files. And from XP I have defragged it, copied 2gb+ large files to it and ts fine.

So it seems the /opt ext4 partition on /dev/sdc1 is corrupted. So I tried unmouting and fsck commads but cold not run fsck as it says a process is using the partition. Of course I tried it right after logging in as well.

Am wondering what would be the best way to try and recover it? 
Maybe from the terminal (w/o going into WM) at all? 
What should be the sequence of steps I should try to fix the superblocks? 
I get strong warning msgs when running fsck w/o trying to unmount so wondering what I sequence should be following.

Thanks for your help.

---

### Post by Fafler on 2010-09-11
Depending on grub version, pres ESC or shift during boot to get to the grub menu. Now edit the command line used to boot Ubuntu and replace the last two words "quiet splash" with "1". This should boot you into single user text mode and allow you to check the drive.

You could also just comment the entry out in /etc/fstab and reboot.

If fsck doesn't find anything it's still possible that the issue is software/driver related. Most SCSI controllers allow you to se the speed of each device. Try entering the SCSI BIOS and set the device to a lower speed, say 80 mb/s instead of 160. Also check that you have correct termination of the SCSI chain and try reading the XP partition from Linux.

---

### Post by m.dr on 2010-09-11
hi Fafler

Thanks for your reply.

Actually did mean to ask if the problem could be driver related. Meaning when I use the GUI 'Disk Utility' tool to check the partitions I get a 'red stop' message:
An error occurred while ... Device is mounted and no online capability in fsck tool for file system.

It happens for all the ext4 partitions on scsi disks on that box. However I do not get the message for the NTFS partitions - I guess because they are not mounted? I have IDE drives as well and the same msg comes for IDEs as well.

Now the card is a Adaptec 39160 - 2 channel and I am using it o another machine with no problem.

I can reboot it commenting out /opt. So fsck can run to fix superblocks as long as I can get to the partition?

What should be the commands I run and in what sequence? I am being careful as Matlab for example is license based and it is a hassle to get another license if I have to reinstall.

Thanks much for your advice.

---

### Post by m.dr on 2010-09-11
btw Fafler - this machine has been working for a week since I first installed it. 

Does that mean that particular disk could still have a problem with termination?

Thanks.

---

### Post by Fafler on 2010-09-13
Did you sort it out?

Anyway, just reboot without mounting /opt and do a

sudo fsck.ext4 /dev/sdc1

Post the output here, if it still acts up.

And yes, it could be termination related. I've seen some odd errors because of that and bad cabling in SCSI setups.  Although Adaptec usually are well behaved. Try fsck'ing and see how it works out.

---

