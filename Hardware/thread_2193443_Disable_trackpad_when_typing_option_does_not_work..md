---
title: "Disable trackpad when typing option does not work."
date: 2013-12-12
forum: Hardware
---

### Post by mattg4542 on 2013-12-12
I don't understand why this is such a hard issue to solve. 

I have a ThinkPad X1 Carbon, which has an over sized trackpad. It is nearly impossible to miss the trackpad when typing and it is constantly selecting things without me wanting it to and causing me to type over things.  

I have tried more than one thing to attempt to solve this. I tried the "[COLOR=#333333][FONT=UbuntuRegular]pointing devices" package in the software center with pal detection, shortcuts to disable the trackpad (which is just a pain and I shouldn't have to do), xinput in terminal and a few other commands, and even a KDE package typed synaptiks.  Synaptiks worked well, but upon wake from sleep my trackpad would be TOTALLY disabled and it would require a reboot in order to correct the trackpad, no matter what I did.

Why is this SO hard? Seriously.

Any help is appreciated. [/FONT][/COLOR]

---

### Post by PaulBx on 2013-12-14
I had the same issue. I made this file in my Desktop directory (/home/paul/Desktop)

[Desktop Entry]
Encoding=UTF-8
Type=Application
Name=Toggle the touchpad
Name[en_US]=Toggle the touchpad
Exec=/home/paul/touch_toggle.sh
Comment[en_US]=
Terminal=false


This is the script touch_toggle.sh:
-----------------------------------
#
# tp_toggle
#
# Toggle the touchpad on/off.


# Get the id number of the touchpad.
tp_id=`xinput list | grep -i touchpad | awk '{ print $6 }' | sed 's/id=//'`


# Find out whether the touchpad is enabled or not.
tp_enabled=`xinput list-props $tp_id | grep Device\ Enabled | awk '{ print $4 }'`


if [ $tp_enabled = 0 ]
then
  # The touchpad is currently disabled, so turn it on.
  xinput set-prop $tp_id "Device Enabled" 1
  echo "Touchpad now on."
elif [ $tp_enabled = 1 ]
then
  # The touchpad is currently enabled, so turn it off.
  xinput set-prop $tp_id "Device Enabled" 0
  echo "Touchpad now off."
else
  echo "tp_toggle: Could not get touchpad status from xinput."
  exit 1
fi
----------------------------------



Just something I got off the internet. I made an icon and just double click it to turn the touchpad on and off.

After all that I discovered that my Fn-F6 key does the same thing! If you look in the laptop manual you might find a keyboard shortcut that does it too.

---

