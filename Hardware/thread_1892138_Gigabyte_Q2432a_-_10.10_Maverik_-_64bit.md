---
title: "Gigabyte Q2432a - 10.10 Maverik - 64bit"
date: 2011-12-07
forum: Hardware
---

### Post by ramster64 on 2011-12-07
Installed 10.10 on a new Gigabyte Q2432 notebook with the following specs:

Display: 14" 1366 x 768 LCD
Graphics: AMD Radeon HD 6730M / 1G
CPU:  i3-2330M
Ram:  4GB DDR3
OS:  Ubuntu - 64 (10.10 Maverik)

At first i had to install the wireless driver to get online by doing the following:

```
cd && wget http://ftp.us.debian.org/debian/pool/non-free/f/firmware-nonfree/firmware-realtek_0.34_all.deb

sudo dpkg -i --force-overwrite firmware-realtek_0.34_all.deb
```

But there are still several things that are bugging me and i hope to list them here as i fix them, and it be great to get some pointers as well as i am not that sure on how to fix all the bugs which are:

when i do the following command '**sudo update-initramfs -u**' this lists:

```
W: Possible missing firmware /lib/firmware/radeon/SUMO_rlc.bin for module radeon
W: Possible missing firmware /lib/firmware/radeon/PALM_me.bin for module radeon
W: Possible missing firmware /lib/firmware/radeon/PALM_pfp.bin for module radeon
W: Possible missing firmware /lib/firmware/radeon/CAYMAN_rlc.bin for module radeon
W: Possible missing firmware /lib/firmware/radeon/CAYMAN_mc.bin for module radeon
W: Possible missing firmware /lib/firmware/radeon/CAYMAN_me.bin for module radeon
W: Possible missing firmware /lib/firmware/radeon/CAYMAN_pfp.bin for module radeon
W: Possible missing firmware /lib/firmware/radeon/CAICOS_mc.bin for module radeon
W: Possible missing firmware /lib/firmware/radeon/CAICOS_me.bin for module radeon
W: Possible missing firmware /lib/firmware/radeon/CAICOS_pfp.bin for module radeon
W: Possible missing firmware /lib/firmware/radeon/TURKS_mc.bin for module radeon
W: Possible missing firmware /lib/firmware/radeon/TURKS_me.bin for module radeon
W: Possible missing firmware /lib/firmware/radeon/TURKS_pfp.bin for module radeon
W: Possible missing firmware /lib/firmware/radeon/BTC_rlc.bin for module radeon
W: Possible missing firmware /lib/firmware/radeon/BARTS_mc.bin for module radeon
W: Possible missing firmware /lib/firmware/radeon/BARTS_me.bin for module radeon
W: Possible missing firmware /lib/firmware/radeon/BARTS_pfp.bin for module radeon
```

Right now the most annoying thing is the graphics they are poor and simple video playback has horizontal stripes in it. 

Here is a threat i have followed to try and get the graphics working properly:

[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)

I followed the:

**[SIZE="2"]Problem: Need to fully remove -fglrx and reinstall -ati from scratch[/SIZE]**

Instruction but still no change in display quality.

Then i also did try to install the proprietary driver that shows up under '**additional drivers**' but that always errors out.

There also is a linux 64 bit driver available directly from AMD Radeon here:

[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx)

Tried to install that but the machine would not even boot after the install.

I also did try to get it to work on the latest 11.10 release but the same poor graphics even though the proprietary driver does install on that properly?

I would like to continue to use the 10.10 version as that is the purpose of this notebook.

+++Update+++

Have not fixed anything yet but have some more errors to post which happen at boot time:

```
[    0.002140] [Hardware Error]: No human readable MCE decoding support on this CPU type.
[    0.002145] [Hardware Error]: Run the message through 'mcelog --ascii' to decode.
[    0.002149] Disabling lock debugging due to kernel taint
[    0.002151] [Hardware Error]: No human readable MCE decoding support on this CPU type.
[    0.002155] [Hardware Error]: Run the message through 'mcelog --ascii' to decode.
```

+++UPDATE+++

Managed to install the proprietary driver from Radeon and now most errors have gone, no idea why it would not install prior but i am not complaining ;)

---

### Post by ramster64 on 2012-01-29
Installed 11.11 on a new Gigabyte Q2432 notebook with the following specs:

Display: 14" 1366 x 768 LCD
Graphics: AMD Radeon HD 6730M / 1G
CPU:  i3-2330M
Ram:  4GB DDR3
OS:  Ubuntu - 64 (11.11 Oneiric)

after the fresh install of 11.11 i simply went through the same process of installing the AMD Catalist driver available here:

[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx)

like i did with 10.10 but for some reason it now does not use the driver but keeps hanging at boot. the only way to get back into X is to wipe the /etc/X11/xorg.conf file and then starx after.

not sure if this is due to the xorg.conf file that gets created at driver install here is the step by step tutorial i followed:

[http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#The_Options](http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#The_Options)

This is the xorg.conf file after the install:

```
Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
        load "dri"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	Option	    "UseFastTLS" "1"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection
```

have tried several variations of the xorg.conf file but none work so far, as far as i can tell the driver installed properly but it does not manage to activate at boot time.

any help would be very welcome i will continue to trial and error and update any new issues that pop up.

---

