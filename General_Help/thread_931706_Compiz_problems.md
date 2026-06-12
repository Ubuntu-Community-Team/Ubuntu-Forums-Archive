---
title: "Compiz problems"
date: 2008-09-27
forum: General Help
---

### Post by Roanoke on 2008-09-27
When I launch blender and compiz, blender does not have decorations and whenever I click on something like a menu in the gnome bar, it "eats" away a bit of blender.
Also, the gnome terminal does not get a top bar, but it gets a border.

---

### Post by jpeddicord on 2008-09-27
It's a problem with OpenGL mixing with a composited desktop. This issue won't be fixed until 9.04. Your best bet is to turn off desktop effects & compiz when you want to work with Blender, and turn them back on when you are done.

---

### Post by Roanoke on 2008-09-27
Oh, ok. The terminal thing seems to be fixed, but one last thing: compiz seems to give non-fatal errors during startup. I have attached a log.

---

### Post by lian1238 on 2008-09-27
Backup your xorg.conf file.
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```Try adding the line```
Option "AddARGBGLXVisuals" "True"
```into your /etc/X11/xorg.conf file under the screen section. Here's mine:
```

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "UseFBDev" "true"
    Option "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       24
        Modes      "1280x800"
    EndSubSection
EndSection
```Restart X. Ctrl+Alt+Backspace.

If somehow it messes up your screen, you can reverse it.
```
sudo cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
```

---

### Post by Roanoke on 2008-09-27
Does not seem to have an effect.
```
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:27a2 (rev 03) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1440x900) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
```

---

### Post by jpeddicord on 2008-09-27
> **Roanoke said:**
> Does not seem to have an effect.
```
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:27a2 (rev 03) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1440x900) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
```

Those don't really look like errors to me, just startup messages. Does Compiz have a problem (other than Blender and 3D apps acting like crap while it is on)?

---

### Post by Roanoke on 2008-09-27
Well, the only other problems I see is that the terminal window's top bar is hidden behind the gnome panel even when it is hidden.

---

### Post by jpeddicord on 2008-09-27
> **Roanoke said:**
> Well, the only other problems I see is that the terminal window's top bar is hidden behind the gnome panel even when it is hidden.

Not quite sure what you mean. Could you post a screenshot of it? Hit Print Screen, save it, and attach it to your post by clicking Manage Attachments below the post reply form.

---

### Post by Roanoke on 2008-09-27
Here.

---

### Post by jpeddicord on 2008-09-27
Ah, so the window is just placed under there? You should be able to hold down Alt and click anywhere on the window to drag it out.

---

### Post by Roanoke on 2008-09-27
Yes, but only the terminal shows this behavior. Isn't this odd?

---

### Post by Roanoke on 2008-09-28
That, and it seems that my theme selection in emerald has no effect - compiz uses my metacity theme. It has worked before, though.
Edit: Nevermind, it seems setting the command to '/usr/bin/emerald --replace' solves the problem.

---

