---
title: "Gnome Alsa mixer starts with speaker set to bottom (zero sound)"
date: 2011-02-02
forum: Hardware
---

### Post by welshmike on 2011-02-02
When Ubuntu 10.04 starts on my ASUS Eee PC 1001P there is no sound output from its speakers. I see that Gnome Alsa mixer shows speaker volume set to bottom (zero sound). I can adjust this latedr of course.
How may I get Ubuntu to start the speaker with some volume please?

---

### Post by pl@yer on 2011-02-02
```

sudo alsactl store

```

---

### Post by welshmike on 2011-02-02
Thanks for the prompt reply.
I set the Gnome Alsa mixer speaker slider to max, ran sudo alsactl store and rebooted. No change I'm sorry to report. Maybe it is a "feature" of Ubuntu on my ASUS Eee PC 1001P.

---

### Post by pl@yer on 2011-02-03
Try running this as root
```

# alsactl init

```
Then run alsamixer and set your volume level, test that it is working. Then run.
```

# alsactl store

```
After reboot if sound level is not right try running.
```

# alsactl restore

```
If you had to run alsactl restore to make it work then I would add it to run at startup.

---

### Post by welshmike on 2011-02-03
Many thanks
alsactl restore
fixed it.

---

### Post by limon80 on 2011-09-04
Thanks for this!! Worked for me on Archlinux also!!

---

### Post by Yosarajo on 2011-12-11
Thank you, it helped me; I fixed my problem on ubuntu 10.10.

---

