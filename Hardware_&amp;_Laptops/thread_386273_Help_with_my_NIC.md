---
title: "Help with my NIC"
date: 2007-03-16
forum: Hardware &amp; Laptops
---

### Post by slingre87 on 2007-03-16
Hello. I've just installed the latest version of ubuntu on my compaq laptop, but I can't get it to connect to internet, either wired or unwired. I was told that I need to recompile my kernel, or something like that, to get ubuntu to recognize my hardware. I think that I have a broadcom nic, and  realtek built in. if this makes any sense, then please help. Thank You

---

### Post by teaker1s on 2007-03-16
you most likely have broadcom wireless, there is a link in my signature 
to query your pci devices
```
lspci
```
to query usb (some internal devices are usb connected so it pays to check)
```
lsusb
```


install cd can be used as cd source
```
gksudo synaptic
``` if it doesn't ask for cd
hit edit tab
select add cdrom
insert cd
hit reload tab
search ndiswrapper
install related ndiswrapper packages-look at the guide in my signature to install ndiswrapper driver and config.

---

### Post by slingre87 on 2007-03-16
what will compiling my kernel do?

---

### Post by teaker1s on 2007-03-16
I'd suggest we try and find out
1) what hardware you have
2)what drivers you need

compiling kernels only needed rarely and I doubt in your situation it is required- think of it as making a new version of operating system

terminal
```
lspci
```
```
lsusb
```
```
iwconfig
```
post output

---

### Post by slingre87 on 2007-03-16
Umm...one thing that I do need to ask..where do i enter all of these commands at? Like I said, I'm really new at this
thanks

---

### Post by teaker1s on 2007-03-16
sure no problem
desktop panel select
applications>accessories>Terminal

now you will need to copy the output either using a usb pen drive/cdrw/or floppy- unless you can see broadcom or realtek in the output in which case we need to see full details as they appear.

Welcome to the forums, beginners section and forum search may also answer some of your questions too

I'm off to bed as it's 1:14am local time, I'll keep an eye on this thread and if you post your findings I'll try to help you resolve your network/wireless issues.
May  also be of interest to have a look here
[https://help.ubuntu.com/community/BasicCommands]("https://help.ubuntu.com/community/BasicCommands")

---

### Post by slingre87 on 2007-03-17
Last night I tried some commands on my comp and I came up with this:

Broadcom BCm4318 802.11g wireless LAN Rev 02)
RealTek RTL-8139/8139c/8139c+ (Rev 10)

and also:

IEEE 802.11 b/g    ESSID: off/any
Mode: Managed   Access Point: Invalid   Bit Rate: 1 Mb/s
RTS thr: off    Fragment thr: off
Encryption key: off

Kernel version is 2.6.15-23-386


Now what do I do to at least get my realtek ethernet to connect to the internet, as I have no connectivity at all, wired or otherwise.  Thank you

---

