---
title: "Unsafe Shutdown Count Increases (Almost every boot)"
date: 2023-07-22
forum: Hardware
---

### Post by joegiampaoli2 on 2023-07-22
A bit concerned here with relatively new self built PC. This is the first time I am using a NVME SSD (ADATA LEGEND 700)

I started using the command:

**sudo watch -n 1 nvme smart-log /dev/nvme0**

to monitor the percentage of usage of the SSD (I know it's still to new to see some usage "burnout") but one thing started to come to my attention and that was the "Unsafe Shutdown" count which keeps incrementing almost every boot-up, I always power off the proper way and I have a habit of turning off the surge/regulator that this PC is connected to, obviously right after it powers off properly. I dual boot two Linux OS's, one is standard Ubuntu and the other is Ubuntu Studio for my audio production.

My BIOS settings are defaults mostly for the boot process, which is not rebooting after a power loss and fast boot enabled (I have tried both fast and normal and seems to have no effect).

I am not really sure if the count increases +1 everytime I power off the surge/regulator, I will be checking that out with time, but I have read that it is always good to unplug a PC when not in use, which is pretty much the same. I have proper grounding, but I am still cautious because I live in Mexico where electricity is not very reliable especially during thunderstorms, I know PC power supplies are there also to protect against surges, but I am still being cautious.

Now the true questions of all this is...

**Should I be worried about this "Unsafe Shutdown" count increasing on every boot and is something becoming physically damaged or files being corrupted?**

Thank you!

---

### Post by joegiampaoli2 on 2023-07-22
Just a quick follow up, I disabled quick boot in BIOS, I am aware that it can cause nothing but trouble in some cases, I will still continue seeing if at least the "Unsafe Shutdown" count increases less...

---

### Post by joegiampaoli2 on 2023-07-23
Another follow up:

I enabled in BIOS (ASUS MB)

**NVMe Driver Support**

It was disabled by default, will see if this changes anything, I am doing this and replying to myself so others may see if I find a solution and it helps them...

---

### Post by joegiampaoli2 on 2023-07-24
Enabling **NVMe Driver Support **doesn't help or make a difference, but I left it enabled, somehow I sense it should and maybe even feel more responsiveness when opening applications, but the "Unsafe Shutdown" count keeps increasing, I also think that maybe it's only when powering down and up the PC, not in reboots.

Will continue testing and posting...:(

---

