---
title: "Why Are Internal Sata Hard Drive Data Transfer Speeds Slow in Ubuntu"
date: 2010-07-06
forum: Hardware
---

### Post by garryconn on 2010-07-06
Hello everyone, this is my first post. I want to start by saying that it is great to see how active and supportive the people are here within the Ubuntu community. Over the last few years I have played around with Linux here and there, but nothing real serious until last year when I purchased a MacBook. After that, Windows was a thing in the past. During the year I have used my MacBook, I see that many of the operations are similar to Linux, and that makes Ubuntu even more fun than it had in the past.

I have Ubuntu 10.04 LTS installed on my Dell Dimension 8400 desktop, which is used for my home-based computer repair business. I could have easily installed and used Windows, but I felt like using Linux was the better choice. The primary purpose for my Dell is performing data transfers and virus removal on customer hard drives.

That said, here is my problem. The data transfer speeds are very slow from one internal sata hard drive to another in my Dell. In most all cases the data transfer speed is less than 1.0 MB/sec. Needless to say, this isn't going to work when the whole purpose behind why I installed Ubuntu was to perform data transfers from one internal hard drive to another. 

I want to mention that prior to writing this post, I spent a lot of time searching through the Ubuntu forums, researching, and reading a quite a bit of information. Based on what I have read here in the forums, as well as a few blogs, is that slow data transfer speeds have been an on-going issue for a few years. And Secondly, there doesn't seem to be an active or mainstream solution.

Ideally, what I would like to know is if there is a different Linux distribution that is better suited for executing data transfers from one internal sata hard drive to another. Of course, I would like to continue using Ubuntu for my home-based computer business, but in order to do that, I will need help speeding up the data transfer rates. Any help pointing me to a different distribution of linux, or support with increasing data transfer speeds will be very appreciated.

```
garryconn@dell-dimension:~$ sudo hdparm /dev/sda
[sudo] password for garryconn: 

/dev/sda:
 multcount     =  8 (on)
 IO_support    =  0 (default) 
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 121601/255/63, sectors = 1953525168, start = 0
garryconn@dell-dimension:~$ sudo hdparm -i /dev/sda

/dev/sda:

 Model=ST31000528AS, FwRev=CC44, SerialNo=9VP50Z4W
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs RotSpdTol>.5% }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=unknown, BuffSize=0kB, MaxMultSect=16, MultSect=8
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=1953525168
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: unknown:  ATA/ATAPI-4,5,6,7

 * signifies the current active mode

garryconn@dell-dimension:~$ 
```

---

### Post by clrg on 2010-07-06
This sounds like a kernel issue. 

Does your laptop's mainboard support [DMA]("https://secure.wikimedia.org/wikipedia/en/wiki/Direct_memory_access") and have you enabled it?

---

### Post by Yarui on 2010-07-06
Well, like clrg said, this issue is probably related to the kernel.  If  that is the case and you really want to switch distros the first ones  you should try are probably Fedora and openSUSE.  The reason for this is  that they are both fairly easy to use and they are entirely different  distros from Ubuntu which are likely to have more noticeable differences  in the kernel than some other distros.

If you were to switch to  Debian, or anything Debian-based, you are more likely to have the same  issues since Ubuntu is Debian-based.  There are a few other major distros that  are different enough that you could have some luck with them, but they  are all a lot more work than Debian, Red hat, or SUSE based distros, so  you would probably be better off trying distros from those 3 branches  first.

All that being said, I'm not sure switching distros is going to be the best solution for this problem, but if you can't find any other solution it could be worth a try.

---

### Post by garryconn on 2010-07-06
I like Ubuntu a lot. I'd prefer that I continue using it. But, I need to figure out why data transfer is so slow.

---

### Post by nos676 on 2010-07-06
as stated in earlier posts. try different distro's to see if it is the ubuntu 10.04 LTS kernel that may be the problem.

---

### Post by garryconn on 2010-07-06
Thanks, I am in the process of researching other distros, but I have a lot interest in solving this issue with Ubuntu. As mentioned in my first post, this is an issue that has been going on for years and there doesn't seem to be a mainstream solution.

---

### Post by garryconn on 2010-07-07
Do anyone want to take a stab at this?

---

