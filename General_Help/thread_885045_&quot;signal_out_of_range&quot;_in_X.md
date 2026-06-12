---
title: "&quot;signal out of range&quot; in X"
date: 2008-08-09
forum: General Help
---

### Post by evildonut on 2008-08-09
I can't get X to work.

This is a fresh install, using Wubi. I have a Geforce 7600 GS. When X starts up, the screen goes blank, and my monitor says "Signal out of range". I can hear the little drum sound, so I know X actually starts. I can also drop to consoles using ctrl+alt+F2 and so on, but there seems to be some misconfiguration here, too: the text doesn't scroll, so once I've got a screenfull of text (say, from doing a ls in /etc/) I can't see what I type or whatever is printed on the screen.

I've tried dpkg-reconfigure xserver-xorg, but it only asks about keyboard related information and then quits. No stuff on video.

I've looked at xorg.conf in vim (a program I have no idea of how to use - I can't even figure out how to quit), and it looks kinda incomplete compared to other xorg.conf's I've seen. For instance, there is no entries on vsync or resolutions or anything like that.

From memory, it looks something like this (I'm not completely sure):
```

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Generic Monitor"
EndSection

```

There's nothing to indicate that it has detected my graphics card or anything like that.

Please help :(

---

### Post by x1a4 on 2008-08-09
Hi,
For some reason your resolution is set to something greater than what your display supports.  On the login screen, click 'Session' and select 'Failsafe Terminal', login and see if you still get the out of range errors. If not, use nano (instead of vim) to edit your /etc/X11/xorg.conf file and reduce the resolution.  Here's an example:
```

Section "Screen"
  Identifier      "Default Screen"
  Monitor         "Generic Monitor"
  SubSection "Display"
    Depth     24
    Modes    "1024x768" "800x600"
  EndSubSection
  SubSection "Display"
    Depth     16
    Modes    "1024x768" "800x600" "640x480"
  EndSubSection
EndSection

```
Restart the X server: Ctrl+Alt+BS

BTW to exit in vim hit Esc than :q
to write to file then quit :wq
to quit without saving :q!

---

### Post by evildonut on 2008-08-09
I can't click on "Session" as I don't get any GUI at all :)

I've edited xorg.conf as you instructed (yay nano!), but it didn't help. Monitor still says "Input signal out of range".

For reference, I'm running Core 2 Duo 6300 1,8 GHz on a Biostar PT890 775 SE mainboard. Graphics card is an Nvidia Geforce 7600GS, and the monitor is a HP L1940T. Native res is 1280x1024. I tried adding that resolution to xorg.conf as well, same result.

I guess Ubuntu can't properly detect my hardware?

---

### Post by zxscooby on 2008-08-09
can you post your xorg.conf ?

---

### Post by x1a4 on 2008-08-09
In the "Device" section for the video card set the Driver to 'nv'.  This is the free nvidia driver.  It doesn't support 3D or many other features, but it should get you X.  For example:
```

Section "Device"
  Identifier  "nVidia"
  Driver      "nv"
  ...
EndSection

```

Once you have everything resolved, you can switch to the restricted driver.

Make sure the Identifier matches the Device value in Section "Screen".

Also, do you have the nvidia driver installed?  It's the **nvidia-glx-new** package.

Finally, have a look at the **nvidia-xconfig** man page.  nvidia-xconfig is a tool to help you setup nvidia for X.

---

### Post by evildonut on 2008-08-09
> **zxscooby said:**
> can you post your xorg.conf ?

I'm leaving out stuff on keyboards ans such:

```

Section "Device"
 Identifier "Configured Video Device"
EndSection

Section "Monitor"
 Identifier "Configured Monitor"
EndSection

Section "Screen"
 Identifier "Default Screen"
 Monitor    "Configured Monitor"
 Device     "Configured Video Device"
  SubSection "Display"
    Depth     24
    Modes    "1024x768" "800x600"
  EndSubSection
  SubSection "Display"
    Depth     16
    Modes    "1024x768" "800x600" "640x480"
  EndSubSection
EndSection

Section "Server Layout"
 Identifier "Default Layout"
 Screen "Default Screen"
EndSection

```

---

### Post by evildonut on 2008-08-09
> **x1a4 said:**
> In the "Device" section for the video card set the Driver to 'nv'.  This is the free nvidia driver.  It doesn't support 3D or many other features, but it should get you X.  For example:
```

Section "Device"
  Identifier  "nVidia"
  Driver      "nv"
  ...
EndSection

```

Once you have everything resolved, you can switch to the restricted driver.

Make sure the Identifier matches the Device value in Section "Screen".

Also, do you have the nvidia driver installed?  It's the **nvidia-glx-new** package.

Finally, have a look at the **nvidia-xconfig** man page.  nvidia-xconfig is a tool to help you setup nvidia for X.

Adding Driver "nv" didn't seem to change anything. Still get "Signal out of Range" when X starts.

As for nvidia-glx-new, that's the proprietary driver, right? I'm using a standard install of 8.04, so the nv driver should be installed by default, I guess?

---

### Post by zxscooby on 2008-08-09
Have you tried removing the other resolutions that are listed
leaving the 1024x768 so that is the only resolution it goes to?

you may have to manually list the refresh and sync rates.

[https://help.ubuntu.com/community/FixVideoResolutionHowto?highlight=%28xorg%5C.conf%29](https://help.ubuntu.com/community/FixVideoResolutionHowto?highlight=%28xorg%5C.conf%29)

---

### Post by evildonut on 2008-08-09
> **zxscooby said:**
> Have you tried removing the other resolutions that are listed
leaving the 1024x768 so that is the only resolution it goes to?

you may have to manually list the refresh and sync rates.

[https://help.ubuntu.com/community/FixVideoResolutionHowto?highlight=%28xorg%5C.conf%29](https://help.ubuntu.com/community/FixVideoResolutionHowto?highlight=%28xorg%5C.conf%29)

Forcing the resolution has no effect. Neither did listing refresh and sync rates. HOWEVER, I've found that if I make the xorg.conf file somehow invalid (by putting quotes around the HorizSync and VertRefresh values, for instance) X drops into "safe" or "low res" mode or whatever it's called (using the vesa driver I guess?). So I can get into X that way, although it will only display 800x600 or 640x480, so it's only a temporary solution.

I have been able to enable the proprietary nvidia driver and run nvidia-xconfig, but the problem remains.

I'm running Update Manager right now to install all the updates that have come out since 8.04 was released, maybe that will help (longshot).

---

### Post by evildonut on 2008-08-09
Yeah, installing all the system updates had no effect, as expected.

A tidbit: After I installed the nVidia driver, my monitor no longer says "input signal out of range", it just goes straight to sleep when X starts.

---

### Post by evildonut on 2008-08-10
Bump.

---

### Post by Dejavou42 on 2008-09-01
1. Just saw your post, I'm actually having a similar problem. Try this for me. on boot up press Escape Key when prompted to get to the boot menu. Select the recovery mode of the kernel that you are using. (Most likely the latest kernel if you don't know which one) Once it gets to the menu select the "repair x-server" option. (NOTE: This will probably erase all of your settings for beryl / compiz, but you will be able to get back to the GUI)
After repairing x-server (Verbose text will disappear and the menu will be the only thing on screen again) select the option to boot into normal mode or GUI mode (I can't remember what it says exactly). This should get you back into your GUI. 

2. Once you are back in your GUI, download and run ENVY from the synaptic package manager. It should install and configure the drivers for the Nvidia card, and you can once again enable 3D / Extra Visual Effects.

Let me know if you have any trouble with this.

---

### Post by evildonut on 2008-09-02
I've managed to solve my issue.

I forgot a rather important detail, it turns out. Other than my monitor, I also had my HDTV connected with VGA. Once I disconnected the TV and repaired my xorg.conf, my monitor was properly detected.

So apparently there's a problem with correctly detecting monitor settings when there's both a monitor and an HDTV (with different native resolutions) connected to the video card. I dunno if I should report it as a bug (or even how)...

---

### Post by Dejavou42 on 2008-09-05
you can report bugs in ubuntu [here]("http://https://launchpad.net/ubuntu/+bugs"), but I'm sure there is a workaround for this. Try this thread:[http://ubuntuforums.org/showthread.php?t=93622](http://ubuntuforums.org/showthread.php?t=93622).

---

### Post by rfrayer on 2008-09-11
here is what i did i changed the monitor and screen section after weaks of headaches over not being able to full screen game


Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1440x900"
	Horizsync	31.5-56.0
	Vertrefresh	56.0	-	65.0
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
  modeline  "1440x900@60" 106.47 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Modes		"1440x900@60"	"1280x800@60"	"1280x720@60"	"1280x768@60"	"800x600@60"	"800x600@56"
	EndSubSection
EndSection




Just change it to suit your monitors range and needs

---

