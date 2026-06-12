---
title: "3ware RAID problems on Breezy"
date: 2006-01-24
forum: Hardware &amp; Laptops
---

### Post by lhoriman on 2006-01-24
Does anyone have the monitoring tools (3DM or CLI) working for a 3ware 7006-2 RAID card with Breezy?  If you have success, can you post the 3ware parts of your dmesg here?

I have a 7006-2 with a pair of 250GB drives mirrored.  Breezy installed and boots just fine.  However, the CLI tool tells me:

root@wasabi:~/tmp# ./tw_cli
3ware CLI> info
List of controllers
-------------------
No controller found.
Make sure appropriate 3Ware device driver(s) are loaded.
3ware CLI>

Also, I get this in dmesg:

scsi_proc_hostdir_add: proc_mkdir failed for <NULL>

There are a few interesting articles on the web about this error, but they all describe problems booting, which is obviously not my problem.  However, if I were to take a WAG at what's going on, perhaps the tw_cli tool requires entries in /proc that are missing for some reason?  The articles I found:

[https://bugzilla.ubuntu.com/show_bug.cgi?id=2710](https://bugzilla.ubuntu.com/show_bug.cgi?id=2710)
[http://www.ubuntuforums.org/showthread.php?t=111741](http://www.ubuntuforums.org/showthread.php?t=111741)
[http://www.ubuntuforums.org/showthread.php?t=65495](http://www.ubuntuforums.org/showthread.php?t=65495)

My uname -a:

Linux wasabi 2.6.12-10-686-smp #1 SMP Mon Jan 16 18:39:17 UTC 2006 i686 GNU/Linux

A bit of my boot msg:

[4294674.994000] SCSI subsystem initialized
[4294674.995000] 3ware Storage Controller device driver for Linux v1.26.02.001.
[4294674.995000] ACPI: PCI Interrupt 0000:02:01.0[A] -> GSI 48 (level, low) -> IRQ 48
[4294674.995000] scsi_proc_hostdir_add: proc_mkdir failed for <NULL>
[4294676.985000] scsi0 : 3ware Storage Controller
[4294676.985000] 3w-xxxx: scsi0: Found a 3ware Storage Controller at 0x3080, IRQ: 48.
[4294676.985000]   Vendor: 3ware     Model: Logical Disk 0    Rev: 1.2
[4294676.985000]   Type:   Direct-Access                      ANSI SCSI revision: 00

Does anyone have any ideas?

One other thing - my write performance sucks with this setup.  I also have a plain old 80GB drive attached to the on-board IDE bus in this machine.  When I test with this:

time sh -c 'dd if=/dev/zero of=/tmp/testfile bs=128k count=8k && sync'

It's 3-4 times slower on the RAID array than it is on the IDE disk.  Furthermore, executing that on the RAID array causes HUGE cpu load.  It seems as if it's not using DMA.  Some output that might be useful:

root@wasabi:~# hdparm /dev/hda
/dev/hda:
 multcount    =  0 (off)
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 16383/255/63, sectors = 156301488, start = 0
root@wasabi:~# hdparm /dev/sda
/dev/sda:
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 896/64/32, sectors = 490232704, start = 0
root@wasabi:~#

Help!

Thanks in advance,
Jeff

---

