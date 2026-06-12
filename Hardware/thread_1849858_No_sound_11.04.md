---
title: "No sound 11.04"
date: 2011-09-25
forum: Hardware
---

### Post by petergriffingr on 2011-09-25
Hello everyone.
I recently installed ubuntu 11.4 along side with windows7.
In windows i used the line in input on my mobo's soundcard to get my speakers work
but in ubuntu the line in isn't working at all

i have searched this issue on google but i couldn't find a working solution

thanks.

---

### Post by petergriffingr on 2011-09-26
please check out my alsamixer and let me know if there's anything wrong
i want to keep ubuntu so much on my pc but i cant without sound
[http://i53.tinypic.com/91j4me.png](http://i53.tinypic.com/91j4me.png)

---

### Post by petergriffingr on 2011-09-26
is "line" and "line in" the same thing?
because on alsamixer shows me only the "line" bar

---

### Post by nothingspecial on 2011-09-26
I'm going to change the title of your thread so that someone who knows how to fix your problem knows that it is about your problem.

In the meantime, post your sound card
```

aplay -l
```

---

### Post by petergriffingr on 2011-09-26
finaly someone responded 

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
whiteboy@ubuntu:~$ ^C
whiteboy@ubuntu:~$

is there anything wrong?

---

### Post by nothingspecial on 2011-09-26
Ok.

Do this
```

zcat /usr/share/doc/alsa-base/driver/HD-Audio-Models.txt.gz | less
```

Scroll down until you find your model.

Now in another terminal, type
```

gksudo gedit /etc/modprobe.d/alsa-base.conf
``` 

And try each of the options from your model in the first terminal, eg add a line like this to the end

```
options snd-hda-intel model=[COLOR="Red"]3stack-dig[/COLOR]
```

Then save and close.

Then type ```
sudo alsa force-reload
```

If that doesn't work, try the next one
 Once again
```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```

Then 

```
options snd-hda-intel model=6stack-dig 
```

save, close

```
sudo alsa force-reload
```


And so on and so on.

Obviously, if the model for your computer is listed, try that first.

ps Nobody responded because your title gave no indication of your problem, that's why I changed it. :P

---

### Post by petergriffingr on 2011-09-26
it says command not found
what im doing wrong? : (

whiteboy@ubuntu:~$ options snd-hda-intel model=w810
options: command not found
whiteboy@ubuntu:~$ options snd-hda-intel model=3stack-dig
options: command not found
whiteboy@ubuntu:~$ options snd-hda-intel model=3stack-dig
options: command not found
whiteboy@ubuntu:~$ options snd-atiixp-modem index=3stack-dig
options: command not found
whiteboy@ubuntu:~$ options bt87x index=-
options: command not found
whiteboy@ubuntu:~$ options snd-hda-intel model=w810
options: command not found
whiteboy@ubuntu:~$ options snd-hda-intel model=6stack-dig
options: command not found
whiteboy@ubuntu:~$

---

### Post by nothingspecial on 2011-09-26
You are supposed to be editing a text file, not typing into the terminal.

```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```

Will open a text file.

You put one of those lines at the bottom.

Then you click save.

Then you close the window with the text file in it.

Then you type

```
sudo alsa force-reload
```

Play a sound. If you here something yay it's fixed.

If not open the text file again.

```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```

Then try the next option (remove the previous one though)

---

### Post by petergriffingr on 2011-09-26
here is what i get

whiteboy@ubuntu:~$ sudo alsa force-reload
[sudo] password for whiteboy: 
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/whiteboy/.gvfs
      Output information may be incomplete.
Terminating processes: 4704lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/whiteboy/.gvfs
      Output information may be incomplete.
 4853lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/whiteboy/.gvfs
      Output information may be incomplete.
 4870lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/whiteboy/.gvfs
      Output information may be incomplete.
 4887lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/whiteboy/.gvfs
      Output information may be incomplete.
 (with SIGKILL:) 4904lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/whiteboy/.gvfs
      Output information may be incomplete.
 (failed: processes still using sound devices: 4921(pulseaudio)).
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/whiteboy/.gvfs
      Output information may be incomplete.
/sbin/alsa: Warning: Processes using sound devices: 4921(pulseaudio). 
Unloading ALSA sound driver modules: snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-seq-device snd-hda-codec-hdmi snd-hda-codec-realtek snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-timer snd-page-alloc (failed: modules still loaded: snd-hda-codec-hdmi snd-hda-codec-realtek snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-timer snd-page-alloc).
Loading ALSA sound driver modules: snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-seq-device snd-hda-codec-hdmi snd-hda-codec-realtek snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-timer snd-page-alloc.
whiteboy@ubuntu:~$

---

