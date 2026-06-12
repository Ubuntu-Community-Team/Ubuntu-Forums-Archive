---
title: "Sound Blaster X-Fi not working properly on Kubuntu (i have sound but no surround)"
date: 2010-05-29
forum: Hardware
---

### Post by Istrebitel on 2010-05-29
Greetings.

I am a newbie to linux and i decided to try kubuntu after reading over the webs. I got lastest 10.04 release of kubuntu installed (downloaded yesterday). 

Out of the box i got sound playing but it only does via front 2 speakers and i have a 5.1 and on windows i got used to having sound surround (even if i listen to stereo the x-fi driver will reroute it to the back speakers and make it feel like its a surround).

First i tried Creative drivers for linux. I dl'ed them and tried to install but i got this:

```
make -C /lib/modules/2.6.31-14-generic-pae/build M=/home/mark/Desktop/XFiDrv_Linux_Public_US_1.00
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic-pae'
  CC [M]  /home/mark/Desktop/XFiDrv_Linux_Public_US_1.00/xfi.o
/home/mark/Desktop/XFiDrv_Linux_Public_US_1.00/xfi.c:14:26: error: sound/driver.h: No such file or directory
/home/mark/Desktop/XFiDrv_Linux_Public_US_1.00/xfi.c: In function &#8216;ct_card_probe&#8217;:
/home/mark/Desktop/XFiDrv_Linux_Public_US_1.00/xfi.c:55: error: implicit declaration of function &#8216;snd_card_new&#8217;
/home/mark/Desktop/XFiDrv_Linux_Public_US_1.00/xfi.c:55: warning: assignment makes pointer from integer without a cast
make[2]: *** [/home/mark/Desktop/XFiDrv_Linux_Public_US_1.00/xfi.o] Error 1
make[1]: *** [_module_/home/mark/Desktop/XFiDrv_Linux_Public_US_1.00] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic-pae'
make: *** [all] Error 2
```

