---
title: "IDE - SATA Incompatibility?"
date: 2011-12-10
forum: Hardware
---

### Post by peabrane on 2011-12-10
I have recently purchased a new system. I have 3 problems which all seem to point to some sort of incompatibility between IDE and SATA drives. I'm probably wrong here, but in my mind I'm convinced that they are connected.

I have a Foxconn A88GMV motherboard with an AMD Phenom II X4 965 processor and 4GB memory. The SATA is 1TB and the IDEs are 500 and 300MB. First I replicated my old system with Ubuntu 11.10 (now 64 bit and not 32) and Windows XP both installed on the SATA drive which is the master boot disc. I don't have any other issues in using the IDE and SATA drives - they mount and are accessible in XP and Ubuntu. The 2 IDE drives are connected to the single IDE connector on the motherboard.

Problem 1. Having replicated my old system, I tried to install Windows 7 (64 bit) on one of the IDE drives. The installer hung at the point it should have finally rebooted into W7. A W7 forum suggested that I install W7 on either IDE or SATA and physically disconnect the other. This allowed the installer to run to completion but when installed on the IDE, W7 wrote to the IDEs MBR and when I put the SATA back, I could not get grub to recognised the W7 partition as bootable. So I put W7 on the SATA and reinstalled grub. So Microsoft know that there is some sort of issue with IDE and SATA here!?! However, I can access both IDE and SATA files and partitions from W7 as I would have expected. But W7 is now installed OK so I'm not bothered about this problem. But it happened and might be relevant to the other 2 problems.

Problem 2. I like to have a cloned Ubuntu partition. So I created one on an IDE drive and copied over all root files except /Proc, /Dev and /sys (noting that there are now /lib32, /lib64 and /run directories). I ran update-grub on the SATA partition and then hand edited grub.cfg for the UUID entries for the new partition - grub never gets the UUID for the "remote" boot image correct in this situation. When I reboot to the new partition, I get /sbin/init not found and a kernel panic. I've used this procedure successfully many times on my old 32 bit system and it is well documented in various threads. I have treble checked that the copy is OK and that the edit to grub.cfg is correct. /sbin/init is absolutely on the IDE partition and I have absolutely got the right UUID.

Problem 3. So, I thought it might just be something with grub on the IDE partition (well it was worth a try). I booted from the live 64 bit Ubuntu 11.10 CD (the DVD drive is SATA), mounted the copied partition, issued mount -o bind commands for /dev, /sys and /proc. This procedure is in many threads and I have used it before quite a few times. But when I try to "chroot" to the new partition, I get /bin/bash not found. This most certainly is on the IDE partition.

