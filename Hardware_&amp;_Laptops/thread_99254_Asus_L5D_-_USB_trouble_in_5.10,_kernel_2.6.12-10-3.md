---
title: "Asus L5D - USB trouble in 5.10, kernel 2.6.12-10-386"
date: 2005-12-05
forum: Hardware &amp; Laptops
---

### Post by coyot on 2005-12-05
I've recently installed on Asus L5000 series (model L5D) - AMD64 based NB.

This is a second installation attempt and here's the problem:
After bootup, with USB mouse plugged in (I tried several different - Logitech NV500, original asus UV55-a), within 30 minutes the mouse pointer freezes. Touchpad continues to work as does keyboard, but, along with the mouse pointer, DNS name resolution goes tits up. Existing ssh and ICQ connections can still happily use the network, XMMS keeps playing next items in the playlist, but web traffic is toast. 
After ifdown eth0 and ifup eth0, I can't seem to get any response from DHCP server (again tried in different networks).

I read the forums, tried acpi=off, tried noacpi, noioapic... darn BIOS contains nothing like USB Legacy setting, either. 

Problem manifests even with the default, off the shelf installation.

This is what I found in the messages.log:
> Dec  5 14:05:30 localhost kernel: [  790.566486] usb 1-2: USB disconnect, address 2 

syslog:
> Dec  5 14:05:30 localhost kernel: [  790.566486] usb 1-2: USB disconnect, address 2
Dec  5 14:05:31 localhost kernel: [  791.630872] ohci_hcd 0000:00:02.0: IRQ INTR_SF lossage
Dec  5 14:05:31 localhost hal.hotplug[8111]: DEVPATH is not set (subsystem input)
Dec  5 14:05:31 localhost kernel: [  791.816951] ohci_hcd 0000:00:02.0: bad entry 17d99001 

Will be grateful for any help/ideas

---

### Post by bag71 on 2006-01-16
hi and sorry for my english
i've the same problems; a work around is to remove the nvidia driver in xorg.conf and insert "nv" driver. With nvidia propietary driver the problem appears also for mandriva 2006 and ubuntu breezy 5.10. 
The usb external mouse work fine only with suse 9.3 (10.0 have a bug with acpi and yu have to download a big file).
I don't know where is the bug.

---

### Post by coyot on 2006-02-08
Unfortunately, this does not do the trick. I have an off-the-shelf install (no changes to configuration, no proprietary drivers). The graphics card driver in xorg.conf definitely says "nv", nothing else.

It's just that bloody USB controller in my bloody notebook that acts funny.

---

### Post by bag71 on 2006-05-30
Hi.
I've found something about this trouble (possible bug in hide-core.c). I'm not sure this is the solution, but please see 
[http://lists.debian.org/debian-kernel/2005/12/msg00509.html](http://lists.debian.org/debian-kernel/2005/12/msg00509.html)

---

### Post by bag71 on 2006-06-01
OK. I'm solved with a "hw patch"; with a external usb 2.0 hub (without power supp.), where plugin my optical mouse.
After 1 hour i've tested that my laptop with ubuntu breezy d'ont freeze.
I hope that with the new kernel this bug is fixed.

---

