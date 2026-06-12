---
title: "keyboard doesnt work proberly Acer Travelmate Laptop"
date: 2006-06-03
forum: Hardware &amp; Laptops
---

### Post by gandalf100 on 2006-06-03
Hi!
I have installed Kubuntu 6.06. Most time it is ok, but sometimes, when i press a key i dont get a rrrresult and sometimes it makes too many resuuuuuults - the text you see is the performance of my keyboard.
I had the same problem with Xubuntu 6.06, i didnt try Ubuntu 6.06.
The keyboard is the kkkkkeyboard of my laptop Acer Travelmate 2303 i tryed many linuxdistributions but had never a problem like this. The keyboard works perffffect with Ubuntu 5.10 also with Suse 10.0, Suse10.1, Ubuntu 5.04, Kanotix, Mandriva...  
Is this a driverproblem? Where can i find the right driver?

---

### Post by wblancqu on 2006-06-03
Same problem with my Acer TravelMate 4000. Not repeating letters, but skipping them sometimes. Might be kernel-related? Didn't have the problem with 5.10.

---

### Post by gandalf100 on 2006-06-04
Im not sure, but i think i can supress the repetitions of letters, when i activate the touchpad of the laptop (?) but it doesnt prevent from skipping letters sometimes. I found this here: [http://www.thorstenhaas.de/toshiba2410/](http://www.thorstenhaas.de/toshiba2410/)

Bad news about the keyboard. The keyboard controller is buggy somehow. It spuriously sends keyrelease-events twice, which leads to double-letters. This problem is well-known in the Toshiba-world and has even been reportet to happen with M$-Windoze98 on older laptops. I agree, this sucks!
This issue has been discussed on one of the linux-kernel mailing lists. See here. I would like to quote Alan Cox who said on these kind of hardware bugs: 
"Well there is one wya to help stop that, which is not to fix them."
The good news: there are five solutions to this. 
Patch the kernel. 
Additional entry [13-Jan-2003]: Linux 2.4.21pre3-ac3 does contain a kernel patch now. So maybe the next stable kernel release will incorporate the cure for this problem.
Patch the XFree-source
Disable the Xkb extension in your XF86Config - a useful one.
Use Xkb extension with AccessX to suppress keyboard bouncing - another useful one.
Use Xkb extension with xkbset to suppress keyboard bouncing - yet another useful one.
Patching would mean we have to patch source on every release of a new kernel or XFree version. It's up to you if you want to burden this on yourself. Contact me for a kernelpatch. A nicer solution is disabling the Xkb extension. Notice: this will lead to a default US-keyboard! This is easy to change and has to be done once only. By the way: nice opportunity to implement your own needs into your keymap, e.g. mapping the windoze-buttons to something useful. ;) If you do not want to do this you can also use AccessX or xkbset to suppress the keyboard-bouncing.

---

### Post by gandalf100 on 2006-06-04
OK. its an official bug -  Bug #37472:
[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/37472](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/37472)

---

