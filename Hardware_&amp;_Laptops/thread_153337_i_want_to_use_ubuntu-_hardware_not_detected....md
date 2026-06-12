---
title: "i want to use ubuntu- hardware not detected..."
date: 2006-03-31
forum: Hardware &amp; Laptops
---

### Post by jpop12 on 2006-03-31
i have Breezy 5.10 installed on a new
amd 64 emachine. 
1 hard drive is running windows, 1 hard drive, ubuntu.
everything is great, except:

my usb ports and cd rom are not detected-
and, as far as i can tell, my ethernet card is not either.
i have researched these issues and have not been
able to resolve them.
i even have a copy of "beginning ubuntu linux"
from apress publishers; no answers there.

i really want ubuntu functional on this machine.
and to be connected to the internet.

any ideas would be greatly appreciated.

also- i have 5.10 installed on a 1999 imac.
everything is fully functional; but, the machine is intolerably slow.

---

### Post by ispmarin on 2006-03-31
Hello there! Just don't give up yet... ;) 
Try to do a 
lspic 
and post here what appears... let's see if your computer finds the hardware and is not properly configuring it, or it can't find the hardware at all...

---

### Post by æþeling on 2006-03-31
[QUOTE=ispmarin]Hello there! Just don't give up yet... ;) 
Try to do a 
lspic 
and post here what appears... let's see if your computer finds the hardware and is not properly configuring it, or it can't find the hardware at all...[/QUOTE]

acctually, that's "lspci", not "lspic".

---

### Post by mips on 2006-04-01
[QUOTE=jpop12]i have Breezy 5.10 installed on a new
amd 64 emachine. 
1 hard drive is running windows, 1 hard drive, ubuntu.
everything is great, except:

my usb ports and cd rom are not detected-
and, as far as i can tell, my ethernet card is not either.
i have researched these issues and have not been
able to resolve them.
i even have a copy of "beginning ubuntu linux"
from apress publishers; no answers there.

i really want ubuntu functional on this machine.
and to be connected to the internet.

any ideas would be greatly appreciated.

also- i have 5.10 installed on a 1999 imac.
everything is fully functional; but, the machine is intolerably slow.[/QUOTE]


Hmm, maybe it would help if you give us more information ?!?!

Brand & Model of pc or of the motherboard if you built your own.

The more info you give the more likely you are to be helped.

Post output of **lspci -v** here

---

### Post by jpop12 on 2006-04-01
thanks for the replies.

system info:
AMD Athlon&#8482; 64 3400+
2.20GHz
NVIDIA® nForce® 410
1GB DDR
NVIDIA® GeForce® 6100 GPU
10/100Mbps integrated Ethernet LAN (RJ-45 port)

i do not know how to transfer lspci and lspci -v
information from the ubuntu system to my windows system-
since the usb ports/ethernet are not working.
(no thumb drive or internet.)

nutshell of returned lspci / lspci -v info:
(all these are "unknown")
ram memory / pci bridge / isa bridge / usb controller
ide interface / communication controller / smbus

thanks.

---

### Post by ispmarin on 2006-04-03
Sorry about the typo... well, information about it would help... what is the type of the windows partition: if it is fat32, you can try to write the information on the partition and then put it in here...

---

### Post by mips on 2006-04-03
We still do not know the **Brand & Model of the PC or motherboard**. If you tell us this maybe we can determine what hardware you have.

As ispmarin suggested you can write to a FAT32 partition if you are dual-booting to copy the info over or you can try and write to a stiffy drive. If you dont have a FAT32 partition maybe resize your Windows NTFS partition so you can fit a small 10MB or so FAT32 partition in, this is assuming you are using NTFS.

If we cant get the info we are just going to go in circles here...

---

