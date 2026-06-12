---
title: "Samsung YP-U3 - I cannot to &quot;see&quot; it"
date: 2007-11-18
forum: Hardware &amp; Laptops
---

### Post by ozzyprv on 2007-11-18
Nothing happens when I plug my new mp3/ogg player to my box. 
I tried to fix the problem based on the comments from [this thread]("http://ubuntuforums.org/showthread.php?t=540577&highlight=Samsung") . 

But either I am still far from being decently proficient in Ubuntu or the thread is incomplete.

I do not even have the file: 65-libmtp.rules within the rules.d folder.
This is my ls -al output
> drwxr-xr-x 2 root root  4096 2007-10-27 09:24 .
drwxr-xr-x 3 root root  4096 2007-04-15 05:56 ..
-rw-r--r-- 1 root root   132 2007-04-10 08:03 00-init.rules
-rw-r--r-- 1 root root   272 2007-04-10 08:03 05-options.rules
-rw-r--r-- 1 root root  2518 2007-04-10 08:03 20-names.rules
-rw-r--r-- 1 root root   438 2007-04-04 21:19 25-dmsetup.rules
-rw-r--r-- 1 root root   191 2007-04-10 08:03 25-iftab.rules
-rw-r--r-- 1 root root   119 2007-04-10 08:03 30-cdrom_id.rules
-rw-r--r-- 1 root root  3057 2007-04-10 08:03 40-permissions.rules
-rw-r--r-- 1 root root   210 2007-04-04 03:30 45-hplip.rules
-rw-r--r-- 1 root root 52405 2007-04-15 05:56 45-libgphoto2.rules
-rw-r--r-- 1 root root 46855 2006-09-10 16:56 45-libsane.rules
-rw-r--r-- 1 root root  5716 2007-04-02 09:45 50-xserver-xorg-input-wacom.rules
lrwxrwxrwx 1 root root    19 2007-08-26 10:19 60-libpisock.rules -> ../libpisock9.rules
-rw-r--r-- 1 root root   769 2007-04-10 08:03 60-symlinks.rules
-rw-r--r-- 1 root root  1303 2007-04-10 08:03 65-persistent-input.rules
-rw-r--r-- 1 root root  3923 2007-04-10 08:03 65-persistent-storage.rules
-rw-r--r-- 1 root root   385 2007-04-10 08:03 80-programs.rules
-rw-r--r-- 1 root root   171 2007-02-18 19:18 85-alsa.rules
-rw-r--r-- 1 root root  1443 2007-03-27 06:39 85-brltty.rules
-rw-r--r-- 1 root root    81 2007-03-04 21:46 85-hdparm.rules
-rw-r--r-- 1 root root   719 2007-03-27 04:39 85-hplj10xx.rules
-rw-r--r-- 1 root root   126 2007-10-22 01:07 85-hwclock.rules
-rw-r--r-- 1 root root   708 2007-04-10 08:02 85-ifupdown.rules
-rw-r--r-- 1 root root   950 2007-03-07 14:45 85-pcmcia.rules
-rw-r--r-- 1 root root  2322 2007-04-10 08:03 90-modprobe.rules
-rw-r--r-- 1 root root   210 2007-03-30 11:53 95-hal.rules
-rw-r--r-- 1 root root    77 2007-04-10 08:03 99-udevmonitor.rules
-rw-r--r-- 1 root root  1224 2007-04-10 08:03 README
me@my-box:/etc/udev/rules.d$ 


Thanks in advance.

---

### Post by ozzyprv on 2007-11-18
I found out that I did not have the libmtp packages installed.

I have my Samsumg YP-U3 connected and working!.

PS: Not sure how to mark a post as SOLVED.

---

### Post by daengbo on 2007-11-19
In Ubuntu 7.10, Rhythmbox has an MTP player plugin which will handle your player for you.

---

