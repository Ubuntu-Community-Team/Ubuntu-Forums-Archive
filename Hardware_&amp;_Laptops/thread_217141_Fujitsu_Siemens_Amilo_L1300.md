---
title: "Fujitsu Siemens Amilo L1300"
date: 2006-07-16
forum: Hardware &amp; Laptops
---

### Post by j4ck455 on 2006-07-16
Ok I ran the **k**ubuntu 6.06 i386 Live [install] CD to first figure out if it would run on this notebook - before obliterating Windoze heXPee, anyways couldn't figure out how to get 802.11g to work - googled off several tangents about ndiswrapper and other stuff [my WRT54GL has SSID broadcasting disabled and I have found [thread=202834]this thread[/thread] which I'm sure will solve that problem].

So, are there any serious issues [like ACPI|DSDT|BIOS] with this notebook, that I should be aware of before zapping heXPee?

---

### Post by Eversmann on 2006-07-16
Please post the specs of the amilo 1300g. I own a L1310G and i'm becoming an expert about this laptop and ubuntu :-D

Post what you have there and i'll inform you about what to do.

---

### Post by j4ck455 on 2006-07-17
> **Eversmann said:**
> Please post the specs of the amilo 1300g. I own a L1310G and i'm becoming an expert about this laptop and ubuntu :-D

Post what you have there and i'll inform you about what to do.Eversmann, thanks for the reply :).

There is a BIOS update available for this notebook, which I will apply before installing Ubuntu.

Here are the specs for this Fujitsu Siemens Amilo L1300:[LIST]
[*]Intel Celeron M 370 CPU [1500MHz]
Windoze Device Manager says:```
ACPI\GENUINEINTEL_-_X86_FAMILY_6_MODEL_13\_0
```
[*]Memory: 512MB
[*]HDD: 80GB
[*]VGA: "Intel shared graphics up to 64MB DVMT, S-Video out"
Windoze Device Manager says:```
Intel(R) 82852/82855 GM/GME Graphics Controller
PCI\VEN_8086&DEV_3582&SUBSYS_10791734&REV_02\3&61AAA01&0&10
PCI\VEN_8086&DEV_3582&SUBSYS_10791734&REV_02\3&61AAA01&0&11
```
[*]Audio: "16-bit sampling, s built-in speakers, 1W subwoofer"
Windoze Device Manager says:```
Realtek AC'97 Audio
PCI\VEN_8086&DEV_24C5&SUBSYS_10791734&REV_03\3&61AAA01&0&FD
```
[*]I/O Ports: "3*USB2.0; CRT; Headphone out; Mic-in; SP/DIF"
Windoze Device Manager says:```
Intel(R) 82801DB/DBM USB Universal Host Controller 24C2,24C4,24CD
PCI\VEN_8086&DEV_24C2&SUBSYS_10791734&REV_03\3&61AAA01&0&E8
PCI\VEN_8086&DEV_24C4&SUBSYS_10791734&REV_03\3&61AAA01&0&E9
PCI\VEN_8086&DEV_24CD&SUBSYS_10791734&REV_03\3&61AAA01&0&EF
```
[*]Modem: "onBoard V.90 / 56kbps & 14.4 kbps Fax"
[*]LAN: "onBoard 10/100Mbps; 1 MiniPCI WLAN 802.11g"
Windoze Device Manager says:```
Realtek RTL8139/810x Family Fast Ethernet NIC
PCI\VEN_10EC&DEV_8139&SUBSYS_10791734&REV_10\4&16793A72&0&10F0
``````
PRISM 802.11g Adapter (3886)
PCI\VEN_1260&DEV_3886&SUBSYS_00001260&REV_01\4&16793A72&0&08F0
Manufacturer: Conexant Systems Inc
```
[*]PCMCIA: 1*TypeII
Windoze Device Manager says:```
ENE CB-710/712/714/810 Cardbus Controller
PCI\VEN_1524&DEV_1411&SUBSYS_10791734&REV_01\4&16793A72&0&20F0
Manufacturer: ENE TECHNOLOGY INC
```
[*]DVD+R/DL RW-R-RW
Windoze Device Manager says:```
_NEC DVD+-RW ND-6500A
IDE\CDROM_NEC_DVD+-RW_ND-6500A___________________2.40____\5&1EA6E060&0&0.1.0
```
[/LIST]<added>[indent]Attached kubuntu 6.06 dmesg [had to split it into 2 parts due to forum filesize limits].[/indent]</added>

