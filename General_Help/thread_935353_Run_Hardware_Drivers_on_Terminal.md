---
title: "Run Hardware Drivers on Terminal"
date: 2008-10-01
forum: General Help
---

### Post by roboa1983 on 2008-10-01
I am trying to use Hardware Drivers to install and nVidia driver. However, that has messed up my computer and now after a seemingly succesful installation, my machine outputs just a tiny horizontal line on the very top. 
Is there a way to run Hardware Drivers on the terminal in order to uninstall this driver?
Thanks

---

### Post by pytheas22 on 2008-10-02
You could edit your /etc/X11/xorg.conf file to tell it to use the default driver, instead of the proprietary one that apparently doesn't work.  To do so, log in on the command line and type:

```
sudo nano /etc/X11/xorg.conf
```

Look for a section labeled "Device."  It probably looks like this now:
```

Section "Device"
	Identifier	"Configured Video Device"
EndSection
```

Add in a line so that it looks like this:
```

Section "Device"
	Identifier	"Configured Video Device"
        driver          "nv"
EndSection
```

Then press control-O (the letter, not zero) to save the file, and control-X to exit nano.  Does this at least allow you to boot to the desktop again?

---

### Post by roboa1983 on 2008-10-03
Hi
I did those changes and I could log in through gnome. However, I don't get the right resolution. The maximum one is 800x600. I've been trying to find other solutions, but there seems to be no systematic way of solving this.I know that my last version of xorg.conf had a section with the resolutions and frequencies on them. However, I can't seem to find anything that can make me get back to this state (should have backuped).

Thanks for the help so far.

---

### Post by Sef on 2008-10-03
What is your graphics card?

---

### Post by pytheas22 on 2008-10-03
Glad to hear you can log into Gnome again.

It may help to use [envy]("http://albertomilone.com/nvidia_scripts1.html") to install your drivers if you haven't already tried it.  It doesn't always work, but it usually does.

If envy still doesn't help, please tell us the exact model of your graphics card, as well as the output of:
```

lspci -nn
cat /etc/X11/xorg.conf
```

Also, if envy breaks your configuration again and makes it impossible to log into Gnome, the solution from last time (adding that line to /etc/X11/xorg.conf) should at least get you back to Gnome.

---

### Post by roboa1983 on 2008-10-04
Hi
Thanks for the help.
The graphics card is:
nVidia GeForce 6100

Envy failed as it has before for me. 
There's a python command it cannot run (raise SystemError, "installArchives() failed"), but I should look into that later. 

Here's the following output:



```

$ lspci -nn
00:00.0 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02f1] (rev a2)
00:00.1 RAM memory [0500]: nVidia Corporation C51 Memory Controller 0 [10de:02fa] (rev a2)
00:00.2 RAM memory [0500]: nVidia Corporation C51 Memory Controller 1 [10de:02fe] (rev a2)
00:00.3 RAM memory [0500]: nVidia Corporation C51 Memory Controller 5 [10de:02f8] (rev a2)
00:00.4 RAM memory [0500]: nVidia Corporation C51 Memory Controller 4 [10de:02f9] (rev a2)
00:00.5 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02ff] (rev a2)
00:00.6 RAM memory [0500]: nVidia Corporation C51 Memory Controller 3 [10de:027f] (rev a2)
00:00.7 RAM memory [0500]: nVidia Corporation C51 Memory Controller 2 [10de:027e] (rev a2)
00:02.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fc] (rev a1)
00:05.0 VGA compatible controller [0300]: nVidia Corporation C51G [GeForce 6100] [10de:0242] (rev a2)
00:09.0 RAM memory [0500]: nVidia Corporation MCP51 Host Bridge [10de:0270] (rev a2)
00:0a.0 ISA bridge [0601]: nVidia Corporation MCP51 LPC Bridge [10de:0261] (rev a3)
00:0a.1 SMBus [0c05]: nVidia Corporation MCP51 SMBus [10de:0264] (rev a3)
00:0a.2 RAM memory [0500]: nVidia Corporation MCP51 Memory Controller 0 [10de:0272] (rev a3)
00:0b.0 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026d] (rev a3)
00:0b.1 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026e] (rev a3)
00:0d.0 IDE interface [0101]: nVidia Corporation MCP51 IDE [10de:0265] (rev f1)
00:0e.0 IDE interface [0101]: nVidia Corporation MCP51 Serial ATA Controller [10de:0266] (rev f1)
00:10.0 PCI bridge [0604]: nVidia Corporation MCP51 PCI Bridge [10de:026f] (rev a2)
00:10.1 Audio device [0403]: nVidia Corporation MCP51 High Definition Audio [10de:026c] (rev a2)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
03:08.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5788 Gigabit Ethernet [14e4:169c] (rev 03)

```

I'm omitting the initial comments in xorg.conf to avoid verbosity.

```

$ cat /etc/X11/xorg.conf
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
	Disable	"dri2"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	driver "nv"
EndSection

```

Thanks once again for the help. Hopefully this can be solved once and for all.

---

### Post by pytheas22 on 2008-10-04
Which driver did you install before?  nvidia says that your card should be supported by the nvidia-glx-new driver, and I can't find anyone else who had problems like yours with it (although I didn't try exhaustively).  Are you sure that you installed nvidia-glx-new before and not just nvidia-glx?  You could always try again and in a worst case fall back to the 'nv' driver in xorg.conf:
```

sudo apt-get install nvidia-glx-new
```

---

