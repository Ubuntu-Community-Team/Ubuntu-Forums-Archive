---
title: "i can't install ubuntu to my computer"
date: 2023-11-11
forum: Hardware
---

### Post by curstua on 2023-11-11
Hello everyone, help me install Ubuntu on my computer. I download the iso image from the official Ubuntu website, then flash it onto a 16 GB flash drive, connect it to a USB port, press the f12 key, select my flash drive and nothing happens. and this is a problem only on my main computer. On the old computer the system boots and installs normally. please tell me what am I doing wrong? The screenshot shows the characteristics of my computer

---

### Post by TheFu on 2023-11-11
Not all flash storage is compatible with all USB ports.
a) Try a different port.  If you were using one on the front of the computer, try the back.  If you were using a USB3 port, try a USB2 port.
b) Try creating the USB Boot install using a different flash drive. 
c) Try using different Linux flashing software. Not all of them always work and over time, the best choices change.

It would also help if you clearly listed exactly the commands used for each step of the preparation and booting.  F12 is common for some motherboards to pick a boot device, but it isn't universal. My systems use F2 and F8.

Having 4 nVidia GPUs isn't a good idea for the install, assuming they are still supported.  Pull all but 1 of those out and try again.  nVidia support under Linux is troublesome and nVidia does drop support for older GPUs.  There is a F/LOSS driver that does work with nearly any GPU, but expecting it to support 4 GPUs is probably asking too much.  

Having only 1 GPU, is my best advice for now. Post install, after you get proprietary nvidia drivers working, then you can add 1 more GPU at a time and try to get them working.  That will be at least 3 reboots adding hardware, just to be clear.

---

### Post by curstua on 2023-11-11
i have 1 gpu on my system, aida64 lies about 4 gpu :lolflag:.  i burn iso to dvd disk and system boot from dvd normaly.

---

### Post by yancek on 2023-11-11
In your initial post, you indicated you downloaded Ubuntu from the official site and put it on a 16GB usb drive.  What software or method did you use to put the iso on the flash drive?  Some common software is Ventoy, Rufus, UUI, etc.  So what did you use?  Did you do this from a windows OS?  How old is this computer?  Can you post the exact name of the iso file you downloaded so we know which release you are using?

---

### Post by curstua on 2023-11-12
i'm flash ubuntu from windows 10 i using rufus latest version, my older computer: cpu amd athlon ii x4 640, 8 gb ddr2 ram, and gpu nvidia nvs 310. on this configurations ubuntu 23.10 works fine. but on my primary computer i can't install ubuntu upper 18.04  version. sorry for my english a'm not native speeker i just learn it :KS

---

### Post by yancek on 2023-11-12
I can't read the image in your initial post as the fonts are too small  for me.  Start with this, why 18.04?  You do know that support for it  ended in April of this year, right?  You can get ESM (Extended Security  Maintenance) described/explained at the ubuntu.com site at the link  below and it is at no cost to home users.

[https://ubuntu.com/blog/ubuntu-18-04-eol-for-devices](https://ubuntu.com/blog/ubuntu-18-04-eol-for-devices)

If your hardware is newer than the 18.04 release, that could be part of the problem.  Try booting from differnet usb ports and the other suggestions above if you have not.

---

