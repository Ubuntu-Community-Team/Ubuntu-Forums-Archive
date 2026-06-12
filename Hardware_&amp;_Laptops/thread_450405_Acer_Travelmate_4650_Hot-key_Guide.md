---
title: "Acer Travelmate 4650 Hot-key Guide"
date: 2007-05-21
forum: Hardware &amp; Laptops
---

### Post by acuozzo on 2007-05-21
This post will serve as a guide to assist those interested in getting the Acer Travelmate 4650 series hot-keys working in Ubuntu Feisty Fawn (7.04). Some command-line knowledge is assumed; however, I will try to make it as "copy&paste" as possible.

_**Step 1 - Installation of AcerHk Driver**_
```

wget http://sidux.com/debian/pool/main/a/acerhk/acerhk-source_0.5.35-2_i386.deb
sudo dpkg -i acerhk-source_0.5.35-2_i386.deb

```Now that we have downloaded the package, it is time to:
```

sudo apt-get install module-assistant
sudo module-assistant auto-install acerhk-source
cd /etc
sudo gedit modules

```Add "acerhk poll=0 force_series=4650" (without quotes) to the end of the file and save. My /etc/modules file looks like this (I removed the commented section.):
```

# /etc/modules
lp
sbp2
acerhk poll=0 force_series=4650

```[B]
_Step 2 - Installation of xbindkeys_[/B]
```

sudo apt-get install xbindkeys
sudo touch ~/.xbindkeysrc
sudo chmod 644 .xbindkeysrc

```[U][B]
Step 3 - Key Mapping
[/B][/U]```

mkdir ~/.boot
cd ~/.boot
touch map_keys.bash xmodmaprc

```Now we add the following to each file:

***map_keys.bash***
```

#!/bin/bash
appname="xmodmaprc"
scriptdir=`dirname "$0"`
currentDir="$PWD"
if [ -e "$PWD/$scriptdir/$appname" ]
then
    cd "$PWD/$scriptdir"
    APP_DIR="$PWD"
elif [ -e "$scriptdir/$appname" ]
then
    cd "$scriptdir"
    APP_DIR="$PWD"
else
    cd "$scriptdir"
    scriptName=`basename "$0"`
    scriptFullPath=`ls -l "$scriptName" | sed -e 's/^.* -> //' `
    appdir=`dirname "$scriptFullPath"`
    if [ -e "$appdir/$appname" ]
    then
        cd "$appdir"
        APP_DIR="$PWD"
    else
        echo "generic_launcher: Error: Could not find $appname"
        exit 1
    fi
fi
xmodmap "$APP_DIR/xmodmaprc"

```[I][B]
xmodmaprc[/B][/I]
```

keycode 140 = EuroSign
keycode 248 = dollar

```After you save each file, you proceed to:
```

chmod 755 map_keys.bash
chmod 644 xmodmaprc

```The combination of map_keys.bash and xmodmaprc will allow the EuroSign and dollar keys (above the left and right arrows, respectively) to work.

_**Step 4 - Setup Keycodes**_
```

cd /etc/init.d
sudo touch setup_keycodes.sh
sudo gedit setup_keycodes.sh

```After this, we add the following to the file:

***setup_keycodes.sh***
```

#!/bin/sh
SKC=/usr/bin/setkeycodes
$SKC e033 132
$SKC e034 133
$SKC e026 148
$SKC e027 149
exit 0

```After you save the file, you proceed to:
```

sudo chmod 755 setup_keycodes.sh
sudo update-rc.d setup_keycodes.sh defaults

```[U][B]Step 5 - Startup
[/B][/U]I prefer to do this the GUI way. Go to System -> Preferences -> Sessions and create 2 new entries.
***Entry 1***:[ http://img.photobucket.com/albums/v288/ilFacell/001.png]("http://img.photobucket.com/albums/v288/ilFacell/001.png")
***Entry 2***:[ http://img.photobucket.com/albums/v288/ilFacell/002.png]("http://img.photobucket.com/albums/v288/ilFacell/002.png")
After this, you must append the .xbindkeysrc file created in Step 2...

[U][B]Step 6 - xbindkeys decisions
[/B][/U]The only keys left without a function are the e, P, FnF2, FnF3. In fact, using this method, P = FnF2 and e = FnF3; therefore, whatever you program you bind to one will be bound to both.
```

sudo gedit .xbindkeysrc

```Here is my .xbindkeysrc file:

***.xbindkeysrc***
```

"gnome-system-monitor"
   m:0x0 + c:151
"gnome-power-preferences"
   m:0x0 + c:159
"firefox"
   m:0x0 + c:178

```_***That's it!***_
The rest of the hotkeys can be configured in System -> Preferences -> Keyboard Shortcuts, a.k.a. /usr/bin/gnome-keybinding-properties. Also, you may want to map Alt_R as a Third-Level-Chooser and add the EuroSign to the 5 key in System -> Preferences -> Keyboard, a.k.a. /usr/bin/gnome-keyboard-properties.

_**Notes**_
This guide is rather incomplete; however, it does work! If you have any questions, feel free to e-mail me.

---

### Post by mfdc1969 on 2007-09-17
Wow, thanks for the great info! 

I have an Acer Aspire 5610Z (5610-2013) and am interested in trying this but I wonder, have you had any comments or feedback from others with 5610Z?

I noticed in different post someone cited the web page [http://www.cakey.de/acerhk/](http://www.cakey.de/acerhk/) and it says  that for Acer 5610 force the "2020" series

Would I simply insert 2020 where your example in step 1 forces 4650?

- Mike

---

### Post by PriceChild on 2008-01-02
I've got a 5610Z as well. I built acerhk from source and it all works... but hardlocks with no way to recover. I can't find anything in logs and would love some pointers or experiences for me to work on?

---

