---
title: "sanity-check-2 exited with status 256"
date: 2011-06-17
forum: Hardware
---

### Post by HornSpiel on 2011-06-17
I have been running Ubuntu since February. I upgraded to running Ubuntu 11.04. I am running in on a Dell D630 laptop. The machine was working normally when I left it running  last  night. In the morning it did not resume but simply showed a blank screen. So I held down the power button to force a reboot.

On rebooting I started getting the error "there is a problem with the configuration server user/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256" immediately after logging on. I get the same message when I log in using Ubuntu (Unity), Ubutu Classic (Gnome), or  Ubutu Safe Modes. I do not get the message when logging on in recovery mode to Terminal.

I tried running the following code suggested several places on line
```
sudo chmod 775 /etc/gconf/gconf.xml.system
```for example at [https://bugs.launchpad.net/ubuntu/+source/gconf/+bug/269215](https://bugs.launchpad.net/ubuntu/+source/gconf/+bug/269215) but this did not solve the problem.

I am also having some screen resolution issues which may or may not be related

Initially this morning the  login screen looked fine. After logging in (to Unity) and clicking past the error message, the screen resolution changed to be smaller (1024x768 rather than the correct 1289x800 (there are black unused spaces on either side in 1024x768.) When I ran Monitor to configure the display settings correctly, the black unity bar at the top went across the screen correctly but the rest of the desktop was black on the right side (but you could still select things on the desktop). I could not get the screen to display correctly after several reboots

Then tried logging in in classic mode. In classic mode I was able set my screen and desktop to display correctly. When I logged-in in Ubuntu (Unity) mode the screen looked correct. Problem solved! However, curiously, now the login screen is displaying at 1024x768 (with black bars at either side) when before it was displaying properly.

I checked the .xsessions-errors file and there are a lot of errors recorded of two types (examples below):

[LIST]
[*]<unknown>:1682): GLib-GIO-CRITICAL **: g_bus_own_name: assertion `g_dbus_is_name (name) && !g_dbus_is_unique_name (name)' failed
[*](nautilus:1703): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed
[/LIST]
I am still getting the Sanity-check error message. There is something messed up. Can someone help?

---

