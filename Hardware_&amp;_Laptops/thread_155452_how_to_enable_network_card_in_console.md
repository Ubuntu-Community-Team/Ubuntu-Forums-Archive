---
title: "how to enable network card in console?"
date: 2006-04-05
forum: Hardware &amp; Laptops
---

### Post by junglemike on 2006-04-05
Hi, i'm new to linux. I'm trying to install Xubuntu (i have 5.04 version)
I have old toshiba 3110ct laptop PII-300mhz/128mb ram/30gb hdd
I'm following the instructions here:
[https://wiki.ubuntu.com/InstallingXubuntu](https://wiki.ubuntu.com/InstallingXubuntu)
the problems is for some reason , my wireless network card is not connecting. And without the network , i can't run this update command to download xubuntu:
```
sudo apt-get install xubuntu-desktop
```

When i run ishw command to see listed hardware this is what i get about the network:
```
..
..
*-network:0 DISABLED
description: IRDA controller
physical id: 1
logical name: irda0
capabilities: irda
*-network:1 **DISABLED**
description: Ethernet controller
physical id: 2
logical name: eth0
serial: 00:02:6f:36:f2:7f
capabilities: ethernet
configurateion: broadast=yes multicas=yes

```
I need to add that my router is configured for dhcp. 
So please help me find out how to enable the network card.
thanks.

P.s:
If this hleps, here is the output of iwconfig command:
```

eth0  IEEE 802.11-DS ESSID: ""  Nickname:"Prism  I"
        Mode:Managed Access Point: 00:00:00:00:00:00 Bit Rate:11Mb/s
        Tx-Power-15 dBm Sensivity: 1/3
        Retry min limit:8 RTS thr:off  Fragment thr:off
        Power management:off
        Link Quality=0/92 Signal level=-68dBm Noise level=-122dBm
        Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
        Tx excessive retries:0  Invalid misc:0 Missed beacon:0

```

---

### Post by Darkriser on 2006-04-05
configuring wireless adapter (if not recognized during install) can be a pain (but not impossible). what brand and model of wireless adapter do you have? there are several solutions, but depends on chipset usd by your adapter.

---

### Post by junglemike on 2006-04-05
Sorry, you answered before i finished posting. Can you tell again what i need to do, or where to read? I added some information to the end of the 1st post.

---

### Post by Darkriser on 2006-04-05
I'm fast :rolleyes: 
Anyway, there's still no info about your adapter - brand and model number - this info is required. You know - every adapter has so called chipset built in. And different chipsets require different drivers. So the best way is to look at your adapter and write down those tricky characters and digits ;) 

On the other side....I recommend installing Ubuntu (or xubuntu) first and trying to set-up your adapter afterwards. Every wifi router has also ethernet connectors, so try connecting to your router (and internet) using cables, installing the system and taking care of your adapter then.

---

### Post by junglemike on 2006-04-05
Thanks.
Unfortunately this laptop does not have network card :-(
But I have desktop computer , if this helps.
> Anyway, there's still no info about your adapter - brand and model number - this info is required. You know - every adapter has so called chipset built in. And different chipsets require different drivers. So the best way is to look at your adapter and write down those tricky characters and digits 
The fact that it lists it in network configuration and sees it as "Prism I" -  doesn't this mean that the driver is already installed?

---

### Post by Darkriser on 2006-04-05
well, if "iwconfig" command lists your wifi card, you should be ok.
now try editing the /etc/network/interfaces file (you'll have to use sudo, as this is a system file). there you should write configuration for your wifi settings. you'll need to include ESSID (name of your network) and encryption details (if set on the router). also, you should add line "iface eth0 inet dhcp" to tell the adapter to request ip address from dhcp server in your router.

for more details about interfaces setting see 
[https://wiki.ubuntu.com/WifiDocs](https://wiki.ubuntu.com/WifiDocs), specifically this one: [https://wiki.ubuntu.com/WiFiHowto](https://wiki.ubuntu.com/WiFiHowto)

---

### Post by az on 2006-04-05
Do you have anything installed?  Do you just have a command line?

If you have just a command line, edit the /etc/network/interfaces file and add a stanza:

auto eth0

inet iface eth0 dhcp
wireless-mode managed
wireless-essid (your ssid)
wireless-key aabbccddee (if applicable)

and then save and exit.  Enable the connection with

sudo ifup eth0

If you already have gnome, just use the networking tool.

---

### Post by junglemike on 2006-04-05
Thaks guys for the help.
I've tried  editing the /etc/network/interfaces file using instructions above (with sudo nano /etc/network/interfaces)
but the instructions above didn't work. I also looked at the guides. So i decided that it is too complicated for total noob like me to do it in console mode. 
So I started Ubuntu 5.04 installation  - this time with regular mode (and not with -server mode). Now it is installing packages (for 2 hours already).
I did ths for the following reason:

I hope that once i load gui - there will be some easier way to set up the network for a noob (i found guides on specific gui tools)


Now it is installing standard set of packages, meaning probaly gnome and open office, and such. This is very old laptop.PII-300mhz/@66mhz fsb 128mb ram @66mhz  No way it could cope with this. I was hoping to install XFCE (Xubuntu?) because it is much lighter. This is why i tried using Xubuntu wiki instruction in the first place. But it failed because xubuntu packages are not on cd and must be downloded.
-=Queston 1=-
After it finishes install, is it possible to install and use XFCE rather than gnome?
-=Question 2=-
I also have win98,and win200 (yet) on this very laptop. So i can download anything from win. Is it possible to somehow download this xubuntu-desktop and put it on fat prtition, And then use some other command instead of ```
 sudo apt-get install xubuntu-desktop
```?
-=Question3=- 
I also have Slackware 10.2 install cd's. I know there is XFCE there. Is it possible to use these XFCE packages from slack cd's?
-=Question4=- about the network card
My card is nor regular card that can be bought in store. It is some internal part of broken bridge. I got some broken bridge called "Long range wireless Muliti client bridge". I opened it up, there way a typical Pcmcia-like card with big external unpluggable antenna. It doesn't have any name or id on it.
But i somehow got it working under windows2000 (somebody helped me find and install the driver :-) ) 
How do i find what chipset this card uses? I tried looking in widows driver zip file - but there are no any readme files , just setups, cabs,etc..
TiA

---

