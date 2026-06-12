---
title: "No bluetooth adapters plugged in (and no Windows)"
date: 2010-12-12
forum: Hardware
---

### Post by lonegreyride on 2010-12-12
Hi all, I apologize if this has been asked before (which I'm pretty sure it has), but I've been trying to find a solution to this for about a week now and can't. I have an HP Pavillion dv9000 with internal bluetooth, and when I try to open Preferences > Bluetooth (or anything related), I get an error stating that I have no bluetooth adapters plugged in.

I've found a large number of other people with the same problem, but the only actual solution I could find involved going into Windows, doing something, and then coming back to Ubuntu. The problem is, I have only one OS installed on this machine, that being Ubuntu 10.10. 

I'm currently using the proprietary Broadcom driver, although I have also tried the default driver with the same results. I'm also unable to find any options in the BIOS for enabling bluetooth.

At this point, I'm starting to assume that Bluetooth in my case is simply not a possibility, which really disappoints me, as it would be the first thing I've had to give up on in 10.10, and I was hoping to not have to go back to Windows at all. I guess I'm mostly wondering at this point if someone can confirm for me whether or not I have any chance of having this work.

I'm also interested to know why we need to boot into Windows to get this working... is it simply because the drivers were written for Windows? 

Thanks for any responses,

John

---

### Post by lonegreyride on 2010-12-15
Just trying one bump to see if anyone might be able to answer me.

---

### Post by lonegreyride on 2010-12-21
Ok, one more try. Apologies if this is frowned upon. I'm really just wondering what's happening here. Is this a known issue, or am I just asking too much to have bluetooth working in Ubuntu without having Windows on the same machine? Is this a new issue or has Ubuntu always had trouble in this department?

Basically, I'm wondering if there's any hope for this in the future, or if I should simply give up on the idea of having my internal bluetooth adapter working under Ubuntu?

---

### Post by pricetech on 2010-12-21
I can't really say what the problem is with your internal BlueTooth, but I have a USB BlueTooth adapter that works flawlessly out of the box in Ubuntu Lucid and Edubuntu Lucid.

It doesn't work under windows though.

As far as needing windows to make yours work, I've read about some wireless adapters that require some sort of activation be done under windows, after which they work just fine in Linux.  You may be looking at a similar issue.

---

### Post by Stunts on 2010-12-21
Try here:
[http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html/11#bluetooth](http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html/11#bluetooth)

Not sure it will work, but it's worth a shot I guess?

---

### Post by odinb on 2010-12-21
I know this is probably not what you want to hear, but it is the easiest solution that can keep you on Ubuntu, buy a new dongle and plug into an available USB port.

They can be found for under $3 on Amazon and other places: [http://tinyurl.com/2bzvspk](http://tinyurl.com/2bzvspk)

The one linked to above, I have used on all my own desktop and most of my friends desktops and laptops. It is true plug-and-play under Ubuntu!

HP, Toshiba etc. should be on a list of shame for making sure everything on their notebooks breaks due to driver issues on older Win-OS than the one it is delivered with, or any Linux flavor for that matter! They consistently flash GPU, soundcard, BIOS etc with firmware that will only work on Vista/Win7 to make sure you do not run anything else, including WinXP, and Linux.

---

### Post by lonegreyride on 2010-12-21
> **Stunts said:**
> Try here:
[http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html/11#bluetooth](http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html/11#bluetooth)

Not sure it will work, but it's worth a shot I guess?

Thanks for the link, but unfortunately neither of the suggestions worked for me. I guess I'll have to go for a USB dongle. I'm not totally against the idea, I'd just rather not have anything plugged into my laptop if I don't have to.

Thanks for the replies guys. Just wanted to make sure that my understanding of my problem was correct. Hopefully someday some update will suddenly surprise me and my adapter will start working. Cheers,

John

---

### Post by odinb on 2010-12-21
By the way, what is the Bluetooth detected as in Linux?

Mine is detected this way:
Bus 005 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)

Do an lsusb and post back.

---

### Post by ignacio69 on 2011-02-23
Hello odinb, 
maybe you can help:
cannot pair ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode) in ubuntu 10.04
i have a USB Bluetooth dongle of the Cambridge Silicon Radio type, USB ID
0a12:0001. When I plug it into my  machine it's detected properly, Bluetooth services
are started, I get the icon in the system tray and everything. However,
scanning for devices - either using gnome-bluetooth's 'Set up new device...'
menu entry or 'hcitool scan' from a console - will not find any other device.
I verified that my NETBOOT RUNNING UBUNTU 9.04 and has a different
Bluetooth adapter) _does_ find these devices when I do a scan, so it's not
something wrong with the devices. The scan just isn't working for some reason.
hcitool scan doesn't return an error - it says 'Scanning ...', waits a while,
then goes back to the console, just as you'd expect if there were nothing to
find.


here is the output: 
lsusb
Bus 002 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)

