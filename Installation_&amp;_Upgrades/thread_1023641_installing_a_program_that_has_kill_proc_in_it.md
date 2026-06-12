---
title: "installing a program that has kill_proc in it"
date: 2008-12-28
forum: Installation &amp; Upgrades
---

### Post by kennydidit on 2008-12-28
I am trying to install a program that has kill_proc in it. Is there any thing I can do as far as replacing that function? 
Here is the error I am getting:

/home/ken/Desktop/dmx4linux-2008-10-07/drivers/devices/usb/usb2dmx.c: In function ‘usb2dmx_delete_interface’:

/home/ken/Desktop/dmx4linux-2008-10-07/drivers/devices/usb/usb2dmx.c:308: error: implicit declaration of function ‘kill_proc’

and here is the line that it is referring too: I think

   if (u2d_if->thread_pid > 0) /* we don't want to kill init */

	{

	  printk ("attempting to kill usb2dmx-thread pid=%d\n", u2d_if->thread_pid);

	  ret = kill_proc(u2d_if->thread_pid, SIGTERM, 1);

	  if (ret)
The program is dmx4linux I am running unbuntu8.10 
If anyone can help it would be greatly appreciated

---

### Post by Partyboi2 on 2008-12-28
Have you tried installing a deb version of it instead of compiling it?
[http://packages.debian.org/etch/dmx4linux-tools](http://packages.debian.org/etch/dmx4linux-tools)

---

### Post by kennydidit on 2008-12-28
yes I have the dmx4linux tools installed, I found that file some time ago and I just rechecked to make sure I had it and I do, but I still cannot get this file to run.

---

