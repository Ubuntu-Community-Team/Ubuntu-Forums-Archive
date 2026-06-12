---
title: "Very loud beep sound"
date: 2007-01-19
forum: Hardware &amp; Laptops
---

### Post by prefec2 on 2007-01-19
Hi folks,

I've a rather unusual problem with a Lenovo 3000c-100 notebook. My brother installed ubuntu 6.10 from CD, updated it and migrated to kubuntu 6.10. He got wlan working (with some telephone support by me :-) including WPA and finally wanted to switch from suse 10.2 to ubuntu 6.10. But now for no reason the laptop starts beeping during startup. First it did this only under ubuntu but now it is reproducable with suse as well. Using windows on the same machine works without that beeping noise. 

As far as I can determine the problem. The sound is emitted only by one of the two speakers. Also my brother told me that the beep starts during boot process close to the ACPI and power management setup. This happens on suse and ubuntu. For some weired reason he cannot provide a dmesg output from ubuntu so I append the suse one. 

Switching of ACPI didn't help. So I guess it must be something else. It might be a problem with PCMCIA, bluetooth or usb. To me the sound is similar to the noise my computer generates when it overheats. But then it must beep also with windows.

So I'm stuck with this problem. A solution would be to reinstall ubuntu from cd and see or beeter hear if the porblem is gone or not. But without any clue this might be a useless effort, because after updating and migrating we might end up at the same place. And he really wants to switch to ubuntu, because it works better than suse and boots faster :-)

Thanks for any help, suggestions are welcome
   Reiner

---

### Post by darrenm on 2007-01-19
If its happening in Ubuntu and Suse then it has to be something relating to the hardware, but obviously something that Windows doesnt touch.

From the output the only thing I can think is to do this: 

> Run chkdsk and mount in Windows

---

### Post by prefec2 on 2008-03-24
I found an solution to the problem. Deactivating the microphone worked. So I guess it has something to do with a acoustic feedback.

Thanks anyway
  Reiner

---

### Post by mindgrind on 2008-07-05
this is an incredibly annoying and loud beep that many people seem to have, associated with error in hybernating/sleeping.

chances are it is this file that's so annoying

/usr/share/gnome-power-manager/gpm-suspend-failure.wav

so rather than muting my system or disabling sound, i just overwrote this file with a more pleasant .wav file until somebody fixes the bug in gnome-power-manager.

> sudo cp /usr/share/gnome-power-manager/gpm-critical-power.wav /usr/share/gnome-power-manager/gpm-suspend-failure.wav


hope that helps

---

