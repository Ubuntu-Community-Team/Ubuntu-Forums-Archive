---
title: "Shut-Down Problems after latest upgrades"
date: 2008-06-03
forum: Hardware
---

### Post by lviggiani on 2008-06-03
Hi All,
I'm running ubuntu 8.04 with nvidia-glx-new driver installed.
In addition I added the following cifs mounts to my fstab file:

//10.0.2.120/Workarea /home/lviggiani/Network/workarea   cifs  auto,credentials=/root/.elccredentials,uid=1000,umask=000,user   0 0

Everithing was working fine until this morning. After doing the latest upgardes, I get this problem:

After the shut down is initiated, the unsplash screen appears and orange the progress bar stops at about 80%. After few seconds, the screen goes in text mode and I get the error that CIFS is not responding. Looking at the screen I see that eth0 is now disabled BEFORE the system tries to unmount the CIFS shares (that was not happening before this morning updates). This I can see if I'm not using the restricted drivers (nvidia).
 If I have restricted nvidia drivers in use, when the system tryes to switch in text mode to display that error, the screen becomes black and some vertical stripes appears in sequence and the screen slowly turns white and freezes....

I think the two problems are not related together:
1) One is that the system de activates the network device before unmounting remote shares
2) The other is that the nvidia restricted driver has problem in switching back to text mode, or something similar.

I can live with problem 2... but problem 1 is something I need to fix.
Any idea?
Thanks!!

---

### Post by sergiom99 on 2008-06-03
Hi there.
You made a duplicate a post about this.

I have the same problem ([http://ubuntuforums.org/showthread.php?t=815800](http://ubuntuforums.org/showthread.php?t=815800)) but I didn't relate it to Nvidia drivers issue. Maybe thats it, but I dunno how to solve it.

Lets hope someone jumps in.

---

### Post by lviggiani on 2008-06-04
Hi,
thanks for the link.

In the mean time I have solved my problem No. 1 by putting a script in
/etc/rc0.d and /etc/rc6.d folders called K09umount :

```
#! /bin/sh
umount /home/lviggiani/Network/workarea
```

In this way, my remote shares are unmounted before the network device is switched off and the shout-down / reboot procedures works fine again.

**NOTE:** I put the same script in both directories, however the Linux gurus tell you to save your script in /etc/init.d folder and put there only a link to that.

---

### Post by sergiom99 on 2008-06-04
Hey.
I see, still no luck with the shutdown/reboot problem.
I liked Gutsy better.

---

