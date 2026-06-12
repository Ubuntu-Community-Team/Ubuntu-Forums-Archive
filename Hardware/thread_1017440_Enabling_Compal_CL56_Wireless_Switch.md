---
title: "Enabling Compal CL56 Wireless Switch"
date: 2008-12-21
forum: Hardware
---

### Post by ljerabek on 2008-12-21
I've seen several questions on Compal CL56 laptop users who can't get their wireless switch working right. So here is the answer.

Ubuntu 8.04 and 8.10

Here are the steps to get a Compal CL56 Laptop wireless working.

Open a terminal window and do the following steps.

Add acerhk to /etc/modules by the following command:

sudo gedit /etc/modules

Goto the last line in the file... and add the text "acerhk"

Save and Exit

Should look something like this:
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
sbp2
acerhk

Now you need to create an init script in /etc/init.d

sudo gedit /etc/init.d/acerhk_on

Add the following to it:
#!/bin/sh
echo 1 > /proc/driver/acerhk/wirelessled

Save and Exit

Now you need to add this to run at runlevel 2

cd /etc/rc2.d
sudo ln -s ../init.d/acerhk_on S99acerhk_on

You are all done now.

Reboot

Let me know if you have any other questions.

---

