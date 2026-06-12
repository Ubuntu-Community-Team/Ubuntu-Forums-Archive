---
title: "HDA Intel PCH: Generic Analog **17.10 Work-around***"
date: 2017-10-18
forum: Hardware
---

### Post by royleith on 2017-10-18
I don't know where the actual problem is, but for the following system, Line Out audio is fine, but Line In does not work with either Kubuntu 16.10 or Ubuntu Studio 16.04.

USB audio interfaces are fine.

Motherboard: ASUS ROG STRIX Z270G-GAMING LGA1151 Micro-ATX
Intel® Z270 Chipset
Bios/UEFI : American Megatrends Inc._128 Mb Flash ROM, UEFI AMI BIOS, V1009 from ASUS
Audio: ROG SupremeFX 8-Channel High Definition Audio CODEC S1220A
Intel 7th Gen Core i3 7100T
Built-in HD audio 2/4/5.1/7.1 channel with optical out

The hardware appears as HDA Intel PCH: Generic Analog and does stereo to 7.1 audio out.
Only the Stereo audio device supports Line In.

I installed the latest Alsa drivers in both OSs and got sound in Ubuntu Studio, but not in Kubuntu. In Kubuntu, the sound recorded, but played back very quickly (x 100?) After a few updates, both result in recording the same continuous crackling either using arecord or audacity.

Could it be that there is a conflict between the Intel HDA audio in the Motherboard Intel® Z270 Chipset and the ROG Audio CODEC S1220A?

Just to confirm, Line Out audio is absolutely fine.

---

### Post by royleith on 2017-11-04
I have just discovered that:

  The Line Input works fine with jack (in Ubuntu Studio).

  Audacity will not load at the same time as jack and jack will not load if Audacity is running.

That does suggest that it is an audacity problem, except that arecord (one of the alsa-utilities) has the same problem as audacity. Since I cannot get the Windows version of audacity to work in wine, I am using Windows Reaper in Wine/WineASIO/jack to record from Line In or using a Behringer (Line) or Focusrite (Mic/Line/Inst) USB audio interface.

---

### Post by royleith on 2018-01-31
I have upgraded to Kubuntu 17.10 (a complete new install except for /home) and the problem still exists with arecord and aplay and with audacity. One change is that audacity fastplay used to be able to just about slow audio to the correct speed. Now it has no effect.

---

### Post by royleith on 2018-01-31
I tried using the install DVD in 'Live' mode. Still the same problem in audacity (installed for the test) and arecord/aplay. Rebooted and tried arecord/aplay and **it worked perfectly**. audacity still had the problem and running audacity and closing it stops aplay from working.

The following runs perfectly after a reboot.

roy@quietpc:~$ arecord -d 5 -f cd -D  hw:0,0 audiotest.wav
Recording WAVE 'audiotest.wav' : Signed 16 bit Little Endian, Rate 44100 Hz, Stereo
roy@quietpc:~$ aplay audiotest.wav

After running audacity the arecord line takes much longer than five seconds and plays back at very high speed.

audacity is doing something to alsa or pulse audio. 

Whilst trying to get the names of the cards for the arecord line, I found that, although alsa-utils is installed, alsamixer and amixer fail with,

roy@quietpc:~$ alsamixer
cannot open mixer: No such file or directory

even after a fresh reboot.

---

### Post by Yellow Pasque on 2018-01-31
I would get an alsa info before and after running Audacity to see if anything changed at the ALSA level:
```
cd ~/
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh
bash alsa-info.sh   #Choose to save file locally
(Run Audacity)
bash alsa-info.sh   #Choose to save file locally
diff /tmp/alsa-info.txt.*
```

Please share one of the copies here (use code tags as it's a lot of text). Or you can run alsa-info again and choose to upload it and share the link.

---

### Post by royleith on 2018-02-02
> **Temüjin said:**
> I would get an alsa info before and after running Audacity to see if anything changed at the ALSA level:
```
cd ~/
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh
bash alsa-info.sh   #Choose to save file locally
(Run Audacity)
bash alsa-info.sh   #Choose to save file locally
diff /tmp/alsa-info.txt.*
```

Please share one of the copies here (use code tags as it's a lot of text). Or you can run alsa-info again and choose to upload it and share the link.

A search of the audacity web-site indicated that this is a problem with Pulse Audio (surprise, surprise!). The workaround they suggested was to use the alsa hardware port rather than the Pulse Audio port. This worked after a reboot.  Leaving audacity set at the alsa Line In port keeps it working. I did not discover this for myself because I did not realise that alsa had been discombooberated and that a reboot was required to get it going again.

It then proved difficult to break audacity, but I finally succeeded!:cool:

The diff gave,

```
6c6
< !!Script ran on: Fri Feb  2 17:05:36 UTC 2018
---
> !!Script ran on: Fri Feb  2 16:59:55 UTC 2018
294c294
<   Converter: stream=2, channel=0
---
>   Converter: stream=0, channel=0
643,644c643,644
< crw-rw----+ 1 root audio 116,  4 Feb  2 17:04 /dev/snd/pcmC0D0c
< crw-rw----+ 1 root audio 116,  3 Feb  2 17:05 /dev/snd/pcmC0D0p
---
> crw-rw----+ 1 root audio 116,  4 Feb  2 16:58 /dev/snd/pcmC0D0c
> crw-rw----+ 1 root audio 116,  3 Feb  2 16:58 /dev/snd/pcmC0D0p
646c646
< crw-rw----+ 1 root audio 116,  6 Feb  2 17:04 /dev/snd/pcmC0D2c
---
> crw-rw----+ 1 root audio 116,  6 Feb  2 16:58 /dev/snd/pcmC0D2c
```

The initial alsa-info file is:
[https://paste.ubuntu.com/26506736/](https://paste.ubuntu.com/26506736/)

I don't understand what this means, but I did find that the ports available in audacity changed after the fault was instigated. The diff seems to suggest that the audio devices have been changed in some way.

---

### Post by Yellow Pasque on 2018-02-02
> It then proved difficult to break audacity, but I finally succeeded
I'm confused. Does this mean it breaks in the same way using ALSA input as Pulsaudio input, but the ALSA input takes a lot longer to break?

> I don't understand what this means, but I did find that the ports available in audacity changed after the fault was instigated. The diff seems to suggest that the audio devices have been changed in some way. 
I don't see anything significant in the diff (timestamp change is expected).

---

### Post by royleith on 2018-02-03
Hi Temüjin,

My problem was that, having got it working with the alsa hardware port selected, it continued to work when the Pulse Audio port was selected. I had to close audacity down and restart it before it exhibited the previous symptoms.

BTW, I tried to use the same workaround (using alsa ports) in UbuntuStudio 16.10 and it would not work. Only after upgrading to US 17.10 was the work-around successful

---

