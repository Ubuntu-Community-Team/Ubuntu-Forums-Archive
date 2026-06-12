---
title: "hdparm.conf is not read upon booting"
date: 2009-12-21
forum: Hardware
---

### Post by grandsatrap on 2009-12-21
I have searched all over for how hdparm.conf works. Instead of typing in hdparm commands at the commandline, I have configured /etc/hdparm.conf  However, I don't know how to make the hdparm.conf take effect when I reboot the computer. 

I haven't been able to find any postings that clearly say how to do this.

One webpage said type this: "sudo update-rc.d hdparm defaults" but it says "update-rc.d: /etc/init.d/hdparm: file does not exist". I am not sure what hdparm file it is looking for. My hdparm is in /sbin/hdparm

Other suggestions are to add some line to /etc/sysconfig -- but I don't have this file,
or to add something to /etc/rc.local  rc.local is empty, (except for "exit 0") so I'm not really sure if this is the best way to do things.

Also:
 I did "sudo apt-get install powermanagement-interface"
This doesn't seem to do anything useful. Can I uninstall it, or does hdparm need it?:(

---

