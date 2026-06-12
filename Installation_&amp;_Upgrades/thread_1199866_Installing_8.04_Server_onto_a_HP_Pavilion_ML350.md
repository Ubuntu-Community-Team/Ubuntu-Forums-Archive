---
title: "Installing 8.04 Server onto a HP Pavilion ML350"
date: 2009-06-29
forum: Installation &amp; Upgrades
---

### Post by wjhildreth on 2009-06-29
Hello all,

I have a few machines at my facility which can be used to install Ubuntu on.  The machine that I started with is a HP Pavilion ML350.

This machine contains a HP Smart Array Controller 6400 and on this controller I have two 40GB drives that I have made into a RAID 1 and a Quantum SDLT Tape drive. Additionally, the machine has an HP Ultra 3 controller with no attached devices.

The boot order has been set to (1) IDE CDROM (2) Hard Drive C: in the BIOS

The Boot Controller order has been set to HP Smart Array 6402 controller in the BIOS

The OS Selection has been set to Linux in the BIOS.

Booting from the 8.04 server install CD and installation seems to go just fine.  I instructed the installer to use the entire disk. I selected the 36.4 GB Compaq Smart Array. When the install reaches the point of writing the boot loader I get this message:

"The following other operating systems have been detected on this computer: Windows NT/2000/XP
... "

Well there should be no other operating systems on the machine.  I selected to install the GRUB Boot loader to the master boot record.

On the system reboot I get the following messages:

Attempting to boot from CDROM (it fails because there is no ROM in the drive to boot from.)

Attempting to boot from Hard Drive C: (it hangs here)

:-(

So I suspect that the problem lies with the master boot record on the hard disks, is that correct?

If so, how can I replace the master boot record?  Or is there somewhere else that I need to be looking?

Warm Regards,

Joe

---

### Post by ronparent on 2009-06-29
That could be the correct diagnosis. It is unclear if you can boot from a live cd (standard install cd). If so boot the live cd and open a terminal. In the terminal run **sudo grub**. From the grub prompt enter **find /boot/grub/stage1**. The output from this will tell you where your ubuntu is installed in grub terms. Enter that output as **root (hdx,y)** instructing grub where to find the install. Next enter **setup (hdx)** to write the mbr to the drive of your install. If this is your problem it should now be solved and you should be able to boot to the grub menu.

PS: If you can boot a terminal from your server cd, that should serve the same purpose.

---

### Post by wjhildreth on 2009-06-29
ronparent:

Thanks for your input.

If I try to boot from a live CD (8.10 desktop) I end up with some sort of busybox termial....  Not sure what to do with that, since sudo and grub both are not available.

How do I boot to a terminal with the 8.04 server install cd, or do I need to download a different one to be able to do that?

Regards,

Joe

---

### Post by ronparent on 2009-06-29
Joe:

I frankly do not know of the capabilities or features of the server cd, but, I can't imagine it would not allow you to boot to a terminal. You might have to abort the install process prior to commiting to any changes to your system to drop to a terminal mode? The live cd for sure loads a terminal thru the gui menu (any version will do).

Busybox supports the **su** command in place of **sudo**. You could also try that to see if it brings up grub.

Regards, Ron

---

### Post by wjhildreth on 2009-07-01
Ron,

Thanks again for all your help.  You gave me enough to go on.  I downloaded the alternate CD and used the terminal from there, but in hindsight I suppose it was available on the rescue option from the Server CD.

When I installed the server, I told it to use all available space on /dev/cciss/c0d0 (this point to my 36GB RAID I drive)

When grub installed I have no Idea where it wrote the boot loader.  I re-wrote the boot loader to /dev/c0d0 and was able to boot into grub.  Making progress anyway.

My main installed partition was located at /dev/c0d0p1 and swap located at /dev/cciss/c0d0p5.  I found this information by issuing a fdisk -l command.

I started a terminal and mounted /dev/cciss/codop1 on /

Next I took a look at the menu.lst file.  The entries pointed out that the System was to boot from (hd2,0).  Not knowing how /dev/cciss/c0d0p1 related to the hd numbering system, I changed it to (hd0,0) thinking that maybe the RAID controller was the first hard disk.

The good news is that I am able to boot into the system now, but I would like to know more about why things happened the way they did.  Any ideas on where to look or read up on it?

Regards,

Joe

P.S.  Thanks again for your help.

---

### Post by wjhildreth on 2009-07-01
One other note, while booting the SCSI BIOS lists the two drives as HD1 and HD2, I am guessing these are (hd0) and (hd1) in the grub file?  Where would grub or the installer get (hd2) from?

Regards,

Joe

---

### Post by wjhildreth on 2009-07-01
The thread can be marked solved since I can boot the system now.

However, After formatting the SCSI Disks using the SCSISelect tools and creating a new RAID 1 and re-installing teh system, I had the same exact issues.

I suppose next is to see if there is a bug in the installation of GRUB or something.  Now I am a little over my head.

Thanks for all the help.

Regards,

Joe

---

### Post by ronparent on 2009-07-03
Joe

The following site, although it deals primarily with dual boot issues, conveys some general understanding of grub: [http://members.iinet.net/%7Eherman546/index.html](http://members.iinet.net/%7Eherman546/index.html)

It is new and I haven't read it yet, but it replaces Herman's prior 'grub page' which gave an excellent review of the topic. So far you have instinctively done some of the right things. Since, typecal of computer things, you have been forced to do things over and over again untile you get it exactly right you are now becoming an expert in your own right. Good luck.

Ron

---

