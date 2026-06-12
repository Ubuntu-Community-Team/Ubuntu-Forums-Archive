---
title: "Error 21 on Ubuntu 9.04, how do I boot up???"
date: 2009-11-05
forum: Installation &amp; Upgrades
---

### Post by giyad on 2009-11-05
I've just installed Ubuntu (my first time installing Linux) and I've got my first error. Let me describe my system a bit first. I have a:

EVGA 680i SLI motherboard
4 SATA drives (150GB Raptor with Windows Vista, 64GB SSDnow V with Ubuntu, and 2x1TB RAID-0 WD Caviars)
8GB DDR2 RAM (4x2gb OCZ)

That should be all the info you need right?

Ok, so I installed Ubuntu on the SSD drive (/dev/sdc), its brand new and first install. Everything went smoothly, I downloaded the Ubuntu 64-bit Jaunty (9.04) and burned it to disc, then stuck it in the drive and rebooted. Selected "Install Ubuntu" and followed the steps. When it was done it told me to reboot and remove the disc. I did that.

Now, when I turn on my computer, it says:
"Grub loading stage 1.5


Grub loading, please wait.....
Error 21"

It doesn't give me an option to boot into windows, and I can't boot into Ubuntu. So I have two questions.

1) How do I solve this so that I can boot into Ubuntu? I'm able to use the live cd and boot in, that works. 
2) How do I boot into Windows (/dev/sda)??

Please bear with me I'm new to linux. How can there be an error here, grub should have been installed properly!

I've followed the instruction [here]("http://ubuntuforums.org/showthread.php?t=224351"), but this didn't work for me, just letting you know what I've tried. In the process I found that the stage1 file points to (hd2,0).

**UPDATE - SOLVED**:

*NOTE:  I'm not actually marking this as solved until we can figure out why it didn't boot up in the first place.

I used Super Grub to fix the boot record, and now everything works, but it (FOR SOME REASON, i think because I had supergrub "fix boot of GNU/Linux") broke my RAID, so i lost everything on there! Good thing I have it backed up, but thats lame! On top of that, I still don't understand why Ubuntu didn't work from a clean install on a separate free disc!??? This doesn't make sense...

Any ideas??

---

### Post by dstew on 2009-11-05
The usual problem here is that the installer, which runs under a Linux OS, can see disks that the BIOS does not see, or that the BIOS disk enumeration is different than the Linux disk enumeration. When grub is installed, Linux is running from the Live CD, but when the real grub runs, it looks at the system BIOS for the disk enumeration. The grub shell, which runs from the Live CD, is also running under Linux, and sometimes the disks are enumerated differently.

I assume you tried the rest of the commands to re-install grub:```
root (hd2,0)
setup (hd0)
```

At present, your system has the stage1 in the MBR of the boot disk, and the stage1.5 in the boot sector of the boot disk, but the stage1.5 file cannot find the disk that was targeted during the install process. It might be looking for the third disk (hd2), but maybe the BIOS is only reporting 2 disks, and so it fails. Possibly the 1T disks are giving your BIOS a problem. Maybe Linux can count the 1T disks, but the BIOS cannot, I don't know...

Anyway, grub will need to be re-installed with the correct disk enumeration. You can try different enumerations like root (hd0,0) or (hd1,0) and see if it works. Or, you can analyze your system to see exactly what has happened, and work from a position of knowledge.

There is a [script]("http://sourceforge.net/projects/bootinfoscript/") you can run that will analyze your boot setup. Post the output of the script and we will see what we can come up with.

---

### Post by giyad on 2009-11-05
> **dstew said:**
> 
I assume you tried the rest of the commands to re-install grub:```
root (hd2,0)
setup (hd0)
```

Possibly the 1T disks are giving your BIOS a problem. Maybe Linux can count the 1T disks, but the BIOS cannot, I don't know...

Anyway, grub will need to be re-installed with the correct disk enumeration. You can try different enumerations like root (hd0,0) or (hd1,0) and see if it works. Or, you can analyze your system to see exactly what has happened, and work from a position of knowledge.



Well, like I said I got it to work by using supergrub, but that broke my RAID, and even though I have it backed up, I don't see why it would?

I do have a question about running the commands
```
root (hd2,0)
setup (hd0)
```

I did try that, but... I assumed that hd0 is my windows partition, since that is /dev/sda.  So, when I tried that earlier, I ran:
```
root (hd2,0)
setup (hd2)
```

that ran successfully, but didn't solve my problem.  Could that have been my mistake??  The thing is hd0 should be my 150GB Raptor drive no?

---

### Post by dstew on 2009-11-05
> I assumed that hd0 is my windows partition, since that is /dev/sdaProperly, (hd0) might be the disk on which you have a Windows partition. The command setup (hd0) would install grub stage1 into the MBR of disk 1. The MBR is not part of any partition. There is one MBR per disk. But, what is disk 1 to Linux, might not be disk 1 to the BIOS, especially if you have a RAID. (hd0) is not always equal to /dev/sda.> The thing is hd0 should be my 150GB Raptor drive no?Not necessarily. It all depends on how the BIOS enumerates the disks.

My trick for seeing the BIOS enumeration is to have a grub boot floppy. I boot it, and grub is running in its *native state*, as it would *before any operating system is loaded*. Grub has quite a bit of functionality. Besides booting, grub has lots of commands that will let you examine disks. I use the grub **geometry** command to figure out which disk is (hd0), which is (hd1), and so forth. Then, I install grub onto the hard disk using this information, which will exactly match what the grub boot loader will see at boot time.

---

### Post by presence1960 on 2009-11-05
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by giyad on 2009-11-05
> **presence1960 said:**
> Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

Thanks, but I'm not sure how useful that would be since I am now able to boot into Ubuntu...?

---

