---
title: "Sound problems ubuntu 9.10"
date: 2010-06-17
forum: Hardware
---

### Post by GazRockK on 2010-06-17
Running Ubuntu 9.10

I had recently purchased a "better" computer and decided to add my older internal hdd w/ubuntu already on it. 
Seemingly all settings adapted upon first boot (unlike the winxp that was also on the old hdd.. shame..), but i'm not getting any sound. 
At first it noticed something in the hardware tab (still no sound however) but i've just found that theres no hardware whatsoever relating to sound. 
hardware tab in "sound properties" lists nothing

No sound when putting things at full blast either

When I go to sound pref.'s the only listed output is 
"Dummy Output" (Stereo)

I played some music in chrome, then in vlc, only not showing up in chrome on the applications tab in sound properties [was playing video on youtube]

Did this in terminal:
```
lspci | grep -i 'audio\|snd'
```
got
```
02:08.0 Multimedia [COLOR="Red"]audio[/COLOR] controller: Creative Labs SB Live! EMU10k1 (rev 0a)

```

thanks .

---

### Post by lidex on 2010-06-17
First have a run through this howto:
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats]("https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats")

I would also recommend these steps.
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* 
sudo rm /etc/asound.conf
```
Logout/in.

```
sudo apt-get update
sudo apt-get upgrade
```
```
sudo apt-get install --reinstall alsa-utils alsa-oss alsa-base libasound2 libasound2-plugins linux-sound-base gstreamer0.10-alsa
```
**Reboot.**

You may be better off re-installing ubuntu with so many hardware changes.

---

