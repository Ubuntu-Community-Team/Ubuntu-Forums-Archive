---
title: "Does not power off or reboot Thinkpad, but can do on LiveCD"
date: 2009-12-13
forum: Hardware
---

### Post by mycenae on 2009-12-13
Hello,
When I run 9.10 as LiveCD on IBM Thinkpad 600x, Shutdown and Reboot work fine. Shutdown can power off the Thinkpad and Reboot can reboot.

However when install to harddisk, Shutdown cannot power off and Reboot restarts the Thinkpad but stop at memory test.

I have tried several combinations of acpi=xxx, apm=xxx. The best I could do is having power off by setting acpi=force. No success on Reboot.

Any suggestion ?

---

### Post by mycenae on 2010-01-02
It's the ndiswrapper. I have added to the reboot script the command to remove ndiswrapper. The Restart is now working.

---

