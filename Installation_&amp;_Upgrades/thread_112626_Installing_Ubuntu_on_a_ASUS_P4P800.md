---
title: "Installing Ubuntu on a ASUS P4P800"
date: 2006-01-04
forum: Installation &amp; Upgrades
---

### Post by Clefferson on 2006-01-04
[COLOR=SeaGreen]Hi great Linux Master![/COLOR]
I'm a IT Manager, almost n00b on Linux (i knew the few), and having trouble while instaling Breezy distro.

[COLOR=Gray]Hardware:[LIST]
[*]Asus P4P800 (Bios v.1019)
[*]P4 2.8GHz HT
[*]1024 Mb SDRAM 400
[*]Ati Radeon 9600 128Mb
[*]120 Gb SATA
[*]40X Pioneer DVD Slot-In
[*]52x32x52 ASUS CDR-W[/LIST][/COLOR]
Tried all day long installing Ubuntu... but of course i've been surprised!
After a cruel battle, i got the following:

[COLOR=Red]skge ignoring bogus sensor interups[/COLOR]

Here are my steps:[LIST]
[*]Installing Ubuntu Breezy[LIST]
[*]instalation hangs at Grub installation
[*]help seeking on ubuntu and linux web universe
[*]loooots of reboots and re-installs  *[SIZE=1]*pehaps it's about time to think about a "recover feature"[/SIZE]*
[*]help seeking on ubuntu and linux web universe
[*]found that there are a trouble while instaling with my motherboard IDE controller
[*]fixed BIOS to Compatible Mode
[*]fixed BIOS to not run with ACPI anc APIC Tables
[*]instalation ok
[*]reboot --> [COLOR=Red]skge ignoring bogus sensor interups[/COLOR][/LIST] 
[*]reboot... hangs while trying to start on WinXp[LIST]
[*]fixed BIOS to run with ACPI anc APIC Tables
[*]windows reboot... ok
[*]fixed BIOS to not run with ACPI anc APIC Tables
[*]help seeking on ubuntu and linux web universe
[*]fixed BIOS to Compatible Mode[/LIST] 
[*] installing Mandrake 10[LIST]
[*] works fine[/LIST] 
[*]Installing Ubuntu 4.10[LIST]
[*]instalation hangs [COLOR=Red]Cannot find CDROM device[/COLOR]
[*]help seeking on ubuntu and linux web universe
[*]loooots of reboots and re-installs  *[SIZE=1]*pehaps it's about time to think about a "recover feature"[/SIZE]*
[*]fixed BIOS to Compatible Mode
[*]instalation problems like no-network-at-all and now-i-want-to-freeze and [COLOR=Red]klogd: spurious apic interrupt on CPU#0[/COLOR]
[*]bios tweaking
[*]bios ACPI tweaking
[*]headhake
[*]bios IDE controler tweaking[/LIST] 
[*]old ubuntu version installing[LIST]
[*]more headhake
[*]bios flashing
[*]kernel inputs like ACPI=NOIRQ, NOAPIC, NOLAPIC, PCI=NOACPI[/LIST] [/LIST]Finally... after a bios Update and a lot of headhake, I have compiled that to install UBUNTU properly and be able to reboot on my old-but-still-working WinXP, BIOS must be set this way:[LIST]
[*]Bios version: 1019
[*]ACPI 2.0: Off
[*]APIC to ACPI: On
[*]Ide Controller: Enhanced Mode on S-ATA only[/LIST]So I've tryed again:[LIST]
[*]Installing Ubuntu Breezy
[*]instalation ok
[*]reboot --> [COLOR=Red]skge ignoring bogus sensor interups[/COLOR][/LIST]still have no solution...

I've heard that there are a lot of trouble while installing Ubuntu on this Motherboard.... so i'm looking for help....
[COLOR=SeaGreen][B]
WHAT SHOULD I DO TO MAKE UBUNTO WORK IN MY HARDWARE[/B][/COLOR]