---

### Post by Eversmann on 2006-07-17
Lots of info, that way is very easy to know who to go ;-)

Well, you have a PRISM wifi card, and a realtek ethernet card (no problem, those are great). Looks like you have to use the driver 8139too.

Kubuntu live version uses 2.6.15-23 kernel version. I had some problems with that kernel until they release 2.6.15-26 recently. Now i don't have problems with my ethernet card and samba. But i have a broadcom one.

About the wifi problem, the card isn't displayed on dmesg, or at least, i don't see it. That can be an issue. I'm assume you have the card enabled by software on that infamous button. That on this laptop is a real problem. To enable it, try my how-to on this thread: [http://www.ubuntuforums.org/showthread.php?t=207428&highlight=l1310g](http://www.ubuntuforums.org/showthread.php?t=207428&highlight=l1310g)

You won't need to install madwifi because the card has prism chipset. I think it has some problems but, if you can enable the wifi light on ubuntu, you can install it using ndiswrapper.

Check out what appears running sudo lspci -vv or sudo lshw.

But you'll have to install kubuntu for everything. Maybe after installing it will work better.

---

### Post by j4ck455 on 2006-07-18
> **Eversmann said:**
> ...
About the wifi problem, **the card isn't displayed on dmesg**, or at least, i don't see it. That can be an issue. I'm assume you **have the card enabled by software on that infamous button**. That on this laptop is a real problem. To enable it, try my how-to on this thread: [http://www.ubuntuforums.org/showthread.php?t=207428&highlight=l1310g](http://www.ubuntuforums.org/showthread.php?t=207428&highlight=l1310g)

You won't need to install madwifi because the card has prism chipset. I think it has some problems but, if you can enable the wifi light on ubuntu, you can install it using ndiswrapper.

Check out what appears running sudo lspci -vv or sudo lshw.

But you'll have to install kubuntu for everything. Maybe after installing it will work better.Hi Eversmann

:confused: I'm a wifi n00b [only got my WRT54GL 1.5 weeks back], as well as new to this Amilo [it has been loaned to me indefinitely by its owner - I warned the owner that heXPee would get replaced with Linux :D], anyways when I boot with the kubuntu 6.06 LiveCD, the wifi led is green - would the LED normally be off in Ubuntu|Linux until it is being used? I did have a look at the thread you posted, right now all this wifi stuff under Linux is a bit beyond my understanding, but I will get into this learning curve after installing Ubuntu [just have to set aside time on Sunday to do it] :).

ifconfig does show eth0 and eth1 [eth1 must be the 802.11g NIC], but I was expecting wlan0 to show instead - I assume that's something I could sort out after installing Ubuntu by editing /etc/network/interfaces...

I have attached the output from lspci -vv and lshw :).

---

### Post by Eversmann on 2006-07-18
If you have the wifi light enabled on booting, those are good news :-D, on the lshw file i see the card recognized and using a driver.

And you say me it appears as eth1. That can't be changed on the interfaces file, must be changed somewhere, but right now i forgot where (on the forum you can find it, i think i saw it looking a broadcoms wifi using a driver and not ndiswrapper). But i see it ok, isn't really a big deal. On my experiences, prism chipsets installs as eth1, ndiswrapper as wifi0, atheros as ath0, etc...

Let's do some more tests:

Open a terminal window and type:

sudo ifconfig eth1 up

(to bring the card up)

Then, let's see if the card can scan for networks:

sudo iwlist eth1 scan

If it finds your net, the card is working, now try to associate to it using:

sudo iwconfig eth1 essid (your essid name)

If you're using wep/wpa, it's something different. Wep it's pretty easy to use, just typing: sudo iwconfig eth1 key (key in hex).

wpa needs to be used thru wpa_supplicant. Installs network-manager-gnome to help on that.

But first, see if the card scans for networks. If you see it on ifconfig, looks like it's running out of the box. If not.... let's head into ndiswrapper.

---

