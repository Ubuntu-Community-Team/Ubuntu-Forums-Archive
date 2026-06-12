---
title: "acpi fujitsu does a shutdown instead of standby"
date: 2007-01-19
forum: Hardware &amp; Laptops
---

### Post by thor918 on 2007-01-19
Hi.
I have a lifebook b2130 and when I push the suspend button, the pc is put to sleep.
this is how the pc responds when the acpi is turned off (I get error message when ubuntu is booting : bios is old 99 and it suggests me to add a acpi= force in the boot parameters.).

I have now added acpi=force and it seems it is enabled.
the problem is that instead of getting the pc to sleep, it will do a complete shutdown.

I want to be able to use the acpi scripting, and I want it to go to standbymode instead of a shutdown.

do anyone have a clue how to enable acpi to sleep?
I'm using drapper with a 2.6.19-custom kernel. (I also have 2.6.18.3-custom, but I have the same results there)


I also tried to run:
lsmod | grep acpi
asus_acpi              16152  0

is there a spesific acpi for fujitsu?

by the way. it seems pc is slower when the acpi is enabled...

---

### Post by thor918 on 2007-01-19
okei. I just ditched acpi, and got apm to work ;)
it does in fact have scripting capabilities as well
look in /etc/apm/script.d

these links helped me on the way:
[http://ubuntuforums.org/showthread.php?t=2368](http://ubuntuforums.org/showthread.php?t=2368)
[https://help.ubuntu.com/community/SuspendHowto](https://help.ubuntu.com/community/SuspendHowto)
[http://www.ubuntuforums.org/showthread.php?t=2620&highlight=apm](http://www.ubuntuforums.org/showthread.php?t=2620&highlight=apm)
[http://www.akos.uklinux.net/biblo-linux/](http://www.akos.uklinux.net/biblo-linux/)

I found this great link: explains how to get status and mode shange using command
[http://gentoo-wiki.com/HOWTO_Getting_APM_Suspend_to_Work](http://gentoo-wiki.com/HOWTO_Getting_APM_Suspend_to_Work)

the only thing I'm wondering now is why it dosent detect the suspend button press when I'm running rdesktop app, it will however imidiatly detect button events once the program shuts down....

---

### Post by thor918 on 2007-01-20
> **thor918 said:**
> 
the only thing I'm wondering now is why it dosent detect the suspend button press when I'm running rdesktop app, it will however imidiatly detect button events once the program shuts down....

I found out that upgrading to rdesktop 1.5 will get the events fired, but it's awfully slow.
So I think it has something to do with rdesktop's code.
(the acpi button seems to be detected fast, but it seems I can't use acpi on this laptop even though the spesifictions says it supports both apm and acpi... the reason is that the laptop seems slow when it is turned on, and it only shutdown the computer, not put it to sleep)

---

