---
title: "Switch view modes (twinview) without leaving/reconfiguring X?"
date: 2005-08-24
forum: Hardware &amp; Laptops
---

### Post by vitorsouza on 2005-08-24
Hi there,

I have a KUbuntu installed on an Acer TravelMate 250 laptop with a Intel Corporation 82852/855GM Integrated Graphics Device (i810 driver). I managed to get TwinView working with the following configuration:

```
Section "Device"
 Identifier "Intel Corporation 82852/855GM Integrated Graphics Device"
 Driver  "i810"
 BusID  "PCI:0:2:0"
 Option  "MonitorLayout"  "LFP,CRT+LFP"
EndSection
``` 

As I understand it, the MonitorLayout value is in the format <pipeA>,<pipeB> and X starts on pipeB by default, so putting CRT+LFP on <pipeB> makes it display the screen on both the LCD and an external CRT or projector.

While that's already fine, what I would really like to do is be able to push Fn+F5 and alternate between view modes: LCD-only, CRT-only and TwinView. The laptop comes with a software that does that on Windows, and Ubuntu shouldn't lag behind, should it?  ;-) 

Fn+F5 triggers an ACPI event and I already managed to map it to /etc/acpi/video.sh, but I don't know which command I could use to switch from <pipeB> to <pipeA>.

Better yet, I've seen some posts describind xorg.conf files that declare various Layout sections, one for each view mode (LCD, CRT, LCD+CRT). I know you can shut down X and start over with -layout <LayoutName> option, but I wish I could do it from inside X, without having to restart it. Is it possible?

I thank in advance any pointers.

Vítor Souza

---

### Post by s_p_a_r_k_y on 2005-08-24
hi there...no Linux should not lag behind windows...ever... However I know your pain. I currently have 2 Xorg config files, and just copy the one I want to use over /etc/X11/xorg.conf

one is setup to have 2 monitors with different screens so I have 2 desktops (more space = true bliss)

and one is just 1 monitor LCD.

I can't get X to scan for my setup and choose one setup on the fly so I have to drop myself to a console and do it manually...not the hugest pain.

---

### Post by locutus42 on 2005-08-25
[QUOTE=s_p_a_r_k_y]hi there...no Linux should not lag behind windows...ever... However I know your pain. I currently have 2 Xorg config files, and just copy the one I want to use over /etc/X11/xorg.conf

one is setup to have 2 monitors with different screens so I have 2 desktops (more space = true bliss)

and one is just 1 monitor LCD.

I can't get X to scan for my setup and choose one setup on the fly so I have to drop myself to a console and do it manually...not the hugest pain.[/QUOTE]

Another way would be to write a couple of scripts to copy xorg.conf1 and xorg.conf2 to xorg.conf and then create desktop objects which run the scripts. Then all you have to do is logout and enter Ctl-Alt-Bsp at the login manager to restart with the new xorg.conf file.

#!/bin/bash

if [ -f $1 ]; then
  ksudo cp -a /etc/X11/$1  /etc/X11/xorg.conf
  if [ "$?" -gt "0" ]; then
     kdialog --error "ERROR: copy of /etc/X11/$1 to /etc/X11/xorg.conf!"
  fi
else
  kdialog  --error "ERROR: /etc/X11/$1 does not exist!"
fi

or something like that... Then create two desktop objects to call the script and pass it the name of the particular custom xorg.conf file (  xorg.conf1 or xorg.conf2 maybe ).

if someone is good with awk and sed then the script could actually just change the particular line in the original xorg.conf to switch/enable the feature.

---

### Post by vitorsouza on 2005-08-25
Yeah, there are many possible solutions if you consider leaving and restarting X. But if there is no way to do it without restarting X, I'll probably keep my current solution (TwinView all the time) and forget about Fn+F5...

Maybe when I get more time I'll dig into X's documentation to find some kind of API that might help me. Thanks a lot for your replies!

Vítor Souza

---

### Post by locutus42 on 2005-08-25
[QUOTE=vitorsouza]Yeah, there are many possible solutions if you consider leaving and restarting X. But if there is no way to do it without restarting X, I'll probably keep my current solution (TwinView all the time) and forget about Fn+F5...

Maybe when I get more time I'll dig into X's documentation to find some kind of API that might help me. Thanks a lot for your replies!

Vítor Souza[/QUOTE]

come to think of it, this is probably a question for the xorg/xfree86 lists and has probably been asked already. Please let us know what you find. Thanx.

---

### Post by kampret77 on 2006-02-25
greetings

I have problem to set twinview in my asus m2n notebook.

currently i just successed to set clone setting, but i want extended view, two monitor show one desktop (so that the view is larger).

Sorry put the question here, i assume that someone has already been successed to set the xorg.conf setting.

this is my piece of current setting

```


Section "Device"
	Identifier	"Intel 8285 gm"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Option		"TwinView" 		    "true"
	Option		"TwinViewOrientation" 	"RightOf"
	Option		"metamodes"		  "1024x768"
	Option		"MonitorLayout"		  "DFP,CRT"
	Option		"Clone"			      "false"
	#VideoRam	8
	#Option		"UseFBDev"		"true"
EndSection


```

many example to set twin setting but all of them use nvidia and ati vga card.

i have use already the special driver from intel, but never been successed to set the twinview.

thanks in advance for any help

---

### Post by motin on 2008-01-26
> **vitorsouza said:**
> I've seen some posts describind xorg.conf files that declare various Layout sections, one for each view mode (LCD, CRT, LCD+CRT). I know you can shut down X and start over with -layout <LayoutName> option, but I wish I could do it from inside X, without having to restart it. Is it possible?

Certainly! And I just wrote a Howto and a bash-zenity application for this: [http://ubuntuforums.org/showthread.php?p=4211618](http://ubuntuforums.org/showthread.php?p=4211618)

---

### Post by derrick81787 on 2008-01-28
> **motin said:**
> Certainly! And I just wrote a Howto and a bash-zenity application for this: [http://ubuntuforums.org/showthread.php?p=4211618](http://ubuntuforums.org/showthread.php?p=4211618)

If that doesn't work, hopefully it does, I know that this is possible using xRandR.  I wrote a how-to about this here [http://ubuntuisms.com/main/?p=38](http://ubuntuisms.com/main/?p=38) .  Regardless of how you do it, I know that what you are trying to do is possible.  Hopeully one of these methods will work.  Let me know if you have any problems.

- Derrick

---

### Post by motin on 2008-01-29
> **derrick81787 said:**
> If that doesn't work, hopefully it does, I know that this is possible using xRandR.  I wrote a how-to about this here [http://ubuntuisms.com/main/?p=38](http://ubuntuisms.com/main/?p=38) .  Regardless of how you do it, I know that what you are trying to do is possible.  Hopefully one of these methods will work.  Let me know if you have any problems.

- Derrick

I just attached an All purpose RandR based configuration (along with other static configurations) to the [earlier mentioned post]("ttp://ubuntuforums.org/showthread.php?p=4211618"). Try them out risk free with the switchxconf tool. 

Cheers!

---

