---
title: "HP ze4630us laptop wireless network help"
date: 2008-12-06
forum: Hardware
---

### Post by tylerlekang on 2008-12-06
Hello,

Very new to Ubuntu. Decided on a whim to try it out. Ordered free disc from website. I think it's 8.04?

Installed fine and everything seems to work fine except I can't detect or connect to any wireless networks.


The help file said something about going to system->prefs->hardware manager(?) to make sure the device is turned on? But this is no hardware manager to select in the prefs menu.


When I do the iwconfig it does show the device name and hardware address and all that stuff. Maybe the radio isn't turned on or I need to download something?


Any help is appriciated. Thanks

---

### Post by tylerlekang on 2008-12-07
Any ideas? Thanks!

---

### Post by bl4hbl4hbl4h on 2008-12-07
Type in lshw -C network in the terminal and post what comes up.

---

### Post by tylerlekang on 2008-12-07
Here is the output when I type lshw -C network in the terminal:

  *-network:0              
       description: Network controller 
       product: BCM4306 802.11b/g Wireless LAN Controller 
       vendor: Broadcom Corporation 
       physical id: 9 
       bus info: pci@0000:00:09.0 
       version: 02 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm bus_master cap_list 
       configuration: driver=b43-pci-bridge latency=64 module=ssb 
  *-network:1 
       description: Ethernet interface 
       product: DP83815 (MacPhyter) Ethernet Controller 
       vendor: National Semiconductor Corporation 
       physical id: 12 
       bus info: pci@0000:00:12.0 
       logical name: eth0 
       version: 00 
       serial: 00:0d:9d:c8:26:f0 
       size: 10MB/s 
       capacity: 100MB/s 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm bus_master cap_list ethernet physical tp mii fibre 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=natsemi driverversion=2.1 duplex=half latency=90 link=no maxlatency=52 mingnt=11 module=natsemi multicast=yes port=twisted pair speed=10MB/s 
  *-network DISABLED 
       description: Wireless interface 
       physical id: 1 
       logical name: wlan0 
       serial: 00:90:4b:4a:48:96 
       capabilities: ethernet physical wireless 
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g 



"*-network DISABLED" doesn't look good, but how to I enable it? Or what else can I try?


Thanks!

---

### Post by bdoe on 2008-12-07
You have a Broadcom card. These cards generally work fine, but require closed-source firmware to get them working. It's usually part of the driver, but since Linux drivers are open-source, the firmware cannot be legally included.

If you have another means of connecting your laptop to the internet, then use it to go to [this website](http://linuxwireless.org/en/users/Drivers/b43) and follow the directions to download your card's firmware and fwcutter, which is needed to extract the firmware from the Windows driver.

If you do not have any other means of connecting your laptop to the internet, then you will need to download the .tar.gz files to another computer, transfer them to your laptop using a thumbdrive, and then go on from there.

Again, the website: [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

---

### Post by tylerlekang on 2008-12-09
Thanks for the website!

I downloaded both files (although windows decided to change them to tar.tar).


Everything seems like it would work perfectly except when I go to compile the fwcutter using the "make" command I get about 1000 lines worth of error messages. So I copied what I suspect is the problem:

fwcutter.c:33:20: error: stdlib.h: No such file or directory 
fwcutter.c:34:19: error: ctype.h: No such file or directory 
fwcutter.c:35:20: error: string.h: No such file or directory 
fwcutter.c:36:19: error: stdio.h: No such file or directory 
fwcutter.c:37:19: error: errno.h: No such file or directory 
fwcutter.c:38:22: error: sys/stat.h: No such file or directory 
fwcutter.c:39:23: error: sys/types.h: No such file or directory 
fwcutter.c:44:22: error: byteswap.h: No such file or directory 

...

md5.h:4:20: error: stdint.h: No such file or directory 


Obviously this is true as none of those .h files are in the b43-fwcutter-011 directory after I extracted them. Are they supposed to be there? Are those .h files included somewhere with Ubuntu?

Or do I have to download them somewhere? Or could someone be nice and just give me the compiled fwcutter program?



Thanks!

---

### Post by tylerlekang on 2008-12-09
Also I should say that I did not use the "wget" command like the website said because I only have access to the internet on a windows machine, so I had to copy the files to a memory stick and copy them into Ubuntu. 


Maybe I'm making the wrong assumption that "make" can be used generically in any directory?


Please help?

Thanks.

---

### Post by Ayuthia on 2008-12-09
The error messages that you are getting mean that you do not have build-essential installed.  However, you should not have to compile b43-fwcutter if you have your liveCD for Ubuntu.  All you need to do is go to the Terminal and do:
```
sudo apt-cdrom add
```Insert the liveCD when asked.  Next do the following:
```
sudo apt-get update
sudo apt-get install b43-fwcutter
```It will ask you if you want it to fetch the firmware for you.  If you have a working wired internet connection in Ubuntu, go ahead and say yes.  However, if you do NOT, say no.  It should exit properly after the install and you can continue with the steps as if you compiled b43-fwcutter.

---

### Post by tylerlekang on 2008-12-12
Using the CD worked to install b43-fwcutter. 

Then I used b43-fwcutter to cut out the broadcom driver into /lib/firmware.


But the wireless still doesn't work. 


So I think I need to try the other two drivers but now I can't delete the b43 folder from the /firmware folder. It won't let me put it into the trash. "Permission denied" it said, which is incredible that I don't have permission to use my own computer. 


Any ideas? Obviously I'm doing something wrong. I hope it was just the wrong driver that I cut out and not something else. 



Thanks!

---

### Post by tylerlekang on 2008-12-13
Update (because I know you care):

the b43legacy driver was the correct one and wireless now works. 


I also used the sudo rm -R command to delete the b43 files/folder out of the /lib/firmware directory. 



Thanks all for the help!

---

### Post by bdoe on 2008-12-15
Glad you got it working! Wireless on Linux is great when it works, but is a real pain in the *** when it doesn't.

As far as permission to use your computer is concerned, just keep in mind that, even though you may have administrator (root) access, Linux considers you a user until you specifically need elevated access, hence the sudo and gksudo commands. This is a safety feature that follows the principle that one should never routinely use the computer with root privileges - Something Microsoft seems to forget quite a lot.

---

