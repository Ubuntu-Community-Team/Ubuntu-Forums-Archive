---
title: "Sounds issues, like many"
date: 2009-01-07
forum: Hardware
---

### Post by Zenegade on 2009-01-07
Googled and googled for a large amount of time trying to find answers, trying different things etc. I only just moved onto Linux Ubuntu 2 days ago (My first ever Linux) and well, the sound is not right. It actually dissapeared in flash videos but is back now, although it is kinda quite even at Max volume.

Infact, on the sound level at the top bar, I can only have it Mute, or Max volume, if I try to set it to anything in between, it snaps to the nearest.

Really hope I can get some help with this, it is alrite the sound now, but it's one of those little annoying things.

---

### Post by namdung on 2009-01-07
Welcome to the Ubuntu world. I see this is ur 1st post and we'll definitely try to resolve ur issue but more info/details provided would help.

Which Ubuntu version?
Which Flash version? Latest Adobe Flash player is 10.

This seems to be ur 1st post here and we'll definitely try to resolve ur issue.

In terminal
```

less /proc/asound/card0/pcm0p/info
```

Check *subdevices_avail*, it if's zero it means that ur sound card is captured by some other device. Stop any other devices and try again.

Try this for multiple sound solution:
[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by Zenegade on 2009-01-09
Ubuntu 8.10 Intrepid. Yeah latest flash installed. I looked at the tutorial on the link you gave. After many toggling and changes to things I managed to get it working, thankfully.

Although I was told to disable the ICe6, I enabled and it worked for me.

---

