---
title: "Upgrade to Natty - stylus keys refuse to work (again)"
date: 2011-07-19
forum: Hardware
---

### Post by ill66 on 2011-07-19
In [this ]("http://ubuntuforums.org/showthread.php?t=1705854#2")thread I solved my stylus problems on my Fujitsu Lifebook Tablet/Convertible with the help of Favux's [script]("http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_PC_Configuration#Fujitsu_T4210").
Now I upgraded to Natty and I still run the script, but the keys (right- and middleclick) won't work anymore. Leftclick (by 'tapping' with the pen tip), erasure and even pressure sensitivity are still there.
I played around with xsetwacom (I suck at commandline stuff) and I am able to set 'tip-tapping' to rightclick instead of leftclick, but both of the keys of the pen remain deaf, no matter what I do.

Any ideas...? :(

---

### Post by ill66 on 2011-07-19
I don't know, if I caused it with my desperate trials, but it turned out that there ARE right- and middleclick on the stylus keys. But they only will work after the stylus tip touches the screen - which is not cool, 'cause now there's a leftclick before every right- or middleclick.
With Maverick I could just hover the screen an press the stylus keys and it worked.

I also adjusted the abovementioned script corresponding to the [new parameters]("http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xsetwacom#Table_of_New_Parameter_Names"), but that didn't do anything either....

Update2:
Thanks to a chat buddy the problem is solved! :) For some reason the TabletPCButton (former TPCButton) was set "on". Now with "off" everythings just fine again.

---

### Post by Favux on 2011-07-19
Hi ill66,

It is suppose to work that way.  That is the TabletPCButton paramater on, which is the default for tablet PCs.  To get it to work like a graphic tablet i.e. in "hover" mode turn it off:
```
xsetwacom set "stylus device name" TabletPCButton "off"
```

The parameter names changed from Maverick to Natty, see:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xsetwacom](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xsetwacom)

---

### Post by ill66 on 2011-07-19
Hi, Favux!:KS

I was just wondering at the fact that it worked with the hovering pre-upgrade and didn't afterwards, even though I didn't change the script.

And like I wrote above I already changed the old parameters in the script and solved my problems. :)

Thanks for your work!

---

### Post by Favux on 2011-07-19
Oh, sorry I misunderstood.  I thought you still wanted hover mode.
> I was just wondering at the fact that it worked with the hovering pre-upgrade and didn't afterwards, even though I didn't change the script.
I think that's because they fixed a bug between the two versions of xf86-input-wacom.  So with the bug fix your tablet PC correctly got the default TabletPCButton "on" default.

---

