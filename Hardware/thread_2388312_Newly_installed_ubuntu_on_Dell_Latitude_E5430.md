---
title: "Newly installed ubuntu on Dell Latitude E5430"
date: 2018-03-31
forum: Hardware
---

### Post by moto1860 on 2018-03-31
Hi all, just installed ubuntu on a Dell Latitude

What hardware do I need to update? Touchpad is very twichy.

```
avo@avo-Latitude-E5430-non-vPro:~$ sudo apt-get install inxi && inxi -Fxxxzc0
[sudo] password for avo: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  gawk hddtemp libsigsegv2 lm-sensors mesa-utils net-tools
Suggested packages:
  gawk-doc ksensors fancontrol read-edid i2c-tools
The following NEW packages will be installed:
  gawk hddtemp inxi libsigsegv2 lm-sensors mesa-utils net-tools
0 upgraded, 7 newly installed, 0 to remove and 0 not upgraded.
Need to get 918 kB of archives.
After this operation, 3,785 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://ci.archive.ubuntu.com/ubuntu artful/main amd64 libsigsegv2 amd64 2.11-1 [13.2 kB]
Get:2 http://ci.archive.ubuntu.com/ubuntu artful/main amd64 gawk amd64 1:4.1.4+dfsg-1 [401 kB]
Get:3 http://ci.archive.ubuntu.com/ubuntu artful/main amd64 net-tools amd64 1.60+git20161116.90da8a0-1ubuntu1 [194 kB]
Get:4 http://ci.archive.ubuntu.com/ubuntu artful/universe amd64 hddtemp amd64 0.3-beta15-52 [52.8 kB]
Get:5 http://ci.archive.ubuntu.com/ubuntu artful/universe amd64 inxi all 2.3.37-1 [140 kB]
Get:6 http://ci.archive.ubuntu.com/ubuntu artful/universe amd64 lm-sensors amd64 1:3.4.0-4 [85.5 kB]
Get:7 http://ci.archive.ubuntu.com/ubuntu artful/universe amd64 mesa-utils amd64 8.3.0-5 [31.9 kB]
Fetched 918 kB in 0s (1,135 kB/s)
Preconfiguring packages ...
Selecting previously unselected package libsigsegv2:amd64.
(Reading database ... 165102 files and directories currently installed.)
Preparing to unpack .../libsigsegv2_2.11-1_amd64.deb ...
Unpacking libsigsegv2:amd64 (2.11-1) ...
Setting up libsigsegv2:amd64 (2.11-1) ...
Selecting previously unselected package gawk.
(Reading database ... 165109 files and directories currently installed.)
Preparing to unpack .../0-gawk_1%3a4.1.4+dfsg-1_amd64.deb ...
Unpacking gawk (1:4.1.4+dfsg-1) ...
Selecting previously unselected package net-tools.
Preparing to unpack .../1-net-tools_1.60+git20161116.90da8a0-1ubuntu1_amd64.deb ...
Unpacking net-tools (1.60+git20161116.90da8a0-1ubuntu1) ...
Selecting previously unselected package hddtemp.
Preparing to unpack .../2-hddtemp_0.3-beta15-52_amd64.deb ...
Unpacking hddtemp (0.3-beta15-52) ...
Selecting previously unselected package inxi.
Preparing to unpack .../3-inxi_2.3.37-1_all.deb ...
Unpacking inxi (2.3.37-1) ...
Selecting previously unselected package lm-sensors.
Preparing to unpack .../4-lm-sensors_1%3a3.4.0-4_amd64.deb ...
Unpacking lm-sensors (1:3.4.0-4) ...
Selecting previously unselected package mesa-utils.
Preparing to unpack .../5-mesa-utils_8.3.0-5_amd64.deb ...
Unpacking mesa-utils (8.3.0-5) ...
Setting up hddtemp (0.3-beta15-52) ...
Processing triggers for ureadahead (0.100.0-20) ...
ureadahead will be reprofiled on next reboot
Setting up gawk (1:4.1.4+dfsg-1) ...
Processing triggers for libc-bin (2.26-0ubuntu2.1) ...
Setting up lm-sensors (1:3.4.0-4) ...
Created symlink /etc/systemd/system/multi-user.target.wants/lm-sensors.service &#8594; /lib/systemd/system/lm-sensors.service.
Setting up inxi (2.3.37-1) ...
Processing triggers for systemd (234-2ubuntu12.3) ...
Processing triggers for man-db (2.7.6.1-2) ...
Setting up net-tools (1.60+git20161116.90da8a0-1ubuntu1) ...
Setting up mesa-utils (8.3.0-5) ...
Processing triggers for ureadahead (0.100.0-20) ...
System:    Host: avo-Latitude-E5430-non-vPro Kernel: 4.13.0-37-generic x86_64
           bits: 64 gcc: 7.2.0
           Desktop: Gnome 3.26.2 (Gtk 3.22.25-0ubuntu0.1) info: gnome-shell dm: gdm3
           Distro: Ubuntu 17.10
Machine:   Device: laptop System: Dell product: Latitude E5430 non-vPro v: 01 serial: N/A
           Mobo: Dell model: 0MYF02 v: A00 serial: N/A
           BIOS: Dell v: A07 date: 10/08/2012
           Chassis: type: 9 serial: N/A
Battery    BAT0: charge: 16.7 Wh 76.9% condition: 21.7/62.2 Wh (35%)
           volts: 11.1/11.1
           model: Samsung SDI DELL 5CGM425 Li-ion serial: <filter>status: Discharging cycles: 0
CPU:       Dual core Intel Core i5-3320M (-HT-MCP-)
           arch: Ivy Bridge rev.9 cache: 3072 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 10365
           clock speeds: min/max: 1200/3300 MHz 1: 2591 MHz 2: 2591 MHz
           3: 2591 MHz 4: 2591 MHz
Graphics:  Card: Intel 3rd Gen Core processor Graphics Controller
           bus-ID: 00:02.0 chip-ID: 8086:0166
           Display Server: wayland (X.Org 1.19.5 ) driver: i915
           Resolution: 1600x900@59.95hz
           OpenGL: renderer: Mesa DRI Intel Ivybridge Mobile
           version: 4.2 Mesa 17.2.8 (compat-v: 3.0) Direct Render: Yes
Audio:     Card Intel 7 Series/C216 Family High Def. Audio Controller
           driver: snd_hda_intel bus-ID: 00:1b.0 chip-ID: 8086:1e20
           Sound: Advanced Linux Sound Architecture v: k4.13.0-37-generic
Network:   Card-1: Broadcom Limited BCM43228 802.11a/b/g/n
           driver: wl bus-ID: 02:00.0 chip-ID: 14e4:4359
           IF: wlp2s0 state: up mac: <filter>
           Card-2: Broadcom Limited NetXtreme BCM5761 Gigabit Ethernet PCIe
           driver: tg3 v: 3.137 bus-ID: 0c:00.0 chip-ID: 14e4:1681
           IF: enp12s0 state: down mac: <filter>
Drives:    HDD Total Size: 500.1GB (1.4% used)
           ID-1: /dev/sda model: ST500LX003 size: 500.1GB
           serial: <filter> temp: 45C
Partition: ID-1: / size: 458G used: 6.5G (2%) fs: ext4 dev: /dev/sda1
RAID:      System: supported: N/A
           No RAID devices: /proc/mdstat, md_mod kernel module present
           Unused Devices: none
Sensors:   System Temperatures: cpu: 63.0C mobo: N/A
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 226 Uptime: 19 min Memory: 1755.3/3819.0MB
           Init: systemd v: 234 runlevel: 5 Gcc sys: 7.2.0
           Client: Shell (bash 4.4.121 running in gnome-terminal-) inxi: 2.3.37
avo@avo-Latitude-E5430-non-vPro:~$ 


```

