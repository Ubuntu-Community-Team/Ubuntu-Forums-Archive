---
title: "Multitouch trackpad. 11.04. Samsung RV511. Doesn't work."
date: 2011-09-17
forum: Hardware
---

### Post by yonni on 2011-09-17
Hi,

I just bought a Samsung RV511 which has a multitouch trackpad. This works beautifully in windows but not in ubuntu. All I've found so far are pages telling me that "11.04 has multitouch support by default". I get nothing, not even any semblance of any support shown on the settings page for the mouse. I don't even get a scroll area on the RHS of the trackpad. This is exceptionally annoying to constantly having to move to the scrollbar to scroll down a page.

How can I enable multitouch support? Or at least a scroll area on the side of the trackpad?


Many thanks!

---

### Post by fedeg86 on 2011-09-30
Hello yonni,

I found a fix here: [https://bugs.edge.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/681904/+index?comments=all](https://bugs.edge.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/681904/+index?comments=all)

Comment #132

You must Install the package and then run in a terminal:

sudo rmmod psmouse
sudo modprobe -a psmouse


Go to System > Preferences > Mouse and you will see a new tab where you can configure the touchpad.


Works fine with Notebook Samsung RV511 and Ubuntu 11.04 ;)

---

