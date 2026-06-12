---
title: "Lenovo X220 X Server Freezing"
date: 2011-06-01
forum: Hardware
---

### Post by omegatemplar on 2011-06-01
I recently purchased a Lenovo X220 laptop and installed Ubuntu 11.04 on it. The main issue that I am having is that the X server keeps on freezing intermittently without any warning.

I've updated the X Server using the xorg-edgers ppa in hopes of causing the issue to stop.

What other steps can I take in order to track down the cause of the issue and help resolve it?

Thanks.

---

### Post by xelander on 2011-06-16
I can confirm this problem and I think that it's a problem with the graphics driver.

I have a lenovo x220 tablet with Kubuntu 11.04 installed and the git version of the intel graphics driver as described on [https://launchpad.net/~glasen/+archive/intel-driver]("https://launchpad.net/%7Eglasen/+archive/intel-driver") .

---

### Post by xelander on 2011-06-16
I think I found a solution: Upgrade the kernel as described in
[http://ubuntuguide.net/ubuntu-11-04-upgrade-linux-kernel-to-2-6-39-0](http://ubuntuguide.net/ubuntu-11-04-upgrade-linux-kernel-to-2-6-39-0)

In
[http://thinkpad-forum.de/threads/114825-Erledigt-X220i-Ubuntu-11.04-64bit-Freezing-im-Idle-Modus](http://thinkpad-forum.de/threads/114825-Erledigt-X220i-Ubuntu-11.04-64bit-Freezing-im-Idle-Modus)
(german) this is said to solve the freezing issue.

---

### Post by xelander on 2011-06-20
Ok. Three days passed and no more freezing.

---

