---
title: "virtualbox kernel for 2-6-24-22"
date: 2008-12-02
forum: General Help
---

### Post by mixmaster on 2008-12-02
Since the ubuntu kernel got bumped to -22 I've been unable to run virtualbox - I get this error message:
> VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..
I assume this is because the most recent vbox kernel in the ubuntu repository is -21.  Is there anywhere I can go to get a matching kernel or some hack I can apply to bypass this restriction?

---

### Post by bollix47 on 2008-12-02
Try opening a terminal and inputting the following:

```
sudo /etc/init.d/vboxdrv setup
```

Not positive that this works with the repository version but know it works with the version I'm using from Sun.

---

### Post by mixmaster on 2008-12-02
Tried that - no dice unfortunately.  I got this:
> 
$sudo /etc/init.d/vboxdrv setup
[sudo] password for leng: 
 * Usage: /etc/init.d/vboxdrv {start|stop|restart|status}
$sudo /etc/init.d/vboxdrv start
 * Starting VirtualBox kernel module vboxdrv                                    
 * No suitable module for running kernel found.
$sudo /etc/init.d/vboxdrv status
 * VirtualBox kernel module is not loaded.


Thanks anyway.

---

### Post by Kristopher on 2008-12-02
+1 waiting for this module to come out

---

### Post by mixmaster on 2008-12-04
Well, as a workaround I'm using a previous kernel offered by grub (21-generic).  I can now use virtualbox again although for some reason I had to force a re-install.

There is a bugzilla open against this.  Apparently the problem has been around for the best part of a year.  Hopefully it will be fixed properly soon.  As an alternative workaround it had been suggested that I use the PUEL version but since I am using it in a commercial environment I don't think that is a good idea.

Bugreport here : [https://bugs.launchpad.net/ubuntu/+source/virtualbox-ose/+bug/179807](https://bugs.launchpad.net/ubuntu/+source/virtualbox-ose/+bug/179807)

---

### Post by detroit/zero on 2008-12-04
> **bollix47 said:**
> Try opening a terminal and inputting the following:

```
sudo /etc/init.d/vboxdrv setup
```Not positive that this works with the repository version but know it works with the version I'm using from Sun.
+1 Works for the version from Sun.

---

### Post by bodycoach2 on 2008-12-04
> **bollix47 said:**
> Try opening a terminal and inputting the following:

```
sudo /etc/init.d/vboxdrv setup
```

Not positive that this works with the repository version but know it works with the version I'm using from Sun.

Thanks! Worked for me. I'm also using the version from Sun

---

### Post by r+9 on 2008-12-04
I miss my virtualbox-ose....

I'm going to have to watch out before future kernel upgrades, I didn't realize this would happen when I upgraded to 8.10.

oh well. I guess we wait?

---

