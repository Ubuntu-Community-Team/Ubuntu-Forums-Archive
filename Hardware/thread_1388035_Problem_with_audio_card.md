---
title: "Problem with audio card"
date: 2010-01-22
forum: Hardware
---

### Post by Freelife on 2010-01-22
Hi to all.

I am having troubles with my audio card:

Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

I can hear sound when I plug my headphones but I cannot hear any sound when I unplug them.
I know that Ubuntu has got problems with pulseaudio. So I removed pulseaudio using Synaptic, I restarted the system but still no sound.

I attach the output of dmesg (dmesg.odt)

Thanks for your attention.
Regards.

Ubuntu 9.10
kernel 2.6.31-17-generic
alsa-base 1.0.20+dfsg-1ubuntu5
NETBOOK: Toshiba NB200

---

### Post by tripolitan on 2010-01-22
Pulse audio has nothing to do with this, you can remove it altogether...

How many physical outputs do you have on your card? is it possible you're plugging the headphones where the speakers should go?

Check using alsamixer in terminal, using F4 and F3 to switch between playback/recording, adjust/enable/disable channels as necessary (using the M and space bar to toggle options, while speakers and headphones are plugged in.

Once satisfied, issue: sudo alsactl store (to save your settings)

---

### Post by Freelife on 2010-01-24
> **tripolitan said:**
> Pulse audio has nothing to do with this, you can remove it altogether...

How many physical outputs do you have on your card? is it possible you're plugging the headphones where the speakers should go?

Check using alsamixer in terminal, using F4 and F3 to switch between playback/recording, adjust/enable/disable channels as necessary (using the M and space bar to toggle options, while speakers and headphones are plugged in.

Once satisfied, issue: sudo alsactl store (to save your settings)


Thanks for your reply,
but the situation has not changed, however the alsamixer's parameters are:
[COLOR="Red"]100% :[/COLOR]"Master", "Headphone", "Pcm" and "Mic"
and
[COLOR="Red"]0 % :[/COLOR] "IEC958" and " IEC958 D"(I can not change them).

Help me, please! :(

P.D.
It is a Netbook (Toshiba NB200)

---

### Post by Freelife on 2010-01-24
I attaching the contents of two files:
1) alsa.conf
2) pulse-alsa.conf

Help!!!

---

### Post by Freelife on 2010-01-25
Up

---

### Post by Yellow Pasque on 2010-01-25
Try
1. Upgrade to latest ALSA: [http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)
2. Specify model keyword
```
gksu gedit /etc/modprobe.d/alsa-base.conf
```
Add the following line at the end of alsa-base.conf file:
```
options snd-hda-intel model=asus-mode4
```


[http://www.gossamer-threads.com/lists/linux/kernel/1134970](http://www.gossamer-threads.com/lists/linux/kernel/1134970)

---

### Post by Freelife on 2010-01-25
> **Temüjin said:**
> Try
1. Upgrade to latest ALSA: [http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)
2. Specify model keyword
```
gksu gedit /etc/modprobe.d/alsa-base.conf
```
Add the following line at the end of alsa-base.conf file:
```
options snd-hda-intel model=asus-mode4
```


[http://www.gossamer-threads.com/lists/linux/kernel/1134970](http://www.gossamer-threads.com/lists/linux/kernel/1134970)

Hello,
thanks for your answer!

To update alsa i preferred to follow this guide:
[http://monespaceperso.org/blog-en/2009/12/17/upgrade-alsa-1-0-22-on-ubuntu-karmic-koala-9-10/](http://monespaceperso.org/blog-en/2009/12/17/upgrade-alsa-1-0-22-on-ubuntu-karmic-koala-9-10/)

I added in alsa-base.conf ```
options snd-hda-intel model=asus-mode4
``` 

(I enclose alsa-base.conf)

Now i have alsa 1.0.22.1 but nothing has changed :(

---

### Post by Yellow Pasque on 2010-01-25
You should contact the ALSA developers then, and provide information from this script: [http://ubuntuforums.org/attachment.php?attachmentid=142560&d=1262704706](http://ubuntuforums.org/attachment.php?attachmentid=142560&d=1262704706)

---

### Post by Freelife on 2010-01-26
> **Temüjin said:**
> You should contact the ALSA developers then, and provide information from this script: [http://ubuntuforums.org/attachment.php?attachmentid=142560&d=1262704706](http://ubuntuforums.org/attachment.php?attachmentid=142560&d=1262704706)


This is the needed results:
[http://www.alsa-project.org/db/?f=4a72836b153be44d5a3b84bce66638fe41afadb7](http://www.alsa-project.org/db/?f=4a72836b153be44d5a3b84bce66638fe41afadb7) 

Who sent him?:confused:

---

### Post by Freelife on 2010-01-26
I made another attempt:

1) :~$ gksu gedit /etc/modprobe.d/alsa-base.conf
and i try one at a time:
model=asus-mode4*
model=asus-mode5
model=asus-mode6
model=3stack-6ch-dig

2):~$ sudo alsa force-reload

3):~$ speaker-test -c2 -D hw:0,0 -t wav -l1

4)I have whit all: 
  playback open error: -16,Device or resource busy 
  and i can't hear sound.

 *I have: no error and  when running speaker headphones, i can hear

---

