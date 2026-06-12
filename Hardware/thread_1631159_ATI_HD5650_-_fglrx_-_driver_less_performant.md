---
title: "ATI HD5650 - fglrx - driver less performant"
date: 2010-11-26
forum: Hardware
---

### Post by patrickvdbemt on 2010-11-26
I would like to get some guidance.
I have got a laptop with the ATI HD5650 video card (1024MB).
the default setup / driver(s) show the startup "ubuntu" with 4 bullets as progress meter working fine ; as well as the "shutdown" one.
But the fan is running like hell.
Therefore i decided to install the ATI version via the sudo apt-get install fglrx .
This installed properly. Now the fan speed is much better (means temperatur management better ??)
however I have got some issues now
* the screen is less performant ; scrolling down though a website shows interrupted screen refreshes
* moving open apps across the screen does not move them as before (less performant / refresh)
* the startup screen is of less quality resolution
* the shutdown screen is of less quality resolution and shows some text lines while shutting down
==> I am far from sure whether the screen / video card is behaving better or worse
Any feedback / experiences are appreciated ...

---

### Post by Yellow Pasque on 2010-11-26
The proprietary drivers are actually slower with 2D rendering. Turn on desktop effects.

> * the startup screen is of less quality resolution
* the shutdown screen is of less quality resolution and shows some text lines while shutting down
This is a known issue with proprietary drivers. There are workarounds, though (google).

---

### Post by patrickvdbemt on 2010-12-21
Desktop effects cannot get turned on for whatever obscure reason .:-k

To be honest, there are so many so-called "workarounds" but those are all different, they do not contribute to this problem.

It takes quite a long time before the propriaty drivers or the kernel get an upgrade in order to get it working properly.

For the moment I have got delays in the system (keyboard typing delays and not always accepted) so the system is becoming slow in responses, and unuseable for typing texts.

If I do not get this fixed quickly I do not see any other option than to switch back to my working OS , which is the Windows7 installed as dual-boot and take that as my primary.

I want to avoid this, but if keep on getting issues with this so-called Microsoft killer I give this up.

please help me (and apparently many others that have these issues).

---

### Post by Yellow Pasque on 2010-12-21
Try updating to latest Catalyst. First, remove the installed driver:
```
sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev* xorg-driver-fglrx
```
Now, follow the guide here: [http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Installing_the_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Installing_the_drivers_manually)

---

### Post by patrickvdbemt on 2010-12-26
got it working ...

---

