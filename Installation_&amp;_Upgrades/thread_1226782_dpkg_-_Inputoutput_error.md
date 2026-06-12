---
title: "dpkg - Input/output error"
date: 2009-07-29
forum: Installation &amp; Upgrades
---

### Post by Kriticar on 2009-07-29
Few weeks ago I installed updates to my Ubuntu 8.4 but something strange happed in the process.. now I get very simple theme - I don't care for the themes or effects much what bothers me is message saying that there is an error in Gnome power management or something similar to it. When I try updating the system states new error message so I finally try an update and upgrade from terminal and I get this:
> dpkg: failed in buffer_read(fd): copy info file `/var/lib/dpkg/available': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)

---

### Post by Kriticar on 2009-07-30
Well I manage fixing this with "sudo dpkg --clear-avail && sudo apt-get update" command but somehow new dpkg error occurred... 
> E: Problem executing scripts DPkg:: Post-Invoke 'if [ -d /var/lib/update-notifier ]; then  touch /var/lib/update-notifier/dpkg-run-stamp; fi'
E: Sub-process returned an error code
E: Sub-process /usr/bin/dpkg exited unexpectedly


---

### Post by jfolpf on 2009-08-20
> **Kriticar said:**
> Well I manage fixing this with "sudo dpkg --clear-avail && sudo apt-get update" command but somehow new dpkg error occurred...
I tried  what you mentioned "sudo dpkg --clear-avail && sudo apt-get update" and it worked with me...

Thanks a lot

---