### Post by Yarui on 2010-07-07
Well like we have already said, it could be a kernel issue.  If you wait a new kernel may resolve it, but aside from that I'm not really sure what you could do.

It is possible it could be hardware related.  replacing cables is always a good place to start when troubleshooting hardware.  If the problem is that the speed is slow when writing from one drive to another, then it would probably be good to replace the cables for both drives.  If one of them is bad it could hurt the speed of the drive.  It could just be that one of the drives is bad, in which case you would have to replace the bad drive.

---

### Post by garryconn on 2010-07-07
> **Yarui said:**
> Well like we have already said, it could be a kernel issue.  If you wait a new kernel may resolve it, but aside from that I'm not really sure what you could do.

Not sure I want to wait another few years, crossing my fingers that this issue will get some needed attention... as I had already said, apparently this has been an ongoing and issue for a few years. Also, it seems to be something people avoid making any forward motion with. I'm just not too sure I'd like to wait for something that is speculative. In all honestly, I more / less just want this problem to be recognized as an issue and see some effort made towards resolution. 

With many online communities, people within reprimand others for not researching the material already in forums. I have done that. I have sat here for many hours, reading, and researching and each thread I read leads to the same result: 1.) it either get's ignored. 2.) it gets over-taken by garbage and unrelated topics, and 3.) it get's left unanswered and unresolved after pages and pages of updates. 

Honestly, I like Ubuntu... a lot. I think it's a great operating system. I have it installed on many of my computers. And for everyday / typical user operations, it works flawlessly. And also, I would have never really known about the lengthy long issue about slow transfers if I hadn't started to research why data transfer was slow on my system.  

> 
it would probably be good to replace the cables for both drives. If one of them is bad it could hurt the speed of the drive. It could just be that one of the drives is bad, in which case you would have to replace the bad drive.


All my cables, drives, and components are in excellent working order. This is not a direct hardware issue. It's either an issue with software settings or something in the OS itself. And that's what I'd like to get support for. If there are some settings that should be tweaked or optimized, etc.

From what I can see so far, no one has brought any solutions to the table regarding this issue. Here's a few of the threads that I have read that cover the same issue:

