---
title: "Toshiba Libretto 110ct"
date: 2006-05-29
forum: Hardware &amp; Laptops
---

### Post by Jawbreaker4Fs on 2006-05-29
Has anyone tried to install Ubuntu on the Toshiba Libretto 110ct? I've been trying all day and I'm pretty certain it's damn near impossible. If anyone's got it working let me know. The laptop has a very strange BIOS that will only boot from either the HDD or FDD, but can't find the PCMICA CD-Rom I have connected (I've tried Smart Boot Manager and Bootable CD Loader, neither of which work). There's no built in USB port or ethernet port, so attempting to boot via USB or doing a net install from a floppy are both out of the question. All I have to work with is basically a bootable floppy. Does anyone have any suggestions?

---

### Post by Jawbreaker4Fs on 2006-05-31
well.. does anyone else have this machine and has tried doing any kind of a linux install on it? I'm putting my attempts on hold for a few weeks until classes are out for summer, at which point I'll probably give it my all for a week or so. Would anyone benefit from a HOWTO if I can get it going?

---

### Post by irieken on 2006-06-03
I have managed to get Ubuntu 6.06 on the Libretto 110CT by doing the install on another machine and running "sudo dpkg-reconfigure xserver-xorg" once it boots on the Libretto.

Tell me if you have any luck on your end; I would like to get the desktop resizing figured out (xorg.conf's modes are all set to 800x480, but Desktop still gets rendered at 800x600).

---

### Post by va3uxb on 2006-10-17
Hi folks,

I just got the screen settings to work on my Libretto 100 CT. Well by 'just', I mean it took all bleeping day.  The 100CT is actually identical to the 110CT, the 100 had a slightly smaller hard drive and was (I think) just for the Canadian market.  Same form factor and same video settings.

I've edited my xorg.conf file and got rid of the default settings for Device, Monitor, and Screen.  Here are the settings I have used:
```
Section "Device"
	Identifier	"NM2160"
	Driver		"neomagic"
	BoardName	"Toshiba Libretto100"
	VideoRam	2048
	Clocks		25.2 28.3 35.26 40.0
	Option		"no_stretch"
	Option		"internDisp"
	Option		"override_validate_mode"
	BusID		"PCI:0:4:0"
EndSection

Section "Monitor"
	Identifier	"Lib100-LCD"
	VendorName	"Toshiba"
	ModelName	"Lib100"
	HorizSync	31.5-37.9
	VertRefresh	50-70
	Option		"dpms"
	Modeline "800x480" 35.26 800 856 1040 1056 480 480 486 488 +hsync
EndSection

Section "Screen"
	Identifier	"Lib100Screen"
	Device		"NM2160"
	Monitor		"Lib100-LCD"
	DefaultDepth	16
	Subsection	"Display"
		Depth	16
		Modes	"800x480"
		ViewPort	0 0
	EndSubection
EndSection

```

Then in the "ServerLayout" section, just change the Screen value to "Lib100Screen" and restart gdm.

It's now working at the native 800x480 screen size.

-Stephanie

p.s. to do the install, I put the hard drive in a different computer and ran the whole installation routine there, then moved the hard drive back into the libretto and did the reconfigure xserver-xorg then edited xorg.conf manually.

---

### Post by irieken on 2006-10-21
How is Ubuntu running on your machine? It runs slow as molasses on my Libretto110CT, and I believe that its because the libretto maxes out at 64MB of RAM.

Perhaps IceWM or Fluxbox would make things better (Xubuntu wasn't much faster than regular Ubuntu).

---

### Post by Nevermore on 2006-10-22
i suggest you all give a look at puppylinux.
64mb ram are too damn little for ubuntu to run..

---

### Post by va3uxb on 2006-10-24
Yes, it was very slow.  Still, for an 8-year old sub-mini-laptop, I guess it was doing the best it could.  As soon as I got X working, I removed gnome-desktop (and everything else installed with gnome) and installed xubuntu-desktop.  That sped things up a little bit.  It was still intolerably slow though.

I'm now experimenting with Damn Small Linux and find that is almost fast enough to be useful.  With a terminal window open and firefox running, it shows only about 20mb of RAM in use, and doesn't even go into the swap at all.  Actually I'm probably going to stick with Damn Small Linux on the Libretto, and keep Ubuntu on my server. 

-Stephanie

---

### Post by irieken on 2006-10-24
I have Fluxbuntu running on a Toshiba Libretto 110CT (233 with 64MB RAM) using a surrogate laptop.

It runs slowly, but at least it works (30 megs spilling into swap at bootup).

I tried DSL, but it got angry at me when I tried to use my VIA USB card. I may end up trying DSLn next weekend.

---

### Post by roggerdavid on 2007-05-11
But .... irieken is it very very very slow .... or is it aceptable slow?

pd: i have your same setup ..... 
pd2: where can i buy hd for this laptop? do you know?

---

### Post by irieken on 2007-05-16
It's slow enough that I wouldn't recommend it. I am probably going to try a Feisty server install in the near future, and add a light weight xserver.

DSL is fairly responsive, but doesn't have the power management features that I want. Xserver on DSL  doesn't seem to take advantage of video acceleration, so video performance is sluggish there.

As for buying a new HD, you can use any IDE laptop HD. The trick is that there are some little plastic spacers on the inside of the drive compartment that you need to remove to get the new drive in (the original drive is pretty thin). This requires a complete teardown of the machine, but there aren't that many parts, so it's a 30 minute job.

I have successfully installed a 100GB Seagate drive in my machine, and it works fine as long as boot partition is less than 8GB.

New Egg has a $30 40GB drive which would be fine for the Libretto: [http://www.newegg.com/Product/Product.aspx?Item=N82E16822146232](http://www.newegg.com/Product/Product.aspx?Item=N82E16822146232)

> **roggerdavid said:**
> But .... irieken is it very very very slow .... or is it aceptable slow?

pd: i have your same setup ..... 
pd2: where can i buy hd for this laptop? do you know?

---

### Post by Jawbreaker4Fs on 2007-05-16
So what's the ideal distro for this? Has anyone got one running at any kind of reasonable speed that would make it considered to be usable?

---

### Post by irieken on 2007-05-22
elive in 16bit video mode has been fairly tolerable.

---

### Post by roggerdavid on 2007-05-25
thank for all that information. i installed dsl and 98 2k and xp on a 30 gb hd. thanks rieken for the info.:)

---

### Post by roggerdavid on 2007-05-25
rieken .... which version of elive did you installed?

---

### Post by irieken on 2007-05-26
> **roggerdavid said:**
> rieken .... which version of elive did you installed?

0.6.9 Unstable. Was extremely slow before I changed the x color depth to 16 bit, but after that, it's quite usable.

On another note, I tried throwing Ubuntu Feisty on the machine today, and it halts with an error "Begin: waiting for root file system" once the kernel loads. Other people seem to have this problem, and it did not happen in Dapper. Must be something new in Feisty that breaks it, and it seems that all Librettos have the same problem with Feisty.

---

