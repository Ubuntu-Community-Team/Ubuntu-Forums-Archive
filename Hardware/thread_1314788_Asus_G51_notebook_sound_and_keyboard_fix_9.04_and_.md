---
title: "Asus G51 notebook sound and keyboard fix 9.04 and 9.10"
date: 2009-11-04
forum: Hardware
---

### Post by Chewable on 2009-11-04
I have a** Asus G51 VX** here with the ICH9 (82801I) for audio. Under 9.04 and 9.10, the ALSA drivers work. But I didn't get any sound. However, when I plugged in my headphones halfway, the sound worked but only for one channel. Fully plugged in, there was no sound at all. So in order to get the headphone jack working properly, I made the following edit:

```
gedit /etc/modprobe.d/alsa-base.conf
```then add or edit the last line to:

```
options snd-hda-intel model=asus-mode3
```Save and reboot (or force an ALSA reload) for the change to take effect. 

The source came from **[http://forum.notebookreview.com/showthread.php?p=5097834](http://forum.notebookreview.com/showthread.php?p=5097834) **and I'm sure many Asus notebook owners will be able to get some sort of sound working with this fix, regardless of the model. 

I have yet to try all the possible modes available off that link. Here's his list:
```

ALC662/663
==========
  3stack-dig    3-stack (2-channel) with SPDIF
  3stack-6ch     3-stack (6-channel)
  3stack-6ch-dig 3-stack (6-channel) with SPDIF
  6stack-dig     6-stack with SPDIF
   [lenovo]("http://www.notebookreview.com/shared/scripts/buyDirect.asp?brandID=9")-101e    Lenovo laptop
  eeepc-p701    ASUS Eeepc P701
  eeepc-ep20    ASUS Eeepc EP20
  ecs           ECS/Foxconn mobo
  m51va         ASUS M51VA
  g71v          ASUS G71V
  h13           ASUS H13
  g50v          ASUS G50V
  asus-mode1    ASUS
  asus-mode2    ASUS
  asus-mode3    ASUS
  asus-mode4    ASUS
  asus-mode5    ASUS
  asus-mode6    ASUS  auto          auto-config reading BIOS (default)
```I'm not certain "asus-mode3" is the best choice for the G51. I will cycle through them all this weekend to see which works with a) the headphone jack, b) the speakers, c) the microphone jack, and d) the line-in jack. The other item not listed is the headphone jack switch that enables/disables the speakers when the headphones are plugged/unplugged.

As a side note, the backslash/bar key doesn't work upon install. It returns the less/greater instead. To fix this, I found one at **[http://crunchbanglinux.org/forums/topic/5033/resolved-switch-asus-keyboard-layout/](http://crunchbanglinux.org/forums/topic/5033/resolved-switch-asus-keyboard-layout/)** where he suggests this:

```
xmodmap -e "keycode 94 = backslash bar"
```Hope ths helps!

---

### Post by pgrim91 on 2012-02-16
Hi, I'm running 11.10 now and having the same issues on a G51VX-A1 with the audio except my internal microphone doesn't work either.  Can you tell me how to check if I have the same audio as you (you stated you had the ICH9 (82801I))?  Also, you sad you were going to check if the asus-mode3 was the best configuration for the G51, would you recommend another setting?

---

