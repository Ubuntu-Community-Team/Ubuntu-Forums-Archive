---
title: "Uefi &amp; legacy boot"
date: 2021-05-11
forum: Hardware
---

### Post by mastablasta on 2021-05-11
I am scouting for an upgrade of motherborard and CPU. at the moment i use old BIOS mothebroard with single core CPU. i have Kubuntu 18.04 installed.

for upgrade i will need 5.4 kernel for CPU and GPU also needs this one because later kernel might lack the nvidia driver, so at some point i will have to either do upgrade to 20.04 or to use HWE on 18.04.

but my questions here are (since i already have an install that is working so well):
- can i just use legacy boot on current install
- and if yes, how can i find out if motherboard has legacy boot option

i checked user manual and tech. specification, but for some reason i can't find this information. i plan to use the same frame i have now and go with Asus Prime B450M-A II (that is what looks like a newer iteration than the one my kid has) & Ryzen 5 3600 or 3500X . i plan to add G.Skill Ripjaws V - 4x8 GB or 2x16 GB. I plan to add samsung 860 1 TB SSD, but i might not need it for OS but just to store a couple of games. 

or does it really pay off to move the whole OS on SSD and do a reinstall of everything? it just took me a while to get it working so well and i don't want to ruin anything :) but on the other hand i do want it to work better.

oh the monitor will be ye olde 4:3 17" SVGA (now in it's 17 year). if it goes bust (lately i have monitor menu popping up) i have another slightly younger SVGA that is actually wide screen. GPU stays at GT 730 for now and until i can actually buy anything else.
 
everyone has better PC than me and they all have to wait 10 minutes before i can login to CS:GO. :)

---

### Post by him610 on 2021-05-11
Hello mastablasta, maybe this will help.

I have a similar system to the one that you plan on building. When I initially installed LTS 20.04 on it, I unintentially configured EUVE/BIOS with legacy boot. It booted without any issues. Later on after realizing that I was booting legacy mode, I decided to reinstall LTS 20.04 to boot using EFI; also, formatted my primary disk (NVME-M.2) to ZFS. No issues encountered then or since.

Here are my pertinent system specs that you might compare with yours...
```

$ inxi -SMCGD
System:    Host: b450m Kernel: 5.8.0-50-generic x86_64 bits: 64 Desktop: Xfce 4.14.2 
           Distro: Ubuntu 20.04.2 LTS (Focal Fossa) 
Machine:   Type: Desktop Mobo: ASRock model: B450M/ac serial: <superuser/root required> 
           UEFI: American Megatrends v: P1.50 date: 10/14/2019 
CPU:       Topology: 6-Core model: AMD Ryzen 5 2600 bits: 64 type: MT MCP L2 cache: 3072 KiB 
           Speed: 1508 MHz min/max: 1550/3400 MHz Core speeds (MHz): 1: 1543 2: 1376 3: 1543 
           4: 1408 5: 1509 6: 1379 7: 1435 8: 1472 9: 1506 10: 1461 11: 1457 12: 1469 
Graphics:  Device-1: NVIDIA GK104 [GeForce GTX 760] driver: nvidia v: 460.73.01 
           Display: x11 server: X.Org 1.20.9 driver: nvidia 
           unloaded: fbdev,modesetting,nouveau,vesa resolution: 2560x1080~60Hz 
           OpenGL: renderer: GeForce GTX 760/PCIe/SSE2 v: 4.6.0 NVIDIA 460.73.01 
Drives:    Local Storage: total: 1.06 TiB used: 49.44 GiB (4.6%) 
           ID-1: /dev/nvme0n1 vendor: Western Digital model: WDS500G2B0C-00PXH0 
           size: 465.76 GiB 
           ID-2: /dev/sda vendor: Seagate model: ST500LM012 HN-M500MBB size: 465.76 GiB 
           ID-3: /dev/sdb vendor: Western Digital model: WD1600BJKT-00F4T0 size: 149.05 GiB 


```

Note: oldfred is fount of information regarding legacy boot, Bios, Euve, EFI boot.

Added: FWIW, I also have another system with a GT 635...
```

$ inxi -G
Graphics:  Device-1: NVIDIA GK208 [GeForce GT 635] driver: nvidia v: 460.73.01 
           Display: server: X.org 1.20.9 driver: nvidia 
           unloaded: fbdev,modesetting,nouveau,vesa tty: 96x32 
           Message: Advanced graphics data unavailable in console. Try -G --display 

```

---

### Post by oldfred on 2021-05-11
Almost all motherboards have UEFI and CSM. And they still call it BIOS, even though since 2012 it really is UEFI.
CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode, only available with secure boot off.

