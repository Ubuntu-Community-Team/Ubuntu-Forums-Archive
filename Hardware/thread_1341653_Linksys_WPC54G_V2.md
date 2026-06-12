---
title: "Linksys WPC54G V2"
date: 2009-11-29
forum: Hardware
---

### Post by cjwescott on 2009-11-29
New Ubuntu user.  Just installed Ubuntu via Wubi on my Laptop.

My wireless adapter is not automatically detected.  I found some websites with help on getting the drivers loaded for the card.  They suggested installing the ndiswrapper packages and then the drivers.  When I try to install the packages through Synaptic Package Manager and select apply, a window pops up telling me to insert the disk labeled: "Ubuntu 9.10 _Karmic Koala_ -Release i386 (20091028.5)".  It won't recognize my live cd which has a label of "Ubuntu 9.10 i386".  Is the labeling of the disk really the issue?  Can I redirect the SPM to look for the files elsewhere?  I have looked for a work around but can't find one.

Your help is appreciated.

Chris

---

### Post by cjwescott on 2009-11-30
I realized after posting that I could go with a wired internet connection and download the files that way instead of using the live cd.  _I don't understand how I would of ever gotten it to work with the live cd since it was looking for a specific label on the CD, which mine label is different, which seems to be out of my control._
 
I got Ubuntu to reckonize my wireless router.  Now the only problem is after entering my password which is does accept I got the continued circular motion that it is trying to connect but doesn't.  Maybe I am impatient and it takes 5 minutes or so and I didn't give it enough time.  I'll try again tonight.

---

### Post by Evillz on 2010-01-02
I can't get mine to work either.  I have Ubuntu 9.10 Karmic Koala 32-bit.  The wireless card is a Linksys Wireless G Notebook Adapter Model WPC54G version 1.2.

When I type This: [B]lspci -n | grep '14e4:43'

[/B]I get this:** 02:00.0 0280: 14e4:4320 (rev 03)**

I tried to following the instruction at [this link]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff") word for word and it did not work either.[COLOR=Red]*  I just realized that this link was for Feisty Fawn, not Karmic Koala.  I hope I'm not the only one that finds this forum board somewhat confusing.*[/COLOR]

Here's what happens for me, and this happened before and after I tried the ndiswrapper instructions that I linked above:

I insert the card and reboot.  The wireless card is recognized.  It does not auto connect like my desktop with Ubuntu 9.10 Karmic Koala does.  I click on the wireless indicator in the top right corner and choose "Connect to a Hidden Network".  I enter the SSID, same as I did on my desktop, and it thinks for 2-3 seconds.  The connect window goes away and I immediately get a popup telling me that I am Disconnected.

I would expect to get this message after disconnecting from a wireless network.  This card worked on my laptop when I still had Windows XP installed.  I am a complete Ubuntu Noob.  My desktop has 64-bit installed and this laptop has 32-bit installed.  I'm just not sure what else I can try.  I'll continue to search the forums.  Please reply!!

---

### Post by Evillz on 2010-01-02
I installed WICD.  This changed the LAN/WLAN indicator in my system tray, but the wireless card didn't work.  I figured I didn't WICD anymore so I uninstalled it.  Now I can't get online with a LAN cable either.  I'm really enjoying myself now...

---

### Post by Evillz on 2010-01-02
I was able to re-install WICD from the Ubuntu Software Center.  After reboot, I was able to connect with LAN again.  Wireless still does not work with my WLAN card.

---

### Post by Evillz on 2010-01-03
I fixed it!  WCP54G v1.2 works in Ubuntu 9.10 Karmic Koala now!

First of all, [thanks to this post]("http://ubuntuforums.org/showthread.php?t=885847").  It has a great wealth of information.  Here is what I did to finally fix my problem.

I opened WICD Network Manager and clicked on Preferences.  On the General Settings tab, I noticed that the Wireless Interface field was blank.  The Wired Interface field had eth0 in it.  I thought it was weird that the Wireless Interface field was blank, but I didn't know what to put here and moved on to research some more.  I found the post that I just mentioned above and started walking through the suggestions outlined.  I finally ran the command **lshw -C Network** in the terminal.  A whole bunch of information came up.

```
  *-network               
       **description: Ethernet interface**
       product: DP83815 (MacPhyter) Ethernet Controller
       vendor: National Semiconductor Corporation
       physical id: 12
       bus info: pci@0000:00:12.0
       **logical name: eth0**
       version: 00
       serial: 00:0b:cd:a5:18:0b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=natsemi driverversion=2.1 latency=90 maxlatency=52 mingnt=11 multicast=yes
       resources: irq:11 ioport:8c00(size=256) memory:d0003000-d0003fff memory:24000000-2400ffff(prefetchable)
  *-network
       **description: Wireless interface**
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       **logical name: wlan0**
       version: 03
       serial: 00:0f:66:4f:99:82
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.55+ASUS,03/22/2004, 3.60.7.0 ip=192.168.1.104 latency=64 multicast=yes wireless=IEEE 802.11g
       resources: irq:11 memory:20000000-20001fff
```

I looked at the description for **Ethernet Interface** and noticed the **Logical Name** of **eth0**.  Hey, that looks familiar!  I scrolled down to the **Wireless Interface** and noticed that the **Logical Name** for this one was **wlan0**.  I opened **WICD Network Manager**, clicked **Preferences**, typed **wlan0** in for the **Wireless Interface** and clicked OK.  I clicked on **Network** and **Find a Hidden Network**, typed in my network's SSID and viola... connected!

I hope this helps save a few of you hours of frustration!

---

### Post by tmyakal on 2010-03-29
Okay, so, this might end up being the dumbest question on this forum, but I'm brand new to Ubuntu (straight off of being a Windows die-hard since '95), and here's where I'm stuck: When I do the ol' **lshw -C network**, my wireless interface is listed as "disabled." I've gathered that this may mean my card is turned off, but I don't know how to turn it on if that's the case.

---

### Post by nibblet5109 on 2010-05-26
I'm running into a similar problem - I can bring up my network info, but I'm seeing *-network DISABLED - thoughts?

---

### Post by Grenache on 2010-07-14
Hi,

I've successfully got it going on my old Dell laptop, according to this post (which is in German):
[http://on-air.stenki.eu/computer-linux/linksys-wireless-g-wpc54g-in-ubuntu-1004-installieren](http://on-air.stenki.eu/computer-linux/linksys-wireless-g-wpc54g-in-ubuntu-1004-installieren)


Briefly:
sudo apt-get install b43-fwcutter
   at prompt to extract firmware, select Yes
System / Preferences / Network Connections / Wireless 
   - set up security info, including ssid & passkey.
Insert card

It worked first time

---

