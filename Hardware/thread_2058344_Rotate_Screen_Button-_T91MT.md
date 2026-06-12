---
title: "Rotate Screen Button- T91MT"
date: 2012-09-15
forum: Hardware
---

### Post by mrmagoo1077 on 2012-09-15
Linux begginer still, but have been self teaching myself through guides posted by other users.  Ive fixed almost all the bugs with my new asus T91MT, but I would like to get the rotate screen button working.  The best guide I could find was:
( [http://ubuntuforums.org/showthread.php?t=1595220](http://ubuntuforums.org/showthread.php?t=1595220) )
[COLOR=Red]**Rotate Button**

Warning: I tried this, and my wireless stopped working (It did make the  rotate button work). However it seems to work for the folks at [/COLOR] [COLOR=Red][=t101]eeeuser.com]("http://wiki.eeeuser.com/ubuntu_9.10_on_the_t91_t91mt?s["), so I will post this in hope it works for those daring enough to try.

Create the file [/COLOR] [COLOR=Red]**/etc/acpi/events/asus-rotate-t91** and add to it:
[/COLOR]  	[COLOR=Red]Code:[/COLOR]
 	[COLOR=Red]event=hotkey (ATKD|HOTK) 0000007b action=/etc/acpi/rotatescreen.sh[/COLOR] 
[COLOR=Red]Then edit **/etc/defaults/grub** and add **acpi_osi=Linux**  to the line starting with GRUB_CMDLINE_LINUX_DEFAULT (make sure you  paste it inside the quotes). This is the part that caused my wireless to  stop working. If you are affected in the same way, simply undo this  line.

Finally edit the file [/COLOR] [COLOR=Red]**/etc/acpi/rotatescreen.sh** and add to the end:
[/COLOR]  	[COLOR=Red]Code:[/COLOR]
 	[COLOR=Red]INPUTDEV="9" ROTATION=`cat /var/lib/acpi-support/screen-rotation` case $ROTATION in     normal) xinput set-int-prop $INPUTDEV "Evdev Axes Swap" 8 0        xinput set-int-prop $INPUTDEV "Evdev Axis Inversion" 8 0 0;;     left) xinput set-int-prop $INPUTDEV "Evdev Axes Swap" 8 1        xinput set-int-prop $INPUTDEV "Evdev Axis Inversion" 8 1 0;;     right) xinput set-int-prop $INPUTDEV "Evdev Axes Swap" 8 1        xinput set-int-prop $INPUTDEV "Evdev Axis Inversion" 8 0 1;;     inverted) xinput set-int-prop $INPUTDEV "Evdev Axes Swap" 8 0        xinput set-int-prop $INPUTDEV "Evdev Axis Inversion" 8 1 1;; esac[/COLOR] 
But the guide was written for ubuntu 10.10 and it appears the the /etc/acpi folder no longer exists.  Im sure it's a simple relocation, but I have no idea where I would create this file in lubuntu 12.04.  Any help would be GREATLY appreciated!  Also does anyone know why that would make the OP of the guides wireless not work?

---

