---
title: "Turn laptop screen off at will?"
date: 2008-09-06
forum: Hardware
---

### Post by fINTiP on 2008-09-06
How would I go about setting a hotkey that would toggle turning the screen on my laptop on/off? (not sleep or anything, just turn off the screen so that I can use skype outside and get the maximum out of my limited battery life.)

I'm running ubuntu studio 8.04.1, and I'm on a 2.2Ghz dell C640, one or two generations back.

<3

---

### Post by ryanhaigh on 2008-09-06
The command you want to use is:
```
xset dpms force off
```

You can also check out man xset for more information (from the terminal) or seach the help in system menu for xset.

If you are using Compiz and have the [apt://compizconfig-settings-manager]("apt://compizconfig-settings-manager") installed then open the configuration manager from System>Preferences>Advanced Desktop Effects Settings.

Open General Options>Commands and enter the above command for one of the entries, noting the number. Then go to the Actions tab and double click on the Run command entry that corresponds with the new command, enter the key combination and you should be done.

If you are not using Compiz then you will need to using the gconf-editor. Press alt-f2 to bring up the run dialog and enter gconf-editor. Find your way to apps>metacity>keybinding_commands in the tree on the left. Again set one of the commands to the above mentioned xset command then go to global_keybindings which should be directly above keybinding_commands. It is a little trickier to set a keybinding in gconf-editor as you have to enter the key combo details as text, there are some examples provided at the bottom of the gconf-window when you select run_command_X from the list. If you want to use the windows key on the keyboard it is referred to as <Super>. So for example you could use <Super>s to bind the windows+s key combination to turn off the display.

NOTE: I am using ubuntu 7.10 so things may be a little different in the Compiz settings manager if you are using 8.04

---

### Post by fINTiP on 2008-09-27
I don't have that menu option available. :\

I'm in ubuntu studio 8.04.01, fully updated.

I'm also having an issue where, when I close my laptop, the screen goes off (Even though I have it set to do nothing under 'power management'), and when I open the lid, it will not come back on.

The computer *does* still function with the screen off, because I can use the hotkey to open a terminal and type in 'sudo shutdown now -P', or 'sudo pm-hibernate', and see it obey.

But hibernation on this machine is shakey, and invariably my computer will not boot up the hibernated state (freezing instead on the load screen) if I sent the hibernate command with the screen turned off.

My computer also will not sleep, if that helps.

L

---

### Post by fINTiP on 2008-09-27
Also, I don't know if it helps, but "xset q" yields the following:

```
user@computer:~$ xset q
Keyboard Control:
  auto repeat:  on    key click percent:  0    LED mask:  00000000
  auto repeat delay:  500    repeat rate:  30
  auto repeating keys:  00ffffffdffffbbf
                        fadfffdfffdfe5ef
                        ffffffffffffffff
                        ffffffffffffffff
  bell percent:  50    bell pitch:  400    bell duration:  100
Pointer Control:
  acceleration:  7/2    threshold:  6
Screen Saver:
  prefer blanking:  yes    allow exposures:  yes
  timeout:  0    cycle:  0
Colors:
  default colormap:  0x20    BlackPixel:  0    WhitePixel:  16777215
Font Path:
  /home/kajo/.gnome2/share/cursor-fonts,/usr/share/fonts/X11/misc,/usr/share/fonts/X11/100dpi/:unscaled,/usr/share/fonts/X11/75dpi/:unscaled,/usr/share/fonts/X11/Type1,/usr/share/fonts/X11/100dpi,/usr/share/fonts/X11/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,/home/kajo/.gnome2/share/fonts
Bug Mode: compatibility mode is disabled
DPMS (Energy Star):
  Standby: 0    Suspend: 0    Off: 0
  DPMS is Enabled
  Monitor is On
File paths:
  Config file:  /etc/X11/xorg.conf
  Modules path: /usr/lib/xorg/modules
  Log file:     /var/log/Xorg.0.log

```

---

### Post by ryanhaigh on 2008-09-27
Well I'm not using Hardy so I can't tell you where to go to add the shortcut key for compiz but you can always just create a launcher on the desktop (right click on desktop > crate launcher) and use the xset command above for the launchers command.

The screen going off when you shut the lid could be a hardware thing and you might be able to run another xset command to try and get it to turn back on but I can offer any advice other than to look at the man page for xset.

---

### Post by pelle.k on 2008-09-27
> I don't have that menu option available. :\
ccsm? install it then!

About gconf-editor, you may enable it by editing the menus. It's usually hidden in the "system" menu.

> Even though I have it set to do nothing under 'power management'
Unless you have special powers, this setting only applies to a notebook connected to AC power. (i'm running arch atm, but it should be identical).
Either way, you may set such "hidden" preferences" using, surprise surprise, gconf-editor. Go to, /apps/gnome-power-manager/buttons/lid_battery.

If you get this keyboard shortcut going you may not have to shut the lid to blank the screen, and you may also wake the screen up should you happen to shut the lid, by some unknown reason i guess.

btw, if "xset dpms force on/off" doesn't work, try "vbetool". (you guessed it, in a terminal window).

Good luck!

---

### Post by fINTiP on 2008-09-30
deleted, accidentally posted in the wrong place.

---

### Post by fINTiP on 2008-09-30
Wrong location.

---

### Post by Mi11z on 2010-09-26
> **ryanhaigh said:**
> The command you want to use is:
```
xset dpms force off
```

You can also check out man xset for more information (from the terminal) or seach the help in system menu for xset.

If you are using Compiz and have the [apt://compizconfig-settings-manager]("apt://compizconfig-settings-manager") installed then open the configuration manager from System>Preferences>Advanced Desktop Effects Settings.

Open General Options>Commands and enter the above command for one of the entries, noting the number. Then go to the Actions tab and double click on the Run command entry that corresponds with the new command, enter the key combination and you should be done.

If you are not using Compiz then you will need to using the gconf-editor. Press alt-f2 to bring up the run dialog and enter gconf-editor. Find your way to apps>metacity>keybinding_commands in the tree on the left. Again set one of the commands to the above mentioned xset command then go to global_keybindings which should be directly above keybinding_commands. It is a little trickier to set a keybinding in gconf-editor as you have to enter the key combo details as text, there are some examples provided at the bottom of the gconf-window when you select run_command_X from the list. If you want to use the windows key on the keyboard it is referred to as <Super>. So for example you could use <Super>s to bind the windows+s key combination to turn off the display.

NOTE: I am using ubuntu 7.10 so things may be a little different in the Compiz settings manager if you are using 8.04


Greeting's, I tried your compiz method but after a little over a second the screen just bounces back on. any ideas?

---

### Post by Mi11z on 2010-09-26
Found a new solution that was exactly what i was looking for, this should help anyone else, so here it is for future reference:

```
sleep 1 && xset dpms force off 
```

and like mentioned above this can be set as a key-binding in compiz settings and also because of ```
sleep 1
``` it doesn't leave you with no way to turn your monitor back on, you simply wiggle your mouse or press any key. :D

PS. sorry for double posting, my head was else where.

---

