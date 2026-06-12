---
title: "Toshiba Portege 3480CT sound is slow"
date: 2005-05-19
forum: Hardware &amp; Laptops
---

### Post by avc on 2005-05-19
I have a 600MHz Portege 3480CT laptop with what shows up as a Yamaha AC-XG Audio Device under Windows 2000 and is listed as a YMF752 or YMF754 on the internet. The audio works fine on Windows but in my Ubuntu 5.04, the sound has strange problems. As GNOME starts, I hear the startup sound play halfway through, and all of a sudden, the sampling rate of the sound drops dramatically (maybe 4x), stretching the sound out and making it slow and low pitch. When I restart the session with a Ctrl-Alt-Backspace, the sound works fine. There's no slowing down. But as soon as I restart the system (cold or warm), the sound problem recurs.

I tried disabling ESD by editing /etc/esound/esd.conf according to the instruction given on this forum:

[esd]
auto_spawn=1
spawn_options=-terminate -nobeeps -as 2 -d default
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options=

I tested it out by lsof /dev/dsp, and it shows ESD running in all cases, when the sound is working properly (after session restart) and when it isn't. I tried changing the output sink under Multimedia Systems Selector to no avail.

lsmod|grep snd results in:
snd_intel8x0           29984  2
snd_ac97_codec         64608  1 snd_intel8x0
snd_pcm_oss            47652  1
snd_mixer_oss          16768  1 snd_pcm_oss
snd_pcm                84872  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              23300  1 snd_pcm
snd                    50276  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9824  2 snd
snd_page_alloc          9604  2 snd_intel8x0,snd_pcm

Interestingly, I see snd_intel8x0, but I think my audio chipset is a YMF7xx. In Windows 2000 (I have a twin of this laptop running w2k), the device properties for the audio device shows 2 Input/Output Ranges: FD00-FDFF and FCC0-FCFF. IRQ is 11. Is it possible the hardware probe detected the wrong sound card? How would I direct it to use the right one?

-Anthony

---

### Post by avc on 2005-10-23
This is still happening in Breezy. :( However, I've discovered some new things under Breezy. The sounds are fine until the gnome-volume-control applet (the one that shows up on the top panel) loads. Then there's a slight buzzing sound and all subsequent sounds are slooooooow.

As a workaround, I made a script that writes a newline to /dev/dsp and then *aplay* a sound. I don't know why it works, but it does clear up the buzzing and the slowness. Maybe there's some garbage in some buffer somewhere and the kernel modules don't clear it. Sound is fine in Fedora 3 on the same laptop.

If I were to run strace on gnome-volume-control, what should I look for? Any other diagnostic programs I can use? Someone please help!

---

### Post by avc on 2005-11-13
Removed OSS drivers by commenting them out in modprobe config files, and no more buzzing! Unfortunately, a few programs that want to use /dev/dsp won't work or have to be reconfigured.

---

