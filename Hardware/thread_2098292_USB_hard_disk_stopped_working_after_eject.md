---
title: "USB hard disk stopped working after eject"
date: 2012-12-26
forum: Hardware
---

### Post by pasR on 2012-12-26
Hello everyone :)

Yesterday I tried to remove my external USB harddrive (500 GB Samsung S2) from my laptop (running Ubuntu 12.04.1). I clicked "Eject" and once the window containing my files was closed I physically removed the drive. Since I have removed the drive it does not seem to work anymore, both on my laptop or on a different pc (which is running Windows 7). I plug it in but simply nothing happens.. The drive does not have its own power supply, its powered via the USB port. My laptop also has an internal 500 GB harddrive. When I open the "Computer" screen it lists:

- 500 GB Hard Disk: 243 GB Filesystem
- 500 GB Hard Disk: System Reserved
- CD/DVD Drive
- File System

The first of these contains the data from my internal drive. I hope someone has a clue as to what happened to my drive, any help is greatly appreciated!

Kind Regards,
Pascal

---

### Post by The Cog on 2012-12-26
With the drive plugged in, can you open a terminal and enter the commands ```
sudo fdisk -l
dmesg | tail
```
and post the output here? That should show us if the drive is seen and perhaps some error messages

---

### Post by pasR on 2012-12-26
pascal@pascal-laptop:~$ sudo fdisk -l
[sudo] password for pascal:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8f18b459

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    27080703    13539328   27  Hidden NTFS WinRE
/dev/sda2   *    27080704    27285503      102400    7  HPFS/NTFS/exFAT
/dev/sda3        27285504   502028287   237371392    7  HPFS/NTFS/exFAT
/dev/sda4       502030334   976771071   237370369    5  Extended
/dev/sda5       502030336   968665087   233317376   83  Linux
/dev/sda6       968667136   976771071     4051968   82  Linux swap / Solaris
pascal@pascal-laptop:~$ dmesg | tail
[   20.038804] NVRM: corruption and stability problems, and is not supported.
[   26.384898] wlan0: authenticate with 38:60:77:5c:30:4b (try 1)
[   26.387670] wlan0: authenticated
[   26.393394] wlan0: associate with 38:60:77:5c:30:4b (try 1)
[   26.396738] wlan0: RX AssocResp from 38:60:77:5c:30:4b (capab=0x411 status=0 aid=2)
[   26.396742] wlan0: associated
[   26.405614] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   37.382150] wlan0: no IPv6 routers present
[  155.565826] iwlwifi 0000:02:00.0: Tx aggregation enabled on ra = 38:60:77:5c:30:4b tid = 0
[  514.860847] iwlwifi 0000:02:00.0: Tx aggregation enabled on ra = 38:60:77:5c:30:4b tid = 2

---

### Post by ahallubuntu on 2012-12-26
dmesg is a monitor of ALL events in the OS as they happen. So you want to type that immediately after you've plugged in the hard drive, to see if any errors are reported at that moment.  If you wait two minutes, more events (nothing to do with the hard drives) are added to the end of the file so you won't see potential messages related to the hard drive.

fdisk shows the drive isn't registering at all, though, assuming it was plugged in while you typed that.

Do any lights come on on the hard drive when you plug it in?  Do you hear anything?

Hard drives do fail all the time, of course, sometimes without warning.

---

### Post by pasR on 2012-12-26
Nope, nothing happens when I plug it in\ (normally there's a blue LED flashing on the drive (and in Win7 a sound)) :(

---

### Post by ahallubuntu on 2012-12-26
Check the cable and the connectors.  Sometimes the connectors on the drive can go bad or you have to wiggle the cable to plug it in firmly.  I've also had USB cables fail.  

If you can't get it to work at all (the light never comes on, you can't feel a vibration, etc.), your next resort might be to crack open the case and remove the drive inside.  Of course, that voids any warranty that you might have on it.  If you're lucky just the enclosure itself failed and the drive itself could be fine (if you had data on it or something).  You can buy a new USB enclosure for a laptop drive (which is probably what's inside) for about $5 on eBay.

---

### Post by sudodus on 2012-12-26
> **pasR said:**
> Nope, nothing happens when I plug it in\ (normally there's a blue LED flashing on the drive (and in Win7 a sound)) :(

I guess you should keep trying a bit more, but maybe you will come to the conclusion, that there is a hardware error.

I know some cases, when that error was in the electronics of the enclosure, and it was possible to open it and take out the HDD (which is usually a standard HDD, that can be attached via a SATA cable directly to a computer or inserted into a new enclosure for an external disk).

---

### Post by The Cog on 2012-12-27
I would expect the act of plugging something into the USB port to show up in demsg. But the dmesg tail shows nothing happening since the wireless lan came up.

It makes me wonder if there's a problem with the USB port driver under Linux. Does any other USB item work in that port when using Linux (mouse for instance)?

---