I have suggested for years, that everyone should use gpt partitioning.
And with gpt you need a bios_grub partition for BIOS boot or an ESP - efi system partition for UEFI boot.
For several years when first starting conversion from BIOS to UEFI, I had both bios_grub & ESP on new drives so I could move drive from old BIOS to new UEFI or vice-versa. But only one is required. And only real difference between UEFI & BIOS is version of grub.

Intel's new standard for 2021 is UEFI Class 3 or UEFI only. (was 2020)
A very few lightweight systems were class 3 before, to try to make a Windows system unique like iPads. They used UEFI 32 bit even though system was 64 bit as back then Linux did not have a 32 bit UEFI boot loader.

Intel is planning to end "legacy BIOS" support in their new platforms by 2020 in requiring UEFI Class 3 or higher.
[http://www.uefi.org/sites/default/files/resources/Brian_Richardson_Intel_Final.pdf](http://www.uefi.org/sites/default/files/resources/Brian_Richardson_Intel_Final.pdf)
[https://support.lenovo.com/us/en/solutions/ht510878-legacy-bios-boot-support-removed-in-lenovo-2020-products](https://support.lenovo.com/us/en/solutions/ht510878-legacy-bios-boot-support-removed-in-lenovo-2020-products)
ACER sf514 laptop UEFI Class 3
[https://unix.stackexchange.com/questions/615603/in-uefi-class-3-how-install-centos-8](https://unix.stackexchange.com/questions/615603/in-uefi-class-3-how-install-centos-8)

Motherboards will probably be that last to be converted to Class 3.

If you want to improve performance an SSD, even a lower cost one make major improvements in boot & loading large programs. Has not helped the issue between keyboard & chair getting slower though.

---

### Post by mastablasta on 2021-05-12
so in theory - HWE kernel on 18.04 & GPU driver should be enough to get it working with current setup as long as i can set the UEFI to BIOS mode (which should also be possible). later on i can perform system upgrade to 20.04, since Kubuntu kind of looses LTS support after 3 years.

how interesting that GT 635 is still supported in new driver. as i checked their website for fermi GT 730, the 3.90 should be the last one and it entered legacy support period. but then again there are different chips on similar models of cards. for example mine has 2 GB VRAM and clock is slightly higher if i remember correctly. while the usual GT730 had 1 GB. or maybe they decided to extend support since new cards are hard to come by.

So legacy boot doesn't need EFI partition, right?

---

### Post by oldfred on 2021-05-12
No ESP required for BIOS boot, but I have seen some posts where installer added an ESP, to new BIOS installs even on MBR drives.

All new drives should be gpt, unless you really want Windows in BIOS boot mode. But can continue to use old MBR with BIOS and then do not need either bios_grub nor ESP.  And often better to add bios_grub and/or ESP as first partitions on drive so out of way. UEFI suggests ESP be first, but it really just needs to be in first 2TB ( I think).

---

### Post by mastablasta on 2021-05-13
ok so 
option one - upgrade kernel, use legacy boot option if available & leave disk it as it is (MBR boot)
 option two - in case option one fails, use new disk and make a brand new UEFI install, then move data from old disk to new disk (or to static data disk) and back again after reformat or just delete system files on old disk.
```

[FONT=monospace][COLOR=#000000]Filesystem      Size  Used Avail Use% Mounted on [/COLOR]
udev            1,9G     0  1,9G   0% /dev 
tmpfs           395M  3,0M  392M   1% /run 
/dev/sdb1       1,8T  669G  1,1T  39% / 
tmpfs           2,0G     0  2,0G   0% /dev/shm 
tmpfs           5,0M  4,0K  5,0M   1% /run/lock 
tmpfs           2,0G     0  2,0G   0% /sys/fs/cgroup 
tmpfs           395M   20K  395M   1% /run/user/1000

[/FONT]
```

+ 2 more NTFS drives inside (from windows XP *era*), one has only one half formatted.

---

### Post by mastablasta on 2021-05-23
> **mastablasta said:**
> 
how interesting that GT 635 is still supported in new driver. as i checked their website for fermi GT 730, the 3.90 should be the last one and it entered legacy support period. but then again there are different chips on similar models of cards. for example mine has 2 GB VRAM and clock is slightly higher if i remember correctly. while the usual GT730 had 1 GB. or maybe they decided to extend support since new cards are hard to come by.


after more reviewing and having APU as option i decided to go with with classic CPU+GPU. hopefully it goes well with current install, but i also have plenty space on external drive for backup and i ordered additional disk.

it seems nvidia scammed the customers with this model. my GT 730 has fermi chip. i checked the box over and over and there is no mention of that. the nvidias with kepler chips are closer in speed to GT 1030 and can even run GTA5, Withcer 3 or Skyrim on medium.  the ones with fermi chips won't run witcher 3, can only get through maybe with low settings on Skyrim... the bad part is that both (or all) cards were sold at the same time and for same amount of money. and both were marketed as GT 730 at the time. one is quite descent, the other one is blyat. :) so what mine has is actually similar chip to GT530 but maybe more RAM. so the performance is similar to or slightly slower than intel HD 530. and the bad part is it is already in legacy. 

so plan is to move to 5.4 kernel and use it for now with the hope of moving to a better card later on. if the prices still remain high and actually you can't buy any cards in 150 EUR range, then i messed it up (i should have taken the AMD APU) and i will probably "upgrade" to GT1030 or similar. but if all goes well and with a bit more more patience i might get to the build i was after that will hopefully last for some time. i really hope that there will be a good new year sale and that not all prices skyrocket. but who knows with these crazy times we live in.

so i got:
Ryzen 5 3600
32 GB 3200 Mhz ram
Asus AMD board 
Samsung 1TB SSD drive

i will move over the 2 year old PSU (550W 80 bronze) and GPU (GT730 with GF108 chip) and use the old monitor for now. later on i need to change the GPU and monitor and i will move the GPU back and use it as media server/old games console. 

i also decided to change the box (frame). this one does not have enough room for the modern GPU (unless i used a low profile one). plus it will be easier to build in new box and i have an easy fall back in place in case something goes wrong. 

i also got a mechanical keyboard that was on sale. it is not exactly what i was after (i wanted a Cherry with mx brown switches & local keys on it), but it is a descent one from logitech and at reduced price price.

---

### Post by oldfred on 2021-05-23
Always check performance of internal gpu vs any video card.

When I build my Asus Haswell based system, I did not pay attention to video out ports. 
Motherboard had HDMI & Display port out, but my old monitor was VGA or DVI in.
So I used an older video card that I had. GT620.
Low end video & other Hardware comparisons, performance: 
[https://www.videocardbenchmark.net/low_end_gpus.html](https://www.videocardbenchmark.net/low_end_gpus.html) 
GeForce GT 620                        430
 Intel® HD Graphics 4600   712  Haswell
Intel HD Graphics 620           927  Skylake

After I saw that Haswell system's own video was better than older GT620, I found an adapter from HDMI to DVI which has worked well and then not issues with install of nVidia graphics (which now is easier). 
I do not play games, although grandson is getting old enough to want some games. So things may change.

I also tried to use a 4 year old power supply. It was ATX standard & should have worked. 
Motherboard would just power up, but not boot. Took it to nearby Microcenter. They put it on their test bench & it immediately booted. Or they sold me a new power supply. Found best to put box on case for insulation, and motherboard on box fully connected to test that it works before finally screwing it in. I wish I had used new case as old case did not have USB3 front ports. I just connect to back with long cord.

---

### Post by mastablasta on 2021-05-24
> **oldfred said:**
> 
After I saw that Haswell system's own video was better than older GT620, I found an adapter from HDMI to DVI which has worked well and then not issues with install of nVidia graphics (which now is easier).

oh yeah. the APU i was looking at is waaay better than my current GPU (the Vega 7 GPU). at least 100% better. not to mention it is much newer (introduced at end of 2019). but somehow i still decided to go with classic for now with the hope of exchanging for a better card later on. i don't game as much and mostly play older games, but when i do i don't want it to lag terribly. plus  after 17 years and low end upgrades or necessary replacements i think i deserve a proper GPU. :)


> 
I wish I had used new case as old case did not have USB3 front ports. I just connect to back with long cord.
that was my plan for the USB ports (connect 2 USB2 internally and then connect cable to back USB3 outside), but still i think the new frame with USB 3 in front is additional feature i could use. and it comes with larger fans that keep the volume down a bit.

---

### Post by mastablasta on 2021-05-26
well worked like a charm and os far so good. i upgraded kernel on Sunday on old PC to 5.4 (HWE). i still need to test a few things and make a few changes (increase RAM frequency to 3200mhz). but out of the box linux support on this motherboard. i will do the upgrade to 20.04 later, maybe during summer.

still waiting for the Samsung SSD which i ordered in another shop.

one thing that did rattle me a bit was that motherboard did a HDD scan and came up with "near failure warning". yet another disk that was hardly ever used (WD green for static data), but at least this one is a bit older. so i am scrambling to get some disk space and copy the files over (at leats the family photos an videos). they should all be on the backup server and on another desktop HDD in different PC, but you can never be too cautious. i wonder if bad cable connection could cause such and error?!

---

