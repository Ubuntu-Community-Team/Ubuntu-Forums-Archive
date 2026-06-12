---
title: "Kernel panic - link_path_walk"
date: 2008-10-05
forum: General Help
---

### Post by ikus060 on 2008-10-05
Hi,

First I have a generale question here about Kernel Panic. I want to know if there is any way to get a logs of this Kernel Panic information. One I look into syslog or messages, I don't have any use full information about the crash it self. It's very anoying. There is any way to enable the logs system for KernelPanic ?

Than, here the situation. I have a host server (Ubuntu Hardy) running VMWare server 1.0.4 and a guest (Ubuntu Edgy).
This morning at 7h35, the host server just stop responding. First I thought it' was a temperature problem, cause the air cooling was off.
By looking at the host logs, there is nothing special. One looking at the guest logs, I have this:
```
Oct  5 07:35:14 localhost kernel: [43202793.270000] ibm_acpi: ec object not found
```
it's the last logs line I have before the server crash.


The same day, between 20h and 21h, the guest system crash with a kernel panic. I don't know if there any relation with the first crash, but here the Kernel Panic I got.
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=87444&stc=1&d=1223259875[/IMG]

---

