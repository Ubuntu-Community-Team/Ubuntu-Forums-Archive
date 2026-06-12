---
title: "VAIO C1vn C1Vp"
date: 2008-12-29
forum: Hardware
---

### Post by sieger007 on 2008-12-29
I have a picture book vaio C1vp . 
8" portable PDA/Laptop Cross that takes W2K 2000 or Linux . It comes without a CD ROM.  
From the literature out there I read that only a Sony PCMCIA CD ROM can be used to install a new OS or you can take out the HDD and transplant it to another PC and get it to work.
I decided to give the 2nd thing a try. Got it out . Hooked it up to another external enclosure. Now I have another VERY SAME model picturebook where the OS is installed and works fine.
So This is what I did so far .
I installed the program  called "Self Image"  that images  1 HDD  and directly wrote the HDD image from working laptop to the USB HDD ( that is the HD of the non working vaio ) 
So the OS contents of the working Vaio were transferred to the non working vaio's hdd.
In spite of that it gives me error "Operating system not found".
I looked up one plausible cause - there is no MBR of course in the non working vaio's hdd.
So I logged into the recovery console of the working VAIO and fixmbr fixboot for the non working vaio's hdd..
Still the same problem- "Operating system not found".
I used this program called MBRFIX that can write a new MBR to a USB HDD.
Still the same problem- "Operating system not found".

Is there any Way I can write a valid MBR via GRUB or lilo and have them boot my windows OS in the non working vaio's hdd.

The only other alternative with the futility of this approach would be go buy the special PCMCIA CD ROM for sony and use that approach.
Any Idead
Wish you ALL A  VERY HAPPY NEW YEAR !!!

---

