---
title: "ATI x300 laptop driver issue"
date: 2011-02-15
forum: Hardware
---

### Post by kaycal on 2011-02-15
Hello, Ubuntu-peeps.

I recently picked up a mega-cheap laptop, and decided to install Ubuntu on it-- largely, in all fairness, for the "adventuring into uncharted lands" aspect. In retrospect, I wish I'd labeled my install-CD (Ubuntu 10.10) with "here be dragons."

The computer is nothing super special; it has 2GB of RAM, and a 1.8GHz CPU. Oh, and a videocard whose sole purpose, it seems, is to create havoc and pain in its wake.

The "Mobility Radeon X300" does not seem to want to run properly. In my quest to play Minecraft, I've run into countless issues, starting with incredibly low FPS (between 1 and 3; 5, if I'm lucky), and finally culminating in a complete inability to start up in the first place. For the moment, though, I'm focusing on the videocard issues.

Initially, the laptop didn't seem to recognize the videocard in the first place, without running terminal tools (I'm using lshw/"Hardware Lister" at the moment); "System -> Administration -> Additional Drivers" displayed absolutely nothing. After fighting with ATI's legacy drivers (and running the installation in "compatibility mode"-- see this link), I managed to change the "Additional Drivers" screen, such that it now displays the ATI/AMD Proprietary graphics driver.

When trying to "activate" it, though, it asks for my password, and does...nothing. The status does not change to "activated," and there are no dialogue boxes to suggest why the status did not change.

[IMG]http://i4.photobucket.com/albums/y115/kdermod/Ubuntu%20Issues/Screenshot-1.png[/IMG]

When I try to configure the card through the Catalyst Control center, I get the following dialogue box;

[IMG]http://i4.photobucket.com/albums/y115/kdermod/Ubuntu%20Issues/Screenshot.png[/IMG]

When I try to configure the card using "aticonfig --initial", I get the following error;

```
kay@kay-Latitude-D610:~$ sudo aticonfig --initial
Warning: Could not find configuration file
Please copy configuration file template to /etc/X11

```When I try to configure the card again using aticonfig after fixing the missing xorg.conf file (albeit, with the suffix "--input=/etc/X11/xorg.conf" as mentioned here), I get the following error;

```
kay@kay-Latitude-D610:~$ sudo aticonfig --initial --input=/etc/X11/xorg.conf
Warning: Could not find configuration file
Please copy configuration file template to /etc/X11
```Furthermore, after installing the drivers from ATI's website, my computer's display won't work properly anytime I'm asked to "log in" (either from starting up, or after going into standby/sleep mode); it displays a semi-dynamic semi-pretty shifting color background, and...nothing else. The only method for me to get back to the gui at that point is to ALT+CTRL+F1, and type: "sudo killall -9 Xorg"

And finally (god forbid I give too much info!), glxgears and glxinfo return the following, respectively;

glxgears;
```
kay@kay-Latitude-D610:~$ sudo glxgears
Xlib:  extension "GLX" missing on display ":1.0".
Error: couldn't get an RGB, Double-buffered visual
```glxinfo;
```
kay@kay-Latitude-D610:~$ sudo glxinfo
name of display: :1.0
Xlib:  extension "GLX" missing on display ":1.0".
Xlib:  extension "GLX" missing on display ":1.0".
Xlib:  extension "GLX" missing on display ":1.0".
Xlib:  extension "GLX" missing on display ":1.0".
Segmentation fault
```Any ideas on what's going on here?

---

### Post by mastablasta on 2011-02-16
it might be a glod idea to check on AMD site if this card is actually supported. I think  it isn't and you are stuck with opensource drivers.

---

