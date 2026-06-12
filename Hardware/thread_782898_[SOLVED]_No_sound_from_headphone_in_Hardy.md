---
title: "[SOLVED] No sound from headphone in Hardy?"
date: 2008-05-05
forum: Hardware
---

### Post by worc on 2008-05-05
Hey everyone!

I have a Toshiba Satellite P105 S9337 and have just fresh installed Xubuntu 8.04 on it.
I was really excited to realize that 8.04 improved so much compared to 7.10! Back under Ubuntu 7.10, I have to compile my own kernel to fix problems caused by bad DSDT info, such as GPU is too hot, no sound, can not be suspended, etc. But under Xubuntu 8.04, boom, everything just works out of box! GPU stays cool with nvidia-glx-new, sound is OK, suspend works great...

Till now, everything is just OK except one thing, no sound after I plug in my headphone. 
I also have a Vista installed on the laptop. Under Vista, when I plug in my headphone, the internal speaker is muted and sounds get emitted from the headphone, which is as anyone would expect. But under Xubuntu 8.04, when I plug in the same headphone, the internal speaker get muted as expected, but there is no sound coming out from the headphone neither. The same laptop, the same headphone, used to be OK under both 7.04 (with custom DSDT file) and 7.10 (with custom compile kernel). Isn't it strange?
PS. I've tried different headphones and I don't think it is the headphone's problem.

After times of trying, I found there IS *some* sound coming out from the headphone. When I plug in the headphone, I have to carefully pull it out a little bit, and if I'm lucky enough (it is really sensitive), I can hear *some* sound from the headphone. I emphasize the word "some" is just because the sound I hear is not all the channels the source contains. When I was watching a movie, I can hear the background sound (like musics) but no conversations. If I unplug the headphone, sound is perfect with the internal speaker. It feels like the headphone shoe is waiting for some multi-channel (more than 2) headphone. 

I'm not sure if I describe everything clear. I don't know what I can do to fix the problem.

Any idea?

---

### Post by worc on 2008-05-05
By the way, could it be possible that the problem is actually caused by xfce? 
I guess not. I've tried Ctrl+Alt+F1 to switch to tty1 and use aplay to play some music, the problem stays exactly the same. Does this mean the Desktop Environment has nothing to do with the problem?  

I've also checked alsamixer and I'm sure every channel is switched on and lifted to the highest level.

---

### Post by Zorael on 2008-05-05
Do you have an Intel HDA card?

I had similar issues my ALC883-based one, where I had to manually toggle Headphones in alsamixer to get it to switch, coupled with there being no sound from the left speaker, etc. Solution was to add a line to /etc/modprobe.d/alsa-base.

See [http://ubuntuforums.org/showthread.php?p=4869649#post4869649](http://ubuntuforums.org/showthread.php?p=4869649#post4869649) as well as the post I linked to there.

---

### Post by worc on 2008-05-05
> **Zorael said:**
> Do you have an Intel HDA card?

I had similar issues my ALC883-based one, where I had to manually toggle Headphones in alsamixer to get it to switch, coupled with there being no sound from the left speaker, etc. Solution was to add a line to /etc/modprobe.d/alsa-base.

See [http://ubuntuforums.org/showthread.php?p=4869649#post4869649](http://ubuntuforums.org/showthread.php?p=4869649#post4869649) as well as the post I linked to there.

Hi Zorael, thanks for the hint.
Yes I have a Intel HDA card:
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Following your post and the link you gave, I've tried model with "CONEXANT","Conexant", "laptop", "laptop-hp" and "laptop-eapd". Actually none of them makes any difference.

Any idea?

I just wonder why this is not a problem back in 7.04 and 7.10?

---

### Post by worc on 2008-05-06
Hello, isn't this some kind of common problem?

---

### Post by worc on 2008-05-06
Tried to compile alsa driver/lib/utils to version 1.0.16, nothing changed. The problem remains the same.
:(

---

### Post by Zorael on 2008-05-07
If the model thing doesn't work, I'm out of ideas. I'm not a developer myself, see.

*Do* enable backports repositories and install both the experimental 2.6.24-17 kernel as well as any backported modules to see if things improved.

Else, you could troll launchpad a bit and see if there are any bugs posted which'd cover your issue, else post one yourself. That failing, I guess reverting to 7.10 would be the only option. :<

---

### Post by worc on 2008-05-08
Already tried kernel 2.6.24-17 from backport, problem remains the same.
Thank you Zorael anyway!

There is one thing I'm still interested, could this be a xfce's problem? How can I proof that?
Earphone worked just great when I was using Ubuntu 7.04/7.10. But that was in gnome, but now I'm in xfce.

---

### Post by DocBob on 2008-05-08
Had issues with sound in Hardy, found out it was alsa issues.

Maybe check your card there: [http://www.alsa-project.org/main/index.php/Matrix:Main](http://www.alsa-project.org/main/index.php/Matrix:Main)

---

### Post by yavez on 2008-05-08
Just like to add that Alsamixer also worked for me.  Installed and fiddled with the settings in there, everything working fine now.  Card is a Realtek ALC883 (as identified by Alsamixer).

---

### Post by worc on 2008-05-08
Finally I downloaded and installed latest OSS from [http://www.opensound.com/download.cgi](http://www.opensound.com/download.cgi), the problem goes away with OSS.

---

### Post by yodermk on 2008-05-17
I'm having the same problem, ALC882 chip on an ASUS Z84JP.

I've tried setting
options snd-hda-intel model=z71v position_fix=1
as I saw somewhere else, doesn't fix it.  I'm going to try model=mbp3 next time I reboot, but who knows when that will be.

I use Kubuntu, and it worked in Feisty.  Not sure I tried in Gutsy.  Regressions like this are pretty disappointing. :(

---

### Post by worc on 2008-05-26
appending "options snd-hda-intel model=laptop-micsense" to /etc/modprobe.d/alsa-base fixes the problem!
Followed this link [https://bugs.launchpad.net/ubuntu/+bug/218817](https://bugs.launchpad.net/ubuntu/+bug/218817)

---

