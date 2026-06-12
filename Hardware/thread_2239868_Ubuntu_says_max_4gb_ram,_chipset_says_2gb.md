---
title: "Ubuntu says max 4gb ram, chipset says 2gb"
date: 2014-08-16
forum: Hardware
---

### Post by Luis_Bozan on 2014-08-16
Hello again.
In my old Dell Inspiron 6000 I've managed to upgrade cpu to an astonishing 2,13 GHZ (came with 1,3). RAM is up to the maximum of 2Gb, from 512Mb. The old hdd 5400 rpm with 40Gb of storage is now an SSD SLC with 32Gb storage. It now boots in 30 seconds. Ubuntu 14.04 32 bits is installed and the computer will hopefully work til the kids move out. That would be a total of 20 years of service.
Now, surfing the web to find upgrades and hacks I've been learning about Ubuntu and Terminal (a little). One of my discoveries was that when I run the command to see specs and limits of the computer, Terminal says 4096Mb max of ram, but I know the chipset limitation is 2Gb. 

So which one is it? Is there a magical way that Ubuntu will support the 4Gb of ram? 

While installing the new out-of-the-box SSD I entered BIOS to run systemcheck and it sounded the alarm saying that it couldn't read the SSD. I turned the computer off and went ahead with my clean installation of Ubuntu, despite the alarm, and it worked like a charm (except that it won't read aucio cd, only the Temptations, but reads DVD).

Anyone with similar ram-issue? Or has solved a similar ram-issue?

---

### Post by weatherman2 on 2014-08-16
I had an Inspiron 6400 which is the successor to the 6000, and it too would only support 2GB of RAM. I am fairly sure this is a hard limitation of both laptops.  The manufacturer's specified maximum RAM isn't always correct, but in this case I think it is.

---

### Post by grahammechanical on 2014-08-16
The physical limits of the motherboard are one thing but the capabilities of the CPU to address memory are something else. A 32 bit CPU can address up to 4 GB of RAM and a 32 bit CPU with Physical Address Extensions (PAE) will be able to address more than 4 GB of RAM.

> I[COLOR=#252525][FONT=sans-serif]n non-PAE modes of [/FONT][/COLOR][x86]("http://en.wikipedia.org/wiki/X86")[COLOR=#252525][FONT=sans-serif] processors, the [/FONT][/COLOR][RAM]("http://en.wikipedia.org/wiki/RAM")[COLOR=#252525][FONT=sans-serif] is always limited to 4 GB.[/FONT][/COLOR]

> [COLOR=#252525][FONT=sans-serif]Limits on physical memory for 32-bit platforms also depend on the [Physical Address Extension]("http://en.wikipedia.org/wiki/Physical_Address_Extension") (PAE), which allows 32-bit systems to use more than 4 GB of physical memory.[/FONT][/COLOR]
[COLOR=#252525][FONT=sans-serif]PAE and 64-bit systems can address up to the full address space of the x86 processor.[/FONT][/COLOR]


[http://en.wikipedia.org/wiki/RAM_limit](http://en.wikipedia.org/wiki/RAM_limit)

Regards.

---

### Post by Luis_Bozan on 2014-08-17
So, when installing Ubuntu 14.04 it automatically detects wether to go for PAE or not (that's what it canonical says), which would, in theory, allow my laptop to use 4 gb ram eventhough the chipset (mobo) says 2 gb ram. Is this correct? Has anyone tried it with another laptop and can say that i actually works?

---

### Post by weatherman2 on 2014-08-17
No, that is not correct.  If your laptop's chipset has a hard limit of 2GB, there is no way to add more.

A PAE kernel allows a 32 bit CPU (or a 64 bit CPU running a 32 bit operating system) to access more than 4GB of RAM if the hardware itself can support it and has more RAM.  Your hardware does not support more RAM.

---

