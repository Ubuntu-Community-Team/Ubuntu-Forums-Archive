---
title: "Boot from USB external hard drive with Ubuntu installed on any pc"
date: 2008-10-06
forum: Hardware
---

### Post by Ash44455666 on 2008-10-06
Hello everyone!

Yesterday, I finally took a trip to FRY's Electronics, and bought myself a 500GB external hard drive.  Although it was meant for backup and storage, I thought I might be able to install a boot-from-anywhere OS.  I knew XP and Vista were impossible (it would violate the EULA), not to mention they both have problems with booting from USB connected devices anyways.  But, then again... what about Ubuntu?

I haven't tried it yet, but from all the guides it looks like it's definitely possible.  What I would like to know is, assuming I can get Ubuntu installed on the external hard drive, could I boot from this external HDD on any computer?  I'm pretty sure it **wouldn't** work, because I've tried connecting a hard drive with Windows XP installed on it to another PC, and it would BSoD during boot up.  However, Ubuntu is not Windows, so I decided to ask :****P

Thanks for reading my thread, and for any help you can give me!

---

### Post by Ash44455666 on 2008-10-07
Hmm, I managed to find some information about this via Google
[http://brainstorm.ubuntu.com/idea/3151/](http://brainstorm.ubuntu.com/idea/3151/)
Some people seem convinced that it should work (boot from any computer that supports booting from a USB device).  Any input?  :|

---

### Post by Ash44455666 on 2008-11-11
Sorry about the triple post to what *appears* to be an old thread of mine.  Actually, I've been keeping (in vain) somewhat updated with the thread, hoping someone would reply.  Well, I finally had a chance to try it myself.


I downloaded the new version of Ubuntu as soon as it came out.  I burned it to disc (as usual), and installed it to my external hard drive.

**An important note**:  I accidentally installed GRUB to the *first* partition on the HDD, which was an NTFS partition that I was using for backup.  Fortunately nothing was deleted (via format or something like that), but it did somehow corrupt the partition.  (I fixed this later)  Eventually I got everything booting up correctly, and I was still able to access the files.

So, to help avoid confusion, there's three partitions on the external hard drive.  An NTFS partition is first, and it's about 440GB or so.  It takes up most of the room.  Then in an extended partition, there is an Ext3 partition for Ubuntu and another one for swap space (it's like 2GB or 1.5GB... I never know how big to actually make them =\).

Since I got everything working just fine, I disconnected the external HDD from my laptop, and took it to the office.  Connected it to my mom's PC, changed the boot order in the CMOS, and let the computer boot into the USB external HDD.  It definitely tried to boot, but here was what it gave me:

> GRUB loading, please wait...
Error 18
After which nothing happened unless I restarted the computer (via Ctrl+Alt+DEL), or forced it to shut down (via Power Button).
Why is GRUB doing this?  Can I fix it?

---

### Post by C.S.Cameron on 2008-11-11
I recall grub error 18 is when the computer,s BIOS will not read disks larger than 32 GB.

edit
Well, I just tested a 120 GB USB hard drive with a 65 GB Xubuntu partition on an old computer I was once getting grub error 18 on, and it booted OK.

I got grub error 18 after installing XP to an 80 GB hard drive on this computer.
XP would only format and install to the first 32 GB.
After installing Ubuntu to the rest of the disk, I got grub error 18.
I reduced the XP partition to 15 GB using gparted, then fit the Ubuntu partition and swap into the first 32 GB.
Both Ubuntu and XP booted with no errors.

---

### Post by caljohnsmith on 2008-11-11
> **C.S.Cameron said:**
> I recall grub error 18 is when the computer,s BIOS will not read disks larger than 32 GB.
Actually the limit is either 8.5 GB or 137 GB. You can read more about where those limits come from in this [Wikipedia article]("http://en.wikipedia.org/wiki/AT_Attachment") for example. 

Ash44455666, in order to prevent a Grub error 18, the bottom line is that you need to move your Ubuntu boot files closer to the front of the drive so that the BIOS can access them on start up. The usual way of doing this is to create a ~200 MB /boot partition at the beginning of the drive, and you should be all set. You can do that during the Ubuntu installation by creating that 200 MB partition and specifying its mount point as "/boot". If you need more details, let me know, but that's the general idea.

---

### Post by Ash44455666 on 2008-11-11
oh, I see.  Would there be some way I could "move" GRUB to a different, new NTFS (or whichever) partition, that was at the beginning of the drive, but was just large enough to fit GRUB in it?  If not, could I reinstall it to the new partition and have it work the same, but not write over the MBR (which is originally what I was avoiding)?

Edit: Heh, we both posted at about the same time :P.  Thanks for the information, I'll try that later today.

---

### Post by C.S.Cameron on 2008-11-11
On a flash drive Windows will only see the first partition.
I just checked my USB hard drive and Windows sees the second partition, which is fat, ok.

---

