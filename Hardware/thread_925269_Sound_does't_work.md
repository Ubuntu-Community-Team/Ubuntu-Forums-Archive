---
title: "Sound does't work"
date: 2008-09-20
forum: Hardware
---

### Post by chaeussinger on 2008-09-20
I'm currently using an Acer Aspire 6920 and I never got sound to work on any distro of linux. Can someone help me figure out what's going on?

---

### Post by sayakb on 2008-09-20
At a terminal (Applications->Accessories->Terminal), type in:
```
sudo apt-get install linux-backports-modules
``` .. for older releases
[B]or
[/B]```
sudo apt-get install linux-backports-modules-hardy
``` .. for Hardy
And reboot your computer.

---

### Post by chaeussinger on 2008-09-20
That didn't work.

---

### Post by hessiess on 2008-09-20
open up a terminal and run 'alsamixer', is anything muted/ turned down?

---

### Post by chaeussinger on 2008-09-20
> **hessiess said:**
> open up a terminal and run 'alsamixer', is anything muted/ turned down?

Nothing but my headphone port, but I can't adjust that. BTW the sound works just fine in Windows Vista, but none of the linux OSes.

---

### Post by markbuntu on 2008-09-20
You most likely have a HDA chip in that machine. See these posts about that:

[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

[http://ubuntuforums.org/showthread.php?t=820959](http://ubuntuforums.org/showthread.php?t=820959)

For more troubleshooting help you can try my guide here:

 
[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by chaeussinger on 2008-09-21
Yeah, I do have an HDA chip in my machine. I'll look into that. Thanks.


Edit: my chip is not listed there. I couldn't post in that first thread to talk about it, so does anyone know anything about the ALC889 chip?

---

### Post by chaeussinger on 2008-09-22
Bump. Does anyone know what to do with an ALC889 chip?

---

