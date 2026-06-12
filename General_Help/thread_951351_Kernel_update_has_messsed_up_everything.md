---
title: "Kernel update has messsed up everything"
date: 2008-10-18
forum: General Help
---

### Post by nimonika on 2008-10-18
After I updated to the new kernel on Friday, my laptop has almost stopped functioning and now even when I put the laptop in suspend mode and then try to get back, it does not work. I have to hard boot every time I suspend. Please can someone help. I have already lost my nvidia configurations,which I have not been able to get back even after loads of trying and reinstalling the driver as well :(. 

Thanks

---

### Post by sparky-steve on 2008-10-18
Hi

Have you tried using the previous kernel - you'll get a brief menu during bootup - it will default to the newest kernel, but the previous one should be there too.

If you'd rather stick with the previous kernel for now, you can change the default in menu.lst

```
sudo nano /boot/grub/menu.lst
```

and change

```
default 0
```
to
```
default x
```

where x is the position of the kernel you wish to run, 0 being the top most kernel. The kernels are listed at the end of menu.lst


As for your nvidia troubles, have you worked through this thread:

[http://ubuntuforums.org/showthread.php?t=949407&highlight=nvidia+sparky-steve](http://ubuntuforums.org/showthread.php?t=949407&highlight=nvidia+sparky-steve)

Seems to have worked for quite a few people.

SS

---

### Post by steveneddy on 2008-10-18
I've answered this a few times.

[Look here]("http://ubuntuforums.org/showpost.php?p=5986899&postcount=4").

> The new kernel is giving fits to some folks.

Try waiting for GRUB while booting, hit the [COLOR=Blue]**ESC**[/COLOR] key and select the kernel ending with [COLOR=Blue]**-19**[/COLOR]

Hope that helps.

---

### Post by nimonika on 2008-10-18
> **sparky-steve said:**
> Hi

Have you tried using the previous kernel - you'll get a brief menu during bootup - it will default to the newest kernel, but the previous one should be there too.

If you'd rather stick with the previous kernel for now, you can change the default in menu.lst

```
sudo nano /boot/grub/menu.lst
```

and change

```
default 0
```
to
```
default x
```

where x is the position of the kernel you wish to run, 0 being the top most kernel. The kernels are listed at the end of menu.lst


As for your nvidia troubles, have you worked through this thread:

[http://ubuntuforums.org/showthread.php?t=949407&highlight=nvidia+sparky-steve](http://ubuntuforums.org/showthread.php?t=949407&highlight=nvidia+sparky-steve)

Seems to have worked for quite a few people.

SS

I tried everything in that thread, but nothing seemed to work. Ultimately I had to go to the restricted drivers area and enable nvidia from there.

---

