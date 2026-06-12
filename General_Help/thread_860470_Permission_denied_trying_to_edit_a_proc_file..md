---
title: "Permission denied trying to edit a /proc/ file."
date: 2008-07-15
forum: General Help
---

### Post by PixelSmack on 2008-07-15
Hi, i am trying to edit /proc/sys/dev/rtc/max-user-freq on ubuntu studio with sudo echo and i am getting a permission denied message. I am aware that i can't use vi to edit this file. What am i doing wrong? i am sure its something really simple that is eluding me.

Thanks.

---

### Post by sdennie on 2008-07-15
Try using a syntax like this:

```

sudo sh -c "echo some_value > /proc/sys/dev/rtc/max-user-freq"

```

---

### Post by PixelSmack on 2008-07-15
> **vor said:**
> Try using a syntax like this:

```

sudo sh -c "echo some_value > /proc/sys/dev/rtc/max-user-freq"

```

That worked a treat, thanks! I have had that problem alot before but always been able to solve it with vim.

---

### Post by CatKiller on 2008-07-15
As an alternative, you can also use ```
sudo su
echo some_value > /proc/sys/dev/rtc/max-user-freq
``` I remember I used to have to do this to get sound to work in RtCW.

Don't forget to mark the thread as solved.

---

