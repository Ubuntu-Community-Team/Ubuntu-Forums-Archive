---
title: "Anyone Got a Solution to Gateway T-Series Sound Issues?"
date: 2009-09-13
forum: Hardware
---

### Post by chessnerd on 2009-09-13
I have read thread after thread on Ubuntu forums and page after page of Linux help info online and have yet to find a simple solution to this problem:

My laptop has no sound for the headphone jack, but the sound for the on-board speakers works perfectly.

The sound does turn off for the on-board speakers when headphones are inserted, but the headphones don't work. There is a half-second of sound the first time headphones are put in after a reboot, but every time after that there is no sound at all.

The output of "cat /proc/asound/card0/codec#* | grep Code" is 

Codec: SigmaTel STAC9205
Codec: Conexant ID 2c06
Codec: Silicon Image SiI1392 HDMI

The output of "cat /proc/asound/card0/pcm0c/info" is

card: 0
device: 0
subdevice: 0
stream: CAPTURE
id: STAC92xx Analog
name: STAC92xx Analog
subname: subdevice #0
class: 0
subclass: 0
subdevices_count: 2
subdevices_avail: 2

Here is what I've tried:

Using alsamixer to try to activate the headphone sound was my first attempt, but there is no "headphones" and only "Master" "PCM" "Front" "IEC958" and "Analog L" are modifiable options (the others are "IEC958 P" and "Digital").

Modifying the alsa-base.conf file with "options snd-hda-intel model="
using every model from ALSA-Configuration.txt that is Gateway related (gateway, m2-2, m6, and pa6) and STAC9205 related (dell-m42, dell-m43, and dell-m44). None of them worked.

Reading about using an older kernel from 8.04. I don't wish to do this if I can avoid it. From my understanding older kernels are not as good as newer ones. :P

I'm not going to stop working on this just because I posted this. I've found a couple more threads (there are dozens of them!) about this same issue and I will try their solutions as well, so if my little guy over to the left shows that I'm offline, I very well could be rebooting.

I'm going to keep this up for the next half hour or so and then I'll go to bed and try again tomorrow. Thanks in advance for any help.

---

### Post by chessnerd on 2009-09-13
I'm done for the night. I'll keep trying tomorrow. I really want the sound to work on this, otherwise I'll have to boot into Windows whenever I want to listen to music (I just got new speakers that are better quality than the on-board ones (which isn't saying much) and, since they need the headphone jack to work I can't use them until I fix this problem...)

---

### Post by chessnerd on 2009-09-15
Success! Oh, the Ubuntu bootup sound has never sounded so good...:)

I used a link provided in [this thread]("http://ubuntuforums.org/showthread.php?t=1007093") (bottom of page 2) which lead to [this site]("http://blog.wessendorf.org/software/headphones-with-ubuntu-904-and-gateway-t-6345u/") and then used steps 5, 7 and 8 (6 apparently isn't needed) and one reboot later, perfectly working sound!

Let's just hope it sticks. There have been a few reports of temporary success with these drivers, but for now, I'm going to kick back, put on my headphones, and listen to some tunes... :guitar:

---

### Post by chollis888 on 2009-09-16
This is all it took for me. Thanks to above poster.......

---

### Post by teejmya on 2010-04-04
I don't know if it still works for anyone, but for my Gateway T-6330u, all I did was install ALSA drivers version 1.0.20, like whatshisface did in that link chessnerd posted.

That alone got my sound to work, Karmic, stock kernel.

> 
sudo apt-get install alsaconf
sudo apt-get install alsa-base alsa-utils
sudo apt-get install build-essential linux-headers-$(uname -r)
wget [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.20.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.20.tar.bz2)
tar -xjf alsa-driver-1.0.20.tar.bz2
cd alsa-driver-1.0.20
./configure
sudo make
sudo make install



EDIT: Well, it didn't stick after reboot. Thanks to Ubuntu, I don't do that often.
Instead I added
> options snd-hda-intel model=eapd probe_mask=1 position_fix=1
to the end of
> sudo nano /etc/modprobe.d/alsa-base.conf

Now it works.

---

### Post by Wootyeah on 2010-04-06
Lol - thanks, now mine works again after the update!

---

