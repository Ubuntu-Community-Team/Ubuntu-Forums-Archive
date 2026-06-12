---
title: "Dual monitor DisplayPort &amp; VGA not working"
date: 2019-11-27
forum: Hardware
---

### Post by tctimmeh on 2019-11-27
I have installed Ubuntu 19.10 on a Lenovo ThinkCenter M710e. It has a VGA and DisplayPort outputs. If I plug a monitor into the VGA port then Ubuntu will only boot to a black screen unless I use nomodeset. Without the VGA monitor it boots up just fine and uses the DisplayPort monitor.

lspci shows:

```

$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation HD Graphics 630 (rev 04)

```

Ubuntu doesn't show any third party drivers available to install. I would really like to get the dual monitors working but I'm not sure where to go from here. Can anybody help me determine what needs to be done?

---

