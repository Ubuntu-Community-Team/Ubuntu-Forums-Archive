---
title: "Trouble booting PC"
date: 2008-04-17
forum: Hardware &amp; Laptops
---

### Post by bearrider on 2008-04-17
Hi,

I picked up an old PC with a pentium 533MHz processor and upgraded it with the following :

80GB IDE HDD, 1 GB RAM and an LG 20x DVD combo drive. I have set the BIOS boot sequence to the DVD drive.

Now I try to boot up with an Ubuntu live CD in the drive but the system always stops at this point (shown below). Doesn't go further. 

Any ideas why? Is there anyway I can get more info? A log file somewhere, for example. Thanks.


-------


Award Medallion BIOS v6.0, An Energy Star Ally
Copyright (c) 1984-2000, Award Software, Inc.

ASUS P3B-F ACPI BIOS Revision 1005

Intel (R) Pentium(R) III 500 MHz Processor
Memory Test :  1048576K OK

Award Plug and Play BIOS Extension v1.0A
Initialize Plug and Play Cards...
PNP Init Completed

Trend ChipAwayVirus(R) On Guard

Detecting Primary Master ... ST380215A
Detecting Primary Slave  ... HL-DT-STDVD-RAM GSA-H55N
Detecting Secondary Master ... SAMSUNG SC-148B
Detecting Secondary Master ... LG CD-RW CED-8083B

- <the cursor just stays here blinking...>

---

### Post by Sef on 2008-04-17
Have you checked the cd for errors?  Instead of booting into Ubuntu, go down the list to Check Disc for Errors o something similar.

---

### Post by bearrider on 2008-04-17
It never reads the live CD. 

I'm still at the command prompt when this shows up 

Trend ChipAwayVirus(R) On Guard

Detecting Primary Master ... ST380215A
Detecting Primary Slave ... HL-DT-STDVD-RAM GSA-H55N
Detecting Secondary Master ... SAMSUNG SC-148B
Detecting Secondary Master ... LG CD-RW CED-8083B

and then stops...

So there is no question of Ubuntu CD being read. I'm stuck at the pre boot process.

---

### Post by prshah on 2008-04-17
> **bearrider said:**
> Hi,
I picked up an old PC with a [color=red]pentium 533MHz [/color]processor and upgraded it with the following :

Intel (R) Pentium(R) III [color=red]500 MHz [/color]Processor
Memory Test :  1048576K OK



A quick solution that MAY work; get into the BIOS, and choose "Load BIOS defaults", then save and exit it. If it works, you can always come back and make the changes you want (Eg, boot order, date/time, PnP, etc).

You say the processor is a 533 Mhz but the BIOS detects it as 500Mhz.. 

The board mentioned is a BX chipset board, with FSB speeds from 66~150 Mhz. The 533 processor is a 66 FSB * 8 multiplier to get 533 Mhz. But maybe your board is running it as 100 FSB * 5 (=500 Mhz), which is why it is hanging... maybe?

This an old type "jumper-setting" board, but it also has a "jumper-free" setup i the BIOS. Maybe you can download the manual from somewhere and figure out how to set the CPU speed from the BIOS rather than the board's jumpers.

You could also try upgrading the BIOS; a BIOS upgrade gone bad would also sometimes display these results.

On a more mundane but immediately fixable level, you can check if the CMOS battery (3v, CR2032) is still good with a cheapo digital multimeter. Any voltage above 2.5v is OK.

Hope anyone of these tips leads you in the right direction.

---

### Post by bearrider on 2008-05-07
thanks for your tips, what i had to do was upgrade the BIOS.

sorry i probably should have mentioned this earlier, i had upgraded to a 80GB hard drive which is not supported by the motherboard.

---

