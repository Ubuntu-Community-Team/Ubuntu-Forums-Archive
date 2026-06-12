---
title: "Getting Pen functions to work in Toshiba Portege m400"
date: 2008-05-12
forum: Hardware
---

### Post by nbotticelli on 2008-05-12
Hello All,

I've been looking through the forums and other sites for the past few days to try and figure out a way to get my tablet functions to work on my Toshiba Tablet Portege M400 S5032.

I've only been using Edubuntu so far for a week and I am quite new to Linux in general. I've used different flavors of Linux for short bursts of time though through out the past eight years but don't know much at all about navigating through command line stuff.

So far everything (except probably bluetooth but I don't care) pretty much runs flawlessly on this machine and I've got it set up as a dual boot Vista/Edubuntu machine and have pretty much switched permanently to using Edubuntu for the past week and am able to administer our win2003 server from it no problem.


The only real bother though is not being able to use the tablet functions of this machine and that's been a huge thing for me as I use the tablet functions constantly through out the day as I work in a school (elementary) and it's very handy being able to do paperless grading etc.

I've searched through the forums and on google quite a bit and have found some info about getting the pen to work but so far nothing has worked for me. Seems all the info is outdated....

I did find this thread [http://ubuntuforums.org/showthread.php?t=184542](http://ubuntuforums.org/showthread.php?t=184542)
and it said to have these programs installed:
wacom-kernel-source
wacom-tools
xserver-xorg-input-wacom
setserial

I've got everything except the wacom-kernal-source one. When I look for it in Synaptic Package Manager it doesn't even show up in the repositories.

Is there a new way to do this with the latest version of Edubuntu 8.04?

My M400 has a Intel Dual Core 1.6 GHz cpu w/ 1GB ram and Intel 950 GMA for graphics if that helps any.

Any help is greatly appreciated!

-Nicco

---

### Post by nbotticelli on 2008-05-12
So far nothing eh? Have things really changed that much since the different releases of Ubuntu? Seems like all the tutorials I've seen are for versions before 8.04 and nothing I try seems to go anywhere.

-Nicco

---

### Post by Drikus on 2008-05-17
got a M400 aswell and should work out of the box after uncommenting the following lines in xorg.conf. 

Section "InputDevice"
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

---

### Post by nbotticelli on 2008-05-19
What does "uncommenting" mean?

I found this site [http://www.control-d.com/?page_id=30](http://www.control-d.com/?page_id=30) and the directions there have really helped me so far......I've got pen functions and the finger print read to work.

Still not right click with the pen and it doesn't come back up after resuming from suspend. I have to restart the machine completely for it to work again.

---

### Post by dukeempire on 2012-10-02
:guitar:my toshiba portege is still not working

---

### Post by Favux on 2012-10-02
Hi dukeempire,

Welcome to Ubuntu forums!


What's not working?  The pen?  If so please post your Ubuntu release e.g. Precise (12.04).  Also post the outputs of the following commands in a terminal:
```
xinput list

and

xsetwacom list
```

By the way posting on a thread this old, or really any thread with no posts for over a year, is considered "necromancy".  So it would be better if you started a new thread on your Protege issue.  :)

P.S.:  And by the way is it a M400 too?

---

