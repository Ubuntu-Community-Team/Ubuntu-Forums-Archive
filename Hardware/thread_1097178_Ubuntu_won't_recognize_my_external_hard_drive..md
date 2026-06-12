---
title: "Ubuntu won't recognize my external hard drive."
date: 2009-03-15
forum: Hardware
---

### Post by Yvan300 on 2009-03-15
Hello, i have a 36gb netdisk ndas external hard drive with a lot of my backed up games etc on it. It is recognized by windows fine but when i plug it in with ubuntu, the activity led is constantly busy, and that's it. No mount or anything. Oh yeah i am a noob, so while searching for an answer i came across a command to search for the drive and the results was a list stating no sense or something. Hope that helped.

---

### Post by taurus on 2009-03-15
Why not post which command did you run and what was the output?

Probably something like

```
sudo fdisk -l
```

---

### Post by kevinbeard on 2009-05-13
NDAS devices are not currently supported on 9.04 I'm afraid.

They work fine with 8.10  but until someone fixes the driver they remain broken :-(

See:

[http://ubuntuforums.org/showthread.php?t=1146707&highlight=ndas&page=2](http://ubuntuforums.org/showthread.php?t=1146707&highlight=ndas&page=2)

and

[http://ubuntuforums.org/showthread.php?t=979370&highlight=ndas&page=3](http://ubuntuforums.org/showthread.php?t=979370&highlight=ndas&page=3)

---

