---
title: "Ubuntu 12.04 Rocks on Lenovo Z570 !!"
date: 2012-07-09
forum: Hardware
---

### Post by foobantu on 2012-07-09
Hi,

Reposting the stuff I posted in compatibility list :)

[B]1)Version Of Ubuntu - Ubuntu 12.04 - Precise Pangolin  - 64 Bit
2)Laptop Maker - Lenovo
3)Laptop Model - Lenovo Z570.

[/B]Everything works and works good :smile:

Suspend/Resume works (This is the ONLY Linux flavour so far on which  this has worked), Changing brightness through laptop keys works, Fn+F2  works (screen off/on), my pppoe connectivity works.

Best part is, this is the only version and flavour of Linux on which my  battery works for 3.5 hours (and still counting...). That too while I am downloading cinammon,  installing it, browsing the net, downloading updates, installing themes  etc.

Best version of Linux I've used till date.

There are some laptop heating issues, but the temperature howers between  37C when Idle and 51C when all the activities mentioned above are going  on. So not like its crossing 60C or something like that.


I was really really bugged with Windows. It would randomly put messages stating my USB Ports are gone dead, give me blue screens etc etc...But one day, while I was backing up my data, it crashed, and somehow the backup too got messed up. That did it for me and I have been looking out for a better OS to move off to.

Tried a lot of Linux Flavours. All of them are great and amazing, but there wasn't a single distro that would have all the features...And thats when I got Ubuntu 12.04 and man does it rock !!

Thank you Ubuntu Developers, now I am finally able to completely move off Windows. :smile:

---

### Post by Lupajz on 2012-07-10
```
https://code.google.com/p/tpfanco/
```

could you please try this software for me ? :) and post some info if you can controll your fans and the temperatures ?

also what kernel are you running ?

---

### Post by foobantu on 2012-07-10
Hi,

Here's what I am using:

```
linuxguy@linuxbox:~$ uname -a
Linux linuxbox 3.2.0-26-generic #41-Ubuntu SMP Thu Jun 14 17:49:24 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
linuxguy@linuxbox:~$ 
```

Will try the software and let you know.

Did you try it yourself? Did it work for you? Or you want to use my laptop as a test ? ;)

---

### Post by Lupajz on 2012-07-11
This may sound evil but I really want to use your laptop as an testing machine :) 

Ty for that kernel message. Have you thought of updating kernel to 3.4.4 already ? I read many articles about the 3.5 so I am still waiting for me to go fully ubuntu :)

---

### Post by foobantu on 2012-07-11
Wow and No, I am not going to upgrade my system to 3.4.4.....

And no, I am not going to install that script. My laptop is fine as of now, and thats how I intend it to be. 

Suggest you try it first :)

---

### Post by Lupajz on 2012-07-13
And how about the thermal button and cinema one ? and special fn keys ? how many of them work ?

---

### Post by foobantu on 2012-07-15
Hi,

None of those keys work. :(

---

### Post by Lupajz on 2012-07-18
Anyone willing to support me ? :) Somebody with z570 could try this out until I get home from vacations to my z570 and try this :) 

New ideapad-laptop.c file : 

- fan control 
- special keys handling 

If it works ? IDK :D Some info from you guys would help :) should work on any kernel :)

> [http://kernel.ubuntu.com/~ikepanhc/ideapad/ideapad-laptop-dkms_3.6_all.deb](http://kernel.ubuntu.com/~ikepanhc/ideapad/ideapad-laptop-dkms_3.6_all.deb)

---

### Post by sumio on 2012-10-19
I updated my kernel release to "3.0.0-26-generic". I then disabled the nvidia graphics card in the bios. These two things, sorted out the fan issue. My computer went from operating at 60 C to this:

sumio@hyperdad:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +47.0°C  (crit = +98.0°C)
temp2:        +40.0°C  (crit = +126.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +47.0°C  (high = +86.0°C, crit = +100.0°C)
Core 0:         +47.0°C  (high = +86.0°C, crit = +100.0°C)
Core 1:         +43.0°C  (high = +86.0°C, crit = +100.0°C)

The only downside is that the brightness keys on the keyboard stopped working(FN + UP/FN + DOWN).

---

### Post by gdea73 on 2012-11-06
HOW does your suspend/hibernate work?
In a jealous way I find that mildly irritating.
I just installed 12.04.1 LTS on my Z575, nearly identical hardware, and the screen is unresponsive after suspend. I can still use it, but the screen (not backlight, entire screen receives no power/data) is non-functional.

/var/log/pm-suspend.log reports no errors other than the failure to resume WiFi by NetworkManager. That's unrelated, and it will also be irritating.

Oh, I just realized the Z570 uses an i5, not the A6-3420M that I have. That would explain it. Sorry for rant... :P

---

