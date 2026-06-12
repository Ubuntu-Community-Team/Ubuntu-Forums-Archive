---
title: "Suggestions on RAM Upgrade"
date: 2010-06-15
forum: Hardware
---

### Post by rathin.saran on 2010-06-15
Hi Guys,

I would like to upgrade my computer's RAM from 512 MB to 1.5 GB. The following are my current RAM specifications :

DIMM1 Memory Module Properties:  
   Module Name      Samsung M3 78T6553EZS-CE6  
   Serial Number    77230673h  
   Module Size      512 MB (1 rank, 4 banks)  
   Module Type      Unbuffered  
   Memory Type      DDR2 SDRAM  
   Memory Speed     DDR2-667 (333 MHz)  
   Module Width     64 bit  
   Module Voltage   SSTL 1.8  
   Error Detection  Method   None  
   Refresh Rate     Reduced (7.8 us), Self-Refresh  
   
  Memory Timings:  
   @ 333 MHz        5.0-5-5-15 (CL-RCD-RP-RAS)  
   @ 266 MHz        4.0-4-4-12 (CL-RCD-RP-RAS)  
   @ 200 MHz        3.0-3-3-9 (CL-RCD-RP-RAS)  
   
  Memory Module Features:  
   Early RAS# Precharge              Supported  
   Auto-Precharge                    Supported  
   Precharge All                     Supported  
   Write1/Read Burst                 Not Supported  
   Buffered Address/Control Inputs   Not Supported  
   Registered Address/Control Inputs Not Supported  
   On-Card PLL (Clock)               Not Supported  
   Buffered DQMB Inputs              Not Supported  
   Registered DQMB Inputs            Not Supported  
   Differential Clock Input          Not Supported  
   Redundant Row Address             Not Supported  

BTW I have 800 MHz Frontside Bus. My computer can support a maximum of 2 GB of RAM.

I would like to buy RAM from Kingston. How can I determine if it is compatible with the existing one from Samsung? Can I judge it's compatibility by looking at its label in some way?

Thanks in advance for all your suggestions ..

---

### Post by cascade9 on 2010-06-15
I've never heard of there being any problems mixing different brand DDR2 RAM sticks. Not saying that it never happens, but its very rare if it does. 

A few other things to think about-

Almost all newer computers with DDR2 use can dual-channel RAM. It wont make your RAM twice as fast, but it does give some benefits. If you have an odd number of RAM sticks, it will only run in single channel mode. 

800Mhz front side bus will get some benefit from using DDR2 800. 

512MB sticks arent that much cheaper than 1GB sticks (this could vary country to country, but most western countries the different is only a few dollars). 

You might be better of getting 2 x 1GB sticks of DDR2 800, and just removing the single 512MB stick you currently run. 

If you post the 'core' output from "sudo lshw" then I can tell if you have a dual channel RAM capablechipset, if it will take 1GB sticks (almost certain it will), etc. BTW, you wontneed to post the whole output ;) 

Here is what my 'core' from lshw gives me- 

```
*-core
       description: Motherboard
       product: MS-7388
       vendor: MICRO-STAR INTERNATIONAL CO.,LTD
       physical id: 0
       version: 1.0
       serial: To be filled by O.E.M.
       slot: To Be Filled By O.E.M.

```

---

### Post by rathin.saran on 2010-06-16
Thank you so much for the reply,mate! I seem to have a dual channel capable chipset. Mine is a Windows Xp Box ( I'm a LINUX noob and run it on a virtual machine ) , so, I guess the lshw command is not available. This is what my diagnosis program tells me :

[ North Bridge: Intel Lakeport-G i945G ]

    North Bridge Properties:
      North Bridge.................Intel Lakeport-G i945G
      Revision / Stepping..........02 / A2
      Package Type.................1202 Pin FC-BGA
      Package Size.................3.4 cm x 3.4 cm
      Core Voltage.................1.5 V
      In-Order Queue Depth.........12

    Memory Controller:
      Type.........................Dual Channel  (128-bit)
      Active Mode..................Single Channel  (64-bit)

    CPUID Properties:
      Socket.......................478
      CPU Serial Number............Unknown


BTW, for the time being I can not afford more than one 1 GB stick ( I would buy another 1 GB within the next two months, though ). So, am I going to be fine with { <the existing 512 MB DDR2 667> + <the new 1 GB DDR2 800> } ?

---

### Post by cascade9 on 2010-06-16
No problems ;) 

You should be fine with 1 stick DDR2 667 (512MB) and 1 stick DDR2 800 (1GB). 

In the unlikely event that you do have issues, you can always just remove the 512MB stick, but I really, really, Really doubt that will happen.

---

### Post by uOpt on 2010-06-16
Of course you will not run dual-channel this way.

