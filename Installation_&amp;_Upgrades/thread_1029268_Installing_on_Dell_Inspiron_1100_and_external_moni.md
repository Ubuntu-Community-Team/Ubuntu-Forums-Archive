---
title: "Installing on Dell Inspiron 1100 and external monitor"
date: 2009-01-03
forum: Installation &amp; Upgrades
---

### Post by impalerau on 2009-01-03
The display panel of my laptop started packing it in a couple of days ago.   If I dim it right down it will display long enough to boot up but that's about it.  It's currently running Gutsy with an external LG 17" LCD monitor.

I'm trying to install Intrepid on a separate partition.  When I run the install CD the initial options menu and Ubuntu startup screens show on the panel.  This is pretty much the same behaviour as the installed version.  Then the display switches to the external monitor for the plain brown splash screen.  After that the screen goes black except for the mouse pointer in the middle.

Is there a startup option available on the installation CD to get around this?

Thanks in advance.

---

### Post by heatpumpcontrol on 2009-01-03
> **impalerau said:**
>  After that the screen goes black except for the mouse pointer in the middle.



Sounds like a video driver issue. Can you get anything displayed by using the live cd?

update: Also, you may want to try to go into your laptop's bios and make sure that you have it set up to activate the 'vga out' feature. Just trying to figure out your exact problem.

---

### Post by impalerau on 2009-01-03
Hi heatpumpcontrol.  

The problem IS with the live CD.  I'm trying to install Intrepid and wanting to know if there is a startup option to fix my problem.  My exising installation works fine but when I run the Intrepid live cd I get the plain brown splash screen on my external monitor and then a black screen with a mouse cursor instead of the desktop. 

Hope that's clearer.

---

### Post by heatpumpcontrol on 2009-01-03
Yes, I'm sure this is a video error form gdm. Try this:

hit 'Ctrl+F1' This will bring you to the prompt menu

```
sudo nano /etc/X11/xorg.conf
```

Now scroll down to Section "Device" and change the 'Driver' from whatever it is to 'vesa'

Type 'Ctrl+X' and hit enter twice to save the changes.

now type:

```
sudo /etc/init.d/gdm stop
startx
```

see what results you get.

---

### Post by impalerau on 2009-01-04
You've lost me completely, heatpumpcontrol.  Where is it that you want me to do this?  I've tried 'Ctrl+F1' everywhere; on the initial menu of the Intrepid live CD, on the black screen (presumably gnome desktop) after it's booted up, even tried it now after booting up the installed version (which is Hardy btw, not Gutsy as per my first post).  The result is always the same; nothing happens at all.

I have made some other discoveries though.  The Hardy live CD boots up just fine but I would really prefer to do a clean Intrepid install rather than install Hardy then upgrade.  I checked out the xorg.conf on my existing hardy partition and it has no driver details for the display device at all, so it's presumably using whatever the default is.

I still suspect that the solution is using one of the startup option on the live CD but no idea which one.  Anyone have a clue?

---

### Post by impalerau on 2009-01-04
Bump!

Any ideas?

---

