---
title: "how to mount external firewire hfs+ hard drive?"
date: 2005-09-19
forum: Hardware &amp; Laptops
---

### Post by AndrewStout on 2005-09-19
Hi folks--

I've searched the forum for answers to this question: I've found several other people asking similar questions, but I haven't found any answers that spell things out enough for me.  (I'm comfortable at the command line, but new to Linux administration.)  The answer must already exist somewhere, but I haven't found it, so please accept my apologies for asking yet again, and if there's a clear how-to somewhere that I didn't find, point me to it.

The question is: How do I mount an external firewire hard drive?  The drive is hfs+ , formatted through my mac; I'm trying to mount it on my new Ubuntu-x86 (Hoary).  I'd like to know both how to mount it once (say, from the command line), and how to set it up to automount (correctly) whenever I hot-plug it in.

It looks like it gets partway there as is: I get a /media/scsidisk, but there's nothing below it.

I have a vague notion that I'll probably need the mount command, and to edit /etc/fstab, but in both cases I'm not sure exactly what to do with them, or what else I might need.  Guidance would be most appreciated!

Thanks in advance,
Andrew Stout

---

### Post by AndrewStout on 2005-09-20
a bit more information:

with a terminal doing `tail -f /var/log/syslog' I plug in the external firewire drive and turn it on.  I see the following in the syslog:

Sep 20 21:29:36 localhost kernel: ieee1394: Error parsing configrom for node 0-01:1023
Sep 20 21:29:36 localhost kernel: ieee1394: The root node is not cycle master capable; selecting a new root node and resetting...
Sep 20 21:29:37 localhost kernel: ieee1394: Error parsing configrom for node 0-00:1023
Sep 20 21:29:37 localhost kernel: ieee1394: Node changed: 0-00:1023 -> 0-01:1023Sep 20 21:29:46 localhost kernel: ieee1394: Node added: ID:BUS[0-00:1023]  GUID[0050770e205d1618]
Sep 20 21:29:46 localhost kernel: ieee1394: unsolicited response packet received - no tlabel match
Sep 20 21:29:46 localhost kernel: scsi4 : SCSI emulation for IEEE-1394 SBP-2 Devices
Sep 20 21:29:48 localhost kernel: ieee1394: sbp2: Logged into SBP-2 device
Sep 20 21:29:48 localhost kernel: ieee1394: Node 0-00:1023: Max speed [S400] - Max payload [2048]
Sep 20 21:29:48 localhost kernel:   Vendor: HDS72252  Model: 5VLAT80           Rev:
Sep 20 21:29:48 localhost kernel:   Type:   Direct-Access                      ANSI SCSI revision: 06
Sep 20 21:29:48 localhost kernel: SCSI device sdc: 488397168 512-byte hdwr sectors (250059 MB)
Sep 20 21:29:48 localhost kernel: SCSI device sdc: drive cache: write through
Sep 20 21:29:48 localhost kernel: SCSI device sdc: 488397168 512-byte hdwr sectors (250059 MB)
Sep 20 21:29:48 localhost kernel: SCSI device sdc: drive cache: write through
Sep 20 21:29:48 localhost kernel:  /dev/scsi/host4/bus0/target0/lun0: [mac] p1 p2 p3 p4
Sep 20 21:29:48 localhost kernel: Attached scsi disk sdc at scsi4, channel 0, id 0, lun 0
Sep 20 21:29:48 localhost scsi.agent[8708]:      sd_mod: loaded sucessfully
Sep 20 21:29:48 localhost udev[8718]: configured rule in '/etc/udev/rules.d/udev.rules' at line 27 applied, 'sdc' becomes '%k'
Sep 20 21:29:48 localhost udev[8718]: creating device node '/dev/sdc'
Sep 20 21:29:48 localhost ieee1394.agent[8730]:      sbp2: already loaded
Sep 20 21:29:48 localhost udev[8799]: configured rule in '/etc/udev/rules.d/udev.rules' at line 27 applied, 'sdc1' becomes '%k'
Sep 20 21:29:48 localhost udev[8799]: creating device node '/dev/sdc1'
Sep 20 21:29:48 localhost udev[8841]: configured rule in '/etc/udev/rules.d/udev.rules' at line 27 applied, 'sdc2' becomes '%k'
Sep 20 21:29:48 localhost udev[8841]: creating device node '/dev/sdc2'
Sep 20 21:29:48 localhost udev[8883]: configured rule in '/etc/udev/rules.d/udev.rules' at line 27 applied, 'sdc3' becomes '%k'
Sep 20 21:29:48 localhost udev[8883]: creating device node '/dev/sdc3'
Sep 20 21:29:48 localhost udev[8920]: configured rule in '/etc/udev/rules.d/udev.rules' at line 27 applied, 'sdc4' becomes '%k'
Sep 20 21:29:48 localhost udev[8920]: creating device node '/dev/sdc4'
Sep 20 21:31:15 localhost kernel: HFS+-fs: unable to find HFS+ superblock
Sep 20 21:31:26 localhost kernel: HFS+-fs: unable to find HFS+ superblock


those last two lines are from my attempts to mount:

andrew@lucky:/dev$ sudo mount -t hfsplus sdc /mnt/airbag/
mount: wrong fs type, bad option, bad superblock on sdc,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

andrew@lucky:/dev$ sudo mount -t hfsplus sdc4 /mnt/airbag/
mount: wrong fs type, bad option, bad superblock on sdc4,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

(same thing with sdc1, sdc2, sdc3)

As I said, I've found other posts with similar problems on the forum, but no solutions...  To me, "error parsing configrom" sounds bad, but I don't know what it means or how to fix it.

Please help!

--Andrew

---

### Post by siplus on 2005-10-15
I googled to find this thread, and it seems pretty recent enough to bump.

I have pretty much the same problem as AndrewSout.

I am running Ubuntu 5.04 (planning on downloading 5.10 in a week or two) and have an 80gb USB hard drive formatted as "Mac OS Extended" which I have assumed to be HFS+

After downloading everything i found with HFS in the title through Synaptic, I still get the error:

root@ubuntu:~ # mount /dev/sda1 /c -t hfsplus
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
missing codepage or other error
In some cases useful info is found in syslog - try
dmesg | tail or so

I'm not sure what to do... I reformatted from "Mac OS Extended (Journaled)" to just regular "Mac OS Extended" hoping that it was just the journalling that was causing problems.

The only thing I get when i pop in the usb drive is:

[taking from a df -h]

/dev/sda9 8.5M 1.4M 7.2M 16% /media/Boot OSX

Now, I have no idea why when i formatted the drive using OS X 10.4's Disk Utility that i would have an 8.5mb partition named 'Boot OSX', but I wouldn't care about such a small partition as long as i had the other 79gb that i could use!

I also tried UFS, but ubuntu can only mount as read-only, apparently

I know that FAT would work, but i want to store files >2gb, so it's not an option

---

### Post by Arto on 2005-10-16
Post the output of executing "dmesg | tail" after the mount attempt (as indicated in the error message).

Notice also that when Ubuntu automounted the OS X boot partition (which will exist on all Mac OS X formatted disks, it seems), it put it under /dev/sda9, but you'd tried to mount /dev/sda1. Perhaps try /dev/sda10, which logically enough should be the actual data partition.

For what it's worth, I had the same trouble with my external HDD, which was formatted by OS X 10.4, and Linux just mounting the useless OS X boot partition instead of the data partition. However, I got it working just fine with Hoary after ditching the automount and adding the following lines to my /etc/fstab file:

[quote=/etc/fstab]
/dev/sda2       /media/macosx   hfsplus  noauto,user,rw 0       0
/dev/sda3       /media/backup   hfsplus  noauto,user,rw 0       0
[/quote]

This mounts both the OS X boot and data partitions. (The device identifiers like "sda2" will vary from computer to computer; and obviously, you'll need to create the two empty directories in /media before attempting a mount.)

---

### Post by siplus on 2005-10-17
I have the problem fixed now, well kinda.

I think what i ended up doing was just reforatting it in OS X without the system information. I was amazed that it automounted when i plugged it in my ubuntu system after that! it's mounted as root-only, but i've no problem sudo'ing.

---

