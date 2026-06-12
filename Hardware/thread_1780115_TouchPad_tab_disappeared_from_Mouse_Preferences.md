---
title: "TouchPad tab disappeared from Mouse Preferences"
date: 2011-06-11
forum: Hardware
---

### Post by JRBalu on 2011-06-11
Hi,

I installed Ubuntu 11.04 in my HP dm1 notebook. Initially the right click on touch pad was not working well. So from the solution found on another thread, I executed this command in terminal

```
echo options psmouse proto=exps > /etc/modprobe.d/psmouse.modprobe

```

After that, the right click feature started working correctly. But the two-finger scrolling feature was gone. Also when I checked the 'Mouse Preferences' in System->Preferences, the 'TouchPad' tab was not there. Before executing the above command, it was there and I was able to activate two-finger scrolling. Please help me to resolve this issue.

Thanks in advance.
Balu

---

### Post by detrepid on 2011-06-11
I'm having the same issues and tried the same solution last night with the same results.  I "undid" the "solution" by using the terminal
change directory to /etc/modprobe.d
then sudo rm psmouse.modprobe
finally reboot.

Now you should be back to the original performance before you tried the fix.  FYI if you two finger tap it should treat it like a right click.  I'm still hunting for a real right click to work while keeping the scrolling features and speed settings working properly.  So I can't fix your original problem but I can undo your attempted fix.

---

### Post by JRBalu on 2011-06-11
Thank you very much detrepid. That did work for me and brought back multi touch in my touchpad. But now 'tap to click' is no more working :(. I checked the flag in gconf-editor(/->desktop->gnome->peripherals->touchpad) and found that it is set to support that. But now I have to press really hard the touch pad and make that click sound heard to select an item rather than just tapping it. Also the 'two-finger tap' right click feature is annoying when I am about to select a piece of text from a page for copying or something.

---

### Post by JRBalu on 2011-06-11
Sorry actually it was an error from my part. For setting the vertical scroll working, i tried a solution suggested in another thread and set flags 'setTaptime' and 'setTapMove' as '0' in /etc/X11/xorg.xonf in touchpad section. when I removed those flags and rebooted, the tap-to-click feature was back. :D

---

### Post by JRBalu on 2011-06-11
> **JRBalu said:**
> Sorry actually it was an error from my part. For setting the vertical scroll working, i tried a solution suggested in another thread and set flags 'setTaptime' and 'setTapMove' as '0' in /etc/X11/xorg.xonf in touchpad section. when I removed those flags and rebooted, the tap-to-click feature was back. :D
But my 'double-tap'-to-rightclick feature is stil screating lot of troubles.

---

