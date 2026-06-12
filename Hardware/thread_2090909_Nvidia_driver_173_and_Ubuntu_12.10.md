---
title: "Nvidia driver 173 and Ubuntu 12.10"
date: 2012-12-03
forum: Hardware
---

### Post by DarkHam on 2012-12-03
I installed ubuntu 12.10 in a pc with nvidia geforce fx 5900, only supported by nvidia driver 173. The package nvidia-173 in the repos don't support xorg 1.13 ([https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173/+bug/1064192](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173/+bug/1064192)) like the newest official nvidia 173 version here [http://www.nvidia.com/object/linux-display-ia32-173.14.36-driver.html](http://www.nvidia.com/object/linux-display-ia32-173.14.36-driver.html) . I installed it, but i've 3d desktop issue, on unity (blank screen and pointer) and gnome shell (desktop with freezed folders with no action possible, and working pointer).Absolutely no problems with 2d desktops like gnome with no effects and cinnamon 2d. Direct rendering are ok and the driver seems to be installed right. Unity/Xorg/Driver/Kernel issue?

[http://pastebin.com/4zUY5hqd](http://pastebin.com/4zUY5hqd) that's my glxingfo 
[http://pastebin.com/H5b3wSBq](http://pastebin.com/H5b3wSBq) that's my Xorg.0.log

---

### Post by DarkHam on 2012-12-04
Nobody with a GeForce FX/6/7 can try to install this driver?:)

---

### Post by dannyboy79 on 2012-12-04
i am battling trying to get a GeForce 6200 working with a new 23" Olevia TV via VGA. All the nvidia binaries (whether from repos or website) result in the TV going into DPMS SUSPEND/STANDBY and will not wake up no matter what. Sorry, can't help you. Plus, I am using 10.04, not 12.10.

---

### Post by DarkHam on 2012-12-05
Nouveau only, for 12.10 users with nvidia-173 supported cards?Is in 12.04 the same?

---

### Post by itpro007ca on 2012-12-05
I'm running Ubuntu Server 12.04 with Nvidia 173 (post Updates,Current Updates).Works perfect.

Hardware:
*Biostar NF61S AM2 Motherboard
*AMD64x2 4 Ghz CPU
*2 GB DDR2 667 Mhz
*WD 160 GB SATA2
*LG DVDRW
*Nvidia GEforce 6100 256 MB Integrated Video

Emachines 180HV 20" LCD Monitor @1366x768

I had to do a reinstall(a few years back I was running Ubuntu Desktop 11.04 -no problems),but,before that,on my initial install,I selected the Nvidia 173 driver(recommended) and upon reboot,the screen just stalled at the default(peach?)screen,wouldn't draw.

I was almost going to give up and do a reinstall,when I hit upon the idea to try Ubuntu 2d.It worked perfectly,so I changed the Nvidia driver to 173 Post Update(top of the list).It worked,but gave me 1280x900 (LAPTOP),and fat icons!

So,I tried again and this time,I changed the driver to the one I mentioned above and had a perfect 1366x768 and after hitting the 'autoconfig' button on the monitor,it was even better.

I did have to update Grub with 'nomodeset' to get rid of the 'input not supported' box at the start and shutdown.

---

### Post by DarkHam on 2012-12-06
must i set, after the driver installation, something in xorg.conf?

[http://paste.ubuntu.com/1415225/](http://paste.ubuntu.com/1415225/) 

This is the mine, actually, after the nvidia .run installation, and the automatic nvidia-xconfig.

---

### Post by dannyboy79 on 2012-12-07
view your lsmod output, if you see nouveau within that list then that means that the nvidia driver and nouveau are fighting to control the graphics card. You have to blacklist the nouveau so it doesn't load upon startup. You should also review your /var/log/Xorg.0.log file

---

### Post by DarkHam on 2012-12-07
Then, [http://paste.ubuntu.com/1417285/](http://paste.ubuntu.com/1417285/) that's my lsmod result.

---

### Post by dannyboy79 on 2012-12-07
i don't see nouveau listed so it doesn't appear to be a driver conflict. not sure man, like I said I am battling my own issue with this stupid TV not getting the correct EDID info from my GeForce 6200. Sorry I can't help.

---

