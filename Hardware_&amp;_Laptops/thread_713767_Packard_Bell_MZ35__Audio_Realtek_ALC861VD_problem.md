---
title: "Packard Bell MZ35  Audio: Realtek ALC861VD problem"
date: 2008-03-03
forum: Hardware &amp; Laptops
---

### Post by _route66_ on 2008-03-03
I recently erased my Windows Vista and installed Ubuntu 8.04 alpha 5 and i've got troubles hearing sound on my phone exit, though through speakers works well.
So, i tried   [this]("http://ubuntuforums.org/showthread.php?t=616845"), [this]("http://ubuntu-utah.ubuntuforums.org/showthread.php?t=534070") and [this]("https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller"). I also tried it with OSS like [here]("http://www.ubuntu-unleashed.com/2007/10/get-better-sound-in-ubuntu-with-brand.html"). It played fine from console when i ran "osstest" but the problem is that with oss i have /dev/oss/hdaudio0/pcm0 for speakers and /dev/oss/hdaudio0/pcm1 for headphones and i don't know how to configure the whole system to send the audio to both of them.

If you need any other details please tell.

---

### Post by _route66_ on 2008-03-04
Ok, so i downgraded and put Ubuntu 7.10 and things are the same...no sound on headphones, only on speakers.

===> later

I instaled manually the realtek drivers and added "option snd-hda-intel model=hp" into /etc/modprobe/alsa-base and worked fine . Eventually seemed that the alpha version of Ubuntu was the problem.

---

### Post by _route66_ on 2008-04-18
Hello again,
it seems I'm having problems once again. I've upgraded to Kubuntu RC1 and still there is no sound output on my jack. I've tried all the above, but nothing. Of course I will wait 5 more days for the final release, but I'm affraid that this driver issue won't be fixed. Have you got any suggestions?
And I can't stop wondering how did the ubuntu developement team let this happen knowing the amount of bug reports related to this problem.

---

### Post by _route66_ on 2008-04-19
I've changed to Ubuntu RC1, but it's the same. Does anyone have any ideas?

---

### Post by kroustou on 2008-04-21
hey man iv got the same problem :S

---

### Post by Shnureaga on 2008-05-09
Yeah, i've got it too !

HELP PLS !

---

### Post by ior3k on 2008-05-12
Try adding this line to /etc/modprobe.d/alsa-base:

options snd-hda-intel model=dallas

if you have a line already with another model, just replace it with the one above (dallas).

Cheers.

---

### Post by virtudtierra on 2008-07-08
Instalé las siguientes librerías dsde adept_manager

alsaplayer-jack libjack0 libavc1394-0 libiec61883-0 libfreebob0


funciona 100%, sin necesidad de recompilar el Kernel

saludos desde chile

---

