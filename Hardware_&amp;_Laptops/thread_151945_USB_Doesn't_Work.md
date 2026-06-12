---
title: "USB Doesn't Work"
date: 2006-03-28
forum: Hardware &amp; Laptops
---

### Post by BitTorrentBuddha on 2006-03-28
Well, my USB ports aren't detecting anything I put in them, though they are detected from the device manager (or at least if I'm interpreting this correctly). My motherboard is a PCchips M960GV and the manual says that all 4 onboard ports are usb, while the device manager says 3 are 1.0 and 1 is 2.0. The output of lsusb is as follows ```
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
```If that is of any help. Ask if you need any more information. And if I can't fix this, is there a particular PCI USB card that will or won't work? And does anybody know if [this one]("http://www.provantage.com/startech-pci625usb2i~7STRP07R.htm") will work? Thanks in advance for all your help :)

---

### Post by BitTorrentBuddha on 2006-03-29
bump

---

### Post by aysiu on 2006-03-29
Can you plug something and post the output of this command? ```
sudo fdisk -l
```

---

### Post by BitTorrentBuddha on 2006-03-30
Disk /dev/hdc: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        3497    28089621   83  Linux
/dev/hdc2            3498        3649     1220940    5  Extended
/dev/hdc5            3498        3649     1220908+  82  Linux swap / Solaris

---

### Post by BitTorrentBuddha on 2006-04-01
bump, digging the april fools day layout they've go going on

---

### Post by Scunizi on 2006-04-01
I've posted this once before (yesturday).  Seems like a lot of people have this problem.  This fixed it for me.

I have FINALLY found the solution to this problem. It was really quite easy after I learned a little about how the file system work and how the system mounts things. You have to remember, the system needs a place holder/directory for each device that is mounted. That is accomplished in the media directory. Also everything you type below is case/CASE sensitive. I have 2 internal SATA drives and 1 IDE internal. I also wanted to be able to plug in my 3 USB devices and have them recognized with icons displayed on the Desktop. The 3 devices are... 1gig usb stick, 256m usb stick, 1 256m mp3 player (creative rhomba). I had to do a little editing of the fstab and media directory in order to get everything working correctly. In my case I already had sda1, sdb1,2,3,5, and hda1.

1> Go to the consol and type sudo gedit /etc/fstab (enter) - This will open up your editor. It will ask for your password after the enter.

2> In fstab I added these three lines
/dev/sdc1 /media/usb1 vfat rw,user,fmask=0111,dmask=0000 0 0
/dev/sdd1 /media/usb2 vfat rw,user,fmask=0111,dmask=0000 0 0
/dev/sde1 /media/usb3 vfat rw,user,fmask=0111,dmask=0000 0 0

Now click save at the top of the screen.

The vfat referance above is for Fat32 formatted devices. Anything other than that and you'll have to change the formatting designator and possibly the fmask. dmask=0000 simply means that any user of the system can read and write to the device. If I remember correctly, if you substitute 0000 with 1000 only the logged user who created all this will be able to use the device. Someone may correct me here if I'm wrong. I'm humble.

You'll notice all my usb referances are sdc sdd sde because I already have 2 SATA drives in the machine that are labeled sda & sdb respectively (the numbers represent the different partitions on the harddrives) I you don't have any SATA drives then you should designate sda, sdb, sdc respectively. I made three seperate entries in case I plug in all three devices at the same time otherwise it won't make any differance.


3> Go back to your consol and click "File" "Open Tab". You'll now see two tabs at the top of the consol. Click the second one and you should have an active prompt like "mgarrow@ubuntu:/$". Type cd /media (enter). This will take you to the media folder/directory.
4> Now type
sudo mkdir usb1 (enter) (maybe enter password)
sudo mkdir usb2 (enter) (maybe enter password)
sudo mkdir usb3 (enter) (maybe enter password)
These lines give a place for the drives/devices to attach to. You can use other names if you want. I just did it this way for simpicity.

Now you're done! Restart your machine then plug in one of your usb devices. I may take a moment but the system should recoginze it, mount it and place an icon for it on the Desktop...

I'm about 3 weeks into learning this system from a cold start and really learning to love it between my bouts of frustration with my ignorance. Happy Ubuntu-ing!!!

---

### Post by BitTorrentBuddha on 2006-04-01
that didn't work, but I don't think this is a mounting problem because I can't even get a USB light to work, I'm betting it's a hardware problem...

---

### Post by BitTorrentBuddha on 2006-04-03
bump

---

### Post by BitTorrentBuddha on 2006-04-08
perhaps it has something to do with the driver?
if so how can I install the file located [here]("http://www.pcchips.com.tw/PCCWeb/Products/ProductsDetail.aspx?MenuID=22&LanID=2&DetailID=346&DetailName=Driver") since it only comes in *.exe

---

### Post by BitTorrentBuddha on 2006-04-08
I believe I can use ndiswrapper for this, but what do I use it on, for the USB download the following *.inf files were in there
SISUSB2X.INF
USB2X.INF
and another executable USB20.EXE, how should I go about this if this is indeed the problem?

---

### Post by KaptainEvilStomper on 2008-02-03
I have been having the same problem.. thing is
 it was working before.. but I put a new sound card in.. and now they do not work at all..

---

### Post by MrKlean on 2008-02-04
Are you sure the usb ports are turned on in the bios ??  Just a thot LOL!

---

