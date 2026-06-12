---
title: "[SOLVED] Video Drivers on Everex Stepnote VA2001T"
date: 2008-12-16
forum: Hardware
---

### Post by finch127 on 2008-12-16
Hey guys, I have been using ubuntu for a few months now and I gotta say i love it. I switched from winblows and ive picked up a few things now. I can edit my xorg conf, etc. and all of the basic command line stuff, and theres only one thing i have trouble with:

I have an Everex Stepnote VA2001T that i ubuntu'ed up and it has this annoying problem, namely that I cant set the resolution. This is due to the fact that it is using a vesa driver and not the open chrome driver, and everything ive tried to use openchrome wont work. On windoze it worked fine so i know the card is good, its just that i cant use it on linux right. I did lspci and it returned that the card is a VIA Chrome 9 with a chipset that i know is supported under the openchrome set (i can post the entire output later if requested). Everything works fine, its just that im stuck with 800x600 and its hard to see, and on winhoes i used 1440x900

I cant calculate a modeline either because it wont detect my monitor for some reason either? I am at a loss here and I was wondering if you all could help me out.

---

### Post by albinootje on 2008-12-16
> **finch127 said:**
> I cant calculate a modeline either because it wont detect my monitor for some reason either? I am at a loss here and I was wondering if you all could help me out.

If you want to calculate a Modeline for xorg.conf, then look up the specifications from your monitor in the manual of the monitor if you still have that.

[http://xtiming.sourceforge.net/cgi-bin/xtiming.pl](http://xtiming.sourceforge.net/cgi-bin/xtiming.pl)

And VIA offers closed-source drivers for some of their cards.
Not easy to find on their kind of messy website, but you can try and see whether your card is included.

---

### Post by finch127 on 2008-12-16
yeah i know how to get them etc. its just that i dont know my refresh rate and all the details but the resolution that i want

and i checked via's website but i just couldnt find a driver

my lspci:

```

00:00.0 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. CN896/VN896/P4M900 I/O APIC Interrupt Controller
00:00.6 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Security Device
00:00.7 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. CN896/VN896/P4M900 PCI to PCI Bridge Controller (rev 80)
00:03.0 PCI bridge: VIA Technologies, Inc. CN896/VN896/P4M900 PCI to PCI Bridge Controller (rev 80)
00:0f.0 IDE interface: VIA Technologies, Inc. VT8237A SATA 2-Port Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 PCI bridge: VIA Technologies, Inc. VT8237A Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge
01:00.0 VGA compatible controller: VIA Technologies, Inc. CN896/VN896/P4M900 [Chrome 9 HC] (rev 01)
04:01.0 Audio device: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) (rev 10)
05:01.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)

```

---

### Post by albinootje on 2008-12-16
Here are some suggestion which you can try :
[https://answers.launchpad.net/ubuntu/+question/11807](https://answers.launchpad.net/ubuntu/+question/11807)

---

### Post by finch127 on 2008-12-16
yeah thanks for that but it didnt work

it just asks me for low graphics mode every time i restart

i think that the driver isnt being loaded or its not right or something like that

---

### Post by finch127 on 2008-12-17
i really just need to up the resolution to 1440x900 again, i dont care for the effects and stuff if the driver doesnt work

is there anyway to get the vesa drivers resolution up?

---

### Post by finch127 on 2008-12-18
yeah just forget about it, i switched to gOS linux because it was made for everexs other stuff and the graphics drivers work fine

i figure since it is ubuntu based i'll be fine lol

---

