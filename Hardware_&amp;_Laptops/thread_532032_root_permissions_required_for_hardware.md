---
title: "root permissions required for hardware"
date: 2007-08-22
forum: Hardware &amp; Laptops
---

### Post by Xunbunutu on 2007-08-22
Hello,

My problem is that accessing the hardware via ISA requires root permissions. Previously on unixy OSes sticky permissions did this, but using chmod ua+s doesn't seem to work.

The application is written in java with a JNI interface to the ISA bus. It runs fine when logged on as root (su), or when the hardware access is disabled. 

I've attempted to use the /etc/sudoers file to disable the password which works but then Xlib refuses to connect to the xserver and the Application bails on screen initialisation. 

All I really need is a launcher on a user desktop that launches the application with root privileges.

Thanks

---

