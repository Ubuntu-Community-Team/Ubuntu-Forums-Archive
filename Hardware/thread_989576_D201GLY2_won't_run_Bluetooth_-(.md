---
title: "D201GLY2 won't run Bluetooth :-("
date: 2008-11-21
forum: Hardware
---

### Post by zorglups on 2008-11-21
Hi Folks,

I'm running Ubuntu on an Intel D201GLY2 and like this board because it is totally fanless.

Thanks to the Ubuntu forum and also this page, I got the video working fine in Hardy 8.04:
[http://ncc-1701a.homelinux.net/WikiBerd/index.php?page=LinuxSis67x]("http://ncc-1701a.homelinux.net/WikiBerd/index.php?page=LinuxSis67x")

Unfortunately using a bluetooth dongle freezes the box as soon as the bluetooth device reconnects.

This hang is solved in kernel 2.6.25 as indicated in [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/183311]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/183311").

Unfortunately, there is no working video driver for the Intel D201GLY2 working with 8.10.

My exact kernel version is 2.6.24-19-386.

What are my options ?

Thanks,

Pierre

---

### Post by zorglups on 2008-11-26
Bump

---

### Post by zorglups on 2009-02-02
Here is how I solved my issue:

I upgraded from Hardy to Intrepid to get a newer kernel and get rid of the kernel freeze.

I then downgraded Xorg from 7.4 to 7.3 to have my sis driver working.
The downgrade process is nicely explained here: [http://dailyvim.blogspot.com/2008/12/ubuntu-downgrading-xorg.html](http://dailyvim.blogspot.com/2008/12/ubuntu-downgrading-xorg.html)

Best regards,

Pierre

---

