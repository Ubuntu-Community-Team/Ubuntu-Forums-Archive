---
title: "Switching to ATI RADEON video card from an nVIDIA - I plugged it in, now what?"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by XGhozt on 2009-11-01
So, I've had this 256mb nvidia quadro card, and it was really easy to setup my dual monitors with it on Ubuntu. But I just got my hands on an old ati radeon (512mb) video card, and I wanted to give it a try. I recently got two new monitors with a much higher resolution, and it was putting a strain on my 256 card.

So, before I rebooted with the new card, I installed the ati drivers from [here]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.36&lang=English").

After I rebooted, I loaded recovery mode into root console, and typed **aticonfig** but it's telling me it can't find any supported devices.

The new card is ATI RADEON X1900

And of course I can't boot properly because xorg is still configured for the nvidia card. I made a backup of the conf file, but I'm not sure what to change this to for it to work with the radeon card.

Any help would be appreciated. :)

---

### Post by jjcv on 2009-11-01
> **XGhozt said:**
> 

The new card is ATI RADEON X1900

And of course I can't boot properly because xorg is still configured for the nvidia card. I made a backup of the conf file, but I'm not sure what to change this to for it to work with the radeon card.

Any help would be appreciated. :)

If you delete the ond xorg.conf file then X should try to create a new one when it starts.   It should detect the new video card if all goes well.

---

### Post by XGhozt on 2009-11-03
> **jjcv said:**
> If you delete the ond xorg.conf file then X should try to create a new one when it starts.   It should detect the new video card if all goes well.

I tried that, then the GDM login screen went blank. I ended up just reinstalling Ubuntu, but I can tell it's still not working as intended.

But things are "working", but I don't know if it's utilizing the video card or not. fglrx, and fglrxinfo isn't even installed.

```
Section "Screen"
        Identifier      "Configured Screen Device"
        Device  "Configured Video Device"
        SubSection "Display"
                Virtual 3840 1080
        EndSubSection
EndSection

Section "Device"
        Identifier      "Configured Video Device"
EndSection


```

That's my xorg.conf file.

---

### Post by Mark Phelps on 2009-11-03
I didn't catch what version of Ubuntu you're running, but if it's 9.04 or newer, the problem is that you forced the installation of ATI drivers that won't work with your card or the OS.

Your card is one of the legacy cards that ATI dropped support for months ago. To get video back, you need to remove the ATI restricted drivers and replace them with the open source drivers.

Link below has the details:  [https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

---

### Post by XGhozt on 2009-11-04
Yeah I'm running 9.10.

I ran this:
```
lspci -nn | grep VGA
```
And it outputted:
> 01:00.0 VGA compatible controller [0300]: ATI Technologies Inc R580 [Radeon X1900 XT] (Primary) [1002:7249]

Let's say that I follow the rest of this tutorial, and then I get a black screen again after booting at the login screen. What's the best way to revert within recovery mode?

---

### Post by XGhozt on 2009-11-04
I tried this, and GDM failes after reboot:
```


Section "Screen"
	Identifier	"Default Screen"
	Device		"Radeon X1900"
	Monitor		"Samsung 2243"
	Virtual		3840 1080
	EndSubSection
EndSection

Section "Device"
	Identifier	"Radeon X1900"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Samsung 2243"
	HorizSync	30-75
	VertRefresh	56-61
EndSection

Section "DRI"
        Mode 0666
EndSection
        
Section "Extensions"
        Option "Composite" "Enable"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

```

---

### Post by XGhozt on 2009-11-04
Is it just working as is? I ask because of the following:
[code]
xghozt:~$ glxinfo | grep vendor
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: DRI R300 Project
xghozt:~$ glxinfo | grep "direct rendering"
direct rendering: Yes

---

