---
title: "No audio by headphones on Asus A6 on Natty"
date: 2011-05-14
forum: Hardware
---

### Post by supersasyna on 2011-05-14
Hi to all.

I hear no audio from headphones. This is my audio device:
```
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04) 
```

Laptop ASUS A6
Ubuntu 11.04 Natty
Kernel 2.6.38-8-generic

Do you have any glue?
Thanks

---

### Post by mörgæs on 2011-05-14
How does it work in a 10.10 live boot?

---

### Post by supersasyna on 2011-05-14
with ubuntu 10.10 it didn't work too!

---

### Post by lidex on 2011-05-14
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by supersasyna on 2011-05-15
here the link
 [http://www.alsa-project.org/db/?f=e51045bc65091d8dede7a92b60207d2915b7daf9](http://www.alsa-project.org/db/?f=e51045bc65091d8dede7a92b60207d2915b7daf9)

---

### Post by lidex on 2011-05-15
You have two entries in your alsa-base.conf looking like this:
```
options snd-hda-intel model=asus
```
Go in there and delete both of them. Leave everything else intact.
Save. Close. Reboot.

To edit:
```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```

---

### Post by supersasyna on 2011-05-19
> **lidex said:**
> You have two entries in your alsa-base.conf looking like this:
```
options snd-hda-intel model=asus
```
Go in there and delete both of them. Leave everything else intact.
Save. Close. Reboot.

To edit:
```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```



Yes. I made the changes that you said...but it doesn't work again! i'm desperate! :(

---

### Post by lidex on 2011-05-19
Post an updated alsa-info please.

---

### Post by supersasyna on 2011-05-24
[http://www.alsa-project.org/db/?f=5b8c44dc5485ffeef9e36feff8b65277f2e0ad69](http://www.alsa-project.org/db/?f=5b8c44dc5485ffeef9e36feff8b65277f2e0ad69)

---

### Post by lidex on 2011-05-24
This doesn't look right:
```
!!ALSA Version
!!------------

Driver version:     1.0.23
Library version:    1.0.23
Utilities version:  1.0.24.2
```
What is this output:
```
dpkg -l | grep "alsa"
```

---

### Post by supersasyna on 2011-05-28
Sorry but i don't know! :(
Anyway i sesrched in Internet and the command should be 
```
dpkg -l | grep alsa
```
and the result is this:
```
ii  alsa-base                                      1.0.24+dfsg-0ubuntu1                       ALSA driver configuration files
rc  alsa-oss                                       1.0.17-4                                   ALSA wrapper for OSS applications
ii  alsa-utils                                     1.0.24.2-0ubuntu6                          Utilities for configuring and using ALSA
ii  alsamixergui                                   0.9.0rc2-1-9                               graphical soundcard mixer for ALSA soundcard driver
ii  alsaplayer-alsa                                0.99.80-5build1                            PCM player designed for ALSA (ALSA output module)
ii  alsaplayer-common                              0.99.80-5build1                            PCM player designed for ALSA (common files)
ii  alsaplayer-gtk                                 0.99.80-5build1                            PCM player designed for ALSA (GTK+ version)
ii  alsaplayer-jack                                0.99.80-5build1                            PCM player designed for ALSA (JACK output module)
ii  bluez-alsa                                     4.91-0ubuntu1                              Bluetooth ALSA support
rc  gnome-alsamixer                                0.9.7~cvs.20060916.ds.1-2                  ALSA sound mixer for GNOME
ii  gstreamer0.10-alsa                             0.10.32-1ubuntu5                           GStreamer plugin for ALSA
ii  libpt-1.10.10-plugins-alsa                     1.10.10-3ubuntu1                           Portable Windows Library Audio Plugin for the ALSA Interface
ii  libsnack2-alsa                                 2.2.10-dfsg1-9                             Sound extension to Tcl/Tk and Python/Tkinter - Tcl/Tk library
ii  libsox-fmt-alsa                                14.3.1-2ubuntu1                            SoX alsa format I/O library
ii  linux-alsa-driver-modules-2.6.35-22-generic    2.6.35-22.201011231600                     Ubuntu-supplied Linux modules for version 2.6.35-22-generic ALSA snapshots
```


it could be helpful????

---

### Post by lidex on 2011-05-29
Look, when you make edits to configuration files that don't work, you need to remove them before trying something else. What are these outputs:
```
ls /etc/modprobe.d
```
```
cat /etc/modprobe.d/alsa-base.conf
```

---

### Post by Yellow Pasque on 2011-05-29
> ii  linux-alsa-driver-modules-2.6.35-22-generic    2.6.35-22.201011231600
If you're using Natty, you shouldn't have this package installed. Also, I'm not sure why your ALSA lib version is 1.0.23:
```
sudo apt-get remove --purge linux-alsa-driver-modules-2.6.35-22-generic
```

---

### Post by supersasyna on 2011-05-30
> **lidex said:**
> Look, when you make edits to configuration files that don't work, you need to remove them before trying something else. What are these outputs:
```
ls /etc/modprobe.d
```
```
cat /etc/modprobe.d/alsa-base.conf
```



yes, you're right.
but now i don't know the role of theese outputs.

---

### Post by supersasyna on 2011-05-30
> **Temüjin said:**
> If you're using Natty, you shouldn't have this package installed. Also, I'm not sure why your ALSA lib version is 1.0.23:
```
sudo apt-get remove --purge linux-alsa-driver-modules-2.6.35-22-generic
```


i did it

---

### Post by lidex on 2011-05-30
> **supersasyna said:**
> yes, you're right.
but now i don't know the role of theese outputs.

Run the commands and copy the terminal output into your next post so we can see what needs to be edited.

---

### Post by supersasyna on 2011-06-01
> **lidex said:**
> Run the commands and copy the terminal output into your next post so we can see what needs to be edited.

here is the result! ;)

> sabrina@*******:~$ ls /etc/modprobe.d
alsa-base               blacklist-firewire.conf      libpisock9.conf
alsa-base~              blacklist-framebuffer.conf   options~
alsa-base.conf          blacklist-modem.conf         options.dpkg-bak
alsa-base.save          blacklist-oss.conf           oss-compat.conf
alsa-base.save.1        blacklist-rare-network.conf  sound.conf
blacklist-ath_pci.conf  blacklist-watchdog.conf      stk11xx.conf
blacklist.conf          dkms.conf

sabrina@sa********:~$ cat /etc/modprobe.d/alsa-base.conf
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
options snd-hda-intel model=z71v position_fix=1


---

### Post by lidex on 2011-06-02
OK. Remove these backup configurations:
```
sudo rm alsa-base~ alsa-base alsa-base.save alsa-base.save.1 sound.conf
```

Now remove this line from alsa-base.conf:
```
options snd-hda-intel model=z71v position_fix=1 
```
To edit:
```
gksu gedit /etc/modprobe.d/alsa-base.conf
```
Save. Close. Reboot.

---

### Post by supersasyna on 2011-06-05
I ran the command and this is the result...

sabrina@*****:~$ sudo rm alsa-base~ alsa-base alsa-base.save alsa-base.save.1 sound.conf

rm: impossibile rimuovere "alsa-base~": File o directory non esistente
rm: impossibile rimuovere "alsa-base": File o directory non esistente
rm: impossibile rimuovere "alsa-base.save": File o directory non esistente
rm: impossibile rimuovere "alsa-base.save.1": File o directory non esistente
rm: impossibile rimuovere "sound.conf": File o directory non esistente

The meaning of "rm: impossibile rimuovere" is rm impossible remove ..... and the meaning of "File o directory non esistente" is File or directory doesn't exist.

What should I do? :( :( 
I made something wrong? ...

Bye

---

### Post by lidex on 2011-06-05
Did you make that edit to alsa-base.conf?
If so, reboot and run alsa-info script again.

---

### Post by supersasyna on 2011-06-21
> **lidex said:**
> Did you make that edit to alsa-base.conf?
If so, reboot and run alsa-info script again.

No.But i run also alsa-info script again.
here is the link
[http://www.alsa-project.org/db/?f=1cc047b46a10bdf309b95f06cc227b26c863ab77](http://www.alsa-project.org/db/?f=1cc047b46a10bdf309b95f06cc227b26c863ab77)

and Thanks for your even help!! :)

---

### Post by VBprogramming on 2011-07-03
> **supersasyna said:**
> No.But i run also alsa-info script again.
here is the link
[http://www.alsa-project.org/db/?f=1cc047b46a10bdf309b95f06cc227b26c863ab77](http://www.alsa-project.org/db/?f=1cc047b46a10bdf309b95f06cc227b26c863ab77)

and Thanks for your even help!! :)

I have the same problem :) So have you solved it?

---

### Post by supersasyna on 2011-07-05
> **vbprogramming said:**
> i have the same problem :) so have you solved it?

no :( :( :(

---

### Post by VBprogramming on 2011-07-09
Ohhh :( pls somebody help meeeeeeeeeee help us

---

### Post by lidex on 2011-07-09
> **VBprogramming said:**
> Ohhh :( pls somebody help meeeeeeeeeee help us
Do you have an asus a6? If not, start a new thread. If you do and can follow instructions unlike some other individuals, post your alsa info.

---

### Post by supersasyna on 2011-07-17
> **VBprogramming said:**
> Ohhh :( pls somebody help meeeeeeeeeee help us

have you an Asus A6???

---

### Post by VBprogramming on 2011-07-17
Sorry for late answer..
Yes, I have asus a6 and I get my alias, [http://www.alsa-project.org/db/?f=d166bb720696d1c2d68d3b83c9e60ed87aa27d60](http://www.alsa-project.org/db/?f=d166bb720696d1c2d68d3b83c9e60ed87aa27d60) here is the link

---

### Post by lidex on 2011-07-17
> **VBprogramming said:**
> Sorry for late answer..
Yes, I have asus a6 and I get my alias, [http://www.alsa-project.org/db/?f=d166bb720696d1c2d68d3b83c9e60ed87aa27d60](http://www.alsa-project.org/db/?f=d166bb720696d1c2d68d3b83c9e60ed87aa27d60) here is the link
Go into alsamixer and toy with these settings:
```
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 63 [98%] [-1.00dB] [COLOR="Red"][off][/COLOR]
Simple mixer control 'Front',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [COLOR="Red"][off][/COLOR]
  Front Right: Playback 64 [100%] [0.00dB] [COLOR="Red"][off][/COLOR]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 65
  Mono:
  Front Left: Playback 65 [100%] [30.00dB] [COLOR="Red"][off][/COLOR]
  Front Right: Playback 65 [100%] [30.00dB] [COLOR="Red"][off]
[/COLOR]
```
off=muted
**Alsamixer**
Using a Terminal="Applications->Accessories->Terminal"
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.

---

### Post by VBprogramming on 2011-07-18
I must change setting [off] and set [on]??

---

### Post by lidex on 2011-07-18
> **VBprogramming said:**
> I must change setting [off] and set [on]??

Yes, the elements showing 'off' are muted. Simply unmute them.

---

### Post by VBprogramming on 2011-07-19
Ok I tryed to do that. Here is the pics but it still don't workinkg

---

### Post by VBprogramming on 2011-08-26
[http://www.alsa-project.org/db/?f=e3d2a4b3d74a8345ca9e3567eb0eacfaaf7ccc1e](http://www.alsa-project.org/db/?f=e3d2a4b3d74a8345ca9e3567eb0eacfaaf7ccc1e)

---

### Post by VBprogramming on 2011-08-26
Oh you know I found out this 
[http://ubuntuforums.org/showthread.php?t=713430&goto=nextoldest](http://ubuntuforums.org/showthread.php?t=713430&goto=nextoldest)
and solve my problem.

Thank you very much

---

### Post by supersasyna on 2011-09-16
> **VBprogramming said:**
> Oh you know I found out this 
[http://ubuntuforums.org/showthread.php?t=713430&goto=nextoldest](http://ubuntuforums.org/showthread.php?t=713430&goto=nextoldest)
and solve my problem.

Thank you very much



mmmm..yes, but it's ubuntu 7 .... Now i've ubuntu 11.04!

---

### Post by lidex on 2011-09-18
> **supersasyna said:**
> mmmm..yes, but it's ubuntu 7 .... Now i've ubuntu 11.04!

So you're saying that doesn't work for you??

---

### Post by supersasyna on 2011-10-25
I formated my laptop and I installed Ubuntu 11.10...and so...No audio by headphones AGAIN.

---

### Post by supersasyna on 2011-10-25
PROBLEM SOLVED
link:
```
sudo gedit /etc/modprobe.d/alsa-base.conf
```

than insert
```
options snd-hda-intel model=z71v position_fix=1 
```

on ASUS A6VA with Ubuntu 11.10

bye bye

---

