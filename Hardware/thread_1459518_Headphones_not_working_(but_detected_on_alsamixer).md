---
title: "Headphones not working (but detected on alsamixer)"
date: 2010-04-21
forum: Hardware
---

### Post by mfnano on 2010-04-21
Hi,

My headphones used to work on ubuntu on my dell studio 1558, but when I reinstalled the system they seems to stop working.

When I plug them in I don't hear anything, the speaker stop working but there is no sound on the headphones.

The headphone is detected on alsa mixer, and they work normally on Windows, I tried this workaround here [http://ubuntuforums.org/showthread.php?t=302543&page=2]("http://ubuntuforums.org/showthread.php?t=302543&page=2") without a solution.

Any idea how to get them to work, thank you.
> laptop:~$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf0b00000 irq 22
 1 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xcfeec000 irq 17

---

### Post by lidex on 2010-04-22
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.

---

### Post by pgmac on 2010-04-27
Hi,
I was having the exact same problem on my Dell Studio 1558 (sound through the speakers, but none when using headphones).  After some more google-ing around, I found this doco: [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

I found my card model using this:
```
cat /proc/asound/card0/codec#* | grep Codec
```
which returned:
```
Codec: IDT 92HD73C1X5
```

This file: /usr/share/doc/alsa-base/driver/HD-Audio-Models.txt.gz lists the sound models with available modprobe modules to use.
```
zless /usr/share/doc/alsa-base/driver/HD-Audio-Models.txt.gz
```
The full model number wasn't in there, because the model has been wildcarded.  I searched for ```
92HD73
```

In this section there are several PC models listed, find the one that best suites you (I used 'dell-eq').
After a reboot, I had headphone sound again.

Cheers,
Paul

---

### Post by tomask on 2010-05-13
Thank you for the post pgmac,

Just what I needed to fix headphone sound on the same Dell studio 1558.

I do not want to moan about others, especially when they volunteer ... this problem is quite old ... so without your post, I'd probably be lost ...

Hello Dell maybe you can volunteer some to help to fix this in alsa ...

---

### Post by balaoko on 2010-05-13
Many thanks, pgmac. It worked for my dell 1558!

---

### Post by commonplace on 2010-05-19
Thanks! Fixed my wife's headphone problem on her Dell Studio 1558.

/Kevin

---

### Post by venkidwaraka on 2010-05-21
Thank you very much for this post.:KS
It really fixed my issue.

Venk!!:guitar:

---

### Post by Simon_WM on 2010-05-22
sorry or the noobie question, but do you type this commands into terminal?

---

### Post by Yellow Pasque on 2010-05-22
> **Simon_WM said:**
> sorry or the noobie question, but do you type this commands into terminal?
```
gksu gedit /etc/modprobe.d/alsa-base.conf
```
Add this line at the end:
```
options snd-hda-intel model=dell-eq
```
Save and quit. The setting will take effect on next reboot.

---

### Post by Simon_WM on 2010-05-22
> **pgmac said:**
> Hi,
I was having the exact same problem on my Dell Studio 1558 (sound through the speakers, but none when using headphones).  After some more google-ing around, I found this doco: [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

I found my card model using this:
```
cat /proc/asound/card0/codec#* | grep Codec
```which returned:
```
Codec: IDT 92HD73C1X5
```This file: /usr/share/doc/alsa-base/driver/HD-Audio-Models.txt.gz lists the sound models with available modprobe modules to use.
```
zless /usr/share/doc/alsa-base/driver/HD-Audio-Models.txt.gz
```The full model number wasn't in there, because the model has been wildcarded.  I searched for ```
92HD73
```In this section there are several PC models listed, find the one that best suites you (I used 'dell-eq').
After a reboot, I had headphone sound again.

Cheers,
Paul

HI Paul,

How did you select " dell-eg " and reboot, 
i've followd the steps in " Terminal" but hasent worked for me =[
it also say:
zless /usr/share/doc/alsa-base/driver/HD-Audio-Models.txt.gz - Permission Denied :(

* * EDIT * *

Hi All,
re-read the post and wrote full command into Terminal.. and almost fixed =]
Am Stuck on how to select " dell-eg "

---

### Post by lidex on 2010-05-22
> **Simon_WM said:**
> HI Paul,

How did you select " dell-eg " and reboot, 
i've followd the steps in " Terminal" but hasent worked for me =[
it also say:
zless /usr/share/doc/alsa-base/driver/HD-Audio-Models.txt.gz - Permission Denied :(

* * EDIT * *

Hi All,
re-read the post and wrote full command into Terminal.. and almost fixed =]
Am Stuck on how to select " dell-eg "
Don't worry about that. If you want to use dell-eq (that's a q, not a g), do as directed in post #9. This is entered in a terminal:
```
gksu gedit /etc/modprobe.d/alsa-base.conf
``` and will open the file in your text editor. There you will add the options line.

---

### Post by Nihilor on 2010-05-31
How would i apply this fix (which worked for me in gnome on 10.04) to Kubuntu 10.04 which i am now running. it is a clean install and of course these commands do not work. I am very new to linux and would appreciate step by step commands for the Konsole that would help out quite a bit :-)

---

### Post by lidex on 2010-05-31
> **Nihilor said:**
> How would i apply this fix (which worked for me in gnome on 10.04) to Kubuntu 10.04 which i am now running. it is a clean install and of course these commands do not work. I am very new to linux and would appreciate step by step commands for the Konsole that would help out quite a bit :-)

Maybe this:
```
kdesudo kate /etc/modprobe.d/alsa-base.conf
```

---

### Post by Nihilor on 2010-06-01
worked like a charm this fixes all of my install bugs (until i find more) ty

---

### Post by dzajic on 2010-06-01
I get sound out of built-ins, but neither of the 2 headphone jacks. The previously mentioned alsa-base.conf line addition does not work for me.  This is a brand new Studio 15 with the Arrandale Core I5.

I'm running a patched kernel (2.6.32-21) to fix the suspend/resume problem, so could that be the problem? I doubt it, but what do I know?

---

### Post by lidex on 2010-06-01
> **dzajic said:**
> I get sound out of built-ins, but neither of the 2 headphone jacks. The previously mentioned alsa-base.conf line addition does not work for me.  This is a brand new Studio 15 with the Arrandale Core I5.

I'm running a patched kernel (2.6.32-21) to fix the suspend/resume problem, so could that be the problem? I doubt it, but what do I know?

Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#* 
```
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

Also, have you tried alsamixer?
**Alsamixer**
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.

I usually suggest gnome-alsamixer for enabling soundcard elements, but that's for gnome. Is kmix equivalent in kde?

---

### Post by dzajic on 2010-06-01
Dell Studio 1558

```

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Advanced Linux Sound Architecture Driver Version 1.0.21.

==> /proc/asound/card0/codec#0 <==
Codec: IDT 92HD73C1X5

==> /proc/asound/card0/codec#3 <==
Codec: Intel G45 DEVIBX

```

---

### Post by lidex on 2010-06-01
> **dzajic said:**
> Dell Studio 1558

```

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Advanced Linux Sound Architecture Driver Version 1.0.21.

==> /proc/asound/card0/codec#0 <==
Codec: IDT 92HD73C1X5

==> /proc/asound/card0/codec#3 <==
Codec: Intel G45 DEVIBX

```

Try these options - only one line at a time. You'll need to reboot to see changes and then check alsamixer.
```
options snd-hda-intel model=dell
options snd-hda-intel model=dell-bios
options snd-hda-intel model=dell-m6
options snd-hda-intel model=ref
options snd-hda-intel model=auto
```

---

### Post by dzajic on 2010-06-02
> **lidex said:**
> Try these options - only one line at a time. You'll need to reboot to see changes and then check alsamixer.
```
options snd-hda-intel model=dell
options snd-hda-intel model=dell-bios
options snd-hda-intel model=dell-m6
options snd-hda-intel model=ref
options snd-hda-intel model=auto
```

Thanks for the tips. I tried them all. No dice. Not sure what I'm supposed to do in alsamixer. I was supposed to add these lines to the end of the /etc/modprobe.d/alsa-base.conf, right?

---

### Post by lidex on 2010-06-02
You may need to enable it. Try gnome-alsamixer.
**Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
**Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.
To install:
```
sudo apt-get install gnome-alsamixer
```

Go to sound preferences and select headphones in the output tab/connector.

---

### Post by kchings on 2010-06-05
> **pgmac said:**
> Hi,
I was having the exact same problem on my Dell Studio 1558 (sound through the speakers, but none when using headphones).  After some more google-ing around, I found this doco: [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

I found my card model using this:
```
cat /proc/asound/card0/codec#* | grep Codec
```
which returned:
```
Codec: IDT 92HD73C1X5
```

This file: /usr/share/doc/alsa-base/driver/HD-Audio-Models.txt.gz lists the sound models with available modprobe modules to use.
```
zless /usr/share/doc/alsa-base/driver/HD-Audio-Models.txt.gz
```
The full model number wasn't in there, because the model has been wildcarded.  I searched for ```
92HD73
```

In this section there are several PC models listed, find the one that best suites you (I used 'dell-eq').
After a reboot, I had headphone sound again.

Cheers,
Paul
Thanks, this works for my Gateway E-155 too!

These are what my laptop returns:
Codec: SigmaTel STAC9205
Codec: LSI ID 1040

STAC9205/9254
=============
  ref           Reference board
  dell-m42      Dell (unknown)
  dell-m43      Dell Precision
  dell-m44      Dell Inspiron
  eapd          Keep EAPD on (e.g. Gateway T1616)
  auto          BIOS setup (default)

And then I followed Temüjin 's advice,

but replaced dell-eq with eapd. It works great! thanks guys.

---

