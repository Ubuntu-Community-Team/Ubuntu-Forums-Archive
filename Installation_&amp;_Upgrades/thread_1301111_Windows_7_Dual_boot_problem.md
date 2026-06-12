---
title: "Windows 7 Dual boot problem"
date: 2009-10-25
forum: Installation &amp; Upgrades
---

### Post by RavensKrag on 2009-10-25
I have windows 7 currently installed and am trying to dual boot with Ubuntu.  I have used ubuntu before, dual booting with Vista.  

However, after installing Windows 7, the partition does not appear in gparted or the installer of the ubuntu 9.10 install disk.  Strange thing is, the partitions are viewable under fdisk as well as the palimpset disk utility.  

I've been working on this for 3 days and have not found a way to get this configuration to work.  Can anyone help me with this problem?  I need windows for some projects that I am working on and such otherwise I would have given up by now and just used Ubuntu.  

Please tell me what information would be useful in solving this problem.  Thanks.

---

### Post by oldfred on 2009-10-25
The quick answer with Karmic is that grub2 should find windows and set it up to boot.

Even still, the latest Karmic Alpha needs some help to find other os.
sudo apt-get install os-prober
sudo os-prober
sudo update-grub2

If that does not work then we need to see your system configuration. This script will list everything:

Boot Info Script 0.32 courtesy of forum member meierfra
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)
Instructions
[http://ubuntuforums.org/showpost.php?p=6725571&postcount=3](http://ubuntuforums.org/showpost.php?p=6725571&postcount=3)
cd to directory saved to:
chmod 755 boot_info_script032.sh
sudo ./boot_info_script032.sh
or  as example if on desktop
sudo bash ~/Desktop/boot_info_script*.sh
This will create a RESULTS.txt file in the same directory. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by RavensKrag on 2009-10-25
I believe that you misunderstood my problem.  This is not a GRUB2 problem.. 
(well, not yet anyway)

As of yet I am not yet even able to install Karmic onto my computer because the installer views the hard disk as unallocated even though I can run Windows 7 off of it.

---

### Post by wilee-nilee on 2009-10-25
> **RavensKrag said:**
> I believe that you misunderstood my problem.  This is not a GRUB2 problem.. 
(well, not yet anyway)

As of yet I am not yet even able to install Karmic onto my computer because the installer views the hard disk as unallocated even though I can run Windows 7 off of it.

Have you tried just installing and seeing if the partition gui sees everything and allows you to partition as you like. You can stop the install at this point as long as you don't partition I believe. There must also be a partitioning tool in W7 that will leave a blank area for Karmic.

---

### Post by Mark Phelps on 2009-10-25
> **RavensKrag said:**
> However, after installing Windows 7, the partition does not appear in gparted or the installer of the ubuntu 9.10 install disk.  Strange thing is, the partitions are viewable under fdisk as well as the palimpset disk utility.  

If you installed Windows 7 to an unformatted drive, it created two partitions, not one as in Vista.  The first is a new BOOT partition -- which the Ubuntu installers might not be able to see.

IF you go ahead and "install anyway", you run the risk of corrupting your Windows 7 installation and/ot boot.

Would be better to use the built-in Disk Management utility to shrink the Windows 7 second partition to make room for Ubuntu.  THEN boot with the Ubuntu CD and see if it sees the unallocated space.

If not, you could try downloading and burning a GParted LiveCD from distrowatch.com, partitioning the unallocated space using it and THEN see if the Ubuntu installer sees those partitions using Manual Partitioning.

---

### Post by RavensKrag on 2009-10-26
@wilee-nilee
> **wilee-nilee said:**
> Have you tried just installing and seeing if the partition gui sees everything and allows you to partition as you like. You can stop the install at this point as long as you don't partition I believe. There must also be a partitioning tool in W7 that will leave a blank area for Karmic.

Thanks for the suggestion, but I tried using the W7 utility already, as that is how I had dual-booted Vista and Ubuntu 9.04.  I can not view the W7 partition in the Ubuntu installer or GParted in the Ubuntu live CD.





@Mark Phelps
> Would be better to use the built-in Disk Management utility to shrink the Windows 7 second partition to make room for Ubuntu. THEN boot with the Ubuntu CD and see if it sees the unallocated space.
As mentioned above, this did not work, and I had already tried it before positing this question. 


> 
If not, you could try downloading and burning a GParted LiveCD from distrowatch.com, partitioning the unallocated space using it and THEN see if the Ubuntu installer sees those partitions using Manual Partitioning.
Is the GParted LiveCD any different from the GParted in the Ubuntu LiveCD?  I assume this means install W7 as normal, then use GParted.  However, if GParted in the Ubuntu LiveCD can't see the partition, what would be so different to make the GParted LiveCD see the W7 partition? 

Also, wouldn't this still leave the problem of the Ubuntu installer not being able to see the partition(s)?

---

### Post by oldfred on 2009-10-26
Did you by any chance convert to dynamic disk or LVM? This is a windows only partitioning scheme that maybe the older gparted in the installer does not even see?

---

### Post by RavensKrag on 2009-10-26
> **oldfred said:**
> Did you by any chance convert to dynamic disk or LVM? This is a windows only partitioning scheme that maybe the older gparted in the installer does not even see?

How would I be able to tell what the partitioning scheme is? Also, as I said before, the partitions are visible under the disk utility, just not GParted or the installer.

---

### Post by oldfred on 2009-10-26
Try to boot info script I recommended in post #2. It tells a lot about how the system is configured.

---

### Post by RavensKrag on 2009-10-27
That probably wouldn't do too much good now as I currently don't have the Windows 7 partition at all.  I just installed Ubuntu and I am running W7 in a virtual machine (ew...).

I still would like a fix for my original problem though.

---

### Post by RavensKrag on 2010-01-17
If anyone else is encountering this problem, I have not found a solution, but believe that the problem is because the W7 partitioner does not round to cylinders like GParted does.  

When trying to re-partition after a "failed" partitioning in W7, make sure to create a new partition table in GParted.  I had to do that to even get my Vista and Ubuntu setup back.  

If someone else tries creating a new partition table, and that method works, kindly post back here for others to follow.  I will not be trying that because W7 will not work out on my computer for other reasons.

---

### Post by Leophys on 2010-02-10
Ok, if it can comfort you, I have the same problem with my new hp laptop. It has win 7 preinsalled and it uses the dynamical disk management.

I think (also because the same Parted told it) that THE problem is this dynamic management, but I don't have the solution too :confused:

PLEASE, I need ubuntu to work but I wouldn't like to erase win 7...anyone got the solution?

Thanks a lot

---

### Post by scotthep on 2010-02-16
I have the exact same problem with an Acer Aspire 1410 laptop/netbook machine. I have WIndows 7 Home Premium installed (x86) and have shrunk the partitions using the disk utility in Win7 but nothing within Ubuntu 9.10 will see the partitioning scheme.

I have tried using fdisk, and as a previous poster stated it can see the partitions, but GParted and whatever the installer uses will not recognize any of them.

I heard mention of problem with AHCI modes for the SATA controller, but I'm not sure if that applies here since the disk is "visible" just not usable. I also tried using the gptsync utlity but that did nothing and stated that no gpt table is present.

At a total loss.

---

### Post by gm_navy on 2010-03-07
I dont think your problem is one of dual boot. There seems to be a fundamental problem in Windows 7 with respect to living peacefully with secondary drives, and the problem appears to be connected with a not so smart idea of Microsoft called 'Smart Monitoring'. This Smart monitoring is supposed to continuously check the physical health of your hard disk drive -such things like RPM, access rate etc, and warn you when your hard disk is getting sluggish. The trouble is it overreacts to the slightest parameter issue, and goes into some endless loop.

The solution probably lies in going to BIOS and just disabling SMART monitoring. If you are really concerned about your hard disk drive's health, download gsmartcontrol for free. It serves the same purpose - of course off line, which is good enough.

---

