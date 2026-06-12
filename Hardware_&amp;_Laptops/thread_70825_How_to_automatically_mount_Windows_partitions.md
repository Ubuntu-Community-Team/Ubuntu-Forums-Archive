---
title: "How to automatically mount Windows partitions?"
date: 2005-10-01
forum: Hardware &amp; Laptops
---

### Post by LinuxConvert on 2005-10-01
Hi everyone,

I thought I posted this earlier but I can't seem to find the thread now... Never mind I had another question to ask anyway so I'll post again...

I'm new to Ubuntu and Linux and so far its been great but there are a few issues I have yet been able to resolve...

1) Ubuntu doesn't automatically detect my Windows partitions... Everytime i reboot, I have to manually mount them again which is a pain because i dual boot and my documents are in a FAT32 partition so that I can share them between them... Any ideas how to solve this problem?

2) My session doesn't get restored after i shut down (for example, GAIM doesn't automatically come back on when I boot up even though I didn't close it before I shut down, etc) What can I do about this?

3) I have a small home Windows network and Ubuntu detects this fine, except it only detects the Shared Documents folder and not any other shared folder in the network... Is there a way around this, other than typing in the exact destination I want in Nautilus?

If it helps, I always log in to Ubuntu as root, because I can't stand having restricted access to everything all the time... I know its not as safe but I feel the convenience is well worth it :P

I apologise if these questions seem very newbie-like, but I'm quite new to Linux and I'd appreciate any help you guys can give me on these issues... Thanks and keep up the good work!

LC

**EDIT**
I just found my earlier post and even a reply to it so ignore this... Tried to remove this post entirely, but I can't find how... Sorry for the mixup...

---

### Post by brk3 on 2005-10-01
1. See ubuntuguide.org for the line you need to add to your /etc/fstab file.

2. Under the admin menu somewhere is an entry called 'Sessions'. Find this and here you can select an option to save session automatically.

3. Not to sure about this one but probably easy enough :) Maybe someone knows?

---

