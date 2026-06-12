---
title: "/etc/modules question"
date: 2009-05-29
forum: Hardware
---

### Post by zenkaon on 2009-05-29
Hello all,

I have a very old TV card that the bttv autodetect doesn't get correct. This means than I have to manually do:
```

sudo rmmod bttv
sudo modprobe bttv card=3

```

And then everything works fine. Clearly I want to set this up so it's done at boot time and I don't have to faff about.

In my /etc/modules I have the line

```

options bttv card=3

```

But it doesn't seem to do the trick. dmesg | grep bttv shows that bttv has tried to autodetect and failed and there is no trace of the card=3 option.

Any pointers?

---

### Post by kerry_s on 2009-05-29
/etc/modprobe.conf is the place to put that.

---

