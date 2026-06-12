---
title: "error 18 problem"
date: 2009-06-03
forum: Installation &amp; Upgrades
---

### Post by aharp on 2009-06-03
Hi:

I am a real neophyte.  I installed U7.10 a year ago without any problem, but have not used it much, although I want to become a linux person as soon as I can find the time.  Recently, I could not get a required version of Adobe Reader to work on win98 so tried linux.  Could not get the appropriate Reader file to open in 7.10 and a lot of applications said my computer (Athalon 2600) was not supported.  So I tried later versions of U, first 9.04 then 8.04.  Both seemed to load fine, but gave error 18 on the start.  I tried the fix of making the disk drive large instead of LBA but that did not seem to make any difference.  I did use the Western Digital software to format the disk between loadings, could that be my problem?  Any help in getting one of the later versions going would be much appreciated.

---

### Post by dstew on 2009-06-03
Grub uses your computer's BIOS to access the disk. Older computers have BIOSes that cannot access partitions that go beyond the 1000th cylinder. This is what the error means.

To get around this, you may need to reinstall Ubuntu, and during the install process create a small "boot partition" at the front of the drive that will contain the grub stage 2 file and the linux kernel. It only has to be 50 to 100 megabytes large, which is much smaller than 1000 cylinders.

If you want to try this, you might need to first shrink or move the Windows partitions to give you room at the front of the drive. Use the Vista tools to manipulate the Vista partition. Once you have some unallocated space at the front of the drive, create a 50 to 100 megabyte partition, format ext3, mount point **/boot**. The rest of the installation should be as before.

---

### Post by aharp on 2009-06-04
Thanks so much for the reply.  To clarify, I have 2 HDDs (both 80 gb) with win on the primary and nothing but Ubuntu on the secondary.  I have unplugged the primary drive when installing Ubuntu to make sure I don't inadvertently mess up my windows stuff.  I have tried relocating grub into the mbr, using the following series of commands as suggested elsewhere (from the terminal of course):
sudo grub
find /boot/grub/stage 1
root (hd0,4) the 4 from the results of the prior line
setup (hd0)
quit
Still get error 18 when starting with either the primary disconnected (boot from hd0) or with both drives active (boot from hd1) which is of course the linux drive.  Setting the drive to LBA or large does not make any difference.  

Also, I have installed 8.04 and 9.04 several times and don't find  an occasion during the installation to create the boot partition.    But clearly, I do not understand the partition options presented during the installation process.

Any other idea? Thanks again for your help.

---

### Post by raymondh on 2009-06-04
Hello aharp,

Using this how to for reference

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Try installing GRUB (the commands you used) using the liveCD.  See what it does.  A live session is supposed to NOT mount your partitions.  But just in case you see them in the livesession desktop, go ahead and unmount them from there.

Good luck, let us know.

---

### Post by dstew on 2009-06-04
To create the boot partition you will need to do a lot of manipulation of the disk partitions. I recommend using the [Gparted Live CD]("http://gparted.sourceforge.net/livecd.php") to do it. That way, you do all the difficult partition manipulation separately from installation. It reduces anxiety a lot, I have found.  You will need to move over whatever paritions are already on the disk, to leave space at the front of the drive for a 50 to 100 Megabyte partition. After you move the other partitions over, create the new boot partition out of the unallocated space. Then, once you start the installation, the partitions will be all set up and ready to go.

During installation, you need to choose Manual partitioning, and then select your pre-made small boot partition, assign it the mount point /boot, and format it ext3. You should also have another, large partition for root (mount point '/', format ext3) and a linux swap partition (no mount point or format, just designate "use as swap"). Once you have set up the partitions like this, it will install the grub stage 2 and linux kernel in the /boot partition, and you should no longer get the error 18.

---

### Post by aharp on 2009-06-05
Guys:

Thanks so much for your help.  I'll get this partitioning business straight pretty quick.

---

