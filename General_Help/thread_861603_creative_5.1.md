---
title: "creative 5.1"
date: 2008-07-16
forum: General Help
---

### Post by Diego Orozco on 2008-07-16
hi ! i have installed Ubuntu 8.0.4 in my pc and all  works good! 
but i have a problem whit the driver of my sound card, my sound card is a creative 5.1 , in one forum i read that i have to installed alsa mixer, so i installed that but whit no effect. the problem is that the center speaker and back speakers don't sound, they only work the woofer and the front speakers!! if someone can help me!!

---

### Post by alfalfa31 on 2008-07-16
Unless there is some new way to do it, just edit .asoundrc to reflect the following.

```

pcm.!default {
type plug
slave.pcm “surround51&#8243;
slave.channels 6
route_policy duplicate
}

```

---

### Post by jerome1232 on 2008-07-16
I would recomend this thread, seems pulseaudio defaults to 2 channels, it got me up and running with 5.1, [http://ubuntuforums.org/showthread.php?t=795525&highlight=pulseaudio+surround+sound](http://ubuntuforums.org/showthread.php?t=795525&highlight=pulseaudio+surround+sound)

---

