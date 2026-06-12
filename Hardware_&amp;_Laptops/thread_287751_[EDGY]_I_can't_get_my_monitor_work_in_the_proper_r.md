---
title: "[EDGY] I can't get my monitor work in the proper resolution"
date: 2006-10-29
forum: Hardware &amp; Laptops
---

### Post by LeonHeart on 2006-10-29
Hi guys, I have been using Ubuntu Dapper for a long time.
Yesterday I downloaded Ubuntu Edgy and just a few hours ago
I installed it. The problem that I face is:

"While in Dapper my monitor worked fine under 1280x1024x32@60Hz now
in Edgy the "Screen Resolution" has available only the choice
of 1024x768x32@60Hz. What can I do in order to fix this?"

Any help will be appreciated,
Thanks

---

### Post by LeonHeart on 2006-10-29
I forgot to tell you,
my graphic card is ATI 9200 Pro and my monitor is LG L1715S (17'.)

---

### Post by neur0 on 2006-10-29
I have the same problem, only I have NVidia 7600SG AGP.

---

### Post by dedefbs on 2006-10-29
Hi there! What you can try is to install your video proprietary driver(fglrx)-from ati- I think it is in ubuntu packages as xorg-driver-fglrx or something like that(I never used ati graphics card). 
Otherwise, you can try to get other resolutions to work doing the following:

Open a console

then "sudo dpkg-reconfigure xserver-xorg". It'll appear a X window with options(the best choice of video driver is the ati one if you don't have the fglrx one or doesn't like proprietary drivers), simply go on hitting "ok" till appear the choices of resolution that you can try. It will give every option of resolution avaible, but be sure to not overdo it, so see wich is the maximum resolution of your monitor. 

Then hit ok till it ends and it should work just fine. If there is any sort of problem(like X server not opening anymore), then all you have to do is to enter "cd /etc/X11/" on terminal.
After that  "ls -a" and see a archive with the following name "xorg.confANDADAMNBIGNUMBER" and digit on console "sudo cp xorg.confANDADAMNBIGNUMBER xorg.conf" to restore the old configurations.
You can e-mail me for questions if you want. 
[email]dedefbs@yahoo.com.br[/email]

---

### Post by neur0 on 2006-10-29
I just solved my problem with editing xorg.conf and adding "1280x1024" (with quotes) to the existig list of resolutions at the bottom of the file (repeat for all "modes" in the file
```

sudo gedit /etc/X11/xorg.conf

```
and the edited part is now:
```

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NVIDIA Default Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

```
at the very end of the config file

---

### Post by theFallen on 2006-10-29
Had allways the same problem after each upgrade.
The solution I found, which didn't help was:
Option "UsesEDID" "false"

but

Option "UsesEDIDFreqs" "false"

did the trick. Don't forget to add a modeline.
Hope it this work, for you to.

---

### Post by nbhaskar on 2006-10-29
I've a similar problem, have a ATI X700 card. When I go to Screen resolution preferences, I see only 800x600 and 640x480. I want to get 1024X768 resolution, which is the maximum supported by my CRT monitor.

My xorg.conf file has the following. Still I cannot get the resolution I want.

```
Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon X700 Pro (RV410)"
	Driver		"radeon"
	BusID		"PCI:5:0:0"
EndSection

Section "Monitor"
	Identifier	"DELL M991"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon X700 Pro (RV410)"
	Monitor		"DELL M991"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

```

Can you experts out there help me get over this small inconvenience?

Thanks in advance.

---

### Post by nbhaskar on 2006-11-07
I finally installed latest fglrx driver by following the instruction as given here
[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_new_8.30.3_drivers_in_Ubuntu_Edgy_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_new_8.30.3_drivers_in_Ubuntu_Edgy_Manually)

I got above mentioned resolution issue sorted out. Here is my fglrx info

```
babu@babu-desktop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X700 PRO Generic
OpenGL version string: 2.0.6119 (8.30.3)
```
:-D

---

### Post by jayachandranm on 2006-11-07
I faced similar problem with my Edgy installation. My graphic card is "ATI Radeon X300" and monitor "Dell 1704FPT (Digital)". 

My previous Dapper installation configured everything properly to give me 1280x1024 resolution. But Edgy installation did not detect my monitor, resulting in a lower resolution, 1024x768.

To fix this issue, I manually edited xorg.conf and changed the monitor section and added the high resolution modes to the display subsection. That worked for me. My system seems to use default driver "ati".

Jaya

---

