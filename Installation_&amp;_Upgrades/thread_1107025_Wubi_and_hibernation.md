---
title: "Wubi and hibernation"
date: 2009-03-26
forum: Installation &amp; Upgrades
---

### Post by KeithH on 2009-03-26
The Wubi FAQ is ambiguous: when it states  "Hibernation is not supported under Wubi". Does this mean that a pc will not enter the hibernation state when actually running Wubi -- or does it mean that, once Wubi has been installed, hibernation when running Windows will no longer work?

Also, if one uninstalls Wubi, is the Windows boot loader restored to its original state (so that it boots up Windows straight away, rather than displaying the Windows Boot Manager screen and waiting for a user response?

Thanks

---

### Post by ugly_peter on 2009-04-23
So, here is what I think. I haven't tested this, but I don't think it would make sense otherwise.

1. Hibernate will still work in Windows. Hibernate will not work in Wubi; i've never had any success with hibernation with Ubuntu in general though. I suspect it will behave similar to simply getting stuck at some black screen and force you to do a hard reboot if you try to hibernate.

2. It should. However, it isn't too much trouble removing an entry from the bootloader either. A quick google will show you how.

However, I am curious about the current state of things. The last time I used Ubuntu was 8.04 and I have heard that hibernation support has improved since then. Is this also the case for Wubi? The FAQ has not been updated for 9.04. It would be great if hibernate worked at least to some extent in Wubi.

---

