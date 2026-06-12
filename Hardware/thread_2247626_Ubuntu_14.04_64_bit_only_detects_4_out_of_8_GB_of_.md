---
title: "Ubuntu 14.04 64 bit only detects 4 out of 8 GB of RAM"
date: 2014-10-09
forum: Hardware
---

### Post by Tetrapack on 2014-10-09
So I have a rather weird Problem with Ubuntu 14.04 64 bit (so no easy answers for you): I have 2 x 4 GB of RAM in dual channel mode. The BIOS always correctly detects all 8 GB and when I start my computer Ubuntu also shows 7.8 GiB (Only seems to happen after the computer was turned off for some time). However after a few minutes it usually either freezes forcing me to restart the system or more commonly just reboots (certainly not due to overheating). After that the BIOS still sees 8 GB but Ubuntu only 4 GB (System info, System monitor and the free -m command all show 3.8 GiB of total RAM). Is this a software problem or just defective RAM? Also are there any additional tests I should run?

Output of the "sudo lshw -class memory" command (Ubuntu was detecting 4 GB of memory at that time. Would it help if I posted an output with 8 GB being detected right after startup):

```
  *-firmware              
       description: BIOS
       vendor: American Megatrends Inc.
       physical id: 0
       version: F1
       date: 04/08/2013
       size: 64KiB
       capacity: 4032KiB
       capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification uefi
  *-cache:0
       description: L1 cache
       physical id: 5
       slot: L1-Cache
       size: 288KiB
       capacity: 288KiB
       clock: 1GHz (1.0ns)
       capabilities: pipeline-burst internal write-back unified
  *-cache:1
       description: L2 cache
       physical id: 6
       slot: L2-Cache
       size: 6MiB
       capacity: 6MiB
       clock: 1GHz (1.0ns)
       capabilities: pipeline-burst internal write-back unified
  *-cache:2
       description: L3 cache
       physical id: 7
       slot: L3-Cache
       size: 8MiB
       capacity: 8MiB
       clock: 1GHz (1.0ns)
       capabilities: pipeline-burst internal write-back unified
  *-memory
       description: System Memory
       physical id: 2c
       slot: System board or motherboard
       size: 8GiB
     *-bank:0
          description: DIMMProject-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>POT-Creation-Date: 2009-10-08 14:02+0200PO-Revision-Date: 2012-02-05 00:26+0000Last-Translator: Andi Chandler <Unknown>Language-Team: English (United Kingdom) <en_GB@li.org>MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2014-07-07 12:12+0000X-Generator: Launchpad (build 17086) Synchronous [empty]
          product: Dimm0_PartNum
          vendor: Dimm0_Manufacturer
          physical id: 0
          serial: Dimm0_SerNum
          slot: Node0_Dimm0
     *-bank:1
          description: DIMM DDR3 Synchronous 800 MHz (1,2 ns)
          product: F3-14900CL9-4
          vendor: Undefined
          physical id: 1
          serial: 00000000
          slot: Node0_Dimm1
          size: 4GiB
          width: 64 bits
          clock: 800MHz (1.2ns)
     *-bank:2
          description: DIMMProject-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>POT-Creation-Date: 2009-10-08 14:02+0200PO-Revision-Date: 2012-02-05 00:26+0000Last-Translator: Andi Chandler <Unknown>Language-Team: English (United Kingdom) <en_GB@li.org>MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2014-07-07 12:12+0000X-Generator: Launchpad (build 17086) Synchronous [empty]
          product: Dimm2_PartNum
          vendor: Dimm2_Manufacturer
          physical id: 2
          serial: Dimm2_SerNum
          slot: Node0_Dimm2
     *-bank:3
          description: DIMM DDR3 Synchronous 800 MHz (1,2 ns)
          product: F3-14900CL9-4
          vendor: Undefined
          physical id: 3
          serial: 00000000
          slot: Node0_Dimm3
          size: 4GiB
          width: 64 bits
          clock: 800MHz (1.2ns)
```

---

### Post by Michael_McKenney on 2014-10-09
You sure you installed 64-bit and not 32-bit?   7.8GB is normal with mapping of RAM on certain boards.  A bad RAM chip should throw and error message.  Memtest64+ can test your RAM.  I would download the ISO version and burn it to a CD.  Then boot the CD and run it outside any OS.  Do a burn test.  It could take 1-2 days to completely test ram 3x.  BIOS shows both sticks.   Try booting a Live Ubuntu CD and seeing what it finds.  I would check to see your chipset is being recognized properly.

---

