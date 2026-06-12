---
title: "Unable to make Gigabit adapter work inside VirtualBox for Windows XP SP3"
date: 2015-10-23
forum: Hardware
---

### Post by Peter_Jacob_Allen_ on 2015-10-23
So far, I have been yet unable to make Gigabit adapter work inside VirtualBox for Windows XP SP3 since Windows XP SP3 does not recognize it due to having no drivers for it. Is there a driver for it out there that I can somehow transfer into the VirtualBox Windows XP SP3? And if so, how can I do that? I have been so far unable to make my wireless adapter be recognized so I can use that instead for the Windows XP SP3 in VirtualBox. Any suggestions would be much appreciated.

---

### Post by The Cog on 2015-10-23
The guest operating system (XP) only sees hardware that the host OS chooses to emulate. So the host must have drivers to be able to use that adapter (sometimes a problem with Linux where manufacturers refuse to release Linux drivers). And the host then has to emulate some kind of network adapter for the guest to "see".

Assuming that the host OS has drivers for the adapter, in VirtualBox there is a networking configuration section where you may (I don't remember for sure) be able to choose which physical adapter the guest sees, and what type of adapter it looks like to the guest.

---

