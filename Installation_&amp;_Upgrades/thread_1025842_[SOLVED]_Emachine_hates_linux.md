---
title: "[SOLVED] Emachine hates linux?"
date: 2008-12-30
forum: Installation &amp; Upgrades
---

### Post by Mathematician on 2008-12-30
Hey hows it going, been using linux for almost a year now, just recently tried to install/run live cd of linux on my eMachine, but it freezes at the splash loading screen every time.

specs:

Emachine T5010
Pentium 4 2.93 Ghz
DDR RAM 744 MB
Intel Graphics Media Accelerator 900
533 Mhz FSB
1 MB L2 Cache
200 GB HD 7200 RPM SATA 

Every form of linux on a live cd that I've tried has always frozen when on the splash loading screen. I have Windows XP currently installed & running, with no problems - but its a special xp disc customized specifically for emachines. I've tried the following linux distros:
ubuntu, xubuntu 8.10, 8.04, 7.10, including alt cd's, PClinuxOS 2008-Gnome and KDE, Debian 2008-xfce, OpenSuse 10.0, Fedora 9

I tested all these cd's on my laptop and all of them work & I was able to install each of them on my laptop (Toshiba Tecra A-eight) at one point in time. 


I think it might be a hardware incapability problem, - was thinking about flashing the BIOS, but I would really prefer not to do so. 

Back when I first got into linux I installed ubuntu 7.04 on the Emachine with no problem but when it got to the splash loading screen it froze like usual. :confused:

Any suggestions? Thanks for the help

---

### Post by oilchangeguy on 2008-12-30
have you tried the alternate version (it's text based)?

---

### Post by cariboo on 2008-12-30
Have you tried the various startup options available by pressing F4 and F6?

I've go a much older eMachine that I installed Ubuntu lite on, it works well enough considering the age. I didnt have much pc-100 ram left, so it is limited to 128Mb, but it does  run.

JIm

---

### Post by Mathematician on 2008-12-30
> **oilchangeguy said:**
> have you tried the alternate version (it's text based)?

Yep tried it, it hung up when I tried to boot into Ubuntu.

> **cariboo907 said:**
> Have you tried the various startup options available by pressing F4 and F6?

I've go a much older eMachine that I installed Ubuntu lite on, it works well enough considering the age. I didnt have much pc-100 ram left, so it is limited to 128Mb, but it does run.

Jim 

hmm I've yet to try those options - I'll look into it 

Thanks for the reply's

---

### Post by SirAlphonso on 2008-12-30
I have an eMachine and I had the exact same problem.

---

### Post by Mathematician on 2008-12-30
> **SirAlphonso said:**
> I have an eMachine and I had the exact same problem.

ah were you able to fix the problem?

---

### Post by abn91c on 2008-12-30
try mandriva 2009

---

### Post by Sin@Sin-Sacrifice on 2008-12-30
Special XP disk??!!?? Smells to me like propriatisation. Is that a word? Should be now... I hate corporate America. Have you tried other distributions of linux I.E. fedora, Gentoo, or Knoppix for example? Or backtrack 3? Hehehehe...

---

### Post by melojo on 2008-12-30
You might try adding boot options, here is a link that may help.

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

I had a system that I had to add
all_generic_ide

---

### Post by Mathematician on 2008-12-30
> **Sin@Sin-Sacrifice said:**
> Special XP disk??!!?? Smells to me like propriatisation. Is that a word? Should be now... I hate corporate America. Have you tried other distributions of linux I.E. fedora, Gentoo, or Knoppix for example? Or backtrack 3? Hehehehe...

yes tried fedora 9, centOS, simplyMepis, sidux, debian, ubuntu, xubuntu 8.10, 8.04, 7.10, PClinuxOS 2008, opensuse 10, Mint

---

### Post by Coder543 on 2008-12-30
when you get to the ubuntu splash menu, click F6 to edit the command
backspace until you have remove the quiet parameter.
press enter (i think) to boot.

If anyone else can clarify my instructions, it would be appreciated.

This should make it talk to you until it locks up. Then you could tell us what happened.

---

### Post by Mathematician on 2008-12-30
> **Coder543 said:**
> when you get to the ubuntu splash menu, click F(something) to edit the command
backspace until you have remove the quiet parameter.
press enter (i think) to boot.

If anyone else can clarify my instructions, it would be appreciated.

This should make it talk to you until it locks up. Then you could tell us what happened.

[QUOTE=melojo]
You might try adding boot options, here is a link that may help.

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

I had a system that I had to add
all-generic-ide[/QUOTE]

thanks guys - I modified the boot options it went pretty fast but for the most part it hits a point where it says this

udevd-event [5222]: run_program: exec of program '/sbin/modprobe' failed

repeatedly with different numbers in the brackets - then goes to - 

[235.597921] SQUASHFS error : sb_bread failed reading block 0xa88af
[235.597921] SQUASHFS error : Unable to read cache block [2a22ab2e:15c4]
[235.597921] SQUASHFS error : Unable to read directory block [2a22ab2e:15c4]

udevd-event [5236]: run_program: exec of program '/lib/udev/scsi_id' failed

appreciate the help - really want to get linux on this machine

---

### Post by melojo on 2008-12-30
This is the mother board it uses.
[http://www.skyline-eng.com/index.cfm/fuseaction/product.display/Product_ID/5786](http://www.skyline-eng.com/index.cfm/fuseaction/product.display/Product_ID/5786)

Its an intel chipset so i don't understand why it won't work.
Have you tried making changes in your bios that reflect sata or ide?

To me it looks like it can't read the cd correctly.

If you had a spare cdrom around I would swap it out and give it a try.

I had a problem with a dvd r/w that couldn't read or write cd's correctly for some reason but had no problem with dvd's.  Didn't make any since. 
I bought another dvd r/w and didn't have the problme anymore.

You might do some googling on that board and find out as much as possible.

Good luck

Maybe someone else can jump in with a better idea.

---

### Post by Mathematician on 2008-12-31
Just finished trying out PCBSD, OPENBSD, MAndriva 10 2009 - none of them worked. Decided to try Gentoo, and it actually worked for some reason? :confused:

The problem I think is the hardware in my eMachine. 

Thanks for all the help, I'll keep you updated if I can figure out whats hanging up in the other linux distros.

---

### Post by melojo on 2008-12-31
Glad you got one working.

Also I type the all_generic_ide incorrectly.  I type it in hyphens instead of underscore.

---

### Post by thepizzaman on 2008-12-31
did you try acpi=off? i couldn't install until i had added that

---

### Post by Mathematician on 2008-12-31
> **melojo said:**
> Glad you got one working.

Also I type the all_generic_ide incorrectly.  I type it in hyphens instead of underscore.

Yeah - appreciate the help

[QUOTE=thepizzaman] did you try acpi=off? i couldn't install until i had added that [/QUOTE]

Yeah tried that - it still froze up in the same spot, I'm still playing around with my BIOS and some of those settings to see if I can get Ubuntu/Xubuntu running.

---

### Post by tmsbrdrs on 2009-12-22
I'll be putting Linux on an Emachine with roughly the same specs. Had problems booting into almost every LiveCD I tried with the exception of Puppy Linux. For some reason, there was no problem at all loading into it. 

Have you tried installing Linux on a different machine then moving it over? Since I've got several machines and Linux isn't tied to the hardware, that might just work.

---

