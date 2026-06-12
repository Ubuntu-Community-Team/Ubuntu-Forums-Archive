---
title: "[SOLVED] I broke compiz."
date: 2008-11-25
forum: General Help
---

### Post by keshava on 2008-11-25
I was trying out the desktop cube and doing allot of experiments to see what I liked. But a misplaced click on animate background made almost my whole system crash. When I restarted compiz wouldn't  start and I don't know how to make it work. :(

---

### Post by Usufruct on 2008-11-25
I would recommend reverting to defaults.  Assuming you have the latest CompizConfig settings manager installed, go to preferences on the bottom left, and click "Revert to default".

---

### Post by keshava on 2008-11-25
I did that. No luck. :'(

---

### Post by keshava on 2008-11-25
When I tipin compiz in terminal the output is:
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:27a2 (rev 03) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity

---

### Post by loomsen on 2008-11-25
You need to get the right driver for your video device.

---

### Post by keshava on 2008-11-25
And how would I do that?

---

### Post by gotron on 2008-11-25
which video card are you using?

---

### Post by keshava on 2008-11-25
Intel Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Comntroller (rev 03) (prog-if 00 [VGA controller])

Is what it says.

---

### Post by gotron on 2008-11-25
see if you have any restricted drivers to use.

---

### Post by loomsen on 2008-11-25
```
sudo apt-get update && sudo apt-get install xserver-xorg-video-intel
```

Then check your xorg.conf to see if it's actually configured to use the appropriate driver, by opening it up with:
```

sudo nano /etc/X11/xorg.conf

```

Search for the **Section "Device"** and make sure it contains a line **Driver "intel"**

Should look sth like this:
```

Section "Device"
    Identifier     "Device0"
**    Driver         "intel"**
EndSection

```

Simply make sure the Driver line is present. Don't change any other lines, as they are Optional anyway.
Save and close the file. Reboot. Check back.

---

### Post by keshava on 2008-11-27
I ran that command, checked xorg.conf and corrected the driver and nothing changed. 
Anybody have any ideas?

---

### Post by keshava on 2008-11-27
Nevermind. I upgraded to 8.10 and it works now.

---

