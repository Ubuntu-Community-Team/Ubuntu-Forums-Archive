---
title: "Continuing Mouse Woes"
date: 2005-12-05
forum: General Help
---

### Post by veelivar on 2005-12-05
I'm afraid I already posted about this before in the Hoary forums when I was still using Hoary.  

([http://http://www.ubuntuforums.org/showthread.php?t=93762]("http://www.ubuntuforums.org/showthread.php?t=93762"))  

I'm sorry for cross posting but I'm still having similar problems with the mouse in Breezy, and posts get lost so quickly round here.

I managed to get the keyboard working fine by enabling usb keybaoed support in the bios.

Unfortunatly I'm still having the same problem with my mouse and have to keep plulling  in my rubbish old one when I use linux (which I'm trying to do more often than not).

Waht i don't understand is that they are both usb mice.  The new one occaisionally works more ofthen doesn't, the old one I can just plug in an go.

The new mouse seemed to work fine when I first installed breezy.  I was only after I installed the fglrx drivers that it stopped working.

I've tried reconfiguring the xorg.conf file with 
```
sudo dpkg-reconfigure xserver-xorg
``` 
but I don't really know what the mouse settings do.

I've compared the mouse section of the original xorg.conf file with the new fiel and they seem to be the same:
```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection
``` 

The only difference seems to be thje installation of the 3d drivers.  Even then it's just a amouse surly a mouse should work like a mouse? or default to a basic setting?

I'm afraid that I am really lost here and need some help.

Cheers,
Dan.

---

### Post by veelivar on 2005-12-07
Sorry to bump but things move so fast around here and it's lost already.

I really want to get ubuntu set up and wroking so I can phase windows out. 

Any ideas I can try? please?

Dan.

---

### Post by veelivar on 2005-12-12
anyone? please.

---

### Post by akiro.yamamoto on 2005-12-12
I'm not 100% on this but you can try :
CODE:
dexconf

to auto configure again your xorg.conf file....

---

### Post by akiro.yamamoto on 2005-12-12
You may find this of help.....
[http://ubuntuforums.org/showthread.php?t=65471&highlight=usb+mouse](http://ubuntuforums.org/showthread.php?t=65471&highlight=usb+mouse)
The first section deals with setting up the usb device.
Hope that helps...

---

### Post by veelivar on 2005-12-12
Thanks very much I'll have a look as soon as I can.

I'm in the process of moving at the moment though so it might be a few days yet.   

The second post looke very useful thanks!  I thought I'd searched the forums for stuff like this already.  Must have just missed it. 

Dan.

---

### Post by akiro.yamamoto on 2005-12-12
No Probs...
Post back with any progress...
Regards

---

