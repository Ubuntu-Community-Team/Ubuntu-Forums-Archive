---
title: "Blank Screen After Login On New Kernel"
date: 2015-09-02
forum: Hardware
---

### Post by ndstate on 2015-09-02
Hello,

If I use a kernel newer than 3.13.0-59-generic my screen goes black after logging in. The computer is a Lenovo y580 with the 2GB Nvidia GeForce GTX660M GPU. How do I begin to figure out how to fix this?

Thanks!

---

### Post by efflandt on 2015-09-03
I think 3.13.0-59 was the kernel version that was broken (it broke steam and I heard wine and some other things). Which Ubuntu nvidia driver package are you using (or did you use something from nvidia.com)? Does your laptop have hybrid graphics (Intel and Nvidia)?

Did you get any errors when updating to newer kernels? Check the term.log files in /var/log/apt. You need to use sudo less to look at those files because they are only readable by root:```
cd /var/log/apt
ls
sudo less term.log
```And if no errors there or not far enough back, look at term.log.1.gz, etc.

---

### Post by ndstate on 2015-10-06
Hello, thanks for your response. I was able to fix the issue by switching to a proprietary driver.

---

