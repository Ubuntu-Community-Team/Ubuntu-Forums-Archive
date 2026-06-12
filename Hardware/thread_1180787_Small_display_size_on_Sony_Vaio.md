---
title: "Small display size on Sony Vaio"
date: 2009-06-07
forum: Hardware
---

### Post by rapper97 on 2009-06-07
There is a black approx. 4-centimetre black band around my laptop screen. I installed Xubuntu 9.04 on a Sony Vaio PCG-FX220 (helpfully aka the PCG-984L). The chipset for this machine is Intel's 82815.

Even in the BIOS, the display is confined to within this inch-and-a-half border. Windows XP, however, fills the screen just fine. I have looked at similar situations online recommend running [font="monospace"]dpkg-reconfigure xserver-xorg[/font], but this does nothing, and, until creating one with dexconf, my xorg.conf was blank. Within the GUI, I have the option for 640x480 and 800x600, and when I go from 800x600, the screen actually shrinks, i.e. the all-around letterbox gets bigger. However, when trying to boot up, I fed weird things into the kernel via GRUB and get an error, but upon trying to select a new resolution, the area of usable screen remains the same, with the context variously squooshed.

Ideally I would like to get something to feed to the kernel to make the display work right, so I could boot into a command line with the whole screen at my disposal, but at this point I'd just be content getting XWindows to work. [font="monospace"]815resolution[/font] is supposedly deprecated, replaced by [font="monospace"]xserver-xorg-video-intel[/font], but when I do run [font="monospace"]dpkg-reconfigure xserver-xorg[/font], it just gives configuration options for the keyboard. Should I install [font="monospace"]815resolution[/font], or the official Intel Linux drivers from, like, 2000? I ran across someone in the forum who looked like they'd had success with [font="monospace"]displayconfig-gtk[/font], but apparently that doesn't come with Xubuntu, either.

Suggestions, folks? I'll whine about no soundcard even being detected next week.

---

### Post by rapper97 on 2009-06-07
[SIZE="3"]**HOLY CRAP.**[/SIZE]

Give all your money to [this guy]("http://ubuntuforums.org/showthread.php?t=998642#postmenu_6489466").



I've spent literally *days* looking at multiple threads from multiple OSes and hardware configs with the same problem, unresolved. Happen to, as I'm giving up + getting ready to reinstal Windows, run across this thread. Yeah, *solved*.

---

### Post by VaioPengiun on 2009-06-21
Sorry, replied to wrong thread.

---

### Post by stantony1 on 2010-01-30
Oh my god.

Three hours researching the internet and here is the answer

[size=7]thank you!!![/size]

the admins should sticky this!!!

:p:p:p:p:p

---

### Post by EssGee on 2010-03-09
Yep, sticky this please

---

### Post by searchfgold6789 on 2011-03-24
THANK YOU SO MUCH! My laptop is now working :)

---

