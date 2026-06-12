---
title: "satellite a105 no audio"
date: 2008-12-02
forum: Hardware
---

### Post by satellitex86 on 2008-12-02
Hi,
I have a Toshiba Satellite a105-s2061
after installing Ubuntu 7.04 everything worked fine, but then I upgraded to 8.04 and lost all audio.

I am currently using "Ubuntu 8.04.1, kernel 2.6.22-15-generic". This is the line from menu.lst
I have tried using kernel 2.6.24-21, but the screen goes blank shortly after the boot process starts, and then the laptop just sits there doing nothing.

I am a fairly competent user (+3 years), and have spent the last week parusing google and the ubuntu forums searching for an answer but to no avail.

I have tried all of the fixes that worked for other people, including adding various lines to the end of /etc/modprobe.d/alsa-base
If it will help, here are the lines I tried:

options snd-cmipci mpu_port=0x330 fm_port=0x388
options snd-hda-intel model=3stack,

options snd-hda-intel model=lenovo,

options snd-hda-intel model=toshiba,

options snd-cmipci mpu_port=0x330 fm_port=0x388 add
options snd-hda-intel model=3stack,

options snd-hda-intel probe_mask=1 model=uniwill-m31

the pairs were tried together, and I have had no luck whatsoever.

Any help would be appreciated,
Thanks,
Anson

---

### Post by satellitex86 on 2008-12-17
Here is an update.

I've upgraded to Ubuntu 8.10, the audio works some of the time, but if I do anything that uses audio for more that a few minutes the audio starts stuttering.

I have followed the instructions on setting up and using pulse audio here
[http://ubuntuforums.org/showthread.php?t=789578]("http://ubuntuforums.org/showthread.php?t=789578")
And that changed nothing even though I didn't have pulse audio setup correctly before.

I don't know what to do, and any help would be appreciated.
Thanks

---

