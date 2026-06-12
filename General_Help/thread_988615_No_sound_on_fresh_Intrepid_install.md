---
title: "No sound on fresh Intrepid install"
date: 2008-11-20
forum: General Help
---

### Post by yuv656 on 2008-11-20
I just installed a fresh copy of 8.10 on my system, but my sound does not work at all (it used to work in Hardy). Clicking on the volume control icon yields:
> The volume control did not find any elements and/or devices to control. This means that either you don't have the right GStreamer plugins installed, or that you don't have a soundcard configured.

> conrad@conrad-desktop:~$ aplay -l
aplay: device_list:215: no soundcards found...
conrad@conrad-desktop:~$ lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)


I searched the forums but haven't found a similar case (no sound in fresh Intrepid install). Any help will be appreciated!

---

### Post by spiderbatdad on 2008-11-20
Please try the sound preferences. Set auto detect for all options. Under Default Mixer Tracks Device. Select your sound device. Restart your system.

---

### Post by yuv656 on 2008-11-20
Thank you for the reply.

Everything is already set to autodetect and there is nothing under Default Mixer Tracks. It is completely empty.

---

### Post by spiderbatdad on 2008-11-20
maybe try this...edit /etc/pulse/default.pa

uncomment: load-module module-alsa-sink
Shown in bold below.

Then restart again.




```
.fail

### Load audio drivers statically (it's probably better to not load
### these drivers manually, but instead use module-hal-detect --
### see below -- for doing this automatically)
#**load-module module-alsa-sink**
#**load-module module-alsa-source device=hw:1,0**
#load-module module-oss device="/dev/dsp" sink_name=output source_name=input
#load-module module-oss-mmap device="/dev/dsp" sink_name=output source_name=input
#load-module module-null-sink
#load-module module-pipe-sink
```

---

### Post by yuv656 on 2008-11-20
This had no effect.

---

### Post by yuv656 on 2008-11-20
With every computer on which I installed Ubuntu in the past (including obscure laptops), the sound worked "out of the box". Why is it that in Intrepid it doesn't work at all, and this on a fairly standard system?!

---

### Post by yuv656 on 2008-11-21
Can someone please help me?

---

### Post by yuv656 on 2008-12-26
Totem asked me whether I wanted install codecs for a video, so I installed the codec and after rebooting my sound worked!

