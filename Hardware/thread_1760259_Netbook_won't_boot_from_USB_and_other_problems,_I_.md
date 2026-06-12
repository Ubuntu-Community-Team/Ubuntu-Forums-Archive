---
title: "Netbook won't boot from USB and other problems, I have checked google!"
date: 2011-05-16
forum: Hardware
---

### Post by Mugmoor on 2011-05-16
I recently bought a Toshiba NB555D-011 which came with Windows 7 Starter installed, obviously the first thing I did was try to install Ubuntu.

I followed the directions on the Ubuntu Website for making a LiveUSB drive, set my Bios to boot to USB first and yet, nothing? So I figured I'd try to install through wubi instead, which worked fine once I booted into demo mode, up until I received an error message (which I do not have written down), it informed me I should reboot though, which I did.

Problem is, now my laptop just boots to nothing at all. Just sits there, not recognizing that my USB drive is installed, not picking up Ubuntu since it didn't fully finish, and not picking up Windows since it got erased.

Does anyone know what I can do right now? I've been looking through the Bios for anything that seems out of the ordinary but I can't seem to figure it out.

---

### Post by dabl on 2011-05-16
I have a Toshiba NB205, running Debian Sid (aptosid) for about a year now, or a bit more.  If you really want Ubuntu, I would advise dumping the WUBI installation along with Windows.

I like the Parted Magic Live CD / USB stick for partitioning work in general.  If you boot that, then do "Device > New Partition Table" and choose MS-DOS type.  That will nuke your hard drive and all the data on it, so you need to back up any valuable data first.

Then use the partitioning tool (gparted) and make whatever partitions you need.  I would advise a 15GB root partition, a 500MB swap space, and the rest for a third partition -- you can mount it on /home, or else use it for a data partition.  Format the two non-swap partitions as ext4.

Then boot a Ubuntu "Alternate Install" CD, and choose "manual partitioning", and just choose the mount points, without formatting.  Everything else can be defaults, including installing Grub to the MBR of the hard drive.

---

### Post by Mugmoor on 2011-05-16
The problem seems that my laptop isn't recognizing that there's anything plugged into the USB port at all. I've tried two different drives and neither work. I guess at this point it isn't a problem with Ubuntu, thanks for your help though!

---

### Post by newboon2 on 2011-06-11
> **Mugmoor said:**
> I've tried two different drives and neither work.
Out of curiosity, what brands were the USB drives?

I also have an NB555D, and it doesn't see any of my Lexar drives at the boot loader stage. Unfortunately, most of mine are Lexar because they tend to work better with my Mac (on my particular machine, Lexar is the only brand where the light turns off after the volume is unmounted / ejected).

After I went out and got something else, it worked fine with 11.04 for booting (but not for installion due to unrelated issues).

So, perhaps try yet another drive and maybe third time will be lucky.

---

