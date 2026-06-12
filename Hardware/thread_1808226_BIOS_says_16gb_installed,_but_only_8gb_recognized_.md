---
title: "BIOS says 16gb installed, but only 8gb recognized by Ubuntu"
date: 2011-07-20
forum: Hardware
---

### Post by zephyr707 on 2011-07-20
Hello,

I have been running with 8gb of RAM in my laptop with 64-bit ubuntu for several months (4gb + 2x2gb).   Today I filled all 4 banks with 4gb sticks, but free, dmesg, etc all say that I only have 8gb of RAM, but the BIOS confirms that I have 16gb installed.  During my search for information I noticed some people saying that there machines had an option in the BIOS to enable the motherboard to "hide" the extra memory until the OS needed it.   My laptop has no such options, not much is configurable in there.

Something else I noticed was that lshw says that the banks are empty:

```

     *-memory
          description: System Memory
          physical id: 25
          slot: System board or motherboard
          size: 8GiB
        *-bank:0
             description: SODIMM Synchronous 1333 MHz (0.8 ns)
             product: F3-10666CL9-4GBSQ
             vendor: 04CD
             physical id: 0
             serial: 00000000
             slot: DIMM0
             size: 4GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:1
             description: SODIMM Synchronous 1333 MHz (0.8 ns)
             product: F3-10666CL9-4GBSQ
             vendor: 04CD
             physical id: 1
             serial: 00000000
             slot: DIMM1
             size: 4GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:2
             description: SODIMM Synchronous 1333 MHz (0.8 ns) [empty]
             product: F3-10666CL9-4GBSQ
             vendor: 04CD
             physical id: 2
             serial: 00000000
             slot: DIMM2
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:3
             description: SODIMM Synchronous 1333 MHz (0.8 ns) [empty]
             product: F3-10666CL9-4GBSQ
             vendor: 04CD
             physical id: 3
             serial: 00000000
             slot: DIMM3
             width: 64 bits
             clock: 1333MHz (0.8ns)

```I haven't been able to find a solution to my laptop recognizing this extra 8gb, most of the searches turn up threads about only 3gb being recognized in 32bit systems.  I definitely have a 64bit kernel:

uname -a
Linux thomas 2.6.35-30-generic #54-Ubuntu SMP Tue Jun 7 18:41:54 UTC 2011 x86_64 GNU/Linux

My bios definitely says that there is 16gb installed in the machine and I have used 3 of the 4 slots with my previous setup, but now it seems to be only using 2 of the slots.  I will try searching to see if I have the latest BIOS, but I was wondering if anyone has any experience dealing with such an issue.

thanks for any help!
z

---

### Post by realzippy on 2011-07-20
...memory allocated to the integrated/onboard graphics chip ?

---

### Post by zephyr707 on 2011-07-20
> **realzippy said:**
> ...memory allocated to the integrated/onboard graphics chip ?

don't think so, since I believe the number that is coming up in free is the same as when I had 8gb of RAM installed.  Also, I don't have integrated/on-board graphics.  If it helps, I have an asus g51jx-x3 laptop that I got off of craigslist, has worked very well, but I'm at a loss on this one.

thanks for your reply,
z

---

### Post by realzippy on 2011-07-20
[http://www.offtek.de/ModelData.php?stid=1&manu=Asus&modeltype=G50+Notebook+Series&model=G51Jx&source=Google_AsusG51Jx&gclid=CKiurdjlj6oCFQQYzQod_gEuzQ](http://www.offtek.de/ModelData.php?stid=1&manu=Asus&modeltype=G50+Notebook+Series&model=G51Jx&source=Google_AsusG51Jx&gclid=CKiurdjlj6oCFQQYzQod_gEuzQ)

link is in German,but it says that 8GB is maximum for your laptop.

..also here:
[http://compreviews.about.com/od/PC-Gaming/fr/ASUS-G51JX-X3.htm](http://compreviews.about.com/od/PC-Gaming/fr/ASUS-G51JX-X3.htm)  :

[I]Description

    * Intel Core i5-430M Dual Core Processor
    * 4GB DDR3 1066MHz RAM, 2 SODIMM Slots (**8GB Max**)
    * 500GB 7200RPM Hard Drive
    * Super Multi Optical Disk Drive
    * 15.6-Inch 1920x1080 LED LCD Display
    * NVIDIA GTS 360M Graphics With 1GB GDDR5
    * Gigabit Ethernet, 802.11 b/g/n
    * 14.8" x 10.4" x 1.6" @ 7.3 Pounds
    * Windows 7 Home Premium[/I]

---

### Post by zephyr707 on 2011-07-20
hi there,
thanks for your reply.  I looked at the specs and they didn't sound right (I have 4 so-dimm slots), so I did a little more research.  Turns out I have the i7 g51jx-x2 with a g60jx motherboard and I'm not the only one with this problem:

[http://blog.aktivematrix.com/blog/2011/05/30/open-letter-to-asus/](http://blog.aktivematrix.com/blog/2011/05/30/open-letter-to-asus/)

how unfortunate!  I wonder if a BIOS update will work.  Seems crazy that it has 4 slots and the bios recognizes all 16gb, but it refuses to report it to the OS.

suck city, i'll try contacting asus to see if they have a solution,
thanks
z

---

### Post by zephyr707 on 2011-07-29
I called up ASUS after receiving no reply to my enquiry.  They were very helpful until I told them I was running Linux...  Apparently it is a quick fix in windows 7: changing some RAM setting in msconfig to recognize all of the available RAM.  Sounded like removing a governor in a car or something.

I am downloading an opensuse 64-bit livecd to see if that recognizes all 16gb of the RAM and if not I will try their fix by reinstalling the windows 7 o/s that shipped with the computer to see if it indeed works.  If it does, I'd be interested to know why Ubuntu fails to recognize the rest of the RAM...

thanks
z

---

### Post by zephyr707 on 2011-07-29
So the opensuse 64bit only recognizes 8gb as well.  I did run  memtest86+ v4.10 that came with the livecd and that showed all 4 slots populated with "4096 MB PC3-10600" memory in the "Memory SPD Informations" section, but it said there was only 8125M of memory and would only test that amount.  

I looked in the DMI Memory Info configuration option and it showed DIMM2 and DIMM3 as Empty, No mapping (Interleaved Device), so I'm not sure what is going on.   I will try swapping the memory around and reseating it to see if it changes anything and then try this windows 7 fix that asus recommended...

---

### Post by zephyr707 on 2011-07-29
I opened up the bottom of the laptop again, pulled all the RAM and cleaned the contacts, swapped them around so they were all in different slots and firmly re-installed them.  the laptop now recognizes all 16gb!   marked as solve

thanks
z

---

