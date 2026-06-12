---
title: "Sony Vaio P - Complete Installation Guide"
date: 2010-05-01
forum: Hardware
---

### Post by chi_kuong on 2010-05-01
Please could anyone make a complete hardware driver installation guide for the Sony Vaio P?

I am totally new to Linux and althought most things work straigh away on the new Ubuntu 10.04 netbook remix on my Vaio P. But the graphic and very slow and I can't even get Skype and Flash plug-in to work. 

I could really want to use Ubuntu as I am sick of the pre-installed Vista. However at this rate I am not getting the things to work properly..

Please could any expert make a guide so that all Sony Vaio P users could benefit?

Many Thanks!

---

### Post by tomoki.taniguchi on 2010-05-04
I recently tried installing 10.04 netbook edition on my Vaio P.
The boot/shutdown time was amazing compared to the XP i am running currently.
Like you mentioned most things seemed to work right out of the box but the following didn't work for me:

1) there is no way to install the needed graphics driver under lucid currently
2) the system will suspend but would not properly recover
3) the system will not power down during hibernation
4) LCD brightness buttons didn't work

as far as i could can remember everything else seemed to work fine.

even though shutdown took under 5 sec for me,
not being able to suspend or hibernate on a netbook was unaccpetable for me.

so i decided to try karmic (9.10) netbook remix.
i was surprised and happy to find that even though karmic is an older release
suspend and the LCD brightness control buttons now works properly.
hibernate still doesn't work.  the graphics is slow... slower even than lucid at first.
but following an online guide on how to install the driver, i am getting decent speeds for 
my browsing needs.  so i am sticking with karmic UNR for now.

I don't understand why things that worked on karmic no longer works under lucid but ... oh well i can't complain.

If you decide the same way i did and stick with karmic for now...
this guide will help you with installing the PSB driver for karmic.
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo)

-Tomoki

---

### Post by quinthar on 2010-06-15
Does anyone else have any feedback on this?  I'm also thinking of getting a P, and I'd like to install 10.04 on it.  (I currently run 8.04 on a Sony TZ.)  Suspend is pretty important, however, and while I remember it being a pain to get working in 8.04, ultimately I did get it working.  Anybody get it to work?

Thanks!

-david

---

### Post by krestfallen on 2010-06-16
well i didn't try to hassle with 10.04 as i saw that the poulsbo driver works best with 9.10...

even in 9.10 there are a lot of problems but i made a summary tutorial of everything that i noticed except GPS (WLAN at constant rates, GMA500 with compiz opengl games and video, sleep/hibernate-fix when wlan on..)

everything works like a charm now and i also don't notice any system freezes anymore!

i posted it here:
[http://1kleinerbeitrag.blogspot.com/2010/06/ubuntu-910-on-sony-vaio-p-p11z-fully.html](http://1kleinerbeitrag.blogspot.com/2010/06/ubuntu-910-on-sony-vaio-p-p11z-fully.html)

edit: well, i can't get the vga port working. when i plug it in and immediately start xrandr i can see the external monitor. when i run it again, it's gone... tried so many xorg.conf configurations with no luck.

---

### Post by alones on 2010-06-26
Hi,

I had an issue with suspend/resume as well.
Manage to fix it, details here:

[http://ubuntuforums.org/showthread.php?t=1517137&highlight=lucid+sony](http://ubuntuforums.org/showthread.php?t=1517137&highlight=lucid+sony)

---

### Post by crapufish on 2010-07-08
> **krestfallen said:**
> 
i posted it here:
[http://1kleinerbeitrag.blogspot.com/2010/06/ubuntu-910-on-sony-vaio-p-p11z-fully.html](http://1kleinerbeitrag.blogspot.com/2010/06/ubuntu-910-on-sony-vaio-p-p11z-fully.html)


Hi!

It seems that the link to the WWAN solution [http://www.logic.at/people/preining/software/sony-laptop_-series-0.9np5.tar.gz](http://www.logic.at/people/preining/software/sony-laptop_-series-0.9np5.tar.gz) is broken; can you point us to another URL or tell us what to Google exactly?

Thank you very much!

Edit: Of course, if you go [http://www.logic.at/people/preining/software/](http://www.logic.at/people/preining/software/) you can see what you need!

---

### Post by ldrn on 2010-08-01
> **krestfallen said:**
> well i didn't try to hassle with 10.04 as i saw that the poulsbo driver works best with 9.10...
<snip>
i posted it here:
[http://1kleinerbeitrag.blogspot.com/2010/06/ubuntu-910-on-sony-vaio-p-p11z-fully.html](http://1kleinerbeitrag.blogspot.com/2010/06/ubuntu-910-on-sony-vaio-p-p11z-fully.html)

I tried 10.04... and ended up switching back to Karmic; I was able to get suspend working and some acceleration, but no compiz. :) I'd done Karmic on the Vaio P once before, but your guide was great and made it very easy! Thank you. 

I think because I used the lpia version of 9.10 lpia, I also had to do the following:
sudo apt-get install psb-kernel-source
... in order to get the video to work. I also settled on adding vga=0x367 to the kernel line and changed mem to mem=2000MB (the recommended number for 10.04) after that, and it seems to work fine.

I wasn't able to get suspend/resume to work until I updated everything -- it worked great for me with the latest karmic lpia kernel. 

I also used this script to get the middle mouse button to scroll:
```

#!/bin/sh
STICKNAME=`xinput --list | grep Mouse | sed -e 's/^.*id\=//' | sed -e 's/\t.*//' | awk '{gsub(/^[ \t]+|[ \t]+$/,"");print}'`
xinput set-int-prop "$STICKNAME" "Evdev Wheel Emulation" 8 1 
xinput set-int-prop "$STICKNAME" "Evdev Wheel Emulation Button" 8 2

```

Anyway, I hope all this helps someone else. :)

---

### Post by gacko on 2010-08-17
hey nice one (middle mouse to scroll), do you mind if i update my installation guide with this?

---

### Post by ldrn on 2010-08-17
Thank you, and not at all -- there's probably a way to do it with fdi files that doesn't have to be run each reboot, but that works for me. :)

---

