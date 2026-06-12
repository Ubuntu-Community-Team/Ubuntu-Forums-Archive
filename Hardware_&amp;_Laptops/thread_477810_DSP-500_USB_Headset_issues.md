---
title: "DSP-500 USB Headset issues"
date: 2007-06-18
forum: Hardware &amp; Laptops
---

### Post by No Leaf Clover on 2007-06-18
Hello all
New linux user here, installed ubuntu 7.04 after some driver issues, got all the buttons on my mouse working, now I am looking to get my headset working.  Its a [Plantronics DSP-500]("http://www.plantronics.com/north_america/en_US/products/cat640035/cat1430032/prod440044"), a headset with a soundcard in-line.  Plugged in, the volume control on it works, I press vol up or down and it pops up on the screen accordingly, but alas, I have no sound, and I am assuming, no mic.  Tried doing some looking around on my own and cant seem to gather up too much good info on how to get it working.
Some information I managed to gather along the way:
The soundcard is recognized:

```
andrew@Drewbuntu:~$ cat /proc/asound/cards
 0 [CA0106         ]: CA0106 - CA0106
                      MSI K8N Diamond MB [SB0438] at 0xd880 irq 17
 1 [Headset        ]: USB-Audio - Plantronics Headset
                      Plantronics Plantronics Headset at usb-0000:00:0b.0-2, full speed
```

and when I go to /proc/asound/devices, I do believe I have located it on the list

```
andrew@Drewbuntu:~$ cat /proc/asound/devices
  2:        : timer
  3:        : sequencer
  4: [ 0- 0]: raw midi
  5: [ 0- 3]: digital audio playback
  6: [ 0- 3]: digital audio capture
  7: [ 0- 2]: digital audio playback
  8: [ 0- 2]: digital audio capture
  9: [ 0- 1]: digital audio playback
 10: [ 0- 1]: digital audio capture
 11: [ 0- 0]: digital audio playback
 12: [ 0- 0]: digital audio capture
 13: [ 0]   : control[B]
 14: [ 1- 0]: digital audio playback
 15: [ 1- 0]: digital audio capture
 16: [ 1]   : control
[/B]
```

Can anyone help me out? Im also interested in getting the microphone working if that has to be done separatly.  If you need any more information, please tell me (and telling me how to get it would be a help too =-)) and I would be more then willing to post it.

Thanks in advance.

---

### Post by No Leaf Clover on 2007-06-18
Well then, I have managed to get sound.  I jumped into linux and completly forgot about the gui tools.  I manage to have sound now, mind you I still have an issue.

System > Preferences > Sound
Went in there and switched all the settings to usb audio, and all the playbacks tested allright (minus the microphone, which didnt at all), but I can not control the volume.  When I click my volume control in-line or on the system panel bar, the bar slides, but to no effect, the volume stays the same.  Anyone experience any similar problem or know how to fix it?

---

### Post by John Hughes on 2007-06-22
[http://ubuntuforums.org/showthread.php?t=480930](http://ubuntuforums.org/showthread.php?t=480930)

This is a solution i have posted recently..... Today :) Hope it helps!!!

---

### Post by slowtrain on 2007-11-26
Hi folks:  I've been trying to get a DSP-500 headset working.  Have followed the advice here to the letter.  Have gotten sound in the headphones, but my mic simply doesn't record. (Also tried messing w/ alsamixer, also to no effect)  Not very good because I'm awfully dependent on Skype for mey work.  I'm running Gutsy Gibbon on an AMD64 X2 system.

I've been thinking of trying the advice out at two other links (see below), but am worried that these are dated and the changes could cause problems rather than fix them.  Any thoughts?

[http://ubuntuforums.org/showthread.php?t=32063](http://ubuntuforums.org/showthread.php?t=32063)
[http://juljas.net/linux/skype/](http://juljas.net/linux/skype/)

Cheers, Slowtrain

---

