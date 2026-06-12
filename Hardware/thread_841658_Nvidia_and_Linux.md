---
title: "Nvidia and Linux"
date: 2008-06-26
forum: Hardware
---

### Post by TechPlusPC on 2008-06-26
Hey guys,

Question about Nvidia, drivers, FLV files and such.... Here is goes:

The FLV file is played through a proprietary media player that was custom made using flash 9 and an XML playlist only be able to be used by Fire Fox 2.0.0.14 or better. The problem is that the hardware has to be more COST EFFECTIVE than anything, thats the issue. I'm trying to get P4 performance out of a VIA C7 cpu running at 1.5GHz and a CX700 VIA chipset using ubuntu 8.04LTS.

Here are the machine specs:

CUSTOM MADE IN TAIWAN:

PROPRIETARY CASE
OFF BAND CUSTOM VIA BOARD
VIA CX700 N and S BRIDGE CHIPSET
INTEGRATED VIA C7 CPU RUNNING @ 1.5GHZ
1GB OF TRANSCEND DDR2 3200 RAM
OFF BRAND NVIDIA GEFORCE FX 5200 128MB PCI-EXPRESS CARD INSERTED INTO A 32BIT PCI ADAPTER THAT GOES INTO A 32PCI PORT ON BOARD
80GB INTERNAL 5200RPM 2.5" LAPTOP HARD DRIVE
UNBUNTU LINUX 8.04LTS

We had the exact same configuration but an onboard graphic card that was a VIA unichrome pro 2 IGP 64MB shared. Ironically even with that huge graphic card change the video is still choppy and slow. Its a bit better with the Nvidia card but not a lot.

To better understand what this is:

A programmer using several languages such as PHP, FLASH 9, and XML has made a PROPRIETARY PLAYER. This player is the only thing we can use to accomplish what needs to get done. Flash 9 and firefox 2.0.0.14 or better need to be installed in order to run. Using the internet in a variety of ways the ads download VIA an XML script into a custom playlist that is then called by his flash 9 payer to be displayed. The ads will run at standard definition with a resolution of 1024x768 on a 42" Vizio LCD. The box will run 24x7. There isn't much we can do. The video Rez was brought down, a different codes was used to compress but keep the quality standard. Down from 12-20MB a file to 3-5MB, the processor has went up from the original 800mhz to 1.5ghz, the memory has doubled from 512MB to 1GB and the O/S has been changed from puppy linux to Ubuntu 8.04LTS and the original FLASH drives of 2GB were changed to the now 5200RPM 2.5" laptop 80GB hard drives. This new change of almost doubled up on the hardware has interacted with the onboard 64MB Unichrome VIA IGP 2 to this new 128MB dedicated PCI FX 5200 Nvidia, and even with the dedicated I get about 15% better results than the onboard card. The drivers installed for the onboard card came right from VIA and were installed properly on unbuntu and the Nvidia drivers were downloaded and installed VIA Unbuntu's hardware manager as with the Xsever the drivers off nvidia's website is difficult to install. The drivers in
the manager do say that they are the most recent.

After all this B/S do you think that the processor and chipset combo is just too weak or is it that Linux cant just support this operation. Because on Windows XP I had much better results with the integrated graphic card than I did with the dedicated card on Unbuntu.
Any help would be much appreciated thank-you guys,

-Louis

---

### Post by sdennie on 2008-06-26
This is a problem with adobe flash.  Adobe doesn't provide very good linux support so flash is always problematic for linux.  There is a way to enable flash hardware acceleration but, I'm not sure if it actually does anything at the moment.  You could also try to install Flash 10 and see if it works any better.

---

