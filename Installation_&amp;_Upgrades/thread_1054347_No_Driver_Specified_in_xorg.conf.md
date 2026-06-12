---
title: "No Driver Specified in xorg.conf"
date: 2009-01-29
forum: Installation &amp; Upgrades
---

### Post by krt on 2009-01-29
Having installed the "nvidia binary xorg driver (new)", "nvidia x server settings" as well as "hardware drivers", I got a notice that said "/etc/X11/xorg.conf" Device Section "Configured Video Device" must have driver line.

Since my video is not optimum (text rendition when on line in FF where "appearance" font controls have no effect), I am posting the relevant sections of xorg.conf, because I have not a clue as to what to do to clean up the video. "Configured Video Device" apparently is not sufficient.
--------------------------------------------
Section "Device"
Identifier "Configured Video Device"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
EndSection
--------------------------------------------
Any suggestions as to what to do here would be greatly appreciated. Video card is nvidia FX5200.

Thank you,

krt

---

### Post by avtolle on 2009-01-29
In Section "Device" add a line Driver with the correct driver as shown```
Section "Device"
Identifier "Configured Video Device"
Driver "(put name of driver here)"
End Section
```I hasten to add I don't know what the name of the correct driver is, but that is how you would do it.

To edit the file, open a terminal and ```
 sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup #This backs up the file
sudo nano /etc/X11/xorg.conf #opens file for editing
```then make the changes. After the editing is finished, Ctrl+o to write, Enter to accept the name of the file, Ctrl+x to exit the editor. Restart X by Ctrl+Alt+Backspace and see if your changes work. Good luck.

---

### Post by krt on 2009-01-29
Thank you for getting back to me on this.  Interestingly, when I was messing around with this prior to posting, I had attempted to configure the video driver by booting into safe mode and choosing my video card from the list, and when I came out of it, I was in deep trouble and had to reboot into safe mode and let the "automatic" x option do its thing which put me back into the original state.

However, as I prepared to follow your suggestions above, I discovered that now under "system>administration" there was an option "NVIDIA X Server settings".  When I click on this, I got (among other things) a pop up box that told me to run (as root) "nvidia-xconfig" and when I did that, and then did the ctrl+alt+backspace thing, it restarted showing the NVidia splash screen, and the new entries were in the xorg.conf file!

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Whether my messing with trying to set the card in safe mode had anything to do with this or not, I don't know, but I do know that after installing the x server deal in synaptic last night, I got that notice about running the deal as root and it would not run . . . 

Anyway, it seems to be working right now, and I appreciate very much your getting back to me.

krt

---

