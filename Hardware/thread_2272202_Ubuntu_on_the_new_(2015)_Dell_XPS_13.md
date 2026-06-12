---
title: "Ubuntu on the new (2015) Dell XPS 13"
date: 2015-04-04
forum: Hardware
---

### Post by chris352 on 2015-04-04
I'm on the market for a new laptop and the new Dell XPS 13 caught my eye. I'm wondering if anyone has any first-hand experience (or has heard about others' experiences) of how nicely it plays with Ubuntu. I tried doing a web search but the only info I've found concerns the 2013 developer's version of the XPS.

---

### Post by zircon_34 on 2015-04-05
I also like this laptop, but the current version has problem for the wireless driver for Ubuntu, most people buy an external card. Other problem, is that linux can't use the full resolution of the screen. I am hoping they get out soon a developer edition with Ubuntu, and another wireless card and fixed other compatibility issues.

---

### Post by cnbiz850 on 2015-06-06
I like this laptop too.  My search on the web seems also to indicate that Ubuntu is not fully functioning on it.  

Has anyone had more progress in running Ubuntu?  Does the latest BIOS update (A04) from Dell help?  I read about the developer edition.  Is that about the same hardware as it is now on the market?  Is there a special Ubuntu image that can be used to install on that hardware?

---

### Post by Ryback on 2015-06-14
I've got this laptop (non 4k display, non touch screen) running Ubuntu 15.04 and it's aesthetically very beautiful and almost trouble free.  Just a few issues remaining on mine:

[LIST]
[*]Very occasional (but frustrating) full system crash caused by wireless driver
[*]Competing modes for the touchpad means it occasionally misbehaves - some trouble selecting/using click 'n' drag.
[*]Some users report repetition of keystrokes from keyboard, but it's not something I've encountered.
[/LIST]

I will post back should I get these fixed, I would still recommend it based on the above (especially if you use a mouse!)

---

### Post by Ryback on 2015-06-14
I fixed the touchpad competing between psmouse and i2c modes using part of the guide below, which you also might find useful.

[http://mclements.net/Mike/mrc-blog/blog-150605.html](http://mclements.net/Mike/mrc-blog/blog-150605.html)

Which means my only remaining issue is the occasional kernel panic from the broadcomm wireless card.  I should add that I didn't encounter as many problems as the writer of that web page, probably because I installed 15.04 cleanly, rather than installing an earlier ubuntu version and upgrading.

---

### Post by b.g.turner on 2015-06-18
I've had this laptop for a couple of weeks now and have 15.04 installed. Things seem to be working pretty well, especially after I upgraded the Bios to A04 using Windows (still have it dual booting). 

A few things that are a little buggy:

**Trackpad** -- most of the time it is flawless, but occasionally it will start acting 'funny' - clicks seem to mimick a 'click and drag' functionality, when really I am just clicking, and then moving the pointer. I haven't  been able to find a recurring theme as to why or when this happens, but if I do I'll file a bug.
**Battery** -- Right now, I get a decent ~5+hr of solid local development (virtualbox running a vagrant machine, along with browsers and sublime text). People indicate that this thing should be getting closer to 10 - 15 for some setups (though my screen is the 3200x1800, so that uses more power). I'm thinking this will improve as kernel things are upgraded etc.
**Screensize** - Like I said, I opted for the 3200x1800 unit. This is A LOT of pixels, and realistically probably more than I need now that I've used it for a while. The issue is that if I set the display to the full resolution (open dash and search for 'display') then it is almost impossible to read and interact with the system. I dabbled with different settings like scaling the icons, increasing the terminal font size etc, but at the end of the day I've basically just set the display to 1920x1080 and called it good. If I were to do it again, I would probably just buy that screen size since that's the one I am actually using and it would take less power, therefore longer battery life. You can learn from my mistake! :)

Those are the only real things I'm noticing about this machine out of the box. On the plus side, I purchased a [Gigaware Mini Display port to HDMI adapter]("http://www.amazon.com/Gigaware%C2%AE-Mini-DisplayPort-HDMI%C2%AE-DVI/dp/B00M7S5VKW/ref=sr_1_2?s=electronics&ie=UTF8&qid=1434672522&sr=1-2&keywords=gigaware+hdmi&pebp=1434672530108&perid=121XRAM6VBJ988SDWX97") that is working great out of the box as I am connected to a Samsung monitor.



Other things that users might need or want, but aren't part of the default system -- 

**Ethernet** -- this doesn't come with an RJ45 jack. I thought I could use this [Inateck USB 3.0 to Ethernet (HB3UVl3-4)]("http://www.amazon.com/gp/product/B00IJU0K2Q?psc=1&redirect=true&ref_=oh_aui_detailpage_o00_s00") and while it is promising that it supposedly has a [Linux driver]("http://www.inateck.com/download/inateck-hbu3vl3-4-usb3-0-hub-gigabit-ethernet-network-adapter/") -- I can't for the life of me figure out how to use it. I think I need to compile it and apply it as a kernel mod, but I've never done anything like that and it sounds intimidating (maybe something like [this]("http://www.cyberciti.biz/tips/compiling-linux-kernel-module.html") is what I need to do). In any event, the Inateck doesn't work out of the box, but I would like to get it working so that I can use my office's faster LAN speeds on a wired connection. 

All told, I'm pretty happy with this machine, it's small and highly portable. The keyboard is different than my old Thinkpad, but I'm growing to like it. I guess that these little annoyances are just part of purchasing hardware that is so new it hasn't been rolled into the larger Linux (and more specifically Ubuntu) ecosystem.

---

### Post by Yellow Pasque on 2015-06-18
Supposedly, the ethernet kernel module/driver is already built into the kernel from Ubuntu Trusty/14.04 onwards. You can verify with:
```
sudo modinfo ax88179_178a
```

So you have the device connected and it doesn't work? Do you see any messages realted to it in dmesg?
```
dmesg | grep -i ax88
```

---

### Post by b.g.turner on 2015-06-20
I realize from my last post that I left one thing out that may be confusing to people who land here. As of writing this (Jun 20) I found that [this post]("http://forthescience.org/blog/2015/04/21/installing_ubuntu_14_04_on_the_new_dell_xps_13_v2/") had the most relevant info on setting up the XPS 13.Some of the information didn't apply to me, since I was installing 15.04, and the article was for 14.10, but it was good info none the less.

 For me, I purchased the model that comes with Windows, and as I understand it, this means it comes with a Broadcom wireless card. That means that wireless doesn't work out of the box, and one needs to[ install a couple of additional things]("http://installing-ubuntu-14-04-and-getting-the-broadcom-wifi-online") to get it working, both during the 'Live media' as well as the fully installed versions of Ubuntu. 

Specifically, this meant that for 15.04 (the article is for 14.10) I needed

* bcmwl-kernel-source_6.30.223.248+bdcom-0ubuntu0.1_amd64.deb
* dkms_2.2.0.3-1.1ubuntu5.14.04_all.deb

That being said, I've since found that someone has created a PPA, that I haven't tried yet, but may be useful to someone visiting this thread. See this [comment on ask ubuntu]("http://askubuntu.com/a/613454").

---

### Post by b.g.turner on 2015-06-20
Thanks for responding Temujin, I think it may have helped me!

It certainly appears that ax88179_178a is installed:

```

$ sudo modinfo ax88179_178a
[sudo] password for benjamin: 
filename:       /lib/modules/3.19.0-18-generic/kernel/drivers/net/usb/ax88179_178a.ko
license:        GPL
description:    ASIX AX88179/178A based USB 3.0/2.0 Gigabit Ethernet Devices
srcversion:     4C676DD260D26D648107038
alias:          usb:v17EFp304Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04E8pA100d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0072d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p4A00d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B95p178Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B95p1790d*dc*dsc*dp*ic*isc*ip*in*
depends:        usbnet,mii
intree:         Y
vermagic:       3.19.0-18-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        F1:A2:A3:18:F7:05:DD:CD:A4:68:5A:32:12:11:6C:13:D2:FD:23:66
sig_hashalgo:   sha512

```

So I then tried the following:

1. Plugin the Inateck USB dongle **without** the ethernet jack plugged in, and checked dmesg:

```

$ dmesg | grep -i ax88
[  509.258058] usb 2-1.1: Product: AX88179
[  510.620306] ax88179_178a 2-1.1:1.0 eth0: register 'ax88179_178a' at usb-0000:00:14.0-1.1, ASIX AX88179 USB 3.0 Gigabit Ethernet, 00:23:56:7c:14:24
[  510.620423] usbcore: registered new interface driver ax88179_178a

```

2. Plug the ethernet cable into the dongle:

```

$ dmesg | grep -i ax88
[  509.258058] usb 2-1.1: Product: AX88179
[  510.620306] ax88179_178a 2-1.1:1.0 eth0: register 'ax88179_178a' at usb-0000:00:14.0-1.1, ASIX AX88179 USB 3.0 Gigabit Ethernet, 00:23:56:7c:14:24
[  510.620423] usbcore: registered new interface driver ax88179_178a
[  537.411181] ax88179_178a 2-1.1:1.0 eth0: unregister 'ax88179_178a' usb-0000:00:14.0-1.1, ASIX AX88179 USB 3.0 Gigabit Ethernet
[  537.411196] ax88179_178a 2-1.1:1.0 eth0: Failed to read reg index 0x0002: -19
[  537.411198] ax88179_178a 2-1.1:1.0 eth0: Failed to write reg index 0x0002: -19
[  537.443051] ax88179_178a 2-1.1:1.0 eth0 (unregistered): Failed to write reg index 0x0002: -19
[  537.443054] ax88179_178a 2-1.1:1.0 eth0 (unregistered): Failed to write reg index 0x0001: -19
[  537.443056] ax88179_178a 2-1.1:1.0 eth0 (unregistered): Failed to write reg index 0x0002: -19

```

3. So that got me curious about what else was happening at the same time, so checking the full contents of dmesg:
```

$ dmesg
## ... lots of other things, following is plugging in the dongle ... ##
[  296.432919] usb 1-1: new high-speed USB device number 7 using xhci_hcd
[  296.563892] usb 1-1: New USB device found, idVendor=2109, idProduct=2812
[  296.563896] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[  296.563899] usb 1-1: Product: USB2.0 Hub             
[  296.563900] usb 1-1: Manufacturer: VIA Labs, Inc.         
[  296.564540] hub 1-1:1.0: USB hub found
[  296.564883] hub 1-1:1.0: 4 ports detected
[  300.097113] usb 2-1: new SuperSpeed USB device number 3 using xhci_hcd
[  305.234246] usb 2-1: device descriptor read/all, error -110
[  503.361082] usb 2-1: new SuperSpeed USB device number 5 using xhci_hcd
[  508.498113] usb 2-1: device descriptor read/all, error -110
[  508.610416] usb 2-1: new SuperSpeed USB device number 6 using xhci_hcd
[  508.861958] usb 2-1: New USB device found, idVendor=2109, idProduct=0812
[  508.861963] usb 2-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[  508.861965] usb 2-1: Product: USB3.0 Hub             
[  508.861966] usb 2-1: Manufacturer: VIA Labs, Inc.         
[  508.862640] hub 2-1:1.0: USB hub found
[  508.862763] hub 2-1:1.0: 4 ports detected
[  509.236075] usb 2-1.1: new SuperSpeed USB device number 7 using xhci_hcd
[  509.258053] usb 2-1.1: New USB device found, idVendor=0b95, idProduct=1790
[  509.258057] usb 2-1.1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  509.258058] usb 2-1.1: Product: AX88179
[  509.258060] usb 2-1.1: Manufacturer: ASIX Elec. Corp.
[  509.258061] usb 2-1.1: SerialNumber: 00000000000163
[  510.620306] ax88179_178a 2-1.1:1.0 eth0: register 'ax88179_178a' at usb-0000:00:14.0-1.1, ASIX AX88179 USB 3.0 Gigabit Ethernet, 00:23:56:7c:14:24
[  510.620423] usbcore: registered new interface driver ax88179_178a

## Now plugin the Ethernet cable ##

[  537.411063] usb usb2-port1: Cannot enable. Maybe the USB cable is bad?
[  537.411090] usb 2-1: USB disconnect, device number 6
[  537.411092] usb 2-1.1: USB disconnect, device number 7
[  537.411181] ax88179_178a 2-1.1:1.0 eth0: unregister 'ax88179_178a' usb-0000:00:14.0-1.1, ASIX AX88179 USB 3.0 Gigabit Ethernet
[  537.411196] ax88179_178a 2-1.1:1.0 eth0: Failed to read reg index 0x0002: -19
[  537.411198] ax88179_178a 2-1.1:1.0 eth0: Failed to write reg index 0x0002: -19
[  537.443051] ax88179_178a 2-1.1:1.0 eth0 (unregistered): Failed to write reg index 0x0002: -19
[  537.443054] ax88179_178a 2-1.1:1.0 eth0 (unregistered): Failed to write reg index 0x0001: -19
[  537.443056] ax88179_178a 2-1.1:1.0 eth0 (unregistered): Failed to write reg index 0x0002: -19
[  538.248150] usb 2-1: new SuperSpeed USB device number 8 using xhci_hcd
[  543.268904] usb 2-1: device descriptor read/8, error -110
[  543.374229] usb 2-1: new SuperSpeed USB device number 8 using xhci_hcd
[  543.399429] usb 2-1: device descriptor read/8, error -71

```

Note the timestamp at "537.411063" -- that's when I plugged in the Ethernet cable. Does that help message really tell me the problem - ie, that "Maybe the USB cable is bad" and therefor this is a hardware issue and I need a replacement? If not, are there additional things that I can do to troubleshoot? Perhaps I need to explore actually installing the driver?

This page seems to indicate that there is indeed a [Linux driver]("http://www.inateck.com/download/inateck-hbu3vl3-4-usb3-0-hub-gigabit-ethernet-network-adapter/") that can be used. But when I downloaded it and opened the archive it is just a few source code files. I've only compiled source files a couple of times, and don't fully understand what I'm doing - so I'm pretty hesitant to try compiling kernel modules on my system that mostly works. Still, this might be just the learning opportunity for me! :)

PS - I realize that this might be getting off topic from the original thread - can I move this to a new thread, or in some way organize this better?

---

### Post by Yellow Pasque on 2015-06-20
> **b.g.turner said:**
> This page seems to indicate that there is indeed a [Linux driver]("http://www.inateck.com/download/inateck-hbu3vl3-4-usb3-0-hub-gigabit-ethernet-network-adapter/") that can be used. But when I downloaded it and opened the archive it is just a few source code files.

The link points to kernel module/driver code that's over two years old. I don't think that's the answer to your problem, since any recent kernel contains the same or newer version of that code. Do any USB devices work if you plug them into the ports on the device?

---

### Post by Ryback on 2015-06-20
> **b.g.turner said:**
> I realize from my last post that I left one thing out that may be confusing to people who land here. As of writing this (Jun 20) I found that [this post]("http://forthescience.org/blog/2015/04/21/installing_ubuntu_14_04_on_the_new_dell_xps_13_v2/") had the most relevant info on setting up the XPS 13...

Thanks for the link! I'll give the power saving stuff a try and see if it boosts my battery time.

---

### Post by danielandrews7396 on 2015-07-14
I've just come across this thread, and thought I'd chime in. I've had the new xps 13 dev edition for a few months now, and I've started to come across a couple of issues. The first being with the broadcom wireless card: Although it works out of the box, and there aren't any issues with general usage... it isn't yet supported by aircarack, so any web admins out there won't be able to use this for monitoring their network. I believe this is a driver issue, so until broadcom release support for monitoring, you'll be dissappointed.
The next issue is the trackpad, out of the box it behaves in a crazy way, jumping around and selecting menus when you didn't actually click anything, etc.. This, again is a driver issue. Although the fix for this is rather simple.... It turns out the unit comes with the driver pre-installed, but it isn't selected for use! You can remedy this by going into the additional drivers app, and scrolling down until you find "Unknown" select the driver that's available for it and apply changes. The trackpad will then work like a dream, including multi-finger gestures!

Hope this is of help to some of you out there!

---

### Post by b.g.turner on 2015-07-16
Thanks for replying Temujin, I've been away from the office, and so haven't had the opportunity to use the ethernet. As to the question of if the other ports work - they do seem to work, though I've haven't been able to identify the precise ways / conditions that makes everything work all of the time. I think the best generalization boils down to these two things:

1. Plugging in a usb device (wireless mouse, wacom tablet, thumbdrive) seems to work even when the Inateck has been previously plugged into the computer
2. the Ethernet only seems to work if I plug the RJ45 into the Inateck first, and then plug the Inateck into the computer

It seems to work well enough for now, so if I find any other issues or determine a more precise way of describing the problem, I let you know! Thanks again!

---

