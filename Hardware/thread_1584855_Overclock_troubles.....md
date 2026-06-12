---
title: "Overclock troubles...."
date: 2010-09-29
forum: Hardware
---

### Post by peptobismal on 2010-09-29
[B]AMD Athlon(tm) II X4 630 Stock: 2.8GHz (200 x 14)
I am able to run stably for awhile everything is running fast and smooth at 3.08GHz, but what's the point in overclocking to that point?

DMIDECODE OUTPUT[/B]: 
    Version[[COLOR=blue][FONT=Verdana][/FONT][/COLOR]]("http://www.tomshardware.com/forum/262152-29-tweaking-gold-ddr2-dram-ocz2g8004gk#"): AMD Athlon(tm) II X4 630 Processor 
    Voltage: 1.0 V 
    External Clock: 220 MHz 
    Max Speed: 3000 MHz 
    Current Speed: 3080 MHz 
    Status: Populated, Enabled 
    Upgrade: Socket 754 
    L1 Cache Handle: 0x0008 
    L2 Cache Handle: 0x000A 
    L3 Cache Handle: Not Provided 

Memory Controller Information 
    Error Detecting Method: 64-bit ECC 
    Error Correcting Capabilities: 
        None 
    Supported_ Interleave_[URL="http://www.tomshardware.com/forum/262152-29-tweaking-gold-ddr2-dram-ocz2g8004gk#"]
[/URL]: One-way Interleave 
    Current Interleave: One-way Interleave 
    Maximum Memory Module Size: 4096 MB 
    Maximum Total Memory Size: 8192 MB 
    Supported Speeds: 
        70 ns 
        60 ns 
        50 ns 
    Supported Memory Types: 
        Standard 
        DIMM 
    Memory Module Voltage: 2.9 V 
    Associated Memory Slots: 2 
        0x0006 
        0x0007 
    Enabled Error Correcting Capabilities: 
        None

Here is my last post at Tomshardware.com you can find the whole thing at [http://www.tomshardware.com/forum/262152-29-tweaking-gold-ddr2-dram-ocz2g8004gk#t1877123](http://www.tomshardware.com/forum/262152-29-tweaking-gold-ddr2-dram-ocz2g8004gk#t1877123)
> **From Me at tomshardware.com:**

Yeah my memory is at 4x which sets it to 900MHz I believe? The 5x  would be 1337MHz or something to that effect. I had to set all the  voltages to Auto, it wouldn'[[COLOR=blue][FONT=Verdana][/FONT][/COLOR]]("http://www.tomshardware.com/forum/262152-29-tweaking-gold-ddr2-dram-ocz2g8004gk#")t boot up feeding the voltages to it. Maybe Gigabyte doesn't like it or I don't  know what I am doing, but messing with the voltages manually I couldn't  get the "VOLTAGES NOT OPTIMISED" warning to disappear. 

I'll try 245 with my stock cooler and see what happens. I was just  getting so frustrated with it not booting properly and having under  clocking everything to boot, so I was trying anything to get it to run. 

**EDIT:** Okay I wrote down all my trials and errors. 
245: POST failure 
240: Kernel failure - Kernel Panic system haulted 
235: The error codes that appear, to me, look like memory errors?  It's a lot of hex files and libraries some of which have "get" and "put"  prefixes. 
230: At first this ran fine, but it was failing to load Gnome or KDE  on login. Then the second go around it was posting error: "No suitable  module for kernel found." Then it continues to boot to shell prompts. 
225: Is delivering that same error message as 230. So, I dunno I went back down to 220 and everything is running fine again? 

I am not sure could it be the kernel? I usually boot from the second  kernel (not the newest); however, I did attempt to try the first kernel  (newest), just to attempt, but same thing. I don't normally boot into  the first one, because it randomly started having problems with my[[COLOR=blue][FONT=Verdana][FONT=Verdana][/FONT][/FONT][/COLOR][FONT=Verdana][/FONT]]("http://www.tomshardware.com/forum/262152-29-tweaking-gold-ddr2-dram-ocz2g8004gk#")_ Ethernet adapter,_ which we all know renders a computer these days almost useless.  

I am going to do some looking around the Ubuntu forums and see what I  can come up with, because you are right about it being able to get to  3.5GHz rather easily. If only my kernels wouldn't seem to mess up at  that speed?  

It did have some boots on the new kernel and the second kernel that  said something about "Did the system wait long enough?" and "Did the  system use the right device?" I dunno if any of that information is at  all helpful. 

**Edit:** After running at 3.08GHz for a minute Firefox  was abruptly shutting down as any other web browser was. Then as I was  downloading PerlMon (like CPU-Z) the screen went black then the  wallpaper loaded and the cursor showed up with sporadic loading in  background and loading cursors interchanging fast. I guess Linux just  isn't the operating system to tweak CPUs on? All the information I have  found has been very ambivalent on what and what doesn't work. 

It's just really weird to me, because 3.08GHz seemed to run fine.  Maybe it's a problem with the CPU Scaling device that is implemented  into Linux?  

All I know is this is getting to the point where I want to just quit  using Ubuntu altogether... I mean seriously, it wasn't my favorite  distro when they were sending you the free CDs along with the Live  CDs... I stuck with Fedora, I went to the store to buy a linux disc when  I was having problems after a Windows 7 upgrade from XP with the  bootmgr.exe. So, I wanted to put Grub on so I decided to get one from  the store, because I did not have Internet at this point. All they had  was Ubuntu, so I tried partitioning and setting up a dual boot which  worked, but Windows still wouldn't go past the start up splash screen. 

Seriously, every Operating System is starting to tick me off, haha.  [IMG]http://img.tomshardware.com/forum/uk/icones/smilies/pfff.gif[/IMG] 

**Edit** Found this: [http://ubuntuforums.org/showthread.php?t=1546143](http://ubuntuforums.org/showthread.php?t=1546143) Do you think this solution may be a problem?                                                                                                                                                                            Please tell me what I am missing here? I have tried everything I can think of to get the kernel to be stable enough to boot/run programs at something higher than 3ghz... I want to kill my computer. ](*,) Also, note that updated the kernel today to what like 35? Which is running stably at 2.8GHz stock? Not running at 245 like where it would be nice at.

---

### Post by peptobismal on 2010-09-30
Bump much?

---