Here are the other threads that helps me a lot.... until now[INDENT][http://ubuntuforums.org/showthread.php?t=107543&highlight=p4p800]("http://ubuntuforums.org/showthread.php?t=107543&highlight=p4p800")
[http://forum.ubuntu-fr.org/viewtopic.php?id=12221]("http://forum.ubuntu-fr.org/viewtopic.php?id=12221")[/INDENT]

---

### Post by Bartender on 2006-01-05
Clefferson -
I'm sorry but can offer no help.  Can you tell me where you'd gone to find out that there have been problems with the ASUS board?  My ASUS P5GDC-V home-built machine won't recognize the LiveCD (it's a good disc) at all.  The DVD drive looks at it several times, then moves on to the hard drive.  I tried changing the IDE setting from "Enhanced" to "Compatible" and the machine wouldn't even boot.
I'm wondering if some ASUS boards just won't cooperate??

---

### Post by Clefferson on 2006-01-06
Here's the news about _Installing Ubuntu on a ASUS P4P800_

Bios SETUP (Bios version: 1019)

[LIST]
[*]Main > IDE Configuration >
[LIST]
[*]Onboard IDE Operate Mode: Enhanced Mode
[*]Enhanced Support on: S-ATA
[/LIST]

[*]Power>
[LIST]
[*]ACPI 2.0 Support : No
[*]ACPI APIC Support: Enabled
[*]BIOS-->AML ACPI Table: Enabled
[/LIST]
[/LIST]
So I've tryed again:

Installing Ubuntu Breezy
[LIST]
[*]instalation ok
[*]reboot freeze --> [COLOR="DarkOrange"]skge ignoring bogus sensor interups[/COLOR]
[/LIST]

Installing Ubuntu 4.10
[LIST]
[*]instalation ok
[*]reboot [COLOR="DarkOrange"]OK![/COLOR]
[*]runing [COLOR="DarkOrange"]OK![/COLOR]
[/LIST]

So here's the fun thing.... with v4.10 running well, I attached to Synaptic pool my Breezy CD. Refreshed all, and Upgraded All....

When I reboot on the new 386 Kernel, the bogus sensor bug appears....
When I reboot on old 386 Kernel, i got no X environnement....  
Seems that i gonna install v4.10 again!!!!

[COLOR="SeaGreen"]Conclusion: the problem comes after I've upgraded to the new 386 Kernel (or pehaps from one of it dependencies also upgraded?)[/COLOR]

Could any GURU try to check this and confirm on a reply?

---

### Post by Tuf on 2006-01-06
I am running 5.10 on a P4C800-E Deluxe with no issues.  I am using the 686 smp Kernel but the regular i386 one seemed fine also.

I am new to Linux but am very interested in the solution so I thought I would shamelessly bump this thread :D

---

### Post by Clefferson on 2006-01-06
[quote=Tuf]I am running 5.10 on a P4**_C_**800-E Deluxe with no issues. I am using the 686 smp Kernel but the regular i386 one seemed fine also.

I am new to Linux but am very interested in the solution so I thought I would shamelessly bump this thread :D[/quote] 
Please, what's your Bios SETUP?

 Bios SETUP (Bios version: [COLOR=Blue]**????**[/COLOR])[LIST]
[*]Main > IDE Configuration >[LIST]
[*]Onboard IDE Operate Mode: [COLOR=Blue]**????**[/COLOR][LIST]
[*]Enhanced Support on: [COLOR=Blue]**????**[/COLOR][/LIST] [/LIST] 
[*]Power>[LIST]
[*]ACPI 2.0 Support : [COLOR=Blue]**????**[/COLOR]
[*]ACPI APIC Support: [COLOR=Blue]**????**[/COLOR]
[*]BIOS-->AML ACPI Table: [COLOR=Blue]**????**[/COLOR][/LIST] [/LIST][SIZE=3][COLOR=DarkRed]...indeed... it's on a P4**_C_**800-E Deluxe... lucky guy...[/COLOR][/SIZE]

---

### Post by johnpodge on 2006-02-23
I also am having problems with my asus motherboard....
but mine will not let me install it frezzes at isapnp on the bot screen for the installer 

Asus p4p800-e Deluxe 
3.0 gHz 
1 Gig Ram

---

### Post by Clefferson on 2006-03-14
Damn! After all this time running the distro correctly, I've had the bad... very bad idea of trying to upgrade the Kernel!

Since yesterday, I was runing with Kernel version 2.6.10-5-686-SMP, and of course, the 2.6.10-5-386 worked as well....

Guess what!?!? The 'bogus sensor' bug comes back! The upgrade makes my Kernel become version  2.6.12...... and no way to roll-back!

Now I probably got a clue of what is happening! All kernels after 2.6.10 wont work with the P4P800! 

Why? Don't ask me.....
 
So if you are trying to install ubuntu on a machine equiped with a Asus P4P800, DON'T TAKE THE BREEZY (5.10) VERSION!

Instead, try to use the Hoary (4.10) or Warty (5.04, I'm not sure, You must verify the kernel)

---

### Post by Christopher on 2006-03-14
I also have an Asus P4C800-E Deluxe, my bios version is 1016 and I have no issues with Fedora Core 4. Im going to install Ubuntu 5.10 and let you know how it goes.

---

### Post by Christopher on 2006-03-15
Ok Clefferson, I just installed Ubuntu v5.10 on my Asus P4C800-E Deluxe with bios version 1016 with no problems. Im also using the NEWEST kernel.

---

### Post by Clefferson on 2006-03-22
...indeed... it was on a P4_**C**_800... you lucky guy..  


After four days seeking more information over the Internet, I finally have a clue!

The problem comes from all kernels above 2.6.10.* ](*,)

To be moke precise, it comes from ubuntu **skge.ko** module bundled with those kernels.This module are supposed to handle Marvell based NICs, included the 3Com Gigabit LOM (3C940), embedded in ASUS P4P800 Motherboard.

_** So.... here's my solution for this... and it works!**_

1.   Bios SETUP (Bios version: 1019 and above)[LIST]
[*]Main > IDE Configuration >[LIST]
[*]Onboard IDE Operate Mode: Compatible Mode   *(otherwise, grub can't be installed, or no CD-ROM detected on reboot)*[/LIST] 
[*]Power >[LIST]
[*]ACPI 2.0 Support : Yes
[*]ACPI APIC Support: Enabled
[*]BIOS-->AML ACPI Table: Enabled[/LIST] [/LIST]2.   Install Hoary version...

3.   Stay calm, don't worry, Hoary works well... :-?

4.   Don't ever try to upgrade to breezy... at least for now... pehaps Dapper will handle the problem...

5.   If you fell having an adventurer soul, try to compile your own Kernel... based on 2.6.12.* or above... **BUT AT YOUR OWN RISKS**! :twisted: 

Lot's of dependencies problems comes after. Pehaps if you can find a way to reconfigure kernel's name AND *.deb* package to fits the ubuntu name and replace it....[INDENT]For recompiling the kernel... [this is a good start]("https://wiki.ubuntu.com/KernelCompileHowto").
[/INDENT][INDENT]Anyway, you'll need to change the skge source to have your network card detected. I've joined the DIFF file, or you can look at [this]("http://sources.gentoo.org/viewcvs.py/linux-patches/genpatches-2.6/tags/2.6.13-1/2105_skge-sensor-interrupts.patch?rev=153")
[/INDENT]6.   If none of the solutions above helps to enlighten your path, run to the nearest computer shop, buy a Intel Chipset based motherboard, and install Breezy....:mrgreen:

[CENTER][B]Good Luck!



[/B] [/CENTER]

---

### Post by steelgrave on 2006-03-23
got ubuntu on p4s800d with latest bios
works fine/

---

### Post by Remillard on 2006-04-08
Thanks for the information.  I'll give this a shot and see if I can't get some form of Ubuntu running on my machine.  I did not have any of the acpi troules, but that skge driver is seriously buggy.

Best regards,
Remillard

---

### Post by alxarch on 2006-05-30
i have the same problems with my asus p4p800...
i don't know i'm just a noob in linux but has anyone trying disabling the onboard NIC to try to solve the problem?(if that's what's incompatible with the 2.6.10 kernel....) i have only manged to install and run through compatible mode but i really want to use all my ide channels:(  if i turn it to compatible mode in order to install and then, after the install i turn the enchanched mode back on it falls into a sort of irq conflict while booting and never gets to boot eventually. but is it possible that the conflict is due to the NIC?

---

### Post by subtler on 2006-05-31
I have a p4p800-SE in mine and breezy loves it.

---

