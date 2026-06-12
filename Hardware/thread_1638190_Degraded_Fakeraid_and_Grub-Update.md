---
title: "Degraded Fakeraid and Grub-Update"
date: 2010-12-05
forum: Hardware
---

### Post by Kalderama on 2010-12-05
Dear community

I run a (fake)raid 1 on my desktop pc for data safety. Recently one hdd failed, so i now run a degraded raid until the replacement hdd will arrive.

After a kernel update, I tried to update grub2, but since then no boot menu appears any more and (fortunately) ubuntu directly starts. For some special tasks, however, I need to start my windows installation, which is impossible without a boot menu.

I tried to update/reinstall grub2, but all attempts failed with the message "**wrong number of devices in RAID set**". What can I do to overcome this problem?

---

### Post by ronparent on 2010-12-05
You might try booting with 'nodmraid' or if that doesn't work temporarily uninstall dmraid. I have no direct experience with your particular but maybe one of these fixes would suffice until you have a new disk. Good luck.

---

### Post by Kalderama on 2010-12-06
Hi ronparent,

thanks for your reply. I didn't want to uninstall/reinstall this time, as I had a hard time when the other disk hat to be replaced. This time i thought i just leave it degraded and let it reassemble itself afterwards. 

In /etc/default/grub i found the things about the hidden menu and was able to unhide it. Then I manually adjusted the boot entry in the grub.cfg-file, and now it works...

However, thanks for concideration!

---

