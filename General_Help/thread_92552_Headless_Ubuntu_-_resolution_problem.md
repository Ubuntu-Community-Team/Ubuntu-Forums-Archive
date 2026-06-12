---
title: "Headless Ubuntu - resolution problem"
date: 2005-11-19
forum: General Help
---

### Post by The Belgain on 2005-11-19
I'm wanting to run a headless Ubuntu machine, which I've set up initially with a monitor, keyboard, mouse plugged in.  Everything worked fine, and I had it running at 1280x1024 res over the network to a Windows machine.

Now that I've rebooted the Ubuntu machine without a monitor connected though, the VNC session has defaulted to 640x480.  Presumably this is because Ubuntu hasn't detected a monitor on bootup, and has therefore booted with failsafe settings.  And since the remote desktop session is just giving me whatever X has been started with, I'm getting 640x480.

Obvisously 640x480 is pretty useless for desktop use... how can I get Ubuntu to use 1280x1024 res anyway?

Thanks

---

### Post by Efwis on 2005-11-19
Read this thread. 

when you do the configuration, or if you edit Xorg.cong, only allow the resolution you want to run in the reconfigure program, that way it will only use that res.

[http://www.ubuntuforums.org/showthread.php?t=83973&highlight=reconfiguring+Xorg](http://www.ubuntuforums.org/showthread.php?t=83973&highlight=reconfiguring+Xorg)

---

### Post by Franko30 on 2006-01-29
Hi,

First: Sorry for the crosspost, but resolving this was just too frustrating for me and I want people to find this in all the other unresolved "help VNC resolution" threads, too.

I didn't want to go for the modelines as described in

[http://www.ubuntuforums.org/showthread.php?p=690202](http://www.ubuntuforums.org/showthread.php?p=690202)

and all the other "edit the xorg.conf" threads didn't work for me - but I found a solution that works for me:

In the **device** section of the **xorg.conf** I changed the driver to

```
Driver		"vesa"
```

and finally my headless Ubuntu setup starts up in the required resolution of 1024x768 I entered in the xorg.conf file - which makes using this machine with VNC a bit nicer than with 640x480. :-)

And we don't need a fancy 3D driver on a machine accessed via VNC - do we?

It worked on two machines (running climateprediction.net with BOINC) with different graphics adapters.

I hope it might work for others, too...

Franko30

---

