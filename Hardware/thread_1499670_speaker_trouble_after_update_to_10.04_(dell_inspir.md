---
title: "speaker trouble after update to 10.04 (dell inspiron 1545)"
date: 2010-06-02
forum: Hardware
---

### Post by sshea on 2010-06-02
hey i  just updated to lucid and after the update (done through update manager) the inbuilt speakers no longer work. I can plug in earphones and i can listen to whatever through them but I would rather having speakers too.

Also on another note I'm personally finding that after the update my startup speeds have become greater rather then the suggested faster startup speeds. Could anyone suggest why?

Thank you

---

### Post by lidex on 2010-06-02
Cruft, perhaps? Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* 
sudo rm /etc/asound.conf
```
Logout/in.

---

### Post by sshea on 2010-06-05
nope :( didnt do anything..i'm prezuming its the driver but i cant seem to find it...i seem to be able to find drivers for other laptop speakers but not the one i'm looking for as of yet

only info i can give u is the Audio and Speakers which dell says is Intel High  Definition Audio 2.0

---

### Post by lidex on 2010-06-05
Try gnome-alsamixer.
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

---

### Post by sshea on 2010-06-06
Its all good. got them working

[http://ubuntuforums.org/showthread.php?t=557031](http://ubuntuforums.org/showthread.php?t=557031)

Thanks for your help tho :)

---

### Post by David006 on 2010-07-17
Same issue on several (refurbished) desktop PCs, after fresh install of 10.04 (Lucid).

Solution: (temporary only)

  amixer -c 0 | grep Master
    (for card 0, OR change to 1, 2, etc.)
    (look for 'mono' control, for internal speaker)
--
Simple mixer control 'Master',0
Simple mixer control 'Master Mono',0
--

  amixer -c 0 sget 'Master Mono',0
    (label from previous)
--
Simple mixer control 'Master Mono',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [-46.50dB] [off]
--

  amixer -c 0 sset 'Master Mono',0 0dB,0dB unmute
    (NOTE: "0dB" is case sensitive!)
    (enable, neutral gain eg. +-0dB)

  amixer -c 0 sget 'Master Mono',0
    (verify setup)
--
Simple mixer control 'Master Mono',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 31 [100%] [0.00dB] [on]
--

  sudo alsactl store
    (store, non-volatile)


UPDATE: Not resolved, as problem re-created on startup.

---

### Post by David006 on 2011-11-16
Tried:

```
  sudo su -
```

```
  alsactl store
```

No improvement.

---

