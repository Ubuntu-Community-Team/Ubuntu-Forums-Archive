---
title: "RAID 0 not detected in ubuntu installer"
date: 2013-01-15
forum: Hardware
---

### Post by PortableSounds on 2013-01-15
What's up guys! ):P So I am in a live session of ubuntu 12.04.1 right now. (sorry it's old it's the best I have right now). Anyways, I have a crap ton of hdds/ssds in my comp for various reasons. i am using 2 "older" 40GB SATA I (ok VERY much older) in a RAID 0 (via MSI BIOS) configuration basically so that I have enough space for everything (i have a bunch of other hdd's but they're being used for windows etc.). My problem is that, when i try to install ubuntu, it lists both hdd's separately, although one doesn' even have any space listed under it. Both hdd's show up under the "choose which hdd to boot from." I have tried reinstalling raid drivers and they're already in. I even ran the check for raid command and it said none detected, even though in my BIOS (which is set to RAID mode) definitely detects it. No one else has exactly had this problem as far as I can tell. Thanks for your help! :)
If it's of any help, here's my specs:
Mobo: MSI 890FX-GD70
CPU: AMD Phenom II x4 975 @ 4.069 GHz
GPU: Nvidia GeForce GTX 560 (Non-Ti) :(
HDD: 2x40GB WD400 SATA I HDD
           Samsung 830 120GB SATA III SSD
           Sandisk 64GB SATA III SSD
           Seagate Barracuda 2 TB HDD
RAM: Corsair Vengeance 16GB (4x4GB)
PSU: Corsair CX600 600w PSU
CPU Cooler: Corsair H100
(sorry if it's a bit exstensive, it's a copy-paste)

---

### Post by Bashing-om on 2013-01-15
PortableSounds; Hi !

The standard desktop install does not support "raid". Down load the server edition for the tools to deal with raid arrays.

I do not know much about "hardware raid", but, there may be problems with ubuntu seeing the "hardware raid" set up. You may have to consider setting up "software raid". I understand it works as well or better. I ran raid level 0, and 1 for sometime on a 3 disk set up. It was all I expected and more.

[INDENT][INDENT][INDENT]hth

[/INDENT][/INDENT][/INDENT]

---

### Post by PortableSounds on 2013-01-15
> **Bashing-om said:**
> PortableSounds; Hi !

The standard desktop install does not support "raid". Down load the server edition for the tools to deal with raid arrays.

I do not know much about "hardware raid", but, there may be problems with ubuntu seeing the "hardware raid" set up. You may have to consider setting up "software raid". I understand it works as well or better. I ran raid level 0, and 1 for sometime on a 3 disk set up. It was all I expected and more.
[INDENT][INDENT][INDENT]hth

[/INDENT][/INDENT][/INDENT]
Thank you so much for the help! I guess I'll have to put that server version on my live usb. That saved me several hours of banging my head on a wall. ](*,) Kudos!

---

### Post by Bashing-om on 2013-01-15
PortableSounds;

Glad to be of help.
If you have no experience with ubuntu/raid I suggest you do some studding, you want to have a solid plan for what you want from your system prior to setting up your partitions. Then it is a piece of cake, just follow the instructions literally (software raid). Lots of tutorials available to get raid set up and running.

[INDENT][INDENT]my best to ya 
[/INDENT][/INDENT]

---

### Post by PortableSounds on 2013-10-01
Not to dig up my old thread, but I just wanted to give you a quick update. After spending hours and hours trying to get the raid to work well, I settled with a better option: I just split up the partitions on each hard drive. I put the home, boot, and swap on one 40 GB drive, and I put the root on the other 40 GB drive. All in all, it was much easier and much stabler and less prone to bugs like the software raid (like trying to reinstall ubuntu and it just not recognizing my old software raid :(  )

---

### Post by Bashing-om on 2013-10-01
PortableSounds; Hey;

I happen to agree with your solution. IF one has not the actual need to run on raid arrays, a more conventional install is best. I too got exasperated at building and rebuilding the raid arrays when I borked my system and now have my set up similar to what you describe. Much easier to maintain and replace. Nor do I notice any degradation in performance ...is a fairly fast system to start with.

[INDENT][INDENT]the right tool for the right job
[/INDENT][/INDENT]

---

