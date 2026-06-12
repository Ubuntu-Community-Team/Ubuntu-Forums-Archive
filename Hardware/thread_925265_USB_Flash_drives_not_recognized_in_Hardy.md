---
title: "USB Flash drives not recognized in Hardy"
date: 2008-09-20
forum: Hardware
---

### Post by lzclzclzc on 2008-09-20
The drives were working fine in 7.10 but now they aren't even being detected. My logitech g5 usb mouse is working fine, and oddly enough my motorola rizr is working fine too. i can r/w files to the mini-sd flash memory module on the z3.

I used to use XP. the drives were also causing me problem. i think i might've fried the USB 2.0 Enhanced controller so in XP i ran the ports at 1.1 speed and they seem fine. But before with 7.10 the ports worked fine in reading and writing data to and from my usb drives. The drives are not defective since i tested them on another machine. 

Please help this ubuntu noob. thanks

---

### Post by crazycaveman on 2008-09-20
Run the following code from the terminal with the drives plugged in and post the output:

```
lsusb
```

Also, have you tried plugging the flash drives into any other computers?

---

### Post by lzclzclzc on 2008-09-20
here's the output:
(it took quite a while for the output to come out)
-----------------------------------------
lun@zv6009us:~$ lsusb
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 046d:c041 Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000  

--------------------------------------------


looks like ubuntu is not even detecting it.

i have tried using the flash drive on another computer. it works fine.

---

### Post by lzclzclzc on 2008-09-21
bump?

---

### Post by Eniak on 2008-09-26
I'm having the same problem as well... The drive lights and blinks like something is being red. With *fdisk -l* I can't see anything, but with *lsusb* I can see it... I tested the drive in another computer and it worked fine, also have plugged an usb keyboard here... So defective drive or usb ports doesn't seem to be the problem. 
  Funny that right after I managed to install some codecs here I got some videos from this same drive to test and it appeard... not anymore :(

  Here are my *fdisk* and *lsusb* outputs...

$ sudo fdisk -l
/dev/hda
        #                    type name                 length   base     ( size )  system
/dev/hda1     Apple_partition_map Apple                    63 @ 1        ( 31.5k)  Partition map
/dev/hda2         Apple_Bootstrap untitled               1954 @ 64       (977.0k)  NewWorld bootblock
/dev/hda3         Apple_UNIX_SVR2 untitled           28162110 @ 2018     ( 13.4G)  Linux native
/dev/hda4         Apple_UNIX_SVR2 swap                1333984 @ 28164128 (651.4M)  Linux swap

Block size=512, Number of Blocks=29498112
DeviceType=0x0, DeviceId=0x0

$ lsusb
0Bus 002 Device 002: ID 1307:0165 Transcend Information, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 0e6a:6001 Megawin Technology Co., Ltd 
Bus 001 Device 001: ID 0000:0000  



  I'm running Ubuntu 8.04 on an Ibook G3 500mhz (a.k.a. Dual USB... eheheheheh... Ironic...)

EDIT: I manage to get my flash drives working, they are not automounting as they did once but at least is working...

I took as reference [this]("http://ubuntuforums.org/showthread.php?t=928924&highlight=usb") topic

I found out that my flash drive wasn't formated and that's why I couldn't get its dev name with *dmesg | tail* ... Once I formated it (in another computer that could read it) *dmesg | tail* gave me its name and I ran the following commands:

$ sudo mkdir /media/edrive
$ sudo mount /sda1 /media/edrive

edrive was the name I chose for the mounting point, it can b anything and /sda1 is the dev name that I got with *dmesg | tail*.

---

