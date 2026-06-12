---
title: "Getting a Wacom Touch/Pen tablet CTL-470 configured at boot"
date: 2013-06-20
forum: Hardware
---

### Post by layolayo on 2013-06-20
using - 13.04 64bit

I have run through many websites and forums to get a very simple solution to my original problem - posting this for anyone else who may have the same/similar issue.

I bought a Wacom CTL-470 for my daughter last Christmas (2012) - plugging in the unit we had instant operation, but no access to configuring the buttons on the actual tablet itself. Also I wanted to be able to switch off the touch feature when drawing with the stylus.

I did some searching - discovered that KDE had more options for the config of the wacom - so used that for a while, but I do like Unity :) - so I gave up, until yesterday when I gave it another shot.

I now have two scripts: wacom-setup.sh and toggle-wacom.sh

wacom-setup.sh is run at boot from the Start-Up Programs (I had to do this as adding these lines to rc.local did not work - any ideas why...?)
toggle-wacom.sh is run at the keyboard command (shift+alt+t)

[B]wacom-setup.sh
[/B]```
xsetwacom --set "Wacom Bamboo 16FG 4x5 Finger pad" Button 1 "key shift alt t"
xsetwacom --set "Wacom Bamboo 16FG 4x5 Finger pad" Button 3 "key ctrl z"
xsetwacom --set "Wacom Bamboo 16FG 4x5 Finger touch" touch off

```

[B]toggle-wacom.sh
[/B]```
#!/bin/bash


## Get the "Device name" or ID number
## for touch from 'xsetwacom list dev'


DEVICE="Wacom Bamboo 16FG 4x5 Finger touch"
TOUCH_STATE=`xsetwacom get "$DEVICE" touch`
if [ "$TOUCH_STATE" == "on" ]; then
    echo "Touch is ON, turning OFF."
    xsetwacom set "$DEVICE" touch off
  else
    echo "Touch is OFF, turning ON."
    xsetwacom set "$DEVICE" touch on
fi

```

I haven't used the two buttons in the middle yet, these are numbered 8 and 9 if you want to configure them.
To get the name of your device use:

```
xsetwacom --list devices
```

I also want to mention that I did attempt to make changes in /usr/share/X11/xorg.conf.d/50-wacom.conf to do some of the above. I ran into many problems, the main one being that I was unable to boot my system. I had to go to recovery mode -> enable read/write access and then remove the changes I had made to the 50-wacom.conf file. It seems that X really doesn't like typo's or dodgy settings!!! I decided to stay safe - but would appreciate any advice in this area if there is any to be had.

---

### Post by Favux on 2013-06-20
Hi layolayo,

Well one bit of advice is to add user customized .conf files to /etc/X11/xorg.conf.d rather than /usr/share/X11/xorg.conf.d which is for the distributions.  The xorg.conf.d in /etc runs after the one in /usr so it controls, i.e. will override settings in /usr.

See:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xorg.conf.d](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xorg.conf.d) from:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Category:HOWTO](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Category:HOWTO)

But the only way to assign keystrokes to ExpressKeys (pad buttons in linuxwacom speak) is through xsetwacom or using one of the configuration gui's.  With xorg.conf.d or xorg.conf you can only assign an integer to a button.

Hope this helps a bit.

---

### Post by layolayo on 2013-06-22
Thanks Favux,

I also found this store house of information: [https://wiki.archlinux.org/index.php/Wacom_Tablet](https://wiki.archlinux.org/index.php/Wacom_Tablet)

---

