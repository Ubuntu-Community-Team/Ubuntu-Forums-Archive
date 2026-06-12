---
title: "Req. help arguing case to Gigabyte"
date: 2007-04-20
forum: Hardware &amp; Laptops
---

### Post by calraith on 2007-04-20
I have an odd request to ask of you guys.  I need advice on how to make my case to Gigabyte that I have a faulty BIOS, or at least confirmation from outside Gigabyte that my computer has a faulty user.  So far I'm not doing terribly well on my own of convincing either party.

I have a Gigabyte GA-M57SLI-S4 motherboard I bought in January.  I get a kernel panic during APIC configuration during bootup unless I pass either "noapic" or "acpi_use_timer_override" on the kernel line in GRUB or LILO.  Apparently this is due to a bug in the interrupt overrides in the ACPI tables, which was recognized and fixed by NVIDIA years ago, but which perpetually gets recycled into new BIOSes over and over for only heaven knows what reasons.

Well, read the conversation:

[FONT=Arial, Helvetica, sans-serif][COLOR=#0042ab]**Question** - 465238[/COLOR][/FONT][INDENT] APIC doesn't work on my board in Linux. I apologize, but I know nothing about BIOS hacking. However, a forum I frequent provided a bit of information that might be relevant. Apparently nForce boards commonly implement timer overrides incorrectly unless they support HPET. Does this make sense? If I boot without passing the kernel param "noapic" I get the following output:

Enabling IO-APIC IRQs
... TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
... MP-BIOS bug: 8254 timer not connected to IO-APIC
... trying to set up timer (IRQ0) through the 8259A... failed.
... trying to set up timer as Virtual Wire IRQ... failed.
... trying to set up timer as ExtINT IRQ... failed :(.
Kernel panic - not syncing: IO-APIC + timer doesn't work!  Boot
with apic=debug and send a report.  Then try booting with the
'noapic' option.

The gentleman also pasted me some kernel code that he said he provided Gigabyte when he encountered a similar problem with his nForce board, which he asserted helped your hackers to fix his BIOS. Have a look at [http://ubuntuforums.org/showthread.php?p=2470372](http://ubuntuforums.org/showthread.php?p=2470372) comment #16 if it'd be relevant
Thanks!
Steve


-------------------------------------------------------------------------------
**Model Name** : GA-M57SLI-S4(rev. 1.1)
--------------------------
**M/B Rev** : 1.1
**BIOS Ver** : F8
**Serial No.** : 
**Purchase Dealer** : 
-------------------------------------------------------------------------------
**VGA Brand** : GIGABYTE      **Model** : GeForce 7300 GS x2
**CPU Brand** : AMD      **Model** : Athlon64 x2 65W      **Speed** : 4200 (2.2GHz)
**Operation System** : Linux      **SP** : 
**Memory Brand** : Corsair      **Type** : DDRII
**Memory Size** : 2x512      **Speed** : 800
**Power Supply** : 450 W
[/INDENT][FONT=Arial, Helvetica, sans-serif][COLOR=#0042ab]**Answer** - 465238
[/COLOR][/FONT][INDENT]This board is acpi comliant, any issue when attempting to test under Windows based?
[/INDENT][FONT=Arial, Helvetica, sans-serif][COLOR=#0042ab]**Question** - 466000
[/COLOR][/FONT][INDENT]No errors in Windows that I've encountered so far, but every Linux distro I've tried -- Gentoo, Debian, OpenSUSE, Knoppix and Ubuntu, have required that I pass either "noapic" or "acpi_use_timer_override" on the kernel string in LILO or GRUB, from every kernel version between 2.6.15 - 2.6.20 (current).

According to some British guy on the Ubuntu forums, the problem is common among older nForce boards, as he states:

"...because of a dodgy hack that is no longer necessary. I game [sic] them that code and they gave me a fixed bios within 2/3 days (beta) and added the fixes to the official bios 2 releases later. "

The code he pasted me, I believe, is part of a kernel patch that, as Allen Martin of LKML.org says, is a workaround to "fix incorrect entries in the BIOS ACPI tables. This bug existed in the NVIDIA reference BIOS for nForce2 and got copied to all customer BIOSes for nForce2. Even though our reference BIOSes and documentation for all chipsets since then have the correct interrupt overrides in the ACPI tables we still see customer BIOSes that get shipped with incorrect entries that were probably copied from their nForce2 BIOS code." Evidence suggests the BIOS for the GA-M57SLI-S4 can be included in Mr. Martin's assertion. Anyway, patch code follows:

{{{

#ifdef CONFIG_ACPI
/* According to Nvidia all timer overrides are bogus unless HPET
is enabled. */
if (!acpi_use_timer_override && vendor == PCI_VENDOR_ID_NVIDIA) {
nvidia_hpet_detected = 0;
acpi_table_parse(ACPI_HPET, nvidia_hpet_check);
if (nvidia_hpet_detected == 0) {
acpi_skip_timer_override = 1;
printk(KERN_INFO "Nvidia board "
"detected. Ignoring ACPI "
"timer override.\n");
printk(KERN_INFO "If you got timer trouble "
"try acpi_use_timer_override\n");

}
}
#endif

}}}


/* end code */

I'm having some other issues which may or may not be related to having APIC disabled at startup. Most notably, I get some funky stack traces and a process goes zombie whenever I try to use the processor instruction sets for hardware virtualization, such as those used by kvm, and I think VMware.

VMware Player freezes on init in Linux. With Windows as the host OS and Windows as guest, the VM crawls, even with guest tools installed. Granted, the host is Vista and I only have a gig of RAM, so that's hardly conclusive, I know; but the extreme latency still persists even with all eye candy, UAC, Windows Defender, and as much other garbage turned off as possible, making Vista behave as closely to Windows 2000 as possible.

Anyway, to rule out various issues, I'm hoping for a BIOS that doesn't require the hackish, outdated workarounds appropriate to nForce2 era boards -- one that properly implements a high precision event timer and correct ACPI tables. If you Google the words "apic acpi bug" you'll find more anecdotal evidence of this bug.

Does all this make sense? I'm not sure it all makes sense to me. The only thing I can say for sure is that there's a bug in my BIOS.
[/INDENT][FONT=Arial, Helvetica, sans-serif][COLOR=#0042ab]**Answer** - 466000
[/COLOR][/FONT][INDENT]Since there are o drivers available for Linux that may be the issue.
Did you checked with Nvidia for further assistant regarding drivers under Linux?
[/INDENT][FONT=Arial, Helvetica, sans-serif][COLOR=#0042ab]**Question** - 466315
[/COLOR][/FONT][INDENT]Even though Gigabyte doesn't supply drivers, support for Nvidia chipsets is built into the Linux kernel directly. If there were no drivers available for Linux, then I would not be able to get sound from my speakers, connect via ethernet, or even probe USB devices, all of which I have no trouble doing.

All this is irrelevant. Availability of drivers is irrelevant. Without "noapic" or "acpi_use_timer_override," the kernel panic happens prior to userspace module loading anyway. Are you 100% certain that there are no flaws in the BIOS for GA-M57SLI-S4 regarding the ACPI tables? If so, then how do you know?

Listen, we're moving backwards here.  We're way past the reboot-and-see-whether-that-fixes-the-problem stage.
[/INDENT][FONT=Arial, Helvetica, sans-serif][COLOR=#0042ab]**Answer** - 466315
[/COLOR][/FONT][INDENT]There are no known issue with it, if there were Windows based should have the same issue.
How many different versions of Linux did you tried testing with?
[/INDENT][FONT=Arial, Helvetica, sans-serif][COLOR=#0042ab]**Question** - 466373
[/COLOR][/FONT][INDENT]Not necessarily. Windows didn't have problems with the nForce2 that I recall, but that's where the faulty interrupt overrides in the ACPI tables first originated. I suspect that, as the Linux kernel development team has speculated (see the Allen Martin quotation in my second e-mail), the faulty ACPI interrupt overrides have been recycled into this board's BIOS from the faulty reference nForce2 BIOS provided by Nvidia years ago. Can you verify the origins of the interrupt overrides in the ACPI tables in my motherboard's BIOS? Did they come from an nForce 570 reference BIOS, or is it possible that that particular part of the BIOS has been recycled from, say, the nForce 550, which had code recycled from its predecessor, and so on and so forth?

As I mentioned in my second e-mail, I've tried Gentoo, Debian, OpenSUSE, Knoppix and Ubuntu, on kernels 2.6.15, 2.6.16, 2.6.17, and 2.6.20. (I skipped 2.6.18 and 2.6.19.)[/INDENT]So that's the conversation so far.  Am I going about this the wrong way?  Can anyone provide any more information about this bug that might help me intelligently argue my case that this BIOS is buggy?  Or do you agree with the Gigabyte techs, and think there's a nut loose on my keyboard?  (1-d-10-t, pebcak, whatever)

---

### Post by Xen2oo6 on 2007-07-16
I have a GA-M55S-S3 (nForce 550) Board with the same bug. But only with Bios-Version FC and FD. Now i use the FB-Version and everyhing works great. The FB is the only one i can enable/disable the HPET support....

I really hope Gigabyte fix this bug :(

---

### Post by Matt 6:27 on 2007-09-15
I just upgraded from an old AMD 800 Mhz Thunderbird based system to a new rig with specs listed in my sig line.  The MB is the Gigabyte GA-M57SLI-S4 _Rev. 2.0_.  So far, EVERYTHING has worked out of the box and without the noapic problem rearing its ugly head.  I had planned on addressing this issue once I finished the build, but as I said, she fired up without a problem and has been running for a couple weeks.  Maybe Gigabyte got their !@#% together and fixed this?   =D>

---

