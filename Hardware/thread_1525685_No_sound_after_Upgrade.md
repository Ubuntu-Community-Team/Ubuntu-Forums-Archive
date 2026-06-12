---
title: "No sound after Upgrade"
date: 2010-07-07
forum: Hardware
---

### Post by finito on 2010-07-07
Well I am not sure if it was an upgrade, I don't shutdown or Restart for months at a time.

Last shutdown / Restart was on Launch Day 10.04.

uname -a
```
Linux finito-desktop 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 08:03:28 UTC 2010 x86_64 GNU/Linux
```

aplay -l
```
**** List of PLAYBACK Hardware Devices ****
Home directory /home/finito not ours.
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

dpkg -l | grep "alsa"
```
ii  alsa-base                                  1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                                 1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                                 4.60-0ubuntu8                                   Bluetooth audio support
ii  gstreamer0.10-alsa                         0.10.28-1                                       GStreamer plugin for ALSA
ii  libesd-alsa0                               0.2.41-6ubuntu1                                 Enlightened Sound Daemon (ALSA) - transition
rc  libsdl1.2debian-alsa                       1.2.13-4ubuntu4                                 Simple DirectMedia Layer (with X11 and ALSA 
ii  libsnack2-alsa                             2.2.10-dfsg1-9                                  Sound extension to Tcl/Tk and Python/Tkinter
ii  libsox-fmt-alsa                            14.3.0-1.1build1                                SoX alsa format I/O library

```

head -n 1 /proc/asound/card*/codec#*
```
Codec: Analog Devices AD1988B
```


Any help will be greatly appreciated.

:D

---

### Post by lidex on 2010-07-07
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* 
sudo rm /etc/asound.conf
```
**Logout/in.**

Check the owner/permissions on /home/finito

---

### Post by finito on 2010-07-07
didn't help.

I get an error when I start up about Ice.autority

---

### Post by finito on 2010-07-07
> Check the owner/permissions on /home/finito

Sorry this didn't light up to, for some reason i didn't read that earlier, OK, it seems my Home directory doesn't belong to me, or is that how it's supposed to be.

Anyways can you please tell me how to set them right? or maybe I am checking the wrong place could you tell me where to check and set.

Thanks again.

---

### Post by undrline on 2010-07-07
Don't know if this will apply to your situation, but my resolution ended up being, in System>Preferences>Sound, to change the  Connector under the Output tab from "Analog Output/Amplifier" to "Analog Mono  Output/Amplifier" (No Amplifier works for me too).

---

### Post by lidex on 2010-07-07
/home should belong to root. /home/finito/ should belong to user finito. Try this:
```
gksudo nautilus
```
Right click on your /home/user folder (finito) and select properties. On permissions tab change to look like the screen below (of course using your user name) then click the 'apply permissions to enclosed files' button. Close nautilus. Rerun the commands posted previously.

---

### Post by finito on 2010-07-08
Wow, All night reading and Chowning all sorts of things and such an elegant solution.

Thanks this fixed other problems I was having for some reason it was pointing to the Username group ID instead of the username it self.

Anyway thanks alot.

---

### Post by lidex on 2010-07-08
You're welcome!

---

