---
title: "disable hyper-threading"
date: 2013-09-22
forum: Hardware
---

### Post by IlPazzo on 2013-09-22
Hi all.

I just wanted to ask if there is a way to disable Hyper-threading in Ubuntu 12.04? Just to try things, not that I have anything against HT.

I read in these [FAQs]("http://www.faqs.org/docs/Linux-HOWTO/BootPrompt-HOWTO.html") that there is a **noht** option to specify at boot time. However, it doesn't seem to work for me. Also I read [somewhere else]("https://bugzilla.redhat.com/show_bug.cgi?id=440321") that in some distro that option is meant to be used only when installing the OS.

To check that HT is enabled/disabled, I follow the suggestions in [this post]("http://askubuntu.com/questions/72999/how-can-i-test-if-ubuntu-activated-hyperthreadinghttp://")  (see answer 5).

Thanks.

---

### Post by tgalati4 on 2013-09-22
Maybe there is a switch in /etc/sysctl.conf.  You would have to do some more research to find it.  It's possible that you would have to compile your kernel to disable it.  Use the kernel configurator to turn it off.  Anyone have a 12.04 build environment to see if there is a kernel config option to turn off hyper threading?

When Hyper Threading first came out, I recall that some desktop computer BIOSes had a switch to turn it off, in case your computer started to smoke.  I would have to check my server's BIOS (with Xeon dual-cores), but that would require a shutdown and attaching a monitor.  How badly do you need to know?

---

### Post by spacesamurai2 on 2013-09-23
Have you given the BIOS a look? This is usually where you access onboard systems and should be able to turn it on/off.

---

### Post by IlPazzo on 2013-09-23
Indeed in some machines is just a BIOS setting as [here]("http://www.youtube.com/watch?v=7rscmqrFWachttp://").

Not in my machine though. Nothing related to HT in my BIOS.

---

