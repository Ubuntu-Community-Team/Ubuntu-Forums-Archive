---
title: "Breezy: Gnome menus and keyboard without response."
date: 2005-10-17
forum: Hardware &amp; Laptops
---

### Post by gubatron on 2005-10-17
I have a laptop compaq nx9010

After upgrading to Breezy, sometimes Gnome starts showing up many
"Take Screenshot"  windows.

I suppose this is because somehow my print scr key get' s stuck.

After I end up closing lots of this take screenshots (If I'm lucky to have the machine still responsive) then my keyboard won't work anymore.

The caps lock led won't turn on/off, no response at all.

Then, the "Applications" , "Places"  or "System"  menus won't display, they will just highlight but they won't be shown.

The same thing to all the menus of all the windows, if you hover and click your mouse pointer through the "File" "Edit" ,etc menus of open apps, they won't display, so you end up stuck in Gnome, with no way to logout, (unless you have placed the "logout" app on the panel).

To workaround this I edited the keybindings with gnome-conf:
Look for this key:
/apps/metacity/global_keybindings/run_command_screenshot

it will have the "print" key set to it, disable it, and let's hope that solves the issue, I'm still posting this so I think it worked, but I still suspect if that key is being pressed still.

Does anyone know how to detect what keys are being pressed? or has anyone heard about this issue, or maybe it's just a malfunction with my keyboard.

---

