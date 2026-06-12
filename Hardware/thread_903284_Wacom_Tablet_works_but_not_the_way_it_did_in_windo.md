---
title: "Wacom Tablet works but not the way it did in windows"
date: 2008-08-28
forum: Hardware
---

### Post by mattgaunt on 2008-08-28
Hey everyone

I know this is going to seem pretty stupid, so I apologize for that, but basically in windows my tablet would allow me to scroll say from left to right, the pen would go completely over the tablet, the mouse would and then if I lifted the pen back over to the left side and over the right, the mouse would continue you to move left from the same position.

In Ubuntu however the mouse starts somewhere on the left hand side of the screen everytime I swipe the pen across, is there anyway of changing this behavior?

Any help or tips would be great

Many Thanks

Gaunt

---

### Post by Tony_uk on 2008-08-29
I think this may be related to the settings in your /etc/X11/xorg.conf file, or the setting that is the system default. My recollection is that the dafault behaviour is as you describe.

The solution in my case was to create and edit my /etc/X11/xorg.conf. A file which I had to create anyway to set up my dual head graphics system.

I have attatched, I believe, my own xorg.conf file as some sort of starting point.
You will need any section that has refers to "wacom" together with the stuff in "ServerLayout":

 InputDevice    "stylus"     "SendCoreEvents"
    Inputdevice    "cursor"     "SendCoreEvents"
    Inputdevice    "eraser"     "SendCoreEvents"
    InputDevice    "pad"

---

### Post by sashko on 2008-08-30
I had a same problem and I think reason is Relative opiton in xorg.conf. I'd just delete that line and my pointer shows anywhere I want.

---

### Post by mattgaunt on 2008-09-04
Thanks guys I managed to get it working after playing arnd with it a bit like u suggested

---

