---
title: "Alternative to UDev?"
date: 2009-01-23
forum: Hardware
---

### Post by icanfly0307 on 2009-01-23
Basically, I want to replace udev with something else that's faster. what does udev do anyway? Is it sensible to get rid of permanently? Thanks for your info. :)

PS. bear with me if I'm being completely stupid.

---

### Post by cariboo on 2009-01-23
For an explanation of what udev does, have a look [here]("http://en.wikipedia.org/wiki/Udev").

Jim

---

### Post by icanfly0307 on 2009-01-23
Is there any way to speed it up? Thanks.

---

### Post by kerry_s on 2009-01-23
hmm, in arch there's a little trick that cuts it in half:
[http://wiki.archlinux.org/index.php/Speedup_udev](http://wiki.archlinux.org/index.php/Speedup_udev)

not sure if you can use the same trick in ubuntu, but might be worth looking into.

i use option 3 the symlink was the fastest for me.

```
mv /lib/udev/load-modules.sh /lib/udev/load-modules.sh.original

ln -s /sbin/modprobe /lib/udev/load-modules.sh
```

WARNING: i feel you need to know messing with udev can toast your install, with out it modules won't load so it will look like it locked up.

---

### Post by icanfly0307 on 2009-01-23
Alright. I'll try your trick. So udev really started to work fast after the symlink thing you did? I'm pretty experienced with linux and I don't mind having to reinstall, so no problems there! :)

---

### Post by kerry_s on 2009-01-23
> **icanfly0307 said:**
> Alright. I'll try your trick. So udev really started to work fast after the symlink thing you did? I'm pretty experienced with linux and I don't mind having to reinstall, so no problems there! :)

in mine i went from 6xxxms to 3xxxms, on anther machine it's down in the 2's.

---

