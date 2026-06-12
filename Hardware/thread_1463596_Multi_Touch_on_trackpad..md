---
title: "Multi Touch on trackpad."
date: 2010-04-27
forum: Hardware
---

### Post by Kisame on 2010-04-27
If I understand correctly then lucid lynx is now multitouch compatible, after about 20 minutes of searching I still haven found any leads on how to get that working on my laptop. Im still not even sure if its a possibility, so if i could get some help it would be much appreciated

---

### Post by demetrius2009 on 2010-04-27
Hey, on my Asus k52JR multi-touch works out of the box in Lucid RC (2, 3 fingers, zoom in, zoom out) am I doing something wrong?:lolflag:

---

### Post by Kisame on 2010-04-28
I found the option in the preferences - mouse  then Trackpad, there are options for disabling, using the side thing for scrolling or 2 finger scrolling, which ive seen work on my dads laptop but is greyed out on mine, any ideas?

---

### Post by pi/roman on 2010-04-28
I don't know if there is a differnece between trackpad and touchpad but if there is maybe someone can explain it to me. The following instructions for changing touchpad options in Lucid are from my tuochpad guide:

[SIZE=4][COLOR=SeaGreen]_b: udev configuration_[/COLOR][/SIZE]
This is the only way I have found to configure the touchpad in Lucid but it may not work with ealier releases.
You will need to create a file to include udev rules so use Alt/F2:```
gksudo gedit /etc/udev/rules.d/touchpad.rules
```Now you should have a blank slate here so here is what you need to put in it:
```
ACTION!="add|change", GOTO="touchpad_end"
KERNEL!="event*", GOTO="touchpad_end"
ENV{ID_INPUT_TOUCHPAD}!="1", GOTO="touchpad_end"
ENV{x11_options.[COLOR=Red]OPTION[/COLOR]}="[COLOR=Red]VALUE[/COLOR]"
LABEL="touchpad_end"
``` In this line: "ENV{x11_options.OPTION}="VALUE" you want to change the option and value to the ones you found to work in step 3 and recreate as many more of these lines as you need to cover all of the settings you want.

[COLOR=SeaGreen]section 3:[/COLOR]
Open a terminal and type:
     

     ```
synclient -l
```You should see some values assigned to your touchpad options here. If you are getting an SHMconfig error then you need to enable it through hal.
You can adjust settings temporarily through synclient by typing in terminal      

     ```
synclient [COLOR=Red]OPTION[/COLOR]=[COLOR=Red]VALUE[/COLOR]
```

---

