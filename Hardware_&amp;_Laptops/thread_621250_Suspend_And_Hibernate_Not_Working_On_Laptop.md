---
title: "Suspend And Hibernate Not Working On Laptop"
date: 2007-11-23
forum: Hardware &amp; Laptops
---

### Post by newtonrealman on 2007-11-23
Hi!
I have a VAIO FE-41S and i cannot recover after hibernating or suspending unless i do a hard reset. I've read many topics where ppl have the same problem but i havent seen a working solution.
My graphics are: NVIDIA Geforce Go 7600 GPU

Hopefully someone has a solution for this
Thanks in advance,
Newton

---

### Post by scorp123 on 2007-11-23
> **newtonrealman said:**
>  i cannot recover after hibernating or suspending unless i do a hard reset. My graphics are: NVIDIA Geforce Go 7600 GPU What do you mean by "I cannot recover" .... ?  Does the screen stay black?

My suspicion is that the problem is here in this file: **/etc/default/acpi-support** ... Please make sure the following parameters are set: ```
ACPI_SLEEP=true
ACPI_HIBERNATE=true
ACPI_SLEEP_MODE=mem
MODULES=""
**[COLOR="Red"]MODULES_WHITELIST="nvidia"[/COLOR]**
SAVE_VBE_STATE=false
VBESTATE=/var/lib/acpi-support/vbestate
**[COLOR="Red"]POST_VIDEO=false[/COLOR]**
[COLOR="Red"]**SAVE_VIDEO_PCI_STATE=true**[/COLOR]
USE_DPMS=false
[COLOR="Red"]HIBERNATE_MODE=platform[/COLOR]
LOCK_SCREEN=true
STOP_SERVICES="mysql "
RESTART_IRDA=false
ENABLE_LAPTOP_MODE=false
```

These parameters helped on one of my systems which too has an Nvidia card.

The problem seems to be that when Ubuntu goes into "sleep" it will unload the "nvidia" kernel module but then fail to reload it again when the system resumes. Result: black screen, you don't see anything and have no choice but a hard reset (at least that was the problem in my case).

So I hope I interpreted your problem right and that this posting helped.

---

### Post by newtonrealman on 2007-11-23
nop, that didnt work. Some more details that i forgot to mention:
when suspending... it suspends .. but when starting.. only a blackscreen is seen
when hibernating, it doesnt hibernate, but just a blackscreen with a blinking cursor appears in the upper left corner.
Help is needed plz!
Thanks

---

### Post by foytix on 2007-11-23
i'm having a similar problem with my sony desktop model PCV-RZ14G also with Nvidia Graphics.  I've tried the above there is even a a line refering to sony specfically tried that too with no luck.  still working on it though.

---

### Post by HydrantHunter on 2007-11-24
Don't know if this'll help, but found this in another thread:

".../etc/X11/xorg.conf and /etc/default/acpi-support matched the values shown, and all did already except for the line in xorg.conf: Option "NvAGP" "1"..."

Here's the thread: [Gutsy Suspend - does it work for anyone? (page 14)](http://ubuntuforums.org/showthread.php?t=588239&page=14)

Post is near the bottom of the page (post #134)

Also, len.ro has a list of the xorg.conf and acpi-support settings for getting suspend (but not hibernate) working on a notebook (Dell Latitude) with an nVidia video chip.
[Install Gutsy...](http://www.len.ro/work/tools/ubuntu-gutsy-on-a-dell-latitude-d820/install-gutsy/view)

Good luck :)

---

### Post by foytix on 2007-11-25
I must have typed something wrong before in the file /etc/default/acpi-support, this took care of the problem for me along with uncommenting the line mentioning the sony.

now if i could just get it to wake up using the keyboard or mouse like it used to do.

---

### Post by mempman on 2008-01-02
Thanks a lot!

> **scorp123 said:**
> What do you mean by "I cannot recover" .... ?  Does the screen stay black?

My suspicion is that the problem is here in this file: **/etc/default/acpi-support** ... Please make sure the following parameters are set: ```
ACPI_SLEEP=true
ACPI_HIBERNATE=true
ACPI_SLEEP_MODE=mem
MODULES=""
**[COLOR="Red"]MODULES_WHITELIST="nvidia"[/COLOR]**
SAVE_VBE_STATE=false
VBESTATE=/var/lib/acpi-support/vbestate
**[COLOR="Red"]POST_VIDEO=false[/COLOR]**
[COLOR="Red"]**SAVE_VIDEO_PCI_STATE=true**[/COLOR]
USE_DPMS=false
[COLOR="Red"]HIBERNATE_MODE=platform[/COLOR]
LOCK_SCREEN=true
STOP_SERVICES="mysql "
RESTART_IRDA=false
ENABLE_LAPTOP_MODE=false
```

These parameters helped on one of my systems which too has an Nvidia card.

The problem seems to be that when Ubuntu goes into "sleep" it will unload the "nvidia" kernel module but then fail to reload it again when the system resumes. Result: black screen, you don't see anything and have no choice but a hard reset (at least that was the problem in my case).

So I hope I interpreted your problem right and that this posting helped.

---

