---
title: "Sound Card problem"
date: 2006-04-07
forum: Hardware &amp; Laptops
---

### Post by raeky on 2006-04-07
I've been trying to figure out how to get my sound card to work now for two days... ](*,)  (btw this is my first linux install... if you can't tell! ;) )

I've read many guides and posts and done much searching to no avail, so I'm resorting to asking for help. *sigh*

I have the following sound card C-Media CMI8768. It is listed as supported by ALSA with the "cmipci" driver.

```
$ lspci -v | grep -i audio
0000:02:0b.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
        Subsystem: C-Media Electronics Inc CMI8738/C3DX PCI Audio Device

```

As you can see it is being recogized as a different chipset version then what I have.. 

I have linux version:

```
$ uname -a
Linux server 2.6.12-10-686 #1 Sat Mar 11 16:22:51 UTC 2006 i686 GNU/Linux

```

The lsmod output for "snd"

```
$ lsmod |grep snd
$

```

This here is something I don't know how to resolve.. the soundcore isn't installed? 

and "/proc/asound/cards" dosn't exist, in fact the "sound" isn't in "/proc/"

And finally I'm planning on useing SPDIF out for the sound card... if I can eventually get it to work! ALSA is supost to support this chipset. ](*,)

---

### Post by FarEast on 2006-04-08
Hi raeky;) ,

> As you can see it is being recogized as a different chipset version then what I have.. 

Don't mind... it's OK, for CMI8738 and 8768 are in the same 'class'.

Execute the command below.
$ dpkg --list | grep alsa
Are 'alsa-base' and 'alsa-utils' installed?

Give a try:
$ sudo modprobe snd-cmipci

Regards

---

### Post by raeky on 2006-04-08
Thanks for your help. :D 

The output is: 

```
# dpkg --list |grep alsa
ii  alsa-base                              1.0.9b-4                             ALSA driver configuration files
ii  alsa-oss                               1.0.9-1                              ALSA wrapper for OSS applications
ii  alsa-source                            1.0.9b-4                             ALSA driver sources
ii  alsa-utils                             1.0.9a-4ubuntu5                      ALSA utilities
ii  alsaplayer-alsa                        0.99.76-6ubuntu2                     PCM player designed for ALSA (ALSA output mo
ii  alsaplayer-common                      0.99.76-6ubuntu2                     PCM player designed for ALSA (common files)
ii  alsaplayer-gtk                         0.99.76-6ubuntu2                     PCM player designed for ALSA (GTK version)
ii  alsaplayer-oss                         0.99.76-6ubuntu2                     PCM player designed for ALSA (OSS output mod
ii  gstreamer0.8-alsa                      0.8.11-0ubuntu5                      ALSA plugin for GStreamer
#           

```

and

```
# modprobe snd-cmipci
FATAL: Module snd_cmipci not found.
FATAL: Error running install command for snd_cmipci
#         

```

---

### Post by ghakko on 2006-04-08
Which version of the kernel, and which release of Ubuntu are you using? (You can use "uname -r" or "lsb_release -c" to find out.)

---

### Post by raeky on 2006-04-08
```
# uname -r
2.6.12-10-686
# lsb_release -c
Codename:       breezy
#

```

---

### Post by FarEast on 2006-04-08
Hmm... it's odd:-k 

Here the module exists in the directory
/lib/modules/2.6.12-10-686/kernel/sound/pci

---

### Post by raeky on 2006-04-08
snd-cmipci.ko is found in these directories under /lib/modules

/lib/modules/2.6.12-10-386/kernel/sound/pci
/lib/modules/2.6.12-9-386/kernel/sound/pci
/lib/modules/2.6.12/misc/pci

:-\

---

### Post by ghakko on 2006-04-08
[QUOTE=raeky]```
# uname -r
2.6.12-10-686
```[/QUOTE]

The "cmipci" driver you're looking for should have shipped with this kernel.

You might first want to check if it hasn't been deleted. You can do this with: "find /lib/modules/`uname -r` -name snd-cmipci.ko"

If it's missing, you can reinstall your kernel image with "sudo apt-get --reinstall install linux-image-2.6.10-10-686". If it's still there, something might have clobbered your module list by accident; do a "depmod -a" to re-generate it.

Once you've replaced the module, the easiest way to load it and fix up your audio stack is to simply reboot. The volume control icon in your GNOME menu bar should then work.

---

### Post by FarEast on 2006-04-08
OK;) 
Then you can load the module if you boot the system with kernel 2.6.12-10-386.
Give a try!

And if the absense of the module is the cause, you may need to remove 'linux-image-2.6.12-10-686' and reinstall it.
Make sure do it when you are runnning kernel 2.6.12-10-[COLOR="Red"]386[/COLOR].

Edit:
It seems ghakko's advice is better.  Thanks, ghakko!!

---

### Post by raeky on 2006-04-08
[QUOTE=ghakko]The "cmipci" driver you're looking for should have shipped with this kernel.

You might first want to check if it hasn't been deleted. You can do this with: "find /lib/modules/`uname -r` -name snd-cmipci.ko"

If it's missing, you can reinstall your kernel image with "sudo apt-get --reinstall install linux-image-2.6.10-10-686". If it's still there, something might have clobbered your module list by accident; do a "depmod -a" to re-generate it.

Once you've replaced the module, the easiest way to load it and fix up your audio stack is to simply reboot. The volume control icon in your GNOME menu bar should then work.[/QUOTE]

This worked perfectly! :D 

Except it should of been "linux-image-2.6.12-10-686" 

THanks everyone that helped! Now to fix other things like TV OUT for the video card so I can watch movies on my TV.. ;-) ](*,)

---

