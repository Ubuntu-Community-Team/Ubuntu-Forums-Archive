---
title: "Installing Ubuntu 64 Bit Odyssey"
date: 2006-06-16
forum: Hardware &amp; Laptops
---

### Post by togume on 2006-06-16
The following is my interesting experience installing ubuntu on a 64 bit machine:

Setup:
Athlon 3800+
2Gb ram
2 x 36.7Gb wd sata raptors
ATI X800 video card

I was "happily?" using windows xp pro 64 on one raptor and the idea was to install ubuntu dapper 64 on the other and choose using grub. I put in the dapper cd and to my surprise the X server failed to start and I only had access to a terminal (and to view the error output). After a little research I learned that this was a bug in the install and that the wrong driver was being loaded into the xorg.conf. To solve the problem I had to replace the "Driver" entry under "Device" in the xorg.conf from "ATI" to "Radeon". Saved it and tried starting x and gnome by using "startx". 

X started and so did gnome and I was able to play with ubuntu for a little while before deciding to install it. I double clicked on the desktop "Install" icon, but I got an error related to the Xauthority file not being able to be read. Immediately I thought this was a permission problem and navigated to the /home/ubuntu/Xauthority... file and found out that it had limited permissions. After chmodding it to 2775 I was able to launch the installer. I chose the correct, and brand new, hard drive (sata raptor #2) for ubuntu to be installed in. Everything seemed to go well from this point on, but little did I know the fun was just starting. 

When the system rebooted I was greeted with a failed to load operating system error... uh oh... It was more than likely my mistake for not unplugging the hard drive, but I could have sworn I selected the correct one. 

After accepting the demise of my windows drive, I tried booting the ubuntu drive only to find a "grub error 21"... Ok then... 

So, now I have my windows back online and will try redoing the ubuntu raptor sometime in the near future.

Any comments are welcome.

Tomas

---

### Post by bruce89 on 2006-06-16
Try the Alternate install CD. - [http://mirror.cs.umn.edu/ubuntu-releases/6.06/ubuntu-6.06-alternate-amd64.iso.torrent](http://mirror.cs.umn.edu/ubuntu-releases/6.06/ubuntu-6.06-alternate-amd64.iso.torrent) - torrent.

---

### Post by togume on 2006-06-16
Thank you Bruce, I did not know about this. I will try this and hopefully remember to unplug master sata #1...

---

### Post by togume on 2006-06-17
I tried using the alternate disc of the intstall and the process was similar with the difference that I used the text installer instead of the live installer. It installed as it had before and the results were the same the first time I booted the system; X server errored out. 

As before, I logged into a terminal and looked at the xorg.conf file (/etc/X11/xorg.conf) and the bug was still there. Apparently the 64 bit installer does not put the right driver into the file and the only thing I needed to change to get it working was to change the "device" driver from "ati" to "radeon". To my pleasent surprise, I had 1280*1024 resolution once X/Gnome started. 

I will now tackle the grub from multiple drives as well as dual monitor setup.

---

