---
title: "custom kernel nvidia troubles"
date: 2008-08-26
forum: General Help
---

### Post by namelessone on 2008-08-26
So I just custom compiled a kernel, and now my nvidia driver doesn't work.

I uninstalled nvidia-glx-new and installed the nvidia drivers with the .run file from the nvidia website.

That all worked, but for some reason, my video display was set down to 640x480. I tried editing some xorg settings, but when I booted again, I got a white screen that slowly faded to black...

So I gave up and tried to go back. I reinstalled nvidia-glx-new and booted into my old kernel, but even though I ran the nvidia-xconfig script, ubuntu loaded into limited graphics mode.


Now what do I do? I just want my screen to display properly!

---

### Post by overdrank on 2008-08-26
> **namelessone said:**
> So I just custom compiled a kernel, and now my nvidia driver doesn't work.

I uninstalled nvidia-glx-new and installed the nvidia drivers with the .run file from the nvidia website.

That all worked, but for some reason, my video display was set down to 640x480. I tried editing some xorg settings, but when I booted again, I got a white screen that slowly faded to black...

So I gave up and tried to go back. I reinstalled nvidia-glx-new and booted into my old kernel, but even though I ran the nvidia-xconfig script, ubuntu loaded into limited graphics mode.


Now what do I do? I just want my screen to display properly!

Hi and you can try what PmDematagoda suggest here
[http://ubuntuforums.org/showthread.php?t=795997](http://ubuntuforums.org/showthread.php?t=795997)

```
Do this:-
1) Open a modules file for editing with:-
Code:

sudo nano /etc/default/linux-restricted-modules-common

2) Edit the DISABLED_MODULES line to make it look like this:-
Code:

DISABLED_MODULES="nv nvidia_new"

and save the file.

Then reboot the PC and see if the Nvidia driver now works.
```

---

### Post by namelessone on 2008-08-26
Well, that didn't work, but I think I figured it out.

I found the backup to my xorg file and was able to restore my old settings using that. Now it all works (with my custom kernel too!)

---