like the person here [http://ubuntuforums.org/showthread.php?t=1304627](http://ubuntuforums.org/showthread.php?t=1304627)

I googled and looked the webs but i found nothing on the matter. It just looks like the problem does not exist! There are numerous tutorials that say "run this" and dont even mention that it DOES NOT WORK! 

Then i stumbled upon a post that stated "you dont need creative drivers anymore since now alsa supports it all". I didnt knew what alsa is by that moment.

Then on the webs i found ppl that tell to edit a file with gedit .asoundrc
like here [http://ubuntuforums.org/showpost.php?p=7736411&postcount=432](http://ubuntuforums.org/showpost.php?p=7736411&postcount=432)

But this file does not exist! It opens a blank file! From what i understood from googling is that this is a config file for alsa and because i dont have it i supposed maybe i dont have the alsa installed. 

So secondly i downloaded this alsa and followed the instructions to install it. It has all gone well until the step after "make install" when i have to "modprobe snd-(my audio device)". Well i dont see anything close to Creative Sound Blaster X-Fi in the list... is it sb-16? doubt that ... Anyway my sound card dropped dead that very moment (something in the corner of the screen complained about sound card failure) and i supposed maybe i have to reboot. I did it, now i have my sound back but no surround and no file and nothing changed...

Can anyone give any insight on this?

---

### Post by kansasnoob on 2010-05-29
Would you please post the output of:

```
lspci | grep VGA
```

---

### Post by kansasnoob on 2010-05-29
It's possible that the Medibuntu package "alsa-firmware" may work with that but need to see the requested output.

> A collection of firmwares for some sound cards:
 aica - Sega Dreamcast AICA
echoaudio - Digigram Echo Audio based cards
emu - E-Mu based cards
hdsploader - RME Hammerfall DSP cards
maestro3 - ESS Maestro3 PCI cards
mixartloader - Digigram miXart cards
pcxhrloader - Digigram pcxhr compatible cards
sb16 - Sound Blaster 16 cards
usx2yloader - Tascam USX2Y USB cards
vxloader - Digigram VX cards
wavefront - Turtle Beach Wavefront cards
ymfpci - Yamaha DS-1 PCI cards


[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

I'll check back later :)

---

### Post by lidex on 2010-05-30
Which one is it?
```
aplay -l
```
[http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs]("http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs")

Also, you may need to select the correct configuration in pulseaudio volume control (pavucontrol).

---

### Post by master-m on 2010-05-30
Hi,

am I allowed to participate in this discussion instead of Istrebitel?
I have exactly the same "problem".
I am using optical out of the following card: aplay -l
```
card 0: XFi [Creative X-Fi], device 0: ctxfi [Front/WaveIn]
  Subdevices: 7/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: XFi [Creative X-Fi], device 1: ctxfi [Surround]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: XFi [Creative X-Fi], device 2: ctxfi [Center/LFE]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: XFi [Creative X-Fi], device 3: ctxfi [Side]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: XFi [Creative X-Fi], device 4: ctxfi [IEC958 Non-audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```This is connected to a receiver which  shows that there are always two channels. If I'm under Win7, I am able to turn on the encoder of the card, which turns everything (more or less) to 5.1 Surround. The problem with this is that the card seems to send a constant signal to the receiver, which is bad for Win, because it always fails to shutdown.
Don't know if the driver in linux is able to turn on the encoder or something like that.
I am using Kubuntu 10.04 (yesterday upgraded from 9.10).
In the System Settings->Multimedia I can choose S/PDIF, but this also is only Stereo, but i little bit louder! :) Furthermore I can choose "Creative X-Fi 20K2 Unknown (Surround)" which produces no sound at all.
To complete the facts, the output of lspci:
```
05:00.0 Audio device: Creative Labs X-Fi Titanium series [EMU20k2] (rev 03)
```Is the output of > lspci | grep VGA  really necessary?

Would be nice to have working surround in linux, but I think this card is a little bit strange, because of the story with Win.

bye,
Martin

---

### Post by Istrebitel on 2010-05-31
Sorry for being inactive, when i have time to work on my kubuntu i will provide the asked logs (i understand switching os'es should not be easy, but so far i cannot do my regular pc tasks on kubuntu, and the problems are piling up one on another, not having a clear solution, so i had to revert to windows for the present moment, until i have more free time to study this kubuntu...)

---

### Post by Istrebitel on 2010-05-31
output of
lspci | grep VGA
is
\01:00.0 VGA compatible controller: nVidia Corporation GT200 [GeForce GTX 280] (rev a1)

and output of 
aplay -l
is
```
**** List of PLAYBACK Hardware Devices ****
card 0: XFi [Creative X-Fi], device 0: ctxfi [Front/WaveIn]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: XFi [Creative X-Fi], device 1: ctxfi [Surround]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: XFi [Creative X-Fi], device 2: ctxfi [Center/LFE]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: XFi [Creative X-Fi], device 3: ctxfi [Side]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: XFi [Creative X-Fi], device 4: ctxfi [IEC958 Non-audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by Istrebitel on 2010-06-02
bump aka still looking for help on this matter

---

### Post by PyrO_PrOfessOr on 2010-06-04
X2 I too am having this problem. My output for aplay -l is the same as everyone else's here, the only difference is I am using an AMD 4870X2 instead of a GTX280.

I have tried all the usual sound configurations bits and pieces in systems settings but just can get anything better than 2.1

Would really appreciate some help on this too, especially as creative has such a bad track record of support on linux. I had hoped with alsa supporting it we could finally have some sweet sound from Kubuntu.

---

### Post by Istrebitel on 2010-06-05
bump aka still looking for help on this

---

### Post by Istrebitel on 2010-06-07
bump ... at least maybe someone can tell us "NO there is no solution dont keep trying" and explain why there isnt so we would start looking for other ways (another audio card?...)

---

### Post by Istrebitel on 2010-06-10
Update!

Very odd but i might have a fix for it! So, i have installed Ubuntu. And in Ubuntu, in System Preferences Sound i found that my card has a myriad of options to choose from! On Hardware tab, Settings for this device.

BUT! If i select 5.1 (which i AM using), it wont work. It makes very glitchy sound. Almost unhearable due to scratching, like someone's tearing a vinyl while it's being played. 

BUT! If (and only if) i select first something.0 mode (stereo, 4.0,...), and then 7.1 mode, i get a working surround! If i select 7.1 mode after anything.1, it wont (same glitches). If i select 5.1 mode after something.0, it wont. Only 7.1 after something.0. 

For an odd reason, subwoofer slider does nothing, but taking it further left also moves volume slider to the left without actually changing the volume and vice versa, thus it allows for louder max volume if set to minimum and lower maximum volume if set to maximum.

I had to tweak front-back balance to achive sound in the right position, but overall, i must say that it KINDA works.

Now, maybe someone with knowledge can tell me where to dig now to make the surround fully work? (i mean, in 5.1 mode, or with subwoofer, its kinda dead now i'm feeling, mean its not doing any woofing...)

---

