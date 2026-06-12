---
title: "Geforce 9300 issue"
date: 2010-12-12
forum: Hardware
---

### Post by mxw on 2010-12-12
Hi all,
 
I am a complete novice when it comes to linux so i am in dire need of help. I think this is the right place as i think its hardware issue? not sure though!
 
I am in the proccess of setting up a mini-itx system to run ubuntu and generally be my playground for learning linux. 
 
Problem:
 
I installed and activated a Nvidia driver. On reboot my system does not boot up properly. It just locks up everything and then lists aload of system messages. I cannot scroll up to see what its about becuase nothing works but the last thing on the list is this
 
[<ffffffff8100af2>] system_call_fastpath+0x16/0x1b
 
After that nothing works. My suspition is that the system goes to startx finds the nvidia driver, goes to startup the graphics and boom instantaly turns into a dribbling mess. I cannot access anything through recovery mode becuase it does exactly the same. i am completly at a loss. I am running a 64bit system so maybe this has some bearing?
 
My system spec:
 
Zotac GeForce 9300-ITX WIFI mobo
intel core 2 duo 3Ghz
4GB kingston RAM 1333
1TB Hitachi HDD
 
Ubuntu 10.10 64 bit
 
Cheers for any help

---

### Post by mxw on 2010-12-13
Just to add more info. I installed the nvidia proprietary drivers. I tried both the recommended (version current) and the 177 driver. Both crash the system on reboot. Id like to provide the logs but i cannot get into command line to get to them. Anyone know how i would go about this?

---

### Post by bkapps on 2010-12-13
I had the same problem with a geforce 8400gs on 32-bit, i ended up just returning the card and living with my intel GMA 950

---

### Post by happyisland on 2010-12-13
Hey all,

I have this same mobo/wifi combo and same issue. The latest flavor of ubuntu that I've been able to get to work is 9.10. Don't know why, but all later versions just won't boot.

The included wifi doesn't work either, but that's for another thread...

---

### Post by Gnea on 2011-01-26
Add me to the list that owns this hardware.  I can't even get Ubuntu to install!  The best I can do with amd64 10.04 is to get the server version booted via usb, and after that, nothing.  It tries to initialize the video (probably with the vesa driver) and the whole screen goes blank and the monitor looks like it's going into standby mode.  Also, the mouse won't work and forget about wifi!  The CPU is a Pentium 4 dualcore, but it won't find the second core, seems to be missing a CPU flag 'nx' or something similar (I don't recall the exact flag).  Pretty disappointed with this rig so far and even more so with Ubuntu's lack of support on it.

Here's the setup:
Zotac Geforce 9300 w/ wifi
Pentium 4 3.00ghz dualcore cpu
4GB Kingston DDR3 ram
500GB WD SATA-3 hard drive

---

### Post by eeverson on 2011-04-03
I had the same issues when using the x64 version. I have since installed the x32 version and everything is working fine... with the exception of WiFi stopping after a couple of minutes.

Cheers
Euge

---

### Post by eeverson on 2011-04-11
Quick Update...

I re did the USB boot disk with 10.10. x64 and it installed fine so I am guessing the original issue was with a bad boot device. I am still getting disconnection issues with the WiFi though.

---

### Post by Gnea on 2011-07-20
It's been awhile now, I finally got the system to work correctly, it needed a bios update which I found on the website.  Lining up the correct version to the numbers printed on the motherboard itself was interesting, but now I have a fully working system, sans the wireless driver.  :KS

Running lshw -C Network produces the following:

```


  *-network:0 DISABLED
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:00:00:00:00:01
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=802.11-a/b/g


```

Which is nice, it at least knows that SOMETHING is there, but running:  `sudo ifconfig eth1 up` hard-locks the system.  The caps lock and scrolllock LEDs blink and the only way out of it is to hit the reset or power buttons as SYSRQ is completely blocked out. ](*,)

Still hunting for a driver.... anyone found it yet?  :confused:

---

