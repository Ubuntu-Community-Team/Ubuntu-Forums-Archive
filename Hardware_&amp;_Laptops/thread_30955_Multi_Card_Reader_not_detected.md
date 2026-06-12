---
title: "Multi Card Reader not detected"
date: 2005-05-01
forum: Hardware &amp; Laptops
---

### Post by Haegin on 2005-05-01
I moved to linux from windows last weekend and have never used linux for any long period of time before (a few days at most). This weekend the multi card reader i ordered a week ago arrived and i plugged it in and it worked fine for a bit but now it just won't work. I can see it but when i try to mount it (it doesn't automount) I just get the following error message:

mount: can't find /dev/sdd1 in /etc/fstab or /etc/mtab. Please check that the disk is entered correctly.

Also I have just discovered my cd drives dont seem to want to mount either but I don't know whether this is a connected problem or not. I cannot think of anything I have done in the last day or so that may have upset it and as I am new to linux I have no idea how to fix it but as you can probably geuss I do need my card reader and my cd drives to work.

The cd drives show a progress bar that stays on 0% for a while and when I try to access them or refresh the contents it gives me another error (The process for the media protocol died unexpectedly)

Hope this is enough information

---

### Post by Haegin on 2005-05-01
okay - i dont know what i did but after uninstalling hotplug, hal, ubuntu-base, kubuntu-desktop and installing some usbmgr, then uninstalling the usbmgr thing and reinstalling the rest (hal, hotplug etc) and restarting several time it all works fine! Yay!

---

