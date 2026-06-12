---
title: "Sound is extremely buggy. (FIrefox)"
date: 2008-08-29
forum: General Help
---

### Post by ZeroFive1 on 2008-08-29
What happens is, whenever I use sound on firefox (flash), and then afterwards I use something like amarok, _all_ other sound is muted. This happens on wine too (I uninstalled). It's extremely frustrating, and I can never find out what the freaking problem is. It's very annoying.

I have tried changing alsa to oss to pulseaudio, used aoss, and all this stuff.

---

### Post by ddixonr on 2008-08-30
Same problem here. I use this command.
```

sudo /etc/init.d/alsa-utils restart

```

I put this into a bash file, set it to execute with chmod +x, and place an icon in the panel to run it when it happens. Now that firefox saves all the open tabs, I just close it down before running the script. Then I can get sound out of everything else. Pop open firefox and continue. Not the answer/fix you might have been looking for, but it works for me since I have not found anything else.

---

### Post by ZeroFive1 on 2008-08-30
It already works when I close it, but thanks for helping me.

---

### Post by ZeroFive1 on 2008-09-02
OK. I solved it.
I needed to change lots of stuff from pulseaudio to alsa.

---

