---
title: "Gnome-Display-Properties malfunctions"
date: 2009-10-18
forum: Hardware
---

### Post by ImConfused on 2009-10-18
I am using an external monitor with Ubuntu 9.04.  I am attempting to turn off the display on the laptop screen.  The FN + F5 keys would do it in Windows but that only turns off the external monitor for a few seconds in Ubuntu.  In windows the information about my laptop is as follows: 

Laptop driver Windows laptop monitor true color 1024 by 768 Intel[R] 82852/82855 GM/GME

In the terminal I typed gnome-display-properties which gave the same screen as did the gnome display "configure display settings" screen.  In the terminal it showed:
"
(gnome-display-properties:13922): Gtk-WARNING **: Ignoring the separator setting

(gnome-display-properties:13922): libglade-WARNING **: could not find a parent that handles internal children for `vbox'
"

I uncheck mirror screens.

I click on the laptop screen.

I click on monitor laptop off.

I click apply.  The laptop monitor turns off for a few seconds then it turns back on again.  I get the message:
"
Could not apply the selected configuration:  Did not receive a reply,  Possible causes include: the remote application did not send a reply,  The message bus security policy blocked the reply, the reply timed out expired, or the network connection was broken
"
It seems that the GUI is not really doing its job in that it really can't change the settings.  It does have the ability to turn off the screen since I see that happening briefly.  This problem is something that has been around for some months now from what I can see on the Internet searching.  When I ran the GUI as root I got the same terminal statement.

In the GUI there was no turning off of the monitor when started as root.  It gave the message:
"
Could not apply the selected configuration Method "ApplyConfiguration" with signature""on interface"org.gnome.SettingsDaemon.XRANDR" doesn't exist
"
Possibly it is looking for the configuration settings in the wrong directory when I started the GUI as root.

I ended up using the following commands as was indicated in another post.

xrandr --output LVDS --off         Turn off Laptop monitor
xrandr --output LVDS --auto        Turn On Laptop monitor

---

