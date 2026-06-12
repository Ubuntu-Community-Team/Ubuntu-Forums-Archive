---
title: "installing video drivers?"
date: 2009-01-31
forum: Hardware
---

### Post by acaprez on 2009-01-31
I have a toshiba satellite m55-s135 with an intel gma900 video card. I just installed ubuntu 8.10 and noticed video performance is slower than under windows. I turned off visual effects already. After some searching I read that the command "lshw -c video" should not list my display as "UNCLAIMED" as it does. The post said to change my xorg.conf to add the line driver "intel" but this did nothing. How can I make sure the proper video drivers are loaded and what else can I do to speed up video performance?

thanks

---

### Post by lykwydchykyn on 2009-01-31
I've never had to do anything to get Intel video working on any Linux.  Most likely the drivers are loaded fine.  Post the output of this command and we can verify that:
```

sudo cat /var/log/Xorg.0.log |grep -i driver

```

What are the specs of the machine?  Intel onboard graphics are decent (I've had good luck running desktop effects on an old laptop with 855gm chipset), but they don't have a lot of video memory at their disposal typically.  That can result in a poor performance.

---

### Post by acaprez on 2009-01-31
the output is ...


	X.Org Video Driver: 4.1
	X.Org XInput driver : 2.1
(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	ABI class: X.Org Video Driver, version 4.1
	ABI class: X.Org Video Driver, version 4.1
	ABI class: X.Org Video Driver, version 4.1
	ABI class: X.Org Video Driver, version 4.1
(II) EXA(0): Driver registered support for the following operations:
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.1
(II) Synaptics touchpad driver version 0.15.2


If the drivers aren't the issue, what can I do to speed ubuntu up? It's a 1.5ghz celeron mobile, 512mb ram. Full specs are here [http://reviews.cnet.com/laptops/toshiba-satellite-m55-s135/4507-3121_7-31447704.html](http://reviews.cnet.com/laptops/toshiba-satellite-m55-s135/4507-3121_7-31447704.html)

One thing that made me think it's the video card (other than slower than xp video performance with windows refreshing in general) is the extremely slow performance of GLSlideshow that I'm trying to use for a picture slideshow. Usually gives me errors, too.

---

### Post by lykwydchykyn on 2009-01-31
I don't know that there's much more you can do; I'm using a laptop of similar specs, apart from upgraded RAM.  The performance is decent, but I'm also not using vanilla Ubuntu so I don't know what that would be like.

You might check the BIOS to see if there's a place to set the video RAM, and you might want to update the BIOS (I had a lot of problems with Dells that had certain Intel chipsets, but upgrading the BIOS usually fixed it).

Other than that, you might try something lighter than full-on Ubuntu if you want more speed.  Xubuntu is marginally faster, fluxbuntu and crunchbang are reportedly quite a bit faster.  

Of course you don't really have to reinstall, just try installing xubuntu-desktop, or fluxbox, or icewm, or openbox, or lxde from the repositories.  Then log out, select the new environment on the "session" menu, and log back in.  Probably be faster.

---

