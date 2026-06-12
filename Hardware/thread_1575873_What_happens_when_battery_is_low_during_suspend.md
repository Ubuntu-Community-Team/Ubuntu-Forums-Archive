---
title: "What happens when battery is low during suspend?"
date: 2010-09-16
forum: Hardware
---

### Post by spupy on 2010-09-16
I put my laptop to sleep (suspend) while my battery was low (~10%), planning to plug it in after going home. I forgot to.
The next day when I opened it, it wasn't suspended anymore, of course, since there was no more power. But when I booted, it resumed from hibernation. There was also a dialog box alerting me that the laptop will go to hibernation soon, because the battery is depleted.

Now my question is: How did it go from suspend to hibernate? I'm pretty sure that ubuntu isn't doing suspend+hibernate when I close the lid, since the process takes shorter time than hibernate would. Did the laptop sort of wake up from suspend, so a hibernate action can be performed? Or perhaps it can go from hibernate to suspend without resuming?

EDIT: Macs have a feature, let's name it Hybrid Sleep, where even though it suspends to RAM, it also copies the contents of the memory onto the disk. This way, in case power to the memory is lost, the previous state can be restored from the image on the harddisk. It's essentially suspend + hibernate as a backup. Does Ubuntu do this as well?

---

