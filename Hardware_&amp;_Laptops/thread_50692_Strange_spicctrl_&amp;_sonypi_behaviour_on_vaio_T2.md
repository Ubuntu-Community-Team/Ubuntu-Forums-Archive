---
title: "Strange spicctrl &amp; sonypi behaviour on vaio T250P"
date: 2005-07-21
forum: Hardware &amp; Laptops
---

### Post by thomas.hansen on 2005-07-21
m getting some strange behavior from the spicctrl utility!
 I load the sonypi module, which seems to go well, but when i ry to set my screen brightness using spicctrl it doesnt change the brightness of my screen; instead it changes teh brightness of my power button!
 
 The power button on teh T series is transparent and glows green when powered on...with "spicctrl -b VALUE" i can change how bright it glows....i mean its kind of cool, cause i had no idea teh power button could glow in different strengths...but really i would like to chaneg my screen brightness instead
 
 has anyone tried runing ubuntu on a vaio t series and gotten this to work? everything else works just fine!
 
 Thomas

---

### Post by thomas.hansen on 2005-07-24
I figured out the problem and figured I would leave the solution in case anyone ever runs into a similar problem.

The sonypi driver is not what you want to set the screen brightness, it only works on "most" sony vaios.  But the author of the sonypi module alsohas a nother driver called aony_acpi, which is what you want in case  sonypi doesnt work.

you can get it here: [sony_acpi](http://popies.net/sonypi/sony_acpi.tar.gz) 

the site describing both modules is here [http://popies.net/sonypi/](http://popies.net/sonypi/) 
The page does link to the sony_acpi module on teh bottom of teh page, but you can easily miss it if you dont know what you are looking for

---

### Post by clarke.rainey on 2005-09-28
Well I have an older Sony PCG-VX89 and I really want to get my F-Keys working... but I cannot get either the Sonypid or the sony_acpi to work on my machine... whenever I got to make either of them I get odd errors that due to my inexperience with linux, cannot solve...

thor@valhalla:~/sony_acpi$ ls
Makefile  sony_acpi.c  sony_acpi.txt
thor@valhalla:~/sony_acpi$ sudo make
make -C /lib/modules/2.6.10-5-686/build SUBDIRS=/home/thor/sony_acpi modules
make: *** /lib/modules/2.6.10-5-686/build: No such file or directory.  Stop.
make: *** [default] Error 2
thor@valhalla:~/sony_acpi$


or 

thor@valhalla:~/Desktop/sonypid-1.9.1$ sudo make
Password:
ln -sf /usr/include/linux/sonypi.h
gcc -Wall -Wstrict-prototypes -O2 -pipe -c sonypid.c -o sonypid.o
sonypid.c:34:22: X11/Xlib.h: No such file or directory
sonypid.c:35:34: X11/extensions/XTest.h: No such file or directory
sonypid.c:41: error: syntax error before '*' token
sonypid.c:41: warning: function declaration isn't a prototype
sonypid.c: In function `simulateKeyPress':
sonypid.c:42: error: `KeyCode' undeclared (first use in this function)
sonypid.c:42: error: (Each undeclared identifier is reported only once
sonypid.c:42: error: for each function it appears in.)
sonypid.c:42: error: syntax error before "keycode"
sonypid.c:43: error: `keycode' undeclared (first use in this function)
sonypid.c:43: warning: implicit declaration of function `XKeysymToKeycode'
sonypid.c:43: error: `disp' undeclared (first use in this function)
sonypid.c:43: warning: implicit declaration of function `XStringToKeysym'
sonypid.c:43: error: `keyname' undeclared (first use in this function)
sonypid.c:44: warning: implicit declaration of function `XTestGrabControl'
sonypid.c:44: error: `True' undeclared (first use in this function)
sonypid.c:45: warning: implicit declaration of function `XTestFakeKeyEvent'
sonypid.c:46: warning: implicit declaration of function `XSync'
sonypid.c:46: error: `False' undeclared (first use in this function)
sonypid.c: At top level:
sonypid.c:50: error: syntax error before '*' token
sonypid.c:50: warning: function declaration isn't a prototype
sonypid.c: In function `simulateKeyRelease':
sonypid.c:51: error: `KeyCode' undeclared (first use in this function)
sonypid.c:51: error: syntax error before "keycode"
sonypid.c:52: error: `keycode' undeclared (first use in this function)
sonypid.c:52: error: `disp' undeclared (first use in this function)
sonypid.c:52: error: `keyname' undeclared (first use in this function)
sonypid.c:53: error: `True' undeclared (first use in this function)
sonypid.c:54: error: `False' undeclared (first use in this function)
sonypid.c: At top level:
sonypid.c:62: error: syntax error before '*' token
sonypid.c:62: warning: function declaration isn't a prototype
sonypid.c: In function `simulateButton':
sonypid.c:63: error: `disp' undeclared (first use in this function)
sonypid.c:63: error: `True' undeclared (first use in this function)
sonypid.c:64: error: `mask' undeclared (first use in this function)
sonypid.c:65: warning: implicit declaration of function `XTestFakeButtonEvent'
sonypid.c:65: error: `button' undeclared (first use in this function)
sonypid.c:67: error: `False' undeclared (first use in this function)
sonypid.c: In function `main':
sonypid.c:96: error: `Display' undeclared (first use in this function)
sonypid.c:96: error: `disp' undeclared (first use in this function)
sonypid.c:137: warning: implicit declaration of function `XOpenDisplay'
make: *** [sonypid.o] Error 1
thor@valhalla:~/Desktop/sonypid-1.9.1$

---

### Post by Peacepunk on 2007-10-15
According to sony_acpi devs, latest version has been renamed to sony-laptop and is being included in the latest kernel, and has been already at times of the former sony_acpi

[http://www.popies.net/sonypi/]("http://www.popies.net/sonypi/")
[http://www.linux.it/~malattia/wiki/index.php/Sony_drivers]("http://www.linux.it/~malattia/wiki/index.php/Sony_drivers")

I do have the same issue, tried to build sony_acpi anyway. Builds fine against 2.6.22.9 but modprobe sony-acpi returns "FATAL: MODULE NOT FOUND" (While both sonypi and sony-laptop "modprobe" ok)

OK; knowing that I should have the right module somewhere 
(I do have a /sys/class/backlight/sony folder, but no in /proc/acpi/), 

That sonypid is doing a fine job monitoring my centrino temp,
(So it's out there & working)
[B]
How do I tell the other module, sony-laptop, to take care of the brightness then?[/B]

I did a modprobe -v -r sonypi, with the actual effect of disabling the PowerButtonBrightness Feature - sending tons of warning about temperature on the screen, and killing the "special" keys (play/pause & stuff)... And spicctrl complains there's no sonypi file in /dev/ anymore...

Then, how do I tell spicctrl tu use sony-laptop ?

:( confused, to say the least :( 'been on this one all day :(

---

### Post by Peacepunk on 2007-10-16
OK solved here, I did, thanks to the ubuntu forums again,

wget [http://download.berlios.de/fsfn/sonyacpi-0.1.tar.gz](http://download.berlios.de/fsfn/sonyacpi-0.1.tar.gz)

&& this one compiled fine on Fedora7 kernel 2.6.22.9 after the usual make && sudo make install + modprobe -v sony-acpi

Don't forget to reboot though, modprobing isn't enough.

[so much for the official website with sony-laptop, its inclusion in the kernel & such. Maybe I needed sony-acpi because this laptop is too old... think three years max....]

OK, off to the function key, the infamous "FN" now... Always some more in me plate, indeed.

Cheers

---