cat /proc/bus/usb/devices  | more
cat: /proc/bus/usb/devices: No existe el fichero o el directorio

lsmod | more
Module                  Size  Used by
xt_limit                1382  8 
xt_tcpudp               2011  7 
ipt_LOG                 4542  8 
ipt_MASQUERADE          1407  0 
xt_DSCP                 1677  0 
ipt_REJECT              1928  1 
nf_conntrack_irc        3332  0 
nf_conntrack_ftp        5381  0 
xt_state                1098  6 
rfcomm                 33421  8 
binfmt_misc             6587  1 
sco                     7885  2 
bridge                 45614  0 
stp                     1655  1 bridge
bnep                    9436  2 
snd_hda_codec_via      27111  1 
l2cap                  30624  16 rfcomm,bnep
iptable_nat             4414  0 
nf_nat                 15735  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      10672  9 iptable_nat,nf_nat
nf_conntrack           61615  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp
,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4          1073  1 nf_conntrack_ipv4
iptable_mangle          2771  0 

hciconfig -a
hci0:	Type: USB
	BD Address: 00:15:83:3D:0A:57 ACL MTU: 310:10 SCO MTU: 64:8
	UP RUNNING PSCAN 
	RX bytes:967 acl:0 sco:0 events:28 errors:0
	TX bytes:367 acl:0 sco:0 commands:28 errors:0
	Features: 0xff 0xff 0x8f 0xfe 0x9b 0xf9 0x00 0x80
	Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
	Link policy: RSWITCH HOLD SNIFF PARK 
	Link mode: SLAVE ACCEPT 
	Name: 'ignacio-desktop-0'
	Class: 0x5a0100
	Service Classes: Networking, Capturing, Object Transfer, Telephony
	Device Class: Computer, Uncategorized
	HCI Ver: 2.0 (0x3) HCI Rev: 0xc5c LMP Ver: 2.0 (0x3) LMP Subver: 0xc5c
	Manufacturer: Cambridge Silicon Radio (10)

dmesg
[   20.954383] Bluetooth: L2CAP ver 2.14
[   20.954387] Bluetooth: L2CAP socket layer initialized
[   21.052328] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   21.052331] Bluetooth: BNEP filters: protocol multicast
[   21.259422] Bluetooth: SCO (Voice Link) ver 0.6
[   21.259429] Bluetooth: SCO socket layer initialized
[   21.732672] Bluetooth: RFCOMM TTY layer initialized
[   21.732682] Bluetooth: RFCOMM socket layer initialized
[   21.732688] Bluetooth: RFCOMM ver 1.11
hcitool dev
Devices:
	hci0	00:15:83:3D:0A:57
hcitool scan
Scanning ...
sudo hcitool cc 00:15:83:3D:0A:57
Device is not available.
2.6.32-28-generic

---

