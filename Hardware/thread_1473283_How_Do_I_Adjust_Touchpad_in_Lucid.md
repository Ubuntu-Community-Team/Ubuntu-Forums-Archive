---
title: "How Do I Adjust Touchpad in Lucid?"
date: 2010-05-05
forum: Hardware
---

### Post by clevertomato on 2010-05-05
[FONT=Arial][SIZE=4]Does anyone know how I can adjust my Synaptics Touchpad in Lucid? In Karmic I did it via_ _[/SIZE][/FONT][FONT=Arial][SIZE=4][http://brettshaffer.com/blog/linux/m...n-ubuntu-9-10/]("http://brettshaffer.com/blog/linux/multi-touch-touchpad-in-ubuntu-9-10/")  which uses [/SIZE][/FONT]
[FONT=Courier New][SIZE=4]/etc/hal/fdi/policy/11-x11-synaptics.fdi[/SIZE][/FONT]
[FONT=Arial][SIZE=4]but I'm told Lucid doesn't use HAL. So where does that leave me for adjusting my touchpad?[/SIZE][/FONT]

---

### Post by zaphod777 on 2010-05-05
depends on what you need to do but I have always used 
system->preferences->mouse

---

### Post by clevertomato on 2010-05-07
Things like jumpy cursor threshold, resizing the sensitive area of the touchpad, adjusting the pressure sensitivity required to convey a click. I've known about the normal touchpad settings... all two or three of them. I'm talking about many more other settings that I used to be able to set with the Synaptics Touchpad fdi file.

---

### Post by zaphod777 on 2010-05-07
hmm after bit of digging around I found this

[http://superuser.com/questions/74024/two-finger-scrolling-with-ubuntu-9-10-samsung-nc10/114227#114227](http://superuser.com/questions/74024/two-finger-scrolling-with-ubuntu-9-10-samsung-nc10/114227#114227)

looks like you can use synclient possibly.

---

### Post by clevertomato on 2010-05-07
Thanks for digging around and finding that, but synclient won't work for me in Lucid. I get an error about shared memory not being enabled, but I've followed instructions from the link in my original post to enable it without success. Synclient and the fdi file works fine for me in Karmic but all that does not work in Lucid.

---

### Post by AnotherMuggle on 2010-05-07
[http://www.bhagwad.com/blog/2010/technology/alps-synaptics-touchpad-configuration-in-lucid-lynx-ubuntu-10-04.html](http://www.bhagwad.com/blog/2010/technology/alps-synaptics-touchpad-configuration-in-lucid-lynx-ubuntu-10-04.html)

Follow the section "Using .conf files in xorg.conf.d"

Works flawlessly for me.

---

### Post by clevertomato on 2010-05-07
Awesome. I'll try it. It looks like just what I need. Thanks.

---

### Post by clevertomato on 2010-05-17
I never got around to trying the .conf files, but in the meantime I found something about xinput. This worked for me. I made a file with xinput commands that I wanted, made it executable, and added a startup application for it. Sample file:

```
#!/bin/bash
#
# list of synaptics device properties http://www.x.org/archive/X11R7.5/doc/man/man4/synaptics.4.html#sect4
# list  current synaptics device properties: xinput list-props '"SynPS/2 Synaptics TouchPad"'
#
sleep 5 #added delay...
# xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Device Enabled" 8 1
# xinput --set-prop --type=int --format=32 "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Pressure" 4
# xinput --set-prop --type=int --format=32 "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Width" 9         #     Below width 1 finger touch, above width simulate 2 finger touch. - value=pad-pixels
xinput --set-prop --type=int --format=32 "SynPS/2 Synaptics TouchPad" "Synaptics Area" 0, 0, 0, 4800 # set sensitive area of touchpad - value=left, top, right, bottom
xinput --set-prop --type=int --format=8  "SynPS/2 Synaptics TouchPad" "Synaptics Edge Scrolling" 1 0 0       #     vertical, horizontal, corner - values: 0=disable  1=enable
xinput --set-prop --type=int --format=32 "SynPS/2 Synaptics TouchPad" "Synaptics Jumpy Cursor Threshold" 300 #     stabilize 2 finger actions - value=pad-pixels
# xinput --set-prop --type=int --format=8  "SynPS/2 Synaptics TouchPad" "Synaptics Tap Action" 0 0 0 0 1 2 3   # pad corners rt rb lt lb tap fingers 1 2 3 (can't simulate more then 2 tap fingers AFAIK) - values: 0=disable 1=left 2=middle 3=right etc. (in FF 8=back 9=forward)
# xinput --set-prop --type=int --format=8  "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Scrolling" 1 0   #     vertical scrolling, horizontal scrolling - values: 0=disable 1=enable
# xinput --set-prop --type=int --format=8  "SynPS/2 Synaptics TouchPad" "Synaptics Circular Scrolling" 1
# xinput --set-prop --type=int --format=8  "SynPS/2 Synaptics TouchPad" "Synaptics Circular Scrolling Trigger" 3

exit
```

---

### Post by VeeDubb on 2010-05-17
The one thing I can't figure out with all this xinput stuff, is how to enable a three finger tap.  I know my touchpad supports it, and I know that even when it's configured, it can be a pain to actually do it successfully, but I'm running out of things on my netbook that don't work as expected, and I need to tinker. :)

---

