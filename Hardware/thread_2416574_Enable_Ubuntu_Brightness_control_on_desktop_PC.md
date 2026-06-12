---
title: "Enable Ubuntu Brightness control on desktop PC"
date: 2019-04-11
forum: Hardware
---

### Post by gipsyshadow on 2019-04-11
I know the title sounds weird but I need you help anyhow. I've a desktop pc with a regular lcd external monitor and I'd like to adjust its brightness digitally via ubuntu 18.04.2lts brightness control.
Light conditions in the room where the pc is change several times per day and I just get bored to push monitor's buttons, navigate within menus and so on therefore I'd like to find a way to change brightness with only a click, if it's possible.
Do you know any way to do that either via ready-to-use ubuntu sw or editing ubuntu graphic system files?

---

### Post by ajgreeny on 2019-04-11
Have a look at [https://askubuntu.com/questions/763642/app-to-adjust-gamma-in-ubuntu-16-04](https://askubuntu.com/questions/763642/app-to-adjust-gamma-in-ubuntu-16-04) to see if any of those scripts are of any use to you

---

### Post by gipsyshadow on 2019-04-13
all right, i solved my case starting from ajgreeny link and then looking at [this page]("http://shallowsky.com/blog/tags/x11/"). the solution is
```

xrandr --output DisplayPort-1 --brightness .5

```
consider that "DisplayPort-1" is related to my monitor and i got this parameter from
```

~$ xrandr -q | grep " connected"
DisplayPort-1 connected primary 1440x900+0+0 (normal left inverted right x axis y axis) 408mm x 255mm

```
note that the space before connected is not a mistake.
consider the ".5" example value can vary from 0.0 to 1.0 (default). also consider that changing brightness digitally via this command won't affect the monitor brightness parameter set physically by pushing buttons therefore i think the best is setting physically @100% for first and just once and then changing it digitally via that command every time you need.

i don't know if i want too much by i'd like to ask if this command can be "linked" directly to the proper desktop brightness setting cursor so my monitor will work as a laptop display. i'm very newbie so if it can be done i'll need your help anyhow :)

---

### Post by Holger_Gehrke on 2019-04-13
'xrandr --brightness' makes the graphics card output a brighter (or less bright) image. This is not quite the same as changing the brightness of the display. Modern displays all have DDC (display data channel) and DDC/CI (Display Data Channel / Command Interface). You can use ddccontrol (or its GUI gddccontrol; both are in the standard repositories) to access most if not all the settings of your display. As an example: I've set up two scripts that switch my display between one of its HDMI-Inputs and VGA to switch between two PCs connected to it. I just click on the starter for either script I've put in a panel and the display changes its input.

Holger

---

