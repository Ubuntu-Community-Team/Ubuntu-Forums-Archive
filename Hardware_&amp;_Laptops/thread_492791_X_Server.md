---
title: "X Server"
date: 2007-07-05
forum: Hardware &amp; Laptops
---

### Post by ifno on 2007-07-05
Hi,

I'm fairly new to Ubuntu and have been trying to setup a file server (using Samba) for a small number of machines. Yesterday I fitted a 500GB USB drive and used gparted to format etc. All seemed to be going well but I was having great difficulty setting permissions for the drive - was working my way through this and other forums in search of answers. Following a restart I got the following screen:

"Could not start X server (your graphical environment) due to some internal error. Please contact your system administrator or check syslog to diagnose. In the meantime this display will be disabled. Please restart GDM when the problem is corrected"

I'm stumped! The only thing I can think of is that when using gparted I had to switch video drivers but the machine has been restarted several times since and no problems.

The last thing I did was to edit /etc/fstab in order to edit permissions of USB drive.

Help greatly appreciated!

Thanks.

---

### Post by geraldm on 2007-07-05
You need to provide information to get help.  
Is your question about the X server not coming up?  When it fails, it falls back to
console mode screen which tells where the log file is.  The reason it failed is to
be found in the log.  NOTE: there MAY also be a log in ~/.xsession-errors for the
user that attempted to start x.  If you do not find out why, then provide
hardware and logs.

Is the question about editing fstab?  Usually USB keys would only be in 
fstab when it is considered permanent to the system.  Temporary USB keys
would have permissions set in /etc/udev/rules.d/*

Gerald

---

