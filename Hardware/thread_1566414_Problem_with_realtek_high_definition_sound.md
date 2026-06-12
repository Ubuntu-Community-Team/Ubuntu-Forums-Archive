---
title: "Problem with realtek high definition sound"
date: 2010-09-02
forum: Hardware
---

### Post by mtaeubert on 2010-09-02
Hi, I installed ubuntu yesterday on my asus G51VX and everything seems to be working fine other than my sound card. I run ubuntu 10.04 alongside w7. I can get sound through the build in laptop speakers, however whenever I try plugging something in I dont get sound anymore. I havent tried usb audio devices yet as I dont have any. 

If i go to System>Preferences>Sound and go to hardware the device listed is called Internal Audio. However, I only get sound through the speakers in 2 profiles which are "analog stereo" and "analog stereo duplex".. In "digital stereo" and "digital stereo duplex" i get no sound at all. 

I have used ubuntu before but only a little bit and I dont really know much about the more advanced things you can do. So any help would be much appreciated.

I dont exactly know what the audio card is called but in w7 its listed as realtek high def. audio

---

### Post by btown1987 on 2010-09-02
I have an asus G60VX. To get my headphone/mic port to work i had to go into the alsa-base.conf and add a setting.

so..
[FONT=Courier New]sudo gedit /etc/modprobe.d/alsa-base.conf[/FONT]

at the very bottom of the file type in...

[FONT=Courier New]options snd-hda-intel model=asus[/FONT]

then save the file.
then type ...
[FONT=Courier New]sudo alsa force-reload[/FONT]

See if that works for you.

---

### Post by mtaeubert on 2010-09-02
Hi, thanks a lot for your reply. I tried that but it didnt work. I got an error saying: 

markus@markus-laptop:~$ sudo alsa force-reload
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/markus/.gvfs
      Output information may be incomplete.
Terminating processes: 1361lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/markus/.gvfs
      Output information may be incomplete.
 3129lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/markus/.gvfs
      Output information may be incomplete.
 3142lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/markus/.gvfs
      Output information may be incomplete.
 3155lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/markus/.gvfs
      Output information may be incomplete.
 (with SIGKILL:) 3168lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/markus/.gvfs
      Output information may be incomplete.
 (failed: processes still using sound devices: 3181(pulseaudio)).
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/markus/.gvfs
      Output information may be incomplete.
/sbin/alsa: Warning: Processes using sound devices: 3181(pulseaudio). 
Unloading ALSA sound driver modules: snd-hda-codec-realtek snd-hda-intel snd-hda-codec snd-hwdep snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc (failed: modules still loaded: snd-hda-codec-realtek snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-timer snd-page-alloc).
Loading ALSA sound driver modules: snd-hda-codec-realtek snd-hda-intel snd-hda-codec snd-hwdep snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.

so im not really sure what happened. Im sure I typed the text correctly at the bottom of the file and saved it. I rechecked afterwards.

---

### Post by mtaeubert on 2010-09-02
maybe it has something to do with that pulseaudio process.. But i have no idea how to kill it or what it is

---

### Post by lidex on 2010-09-03
Probably a different codec. These things are very much hardware-dependent. Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Enter your user password when prompted. Choose the upload option and provide a link for the output.

---

### Post by mtaeubert on 2010-09-04
Hi ive done as you said and this is the link [http://www.alsa-project.org/db/?f=db4d5c21f9c6b53acbe80dde11266271061f175f](http://www.alsa-project.org/db/?f=db4d5c21f9c6b53acbe80dde11266271061f175f) 

Thanks a lot for your help

---

### Post by lidex on 2010-09-04
*mtaeubert:*
Change the option line in alsa-base.conf to this:
```
options snd-hda-intel model=asus-mode3
```
Now reboot. You may still need to upgrade alsa.

---

### Post by mtaeubert on 2010-09-05
Thanks a lot man that solved it! Now everything works! thanks so much for your help and support <3

---

### Post by lidex on 2010-09-06
Great! Please mark the thread solved using 'Thread Tools' up top.

---

