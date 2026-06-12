---
title: "RT2500 With Ubuntus  - need Help Please"
date: 2005-04-24
forum: Hardware &amp; Laptops
---

### Post by linuxgeek60 on 2005-04-24
Hello, I have a problem in installing rt2500-cvs-20050423 to see my Foxconn wireless card. 
 
So far what I did was: 
 
1) sudo apt-get install build-essential linux-headers-$(uname -r) 
 
2) Then I'm running  
$ make 
 
The error I'm getting is: 
 
make: *** /lib/modules/2.6.10-5-386/build: No such file or directory. Stop. 
rt2500.ko failed to build! 
make: *** [Module] error 1 
 
What am I doing wrong? 
 
Thanks. 

Trying to follow the instruction in 
[http://www.ubuntulinux.org/wiki/Rt2500WirelessCardsHowTo](http://www.ubuntulinux.org/wiki/Rt2500WirelessCardsHowTo) but it's not working so far.

JS :???:

---

### Post by diebels on 2005-04-24
is "uname -r" 2.6.10-5-386?

---

### Post by linuxgeek60 on 2005-04-24
diebels, but in running the command as you suugested is giving the message that the linux-headers are already installed and updated.

Thanks anyway,
JS

---

### Post by gekigangar3! on 2005-04-25
I was having the same problem and I think you need to install the kernel headers by either using synaptic package manager and installing all the linux kernel headers or by using 
apt-get install linux-kernel-header-2.6 etc.. basically do a search for linux kernels using  " apt-cache search kernel header " or something and install all the kernel headers applicable. There's a RT2500 howto in the Ubuntu forums somewhere, and it got me beyond that step, although I'm having trouble pinging my gateway now, but I digress. Good luck, O:) u.

---

### Post by gekigangar3! on 2005-04-25
[http://www.ubuntulinux.org/wiki/Rt2500WirelessCardsHowTo](http://www.ubuntulinux.org/wiki/Rt2500WirelessCardsHowTo)

---

### Post by linuxgeek60 on 2005-04-25
gekigangar3! that's the same link I'm using to install drivers, but still does not work. For one thing, the first step calls to download drivers using the wget command which cannot be done from the same computer. I downloaded file using my windows box.
The problem seems to be with the "make" command. 
 ;-)  I'm also trying with Libranet 3.0.

---

### Post by gekigangar3! on 2005-04-25
okay, I just got mine to work, but I don't really know how. Let me tell you what I did anyway. First download the file [http://rt2x00.serialmonkey.com/rt2500-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt2500-cvs-daily.tar.gz) using a web browser. If you're dual booting, then download the file, reboot, and then mount the windows partition from linux. If it's another computer, use a pen drive or floppy disk to transfer the driver. I noticed only the CVS drivers build correctly for me. Make sure you have all the ubuntu build tools and kernel headers. Then follow the instructions in that howto link. Type " make config " and it will prompt you to put in the linux kernel source location (in my hoary 5.04, it was /usr/src/linux-kernel-headers-2.6.10-5 er something like that). Then pretty much follow the directions, and if it doesnt make the rt2500.ko file (or rt2500.o if you're using 2.4 krnl) then you have compiling problems and you need all the proper build tools. Follow the howto and you should build a module, make it bootable and copy it to the modules folder. 

So I did all this, compiled the rt2500.ko module and it didnt' work.. so I did the following. 

1. Copied and configured the RT2500STA.dat file to /etc/Wireless/RT2500STA/ directory. Configure it to your liking. I don't know if it that did anything

2. Run ifdown ra0 and ifup ra0 , not only does it renew your dhcp lease, it makes sure your routing table is all good. I don't fully understand routing but it should say something if you type the " route " command. Mine says:
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 ra0
default         192.168.1.1     0.0.0.0         UG    0      0        0 ra0

3. Try pinging your localhost, gateway, then a remote host [www.yahoo.com](www.yahoo.com) or something. It will help narrow it down. 

wireless on linux is not a perfect science yet. I'll fill you in when I get it to boot up and configure automatically.

---

### Post by gekigangar3! on 2005-04-25
oh and also, don't forget to edit the file /etc/resolv.conf if it is showing up wierd stuff. Since I am using a router, my /etc/resolv.conf file looks something like :

search cox.net
nameserver 192.168.1.1

---

### Post by gekigangar3! on 2005-04-25
I rebooted, and miraculously, everything automatically loads now.

---

