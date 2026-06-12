---
title: "Left-handed mouse, right-handed touchpad/trackpoint."
date: 2011-05-01
forum: Hardware
---

### Post by walkeraj on 2011-05-01
As a regular laptop user, I find that I've grown rather used to using the touchpad (or in the case of my Lenovo X200, trackpoint) with my right hand.  If I'm going to be working on graphics, playing games or even just working for an extended period of time, however, I want to be able to use my mouse.  Being left-handed, I prefer to use my mouse in this configuration, however the default Ubuntu installation even up to Natty only allows one configuration at a time.

I know that rules can be written to do this, but Ubuntu has changed methods for doing this sort of things so many times, that I'm not sure where to begin.  I suspect some sort of udev rule is needed?

---

### Post by walkeraj on 2011-05-09
I'm going to go ahead and answer my own question because I've finally figured it out and because it could potentially be useful to others.

The way to do this in Ubuntu 10.04 and newer is to use xorg.conf "fragments", which, according to the documentation [here]("https://wiki.ubuntu.com/X/Config") are "files [that] can each contain one or more Sections in the same format used by xorg.conf" and are "automatically loaded by X at start prior to reading the xorg.conf".

What's interesting about this documentation is that it claims [here]("https://wiki.ubuntu.com/X/Config/Input") that you can use lines like this to set your buttons in udev rules:

```
ENV{x11_options.ButtonMapping}="1 2 2 4 5 6 7 3 8"
```

I wasn't able to get this to work (perhaps because of the gnome-settings-daemon which I cover later), and read somewhere that it was deprecated.  Regardless, fragments really do seem to bet the better way of going about this, and are cleaner, easier to understand, and more closely mimic the older non-hal non-udev way of doing things in an xorg.conf file.

In Natty, the best place to put these fragments is probably /etc/X11/xorg.conf.d, which you have to create:

```
sudo mkdir /etc/X11/xorg.conf.d
```

In my case, I created a file called **00-mouse-remap.conf**, containing the following:
```
Section "InputClass"
    Identifier "Microsoft Bluetooth Mouse 5000 button remap"
    MatchProduct "Microsoft Bluetooth Notebook Mouse 5000"
    MatchIsPointer  "on"
    MatchDevicePath "/dev/input/event*"
    Driver          "evdev"
    Option          "SendCoreEvents" "true"
    Option          "Buttons" "8"
    Option          "ButtonMapping" "3 2 1 4 5 0 7 0"
EndSection
```

The buttons option is probably unnecessary, but I included it for completeness' sake.  Then, as far as X is concerned, any device that udev reports as having the name "Microsoft Bluetooth Notebook Mouse 5000" will be given this inputclass with this button mapping.

That's not the end of the story, however, as Natty still uses gnome-settings-daemon to control mouse and keyboard settings.  Usually, this is smart enough to get out of the way, but when it comes to mice, (specifically buttons) it will attempt to automatically ensure that your primary and secondary buttons are mapped to the system-wide left or right handed layout.  In this particular case, we don't want that, so we need to turn this bit of functionality off.  The quickest way to do that is with **gconf-editor**, which you need to install:

```
sudo apt-get install gconf-editor
```

Then, once you run gconf-editor, from the GUI, navigate to > apps > gnome_settings_daemon > plugins > mouse and uncheck the box for **"active"**.  Then, restart X.  That should be it!  You will now have a left-handed mouse and a right-handed touchpad.  Note that you will need to re-enable the mouse plugin for gnome-settings-daemon if you want to use the mouse preferences to set your mouse button layout again.

Otherwise, you can do this by making conf fragments for all of your pointing devices to get them set up the way you want (the better option, IMHO).

For more information on this, refer to:
[LIST]
[*] [This excellent tutorial]("https://fedoraproject.org/wiki/Input_device_configuration") at the Fedora Project.
[*]'man xorg.conf' (search for InputClass and InputDevice)
[*]'man evdev' (or your driver) for the options the InputClass can have
[*][https://wiki.ubuntu.com/X/Config]("https://wiki.ubuntu.com/X/Config")
[/LIST]

---

### Post by uncol on 2012-08-31
Ubuntu 12.04:

Default directory is
```
/usr/share/X11/xorg.conf.d
```


Instead gconf-editor should be use gsettings

```
gsettings set org.gnome.settings-daemon.plugins.mouse active false
```

---

### Post by ktucker on 2012-10-02
The above solution would make it so for all users I think? Another approach:

In a terminal:

$ xinput list | grep 'id='
e.g.
...
... AlpsPS/2 ALPS GlidePoint id=19
...
Look at button map (e.g.):
$ xinput get-button-map 19
3 2 1 4 5 6 7 8 9 10 11 12
Only the first three are relevant (left, middle and right buttons set for left-hander in this case).

Then set touchpad to right-handed (without affecting the left-handed mouse which is a different device):

$ xinput set-button-map 19 1 2 3
or
$ xinput set-button-map "AlpsPS/2 ALPS GlidePoint" 3 2 1

Now it works as desired (LH mouse, RH touchpad :-).

The next problem is how to do this automatically as soon as this user logs in (or is auto logged in) to Unity.
Any suggestions?

PS The above commands came from [https://wiki.ubuntu.com/X/Config/Input](https://wiki.ubuntu.com/X/Config/Input)

---

