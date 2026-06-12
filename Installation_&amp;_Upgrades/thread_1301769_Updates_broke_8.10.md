---
title: "Updates broke 8.10"
date: 2009-10-26
forum: Installation &amp; Upgrades
---

### Post by phantom3113 on 2009-10-26
I installed the updates that were made available a few days ago (for 8.10 Intrepid) and discovered some abnormalities. The updates consisted of a new kernel (2.6.7-15 I think) and when I restarted, wlan no longer existed. However, booting into the older version of the kernel took it back to normal. My wireless card is a Realtek 8187b and I have the default drivers blacklisted and the official drivers installed (under the original kernel). Would I have to reinstall the drivers for the new kernel?

---

### Post by ptn107 on 2009-10-26
The only changes made to your kernel were security fixes[1].  If you compiled or installed your wireless drivers manually then you will have to recompile them for the new kernel (2.6.27-15).  However if your using drivers compiled and installed from the repositories then dkms should automatically take care of that.  My guess is that another update that was applied messed with something.  Check /var/log/dpkg.log.

[1][https://launchpad.net/ubuntu/+source/linux/2.6.27-15.43]("https://launchpad.net/ubuntu/+source/linux/2.6.27-15.43")

---

### Post by phantom3113 on 2009-10-26
Ok, I'll try recompiling the drivers, as they definitely aren't from the repositories.

---

### Post by slakkie on 2009-10-26
Could also that you need to install linux-backports-modules. Had the same problem this weekend with hardy.

---

### Post by phantom3113 on 2009-10-27
Just finished recompiling the drivers and all is well. Glad this was a just a simple little mishap. Thanks for the help everyone!

---

