---
title: "[SOLVED] Need help understanding all this..."
date: 2007-10-27
forum: Hardware &amp; Laptops
---

### Post by Arthur Archnix on 2007-10-27
I read this article through digg, basically about some problems people were having with Ubuntu and Hard-Drive lifespan. You can read about the original [here]("http://www.linux-hero.com/rant/explanation-ubuntu-hard-drive-wear-and-tear"), and the follow-up [here]("http://www.linux-hero.com/rant/ubuntu-hard-drive-explosions").

I'm just wondering, usually the first thing I do on a fresh install is to uninstall APM and remove it from startup. I do this because it's a newer laptop so probably only needs ACPI to run power saving features.

Am I still affected? What else can I do, other than the tips mentioned in the follow-up artice?

---

### Post by nick_h on 2007-10-27
You can check to see if you are affected by loading smartmon tools,
```
sudo apt-get install smartmontools
```
and then running smartctl as follows:
```
sudo smartctl --device=ata --attributes /dev/sda
```
assuming that your drive is sda.

There is another thread on this subject [here](http://ubuntuforums.org/showthread.php?t=591564).

---

### Post by Arthur Archnix on 2007-10-28
Thanks for that... and the link.

---

