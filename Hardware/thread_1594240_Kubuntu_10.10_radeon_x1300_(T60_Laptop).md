---
title: "Kubuntu 10.10 radeon x1300 (T60 Laptop)"
date: 2010-10-12
forum: Hardware
---

### Post by pchaffey on 2010-10-12
Hi all,

I have just updated from 10.04 to 10.10 Kubuntu on my Lenovo T60 laptop - everything works well except my ATI radeon x1300 graphics which although working is very slow. Currently glxgears runs at 230 fps.

Previously for 10.04, I edited /etc/default/grub and changed to GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset" (added the nomodeset) followed by the normal sudo update-grub.

I have tried this for 10.10, and yes I get the accelerated graphics at 5000 pfs in glxgears, but if I open a terminal, minimise it and then maximise it, X completely crashes out and returns to the login splash window. This did not occur in 10.04.

I have tried looking through the more logs: syslog, Xorg.0.log, and dmesg but I cannot find any messages to help.

Any ideas anyone ?

Thanks in advance.

---

### Post by pchaffey on 2010-10-14
Bump....

Any ideas anyone ?

---

### Post by arthur_8200 on 2010-10-16
Hi pchaffey,


I have related problems, since I have upgraded from 10.04 amd64 to 10.10 amd64 the 3d performance is very bad.

lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc M52 [Mobility Radeon X1300]


There is no proprietary drivers available anymore. Or is it available on your notebook?

---

### Post by pchaffey on 2010-10-16
Hi Arthur_8200

> **arthur_8200 said:**
> I have related problems, since I have upgraded from 10.04 amd64 to 10.10 amd64 the 3d performance is very bad.

lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc M52 [Mobility Radeon X1300]


lspci returns the same for me.

> **arthur_8200 said:**
> 
There is no proprietary drivers available anymore. Or is it available on your notebook?

I am using the open source ATI driver (for 10.04 also) which when you use the nomodeset command, the performance goes up to a very reasonable speed. Its just when using the open source driver with kubuntu 10.10 and nomodeset the X windows system crashes by just maximizing and minimizing a window - the performance is high when testing using glxgears though.

I would like to know where to look for finding a hint of whats causing the problem - I looked around the normal log files but couldn't find anything useful.

---

### Post by omniuni on 2010-10-19
I'm having the same problem. Kubuntu 10.10 (Maverick) AMD64 with an ATi Radeon X1250.

---

### Post by omniuni on 2010-10-19
I have filed a bug report at Launchpad. Please let them know that it affects you too.

[https://bugs.launchpad.net/ubuntu/+bug/663660]("https://bugs.launchpad.net/ubuntu/+bug/663660")

---

