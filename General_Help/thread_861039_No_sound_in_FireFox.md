---
title: "No sound in FireFox"
date: 2008-07-16
forum: General Help
---

### Post by crazymanjared on 2008-07-16
Yes I know this has been posted a thousand times, I've read them all.  I just installed Ubuntu x64 8.04 and everything went well, until i tried playing a video on youtube, there's no sound, there's also no sound with quicktime within firefox. I have nothing else running that would take sound away from firefox and I have absolutely no idea whats going on.

---

### Post by crazymanjared on 2008-07-17
bump

---

### Post by iaculallad on 2008-07-17
Try installing the audio support wrapper for non-free plugin:

```
sudo apt-get install libflashsupport
```

---

### Post by Ranidan on 2008-07-19
> **iaculallad said:**
> Try installing the audio support wrapper for non-free plugin:

```
sudo apt-get install libflashsupport
```

This worked perfectly,thank you.

---

### Post by crazymanjared on 2008-07-19
> **Ranidan said:**
> This worked perfectly,thank you.

Already have that installed.

---

