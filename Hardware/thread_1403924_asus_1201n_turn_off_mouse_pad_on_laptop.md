---
title: "asus 1201n turn off mouse pad on laptop?"
date: 2010-02-10
forum: Hardware
---

### Post by Rumbl3 on 2010-02-10
Well my FN button don't work to allow me to turn off the built in mouse on my laptop. I hate the thing tend to hit it constantly when i'm typing and stuff.

Is their anyway to manually turn this off? I looked in my bios and it's not their like it was with my old laptop. 

Just curious if their is anyway in the os that list devices? so i can disable it or something?

---

### Post by Miljet on 2010-02-10
You can go into System -> Preferences -> Mouse, click on the Touchpad tab and untick the "Enable touchpad" option. I have never used it, but I would assume that it turns off the touchpad.

Just realized that you are running Xubuntu. I do not know if the same options exist or not.

---

### Post by Rumbl3 on 2010-02-11
Yeah it's different anyone else know where to shut it off?

---

### Post by Rumbl3 on 2010-02-15
I switched over to ubuntu to see and that option is not on their. Don't exist in 9.10 i guess anyone have a clue how to get rid of it?

---

### Post by pi/roman on 2010-02-16
I made a script to toggle the touchpad off when you plug in a usb mouse.
toggle when using usbmouse
Make a script to disable the touchpad and one to enable it called "synkill.sh" and "synwake.sh" using the name of your touchpad as described in 5b of the guide:
```
DISPLAY=:0 xinput set-int-prop 'SynPS/2 Synaptics TouchPad' 'Device Enabled' 8 0
``````
DISPLAY=:0 xinput set-int-prop 'SynPS/2 Synaptics TouchPad' 'Device Enabled' 8 1
```Now create a udev rule to enact the scrpit when the mouse is changed and place it in /etc/udev/rules.d/:
> ACTION=="add", SUBSYSTEMS=="usb", DRIVER=="usbhid", ATTRS{product}=="*Mouse", RUN+="/bin/sh -c /usr/bin/synkill.sh"
ACTION=="remove", ATTRS{product}=="UHCI Host Controller", RUN+="/bin/sh -c /usr/bin/synwake.sh" I also have a guide for adjusting permanent settings on the touchpad.

---

### Post by pi/roman on 2010-02-20
Did this solve the problem?

---

### Post by arma0012 on 2010-02-20
Could you please explain what you mean by '5b of the guide'

Cheers,
Sam

---

### Post by pi/roman on 2010-02-21
Whoops, I forgot to provide a link to it: [[COLOR=Blue]http://ubuntuforums.org/showthread.php?t=1401645[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1401645")
And I have revised the guide a bit but there is still a command in section 5b that will list the name of the touchpad and it's properties here:
```
xinput list --short | grep -i 'touchpad' | grep -o '"[^"]*"' | xargs xinput list-props
```But I have also updated the mouse hot plug toggle so you don't need to know the name of the touchpad.  Using these two scripts which should be placed in /usr/bin/:
```
DISPLAY=:0 xinput list --short | grep -i 'touchpad' | grep -o '"[^"]*"' | DISPLAY=:0 xargs -I nero xinput set-int-prop nero 'Device Enabled' 8 0
``````
DISPLAY=:0 xinput list --short | grep -i 'touchpad' | grep -o '"[^"]*"' | DISPLAY=:0 xargs -I nero xinput set-int-prop nero 'Device Enabled' 8 1
```And a simplified udev rule to place in /etc/udev/rules.d/ which will be applied by plugging any usb mouse:
[HTML]ACTION=="add", SUBSYSTEMS=="usb", ID_CLASS="mouse", RUN+="/bin/sh -c /usr/bin/synkill.sh"
ACTION=="remove", SUBSYSTEMS=="usb", ID_CLASS="mouse",  RUN+="/bin/sh -c /usr/bin/synwake.sh"[/HTML]

---

### Post by arma0012 on 2010-02-22
I've made the first script and saved it in my home directory, then tried to copy it across to usr/bin and was told:

```

sam@angus:~$ cp -v /home/sam/synkill.sh /usr/bin/
`/home/sam/synkill.sh' -> `/usr/bin/synkill.sh'
cp: cannot create regular file `/usr/bin/synkill.sh': Permission denied
```I also could not save directly to /usr/bin

I assume I've made some basic permissions error but not quite sure what, or how to fix it.

Any help greatly appreciated.

Cheers,
Sam

---

### Post by pi/roman on 2010-02-22
You've got it right, just be sure to make the script executable first by right clicking on it, selcecting "properties", then "permissions" tab, and check the box to "allow executing file as program" then place a sudo before your command to copy it.
```
sudo cp -v /home/sam/synkill.sh /usr/bin/
```

---

### Post by arma0012 on 2010-02-23
Thanks a billion. Now I can finally stop typing in random places.

Couldn't have done it without your help.

Cheers,
Sam

---