### Post by Tetrapack on 2014-11-02
Unsure how many passes on Memtest are usually considered sufficient I ran it for 32 passes on default settings and did not find any errors. I assume that disqualifies a defective RAM module as the cause. However it is possible that my motherboard ([GA-970A-DS3P]("http://www.gigabyte.com/products/product-page.aspx?pid=4591#ov")) is not very Linux friendly seeing as I had to perform [this little workaround]("http://ubuntuforums.org/showthread.php?t=2111223&page=4&p=12851568#post12851568") to get it to work with Ubuntu properly. Is there a Memtest-like way to test the chipset?
Sorry for the late response.

---

### Post by MIJ-VI on 2014-11-02
> **Tetrapack said:**
> Unsure how many passes on Memtest are usually considered sufficient I ran it for 32 passes on default settings and did not find any errors. I assume that disqualifies a defective RAM module as the cause. However it is possible that my motherboard ([GA-970A-DS3P]("http://www.gigabyte.com/products/product-page.aspx?pid=4591#ov")) is not very Linux friendly seeing as I had to perform [this little workaround]("http://ubuntuforums.org/showthread.php?t=2111223&page=4&p=12851568#post12851568") to get it to work with Ubuntu properly. Is there a Memtest-like way to test the chipset?
Sorry for the late response.

Is one of these G.Skill sets the one which you are using?
[http://www.gskill.com/en/search?keyword=F3-14900CL9](http://www.gskill.com/en/search?keyword=F3-14900CL9)

Which CPU are you using?

BTW. I've found that **xfce4-terminal** delivers more complete *lshw* results.

---

### Post by Bucky Ball on 2014-11-03
Easiest and quickest? Take one stick out. Boot the machine. Works fine? There's a clue. Take that stick out and put the other one in. Doesn't work? Suspicions confirmed. ;)

That is presuming you have two RAM sticks.

---

### Post by Tetrapack on 2014-11-05
> **MIJ-VI said:**
> Is one of these G.Skill sets the one which you are using?
[http://www.gskill.com/en/search?keyword=F3-14900CL9](http://www.gskill.com/en/search?keyword=F3-14900CL9)

Which CPU are you using?

Ram: G.Skill Sniper 8 GB. [F3-14900CL9D-8GBSR]("http://www.gskill.com/en/product/f3-14900cl9d-8gbsr")
CPU: AMD FX 6300


> **Bucky Ball said:**
> Easiest and quickest? Take one stick out. Boot the machine. Works fine? There's a clue. Take that stick out and put the other one in. Doesn't work? Suspicions confirmed. ;)

Yes I have two sticks but they seem to work on their own. Both of them often cause crashes during and shortly after booting which does not happen if both sticks are plugged in. The problem is that both of them seem to work equally bad with only one module active which leads me to believe that the memory itself is intact.

---

### Post by MIJ-VI on 2014-11-05
> **Tetrapack said:**
> Ram: G.Skill Sniper 8 GB. [F3-14900CL9D-8GBSR]("http://www.gskill.com/en/product/f3-14900cl9d-8gbsr")
CPU: AMD FX 6300


From the QVL of the above link:

