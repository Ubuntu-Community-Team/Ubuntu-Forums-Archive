---
title: "Dell E1505 Screen Resolution Help"
date: 2006-06-26
forum: Hardware &amp; Laptops
---

### Post by hedonistic.heathen on 2006-06-26
Under System > Prefs > Screen Resolution I only have the option to set my resolution as high as 1024 X 768.  I have a 15.5 in widescreen monitor that I have set to ~1200 x ~800 (don't remember exactly what it is) in Windows and everything runs great.

I tried to run "sudo dpkg-reconfigure xserver-xorg" and selected some of the 12XX x 8XX settings and restarted, but they still weren't available as options under the gnome screen resolution "manager".

I also ran "sudo gedit /etc/X11/xorg.conf" and manually changed all of the resolutions to 1280 x 800 (and a bunch of other resolutions as well) but still, the gnome screen res manager only gives me the option of 1024 x 768.

Here's this as well:

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24




Any ideas?

---

### Post by anewvegetable on 2006-06-28
Having the exact same problem, on the exact same hardware, as the OP.

Any help would be welcome.

To the OP: What chipset does the E1505 use? I looked on Dell's website and other sources and could not find the answer. Thanks.

---

### Post by Protazoid on 2006-06-28
Did you guys try running the sudo 'dpkg-reconfigure xserver-xorg' in a virtual terminal (ctrl+alt+f1) or using a terminal in gnome?

---

### Post by hedonistic.heathen on 2006-06-28
I tried it using both the virtual terminal and the terminal in gnome and still no luck...

I can't get anything higher than 1024x768 as an option in the gnome default screen resolution app...its as if it isn't communicating with the xorg file/app (I'm not up to speed on the proper jargon yet).

---

### Post by Jeroen Vernooij on 2006-06-29
You need to install 915resolution. It can be installed via Synaptic Package manager if you have all repositories enabled.

---

### Post by xrchris on 2006-06-29
You need to install the 915resolution package from the universe repository. 

The 915resolution wiki is here [https://help.ubuntu.com/community/i915Driver](https://help.ubuntu.com/community/i915Driver)

---

### Post by hedonistic.heathen on 2006-06-29
Thanks much guys, that did the trick...

Now if I could only get my wireless connection up and running

---

