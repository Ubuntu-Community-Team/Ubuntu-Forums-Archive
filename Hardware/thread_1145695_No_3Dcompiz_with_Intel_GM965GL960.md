---
title: "No 3D/compiz with Intel GM965/GL960"
date: 2009-05-01
forum: Hardware
---

### Post by Just64 on 2009-05-01
I have tried all... and nothing works:

```
*-display:0 UNCLAIMED
             description: VGA compatible controller
             product: Mobile GM965/GL960 Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list
             configuration: latency=0
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile GM965/GL960 Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
```
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/359392](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/359392)
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/363821](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/363821)

Someone with the same problem could fix it?

---

### Post by asuastrophysics on 2009-05-07
i have no clue man. nobody seems to have a fix for this, and it doesn't look like anyone's even filed a bug report for it. 

i'm just about to give up on 9.04. i have no compiz and it wasn't even a good upgrade. 

i think i'll permanently downgrade to 8.10. then i'll just manually update the apps installed. that balloon style notification system isn't worth all these problems :(

---

### Post by asuastrophysics on 2009-05-07
and the bug report doesnt even describe the problem. they just said compiz is disabled. it's a lot more than just disabled. they've totally broken it. i already cleared compiz' blacklist. did absolutely nothing. 

is there a clear and logical reason out there for why compiz isn't running?

it's not because it's blacklisted under /usr/bin/compiz. i checked that and it's commented out. 

it's not because i need compiz to skip the checks. i already did that.
what more can i as an end-user do to fix this problem?

are there any other bug reports out there or are those two the only ones pertaining to our case?

---

### Post by digitalbenji on 2009-05-14
I just wrote a quick script to fix this.  Do this:
```
vi intel.jaunty.fix
```  and paste this:
```

#!/bin/bash
if [ -e ~/.compiz ]
	then echo "SKIP_CHECKS=yes" >> ~/.compiz/compiz-manager
	else 
		mkdir ~/.compiz
		echo "SKIP_CHECKS=yes" >> ~/.compiz/compiz-manager
fi
compiz-manager &

```
If you don't know vi, use another editor, or after you paste hit ESC then type :wq

Then do:```
chmod +x intel.jaunty.fix
./intel.jaunty.fix
```

That worked and started compiz for me.

---

### Post by ndmaque on 2009-05-14
> **digitalbenji said:**
> I just wrote a quick script to fix this.  Do this:
```
vi intel.jaunty.fix
```  and paste this:
```

#!/bin/bash
if [ -e ~/.compiz ]
	then echo "SKIP_CHECKS=yes" >> ~/.compiz/compiz-manager
	else 
		mkdir ~/.compiz
		echo "SKIP_CHECKS=yes" >> ~/.compiz/compiz-manager
fi
compiz-manager &

```
If you don't know vi, use another editor, or after you paste hit ESC then type :wq

Then do:```
chmod +x intel.jaunty.fix
./intel.jaunty.fix
```

That worked and started compiz for me.

just tried aove but it locked up, i already did the blacklist thing (Lenovo T61 Intel GM965), it worked yesterday and also today when i showed it off to the windoze users at work, i locked the screen for lunch and it failed to compiz again after login.

I had already installed the compiz manager which still works but no effects until i run compiz in terminal...
 
...but when i do it hangs at the last bit gtk-window-decorator it locks terminal and snaps any apps to the top of screen, i can often cube rotate and fire sometimes, yesterday i simply killed the hung terminal all was well, but not since.

---

### Post by ndmaque on 2009-05-14
aha - i had to go back into system > appearance > visual effects and enable Extra 

for some reason it had reverted to Normal, i didn't need to run compiz or the intel.jaunty.fix 

hope this helps someone

haven't sussed out how to get the flame effect on window close yet but that is my next job.

Bye bye micro$oft

---

