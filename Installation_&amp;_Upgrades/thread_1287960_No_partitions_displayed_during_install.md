---
title: "No partitions displayed during install"
date: 2009-10-10
forum: Installation &amp; Upgrades
---

### Post by Electromancer on 2009-10-10
Hello, I have recently decided to make the switch from Windows to Linux and have decided Ubuntu was the way to go. I recently downloaded the install for Ubuntu 9.04 x64 version. The live version boots up fine with no problems but when I try to install to my HDD no partitions show up in the install menu for Ubuntu. My current system specs are.
 
XFX 750a Mobo
AMD Phenom BE9750 @ Stock
2x2GB OCZ 800Mhz DDR2 Ram
Two XFX GTS 250s 512MB in SLi
Western Digital 200GB Sata Hdd
Currently running Windows 7 RC Build 7100 Using all 200 GB in one partition.
 
I was not going to dual boot as I wanted to install Ubuntu as my Primary OS.
 
Also I have a Logitech MX5000 BT mouse and KB combo with a Bluetooth dongle. I also have a PS/2 KB and another USB mouse on hand in case the logitech fails and needs drivers.
 
Any help would be appreciated.

---

### Post by stlsaint on 2009-10-10
what version are you using? If jaunty 9.04 than you can boot into the livecd and go to system>admin>partition editor and look to see what the livecd shows...you should see your actual harddrive there...if you rusing karmic than take the same route but instead of looking for partition editor you look for gparted! if you still see nothing there post back here!!

---

### Post by mbuell on 2009-10-10
The first partition screen in the Ubuntu installer offers two choices - the first is something like "Automatic, use whole hard drive", and the second is "Manual". If you are wiping Windows out, use the first. It should also offer you an option to install it side-by-side with Windows in a dual boot. If you go that route, the partitioner would show no space for Linux, and if I recall, you have to use the mouse to drag the existing partition to be smaller. I tried to find a "HowTo" on these forums, or a vid on YouTube. I've seen both, but I couldn't find them tonight.

Good luck;
Hiero

---

### Post by Electromancer on 2009-10-10
Unfortunately, Gparted shows no drive. I have also checked my BIOS and my HDD is shown as the second boot device just under my optical drive as number one. This is puzzling. I hope this has nothing to do with motherboard settings considering Windows boots up fine.

---

### Post by stlsaint on 2009-10-10
put the hdd as first then!

---

### Post by Electromancer on 2009-10-10
I tried that. When I have the HDD as the first boot device I go straight into Windows, no booting off the Ubuntu CD.

---

### Post by Electromancer on 2009-10-10
Another item I should point out is that while the live CD is loading I can see my HDD acess light blink. So I know it is being accessed, but does not come up at all in the partition menu.

---

