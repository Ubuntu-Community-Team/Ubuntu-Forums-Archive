---
title: "hp laptop ubuntu version not working"
date: 2005-07-08
forum: Hardware &amp; Laptops
---

### Post by arthur_kalm on 2005-07-08
Hello everyone,

I have an HP nc4200 laptop that I wanted to install Ubuntu on. I had already installed Kubuntu but several pieces of hardware didn't working (including the wireless). In my search for how to get the wireless card working I came upon [this](http://www.ubuntulinux.org/support/custom/hplaptops) link.

I was very excited because it said that most of the hardware works out of the box. However, upon attempting to install it, package "ed" was unable to install! I reburned it several times (with lower speeds as they suggested), I also downloaded it _again_ with no luck (the md5sums matched).

Did anyone else have this problem as well? I was able to install regular Ubuntu no problem but I would really like to install the HP one to save myself trouble.

Thank you in advance
--
Arthur Kalmenson

---

### Post by arthur_kalm on 2005-08-05
Ok so it seems noone knows why. Is there any chance anyone knows where I can order this CD (maybe something wrong with the download version?).

If not, I am more interested as to what the differences are between the HP Ubuntu version and the regular Ubuntu. Thus, I can go and install all of the programs that are included and hopefully have full support for most of the hardware. If anyone has a link to a list of the differences that would be greatly appreciated.

---

### Post by s_p_a_r_k_y on 2005-08-06
did you do a checksum on the iso image to make sure it wasn't corrupt?

```
md5sum cdimage.iso
```
and it should match whatever the website had

---

### Post by arthur_kalm on 2005-08-09
Yes I did check the md5sum. The problem ended up being the laptop's external CD drive. Essentially what ended up happening was each that I would attempt to install Ubuntu (or SuSE) it would start installing it and then the CD drive would just stop at one point (and thus the install failed).

I thought the problem was either with the laptop, the CD drive, or Linux. I went out and bought an IDE to USB cable and used an internal CD drive and viola! The HP Ubuntu installed with no problems. Thank you though.

---

### Post by nocturn on 2005-08-10
[QUOTE=arthur_kalm]Ok so it seems noone knows why. Is there any chance anyone knows where I can order this CD (maybe something wrong with the download version?).

If not, I am more interested as to what the differences are between the HP Ubuntu version and the regular Ubuntu. Thus, I can go and install all of the programs that are included and hopefully have full support for most of the hardware. If anyone has a link to a list of the differences that would be greatly appreciated.[/QUOTE]

Yeah, I'm actually wondering myself.  I have a HP (not one of those), maybe some of the customizations work on my lappy too.

---

### Post by srijith on 2005-08-10
While I haven't installed vanilla Ubuntu on the HP laptop I have, here are things that I think may be added in the HP version:

- acpi script for sleep, hibernate, lid, networks etc.
- ipw2200 module and firmware (pretty old one though)
- specific video card support, I could use the Intel 915GM supported module
- keyboard extra button binding (for information, speaker mute, up, down, radion on/off

---

### Post by arthur_kalm on 2005-08-10
Yep, everything except the wireless works. I am still trying to get that to work ](*,). If anyone has got it working on the nc4200 I would love to hear how  :grin:

---

### Post by locutus42 on 2005-08-11
[QUOTE=arthur_kalm]Yep, everything except the wireless works. I am still trying to get that to work ](*,). If anyone has got it working on the nc4200 I would love to hear how  :grin:[/QUOTE]


did you try the ndiswrapper utility? It works on my Compaq R4000. here's what I did:
1) install the ndiswrapper-util package
2) get the appropriate MS Windows driver for your network card( see the ndiswrapper site via google )
3) run: sudo ndiswrapper -i PATH/theWindowsDriver.inf
4) run; sudo modprobe ndiswrapper
5) configure your network card with the GUI or edit /etc/network/interfaces
6) if all works, to setup ndiswrapper for each boot, run: sudo ndiswrapper -m

Here is the section of /etc/network/interfaces for the R4000 Broadcom driver( bcmwl5.inf ):

audo wlan0
iface wlan0 inet dhcp
wireless-essid YOUR-SSID
wireless_defaultkey 3
wireless-key1 11111111111111111111111111
wireless-key2 22222222222222222222222222
wireless-key3 33333333333333333333333333
wireless-keymode open
wireless-channel 6

---

### Post by arthur_kalm on 2005-08-11
Hi,

Thanks for the advice. I tried this and got:
[I]
arthur@kubuntu:~/wireless/intel_windows$ sudo ndiswrapper -i w70n501.inf
ls: /etc/ndiswrapper: No such file or directory
Installing w70n501
arthur@kubuntu:~/wireless/intel_windows$ sudo ndiswrapper -l
Installed ndis drivers:
w70n501 driver present
arthur@kubuntu:~/wireless/intel_windows$ sudo modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.10-5-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted[/I]

While dmesg said:

*ndiswrapper (wrapper_init:1494): loadndiswrapper failed (11); check system log for messages from 'loadndisdriver'*

I have an Intel ipw2200. The thing is my card definitely works because I can detect networks and such. The problem is when I attempt to connect to it. DHCP never works.

[I]arthur@kubuntu:~/wireless/intel_windows$ sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth0/00:0e:35:f3:4e:b3
Sending on   LPF/eth0/00:0e:35:f3:4e:b3
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
No DHCPOFFERS received.
No working leases in persistent database - sleeping.[/I]

I tried with a static IP and it seemed to work (ifup and the Networking utility both worked with no problems) but when I tried a ping or opened a browser I had no Internet connection.

This has been very frustrating since wireless will be very important for me when I go back to school.

Another disappointment has been that this "HP Ubuntu" has the features tied to Gnome and since I use KDE this special Ubuntu is basically useless to me.

Thanks for any help you can provide  :)

---

