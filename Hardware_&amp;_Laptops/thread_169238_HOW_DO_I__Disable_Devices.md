---
title: "HOW DO I:  Disable Devices?"
date: 2006-05-02
forum: Hardware &amp; Laptops
---

### Post by unoobu on 2006-05-02
Dear Linux Community,

I am a noob.  I am running Ubuntu on my Inspiron 8600.  My  "eraser mouse" which is part of my keyboard, is broken, and it constantly pulls to the right.  Under my windows partition, I am able to disable the eraser, and I have no problem...

I have no clue how to disable anything.  I am such a noob, that I don't even know the file structure of GNU yet...

Please help, as of now I am limited to only using tab and alt to switch between programs, buttons, and links!!!

Peace,

uNOOBu :confused:

---

### Post by geek.de.nz on 2006-05-02
I am not such a newbie, but I got the same problem with my laptop and kernel 2.6 (any distro). I found a workaround by changing /etc/X11/xorg.conf:

Look for sections like:
```

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "Emulate3Buttons" "true"
    Option         "ZAxisMapping" "4 5"
EndSection

```
and change it to
```

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mouse0"
#  ...
EndSection

Section "InputDevice"
    Identifier     "Other Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mouse1"
#  ...
EndSection
#...

```

Depending on what your touchpad/mouse(s) are. Also, try deactivating the module psmouse:
```
sudo rmmod psmouse
```

If this works, you can probably also deactivate the touchpad or whatever in your bios. 

I don't really know a clean fix for this problem, i.e. how to disable the device. So please, if someone knows, that would help me too.

---

### Post by unoobu on 2006-05-02
[QUOTE=geek.de.nz]I am not such a newbie, but I got the same problem with my laptop and kernel 2.6 (any distro). I found a workaround by changing /etc/X11/xorg.conf:[/QUOTE]

LOL  This is going to prove my noobivity, but I can't change this file.  Do I have to be logged in as root?  If so, when I installed ubuntu, it didn't ask me to set a root password.  Is there a default root password?

Thanks,

uNOOBu :confused:

---

### Post by nolongerlivecd on 2006-05-02
Hey, welcome to the gang that I left a while ago, your root password is the password you set at first

---

### Post by unoobu on 2006-05-02
Oh, thank you!  

I FOUND A FIX FOR IT ON MY OWN!!!  
I JUST RIPPED IT OUT OF MY KEYBOARD WITH SOME NEED NOSE PLYERS!!! LMOA!!!  IT WORKED!  HOW IS THAT FOR A HACK ;-)

Peace,

uNOOBu

---

### Post by geek.de.nz on 2006-05-03
I'm still having trouble with my touchpad. If someone knows how to disable it, please do an effort to post, as I don't really want to open up my Laptop and rip out stuff.

Have a look here for more info:
[http://ubuntuforums.org/showthread.php?t=124567](http://ubuntuforums.org/showthread.php?t=124567)

---

### Post by kelvinelk on 2006-05-07
Hello.

I disabled my pointer stick by changing the "ServerLayout" section only.

# out the InputDevice line which references the stick (mine was "Configured Mouse") or delete it.

Then add "CorePointer" option to the InputDevice "Synaptics Touchpad"

InputDevice    "Synaptics Touchpad" "CorePointer"

---

