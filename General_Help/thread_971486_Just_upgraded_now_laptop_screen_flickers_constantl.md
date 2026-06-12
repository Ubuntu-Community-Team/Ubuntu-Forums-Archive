---
title: "Just upgraded now laptop screen flickers constantly"
date: 2008-11-05
forum: General Help
---

### Post by cr4z3d on 2008-11-05
I decided to upgrade from 8.04 LTS to 8.10 tonight and it finally finished after about 3 hours and now my laptop seems to go between my desktop and a black screen giving it a flicker feeling. It seems to do this randomly and in no particular pattern. I'm not sure what this could be but possibly a graphics driver issue? I've got an ATI Mobility Radeon X1600 on my Acer TravelMate 8200 and was using the ATI driver to get hardware acceleration for Compizfusion. 

Can anyone help me? Unfortunately my knowledge of xorg is pretty limited but I can easily paste in the configurations and any other needed info.

---

### Post by cr4z3d on 2008-11-05
Well seems I fixed the problem by booting into recovery mode and choosing the xfix option. It looks like it put in a default xorg.conf file to use and that solved my issue.

---

### Post by cr4z3d on 2008-11-05
Nope never mind. Now it just happens a lot less often. I feel like I'm going to get a seizure haha.. But here I'll show you what's in my xorg configuration:

```

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "Monitor"
	Identifier   "Configured Monitor"
EndSection

Section "Device"
	Identifier  "Configured Video Device"
	Driver      "fglrx"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
	DefaultDepth     24
EndSection

```

Which now that I look at it has almost nothing in it anymore.. Hmmm.. Any suggestions?

---

### Post by Peter09 on 2008-11-05
do the following terminal command

```
lshw -C display
```
to get an idea of your driver set up. What version of Ubuntu are you using, Intrepid?

---

### Post by cr4z3d on 2008-11-05
Yes I'm on Intrepid now. I just upgraded from Hardy. Here's the output from the above command:

```

  *-display               
       description: VGA compatible controller
       product: M56P [Radeon Mobility X1600]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list
       configuration: driver=fglrx_pci latency=0 module=fglrx

```

---

### Post by Peter09 on 2008-11-05
OK,
can you look in System->Applications->Hardware Drivers

See if its asking for you to enable a third party driver

---

### Post by JunCTionS on 2008-11-12
I have a similar if not the same problem.
The screen flickers with the same image but displaced.
It's like it's suddenly out of sync snd shows the screen out of place
I was surprised to find out how the Xorg.conf holds so little information now, so I don't even know where to look.
I tried configuring it manually the old way but I only managed to get the screen to it's real resolution (the initial install guessed a smaller resolution).
There are no third party drivers on this machine, and in that dialog (Hardware drivers) it only mentions the drivers for the wireless card (made by the ubuntu team).
I'm (temporarily, this is not my permanent laptop) using a Toshiba M55-S135 with Kubuntu Intrepid Ibex 8.10 (KDE4).
And I'm going a bit nuts :biggrin: with this glitch. HELP!

---

### Post by cr4z3d on 2008-11-13
> **Peter09 said:**
> OK,
can you look in System->Applications->Hardware Drivers

See if its asking for you to enable a third party driver
The ATI proprietary driver is in use as it says

---

### Post by JunCTionS on 2008-12-12
as Niscrome pointed out in [this thread]("http://ubuntuforums.org/showthread.php?t=981007"), a fix for kubuntu (my problem was only in Kubuntu with the big K) is to disable the option to monitor changes of monitor by RANDR in the Service Manager.
Hope it helps you guys.

---

### Post by nannus on 2008-12-19
Disabling Compiz seems to fix the issue.

---

