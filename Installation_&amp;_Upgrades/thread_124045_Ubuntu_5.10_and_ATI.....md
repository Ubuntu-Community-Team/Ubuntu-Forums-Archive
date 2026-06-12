---
title: "Ubuntu 5.10 and ATI...."
date: 2006-01-31
forum: Installation &amp; Upgrades
---

### Post by EndGame on 2006-01-31
As stated, doing some research and finding a lot of people with problems installing with ATI cards and for some reason, speciically the X800XL cards. I've done some reading but can not find a reason, nor a fix or easy workaround. Seems you must install and then go back and reinstall VESA drivers to even gain access to Gnome. 

My question, since a Google search finds numerous occurances of this problem and problems in general with ATI cards, is there a simple workaround/fix I've missed?

---

### Post by az on 2006-01-31
Does your card work?  

You should be able to install and run ubuntu fine.  It will not use hardware acceleration by default, since the drivers for this are not free-libre open source. 

If you need to use 3d acceleration, you can easily install the packages to get it working.  See here:
[https://wiki.ubuntu.com/BinaryDriverHowto](https://wiki.ubuntu.com/BinaryDriverHowto)

It should not be a problem.

The hubbub is that these drivers are made by the manufacturer and released in binary (unmodifyable) form.  If they were release as source code that you could share and improve (GPL'ed code) then they would work by default and get better and better as people add improvements to them.  As it is, probably only a small handful of people are working on them to make them better.  That's the cornerstone of free-libre software - the more people who can see the code and modify it, the better it gets.

---

### Post by EndGame on 2006-01-31
That's just it, it doesn't "work" without going back into recovery mode and switching the drivers from ATI to VESA. Anything other than VESA and there is no GUI. 

I've messed with the ATI drivers and honestly, since I don't game on Ubuntu, it's not worth the hassle.

My objective here and for some others in other forums was to find out about this problem and if there is a "fix".

System Specs:

AMD A64 3700+
Asus A8N-E nForce 4 Ultra
ATI X800XL
2X300GB Seagate
Creative Soundblaster Audigy 2 NX
2GB Corsair XMS XLL PC3200 2-2-2-5

---

### Post by az on 2006-01-31
[QUOTE=EndGame]My objective here and for some others in other forums was to find out about this problem and if there is a "fix".
[/QUOTE]

File a bug for the xserver-xorg-driver-ati package

or perhaps add to this one:
[https://launchpad.net/distros/ubuntu/+bug/6037](https://launchpad.net/distros/ubuntu/+bug/6037)


Also:

[https://launchpad.net/malone/distros/ubuntu?field.searchtext=xserver-xorg-driver-ati&orderby=-priority%2C-severity&search=Search](https://launchpad.net/malone/distros/ubuntu?field.searchtext=xserver-xorg-driver-ati&orderby=-priority%2C-severity&search=Search)

---

