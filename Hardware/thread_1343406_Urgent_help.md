---
title: "Urgent help:"
date: 2009-12-01
forum: Hardware
---

### Post by magnetpest2k7 on 2009-12-01
[FONT=Nimbus Sans L, sans-serif]Hello all I need urgent support from all and the ubuntu community. I am a passionate Ubuntu user and I have been using for a year. My old laptop got crashed when I flashed the bios. I now bought a TOSHIBA L505d-S5986 laptop which has amd athlon 2 dual core M300 processor and ATI Radon 4100 video card. [/FONT] 
 

 [FONT=Nimbus Sans L, sans-serif]I had huge trouble installing ubuntu when I put the live usb/cd it took very long time to boot and when it got inside the OS every thing freeze. I then tried fedora but even that dint work well it got into the same problem freeze! [/FONT] 
 

 [FONT=Nimbus Sans L, sans-serif]I searched and found that its due to the error acpi:lnxvideo:' unexpected exit with status 0x0009. [/FONT] 
 [FONT=Nimbus Sans L, sans-serif]This also given in this thread [http://ubuntuforums.org/showthread.php?t=1301101](http://ubuntuforums.org/showthread.php?t=1301101) [/FONT] 
 

 [FONT=Nimbus Sans L, sans-serif]So I put the acpi=off in the grub boot menu and then added to the gconf and now ubuntu is working. But the system monitor shows just one processor in use (again due to disabling acpi I guess) and ofcourse  when I remove the power ubuntu dosent dim the screen and dosent show any battery sign.[/FONT]
 

 [FONT=Nimbus Sans L, sans-serif]All linux guys and developers please post a solution for this hardware module. [/FONT] 
 

 [FONT=Nimbus Sans L, sans-serif]Awaiting your replies[/FONT]
 

 [FONT=Nimbus Sans L, sans-serif]Thanks [/FONT] 
 [FONT=Nimbus Sans L, sans-serif]Vineeth [/FONT]

---

### Post by Iowan on 2009-12-02
Which version (32/64) did you install?

---

### Post by magnetpest2k7 on 2009-12-03
ubuntu 9.10 64bit version

---

### Post by diegohquiros2007 on 2010-05-02
Hi , I have the same problem friend,  my laptop model is a L505D-Sp6905R, just as I disabled the ACPI, but my  computer only detects one processor, no longer do that but I'm desperate  ...

I tried with 32bit and 64bit Ubuntu 9.10

Thanks and  greetings from Costa Rica

---

### Post by sbailey85 on 2010-05-02
[U]oops posted info already posted. 

I would try to patch the kernel using instructions provided in the post you linked in your first post. I had a similar problem and mine works like a charm now. The instructions are on pg 8 of that thread.. (sorry for underlines can't get them off)
[/U][]("http://ubuntuforums.org/showthread.php?t=1301101")

---

