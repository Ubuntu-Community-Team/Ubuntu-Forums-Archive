---
title: "ATI graphics card troubles"
date: 2009-10-24
forum: Hardware
---

### Post by x-ecutioner on 2009-10-24
hi there,

the ubuntu video driver is too squished and hurts my eyes.  Its not very hi-def.

ive tried installing envy to find a new driver, it installs but it does not show up in my system>administration menu!

any suggestions on how i can improve the quality of my graphics card?
[B]
I am using a Radeon HD 5750 Graphics card
[/B]

thanks very much

x-ecutioner

---

### Post by MG37221 on 2009-10-24
Good luck.  I've nothing to add... just subscribing to this thread as I'm about to make the jump from nVidia to ATI.

---

### Post by A0MiKon on 2009-10-24
> **x-ecutioner said:**
> hi there,

the ubuntu video driver is too squished and hurts my eyes.  Its not very hi-def.

ive tried installing envy to find a new driver, it installs but it does not show up in my system>administration menu!

any suggestions on how i can improve the quality of my graphics card?
[B]
I am using a Radeon HD 5750 Graphics card
[/B]

thanks very much

x-ecutioner
I have the same type of card and have the same problem. The latest drivers from ATI can be installed, but it causes all kinds of problems unfortunately. I've just installed EnvyNG, but it doesn't help a bit. (should be under Apps > System Tools)
It only shows one driver (8.620-0ubuntu3~jaunty) and tells me it's not compatible...

If anyone has a solution for this, please help us out...

---

### Post by x-ecutioner on 2009-10-30
bump
any advice of any sort, anyone?

---

### Post by AndyM3 on 2009-10-30
Doubt that would work, but try running "xrandr -s 1920x1080" or whatever resolution.

**EDIT: Nevermind that, I think I found you a driver!** Try [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-9-10-x86.x86_64.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-9-10-x86.x86_64.run) (it's from the AMD website, originally for the HD 5800 series but AFAIK it should work). Just download and run as root.

Tell me how it goes!

---

### Post by x-ecutioner on 2009-11-01
hey there,

thanks for the help
i made the file into an executable, dragged it onto the terminal, and entered my password.

the wizard then went through its process and i selected the normal install (or something like that there were two options i believe normal and custom so i just went with normal)

the installation wizard then completed and it eventually lead me to the window (wizardcompletion.jpg attached with this post).

i typed in aticonfig into the terminal but it said no supported adapters detected.

so i restarted the computer and under my applications tab i got the ATI catalyst control center app appear as well as the ATI catalyst control center administrative.

**i cannot access both control center apps (problem.jpg), aticonfig is still giving me the same message, and my graphics have not improved.  I have tried adjusting the visual effects in the appearance Preferences menu, but it says that normal mode or advanced mode cannot be enabled **

**EDIT: i have also tried typed in aticonfig --initial -f in the terminal but it is also telling me that no supported adapters detected.  Does this all mean my graphics card is not supported?**


any help would be greatly appreciated.


thanks,

x-ecutioner

---

### Post by Zoot7 on 2009-11-01
> **MG37221 said:**
> ..as I'm about to make the jump from nVidia to ATI.
I did that and I'm kind of thinking of switching back and picking up a cheap GTX 260 or 275 maybe, merely for the Linux support. Using custom kernels gave me nothing but headaches with my HD4870, granted the generic ones always worked okay.

Anyway, @x-ecutioner

I normally use a package based install for the fglrx driver, hasn't failed on me yet.
The procedure is as follows; 
1 - Build .deb packages with **sh <Catalyst installer script name> --buildpkg Ubuntu/<release name - hardy, jaunty etc.>**
2 - Install them with **sudo dpkg -i**
3 - Run **sudo aticonfig --initial -f**
4 - Reboot and check to see if running **fglrxinfo** shows your card correctly.

Here's a good guide, it's for Jaunty but it's essentially the same for the other releases too.
**[http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide")**

Using this method has always worked for me with my HD4870, I'm not sure how you'll fare with the 5870 though.

EDIT: Here's a link to the Catalyst Installer I'd recommend to try and use:
[http://www2.ati.com/drivers/linux/ati-driver-installer-9-10-x86.x86_64.run](http://www2.ati.com/drivers/linux/ati-driver-installer-9-10-x86.x86_64.run)

---

### Post by MG37221 on 2009-11-01
@zoot7:  Thanks.  I've an integrated ATI4200 on my motherboard (785G chipset).  I stuck with my 7600GT.  It works (as well as Karmic will allow).

---

