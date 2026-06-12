---
title: "must reset computer to turn off or reset computer"
date: 2008-04-22
forum: Hardware
---

### Post by Charles2008 on 2008-04-22
I am having difficulties with DVI and nvidia 7300 GeForce card working with my Samsung Syncmaster 932 BW monitor.  I can't get the computer to reboot or turn off.  It just goes to a blank screen.  I am using the generic nv driver in my xorg.conf file.  I added the following line to my xorg file under device and now I get a display (non blank screen) ```
Option "ConnectedMonitor" "DFP"
```.  I have tried installing the driver from the NVIDIA website and when I do that it has to create a new driver since it doesnt recognize my kernel.  Using Ubuntu 7.1 system.  After I installed the NVIDIA driver, my monitor went to low graphics mode.  I had to stop using that driver to get Ubuntu to work.  Am I doing something wrong here.  pls advise and thanks in advance.

---

