---
title: "Dell Inspiron 2650 NIC problem."
date: 2008-01-31
forum: Hardware &amp; Laptops
---

### Post by RAF01 on 2008-01-31
Hello Everyone,

I just Installed Ubuntu on my Dell Inspiron 2650 and my network card won't work, the OS can recognize the card but i can not connect to the internet.

The Nic card information:
Interface: Wired Ethernet (eth0)
Speed: 100 MB
Driver: 3c59x
Hardware Address: 00:06:5b:BA:07:D6

can someone help me with this? thanks!

---

### Post by Yellow Pasque on 2008-01-31
What kind of LAN chip is it?
```
sudo update-pciids; lspci | grep Ethernet
```
Post the line that gives you. It should look like this:
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)

---

### Post by RAF01 on 2008-01-31
how can i get this information??? please tell me!

---

### Post by Yellow Pasque on 2008-01-31
> **RAF01 said:**
> how can i get this information??? please tell me!
Copy the snippet of code in my last post into a terminal or search around Dell's site.

---

### Post by RAF01 on 2008-01-31
Thanks for the help bud, but i still can't find anything :(...can you assist me further please?

---

### Post by jan quark on 2008-01-31
open the terminal

go to menu accessoires > terminal
or push alt+f2 and type gnome-terminal and run

then copy this into the terminal 
```

lspci | grep Ethernet
```

and post the result here

---

### Post by RAF01 on 2008-01-31
thank you so much for the help, okay i just did that, and it showed this:

02:01.0 Ethernet Controller: 3Com Corporation 3c905C - TX/TX-M  [Tornado] (rev 78 )

then what can i do?

---

### Post by jan quark on 2008-01-31
check first if under system > administration > restricted driver manager

there is a entry that resembles your network defices
see screenshot

if yes ... well better there is no entry

if there is no entry this means that your wireless card is supported out-of the-box by ubuntu

now it wouldn't be bad to read through this documentation
[https://help.ubuntu.com/community/WifiDocs/WirelessNetworking#head-ce415853bb8f9c18e52168777c376ef4a80e5de1](https://help.ubuntu.com/community/WifiDocs/WirelessNetworking#head-ce415853bb8f9c18e52168777c376ef4a80e5de1)

and ask for more

---

### Post by RAF01 on 2008-01-31
Thanks man, but it is not actually my wireless card its my Ethernet connection, and the entry for it is not in the restricted drivers.....thanks :)

---

### Post by jan quark on 2008-01-31
ops

but I hope you will find what you need in this documentation just browse through it 
here is the main page 
it explains a lot of ubuntu issues

[https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)

ask for more

---

### Post by Yellow Pasque on 2008-01-31
The first thing I would do is run an lsmod command and look for the 3c905 driver module. After we make sure the hardware is working, then we'll look at your network configuration.

So please open up the terminal just like you did before and post the result of:
```
lsmod
```
We'll go from there.

---

### Post by RAF01 on 2008-01-31
thank you Jan, i really appreciate the great help :)

---

### Post by RAF01 on 2008-01-31
> **Temüjin said:**
> The first thing I would do is run an lsmod command and look for the 3c905 driver module. After we make sure the hardware is working, then we'll look at your network configuration.

So please open up the terminal just like you did before and post the result of:
```
lsmod
```
We'll go from there.

thanks i will make sure to do that and i will get with you with the results :)

---

### Post by Yellow Pasque on 2008-01-31
Yw, If you can't copy and paste the result, just look for a module named 3c905 or 3com, something like that.

---

### Post by RAF01 on 2008-01-31
OKay i just got those results:
```

Module			Size Used By
rfcomm			42136 2
12cap			26240 11 rfcomm
bluetooth		57060 4rfcomm,12cap
ppdev			10244 0
speedstep_ich		6416 0
speedstep_lib		6404 1 speedstep_ich
cpufreq_ondemand	9612 1
cpufreq_userspace	5280 0
cpufreq_stats		7232 0
freq_table		5792 3speedstep_ich,cpufreq_ondemand.cpufreq_status
cpufreq_powersave	2688 0
cpufreq_conservative	8072 0
ac			6148 0
dock			10656 0
button			8976 0
sbs			19592 0
container		5504 0
video			18060 0
battery			11012 0
lp			12580 0
bcm43xx			127336 0
ieee80211softmac	31360 1 bcm43xx
ieee80211		35656 2 bcm43xx,ieee80211softmac
ieee80211_crypt		7040 1 ieee80211
joydev			11328 0
snd_inte18x0		34972 1
snd_ac97_codec		100644 1 snd_inte18x0
ac97_bus		3200 1 snd_ac97_codec
snd_pcm_oss		44672 0
snd_mixer_oss		17664 1 snd_pcm_oss
snd_pcm			80388 3 snd_inte18x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy		4740 0
pcmcia			41388 0
snd_seq_oss		33152 0
snd_seq_midi		9600 0
snd_rawmidi		25728 1 snd_seq_midi
i2c_core		26112 0
yenta_socket		27532 2
rsrc_nonstatic		14080 1 yenta_socket
parport_pc		37412 1
parport			37448 3 ppdev,lp,parport_pc
snd_seq_midi_event	8448 2 snd_seq_oss,snd_seq_midi
snd_seq			53232 6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer		24324 2 snd_pcm,snd_seq
snd_seq_device		9288 5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
pcmcia_core		40980 3 pcmia,yenta_socket,rsrc_nonstatic
serio_raw		8068 0
psmouse			39952 0
snd			54660 12
snd_inte18x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore		8800 1 snd
snd_page_alloc		11440 2 snd_inte18x0,snd_pcm
iTCO_wdt		11940 0
intel_agp		25620 1
iTCO_vendor_support	4868 1 iTCO_wdt
shpchp			34580 0
pci_hotplug		32704 1 shpchp
agpgart			35016 1 intel_agp
evdev			11136 6
ext3			133896 1
jbd			60456 1 ext3
mbcache			9732 1 ext3
sg			36764 0
sr_mod			17828 0
cdrom			37536 1 sr_mod
sd_mod			30336 3
ata_generic		8452 0
floppy			60004 0
3c59x			46632 0
mii			6528 1 3c59x
ata_piix		17540 2
libata			125168 2 ata_generic,ata_piix
scse_mod		147084 4 sg,sr_mod.sd_mod,libata
uhci_hcd		26640 0
usbcore			138632 2 uhci_hcd
thermal			14344 0
processor		32072 1 thermal
fan			5764 0
fuse			47124 0
apparmor		40728 0
commoncap		8320 1 apparmor
```

