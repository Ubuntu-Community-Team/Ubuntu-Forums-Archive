---
title: "Ati Radeon HD 6450 / Wine"
date: 2013-06-14
forum: Hardware
---

### Post by vanquishedangel on 2013-06-14
Ok i have used ati cards for awhile now and have never run across this situation before.

my specs are:

hpdc 5750
8gig ram
ati radeon hd 6450
2.4 hgz dual core AMD 4800+
Lubuntu 64 bits 13.04

the issue is I was trying to get neverwinter online working then to create a guide on the forums about how. I noticed that wine in playonlinux was installing the wrong driver when i double checked and i assumed the it was installing the driver for the onboard graphics card (ati x300) that i had disabled. When i rebooted I discovered that the device id was different in the bios for the onboard card than what wine put in. the bios gave 5874 and wine gave 5974.

the device id for my ati radeon 6450 is 6779 but it is not in the bios. I am typing this using the 6450 so it works. I manually put that number in the wine registry but no change to graphics and low fps in game. I have also installed fglrx-updates and they install fine and see the graphics card (6450) the x300 is no longer supported by ati. If I install fglrx (the ubuntu release one) then i get a small window in the corner of my screen saying unsupported hardware. I then installed the xorg drivers from software sources and boot times were Identical, as well as fps in neverwinter.

I need to know what is going on here :) it seems as if I had been using the mesa drivers the whole time.

Update: I made sure all fglrx was removed by software sources and in synaptic, however I then ran the purge command and even though synapic didnt show any fglrx installed, the purge command removed them.

---

### Post by Mark Phelps on 2013-06-14
I wasn't aware that Wine installed any drivers, in fact, from what I knew, Wine was not able to install drivers.

Lubuntu is not going to install AMD restricted drivers automatically, you have to tell it to do so.  So, if you did not install them yourself, then you are using the default Radeon open-source drivers, which will not give you anywhere near the frame rate as will the fgkrx drivers.

As to fglrx driver install, in nearly all cases, the post-release drivers will fail.  Don't know why -- that's just the general experience.

You CAN download and install drivers from AMD but if you do that, you'll have to redo that every time you apply an Update that changes the Linux kernel.  If you install from Additional Drivers, you will not have to redo the install.

---

### Post by Yellow Pasque on 2013-06-14
> **Mark Phelps said:**
> You CAN download and install drivers from AMD but if you do that, you'll have to redo that every time you apply an Update that changes the Linux kernel.  If you install from Additional Drivers, you will not have to redo the install.

That's why you install fglrx with dkms (so it's updated automatically when you install a new kernel).

---

### Post by vanquishedangel on 2013-06-14
I have dkms, but the drivers from amd site failed every time with an error I cant remember. I followed the instructions here: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

In the repos the regular drivers do not see my graphics card as being supported, only the fglrx-updates package works.

Wine can sort of install graphics drivers, it installs the device Id and vendor id in regedit d3d folder, the string looks like this:

VideoPCIDeviceID   dword:00006997 (for amd 6450)
VideoPCIVendorID   dword:00001002 (for all ati)
VideoDriver   ati2dvag.dll

wine communicates with xorg for graphics and these values are pulled from the commands (manually) from "lspci" and "lspci -n"
it seems this process is automated in playonlinux when you select install videodriver from the configure menu. The card may still be too new yet for wine d3d and that could be why I need to manually change the dword value.

I can install the graphics drivers for the 6450 manually from the command line (fglrx-updates) and it all works fine.

P.S. I am really not that new to this, I been using linux and installing ati drivers since well before jockey let alone the software center, the good ol' days of straight up compiling from scratch.

---

