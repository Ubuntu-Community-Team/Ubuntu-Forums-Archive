---
title: "Echo Indigo Installation Help Needed"
date: 2006-01-04
forum: Hardware &amp; Laptops
---

### Post by majinwu on 2006-01-04
I've been trying the steps listed at [http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Echo+Digital+Audio+Corporation&card=Indigo+IO.&chip=Motorola+56361&module=indigoio]("http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Echo+Digital+Audio+Corporation&card=Indigo+IO.&chip=Motorola+56361&module=indigoio")

...but I've been left with no luck. It seems that everyone here got their Echo Indigo to work by compiling drivers into their kernel, but this page only shows how to build the drivers separately as modules.

Can someone point me to a guide/tutorial on how to get this soundcard working? I'm using Breezy Badger Ubuntu on an IBM T42.

Any help would greatly be appreciated.

---

### Post by 23meg on 2006-01-04
Have you been able to build the module? If not, where and how exactly do you fail?

---

### Post by majinwu on 2006-01-04
To my own amazement, I actually just finished getting all the modules built.
I have successfully finished the "last" step of the aforementioned guide:
 modprobe snd-indigoio;modprobe snd-pcm-oss;modprobe snd-mixer-oss;modprobe snd-seq-oss

However, I did some tinkering in my /etc/modules.conf which my come back to haunt me... 

The blue LED on my Echo Indigo didn't light up, so I restarted the computer

Now when I run alsamixer, I get:
alsamixer: function snd_ctl_open failed for default: No such device

My problems are even more compounded:
I am missing /dev/dsp and /dev/mixer (used to have these before)
In System, Preferences, Sound, there is nothing to choose for default sound card

I really appreciate any help.

---

### Post by 23meg on 2006-01-04
You shouldn't be using /etc/modules.conf ; AFAIK it was obsoleted by /etc/modules . Try adding the modules there.

---

### Post by kilgore731 on 2006-03-03
I'm very new to Ubuntu and Linix.  I just installed Ubuntu on my laptop and I'm trying to install the Echo Indigo IO.  I've downloaded and unzipped the alsa-driver-1.0.9rc4a file and am trying to follow the directions mentioned in the forum.  I got to the part where I type 

./configure --with-cards=indigoio --with-sequencer=yes;make;make install

into the terminal, but I get an error saying...

checking for kernel version... The file /usr/src/linux/include/linux/version.h does not exist.  Please, install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /usr/src/linux).

I don't even know how to search my hard drive for the file with the file browser.  

I'm playing a show tomorrow and I would like to record it.  Please help!  At least point me in the right direction.

---

### Post by onyxrev on 2006-04-07
I would like to bump this thread.  I'm having the exact same issue.

---

