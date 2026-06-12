---
title: "Shoud I change my Kernal?"
date: 2006-04-01
forum: Hardware &amp; Laptops
---

### Post by Clunsford on 2006-04-01
I got a IBM T30, this all the info on the prc i found on the net,
CPU 1.8GHZ P4     (wow informative...)

what i wanted to know, should i be using the 686 kernal?

Or should i continue to waft in the n00bE darkness of my pitiful existance!

but seriously, should i install the 686 kernal instead of the 386 kernal?  I understant that the 386 kernal is like the lowest common denominator kernal: But is changing kernals somthing best left to linux gods and not novice mortals like myself? 

and last but not least, I just installed Drake5... would I be adding complication to an already more complicated OS?

---

### Post by Clunsford on 2006-04-01
Intel(R) Pentium(R) 4 Mobile CPU 1.8GHz (1196.13-MHz 686-class CPU)

Confermed 686

---

### Post by teet on 2006-04-01
I'm pretty sure, that as long as you don't remove the old kernel then you should be safe.  If something goes wrong, you should be able to just choose the old kernel from your grub menu.

I'm running a 686 kernel on my "ancient" P3 1.06 ghz laptop and it works fine.  Although I can't tell that much of a difference between it and the old 386 kernel.

-teet

---

### Post by Clunsford on 2006-04-01
seemes to be working just fine'  thanks!

---

### Post by StkvDba on 2006-04-01
A newbie myself, I followed luca_linux's [HOWTO: Kernel compilation]("http://www.ubuntuforums.org/showthread.php?t=43065").  No problems!  Good luck!

---

### Post by adamkane on 2006-04-01
"HOWTO: Kernel compiliation" shows you how to install the latest version 2.6.12. 

If you don't mind a somewhat less than latest-most-bleeding-edge version 2.6.12, then:

```

sudo apt-get intall linux-686 linux-image-686 linux-headers-686 linux-restricted-modules-686

```

Reboot.

GRUB will automatically boot into the new kernel.

If you have problems, you can edit GRUB to boot into the correct kernel:

```

sudo  gedit /boot/grub/menu.lst

```

---

### Post by Skarjoko on 2006-04-01
[QUOTE=adamkane]"HOWTO: Kernel compiliation" shows you how to install the latest version 2.6.12. 

If you don't mind a somewhat less than latest-most-bleeding-edge version 2.6.12, then:

```

sudo apt-get intall linux-686 linux-image-686 linux-headers-686 linux-restricted-modules-686

```

Reboot.

GRUB will automatically boot into the new kernel.

If you have problems, you can edit GRUB to boot into the correct kernel:

```

sudo  gedit /boot/grub/menu.lst

```[/QUOTE]


Will this work if I have 386 already installed, and want to change to 686?

By the way, I have a Pentium 3 700 MHz on an old Dell Latitude L400. Should I change to 686, or leave it as 386?

---

### Post by adamkane on 2006-04-01
686 is for Pentium Pro / II / III / IV.

386 is for ancient Pentiums and 486es.

So go ahead and install 686, and report whether you notice any improvement.

---

### Post by Skarjoko on 2006-04-01
Thanks. Will try now....

Hope this works. I'll edit this post when it's done.

EDIT: That was quick. Well there is a slight difference with the performance...everything runs just a tad bit faster, but its barely noticable. Still, in the end it really helps. Thanks!

---

### Post by Clunsford on 2006-04-06
Thanks I just did it with the synaptic 686 kernal package i didn't know about the other parts... ill make sure to add them right away.

btw side question, what happens if you install new kernal and don't reset right away?

---

### Post by teet on 2006-04-09
> btw side question, what happens if you install new kernal and don't reset right away?

Absolutely nothing to my knowledge.  Since you're not uninstalling the kernel that you're currently running, nothing "bad" will happen.

> 
EDIT: That was quick. Well there is a slight difference with the performance...everything runs just a tad bit faster, but its barely noticable. Still, in the end it really helps. Thanks!

[http://ubuntuforums.org/showthread.php?t=107856&highlight=tweak+ext3](http://ubuntuforums.org/showthread.php?t=107856&highlight=tweak+ext3)

This tweak helped my P3 1.06 ghz laptop more than anything.  I could tell a noticeable difference in the speed with which files opened and such.  It's a little more risky to do, but I haven't had any problems with it.    

-teet

---