> [TABLE="width: 0"]
[TR="class: cola1, bgcolor: #555555"]
[TD="class: white15, colspan: 4, align: left"][COLOR=#FFFFFF][FONT=Arial]
GIGABYTE [IMG]http://www.gskill.com/images/up.png[/IMG][/FONT][/COLOR][/TD]
[TD="width: 11, align: left"][/TD]
[/TR]
[TR="class: colb0, bgcolor: #5C5C5C"]
[TD="width: 9, align: left"][/TD]
[TD="width: 19, align: left"][/TD]
[TD="class: white15, colspan: 3, align: left"][COLOR=#FFFFFF][FONT=Arial]990FX/990X/970 [IMG]http://www.gskill.com/images/up.png[/IMG][/FONT][/COLOR][/TD]
[TD="width: 11, align: left"][/TD]
[/TR]
[TR="class: colc0, bgcolor: #6C6C6C"]
[TD="width: 9, align: left"][/TD]
[TD="width: 19, align: left"][/TD]
[TD="width: 19, align: left"][/TD]
[TD="width: 300, align: left"]GA-990FXA-UD3[/TD]
[TD="align: left"][/TD]
[TD="width: 11, align: left"][/TD]
[/TR]
[TR="class: colc1, bgcolor: #757575"]
[TD="width: 9, align: left"][/TD]
[TD="width: 19, align: left"][/TD]
[TD="width: 19, align: left"][/TD]
[TD="width: 300, align: left"]GA-990FXA-UD5[/TD]
[TD="align: left"][/TD]
[TD="width: 11, align: left"][/TD]
[/TR]
[TR="class: colc0, bgcolor: #6C6C6C"]
[TD="width: 9, align: left"][/TD]
[TD="width: 19, align: left"][/TD]
[TD="width: 19, align: left"][/TD]
[TD="width: 300, align: left"]GA-990FXA-UD7[/TD]
[TD="align: left"][/TD]
[TD="width: 11, align: left"][/TD]
[/TR]
[TR="class: colc1, bgcolor: #757575"]
[TD="width: 9, align: left"][/TD]
[TD="width: 19, align: left"][/TD]
[TD="width: 19, align: left"][/TD]
[TD="width: 300, align: left"]GA-990XA-UD3[/TD]
[TD="align: left"][/TD]
[TD="width: 11, align: left"][/TD]
[/TR]
[TR="class: colb1, bgcolor: #656565"]
[TD="width: 9, align: left"][/TD]
[TD="width: 19, align: left"][/TD]
[TD="class: white15, colspan: 3, align: left"][COLOR=#FFFFFF][FONT=Arial]A55 for Socket FM1 [IMG]http://www.gskill.com/images/dn.png[/IMG][/FONT][/COLOR][/TD]
[/TR]
[/TABLE]


The [GA-970A-DS3P]("http://www.gigabyte.com/products/product-page.aspx?pid=4591#ov") doesn't appear to be supported by that RAM.

---

### Post by Tetrapack on 2014-11-05
So you mean the only solution is to replace the motherboard or the RAM?

---

### Post by MIJ-VI on 2014-11-05
> **Tetrapack said:**
> So you mean the only solution is to replace the motherboard or the RAM?

That would seem to be the most expedient solution. However, perhaps someone at tom'sHARDWARE may have some suggestions for tweaking the RAM's timings to make it work:

Memory - RAM Reviews and Benchmarks - Upgrade Tutorials
[http://www.tomshardware.com/t/memory/](http://www.tomshardware.com/t/memory/)

EDIT; A RAM guru:

Tradesman1's profile - Moderator - Tom's Hardware
[http://www.tomshardware.com/community/profile-1333705.htm](http://www.tomshardware.com/community/profile-1333705.htm)

--

You're not the first one to have problems with the GA-970A-DS3P (rev. 1.0):

GIGABYTE GA-970A-DS3P Problems 
[http://forum.giga-byte.co.uk/index.php/topic,14802.0.html](http://forum.giga-byte.co.uk/index.php/topic,14802.0.html)

There are a number of Kingston DIMMs listed in your motherboard's QVL:

QVL 970A-DS3P.xls - mb_memory_ga-970a-ds3p.pdf
[http://download.gigabyte.us/FileList/Memory/mb_memory_ga-970a-ds3p.pdf](http://download.gigabyte.us/FileList/Memory/mb_memory_ga-970a-ds3p.pdf)

However, my reseach on the 'Net has informed me that it's best to select RAM from the manufacturer's currently recommended DIMMs (due to changes in chip suppliers over time). Unfortunately your motherboard is not listed by Kingston. Here's the closest model:

ValueRAM for Gigabyte GA-970A-UD3P Motherboard
[http://www.kingston.com/us/memory/search?DeviceType=7&Mfr=GIG&Line=GA-970A-UD3P&Model=89814&Description=Kingston_ValueRam_Memory_HyperX_Memory_for_Gigabyte_GA-970A-UD3P_Motherboard](http://www.kingston.com/us/memory/search?DeviceType=7&Mfr=GIG&Line=GA-970A-UD3P&Model=89814&Description=Kingston_ValueRam_Memory_HyperX_Memory_for_Gigabyte_GA-970A-UD3P_Motherboard)

Under this circumstance you may wish to contact Kingston for their recommendations:

Contact Information | Kingston
[http://www.kingston.com/us/company/contacts#tech](http://www.kingston.com/us/company/contacts#tech)

Kingston Technology
[https://www.facebook.com/kingstontechnology](https://www.facebook.com/kingstontechnology)

Whichever DIMMs you get stay with a max. speed of 1600MHz for four DIMM compatibility. Here's why:

DDR3 memory frequency guide 
[http://support.amd.com/en-us/kb-articles/Pages/ddr3memoryfrequencyguide.aspx](http://support.amd.com/en-us/kb-articles/Pages/ddr3memoryfrequencyguide.aspx)

--

My $0.02

A) After investigating UEFI and learning that it is inherently GNU/Linux-hostile (amongst other issues), I decided to buy a couple of used, FX-8350-capable, pre-UEFI-era motherboards in order to preserve the easy-peasy installation process offered by PC-BIOS-based motherboards.

B) I would not have purchased a GA-970A-DS3P (rev. 1.0) because:

1) It is a recent, rev. 1.0 UEFI motherboard which in particular seems prone to misbehaviour.
2) Gigabyte is rather tardy when it comes to offering BIOS / UEFI updates for their motherboards compared to the BIOS / UEFI update diligence exhibited by Asus.
3) Gigabyte AM3+ motherboards do not support ECC RAM whereas a number of Asus' AM3+ 'boards do.
4) Asus' flagship AM3+ motherboards are currently available in rev. 2.0 iterations which have been on the market long enough to have a more established track record.

C) I've bought Kingston ValueRAM for four different systems over the years and so far, so good.

An endorsement of Kingston's QC and a reason to consider an ECC-capable CPU & motherboard combo if you ever decide to use a large amount of RAM:

November 5, 2013 
Advantages of ECC Memory - Puget Custom Computers 
[http://www.pugetsystems.com/labs/articles/Advantages-of-ECC-Memory-520/](http://www.pugetsystems.com/labs/articles/Advantages-of-ECC-Memory-520/)

The use of ECC RAM forms the first line of defence against bit-squatting: 
 
Mar 15, 2013 
Blackhat 2011 - Bit-squatting: DNS Hijacking without exploitation - YouTube 
[http://www.youtube.com/watch?v=_si0FYl_IOA](http://www.youtube.com/watch?v=_si0FYl_IOA)

The FX-series of AM3+ CPUs support ECC but Gigabyte motherboards do not. Here's two currently available top-of-the-line Asus motherboards which do:

Motherboards - M5A99FX PRO R2.0 - ASUS
[http://www.asus.com/Motherboards/M5A99FX_PRO_R20/specifications/](http://www.asus.com/Motherboards/M5A99FX_PRO_R20/specifications/)

ValueRAM for ASUS/ASmobile M5 Motherboard M5A99FX PRO / M5A99FX PRO R2
[http://www.kingston.com/us/memory/search/Default.aspx?DeviceType=7&Mfr=ASU&Line=M5%20Motherboard&Model=81739&Description=Kingston_ValueRam_Memory_HyperX_Memory_for_ASUS/ASmobile_M5_Motherboard_M5A99FX_PRO_/_M5A99FX_PRO_R2](http://www.kingston.com/us/memory/search/Default.aspx?DeviceType=7&Mfr=ASU&Line=M5%20Motherboard&Model=81739&Description=Kingston_ValueRam_Memory_HyperX_Memory_for_ASUS/ASmobile_M5_Motherboard_M5A99FX_PRO_/_M5A99FX_PRO_R2)

The M5A99FX PRO R2.0 employs a socketed BIOS / UEFI chip for which Asus offers a replacement (in case the power goes out during a BIOS / UEFI update):

BIOS Chip for M5 Series Motherboards 
[http://us.estore.asus.com/index.php?l=product_detail&p=3889](http://us.estore.asus.com/index.php?l=product_detail&p=3889)

--

Motherboards - SABERTOOTH 990FX R2.0 - ASUS
[http://www.asus.com/Motherboards/SABERTOOTH_990FX_R20/specifications/](http://www.asus.com/Motherboards/SABERTOOTH_990FX_R20/specifications/)

ValueRAM for ASUS/ASmobile SABERTOOTH Motherboard 990FX R2.0
[http://www.kingston.com/us/memory/search/Default.aspx?DeviceType=7&Mfr=ASU&Line=SABERTOOTH%20Motherboard&Model=85083&Description=Kingston_ValueRam_Memory_HyperX_Memory_for_ASUS/ASmobile_SABERTOOTH_Motherboard_990FX_R2.0](http://www.kingston.com/us/memory/search/Default.aspx?DeviceType=7&Mfr=ASU&Line=SABERTOOTH%20Motherboard&Model=85083&Description=Kingston_ValueRam_Memory_HyperX_Memory_for_ASUS/ASmobile_SABERTOOTH_Motherboard_990FX_R2.0)

The SABERTOOTH 990FX R2.0 employs a socketed BIOS / UEFI chip for which Asus does NOT offer a replacement (I've had this confirmed via an e-mail response from Asus).

BTW. There's also a Gen3 version of this 'board which offered PCIe 3.0. It was quickly discontinued after AMD announced that they would not be supporting PCIe 3.0 on the AM3+ platform.

---

