---
title: "Plantronics DSP-500"
date: 2007-06-02
forum: Hardware &amp; Laptops
---

### Post by Mito on 2007-06-02
I have a Plantronics DSP-500 USB headset and I can't get it to work right.  When in my sound preferences I tell it to use USB-Audio, it works for gnome-related apps, but it is constantly at 100% volume.  Any non-gnome apps don't get any sound at all, which does me no good.

I have tried to follow a few hints via google to get it to work, but nothing has been able to get it to be used as a standard ALSA device (as it is right now after my last test of editing the modules.conf file a little, the above-mentioned USB-Audio workaround doesn't even work).

Does anyone have any ideas on how to get ALSA to see this device properly?  **_Any_** help would be **_hugely_** appreciated!

Thanks!

Mito

---

### Post by crimsun on 2007-06-03
> **Mito said:**
> I have a Plantronics DSP-500 USB headset and I can't get it to work right.  When in my sound preferences I tell it to use USB-Audio, it works for gnome-related apps, but it is constantly at 100% volume.  Any non-gnome apps don't get any sound at all, which does me no good.

I have tried to follow a few hints via google to get it to work, but nothing has been able to get it to be used as a standard ALSA device (as it is right now after my last test of editing the modules.conf file a little, the above-mentioned USB-Audio workaround doesn't even work).

It sounds like you have a perfect use case for PulseAudio, which allows you to migrate the sound device used per-application on the fly.  I would revert any changes you've made to any configuration files (asoundrcs, mainly) for sound, then install the pulseaudio-esound-compat, pavucontrol, and libasound2-plugins packages.  Then, execute `asoundconf set-pulseaudio` in a Terminal/Konsole.  After restarting your sound applications, you should be able to use Applications> Sound & Video> PulseAudio Volume Control to control the devices.

Flash 9 through a Web browser requires a bit more configuration.

---

### Post by Mito on 2007-06-03
Would the pulse audio work for Wine apps though?  The main things that I need sound for (I need them for videos, flash, etc for web browsing etc too, but not as much) is for a bunch of Windows apps that I use via Wine.

Right now my workaround is dual-booting to Windows to use those apps, but that is becoming very old very quickly.

I'll look into this pulse-audio thing, but the better solution would be to get this to work with ALSA, so it will work with anything.  This Pulse-Audio thing looks worth a try though, thanks.

---

### Post by ARTO^UK on 2007-07-25
Install Skype, that makes the inline audio work for some reason so you can control the volume.

---

### Post by Mito on 2007-07-27
> **ARTO^UK said:**
> Install Skype, that makes the inline audio work for some reason so you can control the volume.

Thanks for that, but I am still unable to get any sound with it in Wine apps after installing Skype...

Thanks for the suggestion though!

As I said, the biggest thing I need sound for is my Wine apps.  Anyone know how to get it working with either that ALSA or OSS etc so that Wine can work with it?

Thanks!

---

### Post by samurailink3 on 2007-07-30
I also need sound for USB audio for gaming in wine. Any help would be greatly appreciated. I've been fighting with this thing for a while now.

---

