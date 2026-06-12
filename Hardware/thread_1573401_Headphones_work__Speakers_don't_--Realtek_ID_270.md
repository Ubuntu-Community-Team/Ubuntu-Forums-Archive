---
title: "Headphones work:  Speakers don't --Realtek ID 270"
date: 2010-09-12
forum: Hardware
---

### Post by dan l on 2010-09-12
I'm trying to troubleshoot this:

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: HDA Generic [HDA Generic]
  Subdevices: 0/1
  Subdevice #0: subdevice #0


I think that means it doesn't see the speakers.  

I've been around the googles and haven't found anything with that aplay-l output, so I could use some guidance.

---

### Post by dan l on 2010-09-12
Alright, I'm going through this:  [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)


```
--------
dan@dan-laptop:~$ aplay /usr/share/sounds/alsa/Front_Center.wav
Playing WAVE '/usr/share/sounds/alsa/Front_Center.wav' : Signed 16 bit Little Endian, Rate 48000 Hz, Mono
---------
```

Audio plays through the headphones, not the speakers.  Just for clarity:  I unplugged the headphones and the audio did not come through the speakers.  

```
-------
dan@dan-laptop:~$ fgrep -ie 'audio' /etc/group
audio:x:29:
-------
```

I am not in the audio group.  I don't know what this means.  


```
------
dan@dan-laptop:~$ sudo aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: HDA Generic [HDA Generic]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
dan@dan-laptop:~$ 
------
```

Apparently this didn't mean what I thought it would mean.  

```
------
find /lib/modules/`uname -r` | grep snd
------
```
Test pass would be a 'whole list'.  I get a big list of files like this "/lib/modules/2.6.32-24-generic/kernel/sound/soc/codecs/snd-soc-wm8753.ko
"

```
-----
lspci -v | less
-----
```

Returns:  
```
-----
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
        Subsystem: Hewlett-Packard Company Device 1444
        Flags: bus master, slow devsel, latency 64, IRQ 16
        Memory at d0400000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel


-----
```

Is the access denied part bad?  


--

I tried to find the soundcard here:  [http://www.alsa-project.org/main/index.php/Matrix:Main](http://www.alsa-project.org/main/index.php/Matrix:Main) and I can't seem to find it.  Though, I think I'm probably looking in the wrong place.  


---

I did run the diagnostic script on the alsa site.  If somebody wants, I'll pastebin it.

---

### Post by Alan James on 2010-09-13
Okay, I know this sounds really stupid but did you check the volume? In Kubuntu the volume of Speakers is by default set to off. Every time I reinstall I go through about 2 mins of trying to figure out why only some of my sound is working before I remember to just turn it up.

Right click on the speaker icon in the System Tray. Click on Select Master Channel. In the dialog box click on PCM then click ok. Then turn up the sound by left clicking the speaker icon and turning up the sound.

Do this for all the items on the Master Channel list. In the end reselect Master and make sure it is all the way up. 

This is usually my problem. I hope this will fix your problem.

---

### Post by dan l on 2010-09-13
Thank you.  And yes, Digital, PCM, and Volume are up.  PCM and master both change the head phone volume.  I don't think digital does anything that I can see.

---

### Post by felipemartim on 2010-10-07
Try this: [http://ubuntuforums.org/showthread.php?p=9935365#post9935365](http://ubuntuforums.org/showthread.php?p=9935365#post9935365)

---

