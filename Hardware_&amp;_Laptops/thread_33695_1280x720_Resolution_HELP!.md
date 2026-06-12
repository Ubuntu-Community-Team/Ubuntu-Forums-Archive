---
title: "1280x720 Resolution HELP!"
date: 2005-05-11
forum: Hardware &amp; Laptops
---

### Post by chicagoninja on 2005-05-11
I started using ubuntu for about 3 weeks now and i am defenetly loving it. i have competely switch over from windows. I mean i miss trillian thats about it everything else works great even have coutner strike running.. but one thing really really really bothers me. It's my resolution. I mean i am fine with it but i wish i could have 1280x720. I have a widescreen monitor and it does 1280x720 i mean its an lcd/tv a 27" Syntax Olevia LCD its for my livingroom. but still i can only run at 1280x960 1280x1024, 1280x768, but not 1280x720. Is there anyway i can do this. Thanks alot. Also i would like to say that alot of people have great "How To's" on this site helps me out alot. Hopefully something can be done about this. Thank you in advance

-chicago.ninja

---

### Post by poofyhairguy on 2005-05-11
[QUOTE=chicagoninja]I started using ubuntu for about 3 weeks now and i am defenetly loving it. i have competely switch over from windows. I mean i miss trillian thats about it everything else works great even have coutner strike running.. but one thing really really really bothers me. It's my resolution. I mean i am fine with it but i wish i could have 1280x720. I have a widescreen monitor and it does 1280x720 i mean its an lcd/tv a 27" Syntax Olevia LCD its for my livingroom. but still i can only run at 1280x960 1280x1024, 1280x768, but not 1280x720. Is there anyway i can do this. Thanks alot. Also i would like to say that alot of people have great "How To's" on this site helps me out alot. Hopefully something can be done about this. Thank you in advance

-chicago.ninja[/QUOTE]

You acn do this, but you need to roll up your sleeves. Open up the terminal from system tools. enter in this:

> sudo gedit /etc/X11/xorg.conf 

When the file comes up, find the "screen" section. This is what mine looks like:


> Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Monitor		"NEC LCD1712"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection 

On the line where it says "modes" (all of them), add in that new value: 1280x720 in the first part. Be sure to erase any modes that are higher. AS an example I did mine:

> Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Monitor		"NEC LCD1712"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x720" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x720" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x720" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x720" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x720" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x720" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection 

This will hopefully work. Good luck.

---

### Post by chicagoninja on 2005-05-13
Alright i have tried that buy when i do that it maxes out my resolution at 1024x768 but if i put "1280x720" alone with out the other resolutions my resolution goes and settles at 1280x1024. I dont under stand why 1280x720 wont show up in the resolution settings but every other one will... :(

**also here are the specs of the monitor

27" Syntax Olevia LCD
[http://www.syntaxgroups.com/products/27inch_spec.html](http://www.syntaxgroups.com/products/27inch_spec.html)

---

### Post by chicagoninja on 2005-05-21
Can anyone help me out? i would really like to use 1280x720 instead of (1280x1024 - 1280x960)

---

### Post by FreeEagle on 2005-05-21
[QUOTE=chicagoninja]Can anyone help me out? i would really like to use 1280x720 instead of (1280x1024 - 1280x960)[/QUOTE]


well i will help you , you have to just run this : and you will be okay ... I had this Problem before and i solved it  \\:D/ 

    Run this :   sudo dpkg-reconfigure xserver-xorg

and he will ask you about your Password. Enter the Password and follow all the instructions.

Then restart your PC and wish this will work. by the way when he will ask you about the Resolution just choose what you want , and leave other empty, i mean start with 800x600 and stop at 1280x720 and leave others empty.

after the restart try to select from the Gnome Panel System, then settings and the Screen REsolution and choose that one that you like to have . 

Sorry i have the German Version installed and therefore mybe you will find anothe Words in the Panel not like what i have written here, i tried to translate them , this is my best.

Good Luck


FreeEagle

---

### Post by chicagoninja on 2005-05-22
Thanks for the help but 1280x720 is not on that list  :(  only 1280x768 is the closest :( is there a way to force 1280x720?

---

### Post by FreeEagle on 2005-05-22
i think this is a Xorg Problem, or there is another way maybe to force the system to do it.


I will check an let you know ,,,,


You welcome


FreeEagle

---

### Post by microthorne on 2006-04-29
Hi,

Does anyone have a solution for this?  I am trying the ModeLines listed at the following web site, but not having any luck.  1024x768 is the best I can get, however before I rebuilt this PC (was Windows MCE,) it ran fine at 1280x720 (the native resolution of the LCD monitor.)  None of the hardware has changed.  Could this be an nvidia driver issue? Perhaps an xorg issue?

ModeLines:
[http://www.linuxis.us/linux/media/howto/linux-htpc/video_card_configuration.html](http://www.linuxis.us/linux/media/howto/linux-htpc/video_card_configuration.html)

Oops - didn't realize this thread was posted in the Hoary support forums... I am using Breezy.

Nevermind, I found a modeline that works.
TV Model: Panasonic PT60LC14
ModeLine: ModeLine "ATSC-720-60p" 74.25 1280 1320 1376 1650 720 722 728 750

HTHs someone else.

---

### Post by mistywindow on 2006-05-17
[QUOTE=poofyhairguy]You acn do this, but you need to roll up your sleeves. Open up the terminal from system tools. enter in this:............
When the file comes up, find the "screen" section. This is what mine looks like:...............
On the line where it says "modes" (all of them), add in that new value: 1280x720 in the first part.......[/QUOTE]
Poofyhairguy, you're a legend!
I'm a Linux user with 1 whole day's experience. The 2 biggest problems on my Asus Z92U Turion notebook were wireless connection and screen resolution. Wireless fixed. Now, thanks to your post, so is my screen res! Not only that, restoring the resolution to 1280 x 800 has fixed my fuzzy fonts.
I'm ecstatic. Bye-bye Windows. Office 2003 is going to auction.
Ubuntu is superb!

---

### Post by Konsolkongen on 2006-05-18
I've tried both methods. And 1280x720/1280x768 stil shows up as 1280x1024 with giant boarders.

I'm using a HDTV with a 1280 x 720 resolution.

Also i'm using a VGA kable to connect my pc to the monitor.

Any help at all, would be apriciated.

---

### Post by nolihc on 2006-06-09
I am using ubuntu on my hdtv with 1280x720 on a dvi cable. THe only thing i changed in the xorg.conf was 1280x720 and wipe out everything bigger(1024x768, etc). I'm using nvidia...

---