### Post by ignacio69 on 2011-03-06
Dear all,
the bluetooth adapter ID 0a12:0001 Cambridge Silicon Radio, is working,
however it cannot connect to my headseat NOKIA BH-104.
here is the output when trying:
dmessage:
Mar  5 19:23:07 ignacio-desktop kernel: [   21.419540] Bluetooth: Core ver 2.15
Mar  5 19:23:07 ignacio-desktop kernel: [   21.420017] Bluetooth: HCI device and connection manager initialized
Mar  5 19:23:07 ignacio-desktop kernel: [   21.420020] Bluetooth: HCI socket layer initialized
Mar  5 19:23:07 ignacio-desktop kernel: [   21.667339] Bluetooth: Generic Bluetooth USB driver ver 0.6
Mar  5 19:23:08 ignacio-desktop kernel: [   22.153977] Bluetooth: L2CAP ver 2.14
Mar  5 19:23:08 ignacio-desktop kernel: [   22.153981] Bluetooth: L2CAP socket layer initialized
Mar  5 19:23:08 ignacio-desktop kernel: [   22.223534] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Mar  5 19:23:08 ignacio-desktop kernel: [   22.223542] Bluetooth: BNEP filters: protocol multicast
Mar  5 19:23:08 ignacio-desktop kernel: [   22.394353] Bluetooth: SCO (Voice Link) ver 0.6
Mar  5 19:23:08 ignacio-desktop kernel: [   22.394356] Bluetooth: SCO socket layer initialized
Mar  5 19:23:08 ignacio-desktop kernel: [   22.775342] Bluetooth: RFCOMM TTY layer initialized
Mar  5 19:23:08 ignacio-desktop kernel: [   22.775348] Bluetooth: RFCOMM socket layer initialized
Mar  5 19:23:08 ignacio-desktop kernel: [   22.775351] Bluetooth: RFCOMM ver 1.11
debug:
Mar  5 19:23:07 ignacio-desktop bluetoothd[954]: Bluetooth daemon 4.60
Mar  5 19:23:08 ignacio-desktop bluetoothd[1143]: Failed to find Bluetooth netlink family
kern.log:
Mar  5 19:23:07 ignacio-desktop kernel: [   21.419540] Bluetooth: Core ver 2.15
Mar  5 19:23:07 ignacio-desktop kernel: [   21.420017] Bluetooth: HCI device and connection manager initialized
Mar  5 19:23:07 ignacio-desktop kernel: [   21.420020] Bluetooth: HCI socket layer initialized
Mar  5 19:23:07 ignacio-desktop kernel: [   21.667339] Bluetooth: Generic Bluetooth USB driver ver 0.6
Mar  5 19:23:08 ignacio-desktop kernel: [   22.153977] Bluetooth: L2CAP ver 2.14
Mar  5 19:23:08 ignacio-desktop kernel: [   22.153981] Bluetooth: L2CAP socket layer initialized
Mar  5 19:23:08 ignacio-desktop kernel: [   22.223534] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Mar  5 19:23:08 ignacio-desktop kernel: [   22.223542] Bluetooth: BNEP filters: protocol multicast
Mar  5 19:23:08 ignacio-desktop kernel: [   22.394353] Bluetooth: SCO (Voice Link) ver 0.6
Mar  5 19:23:08 ignacio-desktop kernel: [   22.394356] Bluetooth: SCO socket layer initialized
Mar  5 19:23:08 ignacio-desktop kernel: [   22.775342] Bluetooth: RFCOMM TTY layer initialized
Mar  5 19:23:08 ignacio-desktop kernel: [   22.775348] Bluetooth: RFCOMM socket layer initialized
Mar  5 19:23:08 ignacio-desktop kernel: [   22.775351] Bluetooth: RFCOMM ver 1.11
syslog:
Mar  5 19:23:07 ignacio-desktop kernel: [   21.419540] Bluetooth: Core ver 2.15
Mar  5 19:23:07 ignacio-desktop kernel: [   21.420017] Bluetooth: HCI device and connection manager initialized
Mar  5 19:23:07 ignacio-desktop kernel: [   21.420020] Bluetooth: HCI socket layer initialized
Mar  5 19:23:07 ignacio-desktop kernel: [   21.667339] Bluetooth: Generic Bluetooth USB driver ver 0.6
Mar  5 19:23:07 ignacio-desktop bluetoothd[954]: Bluetooth daemon 4.60
Mar  5 19:23:08 ignacio-desktop kernel: [   22.153977] Bluetooth: L2CAP ver 2.14
Mar  5 19:23:08 ignacio-desktop kernel: [   22.153981] Bluetooth: L2CAP socket layer initialized
Mar  5 19:23:08 ignacio-desktop bluetoothd[1143]: Failed to find Bluetooth netlink family
Mar  5 19:23:08 ignacio-desktop kernel: [   22.223534] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Mar  5 19:23:08 ignacio-desktop kernel: [   22.223542] Bluetooth: BNEP filters: protocol multicast
Mar  5 19:23:08 ignacio-desktop kernel: [   22.394353] Bluetooth: SCO (Voice Link) ver 0.6
Mar  5 19:23:08 ignacio-desktop kernel: [   22.394356] Bluetooth: SCO socket layer initialized
Mar  5 19:23:08 ignacio-desktop kernel: [   22.775342] Bluetooth: RFCOMM TTY layer initialized
Mar  5 19:23:08 ignacio-desktop kernel: [   22.775348] Bluetooth: RFCOMM socket layer initialized
Mar  5 19:23:08 ignacio-desktop kernel: [   22.775351] Bluetooth: RFCOMM ver 1.11

can anybody help?
do I need to set something else?

---

