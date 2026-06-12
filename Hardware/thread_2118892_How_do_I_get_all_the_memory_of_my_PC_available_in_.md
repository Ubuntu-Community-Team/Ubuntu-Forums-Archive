---
title: "How do I get all the memory of my PC available in Linux ?"
date: 2013-02-22
forum: Hardware
---

### Post by Bruno53 on 2013-02-22
With all 32bit Ubuntu or PXLinuxOS systems I installed on my PC came 4 GB of Memory .
When I upgraded the kernel to a pae version, I got 8 GB . The same amount I had wen I installed a 64bit Linux Mint or PCLOS ....
The question is :  my desktop has 16 GB of DDR3 RAM, which is also available in the preinstalled Windows 7 .
What does it take to have that 16 GB availbable in Linux systems ?
Thanks for enlightening me !


Technical specifications :

Lenovo Ideacentre B540P All-in-One PC 58,42 cm (23") 
**************************************************
    Operating system: Windows 7 Home Premium 64bits
    Processor: Intel® Core™ i7-3770 Processor (8M Cache, 3.90 GHz)  -  integrated Intel HD Graphics 4000
    Memory: 16Gb (4x4Gb) DDR3 1333MHz
    Memory Slot: 4
    Display: 23” Full HD (1920x1080), 16:9 widescreen frameless display 
    Graphics: NVIDIA® GeForce™ GT650M 2Gb
    Speakers: Integrated stereo speakers supporting Dolby Advanced Audio V2
    Integrated camera: Integrated Lenovo High-Sense (720p HD) webcam
    Hard drive: 2TB 7200rpm
    Wired Ethernet LAN: 10/100/1000M
    Wireless LAN: WiFi 802.11b/g/n
    Interfaces: Wireless USB Keyboard & Mouse, 4xUSB2.0, 2xUSB3.0 connectors,headphones, mic, HDMI out, 6in1 card reader, TV tuner
    Computer ( h x d x w): 57.6cm x 11cm x 41.19cm (22.7" x 4.34" x 16.22")
    Weight: 9.18kg

---

### Post by sanderj on 2013-02-22
What is the problem?

What is the output of:

```
free -h
uname -a

```
... can you post the output here?

EDIT: I'll plug my script on  [http://www.appelboor.com/dump/check-my-memory.py](http://www.appelboor.com/dump/check-my-memory.py) :


```
wget http://www.appelboor.com/dump/check-my-memory.py
python check-my-memory.py
sudo python check-my-memory.py
```

That will tell you all

EDIT 2: some explanation on [http://www.appelboor.com/dump/check-my-memory.html](http://www.appelboor.com/dump/check-my-memory.html)

HTH

---

### Post by TheFu on 2013-02-22
32-bit Ubuntu with PAE supports 64GB of RAM, if the hardware involved supports that too.
[http://askubuntu.com/questions/142043/whats-the-maximum-amount-of-ram-i-can-use-on-an-specific-hardware](http://askubuntu.com/questions/142043/whats-the-maximum-amount-of-ram-i-can-use-on-an-specific-hardware) says that some motherboard RAM controllers only support 8GB of RAM. Could that be the issue?

It may be that your specific BIOS is out of date too.

---

### Post by sanderj on 2013-02-24
... and ... nothing ...?

OP, it would be nice if you followed up to the info you got.

---

### Post by Bruno53 on 2013-02-24
Saturday been busy with non PC stuff ....

Results of Linux Mint 14  console  :

These results make it clear that Linux sees only the half of the 16 GB that is available in the preinstalled Windows 7 Home Premium ....
The BIOS version is 04/09/2012 , so does that already need updating ? 
Does someone see a solution ?


mouse mouse # free -h
             total       used       free     shared    buffers     cached
Mem:          7,8G       1,9G       5,9G         0B       320M       994M
-/+ buffers/cache:       626M       7,2G
Swap:         9,8G         0B       9,8G
mouse mouse # uname -a
Linux mouse 3.5.0-17-generic #28-Ubuntu SMP Tue Oct 9 19:31:23 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
mouse mouse # wget [http://www.appelboor.com/dump/check-my-memory.py](http://www.appelboor.com/dump/check-my-memory.py)
--2013-02-24 14:40:06--  [http://www.appelboor.com/dump/check-my-memory.py](http://www.appelboor.com/dump/check-my-memory.py)
Herleiden van [www.appelboor.com]("http://www.appelboor.com") ([www.appelboor.com]("http://www.appelboor.com"))... 176.31.156.230, 2001:41d0:2:bb58:dead:beef:8637:e45b
Verbinding maken met [www.appelboor.com]("http://www.appelboor.com") ([www.appelboor.com)|176.31.156.230|:80]("http://www.appelboor.com)|176.31.156.230|:80")... verbonden.
HTTP-verzoek is verzonden; wachten op antwoord... 200 OK
Lengte: 8804 (8,6K) [text/plain]
Wordt opgeslagen als: ‘check-my-memory.py’

100%[==========================================================================================================>] 8.804       --.-K/s   in 0,007s  

2013-02-24 14:40:08 (1,20 MB/s) - '‘check-my-memory.py’' opgeslagen [8804/8804]

mouse mouse # python check-my-memory.py
check-my-memory.py - version: SJ 2013-02-22
OK, you're root
ANALYSIS:
Total of physical memory modules found 8192 MB in 2 memory module(s)
BIOS offers 8151 MB as usable
Memory seen by OS 7949 MB
BIOS version 04/09/2012
CPU is PAE enabled
CPU is x86_64 64-bit enabled
OS is x86_64 64-bit

SUMMARY:
Memory difference between DIMM hardware and BIOS offering 41 MB
Memory difference between BIOS offering and memory seen by OS 202 MB
Memory difference between DIMM hardware and memory seen by OS 243 MB

ADVICE:
Nothong unusual found, so no advice for your setup                              
                                                                                     
Finally: show more detailed memory info from lshw. This can take up to 30 seconds ...      
       description: System Memory                                                                        
       size: 8GiB                                                                                        
          description: SODIMM DDR3 Synchronous 1600 MHz (0,6 ns) [empty]                                          
          description: SODIMM DDR3 Synchronous 1600 MHz (0,6 ns)                                                            
          size: 4GiB                                                                                                                      
          description: SODIMM DDR3 Synchronous 1600 MHz (0,6 ns) [empty]                                                                          
          description: SODIMM DDR3 Synchronous 1600 MHz (0,6 ns)
          size: 4GiB

Finished
mouse mouse # sudo python check-my-memory.py
check-my-memory.py - version: SJ 2013-02-22                                                                                                         
OK, you're root                                                                                                                                       
ANALYSIS:                                                                                                                                             
Total of physical memory modules found 8192 MB in 2 memory module(s)                                                                                   
BIOS offers 8151 MB as usable                                                                                                                          
Memory seen by OS 7949 MB                                                                                                                              
BIOS version 04/09/2012                                                                                                                                 
CPU is PAE enabled                                                                                                                                      
CPU is x86_64 64-bit enabled                                                                                                                            
OS is x86_64 64-bit                                                                                                                                      
                                                                                                                                                         
SUMMARY:                                                                                                                                                  
Memory difference between DIMM hardware and BIOS offering 41 MB                                                                                           
Memory difference between BIOS offering and memory seen by OS 202 MB                                                                                       
Memory difference between DIMM hardware and memory seen by OS 243 MB                                                                                        
                                                                                                                                                            
ADVICE:                                                                                                                                                     
Nothong unusual found, so no advice for your setup                                                                                                          
                                                                                                                                                             
Finally: show more detailed memory info from lshw. This can take up to 30 seconds ...
       description: System Memory
       size: 8GiB
          description: SODIMM DDR3 Synchronous 1600 MHz (0,6 ns) [empty]
          description: SODIMM DDR3 Synchronous 1600 MHz (0,6 ns)
          size: 4GiB
          description: SODIMM DDR3 Synchronous 1600 MHz (0,6 ns) [empty]
          description: SODIMM DDR3 Synchronous 1600 MHz (0,6 ns)
          size: 4GiB

Finished
mouse mouse #

---

### Post by sanderj on 2013-02-24
I think the technical info you posted in your opening post is from some website, isn't it?

If so, I trust

> ANALYSIS:
Total of physical memory modules found 8192 MB in 2 memory module(s)

more than that website info.

Easy check: boot into Windows, and see what Windows says about the memory that's available.

---

### Post by TheFu on 2013-02-24
> **sanderj said:**
> Easy check: boot into Windows, and see what Windows says about the memory that's available.

In the OP, he says that Windows sees all 16GB.
Since he is running a x64 Linux, all that RAM should be seen easily. To me, that means that either the RAM is going bad, he become unseated, the BIOS is not reporting the RAM or the hardware does not support more than 8GB.  If Windows really sees all 16GB of RAM, we know that the hardware, memory controller, seating are not at issue.

Please double-verify that Windows really sees the 16GB of RAM, but he probably does recall the correct number. I know that I would.

```
$ sudo lshw -C Memory
```
will show lots of details about the chips seen by Linux - cache, firmware, banks, sizes, totals.

I've never heard of anyone having this issue that wasn't traced back to a motherboard support issue AND both Windows and Linux reported the same amount of RAM.

---

### Post by Bruno53 on 2013-02-24
I am so so so so embarrassed !
Windows 7 mentions 8GB and so does the BIOS I just checked ...
I don't understand cause I bought this PC that supposedly had 16 gig .
Moreover :  I am certain I checked, when I just got this machine, whether it really had that memory , and according to Windows, at that time, it had .
I am pretty sure about this because a few months before, I had bought a Medion Laptop with 8GB, which on arrival had only 4 GB .
I sended the machine back under warranty and got it after a few weeks with 8GB and the info that there had been a loose contact .
As a result I checked, later with the Lenovo, whether the memory in this PC was allright, therefore I was certain it was . 
The only other explanation is that I have gone mad !
I am going to search further into this ( the bill etc. ) , tomorrow , so I will leave this post open for the time being ....

---

### Post by TheFu on 2013-02-24
We've all done similar things.  No worries, mate.

If all the memory slots are full, pull the chips and reseat them. Sometimes that will make everything work again.

---

### Post by sanderj on 2013-02-24
> **Bruno53 said:**
> I am so so so so embarrassed !
Windows 7 mentions 8GB and so does the BIOS I just checked ...


No problem. And you now know why they say "meten is weten, gissen is missen". ;-)

---

### Post by Gyokuro on 2013-02-24
In your specs it is stated 16GB with 4 RAM slots (4x4GB) and the posted python script discovered 8GB (2x4 GB in two slots) and Windows/BIOS shows the same memory amount as you have only 8GB. Maybe you can return your hardware and tell them that you have ordered it with 16GB or buy additional 2x4GB sticks (buy Lenovo's recommended memory sticks) and you should have 16GB in four memory slots.

---

### Post by Yellow Pasque on 2013-02-25
Caveat emptor...

---

### Post by Bruno53 on 2013-02-25
Today I've found the box that contained my PC, with all the info about it, and it mentions 16 Gb DDR Ram .
The mail invoice gave me the Part Number of the machine, which by googling it, confirms the tech specifications, again 16 Gb .
So I was right about the first check, when I got the computer, and Windows confirming that 16 gig .
As I am not checking this memory every day to see whether it has changed, I assumed a software error when Linux gave me 8 in stead of 16 ...
Now that I know it's a hardware thing, I have to decide what to do, the PC is 4 months old and under warranty .
The downside is I bought it in a Web Store in another country, so I will have to send it back probably, that is what I will have to find out first ....
I could also take the memory out and put it back in, but if that doesn't help ( or worsen it ) , then maybe I've lost my warranty by opening that thing .
Or I can just let it be ..... 
Whatever my decision, this post can now be closed I guess . 
Thanks at those people who gave me helpfull info, if you still have an advice to spare, go ahead, I will wait to end this topic untill tomorrow .
En ja Sander, dat had ik ook al door, hoor !

---

### Post by sanderj on 2013-02-25
> **Bruno53 said:**
> Today I've found the box that contained my PC, with all the info about it, and it mentions 16 Gb DDR Ram .
The mail invoice gave me the Part Number of the machine, which by googling it, confirms the tech specifications, again 16 Gb .
So I was right about the first check, when I got the computer, and Windows confirming that 16 gig .
As I am not checking this memory every day to see whether it has changed, I assumed a software error when Linux gave me 8 in stead of 16 ...
Now that I know it's a hardware thing, I have to decide what to do, the PC is 4 months old and under warranty .
The downside is I bought it in a Web Store in another country, so I will have to send it back probably, that is what I will have to find out first ....
I could also take the memory out and put it back in, but if that doesn't help ( or worsen it ) , then maybe I've lost my warranty by opening that thing .
Or I can just let it be ..... 
Whatever my decision, this post can now be closed I guess . 
Thanks at those people who gave me helpfull info, if you still have an advice to spare, go ahead, I will wait to end this topic untill tomorrow .
En ja Sander, dat had ik ook al door, hoor !

First check: open your computer, and count the number of RAM modules: 2 or 4. 
Oh, and count the number of available RAM module locations.

If 2 modules are there (like Linux reports), and there are no modules available, you 100% know your supplier is wrong, as he says he would deliver 4 modules (of 4GB).

---

### Post by sanderj on 2013-02-25
On [http://www.lenovo.com/products/us/desktop/ideacentre/b-series/b540p/IdeaCentre-B540p-Datasheet.pdf](http://www.lenovo.com/products/us/desktop/ideacentre/b-series/b540p/IdeaCentre-B540p-Datasheet.pdf) (PDF alert) it says:

MEMORY
Up to 16GB DDR3 memory &#8211; 1600 MHz
[2 SODIMM slots ( 1x2GB/1x4GB/2x2GB/
1x2GB+1x4GB/2x4GB/ 4x4GB)


I would interpret "2 SODIMM slots" as two slots, but then I don't understand the "4x4GB".

So: open up your system and check the number of slots.

EDIT:

Wait, do not open your system: first call / mail the supplier, explain the situation and ask what to do.

---

