---
title: "HP dv6000 (Can't boot without noapic kernel flag)"
date: 2006-10-30
forum: Hardware &amp; Laptops
---

### Post by theconley on 2006-10-30
I'm running edgy 64 bit on an hp dv6000.

I can only get it to boot when I use the noapic kernel flag.  However, this kind of ruins a few things for me, such as wireless, can't get opengl hardware support working right, etc.

(When I use the graphical ndiswrapper utility, it shows that I don't have a wireless card for my driver present)

Any suggestions?  Is there something not as harsh as noapic that I can use?

---

### Post by markybob on 2006-10-30
what really stinks is that the fans arent controlled and this laptop *will* overheat and freeze when working hard. anyone know of a workaround for that?

---

### Post by artificialsteve on 2006-10-31
Been experimenting with linux os for over a year now, just got into Ubuntu....Nice OS really, great look and feel, and I really despise Windows and really want to use Ubuntu...But as the trend is going...I cant get Broadcom 4311 wireless  to freaking work!!!
Actually, I cant get my regular old ethernet working either! I'm using the 64 6.10 version.....And I swear to god ndiswrapper is the most UNCLEAR AND ANNOYING utility I have ever seen!!!!! I'M SICK OF THIS CRAP!!!!! Why do these companies only make windows folks happy?? AHEM...BROADCOM!!! At least I am learning how to use the root terminal better.....

OK. So Here are my questions for any geek available..
1. How do you install ndiswrapper if you dont have the internet? I have it on a usb flash drive.
 1.5 ALSO, WHY does it say I need the .INF file and the .SYS file....and where the hell is the folder you're supposed to copy it to, and how do you do all of that while being sudo?? AAAHHH!
I cant believe no one has come up with a better program than ndiswrapper.....WHAT PART OF THE .INF FILE DOES ndiswapper USE??
WHAT PART OF THE >SYS??   ANYONE? 

2. Why arent there any MP3 Players on Ubuntu? What is ogg?WHY?

3. Are there any Multi-track editing programs for linux? Something like cooledit pro/adobe audition??

4. IS there a way to reset Ubuntu to default settings w/o re-install??

Thank you and everyone let's keep trying to make internet neutral!!!!

---

### Post by teaker1s on 2006-11-11
Strange, I have a DV6000 BRANDED dv6116EU the fans run correctly-could it be the bios version needs updating. I have wireless up and running using bcm43xx-fwcutter only running at 11m/bit, but running with NetworkManager Applet 0.6.3. my problems are that it sometimes won't fully boot and sometimes won't reboot.

---

### Post by markybob on 2006-11-11
Could you please tell me which bios version you have?  And if you have the chance, please post a lspci -v.  Which ubuntu version are you using?  Which kernel?  Any special modules?  Have you done CPU-intensive tasks to see if it overheats after a while and freezes?  Something like compiling a kernel?  Thanks!

---

### Post by teaker1s on 2006-11-12
I used the live install cd edgy 64bit 
fan seems to run correctly-ie when it gets warm fan will start slow and occasionally it will run fast briefly when warm.

bios version f.17 i'll post more details on exact bios version later as gf wants to use it
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
        Subsystem: Hewlett-Packard Company Unknown device 30b7
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: <access denied>

00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
        Subsystem: Hewlett-Packard Company Unknown device 30b7
        Flags: 66MHz, fast devsel

00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
        Subsystem: Hewlett-Packard Company Unknown device 30b7
        Flags: 66MHz, fast devsel

00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
        Subsystem: Hewlett-Packard Company Unknown device 30b7
        Flags: 66MHz, fast devsel

00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
        Subsystem: Hewlett-Packard Company Unknown device 30b7
        Flags: bus master, 66MHz, fast devsel, latency 0

00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
        Subsystem: Hewlett-Packard Company Unknown device 30b7
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: <access denied>

00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
        Subsystem: Hewlett-Packard Company Unknown device 30b7
        Flags: 66MHz, fast devsel

00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
        Flags: 66MHz, fast devsel

00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 00004000-00004fff
        Memory behind bridge: b3000000-b31fffff
        Prefetchable memory behind bridge: 00000000d0000000-00000000d0100000
        Capabilities: <access denied>

00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        Memory behind bridge: b3200000-b33fffff
        Capabilities: <access denied>

00:05.0 VGA compatible controller: nVidia Corporation C51 PCI Express Bridge (rev a2) (prog-if 00 [VGA])
        Subsystem: Hewlett-Packard Company Unknown device 30b7
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 11
        Memory at b2000000 (32-bit, non-prefetchable) [size=16M]
        Memory at c0000000 (64-bit, prefetchable) [size=256M]
        Memory at b1000000 (64-bit, non-prefetchable) [size=16M]
        [virtual] Expansion ROM at 50000000 [disabled] [size=128K]
        Capabilities: <access denied>

00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
        Subsystem: Hewlett-Packard Company Unknown device 30b7
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: <access denied>

00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
        Subsystem: Hewlett-Packard Company Unknown device 30b7
        Flags: bus master, 66MHz, fast devsel, latency 0
        I/O ports at 1d00 [size=128]

00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
        Subsystem: Hewlett-Packard Company Unknown device 30b7
        Flags: 66MHz, fast devsel, IRQ 10
        I/O ports at 3040 [size=64]
        I/O ports at 3000 [size=64]
        Capabilities: <access denied>

00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
        Subsystem: Hewlett-Packard Company Unknown device 30b7
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 10
        Memory at b0040000 (32-bit, non-prefetchable) [size=256K]

00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3) (prog-if 10 [OHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30b7
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 217
        Memory at b0004000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3) (prog-if 20 [EHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30b7
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 225
        Memory at b0005000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1) (prog-if 8a [Master SecP PriP])
        Subsystem: Hewlett-Packard Company Unknown device 30b7
        Flags: bus master, 66MHz, fast devsel, latency 0
        I/O ports at 3080 [size=16]
        Capabilities: <access denied>

00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1) (prog-if 85 [Master SecO PriO])
        Subsystem: Hewlett-Packard Company Unknown device 30b7
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 201
        I/O ports at 30c0 [size=8]
        I/O ports at 30b4 [size=4]
        I/O ports at 30b8 [size=8]
        I/O ports at 30b0 [size=4]
        I/O ports at 3090 [size=16]
        Memory at b0006000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2) (prog-if 01 [Subtractive decode])
        Flags: bus master, 66MHz, fast devsel, latency 0
        Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
        Capabilities: <access denied>