### Post by teaker1s on 2007-03-17
firstly great work, we have identified that you have bcm4318, now your easiest way to get it working is
[http://www.ubuntuforums.org/showthread.php?t=197102&highlight=BCm4318]("http://www.ubuntuforums.org/showthread.php?t=197102&highlight=BCm4318")


Looking at your ethernet It appears the realtek site is claiming the driver is in linux kernel. If this is true in ubuntu's case
top panel click
System>Administration>networking
if you can see ethernet you will need to enable it, if you can logon to numeric router page but not see google.com etc then you need to put your ubuntu on a static ip and enter your isp DNS.

or dhcp and stabilise DNS by
[http://www.ubuntuforums.org/showthread.php?t=282034&highlight=stabilise+dns](http://www.ubuntuforums.org/showthread.php?t=282034&highlight=stabilise+dns)

---

### Post by slingre87 on 2007-03-22
Alright, I got my eth0 working, but I still can't get the eth1 to work. I have the compaq driver sp34152.cva onmy desktop, but I don't know what to do with it, or how to get the ndiswrapper to touch it.

slingre87@slingre87-laptop:~$ sudo su
Password:
root@slingre87-laptop:/home/slingre87# sudo rmmod bcm43xx
ERROR: Module bcm43xx does not exist in /proc/modules
root@slingre87-laptop:/home/slingre87# sudo ifdown eth1
ifdown: interface eth1 not configured
root@slingre87-laptop:/home/slingre87# ifconfig eth1
eth1: error fetching interface information: Device not found
root@slingre87-laptop:/home/slingre87# sudo ufup eth1
sudo: ufup: command not found
root@slingre87-laptop:/home/slingre87# sudo ifup eht1
Ignoring unknown interface eht1=eht1.
root@slingre87-laptop:/home/slingre87# sudo ifdown eht1
ifdown: interface eht1 not configured
root@slingre87-laptop:/home/slingre87# sudo ifup eth1
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.
root@slingre87-laptop:/home/slingre87#

Not quite sure what most of this means, except that I don't what else to do.

Any help?    Thanx much

---

### Post by teaker1s on 2007-03-22
okay post terminal output of 
```
iwconfig
```

also post a web link to your driver and I'll extract it for you if you pm me a email address

---

### Post by slingre87 on 2007-03-24
slingre87@slingre87-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

slingre87@slingre87-laptop:~$

There's that....

slingre87@slingre87-laptop:~$ sudo apt-get install cabextract unzip
Password:
Sorry, try again.
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package cabextract
slingre87@slingre87-laptop:~$

slingre87@slingre87-laptop:~$ cd Desktop
slingre87@slingre87-laptop:~/Desktop$ sudo apt-get install cabextract unzip
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package cabextract
slingre87@slingre87-laptop:~/Desktop$

slingre87@slingre87-laptop:~/Desktop$ ./sp34152a
bash: ./sp34152a: is a directory
slingre87@slingre87-laptop:~/Desktop$


And that....

slingre87@slingre87-laptop:~$ sudo su
Password:
root@slingre87-laptop:/home/slingre87# sudo rmmod bcm43xx
ERROR: Module bcm43xx does not exist in /proc/modules
root@slingre87-laptop:/home/slingre87# sudo ifdown eth1
ifdown: interface eth1 not configured
root@slingre87-laptop:/home/slingre87# ifconfig eth1
eth1: error fetching interface information: Device not found
root@slingre87-laptop:/home/slingre87# sudo ufup eth1
sudo: ufup: command not found
root@slingre87-laptop:/home/slingre87# sudo ifup eht1
Ignoring unknown interface eht1=eht1.
root@slingre87-laptop:/home/slingre87# sudo ifdown eht1
ifdown: interface eht1 not configured
root@slingre87-laptop:/home/slingre87# sudo ifup eth1
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.
root@slingre87-laptop:/home/slingre87#

And that on is me messin around...I think

---

### Post by teaker1s on 2007-03-24
to install cabextract and also unzip you must have internet connection through ethernet, which I believe you said you had?
I'd advise synaptic over apt-get
```
gksudo synaptic
```
you also may need to uncomment some of your sources, we are working on a beginners section of wiki- take a look here
[https://help.ubuntu.com/community/Beginners/FAQ?highlight=%28beginner%29#head-690fad6a7665bc2486be6da07c68ad3fa2172c6c](https://help.ubuntu.com/community/Beginners/FAQ?highlight=%28beginner%29#head-690fad6a7665bc2486be6da07c68ad3fa2172c6c)

---

### Post by slingre87 on 2007-03-24
Ok. My driver download is: 
[http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=ob-45290-1&lc=en&cc=us&dlc=en&tool=softwareCategory&product=499847&query=presario%20v5000&os=228](http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=ob-45290-1&lc=en&cc=us&dlc=en&tool=softwareCategory&product=499847&query=presario%20v5000&os=228)

and when I type iwconfig: 
islingre87@slingre87-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

slingre87@slingre87-laptop:~$
slingre87@slingre87-laptop:~$ sudo iwconfig
Password:
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

slingre87@slingre87-laptop:~$
 

anyway, I think that I did that right
Thanx Much

---

