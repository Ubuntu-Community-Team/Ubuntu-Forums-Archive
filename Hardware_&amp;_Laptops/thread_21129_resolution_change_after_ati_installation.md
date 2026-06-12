---
title: "resolution change after ati installation?"
date: 2005-03-20
forum: Hardware &amp; Laptops
---

### Post by nahkapaavali on 2005-03-20
Hi all! 
This is my first post on these forums and im kinda new in all Ubuntu.

My guestion will be that after i installed ati drivers thru this guide: [http://www.ubuntulinux.org/wiki/BinaryDriverHowto](http://www.ubuntulinux.org/wiki/BinaryDriverHowto), i havent been able to change my resolution. When i try to change it from the menu (system->settings->reolution) it prompts that xserver doesnt support XrandR, so it cannot been switched when its running. 
Ive tried to change the reolution from the **/etc/X11/xorg.conf** -file, but i dont know how. ive ran fglrxconfig and changed the deffault resolution to 1024x768 24bit with no luck. It stays in 1280x960 which is bad coz then refresh range is only 60hz. 

Also after that procedure when i started playing Americas Army the mouse woudnt work so well. I mean it somehow "prevents" me to look left(or right) enough. It doesnt move all the way of the screen.
Points to that problem would be appretiated also  :D 

Im using hoary with 9100 radeon card and my mouse is logitech cordless. Basic rat with a ball. My monitor is Nokia 447Zi.

Thanks in advance!

**edit: I think this went to the wrong place...Admins can move this if it did**

---

### Post by MicroChris on 2005-03-20
For the xorg problem, run:

```
sudo dpkg-reconfigure xserver-xorg
```

It has auto detection on hardware and monitors. I had the same problem last night. I was at a really crappy res with a really crappy Hz, so it looked really weird and made me feel like I was gonna puke, lol.

Run that and follow the prompts and you should be good.

Best of luck,
Chris

---

### Post by nahkapaavali on 2005-03-21
[QUOTE=MicroChris]For the xorg problem, run:

```
sudo dpkg-reconfigure xserver-xorg
```

[/QUOTE]

Thanks for the reply but it didnt work for me  :-(  Still having that sick-making refresh rate..
I even rebooted after that code so is there any other way to change the resolution?

Thanks!

---

### Post by cdhotfire on 2005-03-21
try this
```
sudo /etc/init.d/gdm stop
```
and then do
```
sudo dpkg-reconfigure xserver-xorg
```
then
```
startx
```
if it doesnt work tell me.

edit: if you want 1024x768 do this
```
sudo gedit /etc/X11/xorg.conf
```
where it says
```
Section "Screen"
```
change the first one in each to 1024x768 instead of 1280x1024
like this
```

        SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

```

---

### Post by nahkapaavali on 2005-03-21
I changed first lines in xorg.conf file and that worked :D 

Thanks for your help!

---

### Post by cdhotfire on 2005-03-21
[QUOTE=nahkapaavali]I changed first lines in xorg.conf file and that worked :D 

Thanks for your help![/QUOTE]

no prob.:-D

---

### Post by npmLincs on 2007-04-09
I have the same problem.

I have added the 1280x1024 into the xorg file as above. However, I am still not able to see this option in the *System/Preferances/Screen Resolution* box.

Strangly, when I boot into ubuntu from the CD rom, the system defaults to 1280x1024?

Any clues?

---

