---
title: "Gigaware USB Headset"
date: 2009-06-04
forum: Hardware
---

### Post by TonyFordz on 2009-06-04
I have a Gigaware headset in which I bought at Radio Shack that is USB interface, and it works fine in programs on Ubuntu for playing movies, audio, and so on but will not work on anything online such as YouTube.com, PlayList.com, and so on. I have searched all over the web & so far have found nothing. Is there anyone that can help with this? The below picture is one that looks like my headset.

[IMG]http://rsk.imageg.net/graphics/product_images/pRS1C-3227619w345.jpg[/IMG]

Also the mic doesn't work in the recording programs but it works fine if I unmute it as fas as being able to hear myself just doesn't work to record anything.

---

### Post by TonyFordz on 2009-06-06
Wow a first time there is no help...

:icon_frown:

---

### Post by TonyFordz on 2009-06-18
Wow & still no help with this one...

---

### Post by djb0110 on 2009-06-24
I have a radio shack gigaware headset too. It works very well with everything  when I followed the following link:
[http://linuxowns.wordpress.com/2008/07/08/how-i-got-my-usb-headset-to-work/](http://linuxowns.wordpress.com/2008/07/08/how-i-got-my-usb-headset-to-work/)

That is, it worked very well until I unplugged the headset. Then I wound up following the directions again and its working again. So bookmark the url. There will be a slight variation on what you will see in the directions but just select the usb audio device (Alsa mixer) in the Default Mixer Tracks section. Hope this helps.

---

### Post by austinpsycho on 2009-07-04
easy solution: remove your pulseaudio package in synaptic or like this: ```
sudo apt-get remove pulseaudio
``` then set your usb headset as default alsa device by typing in ```
asoundconf list
```
mine looked like this:```
desktop:~$ asoundconf list
Names of available sound cards:
SB
default

``` so out of those; i knew SB wasn't it; so i set mine to default thusly:```
asoundconf set-default-card default
``` replace that second default with your device name and violla ;) it'll work ..  everywhere ;)

---

### Post by austinpsycho on 2009-07-04
i do suggest restarting after removing pulseaudio though

---

### Post by austinpsycho on 2009-07-04
oh and tony you'll only need to do the [FONT=monospace]set default card part... its not necessary to remove pulseaudio unless to get it to work you used the oss drivers when you selected your device in the audio section
[/FONT]

---

### Post by kostkon on 2009-07-04
> **austinpsycho said:**
> easy solution: remove your pulseaudio package in synaptic or like this: ```
sudo apt-get remove pulseaudio
``` then set your usb headset as default alsa device by typing in ```
asoundconf list
```
mine looked like this:```
desktop:~$ asoundconf list
Names of available sound cards:
SB
default

``` so out of those; i knew SB wasn't it; so i set mine to default thusly:```
asoundconf set-default-card default
``` replace that second default with your device name and violla ;) it'll work ..  everywhere ;)
No, sorry that's a messy solution.

Anyway, the thing you need to do is to install the *PulseAudio Device Chooser* (using *Synaptic*).

Run it, left-click on its icon in your system tray and select *Volume Control*.

In *Firefox* put a *Flash* video playing (obviously with sound) and then in the *PulseAudio* volume Control select the *Playback* tab. You should see the audio stream of *Flash* listed there.

Right-click on it and select *Move Stream...* and in the list that will appear select your USB headset. PulseAudio will remember your choice from now on.

You can set your headset as the default input and output device in the *Output Devices* and *Input Devices* tab respectively, by right-clicking on it entry there and enabling the *Default* option.

For more info regarding the above, check [this very helpful thread here]("http://ubuntuforums.org/showthread.php?t=1130384").

---

