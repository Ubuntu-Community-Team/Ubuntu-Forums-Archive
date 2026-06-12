---
title: "Karmic: USB mouse not detected automatically"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by yankee83 on 2009-11-02
Hi,
after upgrading to Karmic from Jaunty my Logitech USB mouse is not detected automatically. Once KDE is started, I have to unplug it and plug it in again to get it activated. Anyone has an idea what the problem could be?
I couldn't find any related post on the forum.
Thanks.

---

### Post by defectivedonkey on 2009-11-04
I was able to use my mouse until I updated yesterday.  Now, it doesn't work no matter how many times I plug it in.  I have no idea what the problem is.  Karmic is still pretty buggy though.

---

### Post by keptjaws on 2009-11-04
me too. It just happened today. I'm sure that new updates caused my mouse not detected. Please guide me how. Thanks.

---

### Post by vincenzoml on 2009-11-11
This happens to me too, but not always. For example, I now plugged in my mouse at boot. Since then, I can unplug and re-plug it as many times as  I like, I can suspend to ram, suspend to disk, everything works fine. But in the previous boot it didn't. Also, to check if this is the same problem, please check if the mouse plugging is signaled in dmesg, in my case it IS even if it does not work in Xorg.

---

### Post by BuffyLinux on 2009-11-12
Same thing here; the USB system finds the mouse just fine, and if I cat the device file or /dev/input/mice I see output from it, but the pointer doesn't move. I assume that the mouse events never get to X; looking in /var/log/Xorg.0.log I see that its looking at the touchpad and the PS/2 mouse, but not /dev/mice. It does have a note in there saying "The server relies on HAL to provide the list of input devices." So I guess its up to Hal to tell X that there's a new mousie, and its not doing so.

But aha! It seems that hald (Hal the daemon?) isn't running at all. When I start him up (sudo service hald start or /etc/init.d/hal start) and re-plug the mouse it works.

So I guess its a question of why hald wasn't running. It looks like it simply never was supposed to start, at least in the normal manner. It could be there's some sort of funny startup method for that, rather than using the normal rc scripts. A casual search doesn't turn up anything about that, but that's hardly conclusive.

In any case, start hald, replug your mouse, and see if that fixes the problem. If so we may need to track down what's happening with hald - crashing, not starting, configuration issue causing hald not to be set to run on some platforms, whatever.

---

### Post by vincenzoml on 2009-11-12
Please all follow up on bug [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/425755](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/425755)

---

### Post by rshetye on 2009-11-15
[http://ubuntuforums.org/showthread.php?t=1277364](http://ubuntuforums.org/showthread.php?t=1277364)

---

### Post by qhor on 2009-11-15
BuffyLinux - Thank you! Identical problem here (including detecting mouse movement via cat /dev/input/mice) on two computers, one desktop and one laptop, that stay on all the time. Doing a:

```
sudo service hal start
```

indeed fixed the problem temporarily without reboot.

You were quite right: hal had crashed since boot some time. Boot was over a week ago for both machines.

vincenzoml - This is a different bug that you have linked to. Similar symptoms, but a quite different problem -- blacklisting uvcvideo solved the problem of USB Hotplugging on the MSI Wind. But, the problem here is that USB hotplugging works at first, but then hal crashes at some point. Thereafter, USB hotplugging will no longer work (even if you suspend/hibernate). Starting hal manually solves the problem.

---