All three problems seem to arise when "control" (if you see what I'm trying to say) is transferred from the IDE to the SATA or the other way round. It would seem obvious that the problem might lie in the BIOS settings, but I'm getting out of my comfort zone here. My IDE BIOS settings are Onchip SATA Channel Enabled; Onchip SATA Type - Native IDE (I've also tried AHCI and Legacy IDE - but not RAID because I don't have one) and SATA IDE Combined Mode Enabled. I can't see any other settings that look relevant.

I have read so many threads that I am tying myself in knots (perhaps that is why they are called threads (ha ha)).

I can use all 3 operating systems so this is not a killer problem. But it is annoying and I would prefer to have at least one bootable not on the SATA in case of failure.

Can anyone help me please?

---

### Post by dabl on 2011-12-10
That's a lot of issues for one post!  #-o

I am aware of an Intel design issue, wrt bootable partitions -- on Intel motherboards, the bootable partition needs the "boot" flag set, or the OS can't find it. But your motherboard is a Foxconn so I would not expect that to be your problem.

The only "IDE-SATA" issue that I've ever run into was on an Intel D975XBX motherboard.  On that one, the *buntu Ubiquity installer refused to let grub install on a SATA drive, if a IDE drive was also present.  I had to disconnect the IDE drive, install on the SATA drive, then reconnect the IDE drive and fix /etc/fstab and grub as required.

I would advise you to step back from the situation and rethink your objectives and methods. The general rule for dual booting is "Windows first, Ubuntu second", in order to let grub find the existing OS during installation, and accommodate it, and you violated that one.  Of course there are Windows fixboot and fixmbr routines available from the Repair Console, but you'll have to use Google to get the fine points of how to do that.

Also, there are more than one way to back up your Ubuntu root partition, if you really insist on doing that.  clonezilla comes to mind as a reasonable approach.

I hope this gives you some ideas.

---

### Post by peabrane on 2011-12-11
Hi dabl,

Thanks for your thoughts.

If I knew then what I know now, I would have installed all Windows O/Ss first. But I have done that and got them working with Ubuntu. My remaining problem is to copy a Ubuntu partition which I should be able to do regardless of what Windows systems are installed. I only mentioned the problem installing W7 was because it seemed to bear some sort of similarity to my Ubuntu partition copy problem.

I looked at Clonezilla but one of its requirements is that the destination is larger than the source. Mine is far smaller (it would only be used as a backup).

Interesting you mention the"Boot flag". I looked in the Ubuntu Disk Utility and found that the boot flag was not set for the clone Ubuntu partition so I set it, or tried to. The Disk Utility shows the little rotating circle against the partition which never goes away. Should have mentioned that in my first posting.

Is there another way I can set the boot flag - fdisk or something?

I thought about installing Ubuntu from the live CD onto that partition but I've effectively done that with a file copy and it won't boot. So I'll get the same problem? I feel I'm fiddling around with the symptoms and not finding/understanding the base problem. The boot flag seems like the best lead?

---

### Post by dabl on 2011-12-11
Gparted will let you set the boot flag.  Just highlight the partition, right-click and choose "manage flags", and check the boot flag, then press "Apply" on the top menu. That could be the problem.  Windows by itself definitely won't boot without a boot flag set, although grub should boot Windows whether the boot flag is set or not.

As a cruder approach to copying your OS to the smaller drive, you could use tar, with or without compression.  That will copy it over, but not make it directly bootable.

For Win 7, the procedure to fix the MBR and booting is [[COLOR="SeaGreen"]**here**[/COLOR]](http://support.microsoft.com/kb/927392).

---

### Post by peabrane on 2011-12-13
Hi again dabl,

Thanks for taking the time to respond.

I don't think I want to fix the W7 loader on the boot MBR. That tends to  wipe out grub. I've got the boot all working apart from this cloned  Ubuntu 11.10 on one of the IDE drives.

I could use tar to copy over the files but I'm not sure if that would be any different to what I am already doing. I don't think I can tar /dev, /sys and /proc, so I think it would only get me to the same point.

Gparted does set the boot flag on the IDE partition. However, I'm still not getting any further than /sbin/init not found. None of the files in the /var/log of that partition have changed so I don't know how to pass over any more diagnostic info. I'm not clear on what processing is done from the MBR of the boot disk (SATA) and where continues on the IDE partition. Presumably, the grub.cfg file does not have different parameters between SATA and IDE? I could list the result of fdisk -l and the appropriate bit of grub.cfg just in case I can't see the wood for the trees but I've check and double checked it so many times.

I suppose I could disconnect the SATA and install Ubuntu onto the IDE but that would set up the MBR of the IDE disk which would be ignored when I reintroduced the SATA. There is either something basic wrong with my computer with the disk setup or some vital component of Ubuntu missing from my copy.

---

### Post by westie457 on 2011-12-14
@peabrane

Having read through the thread a couple of times to try to understand what you want to do, I have come to the conclusion that you want Grub on one IDE drive to boot from without Grub on a SATA drive taking over. Is that correct?

How about if you purge Grub from all hard drives and reinstall Grub to just one IDE drive will that work for you? 

To purge Grub and reinstall go to [here]("http://ubuntuforums.org/showthread.php?t=1581099") for guidance, chrooting to each hard drive as necessary to remove Grub and lastly installing to the drive you wish to boot from.

Hope this helps.

---

### Post by peabrane on 2011-12-14
Hi Westie457,

Thanks for the response.

Not quite the right reading of what I was trying to achieve. I did not have any concept of having separate grub loaders on the SATA and the IDE. I was hoping to get the grub on the SATA to connect to the IDE partition and start up the Ubuntu on that. But having separate grub loaders is an interesting thought.

So perhaps a solution for me is to abandon attempting to boot from the SATA to an IDE partition. Instead, if I install grub into the MBR of the IDE drive, I can use the BIOS to change the boot order so that when I want to use the Ubuntu on the IDE drive, I boot from the IDE disk rather than the SATA? After all, the IDE ubuntu partition is only an emergency fall-back, this would not really be a problem.

I'll give this a try over the next 3 or 4 days and report back.

---

### Post by westie457 on 2011-12-14
> **peabrane said:**
> Hi Westie457,

Thanks for the response.

Not quite the right reading of what I was trying to achieve. I did not have any concept of having separate grub loaders on the SATA and the IDE. I was hoping to get the grub on the SATA to connect to the IDE partition and start up the Ubuntu on that. But having separate grub loaders is an interesting thought.

So perhaps a solution for me is to abandon attempting to boot from the SATA to an IDE partition. Instead, if I install grub into the MBR of the IDE drive, I can use the BIOS to change the boot order so that when I want to use the Ubuntu on the IDE drive, I boot from the IDE disk rather than the SATA? After all, the IDE ubuntu partition is only an emergency fall-back, this would not really be a problem.

I'll give this a try over the next 3 or 4 days and report back.

Things are getting clearer now, just a slightly lighter shade of mud.

If using one of the IDE drives as a fall back it will need its own Grub. To use the SATA drive to look at the IDE drive that will need its own Grub as well.

Think about this to check if my own thinking is right. To get Grub on the IDE drive the Sata drive must be disconnected and Grub must be installed using a LiveCD. After that reconnect the Sata drive and again boot into the Live Desktop and this time chroot into the SATA drive using the guide linked to earlier, install Grub and to be on the safe side run ```
sudo update-grub
``` just incase it does not update automatically. 

This should give you the choice of booting into the Sata drive by default or into the IDE drive if you wish.

If you do not update Grub on the IDE drive the IDE drive will not even know the Sata drive is there.

Is that a better understanding of what you want?

---

### Post by peabrane on 2011-12-17
Thanks again to Westie457 for the advice.

Problem now solved although I had to diverge from Westie457's suggested path.

Firstly, my theory that I could boot from the IDE to get to the reserve Ubuntu partition would fail because my Foxconn motherboard will only boot from the SATA. It can boot from an IDE drive but only if there are no SATA disks present which would not have solved my problem.

As suggested, I disconnected the SATA, but I could not install grub from the Live CD to the IDE partition. As I had previously failed dismally to install grub to an IDE partition when running Ubuntu on a SATA partition, so I failed similarly to install grub to an IDE partition when running Ubuntu from a SATA drive CD. The only solution I could think of was to do a full install of Ubuntu onto the IDE partition (with the SATA removed). From here I could go back to Westie457's suggestion. Once satisfied that the IDE partition booted OK, I reconnected the SATA, booted to my SATA Ubuntu partition and ran update-grub. I can now boot from the SATA disk and successfully get to the IDE Ubuntu partition from the grub menu.

I still don't understand why I can't install grub to an IDE drive when running on a SATA disk or CD (chroot fails - can't find /bin/bash), but I've got to where I wanted to be. So many thanks!

---

### Post by westie457 on 2011-12-17
Glad you got it working and happy to have helped.

Could you mark this as solved please, using 'thread tools'.

---

