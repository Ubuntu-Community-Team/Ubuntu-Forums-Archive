---
title: "Logitech mouse and keyboard"
date: 2007-05-06
forum: Hardware &amp; Laptops
---

### Post by z0phi3l on 2007-05-06
I'm looking for a way to use the extra button on my cordless G7 mouse and to also use the added features/buttons on my LX710 cordless keyboard.

I'm pretty sure logitech doesn't make any Linux drivers so was wondering how to enable these features.

---

### Post by gjtoth on 2007-05-06
Keyboard Shortcuts will give you functionality on the top buttons and Ubuntu picks up on the multimedia buttons on the right set of the keyboard.  To get the extra buttons on top of the mouse to work, paste this to the mouse section of your xorg.conf and reboot.

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "Emulate3Buttons" "false"
        Option          "Buttons" "7"
        Option          "ButtonMapping" "1 2 3 6 7"
        Option          "ZAxisMapping"          "4 5"
EndSection

Works fine for me.

---

### Post by z0phi3l on 2007-05-06
OK that screwed up my xorg.conf file and crashed X

I'm guessing it was because I added it to the file and didn't remove the old entry right?

---

### Post by z0phi3l on 2007-05-06
one more bump before trying again

---

### Post by gjtoth on 2007-05-09
> **z0phi3l said:**
> OK that screwed up my xorg.conf file and crashed X

I'm guessing it was because I added it to the file and didn't remove the old entry right?

Perhaps I should have been more clear.  REPLACE the mouse section with what I posted above.  Do not make a separate entry.

---

### Post by nutz on 2007-06-02
> **gjtoth said:**
> Keyboard Shortcuts will give you functionality on the top buttons and Ubuntu picks up on the multimedia buttons on the right set of the keyboard.  To get the extra buttons on top of the mouse to work, paste this to the mouse section of your xorg.conf and reboot.

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "Emulate3Buttons" "false"
        Option          "Buttons" "7"
        Option          "ButtonMapping" "1 2 3 6 7"
        Option          "ZAxisMapping"          "4 5"
EndSection

Works fine for me.

That worked! Thank you for posting that.

Now what about the Keyboard that comes bundled with it?

[http://www.logitech.com/index.cfm/keyboards/keyboard_mice_combos/devices/147&cl=us,en](http://www.logitech.com/index.cfm/keyboards/keyboard_mice_combos/devices/147&cl=us,en)

---

### Post by nutz on 2007-06-02
> **gjtoth said:**
> Keyboard Shortcuts will give you functionality on the top buttons and Ubuntu picks up on the multimedia buttons on the right set of the keyboard.  To get the extra buttons on top of the mouse to work, paste this to the mouse section of your xorg.conf and reboot.

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "Emulate3Buttons" "false"
        Option          "Buttons" "7"
        Option          "ButtonMapping" "1 2 3 6 7"
        Option          "ZAxisMapping"          "4 5"
EndSection

Works fine for me.

That worked! Thank you for posting that.

Now what about the Keyboard that comes bundled with it?

[http://www.logitech.com/index.cfm/keyboards/keyboard_mice_combos/devices/147&cl=us,en](http://www.logitech.com/index.cfm/keyboards/keyboard_mice_combos/devices/147&cl=us,en)

Is there a way to make the zoom and media launch button work?

---