[http://ubuntuforums.org/showthread.php?t=855082](http://ubuntuforums.org/showthread.php?t=855082) -- abandoned 

[http://ubuntuforums.org/showthread.php?t=1100642](http://ubuntuforums.org/showthread.php?t=1100642) -- abandoned

[http://ubuntuforums.org/showthread.php?t=789820](http://ubuntuforums.org/showthread.php?t=789820) -- abandoned

[http://ubuntuforums.org/showthread.php?t=1264541](http://ubuntuforums.org/showthread.php?t=1264541) -- abandoned

[http://ubuntuforums.org/showthread.php?t=1279459](http://ubuntuforums.org/showthread.php?t=1279459) -- redirected to another thread which has been abandoned

[http://ubuntuforums.org/showthread.php?t=1150108](http://ubuntuforums.org/showthread.php?t=1150108)  -- abandoned after 348 entries

[http://ubuntuforums.org/showthread.php?t=1112701](http://ubuntuforums.org/showthread.php?t=1112701) -- redirected to multiple threads which have been abandoned and abandoned itself

Further, I have search through about 30 more threads found by doing an exact title search in Google for "[slow transfer speed]("http://tinyurl.com/2ffs4k8")" to no avail. 

The main thing I want to communicate is that I have done my homework prior to creating this thread. I have invested many hours into research and once I concluded that the answer couldn't be found, I then decided to create the thread. So seriously, if anyone is willing to help, that would be great. Otherwise, like I said earlier, and what was aimlessly suggested to me already... I'll just experiment with other Linux distros.

---

### Post by Yarui on 2010-07-07
Well if that many threads about this issue have come up with no solution, I'll be surprised if somebody suddenly has a stroke of genius that will fix it.  If you are lucky you may get a response from a dev that actually knows what is going on here, but I wouldn't hold out for that.  If you have done this much work and found no answer then I suppose trying out another distro could be the way to go.  This issue seems to be beyond my ability to help you with, but I have a fair amount of experience with other distros, so I could attempt to contribute some thoughts on that subject if you would like.

---

### Post by garryconn on 2010-07-08
That would be great. I appreciate the help a lot. I apologize, I re-read my last response and realize much of that was more / less venting that anything else. I'll admit, I am slightly frustrated. And, I do realize that this isn't really any particular person's fault. 

So if you're familiar with other brands, basically all I need is something that will allow me to quickly transfer data off customer's hard drives onto my computer. Slightly off topic, but I feel the need to share. I'm in the process of researching some hot swap sata hard drive enclosures for my computer. That way I can easily remove drives from customer's computers and quickly insert them into my computer to pull data off or remove viruses. So basically, if there's a version of Linux that's specific for doing super fast data transfers, that's what I need. 

I don't care about games, apps, and things like that. I just need something that's user friendly, has a nice GUI, stable, and all in all... a great work horse of an operating system. What do you recommend?

---

### Post by Xianath on 2010-07-08
Install the sysstat package either via the GUI or with "sudo aptitude install sysstat". Start a long transfer and run the following command:

iostat -bdpqu -P ALL 60 1

Wait for it to finish (it will just sit there for a minute) and post the results. This should tell us where the resources are going. From there, we can start hacking at the problem.

That aside, Linux in general (not just Ubuntu) might be a poor choice for the particular job you're using it. The NTFS implementation is insanely slow and if most of what you're doing is dealing with Windows hard drives, a hardened Windows system might be a more rational choice. If you want to stick to Linux, you might find that for copying large chunks of data to and from NTFS drives, you might actually get better results running Windows 7 (MUCH better I/O subsystem than XP) in a virtual machine than Linux natively.

---

### Post by IcarusR on 2010-07-08
Might be worth registering a bug @ launchpad. If there isn't one currently active.

---

### Post by recluce on 2010-07-08
You could try one of the more recent kernels in the kernel ppa. Just search the ubuntu forum for "install newer kernel" and you will get all the directions you need. The 2.6.32 kernel line is sort of dated already, 2.6.34 runs quite well on my machine (with Lucid).

If you are in the computer repair business, you probably have access to a PCIe or PCI SATA controller. Try to connect your drives to an alternate controller to see if the problem persists.

Also: what mode is the BIOS set to? AHCI, IDE emulation or RAID? Best choice for Ubuntu is probably AHCI.

---

### Post by dabl on 2010-07-08
I didn't see this on the list of links -- it may or may not have anything useful:  [http://www.thinkwiki.org/wiki/Problems_with_SATA_and_Linux](http://www.thinkwiki.org/wiki/Problems_with_SATA_and_Linux)

I wonder if the observed slow data transfer is possibly due more to the kernel scheduler than anything about the SATA bus or drives.  You might want to investigate setting a scheduler option different than the default (I'm not expert on this, don't ask ...).  Here are some links:

[http://www.wlug.org.nz/LinuxIoScheduler](http://www.wlug.org.nz/LinuxIoScheduler)

[http://www.serverwatch.com/tutorials/article.php/3715071/Ubuntu-Server--Kernel-Configuration-Considerations.htm](http://www.serverwatch.com/tutorials/article.php/3715071/Ubuntu-Server--Kernel-Configuration-Considerations.htm)

[http://www.kernel.org/doc/#Process_Scheduler](http://www.kernel.org/doc/#Process_Scheduler)

Also, you might try a "realtime" kernel -- it's available in the standard repos.  Usually it's wanted for audio processing/editing, but it might yield better results for your purpose too.

---

### Post by Calypoland on 2010-07-08
Hi
I have the same drive.It's connected to ICH9 chipset on X7SBE ,AHCI is off in bios.System Debian/Lenny 2.6.26-2- distro kernel.My works fine
(hdparm says about 116MB/s)  ,exepts one  thing tha bothers me - BuffSize=0kB . IMHO it shoud be 32768kB. Other Seagates (3diffrent models) on this system shows correct values. I don't know is it a hdparm issue or this cache is not used at all. See same thing at your output .
 One diffrence (exept firmware)that i see is MultiSect = 8.Did you try set it  to 16 ? (hdparm -m 16 /dev/sda)  

Here is mine

Model=ST31000528AS                            , FwRev=CC38    , SerialNo=            5VP4XSGF
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs RotSpdTol>.5% }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=unknown, BuffSize=0kB, MaxMultSect=16, MultSect=?16?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=1953525168
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: unknown:  ATA/ATAPI-4,5,6,7

---

