---
title: "Wubi installation"
date: 2008-10-28
forum: General Help
---

### Post by regdabs on 2008-10-28
Spent about 2 hours downloading and installing 8.1 using Wubi because never could get 8.04 to work with wireless.  Seemed to work fine, but when I tried to boot I get a error message that says, boot file system not selected, use partition manager to correct.  I thought using Wubi you did not have to select partitions or file systems, should be automatic.  What went wrong and how do I get things corrected.  Cannot boot to Ubuntu at all, still have access to XP.

---

### Post by Orlsend on 2008-10-29
Can you give us a more detail of the error msg, If you are trying **8.10** which is better at Networking than you could wait till tomorrow when the Official working release comes.

---

### Post by ago on 2008-10-29
Is this during installation? If so uninstall, run chkdsk /r and reinstall. If the problem repeats, boot in verbose mode (press esc at boot) and when it fails press ctrl+alt+f4 to get a terminal

Then run

sudo sh /custom-installation/hooks/failure-command.sh

This will produce c:\ubuntu\installation-logs.zip. Please post them here.

---

