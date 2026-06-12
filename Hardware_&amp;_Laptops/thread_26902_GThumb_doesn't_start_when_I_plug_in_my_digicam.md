---
title: "GThumb doesn't start when I plug in my digicam"
date: 2005-04-14
forum: Hardware &amp; Laptops
---

### Post by teevee on 2005-04-14
Even though it should, according to gnome-volume-properties.

The command to be executed when I plug in my digital camera (Canon Powershot A400, with an ordinary SD card) is:
gnome-volume-manager-gthumb %h (that's also the default Ubuntu/Gnome value)

Other than that this camera works flawlessly, if I run gnome-volume-manager-gthumb manually (or F-Spot) I can import photos without a problem, but it would be nice if it would be started automagically. :)

Any clue?

Oh, audio CD's, blank CD's, MP3 player and USB stick are detected correctly and the specified commands are executed automagically.

---

### Post by el_mexicano_europeo on 2005-04-19
I have the same problem as you. 

it seems that it takes my system about 3 seconds to load the camera completely. if you test this, you can plug in your camera, run gthumb --import-photos immediately afterwards and gthumb fails to detect the camera. however, if you wait 3,4,or 5 seconds, it opens up flawlessly.

this means that when you first plug in your camera, gthumb IS executed but since it doesn't detect the camera, it closes.

at least that is my idea. but that doesn't explain why: if you plug in your camera and if you have gthumb as the Exceuted Applicate in gnome-volume-manager, then it still DOESNT open.

 :-?  


p.s. let me know if you found a solution.

---

### Post by Eremit on 2005-07-02
I have the same problem and wondered if some has already found a solution  :|

---

### Post by twowheeler on 2005-07-06
Yeah, that happened to me too.  So I played with it a while and now it works.  I think I changed the System -- Preferences -- Removable Drives and Media setting to just gthumb %h, and suddenly it worked.  When I changed it back to the original setting of gnome-volume-manager-gthumb %h, it still works.

 :-?   <shrug>   It's a mystery, but it works.

---

### Post by funkydan2 on 2005-07-06
[QUOTE=twowheeler]Yeah, that happened to me too.  So I played with it a while and now it works.  I think I changed the System -- Preferences -- Removable Drives and Media setting to just gthumb %h, and suddenly it worked.  When I changed it back to the original setting of gnome-volume-manager-gthumb %h, it still works.

 :-?   <shrug>   It's a mystery, but it works.[/QUOTE]
 Is your camera being detected as a USB Mass Storage device or as a camera?

If it's detected as UMS then the default setting of gnome-volume-manager would be to mount the device and open nautilus to view the files.  Also, keeping an eye on dmesg just after you plug in the device would help with this.

(NB this is what happened for me under Warty - I haven't had a need to plug in my camera to my Hoary box yet.)

---

