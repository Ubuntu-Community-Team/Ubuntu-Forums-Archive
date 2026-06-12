---
title: "Ubuntu 11.04 64bit constantly crashing on Toshiba Tecra A11-110"
date: 2011-06-02
forum: Hardware
---

### Post by Antonio Tavares on 2011-06-02
Hi!
Ubuntu 11.04 64bit is constantly crashing on Toshiba Tecra A11-110. Sometimes it's just the gui restarting (I'm using Ubuntu classic - Unity is unproductive). Other times it's freezing and I have to reboot on power button. More rarely it spares me the time to press the button and it just reboots. This was happening several times a week, but now it's several times an hour, and I'm writing this message on Windows 7 (no problem until now). I don't want to continue on Windows, because I'm not a gammer - I need to work.
This reboots are random (any time, any program) and I can't see anything on dmesg log at the moment previous to the crash. dmesg has a lot of messages concerning ACPI errors on boot. But it doesn't crash there.
I've tested RAM for 2 hours and it showed no errors. Ubuntu is fully upgraded. I've done filesystem check on my ext4 partition and no problem.
- What can I do to discover the origin of this problem?
- In general, how can we sort-out this kind of random errors?
Thank you for your help.

---

### Post by sanguinoso on 2011-06-02
What graphics card are you using? I have heard claims that a significant portion of crashes like this are due to graphics

---

### Post by Antonio Tavares on 2011-06-02
> **sanguinoso said:**
> What graphics card are you using? I have heard claims that a significant portion of crashes like this are due to graphics

It's the one included on core i5 "Intel® QM57 Express Chipset com Intel® Graphics Media Accelerator HD "([http://pt.computers.toshiba-europe.com/innovation/jsp/SUPPORTSECTION/discontinuedProductPage.do?service=PT&toshibaShop=false&com.broadvision.session.new=Yes&PRODUCT_ID=1082149&BV_Script=/jsp/fixup/productPage](http://pt.computers.toshiba-europe.com/innovation/jsp/SUPPORTSECTION/discontinuedProductPage.do?service=PT&toshibaShop=false&com.broadvision.session.new=Yes&PRODUCT_ID=1082149&BV_Script=/jsp/fixup/productPage))

---

### Post by Antonio Tavares on 2011-06-02
Update: I've just came back from a nasty blue screen on Windows - as I suspected: I've never seen Linux crashing constantly except if it's an hardware problem. Now that for the first time I'm using Windows for more than an hour it fails also.
Now: What part of the hardware is failing? That's the difficult question...

---

### Post by Jack Brown on 2011-06-02
Hi Antonio,

Are you monitoring the hardware temperatures right before the crash?  (CPU, video, hard drive...)

Also have you checked if you are affected by Intel Sandy Bridge circuit design issue?  (they issued a recall for this)

[http://www.intel.com/consumer/products/processors/chipset.htm](http://www.intel.com/consumer/products/processors/chipset.htm)

or google Sandy Bridge Recall at intel.com

---

### Post by Jack Brown on 2011-06-02
also when your notebook pc gets hot, do the fans run?

you can also try running memtest overnight to be really sure there are no errors in your memory.


another thing you can try (if you have run out of less drastic solutions) is to upgrade the bios, if toshiba has a more updated one for your notebook.

another path would be to reformat the hard drive and see if that fixes the issue.

this has a big chance of taking a lot of your time.  choose your path and work diligently towards fixing the issue.  get a temporary replacement work computer, and then you can work at fixing the laptop on your spare time as a hobby.

edit: keep ruling out possible causes to get at the real cause.  You could try running on a LiveCD and let it stay ON overnight and see if it crashes. 
YOu can check ubuntu's disk utility and see if your hard drive has problems.

---

### Post by Antonio Tavares on 2011-06-02
Thanks for your help.

The computer was always very noisy as soon as the CPU starts working so it's not the fans. The sensors are giving me this now:
```
sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +41.0°C  (crit = +107.0°C)
```
So it's not overheating.

I upgraded the BIOS, but no difference, and I still see ACPI errors on dmesg:
```
[    4.002076] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    4.003849] ACPI Error (psargs-0359): [GTF1] Namespace lookup failure, AE_NOT_FOUND
[    4.003853] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.SAT0.PRT1._SDD] (Node f702bc00), AE_NOT_FOUND
[    4.003901] ACPI Error (psargs-0359): [GTF1] Namespace lookup failure, AE_NOT_FOUND
[    4.003904] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.SAT0.PRT1._GTF] (Node f702bc18), AE_NOT_FOUND
[    4.003935] ata2.00: ATAPI: MATSHITADVD-RAM UJ890AS, 1.00, max UDMA/100
[    4.006371] ACPI Error (psargs-0359): [GTF1] Namespace lookup failure, AE_NOT_FOUND
[    4.006375] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.SAT0.PRT1._SDD] (Node f702bc00), AE_NOT_FOUND
[    4.006414] ACPI Error (psargs-0359): [GTF1] Namespace lookup failure, AE_NOT_FOUND
[    4.006417] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.SAT0.PRT1._GTF] (Node f702bc18), AE_NOT_FOUND
[    4.006459] ata2.00: configured for UDMA/100
[    4.024960] scsi 1:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ890AS  1.00 PQ: 0 ANSI: 5
```


Just to be sure, I've removed the hard disk and started from CD. No crash until now, but I'll leave it on overnight just to test.

Tomorrow I'll put another hard disk on it just to check, and I'll report later.

---

### Post by Antonio Tavares on 2011-06-03
I've just seated in front of my computer. Surprisingly it was running well after 15 hours non stop!

There's a new message repeated several times on log:
intel ips 0000:00:1f.6: MCP power or thermal limit exceeded

But it's cool and running well anyway (41ºC).

The difference? Now it has no hard disk.
I've connected the same disk through USB. It didn't break the system.

I've checked the link you gave me ([http://www.intel.com/consumer/products/processors/chipset.htm](http://www.intel.com/consumer/products/processors/chipset.htm)) and there's something interesting:
> On January 31, 2011, Intel disclosed a design issue with a support chip, Intel® 6 Series Express Chipset, indicating that under normal operation the chipset could experience an issue with integrated SATA ports 2&#8211;5 that may result in these SATA ports experiencing a functional issue over time. 

lspci shows me:
```
SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 06)
```

It's not series 6, but... the key part is "over time" - For me the mystery is solved. It must be an issue with the SATA controller.

Mr. Jack Brown you were very helpful! Thank you very much for your help.
I'm sending this computer to a Toshiba repair center.

---

