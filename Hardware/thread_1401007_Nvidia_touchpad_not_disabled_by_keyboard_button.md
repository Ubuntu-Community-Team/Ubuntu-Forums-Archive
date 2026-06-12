---
title: "Nvidia touchpad not disabled by keyboard button"
date: 2010-02-07
forum: Hardware
---

### Post by jcobban on 2010-02-07
I am running 9.10 (Karmic) on a Compaq Presario CQ60 laptop with the -185 driver installed.  This addresses most issues, but I find that the touchpad enable/disable button on the keyboard is ignored.  This causes problems because the touchpad lies underneath normal hand movement for typing.  If I (like most people) am not careful to keep my wrist elevated while typing, occasionally my hand will rub against the touchpad, generating unexpected mouse moves, scrolling, and button clicks.

This appears to be part of a long term problem with these touchpads.  I see dozens of problem reports in Launchpad, for example.  Some of these discuss changes to Xorg.conf to disable the touchpad, but I do not want to completely disable the touchpad, because it is not always convenient to use a USB mouse when away from home base.  I do not see an option to disable the touchpad through System/Preferences/Mouse.  Some of the threads discuss a gsynaptics feature, but I see nothing in any of the manufacturer's reference manuals about the manufacturer of the touch pad, and lshw is not informative.

I just want the touchpad disable button to disable the touchpad.

---

### Post by jjjjeremy on 2010-02-22
Have you found a solution? I have the same problem with the same laptop.

Also, do your speakers mute when you plug in headphones? Mine don't, and other people with the CQ60 are having the same problem, but I haven't found a solution yet.

---

### Post by pi/roman on 2010-02-22
You can use a script from my guide [[COLOR=Blue]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1401645") for toggling the touchpad.  First make an empty file on your desktop and place this in it.
[PHP]# toggle synaptic touchpad on/off
SYNSTATE=$(xinput list-props "SynPS/2 Synaptics TouchPad" | grep Enabled | grep -Eo '.$')
if [ $SYNSTATE = 0 ]; then xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Device Enabled" 8 1
else xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Device Enabled" 8 0; fi  [/PHP]

Then make it executable:
sudo chmod 775 ~/Desktop/syntoggle-file

Then place it in your /usr/bin/:
sudo mv ~/Desktop/syntoggle-file /usr/bin/

Then you can run it by pressing alt/f2 and typing the name of your syntoggle-file or going to keyboard shortcuts:
gnome-keybinding-properties

then create a new shortcut using the name of your syntoggle-file and assign your touchpad disable key to it.

If "SynPS/2 Synaptics TouchPad" is not the name of your touchpad then use "xinput list --short" and check what the name is.

---

