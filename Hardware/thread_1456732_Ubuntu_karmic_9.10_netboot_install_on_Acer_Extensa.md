---
title: "Ubuntu karmic 9.10 netboot install on Acer Extensa 5635G"
date: 2010-04-17
forum: Hardware
---

### Post by zazuge on 2010-04-17
if you want to install Ubuntu via netboot you will be shown the message
"no network interface detected" 
the problem is that the Atheros driver is not included in the CD 
the good news is that any updated ubuntu 9.10 version on any other machine
have the said driver
i tried this with the alternate CD installation 
copy the file atl1c.ko to your flash
/lib/modules/2.6.31-20-generic/kernel/drivers/net/atl1c/atl1c.ko 
and the to your laptop
use:

insmod atl1c.ko

if that doesn't work
try:

mkdir /lib/modules/2.6.31-20-generic/kernel/drivers/net/atl1c/

and then:

cp atl1c.ko /lib/modules/2.6.31-20-generic/kernel/drivers/net/atl1c/

retry "detect network device"

good-luck!
I hope you won't wast a day trying to figure that out like i did ^^
if you have some others problem try acpi=off in the kernel argument
(use tab on the install menu to edit kernel arguments)

---

