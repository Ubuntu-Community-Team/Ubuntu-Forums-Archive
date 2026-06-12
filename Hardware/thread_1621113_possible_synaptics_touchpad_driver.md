---
title: "possible synaptics touchpad driver?"
date: 2010-11-13
forum: Hardware
---

### Post by syraleo on 2010-11-13
[https://launchpad.net/ubuntu/maverick/+source/xserver-xorg-input-synaptics/1.2.2-2ubuntu5](https://launchpad.net/ubuntu/maverick/+source/xserver-xorg-input-synaptics/1.2.2-2ubuntu5)

i just decided to try linux again after 10 years , the touchpad thing is annoying me to no end and after googling a bit, could this be a possible driver for the touchpad?

i'm using a hp dm4 1019tx , i need my right click and the ability to hold the left click and move the window with my 2nd finger.

---

### Post by gnulab on 2010-11-14
I'm facing the same problem too with HP Probook 4420s.

I can't right click and holding down the left click while using the 2nd finger to drag a window around isn't possible at all.

Installing ubuntu 10.10 to a Kohjinsha netbook as well as Kubuntu 10.10 on a Compaq CQ40 were without any hitch. Could it because this laptop is a multi gesture touchpad?

I do not know how to troubleshoot this matter. Anyone facing the same problem and know how to solve or at least troubleshoot it?

Thanks
Henry

---

### Post by yueng on 2011-04-01
I am also using a HP Probook 4420s and I have the same problem. For the right click, I started using the button between the "alt gr" and "right control". For the other problem, well I don't have a solution but to double click and hold. I mean, they are not solutions but workarounds. Hope, someone can give us a hand a find a proper driver and share it.

---

### Post by belltown on 2011-04-01
There is [Bug #308191]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/308191") that seems to indicate that the right-click functionality for certain Synaptic touchpads is broken in the kernel used by Ubuntu 10.10. It should be fixed in the next release. There are a couple of workarounds mentioned, one that configures the touchpad as a psmouse that doesn't seem to always work consistently, and another that enables multitouch functionality that will allow you to use a two-finger tap to emulate a right-click. To use this you install synaptics-dkms-1.1.1-all.deb (there's a link to it on the right side of the bug report under Bug attachments).

A recent comment in the bug report states: "This bug, as stated in the title, has been fixed upstream, 2.6.38, and  has been released in natty. There is also a package linked in this bug,  confirmed by a large number of users, to work on maverick. Therefore, I  am marking this bug as fixed." I'm not sure where the package is that works on Maverick that would enable the right-click button. If anyone knows can they post a link please?

---

