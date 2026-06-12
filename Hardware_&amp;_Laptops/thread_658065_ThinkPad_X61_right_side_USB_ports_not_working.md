---
title: "ThinkPad X61 right side USB ports not working"
date: 2008-01-04
forum: Hardware &amp; Laptops
---

### Post by johj on 2008-01-04
Hello,

I've got Gutsy installed on my ThinkPad X61. It has 3 USB2.0 ports, one on the left side and two on the right. The only one which actually works is the one on the left side. If I plug any USB device into any of the two ports on the right side, they receive power but they never get detected by the kernel - nothing in dmesg at all indicates these ports are even recognized. I've wondered whether this might be a hardware problem, but I've seen [others with similar problems]("http://ubuntuforums.org/showthread.php?t=529552"). How can I debug this further? I will try to create a windows live cd and post the results here.

lsusb output:
> $ lsusb
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 009: ID 0984:0066 Apricorn 
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 007: ID 0a5c:2110 Broadcom Corp. 
Bus 001 Device 006: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 001 Device 001: ID 0000:0000

Please let me know of there is anything else who could provide useful in debugging this.

Thanks,

---

### Post by johj on 2008-01-04
I just rebooted the laptop and discovered that the two USB ports now work - my guess is that they won't work after suspend for some reason. Will check soon :)

---

### Post by johj on 2008-01-04
> [41101.200000] irq 20: nobody cared (try booting with the "irqpoll" option)
[41101.200000]  [<c015b594>] __report_bad_irq+0x24/0x80
[41101.200000]  [<c0143108>] clockevents_program_event+0x88/0x100
[41101.200000]  [<c015b852>] note_interrupt+0x262/0x2a0
[41101.200000]  [<f88af6c2>] usb_hcd_irq+0x22/0x60 [usbcore]
[41101.200000]  [<c015aab0>] handle_IRQ_event+0x30/0x60
[41101.200000]  [<c015c23b>] handle_fasteoi_irq+0xbb/0xf0
[41101.200000]  [<c0106b1b>] do_IRQ+0x3b/0x70
[41101.200000]  [<c0105223>] common_interrupt+0x23/0x30
[41101.200000]  [<c013007b>] sys_capset+0x12b/0x2e0
[41101.200000]  [<f886099a>] acpi_processor_idle+0x24f/0x425 [processor]
[41101.200000]  [<f886074b>] acpi_processor_idle+0x0/0x425 [processor]
[41101.200000]  [<c0102413>] cpu_idle+0x53/0xe0
[41101.200000]  =======================
[41101.200000] handlers:
[41101.200000] [<f88af6a0>] (usb_hcd_irq+0x0/0x60 [usbcore])
[41101.200000] Disabling IRQ #20

I think I've found the reason they're not working ... nobody cared! :(

---

### Post by mbsullivan on 2008-01-06
Hi All,

I, too, have had this problem with my x61 for some time... however, seeing as my laziness knows no bounds, I've just used the USB port on the left side of the laptop. If you must have the USB ports on the right side, however, I believe the following may solve your problem (solution found [here]("http://ubuntuforums.org/showthread.php?t=635977")):

Add "irqfixup" to the boot options for your kernel.  Assuming you're using GRUB as your bootloader, this entails editing /boot/grub/menu.lst.  

If you're as lazy as me, the whole process should be accomplished through the following commands:

```
sudo sed -i.bak -e 's/\(^# kopt=.*$\)/\1 irqfixup/g' /boot/grub/menu.lst && sudo update-grub
```

Let me know if you have any problems. Hope this helps!
Mike

P.S. - Reposted [for similar problem]("http://ubuntuforums.org/showthread.php?p=4083012&posted=1#post4083012").

---

### Post by johj on 2008-01-06
Interesting, although I'm not sure we're having the same problem.

The problem I'm having with my ThinkPad is actually a bug in the ThinkPad BIOS which causes a lot of unexpected interrupts to occur from the USB controller. See [kernel bug #8853]("http://bugzilla.kernel.org/show_bug.cgi?id=8853"). Lenovo has released a [BIOS update for the T61]("http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=MIGR-67989#changes") but not yet for the X61 it seems.

---

### Post by mbsullivan on 2008-01-06
Have you tried it?  It's made to [handle firmware interrupt problems]("http://www.linuxtopia.org/online_books/linux_kernel/kernel_configuration/re16.html"), such as  yours.

Mike

---

### Post by aroman1 on 2008-01-07
I had the same problem with my X61 tablet. Adding irqfixup to the kernel arguments fixed it.

Thank you,
Angel

---

### Post by johj on 2008-01-08
> **mbsullivan said:**
> Have you tried it?  It's made to [handle firmware interrupt problems]("http://www.linuxtopia.org/online_books/linux_kernel/kernel_configuration/re16.html"), such as  yours.

Mike

Yeah, I added the option right after you posted about it and I haven't had any problems so far :D Great! Thanks a lot.

---

### Post by s1m0n13 on 2008-01-24
> **johj said:**
> Interesting, although I'm not sure we're having the same problem.

The problem I'm having with my ThinkPad is actually a bug in the ThinkPad BIOS which causes a lot of unexpected interrupts to occur from the USB controller. See [kernel bug #8853]("http://bugzilla.kernel.org/show_bug.cgi?id=8853"). Lenovo has released a [BIOS update for the T61]("http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=MIGR-67989#changes") but not yet for the X61 it seems.

The BIOS upgrade noted by johj did the trick for me. 

I also tried adding the "irqfixup" to grub before I updated the BIOS. This also worked but it seemed to have a negative affect on my track mouse.  My suggestion would be to stick to the BIOS upgrade.

---

### Post by vakond1 on 2008-05-17
I had similar problems with my R61 14.1" widescreen laptop. I applied the irqfixup patch mentioned earlier in the thread, but that stopped the hibernate to memory function to work, so I updated my BIOS to the newest version avaliable, and I removed the irqfixup patch, now everything seems to work.

---

