---
title: "[SOLVED] Can't get wireless working on my HP laptop..."
date: 2008-06-16
forum: Hardware
---

### Post by jeremy1138 on 2008-06-16
Hello
I just upgraded from Ubuntu version 7.10 to 8.04 on my laptop and now I can't get my wireless card to connect or even turn on for that matter.  It worked fine before so I'm not sure what's up.  I figured that something funky must have happened during the upgrade so I tried doing a fresh install.  No dice.  The indicator light still doesn't even turn on.  I see that there are a lot of threads that deal with this same type of problem but I'm really kinda new at this so I have quite a bit of trouble sorting through it all and finding what I need.  I have tried a few different things but, like I say, it's hard to tell what I need to do.  I have an HP dv5020us laptop.  It's set up to dual boot windows xp pro and Ubuntu.  My wireless network doesn't have any WEP encryption or anything like that; all I use is MAC filtering.  I can't even see my network or any others around me using the wireless utility in Ubuntu.  I'll be happy to post the output of any commands I need to to help diagnose the problem.  Any help with this would be greatly appreciated.  Thanks very much in advance for your help.

---

### Post by alenis on 2008-06-16
On my laptop I have to activate the wireless adapter in the BIOS. That done, it works well and the network manager allow connections to wirelesss networks very easily.

---

### Post by stchman on 2008-06-16
> **jeremy1138 said:**
> Hello
I just upgraded from Ubuntu version 7.10 to 8.04 on my laptop and now I can't get my wireless card to connect or even turn on for that matter.  It worked fine before so I'm not sure what's up.  I figured that something funky must have happened during the upgrade so I tried doing a fresh install.  No dice.  The indicator light still doesn't even turn on.  I see that there are a lot of threads that deal with this same type of problem but I'm really kinda new at this so I have quite a bit of trouble sorting through it all and finding what I need.  I have tried a few different things but, like I say, it's hard to tell what I need to do.  I have an HP dv5020us laptop.  It's set up to dual boot windows xp pro and Ubuntu.  My wireless network doesn't have any WEP encryption or anything like that; all I use is MAC filtering.  I can't even see my network or any others around me using the wireless utility in Ubuntu.  I'll be happy to post the output of any commands I need to to help diagnose the problem.  Any help with this would be greatly appreciated.  Thanks very much in advance for your help.

Since you have an HP is the wireless card Broadcom or Intel?

When you turn the laptop on does the wireless light come on or stay off?  Did you bump the wireless on/off switch?

Does the wireless work when running from the LiveCD?  Does the wireless work on the XP side but then not work on the Ubuntu side?

Please post an lspci output.

Also, running MAC filtering on a wireless network is COMPLETELY worthless.  I recommend that you run WPA or WPA2.  Remember if someone gets on your connection and surfs illegal sites or downloads copyrighted material then you could be blamed.  It is very easy to get your network setup with encryption.

---

### Post by jeremy1138 on 2008-06-16
> **stchman said:**
> Since you have an HP is the wireless card Broadcom or Intel?

When you turn the laptop on does the wireless light come on or stay off?  Did you bump the wireless on/off switch?

Does the wireless work when running from the LiveCD?  Does the wireless work on the XP side but then not work on the Ubuntu side?

Please post an lspci output.

Also, running MAC filtering on a wireless network is COMPLETELY worthless.  I recommend that you run WPA or WPA2.  Remember if someone gets on your connection and surfs illegal sites or downloads copyrighted material then you could be blamed.  It is very easy to get your network setup with encryption.

Let me begin by thanking you for the reply.  I really appreciate it.

-My laptop has a Broadcom wireless card.

-The wireless indicator light on my laptop stays off while I start my computer.  It normally doesn't turn on until I boot into XP or Ubuntu (when it worked).

-My wireless internet does not work when I use a live cd of the current version of Ubuntu but it still works in Windows.

-lspci output:
```

jeremy@jeremy-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
06:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

```

What should I do next?  Oh, by the way, internet works fine when I plug into my router with an ethernet cable.  Thanks again for the help.

edit:
I have 32 bit Ubuntu installed by the way.  Thanks!

---

### Post by jeremy1138 on 2008-06-16
ok so I just got a whole bunch of updates for Ubuntu and one of the things that installed was a driver for my wireless card.  My indicator light is on now but I still can't see my wireless network (or any other) from the network settings panel.  Any ideas?  Thanks!

---

### Post by stchman on 2008-06-16
> **jeremy1138 said:**
> ok so I just got a whole bunch of updates for Ubuntu and one of the things that installed was a driver for my wireless card.  My indicator light is on now but I still can't see my wireless network (or any other) from the network settings panel.  Any ideas?  Thanks!

Does your laptop now see the wireless card in System--->Administration--->Network?  Is there a wireless connection.

Broadcoms are not very Linux friendly.

---

### Post by jeremy1138 on 2008-06-16
> **stchman said:**
> Does your laptop now see the wireless card in System--->Administration--->Network?  Is there a wireless connection.

Broadcoms are not very Linux friendly.

No networks are listed there but I always have to click "unlock" and enter my password to get to change anything there.  Is that normal?  Thanks!

---

### Post by jeremy1138 on 2008-06-16
Thanks for the help all.  If anyone else is wondering how to get their broadcom wifi card working, you may want to go here:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851)

These instructions worked great for me.

---

