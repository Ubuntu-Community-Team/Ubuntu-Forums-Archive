---
title: "agpgart/nvagp"
date: 2004-12-26
forum: General Help
---

### Post by fuzzix on 2004-12-26
Disclaimer: X config during late December festivities is not recommended ;)

Just wondering if I should disable agpgart to use the NvAGP module or should I leave it as is (Option "NvAGP" "2" in Section "Device" to use any available module(I think)).

The reason I ask is nvclock reports supported AGP speeds as 1x, 2x and 4x. The card supports up to 8x and I'm not sure about the bus (I didn't build this box - it's ex-office hardware but decent enough despite :) ) Is nvclock reporting the possible bus speeds or what it detects as possible rates for the card? The max I've been able to get is 2x.

Apologies for incoherence/rambling - I can clarify anything that isn't well put here as soon as I'm more... balanced :)

---

### Post by diebels on 2004-12-27
You should try "NvAGP" "1"
It sometimes works better.
Maybe you need to blacklist the agpgart module too.

---

### Post by fuzzix on 2004-12-27
[QUOTE=diebels]You should try "NvAGP" "1"
It sometimes works better.
Maybe you need to blacklist the agpgart module too.[/QUOTE]

Viewing dmesg output (for "NvAGP" "1") suggests that nvagp can't load due to agpgart and the performance is terrible. Is blacklisting it just a matter of adding module names to /etc/hotplug/blacklist?

Thanks.

---

### Post by diebels on 2004-12-27
I've made my own blacklist file.
/etc/hotplug/blacklist.d/myblacklist
and put agpgart and intel_agp in it.
Not sure if that's the correct way to do it. It works anyway. And will not get overwritten by updates.

---

### Post by nocturn on 2005-01-06
As I posted in another thread on this:

I have file a bugreport for this one:
[https://bugzilla.ubuntu.com/show_bug.cgi?id=5242](https://bugzilla.ubuntu.com/show_bug.cgi?id=5242)

As a workaround, I moved the previously loaded agp modules to .saved files.
This works nicely (although it is un unclean fix).

---

### Post by rutty on 2005-01-06
OK, I have this problem too. Have set "NvAGP" "1" but it still shows as disabled and my Half Life 2 performance is rubbish. Will attempt this blacklist thingy later when I get home.

Thanks - am new to Ubuntu and I'm very impressed so far - this is the only issue I've found with the distro - far easier to install than any other I've tried :)

---

### Post by nocturn on 2005-01-06
[QUOTE=rutty]OK, I have this problem too. Have set "NvAGP" "1" but it still shows as disabled and my Half Life 2 performance is rubbish. Will attempt this blacklist thingy later when I get home.

Thanks - am new to Ubuntu and I'm very impressed so far - this is the only issue I've found with the distro - far easier to install than any other I've tried :)[/QUOTE]

Blacklisting did not work for me (as for most on these threads).
Until it is fixed, I recommend moving the kernel modules...

---

### Post by rutty on 2005-01-06
Hmmm, no sign of the agpart module in /etc/modules :(

Looks like I've got some reading to do....

---

### Post by rutty on 2005-01-06
Hmmm, fixed it by replacing "NvAGP" with "sisAGP" as per [THIS THREAD](http://www.ubuntuforums.org/showthread.php?t=6237&page=1&pp=10)  :)

Well, it's much, much better than it was before. I suppose there's still plenty of juice to get out of the old nVidia driver yet ;)

---

### Post by rutty on 2005-01-06
Hmmm, it is much better now, but it still looks a bit odd in sections, like in stairwells where the graphics tends to go wonky, but otherwise the best I've had this in Linux :)

Still nowhere near up to the Windows standard though - I have plenty to learn where Linux config is concerned though, so we'll see where I go next....

---

### Post by jbh on 2005-01-08
AGPGART is compiled with the kernel, so I have no way to kill it to enable NvAGP.I d/l an ubuntu source 2.6.10 image, checked it out in make xconfig/make menuconfig and you can't set /dev/agpgart to be a module (m). the only work around I could find was to do the kernel config, then manually edit the config file and put the 'm' option back in. compiling now, will see if this works.

---

### Post by jbh on 2005-01-08
failed. still loads AGPGART. oh well at least i have a custom kernel now. and glxgears works

---

### Post by rutty on 2005-01-09
Heh, I've always found the best way for me to kill my distro is to attempt to recompile the kernel ;)

Oh well, glxgears works for me too, but I'm hardly getting fantastic results from my nVidia card. I can always play Half Life 2 in W******s until there's a fix for this, or I may have another go with gentoo - I have it already installed in another partition and the learning is fun :)

I'm going to stick with Ubuntu as my main Distro for the time being though - it's the most stable I've tried so far and I'm on my fourth new kernel  :)

---

