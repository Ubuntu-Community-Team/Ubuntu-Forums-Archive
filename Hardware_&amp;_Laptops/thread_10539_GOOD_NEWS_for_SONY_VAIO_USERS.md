---
title: "GOOD NEWS for SONY VAIO USERS"
date: 2005-01-09
forum: Hardware &amp; Laptops
---

### Post by vaionux on 2005-01-09
Good day mates!

I have been using my VAIO PCG-Z1 laptop and attempted to install various of GNU/Linux OS on my laptop.

Sony VAIO PCG-Z1 Specs:

Centrino 1.3Ghz
256MB RAM
60GB HDD
ATI Mobility 16MB VRAM (1400 x 1050 Res.)
USB 2.0.
SONY MAGICGATE / SONY Memory Stick Adaptor(Built-in)


Unfortunately, none of them did work and I was forced to work with Windows. :-& .

Just found out about Ubuntu from magazine and installed.

FINALLY!!!!
From Battery to Wireless ethernet every thing is compatible, Even the bloody chipset is comaptible! =D> 
And if you have same laptop as mine install NOW!

Now I can finally integrate more with my office BSD box. :D 


Thanks for great OS Ubuntu-Zines!

Network Engineer from Sydney

---

### Post by joebloggs on 2005-05-31
I have a Sony Vaio Z1 and have a very similar positive experience.

Centrino 1.5Ghz
512MB RAM
60GB HDD
ATI Mobility 16MB VRAM (1400 x 1050 Res.)
USB 2.0.
SONY MAGICGATE / SONY Memory Stick Adaptor(Built-in)
Bluetooth

Things still not fully supported;
Have not been able to get the Bluetooth functioning yet, but am in the process of adding Gnome - Bluetooth
Touchpad support is minimal, no scoll function
Keyboard not fully supported, P1 and P2 keys are not functioning
Function keys not supported yet, cannot adjust sound, panel brightness or sleep modes.
Battery life is not as good as within Windows, even though scaling is available.

Even with the handful of unsupported components, this is still a great accomplishment.

Joe


UPDATE!
I now have Bluetooth, and screen brightness. Keyboard is fully functional except for function keys. Battery life is good now that screen brightness can been reduced. Also managed to get Winmodem working. Really want to sort out the 3D support though

---

### Post by nimzo on 2005-05-31
I have a sony vaio vgn s-360.
Everything but the "FN" keys - ( I.E. to increase brightness, volume) worked on from the start! :-P

**** I have not tried playing a 3D graphics intensive game such as Tux Racer, which uses graphics acceleration. A costum graphics driver for the graphics acceleration may be downloaded from ATI's website.

Blinksilvers previous posts:

[http://www2.ati.com/drivers/linux/linux_8.12.10.html](http://www2.ati.com/drivers/linux/linux_8.12.10.html) <- link to ati release notes for the linux drivers, note the section on the mobiltiy stuff, its say 9600, the 9600 and the 9700 are the same chip at different clock speeds

[http://xoomer.virgilio.it/flavio.st...-installer.html](http://xoomer.virgilio.it/flavio.st...-installer.html) and link to third party guy who converted ati's rpm in to deb file for debian based distros as well as how to install them, good luck.

---

### Post by blackpaw on 2005-07-23
I am using a Vaio N505SN, am AMAZED how smooth everything installed!

Especially the wireless support is great! Respect to the programmers who managed it better on one CD what suse can't do on seven ;)

What I would like to get running is (as the previous posters)

[list]
[*]FN-keys (I did some workaround with spicctrl/volume on some ctrl-alt-F-Key combo)
[*]processor speed stepping (okay, pentium 2 does NOT do that but under windows there is a program called "powerpanel" that manually steps the speed down in 100 MhZ-steps.. keeps the unit cool when you read or don't need all the 400 MhZ  :grin: 
[*]Wireless connection broken after resume from standby/hibernation, no idea how to fix this... (replugging won't help, needs reset)
[*]touchpad-scrolling, APLS-kernel-buikd didn't work for me
[/list] 

ciao,


andreas

---

### Post by dwerf on 2005-08-28
Hi there,

I've got a Sony Vaio PCG-K415B and also I was so very happy to find a Linux distribution that found all my hardware in immediately. I really don't mind about the FN-key not working (it's functions can very easily, much easier than in Windows, be assigned to other keys), but one:

Is there a way to adjust the LCD-brightness any other way? Every time my monitor is too dimly lit for me to see it in broad daylight, I have to go into Windows to change that. That really sucks!

Also, my battery is not monitored; when it's empty, it just pops dead instantly.

---

### Post by parktownprawn on 2005-09-11
[QUOTE=dwerf]
Is there a way to adjust the LCD-brightness any other way? Every time my monitor is too dimly lit for me to see it in broad daylight, I have to go into Windows to change that. That really sucks!
[/QUOTE]

try install  spicctrl (from universe)```
sudo apt-get install spicctrl 
```
then ```
spicctrl -b 255 
``` will give you maximum brightness.
spicctrl -b 0 gives minimum brightness.

as usual ```
man spicctrl 
``` will give you more information.

you may have to load the sonypi module for this to work (i don't remember and my laptop is at home).
```
sudo modprobe sonypi
```

the thread 
[http://ubuntuforums.org/archive/index.php/t-13034.html](http://ubuntuforums.org/archive/index.php/t-13034.html)
has some useful details.

You can also get the Fn keys working but that requires a bit more work (and as you point out not really neccesary).

I got my Fn keys working fine under hoary (5.04) fine  using sonypid
from [http://popies.net/sonypi/](http://popies.net/sonypi/). Sonypid is a simple C program which interfaces with the kernel module sonypi. It will requires a teeny amount of C knowledge to customise. 

more information at:
[http://sol4.net/linux/pb-sonypi.shtml](http://sol4.net/linux/pb-sonypi.shtml)
[http://www.linux-on-vaio.8m.com/jslupski-vaio/sonykeyd.html](http://www.linux-on-vaio.8m.com/jslupski-vaio/sonykeyd.html)
[http://sonyfx.sourceforge.net/sonyfxd.html](http://sonyfx.sourceforge.net/sonyfxd.html)
[http://people.freenet.de/obauer/](http://people.freenet.de/obauer/)
[http://www.stray.ch/site/laboratory/wheel.html](http://www.stray.ch/site/laboratory/wheel.html)

---

### Post by flurdy on 2005-09-22
Sjog from the repositories is a nice way to use the jog dial to control brightness etc.

Needs modprobe sonypi first thu.

daemonise it for permamnent availability

---

### Post by blackpaw on 2005-11-21
hey parkdownprawn :)

would you give a hand with the Fn-Keys?
I am using Breezy on my n505sn and am almost there... using sonypi
I installed sony_acpi and now I can raise the brightness by pressing Fn-F6 and lower it with Fn-F5. Also Hibernation/Standby Shortcuts work now (although resume is bad, system not usable/ very slow after resume and wireless lan broken, needs to be restarted)

The volume still can't be adjusted, even if I get responses from the sonypid (I made tail on it and it reports some keypress-events and calls a script like "sonyvolup.sh"  but then exits with error code 0 or 2 and the volume is not changed.

any ideas on that?

merci,


andreas

---

### Post by parktownprawn on 2005-11-21
have you tried using the keyboard short cut preferences

i just set up the volume keys using:

System>Preferences>Keyboard Shotcuts

perhaps you could try this rather than the shell script.

---

