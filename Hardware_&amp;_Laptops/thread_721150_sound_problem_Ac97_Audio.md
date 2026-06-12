---
title: "sound problem Ac97 Audio"
date: 2008-03-11
forum: Hardware &amp; Laptops
---

### Post by linux1time on 2008-03-11
installed ubuntu 7.10 i i dont have sound (realteck ac97audio)
i dont have wifi also(atheros)

please help:guitar:

---

### Post by Sef on 2008-03-11
Could you post the results of the code below:

1) Open the terminal (Applications > Accessories > Terminal

2) ```
gksudo gedit /etc/modprobe.d/alsa-base
```

---

### Post by linux1time on 2008-03-11
i get nothing...it opens a windows but there is nothing written on it

---

### Post by linux1time on 2008-03-11
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { 
/sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388


Here it is :)

---

### Post by Sef on 2008-03-11
> # Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2

I got mine to work by commenting out this line:

> options snd-intel8x0m index=-2

To comment it out, put a # before it, so it should look like this:

> #options snd-intel8x0m index=-2

This [thread]("http://ubuntuforums.org/showthread.php?t=160576") is how I fixed my sound problem.

---

### Post by linux1time on 2008-03-11
did not work neither this way you mentioned neither the way the other fellow mentioned in your thread...now i all messed up...can somebody help?i really really newbie on linux ubuntu...by the way i have an acer 5315 if it helps
 thanks:guitar:

---

### Post by erginemr on 2008-03-11
You should read these two topics thoroughly first:
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
[http://ubuntuforums.org/showthread.php?t=600714](http://ubuntuforums.org/showthread.php?t=600714)

I believe the solution to your problem lies in the second link, post #9:

> ...
After all of this I continued with the first link in adding the "options snd-hda-intel model=acer" line to my /etc/modprobe.d/alsa-base file.
...

So, I suggest you to first backup your current alsa-base file with:
```
sudo cp /etc/modprobe.d/alsa-base /etc/modprobe.d/alsa-base.mybackup
```
edit it with:
```
gksudo gedit /etc/modprobe.d/alsa-base
```
and add the line:
```
options snd-hda-intel model=acer
```
to the end of the file. Restart your computer to see if it helps.

---

### Post by erginemr on 2008-03-11
If it doesn't work, try:
[http://ubuntuforums.org/showthread.php?t=712880&highlight=sound](http://ubuntuforums.org/showthread.php?t=712880&highlight=sound)
the link I gave in post #4 or:
[http://ubuntuforums.org/showthread.php?t=709039&highlight=sound](http://ubuntuforums.org/showthread.php?t=709039&highlight=sound)
post #7.

If that doesn't work either, please post the outcome of:
```
cat /proc/asound/cards
```
and of
```
lspci | grep -i audio
```
which will give us more details on your sound chip.

---

### Post by erginemr on 2008-03-11
If all above tricks fail to work try this excellent howto as a last resort:
[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

which tries to help people identify the keyword to be put in:
```
options snd-hda-intel model=.....
```
to the file /etc/modprobe.d/alsa-base.

---

### Post by superprash2003 on 2008-03-11
try this..may help [http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html](http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html)

---

