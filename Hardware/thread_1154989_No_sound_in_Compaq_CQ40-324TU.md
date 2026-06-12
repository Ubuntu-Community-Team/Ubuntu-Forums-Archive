---
title: "No sound in Compaq CQ40-324TU"
date: 2009-05-10
forum: Hardware
---

### Post by cloudlor on 2009-05-10
any one have idea about this laptop? i have try to install ubuntu 8.10 and 9.04. all the hardware is working well, but have no sound at all. even i using the front speaker. urgent!!!

---

### Post by tantos on 2009-05-14
I'm using Ubuntu 9.04 at the same laptop and same problem as you. 
But now, its recovered already. Be sure you are using ALSA.

Follow this thread for your sound [http://ubuntuforums.org/showthread.php?t=1140667](http://ubuntuforums.org/showthread.php?t=1140667)

And for video, I change my xorg.conf in section device to :
```

Section &#8220;Device&#8221;
Identifier &#8220;Configured Video Device&#8221;
Option &#8220;AccelMethod&#8221; &#8220;uxa&#8221;
Option &#8220;EXAOptimizeMigration&#8221; &#8220;true&#8221;
Option &#8220;MigrationHeuristic&#8221; &#8220;greedy&#8221;
Option &#8220;Tiling&#8221; &#8220;false&#8221;
EndSection

```

---

### Post by azaini06 on 2009-05-29
i'm also using ubuntu 9.0.4 & also using ALSA.

but, where i sould key in all the "code" given? i'm a new user for ubuntu/linux. i know nothing about the ubuntu. somebody could help me what program should i use to key in the 'code' given?

---

### Post by goki75 on 2009-10-15
This worked for me on CQ40


options snd-pcsp index=-2
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=dell-m4-1
options snd-hda-intel enable_msi=1


use alsa in sound configuration

---

