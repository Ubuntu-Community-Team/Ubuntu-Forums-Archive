---
title: "Mouse lag and sound problems in Quake 3 (native)."
date: 2008-04-26
forum: Hardware
---

### Post by lipin on 2008-04-26
Ubuntu 8.04
I am using Nvida Geforce 6200 graphics card and  i managed to get stable fps in quake 3 arena after adjusting some setting using nvclock.

But now into topic. Now i am experiencing some mouse lag. When I move mouse fast it seems that mouse is not quick enough handled. Looks like buffer is filled and than I see mouse movement (after fast move) even if i don't touch it. It is even more clearly visible on high DPI. I use xset m 0 0 to disable mouse acceleration.

Another quite frustrating problem is that quake 3 is hanging when i try to connect to internet server with sound on (s_initsound 1). In single player it works fine. I use X-Fi Music with oss drivers.

Playing quake 3 win32 with Cedega everything works fine (sound/mouse) but i can't use Punk Buster.

Looking for your help.

Greetings

---

### Post by Poffertje on 2008-09-14
> **lipin said:**
> 
But now into topic. Now i am experiencing some mouse lag. When I move mouse fast it seems that mouse is not quick enough handled. Looks like buffer is filled and than I see mouse movement (after fast move) even if i don't touch it. It is even more clearly visible on high DPI. I use xset m 0 0 to disable mouse acceleration.

Old-ish topic, but it seems that they have a habit of getting buried and never answered here.

Same exact problem, also obvious in Warsow and probably any other native (FPS?) game.  I'm running an 8800GT with an Intel Q6600, if that helps.

This completely prevents me from playing native Linux games, which I would really love to do.

=================================

Update 1: Fixed Warsow mouse issue by setting "in_dgamouse 0" as per [http://www.warsow.net/wiki/index.php?title=IN_:_Input_Settings](http://www.warsow.net/wiki/index.php?title=IN_:_Input_Settings).  Uncertain if Quake 3 has a similar command, but I've heard in_mouse -1 works for some (though not me).

=================================

Update 2: Fixed perhaps entirely after a few hours of frustration and Googling.

I first changed mouse driver from "mouse" to evdev, finally settling on the following to work completely with my mx518:

```
Section "InputDevice"
    Identifier      "Configured Mouse"
    Driver          "evdev"
    Option          "evBits"
    Option          "keyBits"       "~272-287"
    Option          "relBits"       "~0-2 ~6 ~8"
    Option          "Pass"          "3"
EndSection
```

This didn't appear to do anything right or wrong, but I figured that switching to evdev couldn't possibly be a bad thing and left it.

What actually fixed it was adding the following to the "Module" section:

```
    SubSection "extmod"
        Option  "omit xfree86-dga" # Don't initialise DGA extensions
    EndSubSection
```

Tested this in Warsow (in_dgamouse "1" produced a warning upon setting, which was fine) and OpenArena.  Both worked flawlessly where they wouldn't before, so I assume that other games will too.

---

