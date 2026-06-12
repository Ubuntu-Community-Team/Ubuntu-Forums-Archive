---
title: "Random Unprovoked Reboots"
date: 2005-10-18
forum: Hardware &amp; Laptops
---

### Post by jmpaluska on 2005-10-18
I upgraded to Kubuntu 5.10 over the weekend on my Via 694X-based Dual PIII/700.  It runs the stock 2.6.12-9-686-smp Ubuntu kernel.  Previously, it ran Debian Testing and a 2.6.12 kernel.

In Ubuntu, my machine randomly reboots without warning: the screens blank, the BIOS beeps, and then restarts the kernel.  I had no such problems under Debian--it was quite stable.  When I moved to the 2.6 kernel in Debian I found that I needed to pass "acpi=off" to the kernel or I'd have problems with my sound and network cards.  I thought that might be related to this problem, but even when I pass "acpi=off" to the Ubuntu kernel, I still get random crashes.

/var/log/syslog contains no useful information before the reboot--just syslog marks and then the reboot banner.

This is quite frustrating and I'd rather not lose another weekend next weekend putting Debian back on the system.  As much as I like how nice Ubuntu looks, stability is more important than looks.  Any ideas?

System Specs:
MSI 694D Pro motherboard (Via chipset)
2x Intel Pentium III/700
512MB CAS2 PC133 SDRAM
Matrox Millenium II (Display 0)
Nvidia GeForce4 MX 440 (Display 1)
Intel 82541GI/PI Gibabit Ethernet
Adaptec 2940UW SCSI Card
(Seagate Cheetah HD, Zip Drive, Plextor CD-RW)
IDE DVD-ROM
Built-in sound, etc.

---

### Post by adwait on 2005-10-18
It sounds like a motherboard or PSU problem.......

---

### Post by jmpaluska on 2005-10-18
I see that on the surface, but why would it manifest itself when I installed Kubuntu?  The machine ran had no problems before the install, even the day of the install, but crashed an hour after booting Kubuntu.

Another odd thing is that when ACPI was running, I couldn't reboot the machine when I wanted to.  The reboot command would shut it off, as would runlevel 6.  That's fixed now, but led me to believe that ACPI on this machine is broken.

I just turned off ACPI in the BIOS--maybe it will help.

---

### Post by funkninja on 2006-01-09
[QUOTE=jmpaluska]I see that on the surface, but why would it manifest itself when I installed Kubuntu?  The machine ran had no problems before the install, even the day of the install, but crashed an hour after booting Kubuntu.

Another odd thing is that when ACPI was running, I couldn't reboot the machine when I wanted to.  The reboot command would shut it off, as would runlevel 6.  That's fixed now, but led me to believe that ACPI on this machine is broken.

I just turned off ACPI in the BIOS--maybe it will help.[/QUOTE]


Hi,

Strangely enough I only installed ubuntu 5.1 a few days ago and I'm getting the same issue.

I've been trying to run Kino to export a few hours of DV footage as a DVD and I'll let it run and come back 7 hours later when it should've finished only to find that after about 3 hours or something (sometimes less sometimes more) the machine is sitting at the login screen and has rebooted.

I too did not have this problem previously. It's quite annoying because theres nothing in any of the logs that I can find.. only startup stuff.

Hmm.. What to do..

---

### Post by jmpaluska on 2006-01-09
For me, it turned out to be a PSU problem.  I went down to the local computer store, bought a new one, and haven't had that problem since.  Other problems--like random hangs--but no longer random reboots.  However, I think the hangs are related to one of the video cards in the system.

---

### Post by funkninja on 2006-01-09
[QUOTE=jmpaluska]For me, it turned out to be a PSU problem.  I went down to the local computer store, bought a new one, and haven't had that problem since.  Other problems--like random hangs--but no longer random reboots.  However, I think the hangs are related to one of the video cards in the system.[/QUOTE]

Mine seems to only happen if the machine is working.

I left it on overnight last night with it just sitting there doing nothing and it didnt reboot.

But without fail if its churning away at a task for hours it will fail.

All fans are working etc. 

It's possible that perhaps the PSU is overheating with all the extra work the disks and cpu are doing / supplying more voltage etc...

Maybe I'll try a different PSU and rerender the video. It's funny that it didn't happen previous to installing 5.1 from what I can remember. 

I'll see what happens.

---

### Post by kittcankitt on 2006-02-22
I dunno guys...this is happenning to me as well.  It started maybe a week ago and with plenty of log reading (to find pretty much what was stated above:  not much useful  :and then BAM MARK -- reboot)  My problem is when the pc is idle.  If we seem to use it, it'll stay on.  For example:  If we are web browsing, photoeditting, writing documents...etc the pc will stay on find.  If we turn around and leave it be, after usually between 1 to 1.5 hours, you'll hear the bios beep and find yourself back at the login screen.  Makes it very difficult to ie: seed a torrent.  I've tried just about everything I can think of to keep it going but nothing has seemed to work.  Finally decided to reinstall and that went great...until I woke this morning to a login screen...

Anyone?  I have changed the psu and the motherboard should be pretty good  as well...

Just thinking about it now, I was using a Live-CD almost all day yesterday and 1/2 the day before and the computer never reboot and I left it alone for several hours at a time.  hmmm?

---

