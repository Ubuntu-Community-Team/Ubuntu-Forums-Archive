---
title: "Bamboo One and 7.10"
date: 2008-04-20
forum: Hardware &amp; Laptops
---

### Post by SnakeArtworX on 2008-04-20
Hi.

I'm looking for _working_ solution for Wacom Bamboo One (CTF-430) pen tablet and Gutsy Gibbon with kernel 2.6.22-14-generic. The following posts are not working in my case:

[http://ubuntuforums.org/showthread.php?t=617699](http://ubuntuforums.org/showthread.php?t=617699)
[http://ubuntuforums.org/showthread.php?t=631881](http://ubuntuforums.org/showthread.php?t=631881)
[http://ubuntuforums.org/showthread.php?t=488013](http://ubuntuforums.org/showthread.php?t=488013)

There's still wacom file missing in /dev/input/ and none of events are responding.

I've tried to use archives from linux-wacom-project site,but still nothing. I'm not intersted with solutions for Bamboo or Bamboo Fun, because I think that they're working in a little different way than Bamboo One, which makes unable to use it with all these How-To's.

I've tried to talk with people at #Ubuntu channel at freenode, but nobody has an idea what could be a cause of my problem. I've heard that in Hardy-Heron will be a full support for new Wacom tablets "out-of-the-box", but I cannot wait until final release and I don't want to reinstall everything, only because of support for new hardware, which could work in previous release as well (only after correct configuration process).
If there is anyone with working Bamboo One (not Bamboo or Fun) please share your experience. I will be grateful for "step-by-step command-by-command" solution. There are plenty of people like me with the same problem. 

P.S. Is there any way to "clean up the mess" after non-successful installation of sources? I want to try everything from very beginning, but there are files not deletable by deinstallation of wacom packages.

I'm sorry if that post looks stupid, but I'm losing my patience for configuring tablets with linux. I've had the same problems with my Wacom PenPartner (RS-232). It works fine with my Amiga, but not under linux. I want to get one final working solution.

---

### Post by SnakeArtworX on 2008-04-20
As an addition to my post, here are effects of the following commands: 

**lsusb**

Bus 002 Device 007: ID 05ac:921b Apple Computer, Inc. 
Bus 002 Device 002: ID 05ac:911b Apple Computer, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 018: ID 046d:c226 Logitech, Inc. 
Bus 001 Device 021: ID 046d:c227 Logitech, Inc. 
Bus 001 Device 019: ID 046d:c21a Logitech, Inc. 
Bus 001 Device 016: ID 046d:c048 Logitech, Inc. 
Bus 001 Device 020: ID 05e3:0604 Genesys Logic, Inc. USB 1.1 Hub
Bus 001 Device 015: ID 056a:0069 Wacom Co., Ltd 
Bus 001 Device 014: ID 046d:c223 Logitech, Inc. 
Bus 001 Device 017: ID 058f:9254 Alcor Micro Corp. Hub
Bus 001 Device 001: ID 0000:0000  

** modprobe -l | grep wacom**

/lib/modules/2.6.22-14-generic/kernel/drivers/usb/input/wacom.ko

**lsmod | grep wacom**

wacom                  19584  0 
usbcore               161584  6 wacom,xpad,usbhid,ehci_hcd,ohci_hcd

**dir /dev/input**

by-id    event0  event2  event4  event6  event8  js0   mouse0
by-path  event1  event3  event5  event7  event9  mice  mouse1

** dmesg  | tail**

[   50.963227] /build/buildd/linux-source-2.6.22-2.6.22/drivers/input/tablet/wacom_sys.c: v1.46:USB Wacom Graphire and Wacom Intuos tablet driver
[   91.083889] evolution-alarm[8591]: segfault at 000000006972755f rip 00002b4983ad8d15 rsp 00007fff2acb53a0 error 4
[  361.159124] NET: Registered protocol family 10
[  361.159216] lo: Disabled Privacy Extensions
[  361.159449] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  361.159586] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  361.159634] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2263.708425] PPP generic driver version 2.4.2
[ 2266.472396] PPP BSD Compression module registered
[ 2266.521961] PPP Deflate Compression module registered

---

### Post by american.swan on 2008-04-22
"out of the box" really?  Great!!  I have a bamboo and I would love it to work with Ubuntu.  Sorry, I don't know how to help you.  I spent about 5 minutes on linuxwacom's website today.  I couldn't get it to install from the pre-made setup.  I am definitly more eager for Hardy-Heron now.

---

### Post by SnakeArtworX on 2008-05-01
Finally, my Bamboo One was recognized by the ubuntu and Gimp, but still no cursor movement nad no responses from *cat /dev/input/event10* (that's where my tablet belongs). Amazingly, even after editing the xorg.conf there's only "pad", "cursor" and "eraser" in Gimp or wacomcpl. There's no "stylus". any ideas?

---

