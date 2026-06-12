---
title: "No sound on 8.10, everything APPEARS fine..."
date: 2009-02-21
forum: Hardware
---

### Post by spookyu on 2009-02-21
I'm stumped....a friend wanted to try ubuntu on her laptop so I've got most of it working, the sound is giving me troubles though. It's an Emachines w4605 (apparently a wal-mart special some time ago?). I've tried numerous tutorials and whatnot, and it doesn't seem like anything is wrong, I've yet to find any little red flag (like ubuntu not finding the audio device, f'ed up drivers, whatever). I'm just stumped, could anyone give me a hand? Just let me know what specific information you'd like, wasn't sure what'd sum it all up best.

---

### Post by Rathillet on 2009-02-21
Carl... you're awesome.

---

### Post by kostkon on 2009-02-21
For a start you could check if
```
aplay -l
```
lists any audio devices. If yes, that's good.

---

### Post by Rathillet on 2009-02-21
aplay -l lists the following:

> **** List of PLAYBACK Hardware Devices ****
card 0: IXP [ATI IXP], device 0: ATI IXP AC97 [ATI IXP AC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Modem [ATI IXP Modem], device 0: ATI IXP MC97 [ATI IXP MC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


---

### Post by kostkon on 2009-02-21
OK.

Do you see a speaker in your system tray. If yes, try to right-click on it and select *Open Volume Control*. From there, try to increase any volume levels that you'll find. To add more volumes, go to *Edit &#8594; Preferences*.

Or better, open a terminal and give
```
alsamixer -Dhw
```
and increase any volume levels.

---

### Post by spookyu on 2009-02-21
Yeah that's good, we've done most the simple things (like check the volume XD). We tried the whole ubuntu sound guide here on the forums as well.

---

### Post by markbuntu on 2009-02-21
Look in here, at the bottom of the **Drivers** section is some info that may help with the AC'97. I have just rewritten almost the entire guide.

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

