---
title: "No HMDI Audio"
date: 2013-05-05
forum: Hardware
---

### Post by Curlydave on 2013-05-05
I just installed Ubuntu 13.04. I have no HDMI audio. Under sound settings, my device is not listed. According to a search, this is due to a glitch in the kernel. Some people solved it by installing kernel 3.8.0-17.

I'm having trouble finding instructions on installing a kernel. I tried 'sudo apt-get install linux-headers-3.8.0-17-generic' in a terminal, but it can't find the package.

---

### Post by Yellow Pasque on 2013-05-06
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1169984](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1169984)
...
[https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)

---

### Post by Curlydave on 2013-05-06
Thank you - that solved my problem. The Ubuntu wiki article had very clear instructions; good rolemodel for Linux how-to articles.

---

