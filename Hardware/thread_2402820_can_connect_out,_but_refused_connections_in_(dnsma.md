---
title: "can connect out, but refused connections in (dnsmask, ssh, ping, etc)"
date: 2018-10-04
forum: Hardware
---

### Post by s.kelly on 2018-10-04
I have a computer that has been set up on our network for a few years. 
But sometime in the last month, i have lost the ability to ssh into the machine. 
when I plug a keyboard and monitor in, I can ping and ssh into other machines on the same network, but the machine refuses any connections in. Like it's network services are all exit only. 
Have tried restarting all services including networking.
Even rebooted the computer (it had an uptime of 248 days)
Nothing has changed in it's configuration in months.
I had thought perhaps that another machine was using the same IP address on our network, but our router tells me that it is the only one. 

The router software could see that it was connected, however nothing else seems to be able to.


thanks for any tips on this.

---

### Post by TheFu on 2018-10-04
Welcome to the forums.

First thing is to look at the system log files for a hardware issue.  If it hasn't been rebooted in 3/4 of a year, it has some major security problems since there are remote root exploits in the kernel from earlier this year.

2nd thing after fixing any hardware issues, it is get it on a weekly patching schedule that includes rebooting whenever the kernel or libc gets replaced.  This happens about once a month, depending on the specific release.

3rd thing is to check the release being used and ensure it is still supported.  If it is a few years old, it is highly likely that the release being run is out of support and just waiting to be hacked, if it hasn't been already.  **more /etc/lsb-release** will show that data.

It is hard for anyone here to help without a currently patched system and knowing which release it is running.

---

