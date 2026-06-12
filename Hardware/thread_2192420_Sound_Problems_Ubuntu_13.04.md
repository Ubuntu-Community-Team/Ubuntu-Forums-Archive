---
title: "Sound Problems Ubuntu 13.04"
date: 2013-12-07
forum: Hardware
---

### Post by tock on 2013-12-07
I have a sony laptop. At first I was just having problems with the headphones. then I tried following procedures to repair the sound and things have gotten worse.

I followed the procedure to remove and re-install the alsa and pulse audio programs. This killed my sound completely. Now It only show "Dummy Output" in the asla settings. I can do a force reload and it will show the sound card until I reboot then its gone again.  Even when I force a reload I still have no sound.

```
card 0: Intel [HDA Intel], device 0: ALC262 Analog [ALC262 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
```

---

### Post by tock on 2013-12-07
This worked for me....  Why I should have to do this is crazy to me.....  wasted hours searching for this answer......


Following the instructions at [http://ubuntuforums.org/showthread.php?t=2143157&p=12650610#post12650610](http://ubuntuforums.org/showthread.php?t=2143157&p=12650610#post12650610) , I disabled speech-dispatcher as follows:

sudo vi /etc/default/speech-dispatcher
And I changed RUN=yes to RUN=no, then rebooted.

---