It stopped working, however, when I installed VLC recently (exact same error message, "no GStreamer plugins or devices".

Removing the vlc package didn't fix it. I tried to remove some of its depencies with no luck.

I don't know how to solve this problem, but perhaps this provides some clues? Can someone PLEASE help me? Thanks in advance..

---

### Post by cylux on 2008-12-26
Try 
```

sudo pkill -9 pulseaudio
```


And then restart whatever program you're trying to listen to audio with.

---

### Post by yuv656 on 2008-12-27
> **cylux said:**
> Try 
```

sudo pkill -9 pulseaudio
```


And then restart whatever program you're trying to listen to audio with.

Thanks. Applications still don't have audio, but I don't know how this is supposed to work:
> conrad@conrad-desktop:~$ sudo pkill -9 pulseaudio
[sudo] password for conrad: 
conrad@conrad-desktop:~$ aplay -l
aplay: device_list:215: no soundcards found...


---

### Post by Zorael on 2008-12-27
> **yuv656 said:**
> ```
conrad@conrad-desktop:~$ sudo pkill -9 pulseaudio
[sudo] password for conrad:
conrad@conrad-desktop:~$ aplay -l
aplay: device_list:215: no soundcards found... 
```
Hum, ouch. Output of the following?
```
$ lshw -C multimedia
```

---

### Post by yuv656 on 2008-12-28
Hi Zorael, thanks for the reply.

> lshw -C multimedia
WARNING: you should run this program as super-user.
  *-multimedia UNCLAIMED  
       description: Audio device
       product: 82801I (ICH9 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0


---

### Post by Zorael on 2008-12-28
Okay. And the following?
```
$ sudo modprobe -v snd-hda-intel
$ aplay -l
```

---

### Post by yuv656 on 2008-12-28
> conrad@conrad-desktop:~$ sudo modprobe -v snd-hda-intel
[sudo] password for conrad: 
conrad@conrad-desktop:~$ aplay -l
aplay: device_list:215: no soundcards found...

This ugly warning is always glaring at me when I click on the volume control icon:
[IMG]http://chweb.net/gstreamer.jpg[/IMG]

---

### Post by linuxonbute on 2008-12-28
I had the same problem on my laptop with an intel hda card
Try this:

sudo gedit /etc/modprobe.d/alsa-base
add the line 
"options snd-hda-intel model=toshiba"

without the quotes, at the end of the file.

This might not work because you may need to try a different word
instead of toshiba such as acer or vaio or 3stack.

If you do a search for snd-hda-intel on the forums you will see lots of threads showing things you can try.

---

### Post by linux_tech on 2008-12-28
your hardware is not being detected properly by alsa
1st check output of-


```

at /proc/asound/card0/codec#* | grep Codec


```

```

 gksudo gedit /etc/modprobe.d/alsa-base

```
(to edit file)

add something like
options snd-hda-intel model=(depends on pc)

check this thread for full details-
[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

---

### Post by yuv656 on 2008-12-28
I tried that solution a while ago and it didn't work.

Everyone who posts to that thread get something from aplay -l or the command you gave me. I don't get anything from either one of them:

> conrad@conrad-desktop:~$ cat /proc/asound/card0/codec#* | grep Codec
cat: /proc/asound/card0/codec#*: No such file or directory
conrad@conrad-desktop:~$ aplay -l
aplay: device_list:215: no soundcards found...

And my sound worked perfectly after installing gstreamer codecs and stopped working again when I installed VLC. 

How this is possible after all the strides Ubuntu has made is simply beyond me.

---

### Post by albinootje on 2008-12-28
> **yuv656 said:**
> Totem asked me whether I wanted install codecs for a video, so I installed the codec and after rebooting my sound worked!

It stopped working, however, when I installed VLC recently (exact same error message, "no GStreamer plugins or devices".

Removing the vlc package didn't fix it. I tried to remove some of its depencies with no luck. 

Did you reboot after you removed vlc ?
Sounds a little bit like a kernel module problem.

Can you try booting with an older kernel ?

And can you post the output of :
```

dpkg -l|grep gstreamer
dpkg -l|grep vlc

```

---

### Post by albinootje on 2008-12-28
See also :
[http://ubuntuforums.org/showthread.php?t=314383](http://ubuntuforums.org/showthread.php?t=314383)

---

### Post by yuv656 on 2008-12-28
Hi albinootje, thanks for your reply.

> Did you reboot after you removed vlc ?

Yes.

> Can you try booting with an older kernel ?

Tried it, made no difference.

> And can you post the output of :
Code:

dpkg -l|grep gstreamer
dpkg -l|grep vlc


Here it is:

```
conrad@conrad-desktop:~$ dpkg -l|grep gstreamer
ii  bluez-gstreamer                           4.12-0ubuntu5                           Bluetooth gstreamer support
ii  gstreamer0.10-alsa                        0.10.21-3                               GStreamer plugin for ALSA
ii  gstreamer0.10-ffmpeg                      0.10.5-1                                FFmpeg plugin for GStreamer
ii  gstreamer0.10-gnomevfs                    0.10.21-3                               GStreamer plugin for GnomeVFS
ii  gstreamer0.10-plugins-base                0.10.21-3                               GStreamer plugins from the "base" set
ii  gstreamer0.10-plugins-base-apps           0.10.21-3                               GStreamer helper programs from the "base" se
ii  gstreamer0.10-plugins-good                0.10.10.4-1ubuntu1                      GStreamer plugins from the "good" set
ii  gstreamer0.10-plugins-ugly                0.10.9-1ubuntu0.1                       GStreamer plugins from the "ugly" set
ii  gstreamer0.10-pulseaudio                  0.10.10.4-1ubuntu1                      GStreamer plugin for PulseAudio
ii  gstreamer0.10-schroedinger                1.0.5-1                                 GStreamer plugin for encoding/decoding of Di
ii  gstreamer0.10-tools                       0.10.21-4                               Tools for use with GStreamer
ii  gstreamer0.10-x                           0.10.21-3                               GStreamer plugins for X11 and Pango
ii  libgstreamer-plugins-base0.10-0           0.10.21-3                               GStreamer libraries from the "base" set
ii  libgstreamer0.10-0                        0.10.21-4                               Core GStreamer libraries and elements
ii  phonon-backend-gstreamer                  4:4.2.0-0ubuntu1                        Phonon GStreamer 0.10.x backend
ii  totem-gstreamer                           2.24.3-0ubuntu1                         A simple media player for the GNOME desktop 
conrad@conrad-desktop:~$ dpkg -l|grep vlc
rc  libvlc2                                   0.9.4-1ubuntu3                          multimedia player and streamer library
rc  libvlccore0                               0.9.4-1ubuntu3                          multimedia player and streamer library
rc  vlc                                       0.9.4-1ubuntu3                          multimedia player and streamer
conrad@conrad-desktop:~$ 

```

> See also :
[http://ubuntuforums.org/showthread.php?t=314383](http://ubuntuforums.org/showthread.php?t=314383)

Please see post #17.

---

### Post by albinootje on 2008-12-28
Thanks.

Here are a few bug-reports from people who have the same or almost the same sound-card (I searched for "82801I sound ubuntu" in a search-engine) :

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/274424](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/274424)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/268757](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/268757)
[https://answers.launchpad.net/ubuntu/+question/55305](https://answers.launchpad.net/ubuntu/+question/55305)

Some talk about the irqpoll and other kernel boot parameters.
Can you read a bit, and try those options ?

Did you file a bug-report about this already ?

---

### Post by strategi on 2009-01-21
hi i am getting the below mentioned msg when i type dpkg -l grep gstreamer

can you please advice on the same.....how to go abt it further because my sound card has not been funtioning after i did an regular update/...


Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  grep           2.5.3~dfsg-3   GNU grep, egrep and fgrep
No packages found matching gstreamer.

---

### Post by albinootje on 2009-01-21
> **strategi said:**
> 
No packages found matching gstreamer.

Are you using Ubuntu or perhaps Kubuntu or Xubuntu ?
If Ubuntu, then I think :
```

sudo apt-get update
sudo apt-get install ubuntu-desktop

```
should already install some gstreamer packages.

---

