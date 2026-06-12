---
title: "RAID 1 with Asus P5B Deluxe WIFI/AP Motherboard"
date: 2008-03-19
forum: Hardware &amp; Laptops
---

### Post by explosive on 2008-03-19
Hi,

I currently have 1x320GB SATA HDD attached to my motherboard. I am considering purchasing a second disk of the same size and creating a RAID1 array so that I can recover faster if I have any HDD problems. 

Does anybody know if the RAID controller on the ASUS P5B Deluxe/WiFi-AP will work with Ubuntu 7.10?

The manual states the motherboard has:
Southbridge
- 6 x SATA 3.0 Gb/s ports
- Intel Matrix Storage Technology supports RAID 0, 1, 5 and 10.
JMicron® JMB363 PATA and SATA controller
- 1 x UltraDMA 133/100/66 for up to 2 PATA devices
- 1 x Internal SATA 3.0 Gb/s port
- 1 x External SATA 3.0 Gb/s port (SATA On-the-Go)
- Support SATA RAID 0, 1 and JBOD

I think currently the JMicron device controls my PATA DVD drive but it would appear that you can switch it to RAID mode.

Which of these devices should I be using to configure RAID and which will work in Ubuntu?

---

### Post by penguinpi.com on 2008-03-19
RAID if its a hardware controller should have it's own BIOS. where you can configure RAID levels, arrays, and format the drives. You will have to set up a LVM partition as well. are you planning on doing a fresh install?

---

### Post by explosive on 2008-03-19
Looking at the screenshots from the mobo manual there are BIOS pages from creating RAID partitions. 

I am planning on doing a fresh install.

---

### Post by penguinpi.com on 2008-03-19
Well this should be pretty easy then.

First you want to enter the RAID BIOS. Here you can format your drives, and create an array and set your RAID level. on my servers I have megaRAID controllers and all I have to do is go to configure and select my drives and create an array. then I can select the RAID level.

Next when installing Ubuntu, make sure you set up LVM. and when you go to partition the drives, select the RAID partition. on my servers is shows hda0,0 as megaRAID and i see a whole bunch on individual drives too, but the RAID partition should be on hda0,0, so make sure you select that one. Thats is really. If you have any problems let us know, but make sure you do have a hardware RAID controller and you know how to use the configuration utility.

Best of Luck!

---

### Post by explosive on 2008-03-19
When I create the RAID paritions in the BIOS do I RAID then entire 320GB?
Should the swap and /boot and /tml etc be raided as well?

---

### Post by penguinpi.com on 2008-03-19
All your going to do is set the whole drive for RAID. so yes you want to array all 320gb on both drives. the partitions will be set up on the Ubuntu install.

---

### Post by explosive on 2008-03-19
Ok cool.

I just need to find out if it is hardware RAID for sure - it is built into the mobo so I am not sure if it is some sort of software/hardware combo... you have to make a driver disk for windows XP but I'm hoping the drivers may already be built into the kernel...

---

### Post by penguinpi.com on 2008-03-19
All my servers are SCSI and I've had no problems. I don't really have much experience with SATA, but best thing to do is try it and see what happens. If you can set up a RAID you should be able to see that volume and partition it in the Ubuntu install. So if you can get that far, you probably wont have any problems further along.

---

### Post by explosive on 2008-03-19
Thanks for the help :)

I'm hoping someone else with the same mobo or the same chip may already have an experience of using it with RAID before I buy a second disk :)

---

### Post by explosive on 2008-03-19
I have done some more searching and it would appear that the motherboard uses "fakeRaid" which does work with Ubuntu but it appears to be a fiddle to setup.

I think I will stick with software raid as that will be easier to setup and probably more reliable.

---

### Post by penguinpi.com on 2008-03-20
Good Luck man... Hardware RAID is really the way to go. see if you can find yourself and old PIII server or something to screw around with, it's pretty cool.

---

