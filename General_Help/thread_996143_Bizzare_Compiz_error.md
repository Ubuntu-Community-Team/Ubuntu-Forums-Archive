---
title: "Bizzare Compiz error"
date: 2008-11-28
forum: General Help
---

### Post by doyouhas on 2008-11-28
I have installed everything that has to do with Compiz (compiz-core, settings-manager, etc). I have restricted drivers enabled as well. But when I run "compiz --replace" I get the following.

```
NVIDIA: could not open the device file /dev/nvidiactl (Permission denied).
NVIDIA: Direct rendering failed; attempting indirect rendering.
/usr/bin/compiz: line 775: 13287 Segmentation fault      $*

```

The only difference when I run "sudo compiz --replace" is the first line about not being able to open the device file goes away, the rest is still there. It locks up the machines and I have to restart X every time I try this command.

Any help is appreciated, thanks!

---

### Post by doyouhas on 2008-11-30
I still have not been able to find the solution to this problem anywhere. Any help?

---

### Post by Forlong on 2008-11-30
What version of Ubuntu are you using?
The Compiz wrapper shouldn't have 755 lines on Intrepid. :?

You may want to run this and post the output here: [http://ubuntuforums.org/showthread.php?t=799070](http://ubuntuforums.org/showthread.php?t=799070)

---

