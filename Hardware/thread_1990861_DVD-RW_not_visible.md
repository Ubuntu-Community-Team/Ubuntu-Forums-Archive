---
title: "DVD-R/W not visible"
date: 2012-05-29
forum: Hardware
---

### Post by crptonx on 2012-05-29
Hi there. So, let me preface this by saying that the drive in question was working. I used it to install 11.10 before upgrading to 12.04. I also used it to install the Win7 dual boot partition. 

I'm running 12.04 64bit.

The drive is a Samsung SH-222. I can no longer access the drive in Windows or Ubuntu and I can't even use bootable CD/DVD even though it appears in my BIOS launch options. The drive is receiving power and opens, but if a disc is loaded I get no response (in either OS). 

Here's fstab - 
> # /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=8f568673-81d3-40f0-aade-3f77fb65b151 /               ext4    errors=remount-ro 0       1
# /windows was on /dev/sda4 during installation
UUID=79753E43529B03B9 /windows        ntfs    defaults,umask=007,gid=46 0       0
# swap was on /dev/sda5 during installation
UUID=4d558b02-e348-4010-bbce-8a5ff8130c8a none            swap    sw              0       0
Here's lspci...
> 00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.4 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 5 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation H61 Express Chipset Family LPC Controller (rev 05)
00:1f.2 IDE interface: Intel Corporation 6 Series/C200 Series Chipset Family 4 port SATA IDE Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
00:1f.5 IDE interface: Intel Corporation 6 Series/C200 Series Chipset Family 2 port SATA IDE Controller (rev 05)
02:00.0 Ethernet controller: Atheros Communications Inc. AR8151 v2.0 Gigabit Ethernet (rev c0)My main HDD is also SATA and is being read fine. I'm at a loss of why this is happening, not just in Ubuntu, but system wide. 

Help would be greatly appreciated. This may have happened a week ago or a month ago, I'm really not sure. I so rarely use the DVD drive that I haven't had any reason to try, so I can't really pinpoint where/when it stopped working, sorry. If you need any additional information, I'll be more than happy to give it.

Thanks in advance.

---

### Post by carl4926 on 2012-05-29
Sounds like it's Jeffed.

---

### Post by crptonx on 2012-05-29
> **carl4926 said:**
> Sounds like it's Jeffed.

I'm guessing Jeffed is toasted? It's pretty new (Installed Feb of this year for the new box).

---

### Post by carl4926 on 2012-05-30
Re-seat all the connections
That means pull them and re-connect them, making sure they are good.

---

### Post by crptonx on 2012-05-31
> **carl4926 said:**
> Re-seat all the connections
That means pull them and re-connect them, making sure they are good.


Hi carl, 
First, I appreciate your time. 

I had already reseated the connection, but I tried again anyhow. No luck.

Any other suggestions?

---

### Post by carl4926 on 2012-05-31
> **crptonx said:**
> Hi carl, 
First, I appreciate your time. 

I had already reseated the connection, but I tried again anyhow. No luck.

Any other suggestions?
Honestly
It sounds like it needs to be replaced. Perhaps you still have the purchase receipt for warranty?

---

### Post by crptonx on 2012-05-31
> **carl4926 said:**
> Honestly
It sounds like it needs to be replaced. Perhaps you still have the purchase receipt for warranty?

Yeah, I do have it. I was hoping to avoid it, but some things just can't be avoided. 

Thanks.

---

### Post by madsmaddad on 2012-06-23
I also have this dvd model SH-222. I bought two of them. 

I am using Kubuntu 12.04. 

In dmesg I get the following: 


peterm@peterm-desktop:~$ dmesg | grep scsi | grep TSSTcorp
[    3.517846] scsi 2:0:0:0: CD-ROM            TSSTcorp CDDVDW SH-222BB  SB00 PQ: 0 ANSI: 5
[    4.205586] scsi 3:0:0:0: CD-ROM            TSSTcorp CDDVDW SH-222BB  SB00 PQ: 0 ANSI: 5

peterm@peterm-desktop:~$ dmesg | grep scsi[0-5]\ :
[    2.573403] scsi0 : pata_sis
[    2.573563] scsi1 : pata_sis
[    3.171061] scsi2 : sata_sis
[    3.173867] scsi3 : sata_sis
peterm@peterm-desktop:~$

cut from dmesg:

[    3.492161] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 3F0)
[    3.500478] ata3.00: ATAPI: TSSTcorp CDDVDW SH-222BB, SB00, max UDMA/100
[    3.516266] ata3.00: configured for UDMA/100
[    3.517846] scsi 2:0:0:0: CD-ROM            TSSTcorp CDDVDW SH-222BB  SB00 PQ: 0 ANSI: 5
 *** [    3.518932] ata3.00: exception Emask 0x100 SAct 0x0 SErr 0x0 action 0x6
[    3.518946] ata3: hard resetting link
[    3.836071] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 3F0)         *** repeat of above
[    3.860223] ata3.00: configured for UDMA/100                                         *** repeat of above
[    3.860669] ata3: EH complete                                                                   ** OK now
[    3.862759] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    3.862765] cdrom: Uniform CD-ROM driver Revision: 3.20
[    3.863094] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    3.863358] sr 2:0:0:0: Attached scsi generic sg1 type 5

[    4.180076] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 3F0)
[    4.188225] ata4.00: ATAPI: TSSTcorp CDDVDW SH-222BB, SB00, max UDMA/100
[    4.204224] ata4.00: configured for UDMA/100
[    4.205586] scsi 3:0:0:0: CD-ROM            TSSTcorp CDDVDW SH-222BB  SB00 PQ: 0 ANSI: 5
[    4.206602] ata4.00: exception Emask 0x100 SAct 0x0 SErr 0x0 action 0x6
[    4.206614] ata4: hard resetting link
[    4.524071] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 3F0)
[    4.548230] ata4.00: configured for UDMA/100
[    4.548640] ata4: EH complete
[    4.550717] sr1: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    4.551018] sr 3:0:0:0: Attached scsi CD-ROM sr1
[    4.551277] sr 3:0:0:0: Attached scsi generic sg2 type 5
[    4.569101] ata4.00: exception Emask 0x100 SAct 0x0 SErr 0x0 action 0x6
[    4.569118] ata4: hard resetting link

Most of those messages about the ata4 repeat throughout the dmesg output. as it tries again after the hard reset. 

These dvd writers work in XP and also in fedora 17, so I think it is a kubuntu problem rather than a hardware problem.  I changed from  an IDE cd drive and IDE dvd r/w to these SATA drives. 

I appreciate any thoughts about fixes/cures.

---

