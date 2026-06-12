---
title: "Sound with Live, no sound after install"
date: 2010-02-17
forum: Hardware
---

### Post by Nitewolf121 on 2010-02-17
I ran ubuntu from disk to check and see how things worked first.  Everything worked good, including sound.

After install everything else is still running well, but i have no sound anymore.  I'm running an HP Touchsmart Tx2.  Alsamixer shows an HDA ATI SB card with Realtek ALC268 chip if that helps any.

After install I rebooted once and the sound worked fine, sound card showed up in sound preferences > hardware, but then after shutting down and restarting later no sound, and none ever since. I've ran all updates through update manager and synaptic, still nothing.  

Any help would be appreciated, running 9.10.  Been trying Ubuntu off and on for last few years, always had something giving problems, this time I really want to give it a solid try, and so far this is the only problem.  I've got everything else working fine finally.

---

### Post by zagor on 2010-02-18
Same issue here, I think we might have similar problems, so I add my problme to yours: I've started the live CD (karmic 64bit) and both my cards where there and sound ok.
After install, no cards are seen, only the "RTP sink" is shown as output in the preferences box (right key on the sound icon).

After update with the 200+ security updates and reboot, the speakes let out only a continuous whistle.
Reboot, disable the onboard audio from the BIOS, and still the whistle. But now, VLC can play sounds (bad quality, though) if I set it to alsa. Rythmbox also kind of "works". No success with Movie Player: absolutely mute.
I've also ntoed that the main volume is not doing anything, while I can change the volume by acting on the slider in VLC or Rythmbox.

Why should the sound work in the live and not after install? doesn't make sense!

My card is a Hercules Game Theater XP Pro.
The fresh install of 9.10 amd64 has been done keepoing the previous existing home partition (form a 8.04 amd64).

---

### Post by zagor on 2010-02-18
Nitewolf,

I quite solved by reinstalling alsa as suggested [here]("http://ubuntuforums.org/showpost.php?p=8541933&postcount=68")

First backup pulse (just in case....):
```
mkdir ~/pulse-backup && cp -r ~/.pulse ~/.asound* /etc/asound.conf /etc/pulse -t ~/pulse-backup/

```

Then, follow the steps as in that url:

1. remove alsa:
```
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils

```
2. shutdown and restart (sometimes better than rebooting...)

3. reinstall alsa:
```
sudo apt-get install linux-sound-base alsa-base alsa-utils
sudo apt-get install gdm ubuntu-desktop
```

4. shutdown and restart

5. configure (if needed):
> goto System > Preferences > Sound
goto Hardware tab and goto Profile:
Select "Analog Stereo Duplex"

Hope it helps you as well

---

### Post by Nitewolf121 on 2010-02-18
Appreciate it, but that didn't work either.

Tried adding the model=toshiba trick too, still no sound.  Even tried acer and one other that I found would work for the chip I have.  

Maybe I should try to go with 32bit instead of 64.  Not sure if that would really make a difference or not.

Any other suggestions?

---

### Post by zagor on 2010-02-19
I have found several possible reasons (and solutions) listed in the thread I have linked earlier.
I have tried to list those in a kind of "note to myself" to have a testing path to follow.
Find it [here]("http://bfrond.blogspot.com/2010/02/sound-issues-on-karmic-64bit.html").

---

### Post by Nitewolf121 on 2010-02-19
A lot of those I've gone through already, but there are 1 or 2 I can still try.  I will give them a try tonight when I get home and see how it all goes.  Will keep this updated as I go if I find something that works.

---

### Post by Nitewolf121 on 2010-02-22
Nothing on there helped.  But I did finally get it working.  Once I did a reinstall the other night and sound worked for a while, then when I activated the driver for the modem (which I never use anyway) the sound stopped working again.  So I just went back in and deactivated the modem driver and sound came back on and has been working ever since.

---

