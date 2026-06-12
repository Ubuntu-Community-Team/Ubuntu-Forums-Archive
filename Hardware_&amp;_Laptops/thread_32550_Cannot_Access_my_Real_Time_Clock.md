---
title: "Cannot Access my Real Time Clock?"
date: 2005-05-08
forum: Hardware &amp; Laptops
---

### Post by raid517 on 2005-05-08
Hi can anyone tell me how to allow devices and applications to gain access to my /dev/rtc (real time clock)? A bunch of applications like VMware and Mplayer and so on perform very poorly because they cannot access it.

Mplayer says:

```
Linux RTC init error in ioctl (rtc_irqp_set 1024): Invalid argument
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
```

VMware says:

```
The host high-resolution timer device (/dev/rtc) cannot be set up to deliver interrupts (Invalid argument).  Certain versions of the Linux kernel do not support this feature. Without the device, the guest operating system can fail to keep time correctly. To avoid this problem, see [http://www.vmware.com/info?id=34.](http://www.vmware.com/info?id=34.)
```

Also several of my games are performing very poorly and I can only assume that they are having similar issues. 

I am not certain how to make a start up script that will work. I was going to ask how to do this. But before I did I decided to try entering the suggested command on the command line.

This is what happend:

```
echo 1024 > /proc/sys/dev/rtc/max-user-freq
bash: /proc/sys/dev/rtc/max-user-freq: No such file or directory
```

I looked and indeed I have no such file in my RTC directory.

I would simply try adding it. But a) I'm not sure what effect this would have and b/ AFAIK /proc contains a virtual file system that is wiped after every reboot anyway.

Can anyone offer any input?

Best regards,

GJ

---

