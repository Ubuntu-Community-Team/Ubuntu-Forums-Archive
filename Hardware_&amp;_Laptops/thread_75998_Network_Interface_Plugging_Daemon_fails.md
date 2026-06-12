---
title: "Network Interface Plugging Daemon fails"
date: 2005-10-14
forum: Hardware &amp; Laptops
---

### Post by burningbed on 2005-10-14
During boot up on my HP Pavilion dv1000 laptop I get the message "Starting Network Interface Plugging Daemon failed" this message stays on for quite a while and boot up gets delayed (I can press CTRL-C to skip this step to speed things up). Later during bootup the same message gets displayed again briefly and this time there's no further delay. Can anyone give me pointers on how to fix this? I'm not sure if this is relevant, but ifplugd is configured as follows (these are all the default settings): static interfaces to be watched by ifplugd: auto, hotplugged interfaces to be watched by ifplugd: all, arguments to ifplugd: -q -f -u0 -d10 -w -I, suspend behaviour: stop. I'm also attaching the output of dmesg.

---

### Post by Zym0tiC on 2005-10-26
I have the same problem with starting the ifplugd.

i configured it with dpkg-reconfigure ifplugd but when it wants to start it fails...

btw: if i get it right, the ifplugd is for wired networks en whereami for wireless?

edit: after a reboot and ps aux | grep plug i see:

root      7024  0.0  0.1   1588   560 ?        Ss   15:58   0:00 /usr/sbin/ifplugd -i eth0 -q -f -u0 -d10 -w -I

so it should be up? but when i boot without a network cable it keeps trying to find a network. after pressing ctrl+c twice and plugin the cable when i'm in gnome it doesn't brings up my network

---

