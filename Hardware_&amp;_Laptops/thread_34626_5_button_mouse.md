---
title: "5 button mouse"
date: 2005-05-15
forum: Hardware &amp; Laptops
---

### Post by Oblivious Hazard on 2005-05-15
hello, my 5 button mouse isent working. the 4/5th button atcs as the 2/3 buttons. in firefox, and in STEAM... anyone have a way to fix this?

---

### Post by DaGGer on 2005-05-15
i have the same problem...what is the command to fix this..

---

### Post by crane on 2005-05-15
After a quick seach I found [this](http://ubuntuforums.org/showthread.php?t=28374) 

If that doesn't help be sure to [search](http://ubuntuforums.org/search.php?) 

I don't think it will be that difficult. If I remember correctly it's just a setting in your xorg.conf file

---

### Post by Maestro23 on 2005-05-15
[QUOTE=Oblivious Hazard]hello, my 5 button mouse isent working. the 4/5th button atcs as the 2/3 buttons. in firefox, and in STEAM... anyone have a way to fix this?[/QUOTE]

Did a quick forum search (5 button mouse config) and found this thread among some others. Don't have a 5-button mouse myself, but this might help ya or put you on the right track.

Link: [http://www.ubuntuforums.org/showthread.php?t=3828&highlight=button+mouse+config](http://www.ubuntuforums.org/showthread.php?t=3828&highlight=button+mouse+config)

---

### Post by Oblivious Hazard on 2005-05-15
I have a way to fix this issue...... 

type in: sudo gedit /etc/X11/xorg.conf 

and scroll down to the mouse and replace the last 3 lines with this:

	Option		"Protocol"		"ExplorerPS/2"
	Option          "Buttons"               "7"
	Option		"ZAxisMapping"		"4 5"

---

### Post by Vivica_Gsy on 2007-09-29
This all seemed to make sense to me, and i've been putting up with the same problem with my 5 button mouse for a while as well.
Having made the above changes to xorg.conf my forward/back side buttons no longer act as second left/right click buttons (respectively), but they still don't act as they do when i boot to Windows, as page forward and back within any of my web/file browsers.

Anybody else had this problem and know of a fix?
I'm obviously quite a novice Linux user, but always find fixes and work arounds on these forums pretty obvious to implement.

Thanks in advance.

---

### Post by six616 on 2008-03-21
I edited the /etc/X11/xorg.conf file. You must be root or have sudo rights to do this.

There is a stanza for the mouse, likely showing as a Emulate 2 Button or Emulate 3 Button mouse. Comment out this stanza by placing a # in front of each line.

Insert the following stanza:

Section "InputDevice"
       Identifier "Configured Mouse"
       Driver "mouse"
       Option "CorePointer"
      Option "Device" "/dev/input/mice"
      Option "Protocol" "ExplorerPS/2"
      Option "Buttons" "7"
      Option "ButtonMapping" "1 2 3 6 7"
      Option "ZAxisMapping" "4 5"
EndSection

Now make sure the section title matches the InputDevice name in the ServerLayout Section.

Next step, restart X. In other words, log out an in again.

As a side note, some mice will use a ZAxisMapping setting of "6 7". If your scroll wheel does not work, try changing that setting.

If you are questioning the Buttons "7" setting. It is correct. The scroll wheel actually is shown as a button to the Linux operating system.

---

