---
title: "Toshiba L745D - internal mic not working"
date: 2011-10-27
forum: Hardware
---

### Post by hotweiss on 2011-10-27
I have a Toshiba L745D (AMD A6-3400M).  I cannot get my internal mic to work.

My sound card: Conexant CX20585

I've tried this:

```
echo "options snd-hda-intel model=thinkpad" | sudo tee -a /etc/modprobe.d/alsa-base.conf
```

```
echo "options snd-hda-intel model=ideapad" | sudo tee -a /etc/modprobe.d/alsa-base.conf
```

```
echo "options snd-hda-intel model=asus" | sudo tee -a /etc/modprobe.d/alsa-base.conf
```

...but that didn't work either.  Apparently that works for different notebook models with the same sound card.  I also tried muting the right mic channel; that also worked for someone on a different model.

Here is my ALSA information:

[http://www.alsa-project.org/db/?f=6b57a7faecf5525ccb5212a6f60ee9d1bc792838](http://www.alsa-project.org/db/?f=6b57a7faecf5525ccb5212a6f60ee9d1bc792838)

Any solutions out there?

---

### Post by rylangrayston on 2011-10-27
I just purchaced a toshiba L745D and would love to help get the mike working to... but I have a bigger problem to solve first 
my screen dosent work at all in ubuntu

I tried installing ubuntu 10.10 both with wubi and from a 
usb stick.

What vertion of linux did you install and how did it go?
Did you have to use any work arounds?

---

### Post by hotweiss on 2011-10-27
> **rylangrayston said:**
> I just purchaced a toshiba L745D and would love to help get the mike working to... but I have a bigger problem to solve first 
my screen dosent work at all in ubuntu

I tried installing ubuntu 10.10 both with wubi and from a 
usb stick.

What vertion of linux did you install and how did it go?
Did you have to use any work arounds?

You have to first install Ubuntu 11.04, then install the fglrx Catalyst driver and then finally upgrade to 11.10.  After that you have to apply the compiz fix:

[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/763005/comments/68](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/763005/comments/68)

The only thing left is the mic problem.

---

### Post by hotweiss on 2011-10-29
Here is my 'cat /proc/asound/card0/codec* | grep Codec' output:

Codec: ATI R6xx HDMI

Odd that it doesn't state that it's a Conexant card.

---

### Post by hotweiss on 2011-11-02
The internal microphone will not work if you have Fast Boot enabled in the BIOS.  If you install Ubuntu with Fast Boot enabled, you will have to reinstall it with Normal Boot enabled to get your microphone working.

---

### Post by hotweiss on 2011-11-03
If anyone is interested, I've made a Ubuntu installation guide for the Toshiba L745D:

[http://seethisnowreadthis.com/2011/10/31/how-to-install-ubuntu-11-10-on-the-toshiba-l745d/](http://seethisnowreadthis.com/2011/10/31/how-to-install-ubuntu-11-10-on-the-toshiba-l745d/)

---

