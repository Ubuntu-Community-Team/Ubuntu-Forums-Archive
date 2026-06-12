---
title: "HP Pavilion zv5000 trackpad tap-to-click"
date: 2006-09-24
forum: Hardware &amp; Laptops
---

### Post by obfuscator2004 on 2006-09-24
I'm running Dapper on an HP Pavilion zv5000, and after trying everything in the threads to disable the tap-to-click feature, I have had absolutely no luck whatsoever.  Can anyone help me?  I've only been using Linux for a few days, so I can use all the help I can get.  I've tried adding "MaxTapTime 0" and "SHMConfig" and such, but to no avail.

---

### Post by eq235 on 2006-10-23
I have a simple solution that disables all tapping capabilities. Add this line to your xorg.conf:

Option "MaxTapTime" "0"

So your xorg.conf touchpad section should look something like this:

Section "InputDevice"
Identifier "Synaptics Touchpad"
Driver "synaptics"
Option "SendCoreEvents" "true"
Option "Device" "/dev/psaux"
Option "Protocol" "auto-dev"
Option "MaxTapTime" "0"
Option "HorizScrollDelta" "0"
EndSection

Hope this helps.

---

### Post by sedd on 2006-10-23
The command line program synclient lets you play with these settings while you're in X, so you don't have to restart the server, plus it list all availible options (which I think are supported with every synaptics touchpad.) For instance, you can turn on horizontal scrolling (which comes in handy) even though by looking at the pad, you'd think there was only vertical.

---

### Post by D351 on 2007-12-05
I'm having this same problem with xubuntu 7.10 (When I had 7.04, editing the file worked fine), but when I tried to edit the file it gives me the following errors...

"Writing error when attempting to save /etc/X11/xorg.conf" (when attempted in AbiWord)

and

"Can't open file to write" note: File was already opened and edited. This is just the message I got when I tried to save. (when attempted in mousepad)

---

### Post by Driv3r912 on 2007-12-05
> **D351 said:**
> I'm having this same problem with xubuntu 7.10 (When I had 7.04, editing the file worked fine), but when I tried to edit the file it gives me the following errors...

"Writing error when attempting to save /etc/X11/xorg.conf" (when attempted in AbiWord)

and

"Can't open file to write" note: File was already opened and edited. This is just the message I got when I tried to save. (when attempted in mousepad)

You should be using the Text Editor, not AbiWord, also make sure you have your administrator/root privelages - or else it's not going to save.

---

### Post by D351 on 2007-12-05
> **Driv3r912 said:**
> You should be using the Text Editor, not AbiWord, also make sure you have your administrator/root privelages - or else it's not going to save.

Well, I've got every privilege turned on that I can find. By text editor, I'm guessing that you mean mousepad. I just tried rebooting too, to see if it was just a settings thing, but that didn't help either. And when I tried getting in to the file through the terminal I met with all kinds of strange difficulties.

---

### Post by D351 on 2007-12-05
Turns out you were right about the privileges being the problem. I had some login tweaking to do. Much thanks.

---

