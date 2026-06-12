---
title: "Toshiba Tecra M2 issues - LCD goes off with DPMS, but won't turn on again"
date: 2005-10-14
forum: Hardware &amp; Laptops
---

### Post by OpMatt on 2005-10-14
just did a clean install of breezy on this laptop, it was running ubuntu before.
Now I've got the following problems with it:

1. the suspend to ram hangs the laptop before finishing suspend (the screen goes off but the cpu is still working at full speed, the side exhaust fan keeps on running).. i have to hit the power button for 5 seconds to make it go off. Then it is off, not suspended. This worked before on previous version of ubuntu.. I know i had to tweak some stuff in suspend script before it worked. but i've forgot what :-)

2. before the LCD screen would go off but the backlight would stay off.. really annoying. Now the screen and backlight go off on DPMS suspend, but there is no way of getting them on again, short of reboot - not really usefull.
This is the one biggest annoying thing..

3. suspend to disk is broken, but i never really cared for it

4. the SD card reader is not detected/doesn't work.. would be usefull but again not a big deal

5. the splash screen on boot displays briefly till "loading modules", then goes away and normal text booting screen appears.

6. sound - probably i need to play again with alsa to do software mixing.. if one app uses sound and another one wants to use it too it has to wait. (ie. playing music and running flash animation in web browser)

---

### Post by Technoviking on 2005-10-14
[QUOTE=OpMatt]just did a clean install of breezy on this laptop, it was running ubuntu before.
Now I've got the following problems with it:

1. the suspend to ram hangs the laptop before finishing suspend (the screen goes off but the cpu is still working at full speed, the side exhaust fan keeps on running).. i have to hit the power button for 5 seconds to make it go off. Then it is off, not suspended. This worked before on previous version of ubuntu.. I know i had to tweak some stuff in suspend script before it worked. but i've forgot what :-)
[/QUOTE]
Same problem with a Toshiba Satellite M30.

---

### Post by gregh on 2005-10-24
And with Toshiba A70 satellite

---

### Post by OpMatt on 2005-10-26
Additional things after few weeks of using the laptop with ubuntu:

* sometimes, and this is with DPMS and screesaver disabled, the screen would go off and can't be turned back on short of resbooting the computer. even alt-ctrl-backspace doesn;'t help
* if i close the lid and right away open it again, the above happens too.
I fixed it by disabling the lid script under acpi. ie, now the script doesn't run at all when i manipulate the lid

---

### Post by 23meg on 2005-11-07
Same here with a Toshiba Tecra M4. Very annoying.

---

### Post by Maverick911 on 2005-11-08
[QUOTE=OpMatt]just did a clean install of breezy on this laptop, it was running ubuntu before.
Now I've got the following problems with it:

1. the suspend to ram hangs the laptop before finishing suspend (the screen goes off but the cpu is still working at full speed, the side exhaust fan keeps on running).. i have to hit the power button for 5 seconds to make it go off. Then it is off, not suspended. This worked before on previous version of ubuntu.. I know i had to tweak some stuff in suspend script before it worked. but i've forgot what :-)

2. before the LCD screen would go off but the backlight would stay off.. really annoying. Now the screen and backlight go off on DPMS suspend, but there is no way of getting them on again, short of reboot - not really usefull.
This is the one biggest annoying thing..

3. suspend to disk is broken, but i never really cared for it

[/QUOTE]

I've got the same problem on my HP zx5000:???:

---

### Post by digikim on 2005-11-10
Hello all!

[QUOTE=OpMatt]2. before the LCD screen would go off but the backlight would stay off.. really annoying. Now the screen and backlight go off on DPMS suspend, but there is no way of getting them on again, short of reboot - not really usefull.
This is the one biggest annoying thing..[/QUOTE]

I have enqountered the same problem with my Toshiba Portégé M300 both when doing hibernate and sleep. I have tried to solve the problem with google etc, but haven't find any solution sofar.


Things I have tested (I'm not a huge Linux guru, so this has been more randomly testing everything that I can think about):

- vbetool dpms on    --- doesn't help
- xset dpms force on  --- doesn't help
- tested radeontool -- doesn't help since the Toshiba is not using an ATI video card
- tried to debug /etc/acpi/resume.sh, but sofar I do not know which command turns the backlight off (might be when the video card's state is restored ("vbetool
vbestate restore <$VBESTATE")??)

I haven't tested whether I have also the other problems OpMatt described.

I would be very thankfull for any ideas, suggestions and comments you have how to solve the problem!

Regards,
Kim

---

### Post by digikim on 2005-11-14
Hello,

[QUOTE=digikim]I have enqountered the same problem with my Toshiba Portégé M300 both when doing hibernate and sleep. I have tried to solve the problem with google etc, but haven't find any solution sofar.[/QUOTE]

The solution might be the following:

I found a little tool called toshset which allows you to manipulate many kind of settings of your Toshiba laptop. See "man toshset" for more information. One option is "-bl on|off", which sets the backlight on (or off).

Add the following line as the _second_ line of /etc/acpi/resume.sh:

```
/usr/bin/toshset -bl on

```
The result should be something like this:
```

#!/bin/bash

/usr/bin/toshset -bl on

# Post the video card
if [ x$POST_VIDEO = xtrue ]; then
  vbetool post
fi
```

I have tested the hibernate with this addition and sofar it seems to work... No guarantee provided, however. :)

Regards,
Kim

---

### Post by spitfire_aus on 2005-11-22
[QUOTE=digikim]

Add the following line as the _second_ line of /etc/acpi/resume.sh:

```
/usr/bin/toshset -bl on

```
[/QUOTE]

That worked for me!! But then again i'm running a Toshiba Laptop.

Interestingly enough my when my LCD had no backlight on resume I was able to hold the little button used to sense when my screen is closed for a few seconds and then when I let go the backlight would come back on. 
Strangly enough, that mean't that I had to enter my password into TWO lock screens for some reason?! 
This might help you non-toshiba guys?

But now thanks to digikim I only have to do it once =D.

Thanks!
Glen

---

