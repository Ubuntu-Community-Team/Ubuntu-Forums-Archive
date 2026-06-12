---
title: "Screen brightness doesn&quot;t work after upgrade to 13.04 on Esprimo Mobile M9410"
date: 2013-05-21
forum: Hardware
---

### Post by PauloI on 2013-05-21
Hi Everybody,

I am quite new to this forum and to Ubuntu. I may say I am totally novice. I have Fujitsu-Siemens Esprimo-Mobile M9410 laptop and I wanted to try Ubuntu.
    Yesterday I dared to upgrade my system from 12.04 to newest 13.04. Unfortunately it seems this decision has been a mistake and system isn't mature enough. The screen brightness window stopped to have any influence on the real screen brightness which is on its minimum level. So screen remains totally dark and I can hardly see anything. A slide bar is a visible but slider doesn't change screen brightness. I have edited grub (GRUB_CMDLINE_LINUX="acpi_osi=Linux") so now I have a nice 10-degrees brightness scale on the top bar "under my thumb". But it hasn't helped. Maybe the problem is I have no vendor (Intel  Mobile Intel® GM45 Express Chipset x86/MMX/SSE2) driver? Could anyone help me and tell me what shall I do, where can I get the driver from and how to install it? Or maybe it is not necessary, because it is an issue of the Ubuntu 13.04 itself? Does anyone know how to fix this issue?
I can remember there was the same issue on Ubuntu 10.xx and then it was fixed on 12.04. I am a total Ubuntu novice and simple Ubuntu-user, I am not an ubuntu programmer, so please, if you know an answer, put in in an easy way.

Thank you,
Paulo

---

### Post by PauloI on 2013-05-23
OK, so I have found a solution. Maybe not perfect but it lets me going on. I searched for "ubuntu intel driver" on google and found out that Intel released Intel Linux Graphics Driver application for Ubuntu.  So I've downloaded .deb package and installed it using Software Center. Apart from the information that among many previous releases that were supported by the drivers, the current one was missing, installation was not obvious due to an intimidating and confusing warning message that Ubuntu showed to me. Namely, it informed that package doesn't conform to some package building rules and instead of declared 3 it consisted of 4 parts. Message stated it was considered a very serious error, could cause an instability of a system... Therefore installation was strongly discouraged... Well it didn't sound well. But I dared and .. it has worked! However what is surprising, Software&Updates, Additional Drivers tab doesn't show any Intel drivers installed. On the other hand Other Software tab shows a Intel Graphic drivers on the list. So I bit unclear. Part of grub I edited: 

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="acpi_osi=Linux acpi_backlight=vendor"
```

So the backlight slider disappeared from Brightness&Lock settings however brightness is very good, I guess it stayes at its maximum level.
So how could I get the slider back now, any ideas?

---