Some boards run single sticks but refuse to do single-channel with two sticks (if the board has only two slots).

It would be more useful to post what board you have, not what RAM you have.

---

### Post by rathin.saran on 2010-06-17
Yeah man! I would have to bear with single channel for about two months. Some excerpts from my motherboard spec are as follows:

Motherboard Properties:
      Motherboard ID____________________HPQOEM Lakeport

    Front Side Bus Properties:
      Bus Type_________________________Intel NetBurst
      Bus Width________________________64-bit
      Real Clock________________________200 MHz (QDR)
      Effective Clock____________________800 MHz
      Bandwidth________________________6400 MB/s

    Memory Bus Properties:
      Bus Type_________________________DDR2 SDRAM
      Bus Width________________________64-bit
      Real Clock________________________333 MHz (DDR)
      Effective Clock____________________667 MHz
      Bandwidth________________________5333 MB/s

    Chipset Bus Properties:
      Bus Type_________________________Intel Direct Media Interface

Please tell me if you guys need some other info related to the motherboard.

---

### Post by cascade9 on 2010-06-17
'Lakeport' = Intel 945/946/955 chipsets. 

[http://ark.intel.com/ProductCollection.aspx?codeName=2674](http://ark.intel.com/ProductCollection.aspx?codeName=2674)

There are lots of motehrboards using that chipset, its more than possibel that you migth get the issue that uOpt posted.....but without the exact model motehrboard, its hard to know. I doubt you will have any issues with running 1x1GB and 1x512MB sticks, but like I said, if there is an issue, just remove the 512MB stick. 

BTW, those intel chipsets only support DDR2 @ 667 AFAIK. (DDR2 800 orfaster should still work fine, just it wont run at full speed)

---

### Post by rathin.saran on 2010-06-18
Motherboard model = Lakeport 945GC

??? FSB Frequency = 800/533 MHz???
>>Supports DDR2 400, DDR2 533, and DDR2 667 


Is it going to refuse to do single channel with two sticks?



 I also downloaded the documentation from the link posted by cascade9(Thanks!!!). It defines the rules for populating DIMM slots as follows:

>>In all modes, the frequency of system memory will be the lowest frequency of all DIMMs in the system, as determined through the SPD registers on the DIMMs. 

>>In the single channel mode, any DIMM slot within the channel may be populated in any order. Either channel may be used. To save power, do not populate the unused channel. 

>>In dual channel asymmetric mode, any DIMM slot may be populated in any order. 

>>In dual channel interleaved mode, any DIMM slot may be populated in any order, but the total memory in each channel must be the same.


I also visited crucial.com and entered my computer model 
(Compaq Presario SG3140IL). 

They gave me the following specs:
Product Code - CT877990

1GB, 240-pin DIMM, DDR2 PC2-5300 memory module

    * Module Size: 1GB
    * Package: 240-pin DIMM
    * Feature: DDR2 PC2-5300
    * Specs: DDR2 PC2-5300 &#8226; CL=5 &#8226; Unbuffered &#8226; NON-ECC &#8226; DDR2-667 &#8226; 1.8V &#8226; 128Meg x 64

---

### Post by cascade9 on 2010-06-19
> **rathin.saran said:**
> Is it going to refuse to do single channel with two sticks?

It should be fine, but honestly....its impossible to tell without trying it.

---

### Post by uOpt on 2010-06-19
At the least we need to know which board specifically this is.

The ability to do this is in the BIOS, not the chipset.

---

### Post by cascade9 on 2010-06-19
Its a ECS 945GCT-HM (which ECS made for compaq). I've found its very hard, if not impossible, to find out to 100% accuracy anyway. 

Things sometimes work fine with some types of RAM, but not with others. EG- 1x512MB samsung + 1x 1GB a-data, fine. 1x 512MB adata + 1 x 1GB winbond, no go. 

I'll stick with 'no way of knowing for sure without trying it'.

---

### Post by rathin.saran on 2010-06-23
NEW PROBLEM
Thank U so very much cascade9 & uOpt!! My RAM upgrade is almost a success!!

But whenever I boot up my pc I get a screen which shows all my hardware info (plus 1.5 GB of RAM) and when the operating system loads up the system time is shown as 12:00 AM and date as September 3, 2007. It is happening every time I am booting up the PC.

Am I doing something wrong??

---

### Post by rathin.saran on 2010-06-24
PROBLEM SOLVED - cascade9 & uOpt - MANY MANY THANKS!!

I took out the CMOS Battery and wiped it with a piece of cloth and put it back on its place. I did a reboot. It reset the BIOS once.

Rebooted again and VOILA!

No more checksum issue messages!

---

### Post by cascade9 on 2010-06-25
Excelent, the RAM worked, and you fixed your CMOS problem ;) 

Enjoy ;)

---

