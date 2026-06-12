---
title: "Compiz troubles"
date: 2008-11-04
forum: General Help
---

### Post by brad123 on 2008-11-04
Hi,

I recently upgraded my ubuntu from 8.04 to 8.10.  Immediately I noticed that my compiz was not working, so I ran command prompt "compiz --replace" and this is what came up Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 

I can't enable any desktop effects.  I think it has something to do with either video driver or xorg configurations..  I'm still extremely new to ubuntu, so it's probably something easy and silly but any help would be greatly appreciated!

---

### Post by thumper_e on 2008-11-04
HI there,

Is the proprietry driver enabled from System --> Administration --> Hardware Drivers. If not I suggest enabling it and seeing if that helps, otherwise drop a note back with a few more details, your graphics card, xorg.conf setup and the output of ```
fglrxinfo 
```

---

### Post by brad123 on 2008-11-04
I ran that code in the terminal, I don't know if thats what you wanted, but this is what came up brad@brad-laptop:~$ fglrxinfo
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  10
  Current serial number in output stream:  10

I went to the system>admin>hardware drivers and it is enabled, but the only driver it is showing is for my wireless.

My video card is Intel Integrated Video 950

xorg.conf = 

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Virtual	2048 776
	EndSubSection
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection


Thanks for the help, if you need any more info let me know

---

### Post by thumper_e on 2008-11-04
What graphics card do you have?

If its an ATI card you could try running

```
 sudo apt-get install xorg-driver-fglrx 
```

also check the ati website to see if there are any new drivers for linux and your graphics card. (There is a link from the driver download page on how to install the driver)

I hope this helps somewhat.

---

### Post by thumper_e on 2008-11-04
What graphics card do you have?

If its an ATI card you could try running

```
 sudo apt-get install xorg-driver-fglrx 
```

also check the ati website to see if there are any new drivers for linux and your graphics card. (There is a link from the driver download page on how to install the driver)

I hope this helps somewhat.

---

### Post by brad123 on 2008-11-04
I ran sudo apt-get install xorg-driver-fglrx and I already had the latest version.. I went to the ATI webpage but didn't knwo what driver I needed..

---

### Post by thumper_e on 2008-11-04
Sorry I have just re-read your post and realised that I should have paid attention to it as you have said what I wanted to know.

I believe there is a linux intel driver try here :

[url][URL="http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=2159&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go!"]

---

### Post by brad123 on 2008-11-04
beautiful.. I was just at that websit but couldn't find the driver.  thanks a lot, its downloading right now.  how do I install it once it's done?

---

### Post by thumper_e on 2008-11-04
That my freind I have no Idea! 

However befor you do try to install it make sure 

```
 sudo dpkg --status xserver-xorg-video-intel 
```

is installed. If it isn't run

```
 sudo apt-get install xserver-xorg-video-intel 
```

If it is try running ;

```

echo 'SKIP_CHECKS="yes"' >> ~/.config/compiz/compiz-manager

```

and restarting your desktop alt-ctrl-bkspce

see if it works.

If not have a quick read of the installer documents

Good luck!

---

### Post by brad123 on 2008-11-04
alright, thanks again for all your help.  If this doesn't work then I'll do some more research.. I've been battling with this for a few days now

---

