---
title: "Hard Drive Load Causes Complete Lock Up/Freeze"
date: 2007-10-02
forum: Hardware &amp; Laptops
---

### Post by Jimmy The Clown on 2007-10-02
Been chasing this annoying problem for about a month and a half and I am desperate.

Everytime I have significant hard drive load for a decent length of time I get a hard lock up. No mouse pointer, No ctrl-alt-Fx. No ctrl-alt-backspace. I have to turn the computer on and off physically. When I say hard drive load, I mean copying a dvd to my hard drive, or copying the contents of my USB hard drive over to my desktop, or even sometimes using bonnie++ (hard drive load tester). It seems to take about 3 gig of data at high speeds to cause the lock. If I bittorrent an install dvd iso it will come through fine.

Hardware:
Shuttle XPC SN27P2 w/ Nvidia nforce 570 ultra chipset
AMD 64 x2 5200
4 gig ram
WD 320 gig HD sata 2.0
nvidia 6800
Atheros based wifi card

I have tried:
[LIST=1]
[*]Feisty 32 bit
[*]Gutsy Beta 32
[*]Flashing to latest bios
[*]Stressing video card heavily
[*]Full test of HD using WD's tools
[*]Memtest
[/LIST]

If I don't spin the hard drive up too much, I can stay running for days before I get a crash. Otherwise I can repeatably crash this thing every time I try to copy my mp3 collection over from USB hard drive or rip a dvd. This is incredibly annoying and basically makes my system unusable.

Anyone have any tips about bios settings or boot options? I need some help here...

-JTC

---

### Post by Jimmy The Clown on 2007-10-05
**bump**

Does anyone even have any suggestions for troubleshooting???

-JTC

---

### Post by dabl on 2007-10-05
No magic bullet here, but I'd look into tweaking performance to perhaps allow more aggressive use of swap and things like that.  Here's a "Linux Performance" link that I use:

[http://rudd-o.com/archives/2007/10/02/tales-from-responsivenessland-why-linux-feels-slow-and-how-to-fix-that/](http://rudd-o.com/archives/2007/10/02/tales-from-responsivenessland-why-linux-feels-slow-and-how-to-fix-that/)

The other thing that you could do is remember the "_R_aising _S_kinny _E_lephants_ I_s _U_tterly _B_oring" routine.

RSEIUB

You have a "SysRq" key on your keyboard, probably to the right of F12 and above "Insert".  Used with the Alt key, it is able to issue commands to your frozen Linux system, and will allow you to do a graceful shutdown rather than a hard crash with the power button.  So, then next time it is totally hung, you give it Alt-SysRq RSEIUB and it will restart without damage.

[http://digg.com/linux_unix/Fix_a_Frozen_System_with_the_Magic_SysRq_Keys](http://digg.com/linux_unix/Fix_a_Frozen_System_with_the_Magic_SysRq_Keys)

:)

---

