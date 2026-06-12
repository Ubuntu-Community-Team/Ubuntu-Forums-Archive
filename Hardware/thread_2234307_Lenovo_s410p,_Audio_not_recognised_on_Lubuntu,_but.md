---
title: "Lenovo s410p, Audio not recognised on Lubuntu, but it works fine on Ubuntu"
date: 2014-07-13
forum: Hardware
---

### Post by sander7 on 2014-07-13
Hi,

I have a Lenovo s410p laptop. On the newest Lubuntu (14.04) the audio is not recognized (no audio sign in panel). 
However on the newest Ubuntu (14.04) the audio works fine out-of-the-box.

lenovo official s410p page: [http://shop.lenovo.com/sa/en/laptops/lenovo/s-series/s410p/](http://shop.lenovo.com/sa/en/laptops/lenovo/s-series/s410p/)
a page to the drivers for s410p: [http://www.notebook-driver.com/lenovo/lenovo-ideapad-s410p-drivers-software/](http://www.notebook-driver.com/lenovo/lenovo-ideapad-s410p-drivers-software/) 

I have tried to change things in ALSAmixer but to no avail.

I think I need to install something to make it work but I'm puzzled as to what I have to install.

Any help much appreciated. Since I can't stand the bloated Ubuntu!

Thanks in advance

---

### Post by slooksterpsv on 2014-07-13
Could you post the following information:
```

lshw -c Sound

```

I'm wondering if it's defaulting to an HDMI audio and not your speakers.

---

### Post by sander7 on 2014-07-14
here it is (run as super-user):

```

  *-multimedia:0          
       description: Audio device
       product: Haswell-ULT HD Audio Controller
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:00:03.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=snd_hda_intel latency=0
       resources: irq:61 memory:e0610000-e0613fff
  *-multimedia:1
       description: Audio device
       product: Lynx Point-LP HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 04
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=snd_hda_intel latency=0
       resources: irq:60 memory:e0614000-e0617fff
```

---

### Post by slooksterpsv on 2014-07-14
Seems like there may be an issue with the Lynx Point audio on Trusty Tahr. HDMI audio should be working, but the speakers usually won't until you reboot, but the bug was fixed in 12.04 but reappeared in 14.04. You can file a bug report to see if it gets fixed. Unless someone comes on and says here's what to add to alsa-base.conf in /etc/modprobe.d/

---

### Post by sander7 on 2014-07-14
Thanks for the response(s), 
at least I know whats going on now!

I will wait until the next Lubuntu release and hope it gets fixxed.

---

### Post by sander7 on 2014-08-04
Is this problem fixed in Lubuntu 14.04.1?

Thanks for any help

---

### Post by slooksterpsv on 2014-08-05
You know I just read something very key that I missed in your first statement. I don't know if the newer versions of Lubuntu uses PulseAudio. Ubuntu does along with alsa. Try installing PulseAudio on your system, that may be the key thing there.

---

### Post by sander7 on 2014-08-05
thanks, will try that!!!!!!

---

### Post by sander7 on 2014-08-06
`sudo apt-get install pulseaudio` + a reboot fixxed the problem.  at last, thank you very much slooksterpsv

---

### Post by slooksterpsv on 2014-08-07
You're welcome, if you want to mark the thread as solved, that'd be great.

I was thinking about pulseaudio because every time I've ran into sound issues I usually just restart the pulseaudio service. It made me think, does Lubuntu use it or not. Didn't think it did, glad that fixed it. =D

---

