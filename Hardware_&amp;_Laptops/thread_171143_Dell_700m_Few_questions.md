---
title: "Dell 700m Few questions"
date: 2006-05-06
forum: Hardware &amp; Laptops
---

### Post by DarkManX4lf on 2006-05-06
ok i have a dell 700m with an intel 2200 wireless adapter,a nd i got the wireless to work but the icon doesnt show in the system tray...how do i get the wifi icon to show?

and also how do i set the resolution of my display? it only lets me select 1024x768, in windows i can support upto 1280x960...

---

### Post by paritybit on 2006-05-06
[http://www.ubuntuforums.org/showpost.php?p=947920&postcount=4](http://www.ubuntuforums.org/showpost.php?p=947920&postcount=4)
That might help with your resolution problems.... Works on my 710m.
As for wifi, I am not so sure.

---

### Post by DarkManX4lf on 2006-05-06
ok i downloaded the .deb package and i followed the instruction on that post, but when i do 

sudo dpkg -i 915resolution_0.5.2-3_i386.deb

it says this
```

(Reading database ... 63899 files and directories currently installed.)
Preparing to replace 915resolution 0.5.2-3 (using 915resolution_0.5.2-3_i386.deb) ...
Unpacking replacement 915resolution ...
dpkg: dependency problems prevent configuration of 915resolution:
 915resolution depends on libc6 (>= 2.3.6-6); however:
  Version of libc6 on system is 2.3.5-1ubuntu12.5.10.1.
dpkg: error processing 915resolution (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 915resolution

```

how do i get this to work?

---

### Post by paritybit on 2006-05-06
Sorry forgot about checking that, this package here should work.
[http://www.freshnet.org/debian/hoary/915resolution_0.5-2_i386.deb](http://www.freshnet.org/debian/hoary/915resolution_0.5-2_i386.deb)

---

### Post by DarkManX4lf on 2006-05-06
that link doesnt work

---

### Post by paritybit on 2006-05-07
Works fine here.
How about instead of saying "it doesn't work" try and google the solution becuase there is a heap of help on this topic.
[http://users.skynet.be/thomasvst/linux-on-laptop/](http://users.skynet.be/thomasvst/linux-on-laptop/)
That may help you, hope think link works.

---

### Post by DarkManX4lf on 2006-05-07
[QUOTE=paritybit]Works fine here.
How about instead of saying "it doesn't work" try and google the solution becuase there is a heap of help on this topic.
[http://users.skynet.be/thomasvst/linux-on-laptop/](http://users.skynet.be/thomasvst/linux-on-laptop/)
That may help you, hope think link works.[/QUOTE]

thanks for your help man, i figured out what i had to do, the 915resoultion wasnt the right one to use i searched around and i foudn that i needed the 855resolution package i installed that, and i followed [this guide]("http://www.ubuntuforums.org/showthread.php?t=24923&highlight=855resolution")

and it works

thanks again

---

### Post by paritybit on 2006-05-07
That's good. Try to remember to upgrade to 915resolution when you uprade to dapper in a few months. It should work then and from what I have read is an important upgrade to 855resolution.
Glad to see you widescreen is working now though!

---

