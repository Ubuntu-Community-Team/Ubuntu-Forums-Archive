---
title: "Resume Issues on Intel Atom Server 9.10"
date: 2010-06-27
forum: Hardware
---

### Post by kuchera68 on 2010-06-27
Hello,

   I have finally took the step in registering myself on the forums and built up the courage to do my first post. I believe I have found a bug (as I believe many other people have) in the power management on my ubuntu server. Since I am fairly new to Linux/Ubuntu, and completely new to the forums, I wanted to ask if someone is seeing the same problems as I am, and find out if/how to file a bug report if it is required.

  I built my NAS server 4 months ago using the Intel Atom 330 processor, 1GB of ram, and a 2 drive sata linux raid. I struggled through tutorials but eventually got familiar with Ubuntu and had a well running Smaba/Apache/SSH server that automatically detected if no more computers were on the network and was put to sleep through pm-suspend. Wake up was performed remotely with the magic packet solution. It worked great for 2 months straight without rebooting.

  Then I started noticing that sometimes the server would not come back out of standby. I could hear it start up, but only black screen, no communication on the network (no response on ip ping), no access to samba drives. Only thing that would would fix it is cycling the power. I checked the pm-suspend logs and kernel logs and they didn't have any entries for the time span of the wake command. 

  As the last effort, I reinstalled the 9.10 version, and also tried a fresh install of the new 10.04. No success, in fact, 10.04 seemed to exhibit this behavior every 2-3 resumes. What finally solved it, was that I realized the kernel during the fresh install of 9.10 was different than when I originally installed it (2.6.31-22 vs 2.6.31-14). I didn't realize that the kernel was getting updated automatically. With that knowledge, I installed the old kernel (2.6.31-14-generic) and removed the new one and rebooted. The server has been sleeping and resuming for 10 days without a single problem. I put a hold on the kernel and won't upgrade again without a full backup first.


So, my questions:

1. I have read in the forums that many people have had issues with laptops. Are these the same issues as mine?
2. How do I find out if an existing bug report covers my issue?
3. Should I file a bug report myself?

I hope that I have given the correct information, and posted in the correct place. Thanks for reading and please have mercy on a first time poster.

Josh

---

### Post by mikewhatever on 2010-06-27
Hi, and welcome to the forums.
I'd say, go ahead and file a bug report. In case the same bug on the same hardware has already been reported, they'll merge yours with the existing one.

---

### Post by kuchera68 on 2010-06-27
I posted a bug report. For anyone who is interested in following it:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/599116](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/599116)

Josh

---

