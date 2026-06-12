---
title: "Want to make a Dell m1330 custom kernel"
date: 2008-06-14
forum: Hardware
---

### Post by atlas95 on 2008-06-14
Hello,
I search help of Dell m1330 owner and which know well how to do a custom kernel.
I search how to improve performance/boot time for my laptop.
I know a lot of people have this laptop yet and I wish you will be able to help me.


I hope you can help me/work with me, I have allready made a kernel but this was in gentoo, at my start with gentoo a lot of years before.

I'm french, sorry if my english isn't very good, i really hope my idea will interest you.

Best regards

Cyril

---

### Post by sdennie on 2008-06-14
I have used this guide in the past and it works well: [http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

Also, if you have the XPS m1330 with the NVidia 8400M GS, you'll need to manually install the NVidia drivers for your new kernel.  I run a custom kernel (coincidentally on an XPS m1330) and I generally just download the nvidia drivers from here: [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

Having said all that, I don't know how much extra performance you'll get from compiling your own kernel (in fact, if you are using the 8400M GS and compiz, 2.6.25 series kernels will probably show a drop in performance).  I would really only recommend it if you have some specific need that the default Ubuntu kernel doesn't provide.

---

### Post by atlas95 on 2008-06-15
I want to do that because I have see, on the eeepc ubuntu project, hmm this link [http://forum.eeeuser.com/viewtopic.php?id=30390](http://forum.eeeuser.com/viewtopic.php?id=30390)

we can win a lot of second while booting, I want to win boot time before all.

I'm using the last driver nvidia too, for have function+f8 key working ^^

---

### Post by sdennie on 2008-06-15
If your primary concern is with boot time, my suggestion would be to simply stop shutting it down.  It sounds like you have the same machine as I do and I just suspend the machine when I'm not using it (it can stay suspended for several days on a full battery).  Check out System->Preferences->Power Management and, on the first two tabs set "When laptop lid is closed" to "Suspend".  That way whenever you close your laptop, it will suspend and whenever you open it back up, it will be exactly how you left (it takes about 5 seconds for it come back up completely).

---

### Post by atlas95 on 2008-10-07
Bump !

---

