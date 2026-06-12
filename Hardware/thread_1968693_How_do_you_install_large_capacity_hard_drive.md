---
title: "How do you install large capacity hard drive?"
date: 2012-04-29
forum: Hardware
---

### Post by Elzenbr8 on 2012-04-29
I've read somewhere, that installing TB hdd is tearing.
I bought one to add more space, and yes, I can't make it work alongside with my ubuntu.
I wonder why, and how...

So, how do you install TB hard drive alongside with ubuntu?
Please let me know your experiences about this....

> System specification:
Mobo: GA-MA790GP-UD4H
[http://www.gigabyte.us/products/product-page.aspx?pid=3003&dl=1#sp](http://www.gigabyte.us/products/product-page.aspx?pid=3003&dl=1#sp)

Disk Drives:[INDENT]80 GB Maxtor, PATA, as system (ubuntu 11.10 64bit)
2 TB WD Caviar Green (WD20EARX), SATA, unformatted
[http://www.wdc.com/global/products/specs/?driveID=933&language=1](http://www.wdc.com/global/products/specs/?driveID=933&language=1)
[/INDENT]Optical Drive:[INDENT]SATA DVD drive
[/INDENT]Problem:
Installing WD20EARX (not as system).

---

### Post by MonkeyPaw on 2012-04-29
What about it doesn't work? If you're using an older PC, there's a chance the BIOS may not be recognizing the drive. If the BIOS doesn't see it correctly, no OS is going to either. 

If all you are wanting to do is add the drive to your storage volumes and not put an OS on it, then it should be very simple.

What version of Ubuntu are you using, and what kind of hardware do you have? Mainly looking for motherboard model name.

---

### Post by haqking on 2012-04-29
I use a screwdriver ;)

NO seriously, if your BIOS dont support it then it wont see it.

How old is machine ? What filesystems you using, can you see it from Live CD ?

---

### Post by Bandit on 2012-04-29
> **haqking said:**
> I use a screwdriver ;)

NO seriously, if your BIOS dont support it then it wont see it.

How old is machine ? What filesystems you using, can you see it from Live CD ?

I was going to mention I used rails to isntall mine.. hehe

But yea Ditto to what Haqk mentioned.
But if it is installed and able to see it, you may have to low level format it since you didnt mention the brand or model of the drive hard to tell. But you may just need to do a basic format, I suggest Ext4 FS and then chown of the drives folder over to your account so you can read and write to it.

Cheers..
Joe

---

### Post by Elzenbr8 on 2012-04-30
Thanks for your reply all.

