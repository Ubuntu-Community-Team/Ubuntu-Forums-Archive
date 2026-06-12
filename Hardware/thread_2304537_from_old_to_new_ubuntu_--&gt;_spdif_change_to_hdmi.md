---
title: "from old to new ubuntu --&gt; spdif change to hdmi"
date: 2015-11-27
forum: Hardware
---

### Post by lorenzo25 on 2015-11-27
Hello world,
  i had one ubuntu 12.10 on my home theatre (pc i3 4GB with 1,5 Tb hd), the motherboard is one AsRock h550M Pro with audio chip onboard (7.1 CH HD Audio - VIA VT1708S Audio Codec), and i used the spdif digital output connected to my amplifier... and i listened one perfect 3.1 audio output (xbmc-kodi  and tvheadend for the television). I decided to upgrade all the system to the last ubuntu release 15.10, but my digital output 7.1 spdif was transformed to hdmi only stereo. I tried to install ubuntu 13.10, 14.10 but i have the same problem... only with 12.10 the spdif output comeback...


in 15.10... i try this command:


```
>cat /proc/asound/cards
 0 [MID            ]: HDA-Intel - HDA Intel MID
                      HDA Intel MID at 0xfbaf8000 irq 25



```


```
>cat /proc/asound/card0/codec* | grep Codec
Codec: VIA VT1718S
Codec: Intel IbexPeak HDMI
```


```
>aplay -l 
**** Lista di PLAYBACK dispositivi hardware ****
scheda 0: MID [HDA Intel MID], dispositivo 0: VT1718S Analog [VT1718S Analog]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
scheda 0: MID [HDA Intel MID], dispositivo 2: VT1718S Alt Analog [VT1718S Alt Analog]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
scheda 0: MID [HDA Intel MID], dispositivo 3: VT1718S Digital [VT1718S Digital]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
scheda 0: MID [HDA Intel MID], dispositivo 7: HDMI 0 [HDMI 0]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
scheda 0: MID [HDA Intel MID], dispositivo 8: HDMI 1 [HDMI 1]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
```



do you know where is the problem?


another solution i think is to re-install ubuntu 12.10 and search the configuration/device differences to 15.10, but i don't know where search this difference and the mode to apply it to 15.10...


help me... 
  Thankyou at all


Lorenzo

---

### Post by weatherman2 on 2015-11-27
Look more carefully at the controls in audio settings.  In the newer versions of Ubuntu, the way to select the correct digital output has changed.  I know the first time I tried to select digital optical out instead of analog it took me a few minutes to figure it out, because the options were in different spots vs. older versions.

---

### Post by grahammechanical on 2015-11-27
Also, Sound Settings is kind of like plug & play. Plug in the headphones and an option to select headphones as an output appears. Plug an audio cable into line-out and an option to select line-out as an output appears. Make an HDMI cable connection between the Monitor and the graphic adapter and an HDMI/Display port output appears and the sound will be directed over the HDMI cable to the monitor speakers.

Regards.

---

### Post by blm-ubunet on 2015-11-27
Your PC has 2 audio devices :-
- onboard mobo audio (analogue & spdif I/O)
- hdmi

Both can support S/PDIF digital output.
One or both of these could fix it.
Run alsamixer(gui) select right audio device & then select approp. codec/mixer & unmute.
Install/run "pavucontrol" select the onboard audio device & configure it to be digital spdif I/O.

Kodi can use the pulse audio device or alsa device directly, it should have been able to be configured to work.

---

### Post by lorenzo25 on 2015-11-28
Hello all... tx for yours information...

the alsamixer outputs was all unmute and with max volume...

i have installed pavucontrol and in the configuration tab i find the "digital stereo hdmi output" (that when active use the digital output to the amplifier and i listen the sound correctly), the  "digital stereo hdmi 3 output" (used correctly connected at my stereo television) and a lot of Unplugged other selections... one of this is "digital sourround 5.1 hdmi 2 output (unplugged)"... but I not able to resolve the problem...

