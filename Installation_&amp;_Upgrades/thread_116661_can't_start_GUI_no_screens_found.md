---
title: "can't start GUI: no screens found"
date: 2006-01-13
forum: Installation &amp; Upgrades
---

### Post by Bubba Ho-Tep on 2006-01-13
Hi,

I've just installed Ubuntu on an old box I blagged from work.

However the GUI doesn't load with the error messages:

Cirrus(0) Cannot read V_BIOS

Screen(s) found but none have a useable configuration

Fatal server error: no screen(s) found

The X server output read:

Screen "default screen"
Monitor "generic monitor"
device "Cirrus Logic GD 5480"


a search of this site for "no screen(s) found" yielded nothing (is it just me or does the advanced search suck?)

but other searches found [this](http://ubuntuforums.org/showthread.php?t=115515&highlight=screens+found) and a few other threads 

so I tried 
sudo dpkg-reconfigure xserver-xorg

answered the questions as best I could but no luck

this: #cat /var/log/Xorg.0.log |grep EE
produced 
Loading MIT-SCREEN-SAVER
Cirrus(0) Cannot read V_BIOS
Screen(s) found but none have a useable configuration

Other info: 
Monitor: Samsung Syncmaster 172x (which was detected by the "sudo dpkg-reconfigure xserver-xorg" run thru
Mouse: HP optical mouse
Keyboard: HP US English
and is connected thru a KVM (a 2 port ATEN)
I don't know the brand of video card and can't see any brands/names on it. Is there any commands I can issue to query the video card? It is an AGP card. The motherboard has onboard video as well.

If anyone has any ideas... would be appreciated.

Cheers
BHT

PS The exact same problem has occured on a box i'm trying to set up at work - different video card, monitor etc altho it does go thru an ATEN KVM. I don't thnk its the KVM however as i've successfully installed Ubuntu on 2 computers routed thru the ATEN KVMs. This problem also happened with Kubuntu and mandrake installs.

---

### Post by Pixel on 2006-01-13
[QUOTE=Bubba Ho-Tep]Hi,

I've just installed Ubuntu on an old box I blagged from work.

However the GUI doesn't load with the error messages:

Cirrus(0) Cannot read V_BIOS

Screen(s) found but none have a useable configuration

Fatal server error: no screen(s) found

The X server output read:

Screen "default screen"
Monitor "generic monitor"
device "Cirrus Logic GD 5480"


a search of this site for "no screen(s) found" yielded nothing (is it just me or does the advanced search suck?)

but other searches found [this](http://ubuntuforums.org/showthread.php?t=115515&highlight=screens+found) and a few other threads 

so I tried 
sudo dpkg-reconfigure xserver-xorg

answered the questions as best I could but no luck

this: #cat /var/log/Xorg.0.log |grep EE
produced 
Loading MIT-SCREEN-SAVER
Cirrus(0) Cannot read V_BIOS
Screen(s) found but none have a useable configuration

Other info: 
Monitor: Samsung Syncmaster 172x (which was detected by the "sudo dpkg-reconfigure xserver-xorg" run thru
Mouse: HP optical mouse
Keyboard: HP US English
and is connected thru a KVM (a 2 port ATEN)
I don't know the brand of video card and can't see any brands/names on it. Is there any commands I can issue to query the video card? It is an AGP card. The motherboard has onboard video as well.

If anyone has any ideas... would be appreciated.

Cheers
BHT

PS The exact same problem has occured on a box i'm trying to set up at work - different video card, monitor etc altho it does go thru an ATEN KVM. I don't thnk its the KVM however as i've successfully installed Ubuntu on 2 computers routed thru the ATEN KVMs. This problem also happened with Kubuntu and mandrake installs.[/QUOTE]

Post the output of:
```
cat /etc/X11/xorg.conf
```

---

### Post by Bubba Ho-Tep on 2006-01-13
The ouput more than fills my screen  and i can't figure out how to scroll thru it.

Plus i don't have the Linux box connected to the net and have no way to cut and paste to my Win box 

is there some way to output the text in a nicer format? 

Thanks for the quick reply!

BHT

-----
EDIT

Scrub the above, played about with cat and using the -b switch (number non-blank lines) I get:

-----------------------
SubSection "Display"
	Depth 	16
	modes 	"1280x1024" "1024x768" "832x624"
		"800x600" "720x400" "640x480"

SubSection "Display"
	Depth 	24
	modes 	"1280x1024" "1024x768" "832x624"
		"800x600" "720x400" "640x480"


Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"	
	Input Device	"Generic Keyboard"
	Input Device	"Configured Mouse"

Section "DRI"
	Mode 0666 

------------------------------
I hope/think that is all the output - as i said i can't seem to scroll thru the text

---

### Post by Bubba Ho-Tep on 2006-01-15
Anyone?

---

