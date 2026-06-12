---
title: "HD on same IDE controller as DVD?"
date: 2005-11-26
forum: Hardware &amp; Laptops
---

### Post by quietglow on 2005-11-26
Quick question!

I'm getting ready to put in a 200g HD in my desktop and I'm out of room on my IDE controller that has drives on it (not another connector). I'm considering pulling one of my 2 optical drives and replacing it with the new drive.

Is there any problem with mixing optical and HD on the same controller?

Thanks!

---

### Post by metoo on 2005-11-26
No, should be save.

Just check later if DMA is enabled by default => hdparm /dev/hdx

---

### Post by dcstar on 2005-11-27
[QUOTE=quietglow]Quick question!

I'm getting ready to put in a 200g HD in my desktop and I'm out of room on my IDE controller that has drives on it (not another connector). I'm considering pulling one of my 2 optical drives and replacing it with the new drive.

Is there any problem with mixing optical and HD on the same controller?

Thanks![/QUOTE]
In the past there may have been, but these days apparently not:

[http://www.pcguide.com/ref/hdd/if/ide/confTiming-c.html](http://www.pcguide.com/ref/hdd/if/ide/confTiming-c.html)

---

