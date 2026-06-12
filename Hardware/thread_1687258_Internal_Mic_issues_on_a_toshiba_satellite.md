---
title: "Internal Mic issues on a toshiba satellite"
date: 2011-02-13
forum: Hardware
---

### Post by king james II on 2011-02-13
So I had been having your run of the mill laptop headphone jack and mic issues that so many have encountered until I found this this thread;
[http://ubuntuforums.org/showthread.php?t=1603735&highlight=toshiba+headphone+jack](http://ubuntuforums.org/showthread.php?t=1603735&highlight=toshiba+headphone+jack)
I ran this script ```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa; sudo apt-get update; sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```
and it worked perfectly for the headphones however the internal mic is still not picking up anything. I opened alsamixer in the terminal hit view all then used the spacebar on my capture and analog mic boost, and still get nothing. Does anyone out there have any idea what I should do?

P.S. I have a  toshiba satellite T135D-S1324 RT if that makes any difference.

---

### Post by king james II on 2011-02-14
Anybody out there?

---

### Post by king james II on 2011-02-24
Well this is disappointing.

---

### Post by king james II on 2011-04-14
Well I have an update. My headphone jack has pretty much completely stopped working. I was able to get it to work off and on for the past month or so by reinserting the aforementioned bit of code, however that has stopped working altogether. when ever I put in the code nowadays I get this message:
E: Couldn't find package linux-alsa-driver-modules-2.6.32-30-generic
I really don't know what to do. The lack of a microphone is actually putting a strain on my already strained long-distance relationship (skype is the only affordable way her and I can keep in touch). So I'm begging anybody out there that has the slightest notion of what may be wrong to just post something anything here. :confused:
The future of my love-life lies in the hands of the Ubuntu community(that might be the first time that statement has been put in print.)

---

### Post by lidex on 2011-04-17
Try this using a Terminal="Applications->Accessories->Terminal"
```
echo "options snd-hda-intel model=olpc-xo-1_5" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

Now this:
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---

### Post by Marcelo Ruiz on 2011-04-18
Check this:

[http://ubuntuforums.org/showthread.php?t=1701900]("http://ubuntuforums.org/showthread.php?t=1701900")

It worked in my Qosmio.

---

### Post by king james II on 2011-04-18
thanks for your help here is the link.

[http://www.alsa-project.org/db/?f=a42b76eeea56616e9239c10bddc93bd5927b74f2](http://www.alsa-project.org/db/?f=a42b76eeea56616e9239c10bddc93bd5927b74f2)

---

### Post by king james II on 2011-04-18
@ marcelo
I tried adding those lines to my modprobe and rebooted. It didn't work. I'm running lucid if it makes any difference. Here is what my modprobe reads currently.

```

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
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
options snd-hda-intel model=3stack enable=yes
options snd-hda-intel model=olpc-xo-1_5
options snd-usb-audio index=-2
options snd-hda-intel model=hp-laptop
```

---

### Post by lidex on 2011-04-18
You've got a bunch of models in there. Post these outputs for me please:
```
cat /etc/modprobe.d/alsa-base.conf
```
```
ls /etc/modprobe.d/
```

---

### Post by king james II on 2011-04-18
Status Update:
Well I finally installed maverick and to my surprise the the headphones were working, however it did not fix my mic. I added Marcelo's code to my modprobe and rebooted, still nothing. I removed the code and tried the echo code again I rebooted and the mic still did not want to work. So I've run the second lidex code and posted the link to the outcome below.  

[http://www.alsa-project.org/db/?f=bd082a49cd35c74cbad845b73bbb25bbe4e0d85a](http://www.alsa-project.org/db/?f=bd082a49cd35c74cbad845b73bbb25bbe4e0d85a)

I just read you reply lidex as I was typing this I here is the is the out come for the code.

```
james@james-desktop:~$ cat /etc/modprobe.d/alsa-base.cong
cat: /etc/modprobe.d/alsa-base.cong: No such file or directory
james@james-desktop:~$ cat /etc/modprobe.d/alsa-base.cong
cat: /etc/modprobe.d/alsa-base.cong: No such file or directory
james@james-desktop:~$ ls /etc/modprobe.d/
alsa-base.conf           blacklist-framebuffer.conf
alsa-base.conf.dpkg-old  blacklist-modem.conf
alsa-base.conf.save      blacklist-oss.conf
alsa-base.conf.save.1    blacklist-watchdog.conf
blacklist-ath_pci.conf   intel-5300-iwlagn-disable11n.conf
blacklist.conf           libpisock9.conf
blacklist-firewire.conf


```

---

### Post by lidex on 2011-04-18
> **king james II said:**
> Status Update:
Well I finally installed maverick and to my surprise the the headphones were working, however it did not fix my mic. I added Marcelo's code to my modprobe and rebooted, still nothing. I removed the code and tried the echo code again I rebooted and the mic still did not want to work. So I've run the second lidex code and posted the link to the outcome below.  

[http://www.alsa-project.org/db/?f=bd082a49cd35c74cbad845b73bbb25bbe4e0d85a](http://www.alsa-project.org/db/?f=bd082a49cd35c74cbad845b73bbb25bbe4e0d85a)

I just read you reply lidex as I was typing this I here is the is the out come for the code.

```
james@james-desktop:~$ cat /etc/modprobe.d/alsa-base.cong
cat: /etc/modprobe.d/alsa-base.cong: No such file or directory
james@james-desktop:~$ cat /etc/modprobe.d/alsa-base.cong
cat: /etc/modprobe.d/alsa-base.cong: No such file or directory
james@james-desktop:~$ ls /etc/modprobe.d/
alsa-base.conf           blacklist-framebuffer.conf
alsa-base.conf.dpkg-old  blacklist-modem.conf
alsa-base.conf.save      blacklist-oss.conf
alsa-base.conf.save.1    blacklist-watchdog.conf
blacklist-ath_pci.conf   intel-5300-iwlagn-disable11n.conf
blacklist.conf           libpisock9.conf
blacklist-firewire.conf


```

There was a typo in that first command, sorry. I want you to remove the excess files there:
```
cd /etc/modprobe.d/
```
```
sudo rm alsa-base.conf.dpkg-old alsa-base.conf.save alsa-base.conf.save.1 
```

And let's try this one again:
```
cat /etc/modprobe.d/alsa-base.conf
```

---

### Post by king james II on 2011-04-18
This is the output that I got:

```
james@james-desktop:/etc/modprobe.d$ cat /etc/modprobe.d/alsa-base.conf

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
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2
options snd-hda-intel model=olpc-xo-1_5

james@james-desktop:/etc/modprobe.d$ ^C
james@james-desktop:/etc/modprobe.d$ 

```

---

### Post by lidex on 2011-04-18
And you removed those other files, correct?
Run the alsa-info script again so we can see where we are, but first I want you to reboot.

---

### Post by king james II on 2011-04-22
Sorry it took me a while it's finals week. Here is the Alsa-info: [http://www.alsa-project.org/db/?f=7b032711e9d7374589e2fd73aa4b0add2f015016](http://www.alsa-project.org/db/?f=7b032711e9d7374589e2fd73aa4b0add2f015016)

---

