---
title: "how to enable clicking with the pointing stick on ubuntu 9.04 ?(Vaio P)"
date: 2009-10-12
forum: Hardware
---

### Post by sarah.b on 2009-10-12
hi,all
i just installed ubuntu9.o4 on my sony vaio p 
everything's fine except the "pointing stick"
does anybody know how to enable the funtions of" clicking with the pointing stick" /Scrolling /Press to select /tap to click......etc?
after tons of googling,i found some solution..but no luck .:(
[http://www.sabamiso.net/yoggy/tdiary/?date=20090202](http://www.sabamiso.net/yoggy/tdiary/?date=20090202)
[http://www.thinkwiki.org/wiki/How_to...the_TrackPoint]("http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint")

```
xinput list
``` "Virtual core pointer"    id=0    [XPointer]
    Num_buttons is 32
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is -1
        Max_value is -1
        Resolution is 0
    Axis 1 :
        Min_value is -1
        Max_value is -1
        Resolution is 0
"Virtual core keyboard"    id=1    [XKeyboard]
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Sony Vaio Keys"    id=2    [XExtensionKeyboard]
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"AT Translated Set 2 keyboard"    id=3    [XExtensionKeyboard]
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Video Bus"    id=4    [XExtensionKeyboard]
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Macintosh mouse button emulation"    id=5    [XExtensionPointer]
    Num_buttons is 32
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is -1
        Max_value is -1
        Resolution is 1
    Axis 1 :
        Min_value is -1
        Max_value is -1
        Resolution is 1
"PS/2 Generic Mouse"    id=6    [XExtensionPointer]
    Num_buttons is 32
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is -1
        Max_value is -1
        Resolution is 1
    Axis 1 :
        Min_value is -1
        Max_value is -1
        Resolution is 1
"USB Optical Mouse"    id=7    [XExtensionPointer]
    Num_buttons is 32
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is -1
        Max_value is -1
        Resolution is 1
    Axis 1 :
        Min_value is -1
        Max_value is -1
        Resolution is 1

windows XP detect the pointing stick as "alps stickpointer"  [B]

but Ubuntu 8.10/9.04 detect the alps stickpointer as a PS/2 GenenricMouse ?:confused:

[/B]if anyone know how to config the "pointing stick", please be kindly tell me~thanks!         
 [[IMG]http://forum.pocketables.net/images/buttons/quote.gif[/IMG]]("http://forum.pocketables.net/newreply.php?do=newreply&p=31995")

---

### Post by yotam on 2009-10-17
You may consider trying my Alps driver in
   [http://www.medini.org/software/alps/alps.html]("www.medini.org/software/alps/alps.html")
-- yotam

---

