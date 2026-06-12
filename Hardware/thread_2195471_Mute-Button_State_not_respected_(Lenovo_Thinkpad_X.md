---
title: "Mute-Button State not respected (Lenovo Thinkpad X1)"
date: 2013-12-24
forum: Hardware
---

### Post by manuel.imobersteg on 2013-12-24
Hi Ubuntu community!

I am using Xubuntu on a Lenovo Thinkpad X1 1924-2NG and are perfectly happy with it.
I remain with one issue I could not resolve and therefore hope for your support :)

The X1 has a mute button that remembers its state. If I hit the mute button, it works fine (the system mutes, the button glows, no sound is played) and so does unmute (the volume control activates, the button stops glowing and the sound plays).
The problem occurs when I reboot the Laptop while muted: The mute button glows, no sound is played, but the system is not muted (volume control is active). When I hit the mute button now, the button does not glow anymore, but the system mutes now and therefore no sound is played.

I can work around this, if I unmute the system in the volume control. After that, the mute butten works as expected again. That's ok, but not perfectly satisfactory. Is there a way I can make the System check for the state of the mute button at startup, so they are always synced?

Thank you and Cheers
Manu

System info:
```
manu@epicur:~$ uname --all
Linux epicur 3.11.0-14-generic #21-Ubuntu SMP Tue Nov 12 17:04:55 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

```

---

### Post by manuel.imobersteg on 2013-12-25
Any ideas? Or is there a way to have xubuntu completely ignore the button?

---

### Post by manuel.imobersteg on 2013-12-31
I still haven't found a solution... anyone out there who uses xubuntu on a X1?

---

### Post by waterhead on 2013-12-31
Using the last reply in this link:
[http://askubuntu.com/questions/109937/ubuntu-starting-with-mute-sound](http://askubuntu.com/questions/109937/ubuntu-starting-with-mute-sound)

Mute it, then check to see if it is muted using the alsamixer command.

```
alsamixer
```

Usually it is the Master that would be muted, if so it will have "MM" at the bottom of the level indicator. You can mute/unmute and do volume up/down and alsamixer will show the changes. Press the Esc key to exit alsamixer.

When you are sure which setting is the correct one (Master), try to change the level with a command:

```
amixer set Master 50%
```

It will also give a range in the 'Limits: Playback' section. You can use a number instead of a percent.

```
amixer set Master 30
```

Once you know what setting you want, save it:

```
sudo alsactl store
```

And as a backup in case alsactl doesn't work, save the setting in your user profile:

```
echo 'amixer set Master 50%' >> ~/.profile
```

I hope that works for you.

---

### Post by waterhead on 2013-12-31
I always try out my own advice,and the 'alsactl store' method doesn't seem to work. I think that you are suppose to tell it what sound card, but the correct syntax I do not know.

But, saving the sound settings in your .profile file does work.

---

