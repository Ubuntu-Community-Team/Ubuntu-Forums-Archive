---
title: "Disabling Touchpad &amp; Thumb Stick Mice"
date: 2006-02-22
forum: Hardware &amp; Laptops
---

### Post by acyd burn on 2006-02-22
I just thought I would put this all into one post so other newbies like myself can easily find out how to do this.

The problem is, with my laptop, a Dell Inspiron 4100.  The thumb stick mouse was getting stuck and sending interupts to the kernal making the mouse unusable.

To disable the thumb stick mouse. Open terminal and type:

**sudo modprobe -r psmouse**

Now you may be wondering if that disables a external USB mouse and it doesn't.  That takes care of your erratic mouse.

Now if you don't plan on using the Touchpad either or wish to disable the **Tap-to-click** feature, you need to edit a X11 file.  So open terminal and type:

**sudo gedit /etc/X11/xorg.conf**

Scroll down to the section for Synaptics Touchpad

```
Section "InputDevice"
      Identifier "Synaptics Touchpad"
      Driver "synaptics"
      Option "SendCoreEvents" "true"
      Option "Device" "/dev/psaux"
      Option "Protocol" "auto-dev"
      Option "HorizScrollDelta" "0"
      Option "MaxTapTime" "0"
EndSection
```

The 2nd to last line is the important part. Make sure **MaxTapTime** is set to 0 or if that line doesn't exsist, add it with a value of 0.

To disable the touchpad completely.  Edit the **SendCoreEvents** entry to **false**

When your done. **Control-Alt-Backspace** to reload the GUI and have the settings take effect.

---

### Post by Luke on 2006-02-22
i think it might be easier to disable the touchpad as follows:

Make sure following line is in /etc/X11/xorg.conf
Option "SHMConfig" "on"

The following command will turn off touchpad
synclient touchpadoff=1

---

