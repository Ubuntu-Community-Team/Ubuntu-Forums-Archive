---
title: "Restart required for webcam to work; how to manually restart?"
date: 2009-01-11
forum: Hardware
---

### Post by bluebook on 2009-01-11
After some ubuntu update recently, my webcam has stopped working with Skype after my computer has been on for a while. It still works if I restart my computer, then open skype and try to use it, but it has yet to work hours after that (perhaps because I am hibernating in between, not sure). 

It appears that what is happening is that the camera is "busy" but that is just my impression.

Is there any way to "restart" the webcam via a terminal command while the computer is on? Or alternatively, does anyone know what could be happening with the camera not starting?

---

### Post by wmdiem on 2009-01-11
you might try using lshw to figure out which module is running it, then use modprobe -r to unload that, and plain ol' modprobe to reload the module. But i actually have no idea how webcams work (i.e., whether there is a module associated with it).

---

### Post by ItalOz on 2009-01-29
got the same problem here on a DELL inspiron 1525, sometimes, only sometimes, the camera does not work and I have to restart ubuntu to make it work again with skype or cheese...

so BUMP!

---

### Post by PatricioLearner on 2009-06-13
I think I have the same problem.  The cam used to work but doesn't any anymore (I haven't reboot yet).  
From the kern.log:

/var/log/kern.log:Jun 13 15:20:31 patricio-laptop kernel: [29606.529587] uvcvideo 2-4:1.1: resume error -5
/var/log/kern.log:Jun 13 15:26:01 patricio-laptop kernel: [29937.049414] uvcvideo: Failed to query (135) UVC control 2 (unit 3) : -71 (exp. 2).
/var/log/kern.log:Jun 13 15:32:04 patricio-laptop kernel: [30300.054961] uvcvideo: Failed to query (135) UVC control 2 (unit 3) : -71 (exp. 2).

lsusb
Bus 002 Device 002: ID 04f2:b015 Chicony Electronics Co., Ltd VGA 24fps UVC Webcam

---

### Post by PatricioLearner on 2009-06-13
I restarted and the cam works now... it would be great to know how to restart from terminal.

---

### Post by piiotr on 2009-06-14
Same problem here, with hp dv2600, after suspend, about half the time I get the "uvcvideo resume error 1-4 1:1 -5". Camera is listed by lsusb as "ID 04f2:b016 Chicony Electronics Co., Ltd". Works after restart. That's with ubuntu 9.04 64_bit

---

### Post by PatricioLearner on 2009-06-14
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/386799](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/386799)

---

### Post by bastoun on 2009-06-20
Two possibilities to solve your problem:

In a terminal, try this command:

sudo modprobe uvcvideo


If you don't want to use this command everytime, you can modify the file modules in the repository /etc by typing in a terminal:

sudo gedit /etc/modules

and add the line uvcvideo at the end of the file. This modification will force the system to load the module uvcvideo even if no webcam is detected at the boot.

See you.

Seb

---

### Post by anutadanchik on 2009-08-02
I have the same problem with a Logitech webcam.  Worked fine initially for couple months, then reboot seemed to fix it lately, however that has seemed to stop working as well- have rebooted 3 or 4 times now.  I've tried the modprobe uvcvideo command also.

---

### Post by anutadanchik on 2009-08-07
I just tried a new install of Jaunty and it works...

---

### Post by micdhack on 2009-09-18
micdhack@micdhack-laptop:~$ sudo rmmod uvcvideo
micdhack@micdhack-laptop:~$ sudo modprobe uvcvideo
WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.
FATAL: Error inserting uvcvideo (/lib/modules/2.6.28-15-generic/kernel/drivers/media/video/uvc/uvcvideo.ko): Cannot allocate memory

---

### Post by ItalOz on 2009-12-04
I have recently installed 9.10 and I hit the same problem on my Inspiron 1525 laptop with integrated webcam but these two commands from micdhack (thanks) did the job

```
sudo rmmod uvcvideo
sudo modprobe uvcvideo
```

---

### Post by Otto Nascarella on 2010-01-18
yeah....

rmmod + modprobe worked fine.

hopefully they'll find the little bug that needs killing soon

ciao!

---

### Post by angadarora on 2012-05-22
I want to disable my system camera so i am blacklisting it in /etc/modprobe.d/blacklist.conf using command "blacklist uvcvideo".
But I want my external camera to work instead of that which works with the same command "sudo modprobe uvcvideo".So whenever i am giving this command ,system's camera also gets enabled which i dont want.

    So is there any way I can pass the parameter in that command to disable the system camera permanently.

---

