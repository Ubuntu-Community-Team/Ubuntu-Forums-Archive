---
title: "1066 MHz Memory running at 800 Mhz"
date: 2011-04-29
forum: Hardware
---

### Post by pokkie on 2011-04-29
Hi,

I recently decided to add additional memory to my desktop. I wanted to check my current memory configuration so I ran the following command :

```

$ sudo dmidecode --type 17
Handle 0x001A, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x0019
	Error Information Handle: Not Provided
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 2048 MB
	Form Factor: DIMM
	Set: None
	Locator: A0
	Bank Locator: Bank0/1
	Type: Unknown
	Type Detail: None
	**[COLOR="Red"]Speed: 800 MHz (1.2 ns)[/COLOR]**
	Manufacturer:  
	Serial Number:  
	Asset Tag:  
	Part Number:  

```

So, I rebooted, checked the BIOS and it reports that my memory is running at **1066 MHz**

Then, I decided to boot into Windows, run cpu-z, and it also reported my memory as running at **1066 MHz**

I rebooted again and ran memtest86+, also **1066 MHz**

However, as soon as I boot into Ubuntu, and ran the command above, it reports it at **[COLOR="Red"]800 MHz[/COLOR]**.

I thought it might be related to the fact that I am on a PAE-kernel, but I couldn't find anything to suggest that that might be the issue.

I am currently on 10.04 with Kernel 2.6.32-30-generic-pae #59-Ubuntu SMP Tue Mar 1 23:01:33 UTC 2011 i686 GNU/Linux


Anybody have any ideas?

Regards,
--pokkie

---

