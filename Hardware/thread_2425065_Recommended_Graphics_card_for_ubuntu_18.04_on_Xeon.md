---
title: "Recommended Graphics card for ubuntu 18.04 on Xeon Server Board"
date: 2019-08-20
forum: Hardware
---

### Post by durairajkumar on 2019-08-20
I have below  Server Board with Basic  integrated Video card which I see is not good for Ubuntu Genome desktop. CLI is good but the Video quality should be good enough for basic web brwosing on ubuntu genome desktop 


Base Board Information:
        Manufacturer: Intel Corporation
        Product Name: S1200SP
        Version: H57533-270


Processor information: 


product: Intel(R) Xeon(R) CPU E3-1220 v6 @ 3.00GHz
          vendor: Intel Corp.
           size: 899MHz
          capacity: 3500MHz


Memory information:


Memory Device
        Size: 16384 MB
        Manufacturer: Kingston
        Type: DDR4
        Form Factor: DIMM
		
		
Inbuilt VGA but its not good for Video 	


 *-display UNCLAIMED
                description: VGA compatible controller
                product: MGA G200e [Pilot] ServerEngines (SEP1)
                vendor: Matrox Electronics Systems Ltd.
      

Thank you in advance 

regards
Durai

---

### Post by durairajkumar on 2019-08-20
I found this below URL which is helpful. Will look into the list but let me know if anyone has suggestion in the mean time 

[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsNvidia](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsNvidia)


Thank you 

Regards
Durai

---

### Post by TheFu on 2019-08-20
Servers don't have GUIs.  Use ssh to manage it.

That link is showing cards that almost all won't be supported by nvidia drivers today with the current kernels.  
 [https://www.nvidia.com/en-us/drivers/unix/](https://www.nvidia.com/en-us/drivers/unix/) is where to begin if you prefer nvidia.  On LTS releases, nvidia and Canonical are working together to make installing the drivers easier. This just changed in the last month or so.

I don't know much about AMD GPUs.

---

### Post by cruzer001 on 2019-08-20
No need to overthink it either.  Cheap, used cards is the route I go.  My cards usually fall in the 20 to 50$US range.  Not a gamer so I don't need to spend the money on hi-tech.  Nvidia is my favored brand and geForce my first choice, but quadro is also a fine product.  These days video drivers offer wide support and I find it very hard to go wrong.

---

### Post by durairajkumar on 2019-08-21
Thank you for the reply. I see nvidia is predominately used/recommended. 

Closing this thread

---

### Post by TheFu on 2019-08-21
To actually close it, use "thread tools" button near the top.

---

