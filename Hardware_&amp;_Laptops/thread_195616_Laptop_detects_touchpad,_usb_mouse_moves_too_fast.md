---
title: "Laptop detects touchpad, usb mouse moves too fast"
date: 2006-06-13
forum: Hardware &amp; Laptops
---

### Post by fredinator on 2006-06-13
I have a problem on my ubuntu (dapper) laptop, which is that my touchpad is detected, but when i go to plug in a usb mouse (which is what i prefer over the touchpad), it moves the cursor 4 pixels at a time! Is there any way to make it move smoothly without making it too slow? I tried slowing down the accelaration but it was too2 slow, _and_ still moved 4 pixels at a time.I dont know what to do, please help:confused:

---

### Post by Paerez on 2006-06-15
OK I think I know what the problem is.

First, make a backup of your xorg.conf:

```

$ sudo cp /etx/X11/xorg.conf /etc/X11/xorg.conf.bak

```

If anything messes up during this proccess, just use cp and reverse the two file names to copy the back-up back.

Now lets edit the file. Press Alt-F2 to bring up run and type the following in (or type it in a terminal):

```

gksudo gedit /etc/X11/xorg.conf

```

put in your password if necessary to open the editor.

Now locate the mouse section, it looks like this:

```

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "IMPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Resolution"            "1000"
EndSection

```

But, you will notice that you probably don't have the "Resolution" line. Add that line in to your file. If the other stuff is different, don't worry, don't change it. And make sure you ARE NOT editing this section:

```

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
EndSection

```
because that is your touch pad.

OK, now log out and log in again (you may need to press CTRL+ALT+BACKSPACE at the Login window to force xorg to reload).

Good Luck!

---

### Post by fredinator on 2006-06-18
nope didn't work... it didnt even change anything:confused:

---

