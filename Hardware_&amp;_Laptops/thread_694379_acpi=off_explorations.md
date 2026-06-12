---
title: "acpi=off explorations"
date: 2008-02-12
forum: Hardware &amp; Laptops
---

### Post by Neovos on 2008-02-12
Since boot issues with "acpi=off" as a workaround is a ridiculously common thing (myself included) I wanted to point out a way to finesse acpi a little more. I wanted to also sort of compile a few things I just realized are a common line of thinking regarding acpi problems:

First off, my particular problem was that my computer wouldn't boot normally and was giving me a sort of "ata xfermode" error. So first I tried the boot option "irqpoll" which got it up and running after a very long time but killed HAL once GDM started up and everything was a mess. 

So then I tried "acpi=off" and it worked again and brought up everything, but I lost use of my hyperthreading and the whole mess of stuff that acpi does for me. So I found this page here:

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

and put the two solutions together and tried the "acpi_irq_balance" option and viola! Booted with no problem. So my conclusion is that the common source of acpi problems (where disabling it altogether works somewhat as a work around) is probably linked to an irq conflict of sorts. I also found this page here (the last post):

[http://ubuntuforums.org/showthread.php?t=651872](http://ubuntuforums.org/showthread.php?t=651872)

where manually adjusting the SATA ports to the highest numbers on the actual motherboard fixes the conflict. That implies an irq conflict (because switching which SATA cable is connected to which port does manually change the irq orders and the interrupts). I think this is also implicit in cases where USB ports crash or don't work and then start to upon use of "acpi=off" like here:

[http://ubuntuforums.org/showthread.php?p=4314428](http://ubuntuforums.org/showthread.php?p=4314428)

Again that very likely could be an irq conflict between the USB ports and either acpi or some device it's controlling. 

So I just wanted to point out my findings I made while fixing this problem for myself. I hope that maybe this line of thinking could help people with similar problems or help with bug fixes.

---

