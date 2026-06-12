---
title: "apt-get install ssh without starting?"
date: 2008-07-11
forum: General Help
---

### Post by quinthar on 2008-07-11
Is there any way to "apt-get install ssh" without having it automatically start sshd?  Same for "lighttpd".

Basically, I'm making great progress in my [bootable QEMU image script]("http://blog.quinthar.com/2008/07/building-1gb-bootable-qemu-image-using.html"), but when I chroot in to install packages it automatically starts them up.  This isn't too horrible -- I can just stop them -- but it complicates my script and leaves a slightly polluted image behind.  (Furthermore, stopping a process inside a chroot is annoying because you first must mount /proc inside.)

Is there any "-o" option to the ssh and lighttpd installers to do everything *except* start them?  Thanks!

-david

---

### Post by NullHead on 2008-07-11
I believe you can do this with sysv-rc-conf. This you can use to disable services on boot up. FYI it needs to be run from the terminal. ;)

Install it like so: ```
sudo apt-get install sysv-rc-conf
```

---

### Post by quinthar on 2008-07-11
Well, that will let me stop it from starting on future boots, but that's not quite what I'm looking to do.

Rather, I *do* want it to start on future boots.  I just don't want it to start immediately after installation.

Any tips for that?

Thanks!

-david

---

### Post by NullHead on 2008-07-12
um ... they should already start after installation. :confused:

You can manually start/stop them by doing: ```
sudo /etc/init.d/sshd <start/stop>
```

---

### Post by quinthar on 2008-07-13
Yes, they do start after installation, and that's the problem: I don't want them to start right away.  Rather, I want them to start up for the first time when the machine boots.  I want to install lighttpd and take a snapshot of the totally-clean, never-run installation, and then reboot and have it start up for the first time.  Any ideas?

---

### Post by unutbu on 2008-07-13
```
sudo apt-get --download-only install openssh-server
cp /var/cache/apt/archives/openssh-server_1%3a4.6p1-5ubuntu0.5_i386.deb /tmp         # or some working dir
cd /tmp
dpkg --control openssh-server_1%3a4.6p1-5ubuntu0.5_i386.deb
```

The control files will be deposited in a directory called /tmp/DEBIAN

Look inside /tmp/DEBIAN/postinst:

```
setup_init() {
	if [ -x /etc/init.d/ssh ]; then
		update-rc.d ssh start 16 2 3 4 5 . stop 84 1 . >/dev/null
		if [ -x /usr/sbin/invoke-rc.d ]; then
			invoke-rc.d ssh restart
		else
			/etc/init.d/ssh restart
		fi
	fi
}
```

setup_init is the one of the functions called by the postinst script, and here we see the command that starts the sshd server.

You could comment out 
```

# 		if [ -x /usr/sbin/invoke-rc.d ]; then
# 			invoke-rc.d ssh restart
# 		else
# 			/etc/init.d/ssh restart
# 		fi

```
Then you could build your own custom deb package with the modified postinst script.
I don't know much about this last step; Here are some links which may help however: [http://www.linuxdevices.com/articles/AT8047723203.html](http://www.linuxdevices.com/articles/AT8047723203.html),
[http://ubuntuforums.org/showthread.php?t=51003](http://ubuntuforums.org/showthread.php?t=51003)

---

### Post by quinthar on 2008-07-14
Aha!  Turns out the real solution is this:

1) Create a file /usr/sbin/policy-rc.d containing:

#!/bin/sh
exit 101

2) chmod +x /usr/sbin/policy-rc.d

After that, packages will install correctly, but not start.

Once you're done and ready to snapshot your pristine chroot/image, just delete that file.  That will let the service start as normal on future boots.  Cool!

-david

---