00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
        Subsystem: Hewlett-Packard Company Unknown device 30b7
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 50
        Memory at b0000000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
        Subsystem: Hewlett-Packard Company Unknown device 30b7
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 209
        Memory at b0008000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at 30e0 [size=8]
        Capabilities: <access denied>

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
        Flags: fast devsel
        Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
        Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
        Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
        Flags: fast devsel
        Capabilities: <access denied>

03:00.0 Network controller: Broadcom Corporation Unknown device 4311 (rev 01)
        Subsystem: Hewlett-Packard Company Unknown device 1364
        Flags: bus master, fast devsel, latency 0, IRQ 233
        Memory at b3200000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

daniel@daniel-laptop:~$

---

### Post by bfledderjohn on 2006-11-29
I am relatively new to linux, and Ubuntu, but I have just gotten a dv6000, too.  I read somewhere that the newer linux kernels (I believe Edgy uses 2.6.17.10) are addressing the apic issue. 2.6.19 rc1 was specifically mentioned as ironing out some of the problems.

I haven't installed Edgy on the dv6000, yet, and before I do, how scary it is to upgrade the kernel to 2.6.18 or even scarier 2.6.19 after I install Edgy?  And will it fix the problems?

Thanks!

Bret

---

### Post by teaker1s on 2006-11-29
[look here for a few pointers]("https://wiki.ubuntu.com/hp_dv6000_series_%28dv6116eu%29?highlight=%286116eu%29")