what do you see :)

Thanks!

---

### Post by Yellow Pasque on 2008-01-31
I see what appears to be the driver module is correctly loaded.
> 3c59x			46632 0

Ok, now go to System -> Administration -> Network
Is your wired connection enabled? Do you have a static IP that your ISP assigns you or do you just use DHCP?

Now we'll look in System -> Administration -> Network Tools
Do you have a loopback interface and an Ethernet interface?

---

### Post by RAF01 on 2008-01-31
Ok it says that the Wired Connection:Address:dhcp, but when i clicked on properties it does not show an IP address or subnet Mask or gateway address all these fields are empty.

In my Network tools I have both a loop back interface and Ethernet interface (eth0) but all the interface information on both of them says not available. Also, on the Network Device when i click on Ethernet Interface (eth0) the configure button is disabled....

HELP!!!!

---

### Post by Yellow Pasque on 2008-02-01
I'm not a networking expert, but I'll keep trying to help you if no one else is jumping in. Can you run a few commands for us?
```
cat /etc/network/interfaces
ifconfig
ethtool -i eth0
```

---

### Post by RAF01 on 2008-02-01
thank you so much :)

okay, for the command:

 cat /etc/network/interfaces

i got this result: 
auto lo
iface lo inet loopback

iface eth0 inet dhcp

auto eth0

for this command:
ethtool -i eth0

i got this:
Driver: 3c59X
version: (empty)
firmware version: (empty)
bus-info: 0000:02:01.0

would this help?

---

### Post by Yellow Pasque on 2008-02-01
Those look okay to me. Ok, one more and that's it for me tonight. I'll stop bullsh!tting my way through this and let a real expert take over.
Just:
```
sudo ethtool eth0
```

---

### Post by RAF01 on 2008-02-01
ok thanks again for getting back with me about this, i got the following results regarding this matter

sudo ethtool eth0 
Settings for eth0: 
        Supported ports: [ TP MII ] 
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
        Supports auto-negotiation: Yes 
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
        Advertised auto-negotiation: Yes 
        Speed: 10Mb/s 
        Duplex: Half 
        Port: MII 
        PHYAD: 24 
        Transceiver: internal 
        Auto-negotiation: on 
        Current message level: 0x00000001 (1) 
        Link detected: no 

again thanks for your help

---

### Post by Yellow Pasque on 2008-02-01
> again thanks for your help
Hey, np. I think we're finally on to something.

> Link detected: no
Seems to indicate hardware/driver issue. Is there any way you can verify that your LAN cable works with another connection?

Another thing we can try that I've seen work with some NIC's is restarting the driver. After you run the following commands, does the ethtool output look any different than what you posted above?:
```
sudo rmmod 3c59x
sudo modprobe 3c59x
sudo ethtool eth0
```

---

### Post by RAF01 on 2008-02-01
> **Temüjin said:**
> 

Seems to indicate hardware/driver issue. Is there any way you can verify that your LAN cable works with another connection?



No the cable is fine, i just tested it on another PC that runs Windows XP, and its good...

> **Temüjin said:**
> Another thing we can try that I've seen work with some NIC's is restarting the driver. After you run the following commands, does the ethtool output look any different than what you posted above?:

how can i restart the driver...any ideas??

---

### Post by Yellow Pasque on 2008-02-01
> how can i restart the driver...any ideas??
The commands I gave were intended to do that. Run these commands in the terminal and see if the ethtool output is different than what you got last time.
```
sudo rmmod 3c59x
sudo modprobe 3c59x
sudo ethtool eth0
```

---

### Post by RAF01 on 2008-02-01
no mate its the same...:(

---

### Post by Yellow Pasque on 2008-02-01
I searched around the web and I don't see any kind of common problem with the driver for this NIC. It's starting to sound like a bad NIC to me.
Try to run a self-test on the NIC by typing this in the terminal:
```
sudo ethtool -t eth0
```

---

### Post by RAF01 on 2008-02-01
Yep bud, the NIC card is on...i dont understand... :(

---

### Post by MatthewT on 2008-04-10
Hello, I am also having a similar networking issue with my Dell Inspiron 2650.

I know the network card used to work fine out of the box for Ubuntu 7.04 and up.

Unfortunately now it will work off and on, after rebooting, for say up to 30 minutes. Then the port shuts off regardless of what is going on. Doesn't recognize the cable or anything(no lights).

Checked in Windows or any LiveCD. Does the same thing. I'm starting to suspect a hardware issue but I don't want it to be true because I can't replace the Motherboard. :/

---

