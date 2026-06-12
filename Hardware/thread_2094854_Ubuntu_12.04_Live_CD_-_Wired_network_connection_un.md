---
title: "Ubuntu 12.04 Live CD - Wired network connection unavailable"
date: 2012-12-15
forum: Hardware
---

### Post by vvd416 on 2012-12-15
I have a problem when I boot my machine from Ubuntu 12.04 live CD. After booting the system says that the network cable is unplugged, although the interface is visible with correct MAC in the output of ifconfig. It is MX978x5 Realtek NIC. 
Ubuntu 10.04, which I am using now, has no problems like this.
Could anyone tell me what could be wrong?

---

### Post by rajhanschinmay on 2012-12-16
Few suggestions:

1) One error can be the file corresponding to the network in the CD is damaged or not readable. That is one problem with CDs. Better use pen drive.
You can boot from USB bootable disk of Ubuntu.
It can be created using create USB disk and provide it .iso image of the ubuntu 12.04 image.

2) Software may be good. But network disabled.
Kindly check if networking is enabled. There is option called 'enable networking'. Once u do that, it will find network adapters automatically. Then u can use.

3) Wrong IP address. You may be using manually set IP address. Kindly check in the settings or using command ifconfig if ur IP address is correct.

4) If none works, then u can try reinstalling the network package again. You can download that offline package .deb file on some other computer with net, take it in pen drive to this machine and use dpkg -i command to install it.
After restart, it may work.

5) Reinstall the OS using bootable USB disk or pen drive.
You can deselect format option during installation so that all ur previous settings r retained.

Do reply back if any of these work for u.
Thank you.

---

### Post by vvd416 on 2012-12-16
Thank you, but CD is not a problem. I booted from Xubuntu 12.04 livecd and got the same problem. Here is the output of lshw:

description: Ethernet interface
       product: MX987x5
       vendor: Macronix, Inc. [MXIC]
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: 25
       serial: 00:80:c6:fc:4a:5c
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=tulip driverversion=1.1.15 ip=192.168.0.20 latency=32 maxlatency=56 mingnt=8 multicast=yes
       resources: irq:11 ioport:9800(size=256) memory:cd800000-cd8000ff memory:20000000-2003ffff(prefetchable)

Live CD from 10.04 shows that everything us fine; after booting network is available.

By the way, this post is still unanswered:
[http://askubuntu.com/questions/128174/wired-macronix-98715-ethernet-doesnt-work-after-12-04-upgrade](http://askubuntu.com/questions/128174/wired-macronix-98715-ethernet-doesnt-work-after-12-04-upgrade)

This guy had the same problem.

---

### Post by vvd416 on 2012-12-16
2 and 3 are not the case. Networking is enabled, and IP is not assigned since the system believes that the cable is unplugged.
4 and 5 are not relevant to the issue, I am using live CDs. I have 10.04 installed on my hard drive, and it works fine, but I am scared to upgrade because of the Live CD networking issues.

---

### Post by vvd416 on 2012-12-16
BTW, 12.10 doesn't have this problem. Tested with Xubuntu 12.10 live CD.

---

### Post by orionds on 2013-02-23
Use the Alternate (text) installer which manages to connect to the Internet. Then after reboot and find your network connection broken, follow these steps:

(1) Open a terminal and type "sudo gedit /etc/network/interfaces". My Macronix card was recognized as eth1 (normally eth0). I added these two lines and saved the file:

auto eth1
iface eth1 inet dhcp

[ATTACH]231808[/ATTACH]

To check if your card is eth0 or eth1, type "ifconfig" in a terminal. It was eth1 for me.

[ATTACH]231809[/ATTACH]

(2) Then, in the terminal type "sudo gedit /etc/NetworkManager/NetworkManager.conf". Change "managed=false" to "managed=true". You may not have the same text as mine. This does not matter, but "managed=false" should be there. Save the file and reboot.

[ATTACH]231810[/ATTACH]

After rebooting, you should see your network connected. If you click on the network-manager and choose "edit connections", you should see an extra line added which is not editable under "wired connection 1" (or whatever network connection name you chose to use). DO NOT DELETE it.

[ATTACH]231811[/ATTACH]

Hope this fixes your Macronix network card problem in 12.04. It worked for me.

---

