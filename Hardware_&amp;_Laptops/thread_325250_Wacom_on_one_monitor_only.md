---
title: "Wacom on one monitor only?"
date: 2006-12-25
forum: Hardware &amp; Laptops
---

### Post by saxofoner on 2006-12-25
I have 2 monitors, which I use with Twinview, and I was wondering if there was a way to make the pen on the tablet only use 1 monitor for it's active area.  Ideally the wacom mouse would do 2 screens, so I could draw w/ the pen on the one screen and use the mouse for everything... This is possible in the Wacom properties on windows, is there such a thing for it in Ubuntu?  I don't see any settings, but I would guess it would be in the xorg.conf.  Anybody diggin' me?

---

### Post by saxofoner on 2006-12-25
Maybe I should have been more... general.  Does anybody know how to set preferences on a tablet?  I need to change some settings around...

---

### Post by saxofoner on 2006-12-27
I figured it out!  I pulled together random bits of info from the web, and after dozens of Ctrl-Alt-Backspaces, it works!  

I figured, since it was that hard for me, I should write a tutorial!

Okay:  

Prerequisites:
-A tablet
-Twinview (This may work w/ other dual monitor apps, I'm not sure.)  
-Some time

1.  Install the "wacom-tools" package.  
2. run:  
sudo gedit /etc/X11/xorg.conf
This will open up xorg.conf in gedit, and the sudo part lets you write to it.  Make sure you have backed it up!  How to do that is in plenty of other tutorials, DO IT!!!
3. Scroll down until you see the
```
Section "InputDevice" 
Driver          "wacom"
```
part.  

There should be 3.  One each for stylus, eraser, and cursor. Change that whoooole section to:
```

    Section "InputDevice"
      Driver        "wacom"
      Identifier    "stylus"
      #Option        "Device"        "/dev/ttyS0"          # SERIAL ONLY
      Option        "Device"        "/dev/input/wacom"   # USB ONLY
      Option        "Type"          "stylus"
      Option        "USB"           "on"                  # USB ONLY
      Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY"                  
      Option        "KeepShape"     "on"
    EndSection

    Section "InputDevice"
      Driver        "wacom"
      Identifier    "eraser"
      #Option        "Device"        "/dev/ttyS0"          # SERIAL ONLY
      Option        "Device"        "/dev/input/wacom"   # USB ONLY
      Option        "Type"          "eraser"
      Option        "USB"           "on"                  # USB ONLY
      Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
      Option        "KeepShape"     "on"
    EndSection

    Section "InputDevice"
      Driver        "wacom"
      Identifier    "cursor"
      #Option        "Device"        "/dev/ttyS0"          # SERIAL ONLY
      Option        "Device"        "/dev/input/wacom"   # USB ONLY
      Option        "Type"          "cursor"
      Option        "USB"           "on"                  # USB ONLY
      Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
      Option        "KeepShape"     "on"
    EndSection

    # This section is for Intuos3, Cintiq 21UX, or Graphire4 only
    Section "InputDevice"
      Driver        "wacom"
      Identifier    "pad"
      #Option        "Device"        "/dev/ttyS0"          # SERIAL ONLY
      Option        "Device"        "/dev/input/wacom"   # USB ONLY
      Option        "Type"          "pad"
      Option        "USB"           "on"                  # USB ONLY
      Option        "KeepShape"     "on"
    EndSection

```

Now restart (the whole computer, or just ctrl alt bkspace it), and your wacom's area should match the screen perfectly!  No more horizontal distortion!  Yay.

Can someone put this in the howtos?  Or do I have those privs?  I'll see.

---

