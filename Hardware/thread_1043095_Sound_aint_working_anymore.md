---
title: "Sound aint working anymore"
date: 2009-01-18
forum: Hardware
---

### Post by s0mmer on 2009-01-18
Hey ubuntu people.

I recently switched to ubuntu and everything seemed working. The only thing was my microphone so i started googling and tried to do this guide: [http://10xforce.blogspot.com/2007/06/ubuntu-microphone-problems-and.html](http://10xforce.blogspot.com/2007/06/ubuntu-microphone-problems-and.html)

After i'd done it restarted and all my sound was gone. I get the famous error : "No volume control GStreamer..." and aplay in terminal says no sound driver. I've tried a bunch of things but nothing works. And the sound have worked before so my hardware must be supported..

Can you please help?

---

### Post by linux_tech on 2009-01-18
what is output of
```

cat /proc/asound/card0/codec#* | grep Codec

```

---

### Post by s0mmer on 2009-01-18
That it cant be found:

s0mmer@s0mmer-ubuntu:~$ cat /proc/asound/card0/codec#* | grep Codec
cat: /proc/asound/card0/codec#*: No such file or directory

---

### Post by linux_tech on 2009-01-18
Ok does ```
aplay -l
```
show anything?

---

### Post by s0mmer on 2009-01-18
s0mmer@s0mmer-ubuntu:~$ aplay -l
aplay: device_list:215: no soundcards found...

---

### Post by linux_tech on 2009-01-18
```
lspci -v
```

---

### Post by s0mmer on 2009-01-18
The one you are looking for:

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
	Subsystem: Lenovo Device 20ac
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at fe220000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

---

### Post by linux_tech on 2009-01-18
In terminal type:
```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2

```

---

### Post by s0mmer on 2009-01-18
I copied and pasted the command you wrote and noticed this:
Couldn't find any package whose name or description matched "linux-ubuntu-modules-2.6.27-9-generic"
Couldn't find any package whose name or description matched "linux-ubuntu-modules-2.6.27-9-generic"

but ill try to reboot.

---

### Post by s0mmer on 2009-01-18
That helped! but still not completely there..

1.On my laptop like many others you can mute and controle the volume, but after i changed (before the sound stopped working) i cant use them correctly anymore.. i mean, when i open the alsa mixer they adjust the microphone level..

2. My microphone isnt working. maybe the first problem causes this? cause microphone is also set to playback?

---

### Post by s0mmer on 2009-01-18
I got the buildt-in buttons to work!

Now only my microphone is the problem.. u got any idea?

---

### Post by linux_tech on 2009-01-18
Gnome-alsamixer is easier to use than alsamixer. Try installing and running it it first
```
sudo apt-get install gnome-alsamixer

``` 
To open gnome-alsamixer type


```
gnome-alsamixer

```
check all settings, make sure nothing is muted

---

### Post by linux_tech on 2009-01-18
Open Gnome alsamixer, select edit > sound card properties, make sure mic is checked

---

### Post by s0mmer on 2009-01-18
Downloadede the gnome alsamixer and tried to unmute everything. But when i start the sound recording application i cant record. I turned microphone and the booster to the max.

---

### Post by linux_tech on 2009-01-18
try running this again
```


cat /proc/asound/card0/codec#* | grep Codec


```

---

### Post by s0mmer on 2009-01-18
s0mmer@s0mmer-ubuntu:~$ cat /proc/asound/card0/codec#* | grep Codec
Codec: Analog Devices AD1984

---

### Post by linux_tech on 2009-01-18
Is this a thinkpad?

---

### Post by s0mmer on 2009-01-18
Yes it is. And the microphone is buildt in. Is it then a internal mic or docking mic ?

---

### Post by linux_tech on 2009-01-18
The thinkpad internal mics can be problematic
But give this a try
1st open /etc/modprobe.d/alsa-base:

```

gksudo gedit /etc/modprobe.d/alsa-base

```
Either modify (you may have one like it already) or add this line with "options"
```

options snd-hda-intel model=thinkpad

```
you will need to reboot, or you you can try:
```

sudo alsa force-reload

```
then test mic again

if options snd-hda-intel model=thinkpad

doesn't make any difference for mic, then try

options snd-hda-intel model=basic

---

### Post by s0mmer on 2009-01-18
Now we are close! The thinkpad model didn't do much but the basic make a front mic come up, and after i enabled that i can now see the "level" changing with the sound of my voice in the sound recording. but when i play it i cant hear it ? Maybe some capture .. ?

---

### Post by linux_tech on 2009-01-18
open Gnome alsamixer, on far right make sure rec is checked, increase capture slider

---

### Post by linux_tech on 2009-01-18
Open volume control and check all settings as described here:
[http://ubuntufs.wordpress.com/2006/06/08/trouble-with-your-microphone/](http://ubuntufs.wordpress.com/2006/06/08/trouble-with-your-microphone/)

Let me know if there are any issues

---

### Post by s0mmer on 2009-01-19
Sorry for my slow reply :)

I finally got the microphone working and my sound runs too! But when i try to use skype i cant get it working with none of the skype configurations. Do you got any expierence with skype? Like the sound in: HDA intel(hw:intel,0) i really dont know what that means...

---

