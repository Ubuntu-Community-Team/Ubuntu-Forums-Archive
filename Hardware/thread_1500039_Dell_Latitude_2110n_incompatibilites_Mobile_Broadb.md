---
title: "Dell Latitude 2110n incompatibilites: Mobile Broadband 5620/Gobi 2000, Wireless 1501"
date: 2010-06-02
forum: Hardware
---

### Post by natefoo on 2010-06-02
Hi all,

I've just received a Latitude 2110n which I was planning to use on one of the US cell networks.  As such, I ordered it with the Dell Wireless 5620 / Gobi 2000 Mobile Broadband card.

Upon receiving the laptop, I was surprised to discover that this card was completely unrecognized by the system.  A quick aside, neither was the Dell Wireless 1501 / Broadcom BCM4313 b/g/n card, and for some reason bcmwl-kernel-source didn't work with it either - I had to compile the STA/wl driver by hand.

Unlike the Broadcom, Qualcomm does not directly release drivers for the Gobi card, although they mention that it's supported under Linux.  Dell has Windows drivers, but I have yet to extract anything useful from the driver - according to the [gobi_loader page]("http://www.codon.org.uk/%7Emjg59/gobi_loader/"), all you need is the firmware.  Unfortunately, the Windows driver exe unzips and places a bunch of .cat, .inf and .sys files on disk, but nothing that looks like firmware (I suspect it may be in the sys files, but can't figure out how to get it out).  The Setup.exe contained within the self-extracting exe downloaded from Dell support doesn't run, I assume because I'm not running it on the 2110 or because there's no Gobi card installed on the machine I'm trying to extract drivers on.

Other vendors (such as Lenovo) have more useful Windows drivers, as can be seen here:

[http://www.thinkwiki.org/wiki/Talk:Qualcomm_Gobi_2000](http://www.thinkwiki.org/wiki/Talk:Qualcomm_Gobi_2000)

I did manage to extract that firmware from the Lenovo driver, but I'm not clear on whether that firmware is compatible with my Dell-branded Gobi card.  Any hints here would be appreciated (or at least thoughts on whether trying them might damage my hardware). ;)

I'm trying to work this through Dell's support channel but thus far have not gotten anywhere.  Their Ubuntu support team told me to post here and someone would produce the drivers, but everything I'm reading about the Gobi card says drivers have to come from the vendor.

So, buyers beware, it doesn't seem like Dell has done much in the way of ensuring Ubuntu compatibility on this hardware, despite selling a special Linux version of it in their store...

---

### Post by natefoo on 2010-06-03
So, I finally found the actual firmware.  cabextract on the Dell Windows driver's Utility/Setup.exe will extract a bunch of files like:

_1399D3D2AB15428390AB9541D41069F9
_18D8D1860AC74D6C96798DB49BCBEE1B

etc.  By comparing file sizes and the output of 'strings' with the Lenovo versions, I was able to determine which of these were the appropriate firmware for my provider.  Interestingly, while my drivers were the same size (to the byte) of the Lenovo versions, their contents were slightly different.

Aaaaaaaaaaanyway, I've now learned that thanks to the awesomeness of CDMA technology, you have to program the modem to use the new number assigned.  And AFAIK this programming is only possible via VZW's Windows/Mac application.  Anyone know of a way to do this under Ubuntu, or am I SOL?

Gonna try Wine first, I guess, and failing that, try a Windows VM.  And failing that, switch to AT&T. =P

---

### Post by CalaverX11 on 2010-08-12
I installed the firmware in Windows, but the card isn't activated yet. Will it only show up in Network Manager if/when it's activated?

---

### Post by natefoo on 2010-08-12
It should show up in Ubuntu even before activation.  You'll need to make sure you have gobi_loader installed, the firmware properly placed in /lib/firmware and the recompiled kernel modules installed.  I used this process:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/554099/comments/33](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/554099/comments/33)

---