i try to plug out and plug in all cables... but nothing... 
i don't find another option to set the spdif output in pavucontrol or alsamixer (where the spdif1, spdif2, spdif3 are active) to correct the problem...

any other ideas?

tx

---

### Post by blm-ubunet on 2015-11-28
Maybe I don't understand what the problem is..

You have (2) audio connections ?
1 HDMI to AVR/HT-amp then hdmi to TV
2 S/PDIF (coax or TOSLink) to TV ?

Is connection 2 just analogue stereo 3.5mm? That's not S/PDIF.

Kodi, VLC & MythTV are all able to output directly to the alsa device of your choice.
They can all just use the system wide audio settings (pulse).

In pavucontrol "Output Devices" tab select the non-HDMI device. Then use "Configuration" tab to set the output config to Digital IEC958..
Think you can also tick the required capabilities (AC3, DTS etc)

---

### Post by lorenzo25 on 2015-11-28
ok.. sorry i try to explain better...
i have
1) one hdmi connected to the television (no problem)
2) one spdif (optical cable) connected to the amplifier (this is my problem)

connected to the amplifier i have dolby 3.1 loudspeakers... but the hdmi connection (was spdif in 12.10 ) to the amplifier is only stereo (i can use only 2 loudspeakers). In pavucontrol all other connections are indicate as unplugged... if i select for example the dolby 5.1 output, I configure it in pavucontrol (also if is indicate as unplugged) but i can't select this output in ubuntu. Into ubuntu sound settings i have only:

"digital stereo hdmi 3 output" --> when selected I listen sound in television (perfect! no problem)
"digital stereo hdmi output" --> when selected I listen sound in the amplifier (perfect!) but only in two loudspeakers - stereo (this is the problem)... i want use all other two loudspeakers: all the digital dolby surround 3.1.

in the pavucontrol i can't select other output (only stereo) in the "digital stereo hdmi output"... and so I don't able to use my dolby 3.1 loudspeakers..

I don't understand if i can use kodi to use the 3.1 dolby output even if ubuntu does not recognize it...??

thankyou for all support...

---

### Post by blm-ubunet on 2015-11-28
Don't use the simple audio control app in ubuntu.
Make pavucontrol the default audio/sound control app.
Pulse audio is the default system wide audio server in ubuntu.

Multi-channel audio (>2ch) over S/PDIF is **only **possible with "digital pass-through" & matrix encoding to either AC3 or DTS **only**.
There is no auto-detection of the jack and no operating capabilities of receiver (ELD).

The "Digital Dolby AC5.1 output" is a misnomer, it is discrete analogue 6 outputs (3 stereo jacks), you do not want this.

pavucontrol:
With this device selected "digital stereo hdmi output" you need to tickbox select the capabilities of amp (AC3, DTS)
Click the well hidden "Advanced" drop-down gadget & then select AC3 & DTS (if your does this).

Are you sure you don't have an output device called "Digital Stereo (IEC958) Output" ?
It is very odd that the S/PDIF output (from mobo) is called "digital stereo hdmi output"..
But HDA HDMI can support S/PDIF multichannel "encoded" pass-through AC3 & DTS.

Many multimedia programs are able to scan/select/test the alsa audio devices directly & they can & do temporarily disable the pulseaudio server when running.
Disabling the pulse server prevents all/any other audio outputs (not entirely true but close enough).

---

### Post by lorenzo25 on 2015-11-28
FANTASTIC!!!! 
after the selection of DTS and AC3... i listen the 3.1 sound in my amp... fantastic!!!!

Thank you very very very much... blm-ubunet!!!! ... I'm very happy now! :-)

ps. I don't have one output device called "Digital Stereo (IEC958) Output" or similar... but the "digital stereo hdmi output" run ok...

---

