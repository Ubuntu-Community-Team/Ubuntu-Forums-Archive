---
title: "touchpad problem after resume"
date: 2006-06-01
forum: Hardware &amp; Laptops
---

### Post by oscarBravo on 2006-06-01
Running Dapper on my Inspiron 6000, I'm having a problem when the laptop "wakes up" from suspend mode: the touchpad doesn't work properly. Specifically, it behaves like a mouse, not a touchpad (the scroll areas don't work, and the sensitivity is all wrong).

It seems to be down to the permissions on the input devices: ```
paul@orac:~$ ls -l /dev/input/
total 0
crw-rw-r-- 1 root root 13,  64 2006-05-30 21:56 event0
crw-rw-r-- 1 root root 13,  65 2006-06-01 19:53 event1
crw-rw-r-- 1 root root 13,  66 2006-06-01 19:53 event2
crw-rw-r-- 1 root root 13,  67 2006-05-30 21:56 event3
crw-rw-r-- 1 root root 13,  63 2006-05-30 21:56 mice
crw-rw-r-- 1 root root 13,  32 2006-06-01 19:53 mouse0
crw-rw-r-- 1 root root 13,  33 2006-06-01 19:53 mouse1
crw-rw-r-- 1 root root 13, 128 2006-06-01 19:53 ts0
crw-rw-r-- 1 root root 13, 129 2006-06-01 19:53 ts1
paul@orac:~$ ls -l /dev/input/
total 0
crw-rw-r-- 1 root root 13,  64 2006-05-30 21:56 event0
crw-rw---- 1 root root 13,  65 2006-06-01 19:54 event1
crw-rw---- 1 root root 13,  66 2006-06-01 19:54 event2
crw-rw-r-- 1 root root 13,  67 2006-05-30 21:56 event3
crw-rw-r-- 1 root root 13,  63 2006-05-30 21:56 mice
crw-rw---- 1 root root 13,  32 2006-06-01 19:54 mouse0
crw-rw---- 1 root root 13,  33 2006-06-01 19:54 mouse1
crw-rw---- 1 root root 13, 128 2006-06-01 19:54 ts0
crw-rw---- 1 root root 13, 129 2006-06-01 19:54 ts1
paul@orac:~$ 
``` I manually set the permissions on the device nodes, as shown in the first listing. Then I suspended and resumed the laptop, with the result you can see in the second listing. The X server naturally has a problem with this: ```
 paul@orac:~$ grep event2 /var/log/Xorg.0.log
(**) Option "Device" "/dev/input/event2"
(EE) xf86OpenSerial: Cannot open device /dev/input/event2
paul@orac:~$ 
``` udev's permissions look like they should be ok - and after all, it works on a fresh reboot: ```
 paul@orac:/etc/udev/permissions.d$ grep input udev.permissions
input/mice:root:root:0644
input/mouse[0-9]*:root:root:0644
input/js[0-9]*:root:root:0644
input/*:root:root:0644
paul@orac:/etc/udev/permissions.d$ 
``` Any thoughts?

---

### Post by Egalus on 2006-06-01
I had the same problem with a selvecompiled kernel and the solution was to build ps2mouse into the kernel and not as a module.

---

### Post by oscarBravo on 2006-06-02
Hmm. Thanks, but my kernel's vanilla. Any other ideas?

---