---

### Post by TheFu on 2018-03-31
Can't really understand the question from what has been provided.
```
sudo apt update
sudo apt upgrade

```
That should do it. Run those once a week.

If you want proprietary drivers, there is a button somewhere. Mainly that is for GPU support. Do it once, then do the update/upgrade stuff.

The install output is useless. Why included?

Google found this guide:
[http://www.dell.com/support/article/us/en/04/sln151664/how-to-install-ubuntu-linux-on-your-dell-pc](http://www.dell.com/support/article/us/en/04/sln151664/how-to-install-ubuntu-linux-on-your-dell-pc) 
and this post-install guide: [http://www.dell.com/support/article/us/en/04/sln151748/how-to-configure-ubuntu-linux-after-its-first-installed-on-your-dell-pc](http://www.dell.com/support/article/us/en/04/sln151748/how-to-configure-ubuntu-linux-after-its-first-installed-on-your-dell-pc)

---

### Post by oldfred on 2018-03-31
Another Dell. 
Lots of issues and solutions discussed, may be similar.
[https://ubuntuforums.org/showthread.php?t=2317843](https://ubuntuforums.org/showthread.php?t=2317843)


Have you updated UEFI/BIOS to latest version from Dell?

---

### Post by moto1860 on 2018-03-31
> **TheFu said:**
> Can't really understand the question from what has been provided.
```
sudo apt update
sudo apt upgrade

```
That should do it. Run those once a week.

If you want proprietary drivers, there is a button somewhere. Mainly that is for GPU support. Do it once, then do the update/upgrade stuff.

The install output is useless. Why included?

Google found this guide:
[http://www.dell.com/support/article/us/en/04/sln151664/how-to-install-ubuntu-linux-on-your-dell-pc](http://www.dell.com/support/article/us/en/04/sln151664/how-to-install-ubuntu-linux-on-your-dell-pc) 
and this post-install guide: [http://www.dell.com/support/article/us/en/04/sln151748/how-to-configure-ubuntu-linux-after-its-first-installed-on-your-dell-pc](http://www.dell.com/support/article/us/en/04/sln151748/how-to-configure-ubuntu-linux-after-its-first-installed-on-your-dell-pc)
I was mainly concerned about the jumpy touchpad (and thought I needed drivers for it), I've found a solution here:  [https://askubuntu.com/questions/894679/ubuntu-touchpad-issues-mouse-pointer-jumps-around?utm_medium=organic&utm_source=google_rich_qa&utm_campaign=google_rich_qa](https://askubuntu.com/questions/894679/ubuntu-touchpad-issues-mouse-pointer-jumps-around?utm_medium=organic&utm_source=google_rich_qa&utm_campaign=google_rich_qa)

I posted the install output as per suggestion here: 
> **jeremy31 said:**
> I would start a new thread in hardware and say what other hardware isn't working. It might help to give some idea of what hardware you have ```
sudo apt-get install inxi && inxi -Fxxxzc0
```
and paste the results using code tags

Use the thread tools near the top right of page to mark as solved

Thanks for the guide as I hadn't have the chance to look at it anyway. My win crashed and I needed a running OS pronto.

> **oldfred said:**
> Another Dell. 
Lots of issues and solutions discussed, may be similar.
[https://ubuntuforums.org/showthread.php?t=2317843](https://ubuntuforums.org/showthread.php?t=2317843)


Have you updated UEFI/BIOS to latest version from Dell?Most definitely I haven't, not sure how to do it now but I'm going to read the linked thread.

---

### Post by TheFu on 2018-04-01
Ah ... I didn't see the other post.

The **inxi** output WAS definitely helpful. If there aren't issues doing installs/upgrades, then it doesn't help to show all of that. Actually, when I saw all that output and it wasn't a install issue, I didn't read anything more until a few hours later.  Sometimes too many details are bad. It is hard to know when that is.  But since you included it, I assumed it was an install/upgrade problem, hence provided the commands that I did.   At least that was my thought process.  I'd figured you didn't do the initial patching during install, so fresh drivers weren't downloaded.   "Newly installed Ubuntu" ... see my thought process?

For the future, best to put the laptop make and model in the title for any HW issues.  "Dell xyz touchpad prob" ... for example. People that have a dell and solved the touchpad issue will read quickest that way.  I have a dell 1558, but never had any touchpad issues.  For issues likely unrelated to HW, it is still helpful to mention it, but not specifically in the title.  A good title is everything to get viewers who might be able to help.  A less good title, gets responses from people like me, who are clueless.

---

### Post by moto1860 on 2018-04-04
edit

---

