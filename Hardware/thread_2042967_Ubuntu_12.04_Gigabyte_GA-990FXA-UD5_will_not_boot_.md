---
title: "Ubuntu 12.04 Gigabyte GA-990FXA-UD5 will not boot after install"
date: 2012-08-15
forum: Hardware
---

### Post by cmh79 on 2012-08-15
Hello I need help with a clean install on my brand new Gigabyte ga-990fxa-ud5. I bought the board and swapped all other components from my previous machine onto the new mobo. I had 12.04 installed on that system with no problems. So I know that it is not a driver issue with any other components except the motherboard. 
I could not install ubuntu 12.04 in the new machine until I swapped the sata from the dvd drive from the sata II to the sata3. I would get busybox v1.18.5 (initramfs) unable to find a medium containing a live file system message. After swapping to sata3 I was able to install 12.04. Now it begins to load to the purple/brownish screen and hangs up before it gets to a login screen.  
I tried changing in bios IDE to ACHI with no avail. I have pretty much tried everything the general google search suggest. It appears to be a motherboard issue please help. If you have witnessed a working 12.04 on this motherboard or have any ideas please let me know how it was done. 

Here are my system specs just in case:
Gigabyte GA-990FXA-UD5
Phenom II x6 1090T @3.2GHz
Team Elite @ 1333
Sapphire HD6950 2GB ddr5
scythe 12 fan controller 
WD HDD x3
I removed all external devices.

---

### Post by freackout on 2012-10-04
> **cmh79 said:**
> Hello I need help with a clean install on my brand new Gigabyte ga-990fxa-ud5. I bought the board and swapped all other components from my previous machine onto the new mobo. I had 12.04 installed on that system with no problems. So I know that it is not a driver issue with any other components except the motherboard. 
I could not install ubuntu 12.04 in the new machine until I swapped the sata from the dvd drive from the sata II to the sata3. I would get busybox v1.18.5 (initramfs) unable to find a medium containing a live file system message. After swapping to sata3 I was able to install 12.04. Now it begins to load to the purple/brownish screen and hangs up before it gets to a login screen.  
I tried changing in bios IDE to ACHI with no avail. I have pretty much tried everything the general google search suggest. It appears to be a motherboard issue please help. If you have witnessed a working 12.04 on this motherboard or have any ideas please let me know how it was done. 

Here are my system specs just in case:
Gigabyte GA-990FXA-UD5
Phenom II x6 1090T @3.2GHz
Team Elite @ 1333
Sapphire HD6950 2GB ddr5
scythe 12 fan controller 
WD HDD x3
I removed all external devices.

i had similar prob but my system was installed already example i installed a new sata dvd burner and encounted linux not seeing it...

so i thought ok as i dont use windows much anyway put in a live distro booted to cdrom (plugged in on marvel as slave (one of the two grey satta connections)cos didnt bother which one)
what gives bios sees it boots to initramfs message on screen ok..

so changed my gsata in bios from ide to achi on took out live booted into my ubuntu and hey presto....i had no raid disks installed so i had no problem... achi can be on/off for different raid setups. i was on 10.04 no probs,, automounts and burns dvd's great cheepo samsung super writemaster. sata 22x it did my media at 17x in k3b, depends on media speed.......:-)

---

### Post by cmh79 on 2012-10-06
Ok so when I installed Ubuntu I installed it _not_ in a raid setup. All other HDD's were disconnected from the motherboard so I would have the cleanest install possible.  I played with every bios setting I could think of (one at a time of course) including ACHI.  None of my HDD's are partitioned. I have one dedicated to windows, One dedicated to Ubuntu, and one for storage. Not a RAID setup.  All components that are not vital to the operation of the computer were disconnected including the extra HDD's. I just can not seem to get it to boot. I had it setup the exact same way on my last MOBO which was also a gigabyte and it worked flawlessly. I am at a loss. And of course Gigabyte wont help me because they don't have support for Linux.

---

### Post by marsanyi on 2013-01-09
Screw it. I'm trying to install 12.04 LTS on a Gigabyte GA-990FXA-UD3; I can boot to a fresh image, but: no network, no USB.

Googling shows network driver is incorrect; managed to compile and install proper driver, but can't enable the network.

Googling shows USB errors likely caused by enhanced USB driver, suggested removing and defaulting back to USB1.1.  Really?

Thoroughly unimpressed.  I've spent two days on this already, had to overwrite my old drive's 12.04 LTS image and managed to corrupt the ext4 filesystem on my /home drive.  Huge time waste.  Sending the board back, ordering a board that I _know_ works without issues.

---

### Post by gamarino on 2013-06-08
In my case, only the two USB3 port were working, no USB2 nor the front ones were usable. No network was working

I have solved the problem changing the BIOS setup.
Try setting on bios IOMMU = yes.

---

### Post by tleepc on 2013-11-29
Thank you, Thank you, Thank you.  It really is great when something simple is overlooked but someone takes the time to let others know.  Tlee

---