I'm using gigabyte mainboard, it's GA-MA790GP-UD4H.[INDENT] Official spec available here:
[http://www.gigabyte.us/products/product-page.aspx?pid=3003&dl=1#sp](http://www.gigabyte.us/products/product-page.aspx?pid=3003&dl=1#sp)
[/INDENT]And hdd is WD Caviar, WD20EARX.[INDENT] Official spec available here:
[http://www.wdc.com/global/products/specs/?driveID=933&language=1](http://www.wdc.com/global/products/specs/?driveID=933&language=1)
[/INDENT]And I used my old hdd 80 GB (PATA) for ubuntu. Currently I downgraded to 11.10.
Well, I think this should work. Since I read some people attach more than 2TB successfully. However, some not.

My BIOS can detect it, but I don't know why won't show it. And ubuntu keep saying softreset.
Should I unplug my old one and attach only the new one?

Any idea?

---

### Post by Elzenbr8 on 2012-04-30
Oh, well..
It's really hauting me. I've never thought adding additional space would be hard like this.
Maybe I need to make it as an accessory before got me insomnia again and again, haha....

---

### Post by Elzenbr8 on 2012-04-30
There it is, I remove my old one and add only this wd20earx and optical drive connected on sata controller.
Then, I swit ch  sata type as ide from by bios. Now, both are on the ide list. But, detected capacity is 0 MB.
With this, I think there is no way to make it works with ubuntu, neither do with another OSs.

mhdd (ubcd), said the drive is not ready. whil e my ubuntu keep saying softreset over and over again.

---

### Post by MonkeyPaw on 2012-04-30
I think you'll want AHCI, not IDE, though that mainly depends on what the BIOS was set at on last install so you can boot. Once you boot into Ubuntu, you'll need to run Disk Utility.  Locate your new drive,  and format/partition it. If it's a brand new drive, there is no file system on it, which is why Ubuntu doesn't "do" anything with it right away. If this drive is already set up and there's data on it, then it should be detected (but not mounted) automatically. Clicking on the drive would then mount it for access.

---

### Post by oldfred on 2012-04-30
your motherboard has 3 Gb/sec ports and drive is new Advanced format with 6 Gb/sec connection. 

I do not see anything about it also being backwards compatible with the 3 Gb/sec but I thought most drives were. Do you know for sure if it is? What does vendor say?

---

### Post by Elzenbr8 on 2012-05-01
> **MonkeyPaw said:**
> I think you'll want AHCI, not IDE, though that  mainly depends on what the BIOS was set at on last install so you can  boot. Once you boot into Ubuntu, you'll need to run Disk Utility.   Locate your new drive,  and format/partition it. If it's a brand new  drive, there is no file system on it, which is why Ubuntu doesn't "do"  anything with it right away. If this drive is already set up and there's  data on it, then it should be detected (but not mounted) automatically.  Clicking on the drive would then mount it for access.
 
 Yes, I need it in AHCI istead of IDE/RAID. But to ensure my BIOS can detect  it, I need to switch to IDE, so it's got on the list, since AHCI rom list  only my SATA optical drive. And it's brand new, so of course the first thing I want to do is to format it. I've checked, during the boot process, said something like ATA4 softreset (I don't remember what message exactly written). I've used my installed ubuntu and live ubuntu, but can't have it mounted (automatically which is using nautilus since it's not listed there, or manually using terminal).
 
 > **oldfred said:**
> your motherboard has 3 Gb/sec ports and drive is new Advanced format with 6 Gb/sec connection. 
  
  I do not see anything about it also being backwards compatible with the 3  Gb/sec but I thought most drives were. Do you know for sure if it is?  What does vendor say?
  Yes, my motherboard has 3 Gb/s port. And my hdd is 6 Gb/s and has backwar dcompatibility, so I don't need to worry, right?Maybe...
Without jumpering it should be compatible with 3/1.5 Gb/s. However, I did jumpering too, and still got the same. Connectors and ports are all fine. It doesn't matter if it runs on 3/1.5 Gb/s, limited, or so...
I have no more idea why it doesn't work....

By the way, upgrading or downgrading BIOS, will it make it works or maybe will make the things worst?

---

### Post by oldfred on 2012-05-01
I have not updated a BIOS for ages. My current system does automatically read a FAT32 flash drive so it is easy to upgrade. Most use Windows .exe, so from Linux it is difficult or impossible.

The general suggestion is not to upgrade BIOS as that can be dangerous (bricked system) and unless update specifically resolves an issue you have it will not help.

---

### Post by MonkeyPaw on 2012-05-01
A BIOS update may help, but I don't think it's the issue. 1TB drives have been around a while now, so any components built in recent years should see them just fine. One thing I have noticed in today's BIOSes is that they don't always show hard drives as detected when set to AHCI, but they actually are. I'm not sure why that is, but the drives show up in the OS. Have you tried booting while set to AHCI and see what happens once you get into Ubuntu, or are you getting an error?

A few other things to consider in the BIOS is boot priority. When you have more than one HDD, the BIOS must chose which drive to boot from. Often it takes the existing drive first, but you never know.

---

### Post by oldfred on 2012-05-01
Some info on 4K drives.

[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/index.html](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/index.html)
Technical details - from 2010 so now newer kernel resolve linux issues
[https://ata.wiki.kernel.org/index.php/ATA_4_KiB_sector_issues](https://ata.wiki.kernel.org/index.php/ATA_4_KiB_sector_issues)

---

### Post by Elzenbr8 on 2012-05-02
> **MonkeyPaw said:**
> Have you tried booting while set to AHCI and  see what happens once you get into Ubuntu, or are you getting an error?

A few other things to consider in the BIOS is boot priority. When you  have more than one HDD, the BIOS must chose which drive to boot from.  Often it takes the existing drive first, but you never know.

Well, I've tried all. AHCI failed to make it on the list, only my SATA  optical drive listed there. And with my PATA hdd that has ubuntu in it  removed, it was not on the list either. Ports, connectors, access mode,  and SATA type controller, I've tried that all. And I don't need to worry  with boot priority, since there's boot priority menu to select which  device want to boot. And basically, ubuntu will be booted up since the  new hdd is blank.

> **oldfred said:**
> I have not updated a BIOS for ages. My current  system does automatically read a FAT32 flash drive so it is easy to  upgrade. Most use Windows .exe, so from Linux it is difficult or  impossible.

The general suggestion is not to upgrade BIOS as that can be dangerous  (bricked system) and unless update specifically resolves an issue you  have it will not help.

Yes, that's true, upgrading BIOS was my last hope but it seems there's  no way would solve this problem since I read there's no related patch  with this. And it's not that difficult to do, we just need to extract  the update file from ubuntu (in my case) to FAT32 UFD..

> **oldfred said:**
> Some info on 4K drives.

[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/index.html](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/index.html)
Technical details - from 2010 so now newer kernel resolve linux issues
[https://ata.wiki.kernel.org/index.php/ATA_4_KiB_sector_issues](https://ata.wiki.kernel.org/index.php/ATA_4_KiB_sector_issues)

Thanks for the info. But both fdisk and GParted are only work with ready drive.
So, it should be recognized as device file first, right? like, sda, sdb, etc...
Hence, it's not on the list under SATA controller on disk utility.
My kernel version is 3.0, so issues should be resolved. While, advanced format works only with windows.
By the way, CHS in my BIOS is only available for IDE (not for SATA or SATA as native IDE), and so does LBA.

What do I need to do then?

---

### Post by oldfred on 2012-05-02
CHS was back when drives were not larger than 8GB. We set in BIOS the cylinders, heads, sectors from a label on the drive. Many tools still show CHS for legacy reasons. (or they just never updated)

All new drives are LBA. But BIOS give various options. If you ever turn the RAID setting on that will write info to drive that interferes with an install unless you really have multiple drives and want RAID.

I have accumulated many issues reported by other users. See if any apply.

> Some issues on booting install:
fixed the problem by adding rootdelay to grub.cfg this allows time for the usb drive to load.
BIOS settings need USB mouse & keyboard
BIOS in not updated to latest revision
BIOS not set to boot CD or USB first
BIOS shows floppy or firewire and you do not have those
changing newer BIOS SATA 6 Gbit/s  from 6 Gbs to a SATA II - 3Gbs 
BIOS & disable "Boot Sector Virus Protection"
Other BIOS settings - Security or locked down Boot sector, Bitlocker
Old BIOS, new drive 137GB max boot size
NTFS partition needs chkdsk, gparted will not see drive if chkdsk flag set, flag is set on resize
Raid meta data on drive - even if one drive (Vendor happend to set it on)
Old gpt data on drive
Disable Quickboot in BIOS
BIOS setting, Keyboard response in grub really slow
Fast Boot setting prevents keyboard from working & other issues
Bios not loading no key works - disconnected power for about 10-15 minutes and the bios reset itself.
After update, It had reset to the BIOS defaults, setting the video to ONBOARD and switching off the dynamic video memory allocation (manually allocating 32Mb instead of leaving it as AUTO).
The mode for the disc was set to AUTO. Changed it to LBA. Then it worked.
Sometimes specific issues by motherboard like this:
[Natty] Marvell 88SE9120 IDE-Part not working 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/777325](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/777325)
External drive needed separate power supply
Asus m4a87td  core unlocker feature on usb3 was causing the problem
Asus - Security> I / O interface Security> "New interface card" or so. SET IT TO LOCKED!!! 
In the Asus BIOS I selected Advanced Mode>Advanced>SATA Configuration.
Changed IDE Mode to AHCI Mode
Then,when the SATA3G_1 selection appears in the drive list below,select the Enabled option.

Large external drive still needed /boot at beginning:
[http://ubuntuforums.org/showthread.php?t=1888497](http://ubuntuforums.org/showthread.php?t=1888497)

It was in the BIOS. Under Onboard Devices Settings, the SATA Mode was set to SATA. I changed it to AHCI. Then another line showed up in the BIOS that stated "Change the AHCI DID for Linux to Enabled. I booted to win7 and it loaded some new drivers. I booted to Gpart and glory be there were my hard drives.

Change SATA controller mode from AHCI to Compatibility (AHCI should be ok for Vista/7 & Linux), XP may not have AHCI driver.
[http://ubuntuforums.org/showthread.php?t=1694750&page=8](http://ubuntuforums.org/showthread.php?t=1694750&page=8) post #79
Standard BIOS Settings -> [drive you want to change] -> IDE Access -> “Large”, did the trick. 


---

### Post by Elzenbr8 on 2012-05-02
> **oldfred said:**
> If you ever turn the RAID setting on that will write info to drive that interferes with an install unless you really have multiple drives and want RAID.
You meant creating disk drives array? If so, no never, I don't want to, since mine have different interface (brand, capacity, speed, chip, etc..).
And I've tried both AHCI and IDE with all available access mode, there are only two options by the way, Auto and Large. And, didn't solve the things.

And this is what I did today (just repeating what I previously did, and found inconsistency):
First, I removed 80 GB PATA disk drive.
Then, added 2TB wd20earx.
Finally, playing arround with SATA type controller and its access method.

Result:
[AHCI]
My wd20earx listed on the AHCI rom list but not on boot menu (all installed drives should be listed).
Sometimes, with additional text like SMART unsupported sided, and sometimes not.
DVD drive listed too.
This result was different than before. Previously wd20earx never got on the list.
(Glad now to see it listed there, at least...)

[Native IDE]
Nothing different in this mode.
WD20EARX detected and listed on IDE channel.
Detected capacity is 0MB.


Some people told me to initialize the disk, do partitioning and formating to make it works. I wonder how...

By the way, I did dmesg, and this is the output that may related to:
```

[   13.692020] ata1: softreset failed (device not ready)
[   23.704019] ata1: softreset failed (device not ready)
[   34.276020] ata1: link is slow to respond, please be patient (ready=0)
[   51.020021] ata1: softreset failed (device not ready)
[   51.020024] ata1: applying PMP SRST workaround and retrying
[   58.472030] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   58.472314] ata1.00: failed to IDENTIFY (INIT_DEV_PARAMS failed, err_mask=0x80)
[   73.484017] ata1: softreset failed (device not ready)
[   77.556036] ata1: SATA link down (SStatus 0 SControl 300)
----------------------
[   77.595371] ata1: exception Emask 0x10 SAct 0x0 SErr 0x40c0000 action 0xe frozen
[   77.595374] ata1: irq_stat 0x00000040, connection status changed
[   77.595376] ata1: SError: { CommWake 10B8B DevExch }
[   77.595380] ata1: hard resetting link
----------------------
[   87.632054] ata1: softreset failed (device not ready)
[   87.632059] ata1: hard resetting link
----------------------
[   97.636036] ata1: softreset failed (1st FIS failed)
[   97.636042] ata1: hard resetting link
[  108.576033] ata1: link is slow to respond, please be patient (ready=0)
[  125.688044] ata1: softreset failed (device not ready)
[  125.688049] ata1: applying PMP SRST workaround and retrying
[  130.848034] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[  135.848037] ata1.00: qc timeout (cmd 0xec)
[  135.848048] ata1.00: failed to IDENTIFY (I/O error, err_mask=0x5)
[  135.848052] ata1: hard resetting link
[  145.860030] ata1: softreset failed (device not ready)
[  145.860034] ata1: hard resetting link
[  155.872070] ata1: softreset failed (device not ready)
[  155.872081] ata1: hard resetting link
[  166.444071] ata1: link is slow to respond, please be patient (ready=0)
[  167.900114] ata1: softreset failed (device not ready)
[  167.900125] ata1: applying PMP SRST workaround and retrying
[  172.272080] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[  182.272083] ata1.00: qc timeout (cmd 0xec)
[  182.272101] ata1.00: failed to IDENTIFY (I/O error, err_mask=0x5)
[  182.272111] ata1: limiting SATA link speed to 1.5 Gbps
[  182.272120] ata1: hard resetting link
[  192.288064] ata1: softreset failed (device not ready)
[  192.288069] ata1: hard resetting link
[  202.316070] ata1: softreset failed (device not ready)
[  202.316081] ata1: hard resetting link
[  212.888073] ata1: link is slow to respond, please be patient (ready=0)
[  214.456071] ata1: softreset failed (device not ready)
[  214.456082] ata1: applying PMP SRST workaround and retrying
[  219.108060] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  219.108402] ata1.00: failed to IDENTIFY (INIT_DEV_PARAMS failed, err_mask=0x80)
[  224.108077] ata1: hard resetting link
[  234.124070] ata1: softreset failed (device not ready)
[  234.124082] ata1: hard resetting link
[  244.136070] ata1: softreset failed (device not ready)
[  244.136081] ata1: hard resetting link
[  254.708083] ata1: link is slow to respond, please be patient (ready=0)
[  263.280074] ata1: softreset failed (device not ready)
[  263.280085] ata1: applying PMP SRST workaround and retrying
[  268.492068] ata1: link is slow to respond, please be patient (ready=0)
[  269.500088] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  269.516063] ata1: EH complete

```Well, I think this would be an unsolveable issue. And maybe I need to give up soon before turns me to be the frustrated one....

---

### Post by Elzenbr8 on 2012-05-05
**:: An Unsolvable One ::**

I've contacted my vendor. And it seems true that they don't support Linux users.
Thanks to oldfred, for pointing to this thread:
[http://ubuntuforums.org/showthread.php?t=1694750&page=8](http://ubuntuforums.org/showthread.php?t=1694750&page=8)

And thanks to you all for your quick responses.
Time to quit and having fun. Yay-yay...

---

### Post by mips on 2012-05-05
That drive should work fine.

I'll get back to you later.

---

