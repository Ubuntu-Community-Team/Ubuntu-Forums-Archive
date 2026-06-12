---
title: "getting a webcam to work."
date: 2009-01-03
forum: Hardware
---

### Post by Ewan the moomintroll on 2009-01-03
Hi,
I have a Lili webcam: [http://www.unitedpepper.org.uk/proddata.php?partno=E1800&desc1=United%20Pepper%20Lili%20Webcam%20(Red)]("http://www.unitedpepper.org.uk/proddata.php?partno=E1800&desc1=United%20Pepper%20Lili%20Webcam%20(Red)") and I can't get it working. When I plug it in nothing happens, and the dmesg is: 
[41688.723334] usb 4-4: new high speed USB device using ehci_hcd and address 7
[41688.856374] usb 4-4: unable to read config index 0 descriptor/start: -71
[41688.856387] usb 4-4: chopping to 0 config(s)
[41688.857994] usb 4-4: string descriptor 0 read error: -71
[41688.890680] usb 4-4: no configuration chosen from 0 choices

Can anyone help me set it up, or should I give up?

Thanks,
Ewan

---

### Post by teaker1s on 2009-01-03
```
lsub
``` find the exact vendor and product id and then you can search for driver.

---

### Post by Ewan the moomintroll on 2009-01-04
I'm not sure I follow... the webcam is made by a company called united pepper.
What do I do with lsub?

---

### Post by Wobblybob on 2009-01-04
think Teaker1s meant to say get the result of lsusb, with webcam plugged in, type this into a terminal and check the results, it should give you more details of the cam and enable a better search result for help.

---

### Post by teaker1s on 2009-01-04
correct you need webcam plugged in and terminal type the code 
```
lsusb
``` often with devices the makers name is useless and we can find much more by vendor and product id. example

daniel@daniel-desktop:~$ lsusb
Bus 002 Device 004: ID 0bda:0111 Realtek Semiconductor Corp. Card Reader
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0a5c:200a Broadcom Corp. Bluetooth dongle
Bus 001 Device 003: ID[COLOR="DarkRed"] 046d:08af[/COLOR] Logitech, Inc. QuickCam Easy/Cool
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

note the red string is my webcam vendor and product id, find the whole line and paste as a reply

---

### Post by Ewan the moomintroll on 2009-01-04
Bus 004 Device 003: ID 0c45:6270 Microdia U-CAM PC Camera NE878
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 093a:2510 Pixart Imaging, Inc. 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by teaker1s on 2009-01-04
[COLOR="Red"]Bus 004 Device 003: ID 0c45:6270 Microdia U-CAM PC Camera NE878[/COLOR]

don't seem to be able to find MUCH support for it in common drivers
found  this discussion
[http://www.linuxmint.com/forum/viewtopic.php?f=49&t=17132]("http://www.linuxmint.com/forum/viewtopic.php?f=49&t=17132")

---

### Post by Ewan the moomintroll on 2009-01-05
Thanks a lot for finding that.
I'm trying to follow:
```

sudo aptitude install kernel-package linux-source build-essential git-core exuberant-ctags cheese
git clone http://repo.or.cz/r/microdia.git
cd microdia
make
sudo insmod ./microdia.ko
cheese
```
what do I do with this bit: "kernel-package linux-source"?

---

### Post by teaker1s on 2009-01-05
```
sudo aptitude install nameofpackage nameofpackage1
``` will install each package listed. have you tried plugging camera in then
```
cheese
```

can you see yourself on camera?

if no try rebooting and again
```
cheese
```
if nothing post output of 
```
lsmod
```

---

### Post by Ewan the moomintroll on 2009-01-05
When I enter: 
```
sudo insmod ./microdia.ko

```
I get:
```
insmod: can't read './microdia.ko': No such file or directory

```

I can't see myself.
My lsmod output is...long; is there any part of it you need?

---

### Post by teaker1s on 2009-01-05
[http://ubuntuforums.org/showthread.php?t=921153&highlight=0c45%3A6270]("http://ubuntuforums.org/showthread.php?t=921153&highlight=0c45%3A6270") Try this first
 if no success then post in that thread and also:-

I would suggest posting on linux mint forum thread,this is because I honestly don't know how to proceed further and it's not a popular or well supported model.

I tried as you have and can not get module installed,maybe the guys on the thread will have some more trouble shooting suggestions:-unless anyone on these forums can suggest anything

---

### Post by linux6994 on 2009-01-05
Cheese Webcam Booth and XawTV will both most likely work fine, it's Camorama and Kopote for me that will not.

---

### Post by Ewan the moomintroll on 2009-01-07
I'm trying to follow these instructions:
[http://groups.google.com/group/microdia/web/testing-microdia-driver-draft](http://groups.google.com/group/microdia/web/testing-microdia-driver-draft)

Can anyone help?

Edit: I get the following when I try:

bellamy@a-black-box:~$ git clone [http://repo.or.cz/r/microdia.git](http://repo.or.cz/r/microdia.git)
fatal: destination directory 'microdia' already exists.

bellamy@a-black-box:~$ cd microdia

bellamy@a-black-box:~/microdia$ make
make -C /lib/modules/2.6.27-9-generic/build SUBDIRS=/home/bellamy/microdia modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-9-generic'
  CC [M]  /home/bellamy/microdia/sn9c20x-usb.o
In file included from include/linux/gfp.h:4,
                 from include/linux/kmod.h:22,
                 from include/linux/module.h:13,
                 from /home/bellamy/microdia/sn9c20x-usb.c:27:
include/linux/mmzone.h:18:26: error: linux/bounds.h: No such file or directory
include/linux/mmzone.h:197:5: warning: "MAX_NR_ZONES" is not defined
In file included from include/linux/gfp.h:4,
                 from include/linux/kmod.h:22,
                 from include/linux/module.h:13,
                 from /home/bellamy/microdia/sn9c20x-usb.c:27:
include/linux/mmzone.h:218: error: &#8216;MAX_NR_ZONES&#8217; undeclared here (not in a function)
make[2]: *** [/home/bellamy/microdia/sn9c20x-usb.o] Error 1
make[1]: *** [_module_/home/bellamy/microdia] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'
make: *** [driver] Error 2

bellamy@a-black-box:~/microdia$ insmod ./sn9c20x.ko
insmod: can't read './sn9c20x.ko': No such file or directory

I'm pretty sure I'm doing it wrong; I'm using linux kernel 2.6.27-9 and ubuntu 8.10.

---

### Post by SomethingFishy on 2009-01-19
Any luck yet Mr Moomintroll?  I bought a Lili webcam a couple of months ago and after reading various rather difficult to understand threads on here I decided to email United Pepper about Linux support.  They replied to say they were testing a solution so I thought I'd relax about it til after Christmas.  I've just emailed them again to see how they're getting on.  Let me know if you'd like the support guy's email address :smile:

---

