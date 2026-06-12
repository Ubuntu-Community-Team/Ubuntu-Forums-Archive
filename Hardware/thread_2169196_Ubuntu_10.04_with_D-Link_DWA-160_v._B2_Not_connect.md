---
title: "Ubuntu 10.04 with D-Link DWA-160 v. B2 Not connecting to wireless network"
date: 2013-08-21
forum: Hardware
---

### Post by Justin_Frahm on 2013-08-21
I have recently installed a wireless card D-Link DWA-160 version B2. I followed the directions at:
[http://bernaerts.dyndns.org/linux/74-ubuntu/229-ubuntu-precise-dlink-dwa160-revb2](http://bernaerts.dyndns.org/linux/74-ubuntu/229-ubuntu-precise-dlink-dwa160-revb2)
Except that I skipped step 4.5 as my kernel is still 2.6.32 and doesn't need the names changed and 4.6 since it doesn't look essential.
Everything complied and installed ok. My wireless card started blinking and I can now see the networks in the area. When I try to connect, I enter the passphrase and it attempts to connect for a while then disconnects. Every time.

I'm not sure what else to check.

---

### Post by sanderj on 2013-08-21
Why are you using 10.04? It's not supported anymore (unless you use the server edition).

If you live-boot Ubuntu 13.04 from a CD/USB-stick, does your wireless card work?

---

### Post by Justin_Frahm on 2013-08-21
I'm using 10.04 because I tried 12.04 but my hardware is not fast enough to have it run smoothly. I went back to 10.04 since I'm familiar with it. I'll give 13.04 a try. Should it work without any tinkering?

---

### Post by sanderj on 2013-08-21
> **Justin_Frahm said:**
> I'm using 10.04 because I tried 12.04 but my hardware is not fast enough to have it run smoothly. I went back to 10.04 since I'm familiar with it. I'll give 13.04 a try. Should it work without any tinkering?

If Ubuntu is too slow, you can consider Lubuntu.

I'm not sure if it works without any tinkering, but I hope so: 13.04 has a much newer kernel.

---

### Post by kurt18947 on 2013-08-21
> **Justin_Frahm said:**
> I'm using 10.04 because I tried 12.04 but my hardware is not fast enough to have it run smoothly. I went back to 10.04 since I'm familiar with it. I'll give 13.04 a try. Should it work without any tinkering?

I don't know about this particular adapter but newer kernels typically are superior for newer hardware.  I too would recommend Xubuntu or Lubuntu on older or lower spec. machines.

---

### Post by Justin_Frahm on 2013-08-21
Okay, one thing at a time: I installed a fresh version of 13.04 and now my eth0 won't connect either. I can't attempt the installation directions from the website I've already linked (at least not easily). It does the same thing that the D-Link was doing: it tries to connect for a minute or so then eventually just pops up as disconnected. The strange thing at least eth0 worked fine when I was running 13.04 from the USB drive.

---

### Post by sanderj on 2013-08-22
Hmm. Weird. You could go the usual way (ifconfig, show the network hardware with lspci, etc), but do you want to do that?

---

### Post by Justin_Frahm on 2013-08-23
Yeah, I kind of wrestled with all that stuff for a while and didn't make much progress. It took me quite a while just to get to the point where I could detect wireless networks and I seemed to hit a dead end there. I think I'm just going to return the card. I'll find one that is supported more easily and go with maybe 11.04 until I upgrade a lot of the hardware. There is weird network business going on and I'm not sure its worth fighting.

---

### Post by kurt18947 on 2013-08-23
A couple things to consider.  Yes, if you can return that adapter, that's probably a good idea.  I know of some N150 adapters that are plug 'n' play, I have no personal experience with N300/dual frequency wifi adapters.  If you want a gnome 2 feel, have you considered a MATE distro?  MATE is supposed to do a very good job of emulating gnome 2.  Xubuntu/XFCE is also a good choice on older/lower spec hardware.

---

