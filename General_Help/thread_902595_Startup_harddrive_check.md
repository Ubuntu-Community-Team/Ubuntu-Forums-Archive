---
title: "Startup harddrive check"
date: 2008-08-27
forum: General Help
---

### Post by knutz on 2008-08-27
Hi everybody :)

I was wondering, if it is possible to disable the harddrive check, ubuntu automatically does every 30th time i boot my computer?



Thanks!

---

### Post by de0xyrib0se on 2008-08-27
You can quit the check with ESC.

You can adjust the number of mounts the kernel will automagically force fsck-ing when it is exceeded with the command below:

sudo tune2fs -c <max-mount-counts> device

If max-mount-counts is 0 or -1, forced-fsck is disabled, device is your partition in /dev, usually /dev/sdXY.

You can also specify device through its label, which is located under /dev/disk/by-label/.

---

