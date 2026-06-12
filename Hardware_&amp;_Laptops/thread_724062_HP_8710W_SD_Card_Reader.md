---
title: "HP 8710W SD Card Reader"
date: 2008-03-14
forum: Hardware &amp; Laptops
---

### Post by tobie.de.beer on 2008-03-14
Hi,

I have a problem getting my SD ( and other ) card reader running under ubuntu ( and all other distro's I tried including hardy alpha 4 and PCLinuxOS) this is on a HP 8710W

the hardware seems to be recognized but if you put in an SD card nothing happens. after about 10 minutes DMESG report that IRQ #19 is being cancelled due to noboy caring.

I've googled and tried everying i could get my hands on - mostly setpci type stuff - none worked for me

Also tried pollirq and acpi_use_timer_override boot options that I found.

Does anyone have som advice?

Thanks
Tobie

I don't have the lspci output with me, but it is something similar to:
02:06.3 ....... Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adaptor

parts of DMESG:

[   13.500000] Yenta: CardBus bridge found at 0000:02:06.1 [103c:30c3]
[   13.608000] sdhci: Secure Digital Host Controller Interface driver
[   13.608000] sdhci: Copyright(c) Pierre Ossman
[   13.624000] iwl4965: Intel(R) Wireless WiFi Link 4965AGN driver for Linux, 1.1.0

-------

[   13.632000] pcmcia: parent PCI bridge Memory window: 0x80000000 - 0x87ffffff
[   13.632000] sdhci: SDHCI controller found at 0000:02:06.3 [1180:0822] (rev 20)
[   13.632000] ACPI: PCI Interrupt 0000:02:06.3[B] -> GSI 19 (level, low) -> IRQ 19
[   13.632000] mmc0: SDHCI at 0xe4103000 irq 19 DMA
[   13.632000] ACPI: PCI Interrupt 0000:10:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   13.632000] PCI: Setting latency timer of device 0000:10:00.0 to 64

-------

[  836.664000] irq 19: nobody cared (try booting with the "irqpoll" option)
[  836.664000]  [<c015b5b4>] __report_bad_irq+0x24/0x80
[  836.664000]  [<c015b872>] note_interrupt+0x262/0x2a0
[  836.664000]  [<c015aad0>] handle_IRQ_event+0x30/0x60
[  836.664000]  [<c015c25b>] handle_fasteoi_irq+0xbb/0xf0
[  836.664000]  [<c0106b1b>] do_IRQ+0x3b/0x70
[  836.664000]  [<c013eb4b>] enqueue_hrtimer+0x6b/0x110
[  836.664000]  [<c0105223>] common_interrupt+0x23/0x30
[  836.664000]  [<f886699a>] acpi_processor_idle+0x24f/0x425 [processor]
[  836.664000]  [<f886674b>] acpi_processor_idle+0x0/0x425 [processor]
[  836.664000]  [<c0102413>] cpu_idle+0x53/0xe0
[  836.664000]  [<c03e3a85>] start_kernel+0x325/0x3b0
[  836.664000]  [<c03e31f0>] unknown_bootoption+0x0/0x260
[  836.664000]  =======================
[  836.664000] handlers:
[  836.664000] [<f8a488e0>] (yenta_interrupt+0x0/0xe0 [yenta_socket])
[  836.664000] [<f8a9aae0>] (sdhci_irq+0x0/0x550 [sdhci])
[  836.664000] Disabling IRQ #19

---

### Post by GoingDown on 2008-04-03
Same here. I am having exactly same symptoms, nobody cared irq 22 in my case.

HP Compaq 8510w with Ricoh R5C822. And it does not work.

---

### Post by octesian on 2008-04-05
I have a Ricoh r5c822 card reader on my inspiron 1420n and I don't know how to get it to work either.

---

### Post by apedraza on 2008-05-07
Same situation here.  HP8710w. The SD card reader does not work.

The driver seems to be loaded properly and is reporting interrupt 19.

02:06.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b9)
02:06.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b9)
02:06.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 03)
02:06.3 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 20)
02:06.4 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 10)
02:06.5 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 10)
02:06.6 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 10)

I have tried the set pci stuff to no avail.

If anyone has any advice, I will appreciate the help.

Thanks in advance.

---

### Post by phelge on 2008-05-18
Same laptop (8710w) and same problem.

I tried sdricoh_cs-0.1.3 module both as a DEB package and by compiling source (as indicated in an other thread) with no success.

---

### Post by SKiDRoX on 2008-05-20
Same problem here on HP 6910p ...

02:06.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b9)
02:06.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b9)
02:06.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 03)
02:06.3 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 20)
02:06.4 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 10)

Thanks!

---

### Post by GoingDown on 2008-05-21
I got it working finally by upgrading kernel to vanilla 2.6.25.4!

Running Arch Linux on Compaq 8510w, but as mentioned previously, just the same symptoms that others are seeing - no detection of MMC or SD cards when inserted, nothing gets printed to logs, and after 10 minutes "irq nobody cared"...

---

### Post by eckz59 on 2008-06-15
> **GoingDown said:**
> I got it working finally by upgrading kernel to vanilla 2.6.25.4!

Running Arch Linux on Compaq 8510w, but as mentioned previously, just the same symptoms that others are seeing - no detection of MMC or SD cards when inserted, nothing gets printed to logs, and after 10 minutes "irq nobody cared"...
Hi... I'm new to Ubuntu (actually, to Linux in general) and I have this same problem with my 8510W. Can you please tell me how to upgrade my kernel to the correct one? I am having trouble finding the correct commands to enter into the terminal. Here is the output of uname -r :

2.6.24-18-generic

I am using 8.04 Hardy Heron. Thanks for your help!

---

### Post by GoingDown on 2008-06-15
> **eckz59 said:**
> Can you please tell me how to upgrade my kernel to the correct one? I am having trouble finding the correct commands to enter into the terminal. Here is the output of uname -r :

2.6.24-18-generic

I am using 8.04 Hardy Heron. Thanks for your help!

Take a look following guide:
[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

Note that you can download vanilla 2.6.25.x kernel from [http://www.kernel.org](http://www.kernel.org) (I am not sure if Ubuntu development kernel is 2.6.24 or 2.6.25).

More documentation:
[http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

Just find a way which suits you best.

---

### Post by tobie.de.beer on 2008-07-16
Thanks guys, 

Mine (8710W) also works with 2.6.25.6. had to install nVidia manually from nvidia d/l afterwards.

Thanks
T

---

