---
title: "OS randomically doesn't start at boot"
date: 2021-10-25
forum: Hardware
---

### Post by pad-0001 on 2021-10-25
Hi All.
I notice that sometimes (9 times out of 10), when i turn on or restart my PC, my boot blocking on "Gigabyte" logo previous the boot.

My HW information is follow, tell me if you need more details:
[COLOR=#000000]Motherboard:[/COLOR]
[COLOR=#000000]Gigabyte Tech. Co.[/COLOR]
[COLOR=#000000]970A-DS3P[/COLOR]
[COLOR=#000000]Bios:[/COLOR]
[COLOR=#000000]American Megatrends Inc.[/COLOR]
[COLOR=#000000]F1[/COLOR]
[COLOR=#000000]04/08/2013[/COLOR]

Thanks, Pietro

---

### Post by TheFu on 2021-10-25
Which OS and which release of that OS?

Do you have multiple HDDs/SSDs connected?

If you run the boot-info script, someone might be able to see conflicts. I think the Boot Repair tool has a "Gather Information" button that will generate a URL with data. Share that URL here.

There is also a new system information script that could be helpful, but the boot-info will help more.

A failing HDD can refuse to boot all the time.  Any SMART data showing HDD issues? If you boot from flash USB storage into a *Try Ubuntu* environment, do that always work?  Please attempt to isolate the issue between different parts of the hardware.

And lastly, could the issue be that the CMOS battery is dead?  $2 replacement can solve all sorts of odd issues.

---

### Post by pad-0001 on 2021-10-26
For now i have only one SSD connected. The info that you shared me has useful!
I downloaded the bootInfoScript and execute that in my server. I notice some errors but i can't understand them, I'll send you the output file.
I also tell you that my OS is Ubuntu Server 20.04.3, I doesn't know if there are SSD issue but i could think no and, to answere about boot from usb, I opened another topic for USB issue, then I can't try that now.

---

