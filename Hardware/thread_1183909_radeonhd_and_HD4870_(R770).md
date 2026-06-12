---
title: "radeonhd and HD4870 (R770)"
date: 2009-06-10
forum: Hardware
---

### Post by rubenvb on 2009-06-10
Today I took the plunge as KDE4 (latest) is having a hard time with fglrx. In fact, when I think about it, GNOME has a problem with my fglrx also (slow unresponsive desktop for no apparent reason, GNOME is still quasi-usable, KDE4 not at all). But this is not the issue...

I added the Ubuntu launchpad radeonhd repository ([http://ppa.launchpad.net/tormodvolden/ppa/ubuntu](http://ppa.launchpad.net/tormodvolden/ppa/ubuntu) jaunty main) and installed the latest radeonhd.

For documentation purposes:
1. add git repository
2. uninstall all fglrx packages in Synaptic
3. install "xserver-xorg-video-radeonhd" version 1.2.5+gitsomething
4. run "sudo dpkg-reconfigure xserver-xorg"
5. reboot and cross fingers
6. log in and all is well

Now I want to enable the experimental 3D acceleration that has presumably been added in the last few weeks. I understand it might require some recompiling and I'm not afraid of that (if someone is willing to help :D)

To get started, this is my current xorg.conf file:
```

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Virtual	3360 1050
	EndSubSection
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"		"true"
EndSection

```

Is there anything I can add to it to enable/try 3D acceleration? I'd be happy to share my experiences once I get it working (hopefully without too many hiccups :s)

Thanks a lot!

PS: any idea when power saving (automatic downclocking of core and mem clocks) will be (experimentally) implemented?
PS2: I'm having a thought here: I have both radeon and radeonhd installed, so how do I know which is being used? I'm not sure if uninstalling one of them is a good idea...

---

