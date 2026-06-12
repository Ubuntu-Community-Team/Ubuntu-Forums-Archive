---
title: "Dell 700m screen resolution..please help me"
date: 2006-01-28
forum: Hardware &amp; Laptops
---

### Post by shuttleworthwannabe on 2006-01-28
Hi I am totally new to Ubuntu/Linux

I am trying to follow these instructions: [http://www.ubuntuforums.org/showthread.php?t=24923&highlight=855resolution](http://www.ubuntuforums.org/showthread.php?t=24923&highlight=855resolution)

but getting stuck.
1.  I did this

cd /etc/X11
sudo gedit xorg.conf

this is in my file under display:

Section "Device"
	Identifier	"Intel Corporation 82852/855GM Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Modeline	"1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82852/855GM Integrated Graphics Device"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
	EndSubSection
EndSection


So ut looks like it is beibg recognized by the X.org, right?


2. I have downloaded the 855resolution and extrated it into my home folder (folder is called 855resolution)
3. I have installed gcc using synapticPM


but when I do this

$ cd /home/linuser/855resolution

then do $ make

I get this error:
bash: make: command not found

so what am I doing wrong?

I want this working desparately.. I appreciate your help
swb

---

### Post by x3non on 2006-01-28
"sudo apt-get install build-essential" should solve your problem.

Bye!

---

### Post by shuttleworthwannabe on 2006-01-28
Thanks, I did that and sorta worked, but got stuck further down the line. So her is what I did:

1. $sudo apt-get install 855resolution

it installed and prompted me to edit /etc/default/855resolution

so I did this:

$sudo gedit /etc/default/855resolution

the file popped up and I filled in the required resolutions (in y case I chode mode=5a
V= 1280
H= 800

saved and rebooted.

It sort off picks up the resolution at the login screen, but loses it when GNOME loads. So I went to screen resolution under ssytem>Preferences>Screen resolution

and selected 1280x800, and promted me to set this (i chose ok).

My question will I have to select res everytime I logon???

Many thanks to all that have put together a great helpful site!

swb

---

### Post by x3non on 2006-01-29
could you please post your /etc/X11/xorg.conf file?

---

