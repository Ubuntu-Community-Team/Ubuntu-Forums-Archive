---
title: "main speakers are not muting upon using headphone"
date: 2009-03-15
forum: Hardware
---

### Post by shoaibnawaz on 2009-03-15
Hi! every loved one.
I am using ubuntu (intrepid) on my VAIO (FW230J/H) notebook. I am facing the strange behavior of its built in sound system that main speaker are not muting upon plugging in the headphone jack. The sound continues to hear from both mediums. Tell me any clue to deal with this problem. Most probabbly it seems to be the problem of my configurations.

The deviece in my use:
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

Is there any one who had solution of this problem and any experience with this matter?

---

### Post by sgosnell on 2009-03-15
It's a hardware problem with your laptop, I think.  Inserting the headphone plug should physically change contact status in the jack.

---

### Post by ggeorgak on 2009-04-25
It's hardware alright, but that doesn't mean his laptop is faulty.
 
shoaibnawaz search for threads in the forums referring to vaio and headphones. I remember that you could solve the problem by entering some flags to /etc/modprobe.d/alsa and installing some module backports.

---

### Post by shoaibnawaz on 2009-06-26
Yes definitly it was not a hardware problem. Because it is working finely in Windows.
I have found the solution of this issue by adding a line

options snd-hda-intel model=sony-assamd

in the file

Intrepid: /etc/modprobe.d/options
Jaunty: /etc/modprobe.d/alsa-base.conf

---

