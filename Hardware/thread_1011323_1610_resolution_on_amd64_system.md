---
title: "16:10 resolution on amd64 system"
date: 2008-12-14
forum: Hardware
---

### Post by mylo9000 on 2008-12-14
I've recently acquired my Fathers old PC the specs are
AMD Athlon 64 3200+
BFG GeForce 6200A 256MB
1GB Ram
Ubuntu 8.10
Kernel 2.6.27-9-generic

I have Ibex x64 installed and updated to the max
I'm using the 177 driver from the Hardware drivers

I have a Nova 15" Wide (16:10) 1280x800 max res LCD display with VGA connector.

Right now if i try to get any res higher then 800x600 the only option i get is 1024x768 and it flickers like mad (almost like the back light is broken) it doesn't flicker on the usplash or in a tty.

I used to use this monitor on my old Pc setup running 7.04 - back then it was detected as a Sangyo monitor and everything i worked fine.
Now its detected as an Unknown monitor and the Nvidia-settings tool describes it as CRT-1 on GPU-0

i searched all over these forums and other forums to find an answer for this but nothing seems to work.

here's my xorg.conf

```
Section "Monitor"
    Identifier    "Configured Monitor"
    Option        "DPMS" # I added this but it does nothing
    HorizSync     49.31 # Is the only thing that doesn't flicker
    VertRefresh   71    # Ditto and the modeline below
    Modeline      "1280x800_50.00" 68.56 1280 1336 1472 1664 800 801 804 824 -HSync +Vsync
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor       "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth 24
    SubSection "Display"   #i also added this subsection - no effect
        Modes "1280x800"
    EndSubSection
EndSection

Section "Module"
    Load   "glx"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Driver        "nvidia"
    Option        "NoLogo"   "True"
EndSection
```

I'm not sure why but recently it seems like any changes I make to the xorg.conf either go ignored or break it.

I would really like to use this monitor to its full potential even if 1280x800 is the only option to use, any help would be appreciated.

---

### Post by mylo9000 on 2008-12-18
iguess i'm not the only one with no idea how to fix this. :confused:

i'm confident that its only the monitor tho.
back in the day of 7.04 the monitor was detected fine and worked better than it ever did in windows.

but now its only detected as unknown and is impossible to configure.

if i ever find a fix i'll post it here.

but i'll probably end up selling the screen and getting a more compliant one.

---

### Post by vishalrao on 2008-12-18
try deleting (actually backing up/renaming away) your xorg.conf and restart Xorg?

---

### Post by mylo9000 on 2008-12-22
Funny thing is i've tried that, all i get is a xorg.conf with almost nothing in it. 

Its curious because if the conf is so empty, with almost nothing specified, how does it know to do anything? like the dri module isn't even being specified yet glxinfo states direct rendering: YES.

strange, don't you think?
Perhaps compiz-fusion uses a separate setup somewhere else, or maybe everything is just auto-detected on start-up?

maybe thats why most changes i make to the xorg.conf go ignored?

---

### Post by mylo9000 on 2009-12-07
ok its been a long time since i've posted anything about this. i gave up on trying to get the max res on this screen. it seems that it can only do it if the refresh is set to 75 but it also causes the screen to flicker like crazy so i'm just living with the default max res.

so if you have a 1280x800 max res screen and can't get it to do it, try upping the refresh to 75 and see if it will let you do it.

i have seen it where it will set the screen res but be at an incorrect ratio. everything gets stretched out. thats what gave me the idea to change the refresh.

so i did find a solution (refresh 75) but i can't take the flicker.
so i'll stick with what works.

---

### Post by mylo9000 on 2012-03-28
ok i did eventually get this working, its something to do with the horizontal and vertical refresh rate rages in xorg.conf.

```
Section "Monitor"
    Identifier  "My Monitor"
    HorizSync   30.0 - 125.0
    VertRefresh 50.0 - 160.0
EndSection
```

or somthing like that.
i'm not on that system right now so i don't know for sure.
but it works for me and i get the res i want.
can't complain.

---

