---
title: "Run a patch"
date: 2008-08-10
forum: General Help
---

### Post by realizee on 2008-08-10
HI, 

I'd like to know how I run a patch.
I'm trying to run this patch for my s810 emtec but I can't find out how. 
Does someone know? 

Thanks


[http://lists-archives.org/video4linux/21813-support-for-dvb-t-usb-device-emtec-s810.html](http://lists-archives.org/video4linux/21813-support-for-dvb-t-usb-device-emtec-s810.html)

---

### Post by Achetar on 2008-08-10
You need to copy the patches to two text files and then go to the /usr/src directory and run:
```

sudo patch patch1
sudo patch patch2

```

If it says source not found or something similar look around and find the files the patch is supposed to work on. Then move the patches to that directory and run the commands again

---

