---
title: "No  proprietary drivers in Ubuntu"
date: 2018-10-28
forum: Hardware
---

### Post by RobGoss on 2018-10-28
Hello everyone, I have a question about installing ** proprietary drivers** in Ubuntu. I notice when I go to software and updates and search for proprietary drivers there is none listed, any reason why it's not showing any available drivers. thanks so much

---

### Post by ajgreeny on 2018-10-28
Probably because there are none available.

What hardware have you that you believe needs a driver not already installed and in use?
Let's see the output of **inxi -F**
Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

---

### Post by dino99 on 2018-10-28
With a standard ubuntu installation, and 'restricted' archive enabled, you do have the main drivers listed.

For example, 'nvidia' is  one of them, and is indeed listed.
What are you glancing about ?

---

### Post by RobGoss on 2018-10-28
I have a old DELL INSPIRON 531 running Linux lite, seeing it's Ubuntu based I ask this question here. The machine is running well but after a few minute the screen get all distorted and cannot do anything. I managed to run the following code and was able to see the available drivers to install. It's been running for a few hours now and no issues

Run this code:

```
 sudo add-apt-repository ppa:graphics-drivers/ppa
```

 Output of** inxi -F**

```

System:    Host: -Inspiron-531 Kernel: 4.15.0-38-generic x86_64
           bits: 64
           Desktop: Xfce 4.12.3 Distro: Ubuntu 18.04.1 LTS
Machine:   Device: desktop System: Dell product: Inspiron 531 v: 00 serial: N/A
           Mobo: Dell model: 0RY206 v: &#65533;&#65533;&#65533; serial: N/A
           BIOS: Dell v: 1.0.6 date: 09/06/2007
CPU:       Dual core AMD Athlon 64 X2 4000+ (-MCP-) cache: 1024 KB
           clock speeds: max: 2100 MHz 1: 1800 MHz 2: 1800 MHz
Graphics:  Card: NVIDIA C61 [GeForce 6150SE nForce 430]
           Display Server: x11 (X.Org 1.19.6 )
           drivers: nouveau (unloaded: modesetting,fbdev,vesa)
           Resolution: 1366x768@59.79hz
           OpenGL: renderer: NV4C version: 2.1 Mesa 18.0.5
Audio:     Card NVIDIA MCP61 High Def. Audio driver: snd_hda_intel
           Sound: Advanced Linux Sound Architecture v: k4.15.0-38-generic
Network:   Card-1: NVIDIA MCP61 Ethernet driver: forcedeth
           IF: enp0s7 state: down mac: 00:1a:a0:69:78:b2
           Card-2: Belkin F7D1101 v1 Basic Wireless Adapter [Realtek RTL8188SU]
           driver: r8712u
           IF: wlxec1a59bfd3b4 state: N/A mac: N/A
Drives:    HDD Total Size: 250.0GB (7.0% used)
           ID-1: /dev/sda model: Hitachi_HDT72502 size: 250.0GB
Partition: ID-1: / size: 229G used: 17G (8%) fs: ext4 dev: /dev/sda1
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 13.0C mobo: N/A
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 179 Uptime: 3:29 Memory: 1609.1/3880.7MB
           Client: Shell (bash) inxi: 2.3.56     
```

If you look at the screen shot below it will show you what drivers I have installed. Seems to be ok now

---

### Post by deadflowr on 2018-10-28
If it's a card that could only use the 304 driver then it seem right since the 304 driver is no longer supported for new Ubuntu releases.
(Or more technically, the driver won't build for new kernel version, something like any kernel newer than 4.14, maybe older.)
Here's a thread on that:
[https://ubuntuforums.org/showthread.php?t=2395766]("https://ubuntuforums.org/showthread.php?t=2395766")

---

### Post by RobGoss on 2018-10-28
> **deadflowr said:**
> If it's a card that could only use the 304 driver then it seem right since the 304 driver is no longer supported for new Ubuntu releases.
(Or more technically, the driver won't build for new kernel version, something like any kernel newer than 4.14, maybe older.)
Here's a thread on that:
[https://ubuntuforums.org/showthread.php?t=2395766]("https://ubuntuforums.org/showthread.php?t=2395766")

Thanks so much for the link

I really wanted** Ubuntu mate** on this machine but as I stated it would not give me a option to install any drivers. The screen get all messed up before I can change anything

Is there anyway to get Ubuntu mate installed with the correct drivers and all?

I'm assuming I could try running the same code: To get Ubuntu mate running on this machine what you think?
```
 sudo add-apt-repository ppa:graphics-drivers/ppa
```

Big thanks

---

### Post by deadflowr on 2018-10-28
I'm not sure the ppa version works either since it's now almost a year old and built for a very early bionic development kernel.

The link I posted has a link by the last poster for a workaround, but you have to get dirty and do the patching yourself:
[https://adufray.com/blog/2018/06/02/nvidia-304-127-on-bionic]("https://adufray.com/blog/2018/06/02/nvidia-304-127-on-bionic")

But it should only be a one time patch, since the driver will never be updated.

---

### Post by RobGoss on 2018-10-28
Thanks Deadflowr, I'll see if that works thank you

Thanks everyone for the help

---

