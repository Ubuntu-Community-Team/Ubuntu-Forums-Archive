---
title: "mount old home partion"
date: 2009-01-11
forum: Installation &amp; Upgrades
---

### Post by egamal on 2009-01-11
Salam everybody,

I had 8.4 then I updated to the great 8.10 ubuntu then sound had few problems but I didn't mind it was only happening when I hibernate .. 
Now I was installing some software and I-not on intention- copies some libs to my libs dir which sounds to effect my GDM and now my laptop isn't booting to graphical user interface ..
I searched from another PC and I found:
```

$sudo apt-get install ubuntu-desktop

```

and I did issues the command after removing the package ..
then I tried to log in a gain and a problem in file called .XAuth .. is somehow locked or something ..

Now I've all my urgent data on a separate partition which was "/home" in old system.

My Question is can I install a new 8.10 ubuntu then mount my old partition home to it to work just like before ?
Or I'm dreaming ..!

In case there is away .. how can I ?

Thanks

---

### Post by pizmooz on 2009-01-11
I would boot to a live CD, like the 8.10 install disc, and backup /home to another HD or external media.  Install Ubuntu fresh and copy back the data that you need from the external media.

If your /home is actually it's own partition, you can probably just set it as the mount point for /home during the install.  However I don't recall if you can do this in 8.10 install, but it is pretty standard that you can for most any linux distro install.

But before you reinstall, I would make sure that you have a backup of your data.

Hope that helps

---

