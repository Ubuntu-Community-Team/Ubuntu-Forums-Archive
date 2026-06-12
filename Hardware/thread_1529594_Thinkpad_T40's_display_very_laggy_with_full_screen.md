---
title: "Thinkpad T40's display very laggy with full screen apps"
date: 2010-07-12
forum: Hardware
---

### Post by fiddler616 on 2010-07-12
Hello,

I just installed Crunchbang (exact same thing as Jaunty but with Openbox and no Gnome) on my Thinkpad T40. The somewhat-wacky native resolution of 1400x1050 was supported out of the box, but it can be very laggy with full-screen apps. If I switch to gedit, it takes a long time for the icons/menus to get drawn. If I scroll in gedit, Chrome, or the terminal it's super-laggy. Right now I've shrunk Chrome to take up less than half of my screen--and it scrolls smoothly when I do that.

Here's some information:

```
$ lspci | grep Radeon
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] (rev 02)

```

```
$ Xorg -version

X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-25-server i686 Ubuntu
Current Operating System: Linux thinkpad-t40 2.6.28-19-generic #61-Ubuntu SMP Wed May 26 23:35:15 UTC 2010 i686
Build Date: 06 May 2010  09:36:28PM
xorg-server 2:1.6.0-0ubuntu14.2 (buildd@) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.

```


If you want anything else, I can provide it.

Google suggested that I add the following to my xorg.conf:

```
Section "Device"
        Identifier      "ATI Radeon"
        Driver          "radeon"
        Option "DynamicClocks" "on"
        Option "AGPMode" "4"
        Option "RenderAccel" "on"
        Option "EnablePageFlip" "on"
        Option "BIOSHotkeys" "on"
        BusID           "PCI:1:0:0"
EndSection
```

But as far as I can tell that hasn't done anything.

What should I do?

Thanks in advance!

---

### Post by fiddler616 on 2010-07-12
Solved. I updated X using [this]("http://launchpad.net/~ubuntu-x-swat/+archive/x-updates") repository.

Then I ran

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Then I added this to xorg.conf under section "Screen":

```
Subsection "Display"
		Depth	24
		Modes	"1440x1050"
		Virtual 1440 1050
	EndSubSection
```

and put this under "Device":
```
	Option	"AccelMethod" "XAA"
	Option	"XAANoOffscreenPixmaps" "true"
```

---

