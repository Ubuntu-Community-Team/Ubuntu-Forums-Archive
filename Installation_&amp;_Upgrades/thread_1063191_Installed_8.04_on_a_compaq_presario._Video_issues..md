---
title: "Installed 8.04 on a compaq presario. Video issues."
date: 2009-02-07
forum: Installation &amp; Upgrades
---

### Post by TombKing on 2009-02-07
amd athlon 64
1GB ram
ATI Radeon XPRESS 200 video card

Grub starts in an unsupported video mode so blank screen.

It does boot to the login screen. Gnome only will come up in safe mode. Not sure what startup script is hosing the X session but something is.

I do have network and updates are downloading. I hope that fixes things.

Any hints for editing the grub settings so I can actually see it and what might be b0k3d on the gnome startup?

Thanks in advance.

---

### Post by avtolle on 2009-02-07
Once done downloading and updating, I suggest that you will want to try to install the ati driver before restarting from System>Administration>Hardware Drivers and see if that takes care of your problem, which is related to your ATI video card.

---

### Post by avtolle on 2009-02-07
Here's a little something I found after reading another thread: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver) which might help.

---

### Post by TombKing on 2009-02-07
yay gnome loading fine.

still get no screen for grub though. this would be the same settings for a non gui console as switching to a standard console session gives me the same grub error.

at least i am working and updated with it. now just to get the kid to be patient while i load the edbuntu extras and get a pci wireless card working.

---

### Post by TombKing on 2009-02-08
I ended up punting and redoing it from scratch with 8.10 which works just fine.
Still not sure where the video settings are for the plain terminal settings are though.

My only issues now are wireless network so that much is good. It connects to the neighbors open stuff but does not work on my passworded setup. Not that the kid really needs internet access all that bad.

---