---

### Post by ubm on 2007-03-20
teaker1s thanks a bunch for that link!

---

### Post by Cywolf1 on 2007-09-07
Guys check out this other post I made.  I think I have a solution to the noapic problem when booting.  Basically just do this in a terminal.

echo "dev.rtc.max-user-freq=1024" >> /etc/sysctl.conf

The problem seems to be the freq of the RTC.

[http://ubuntuforums.org/showthread.php?p=3323930&mode=linear#post3323930](http://ubuntuforums.org/showthread.php?p=3323930&mode=linear#post3323930)

Cyber///olf

---

### Post by Ayuthia on 2007-09-07
> **Cywolf1 said:**
> Guys check out this other post I made.  I think I have a solution to the noapic problem when booting.  Basically just do this in a terminal.

echo "dev.rtc.max-user-freq=1024" >> /etc/sysctl.conf

The problem seems to be the freq of the RTC.

[http://ubuntuforums.org/showthread.php?p=3323930&mode=linear#post3323930](http://ubuntuforums.org/showthread.php?p=3323930&mode=linear#post3323930)

Cyber///olf

I tried out your suggestion and when I rebooted, it locked up where it usually does.  I have a dv6338se with the AMD/Nvidia 6150/Broadcom 4311 setup and running Kubuntu Gutsy 64-bit 2.6.22-10-generic flavor.  I am now using the noapic noirqdebug option.

---

### Post by Cywolf1 on 2007-09-08
Hmm, that's odd.  Mine has been running fine now for a couple of days, after multiple reboots.  All of my issues were resolved.  Your model is a bit different....but it should be similar hardware. So that's strange...Well I would check and make sure that your model is locking up on the system clock....like mine was.  

I do know of one more possible solution that may help, if your's still locks up on the system cock.  You can go into the /etc/rcS.d/S11hwclock.sh file and add "--directisa" to all of the lines that execute /sbin/hwclock.  (It's a shitty hack, but what can you do)

 When I was debugging and testing the clock problem, I found that if I disabled the hwclock startup script, the computer would boot normally without kernel boot options like noapic, however when you opened a console and ran the "hwclock -s" command, the computer would freeze. If I ran "hwclock -s --directisa", the clock would function normally and set the time drift correctly. 

Funny thing is, I just tested mine running hwclock -s --debug and my laptop locks up...it seems to boot fine, as long as I never run hwclock within the system after startup.  Debug says:

Waiting for clock tick...
/dev/rtc has no interrupts, waiting in loop for time change from /dev/rtc....

So the real problem is that /dev/rtc is not working like it should be and reporting hwclock time.  The hwclock binary just halts the system, and waits for a time event from /dev/rtc inside of some conditional loop in the binary, but it never gets it....so the system appears frozen....but it is really just waiting forever inside of a loop...

They (ubuntu) just changed the rtc to built in instead of a kernel module in 2.6.22-10 from what I can tell.  It was module not too long ago, from what I remember.  So it seems that /dev/rtc is not being setup properly or is not talking to the system correctly.  Not sure if it's related to the module/builtin change, but you never know.

---

### Post by brainsqueezer on 2008-01-30
I'm trying to join efforts. HP tx1000 series seem to have exactly the same problem:

[http://ubuntuforums.org/showthread.php?t=442483](http://ubuntuforums.org/showthread.php?t=442483) (57 pages now)

I think a firmware update (that won't appear in next months or maybe never) or a kernel workaround must be the only one real solution. Here is the only related bug report that has not been given much importance:

[http://bugzilla.kernel.org/show_bug.cgi?id=8870](http://bugzilla.kernel.org/show_bug.cgi?id=8870)

At comment #27 a developer talk about a possible patch:

[http://bugzilla.kernel.org/show_bug.cgi?id=8870#c27](http://bugzilla.kernel.org/show_bug.cgi?id=8870#c27)

---

