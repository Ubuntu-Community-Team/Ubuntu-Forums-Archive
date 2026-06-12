---
title: "Help making driver for rocketraid 1520 controler"
date: 2007-08-11
forum: Hardware &amp; Laptops
---

### Post by Sivart832z on 2007-08-11
Hello. I have just downloaded and installed Ubuntu 7.04 and am now trying to get it to recognize my SATA controller so that I can access my files. This is the first time I've ever installed Linux on this computer, and my first experience using it, so I'm entirely clueless about how to do absolutely everything. I've been searching online and in this forum and just can't seem to find anything that works, so I'm hoping I can just start a new thread and get someone to point me in the right direction rather than following instructions that are 2 years old and just getting more frustrated. I'll try and be as descriptive as I can be, and if anyone wants to help me, let me know what else you need to know (and what to type to find it out).

I am using an AMD Athlon XP 2800+ x86 CPU on a Soyo KT400 MB. I have Ubuntu 7.04 (the command 'uname -r' returns '2.6.20-16-generic') installed on a PATA hard disk connected to the primary IDE channel of the motherboard. Ubuntu is booting and running fine as far as I can tell.  I have a HighPoint Rocketraid 1520 PCI SATA controller which I use to connect two SATA drives to my computer. I have been using this controller for over a year and a half with Windows XP where is was detected automatically and worked fine. I have also used an older live CD of Knoppix (I don't remember the exact version and I loaned it out and can't look, but at least 3 years old) and it has always booted successfully and detected my drives on the rocketraid controller automatically and mounted them for my use.

Please note that, although this card can do RAID, I am not using it for RAID. It is simply acting as a SATA controller. Additionally, I am not trying to install Ubuntu to drives attached to this card, and Ubuntu is not running on drives attached to this card. The drives simply contain all of my files.

When I first tried to use the Ubuntu live CD, it would fail while booting with a message about "sbin/modprobe abnormal exit". I discovered through trial and error that if I unplugged both drives (the card supports a total of 2, which I have attached) from the card, Ubuntu would boot successfully. This was true of the Live CD and also true of Ubuntu once I installed it onto the PATA drive on my computer. I have never had to remove the card from the PCI slot, I have just unplugged both drives. Leaving either drive plugged in causes the error.

I have been trying to research this issue all day and just keep getting conflicting information. According to [http://ubuntuforums.org/showthread.php?t=41899&highlight=rocketraid](http://ubuntuforums.org/showthread.php?t=41899&highlight=rocketraid) the card is supported by Ubuntu. According to [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/58189](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/58189) the card isn't supported. Yet, I've had the card automatically detected and used by a 3 year old copy of Linux, and the card itself claims it is supported under Linux, so I can't see why it shouldn't work now.

According to the [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/58189](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/58189) link, it sounded like the crashing I am experiencing when trying to start with the disks attached is due to using the wrong drivers, or something. The link wasn't very clear about how to fix the issue.

This post on the forums ([http://ubuntuforums.org/showthread.php?t=148001&highlight=rocketraid](http://ubuntuforums.org/showthread.php?t=148001&highlight=rocketraid)) seems to include instructions for how to make the correct driver, but I can't seem to make them work regardless of how many things I download and install. I've downloaded the latest 'drivers' from the cards website ([http://www.highpoint-tech.com/USA/bios_rr1520.htm](http://www.highpoint-tech.com/USA/bios_rr1520.htm)) and tried to follow the directions given in that post, but when I get to the 'make' step it just gives my the following response, and never makes the files.

```
gcc -DDRIVER_VERSION=\"2.1.060607\" -DLIST_H_INCLUDED -DMODVERSIONS -DMODULE -DL
INUX -D_LINUX_ -D__KERNEL__=1 -DCONFIG_PCI -DRR1520 -DHPT3XX_SATA_RESET -DNO_CRO
SS_CTRL=1 -DSUPPORT_ARRAY -DDBG=0 -Wall -O2 -Wstrict-prototypes -fomit-frame-poi
nter -I. -I/usr/src/linux/include -I/usr/src/linux/drivers/scsi -c hpt.c -o hpt.
o
hpt.c:1:26: error: linux/config.h: No such file or directory
In file included from /usr/src/linux/include/asm/thread_info.h:16,
                 from /usr/src/linux/include/linux/thread_info.h:21,
                 from /usr/src/linux/include/linux/preempt.h:9,
                 from /usr/src/linux/include/linux/spinlock.h:49,
                 from /usr/src/linux/include/linux/capability.h:45,
                 from /usr/src/linux/include/linux/sched.h:46,
                 from hpt.c:8:
/usr/src/linux/include/asm/processor.h:82: error: ‘CONFIG_X86_L1_CACHE_SHIFT’ un
declared here (not in a function)
/usr/src/linux/include/asm/processor.h:82: error: requested alignment is not a c
onstant
/usr/src/linux/include/asm/processor.h: In function ‘cpuid_count’:
/usr/src/linux/include/asm/processor.h:611: warning: pointer targets in passing
argument 1 of ‘native_cpuid’ differ in signedness
/usr/src/linux/include/asm/processor.h:611: warning: pointer targets in passing
argument 2 of ‘native_cpuid’ differ in signedness
/usr/src/linux/include/asm/processor.h:611: warning: pointer targets in passing
argument 3 of ‘native_cpuid’ differ in signedness
/usr/src/linux/include/asm/processor.h:611: warning: pointer targets in passing
argument 4 of ‘native_cpuid’ differ in signedness
In file included from /usr/src/linux/include/linux/sched.h:51,
                 from hpt.c:8:
/usr/src/linux/include/linux/jiffies.h:33:3: error: #error You lose.
/usr/src/linux/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux/include/linux/jiffies.h:269:46: error: division by zero in #if
In file included from /usr/src/linux/include/linux/sched.h:51,
                 from hpt.c:8:
/usr/src/linux/include/linux/jiffies.h: In function ‘jiffies_to_msecs’:
/usr/src/linux/include/linux/jiffies.h:274: error: ‘CONFIG_HZ’ undeclared (first
 use in this function)
/usr/src/linux/include/linux/jiffies.h:274: error: (Each undeclared identifier i
s reported only once
/usr/src/linux/include/linux/jiffies.h:274: error: for each function it appears
in.)
/usr/src/linux/include/linux/jiffies.h:280:46: error: division by zero in #if
/usr/src/linux/include/linux/jiffies.h: In function ‘jiffies_to_usecs’:
/usr/src/linux/include/linux/jiffies.h:285: error: ‘CONFIG_HZ’ undeclared (first
 use in this function)
/usr/src/linux/include/linux/jiffies.h:293:46: error: division by zero in #if
/usr/src/linux/include/linux/jiffies.h: In function ‘msecs_to_jiffies’:
/usr/src/linux/include/linux/jiffies.h:298: error: ‘CONFIG_HZ’ undeclared (first
 use in this function)
/usr/src/linux/include/linux/jiffies.h:306:46: error: division by zero in #if
/usr/src/linux/include/linux/jiffies.h: In function ‘usecs_to_jiffies’:
/usr/src/linux/include/linux/jiffies.h:311: error: ‘CONFIG_HZ’ undeclared (first
 use in this function)
/usr/src/linux/include/linux/jiffies.h: In function ‘timespec_to_jiffies’:
/usr/src/linux/include/linux/jiffies.h:330: error: ‘CONFIG_HZ’ undeclared (first
 use in this function)
/usr/src/linux/include/linux/jiffies.h:336: error: ‘SHIFT_HZ’ undeclared (first
use in this function)
/usr/src/linux/include/linux/jiffies.h: In function ‘jiffies_to_timespec’:
/usr/src/linux/include/linux/jiffies.h:349: error: ‘CONFIG_HZ’ undeclared (first
 use in this function)
/usr/src/linux/include/linux/jiffies.h: In function ‘timeval_to_jiffies’:
/usr/src/linux/include/linux/jiffies.h:371: error: ‘CONFIG_HZ’ undeclared (first
 use in this function)
/usr/src/linux/include/linux/jiffies.h:375: error: ‘SHIFT_HZ’ undeclared (first
use in this function)
/usr/src/linux/include/linux/jiffies.h: In function ‘jiffies_to_timeval’:
/usr/src/linux/include/linux/jiffies.h:387: error: ‘CONFIG_HZ’ undeclared (first
 use in this function)
/usr/src/linux/include/linux/jiffies.h:400:6: error: division by zero in #if
/usr/src/linux/include/linux/jiffies.h:400:6: error: division by zero in #if
/usr/src/linux/include/linux/jiffies.h:400:6: error: division by zero in #if
/usr/src/linux/include/linux/jiffies.h:400:6: error: division by zero in #if
/usr/src/linux/include/linux/jiffies.h:400:6: error: division by zero in #if
/usr/src/linux/include/linux/jiffies.h:400:6: error: division by zero in #if
/usr/src/linux/include/linux/jiffies.h:400:6: error: division by zero in #if
/usr/src/linux/include/linux/jiffies.h:400:6: error: division by zero in #if
/usr/src/linux/include/linux/jiffies.h:400:6: error: division by zero in #if
/usr/src/linux/include/linux/jiffies.h:400:6: error: division by zero in #if
/usr/src/linux/include/linux/jiffies.h:400:6: error: division by zero in #if
/usr/src/linux/include/linux/jiffies.h:400:6: error: division by zero in #if
/usr/src/linux/include/linux/jiffies.h:400:6: error: division by zero in #if
/usr/src/linux/include/linux/jiffies.h:400:6: error: division by zero in #if
/usr/src/linux/include/linux/jiffies.h:400:6: error: division by zero in #if
/usr/src/linux/include/linux/jiffies.h:400:6: error: division by zero in #if
/usr/src/linux/include/linux/jiffies.h: In function ‘jiffies_to_clock_t’:
/usr/src/linux/include/linux/jiffies.h:401: error: ‘CONFIG_HZ’ undeclared (first
 use in this function)
/usr/src/linux/include/linux/jiffies.h: In function ‘clock_t_to_jiffies’:
/usr/src/linux/include/linux/jiffies.h:412: error: ‘CONFIG_HZ’ undeclared (first
 use in this function)
/usr/src/linux/include/linux/jiffies.h:431:6: error: division by zero in #if
/usr/src/linux/include/linux/jiffies.h:431:6: error: division by zero in #if
/usr/src/linux/include/linux/jiffies.h:431:6: error: division by zero in #if
/usr/src/linux/include/linux/jiffies.h:431:6: error: division by zero in #if
/usr/src/linux/include/linux/jiffies.h:431:6: error: division by zero in #if
/usr/src/linux/include/linux/jiffies.h:431:6: error: division by zero in #if
/usr/src/linux/include/linux/jiffies.h:431:6: error: division by zero in #if
/usr/src/linux/include/linux/jiffies.h:431:6: error: division by zero in #if
/usr/src/linux/include/linux/jiffies.h:431:6: error: division by zero in #if
/usr/src/linux/include/linux/jiffies.h:431:6: error: division by zero in #if
/usr/src/linux/include/linux/jiffies.h:431:6: error: division by zero in #if
/usr/src/linux/include/linux/jiffies.h:431:6: error: division by zero in #if
/usr/src/linux/include/linux/jiffies.h:431:6: error: division by zero in #if
/usr/src/linux/include/linux/jiffies.h:431:6: error: division by zero in #if
/usr/src/linux/include/linux/jiffies.h:431:6: error: division by zero in #if
/usr/src/linux/include/linux/jiffies.h:431:6: error: division by zero in #if
/usr/src/linux/include/linux/jiffies.h: In function ‘jiffies_64_to_clock_t’:
/usr/src/linux/include/linux/jiffies.h:432: error: ‘CONFIG_HZ’ undeclared (first
 use in this function)
In file included from /usr/src/linux/include/linux/aio.h:5,
                 from /usr/src/linux/include/linux/sched.h:260,
                 from hpt.c:8:
/usr/src/linux/include/linux/workqueue.h: In function ‘cancel_delayed_work’:
/usr/src/linux/include/linux/workqueue.h:203: warning: dereferencing type-punned
 pointer will break strict-aliasing rules
In file included from hpt.c:8:
/usr/src/linux/include/linux/sched.h: In function ‘dequeue_signal_lock’:
/usr/src/linux/include/linux/sched.h:1309: warning: implicit declaration of func
tion ‘local_irq_save’
/usr/src/linux/include/linux/sched.h:1311: warning: implicit declaration of func
tion ‘local_irq_restore’
In file included from /usr/src/linux/include/linux/module.h:21,
                 from hpt.c:9:
/usr/src/linux/include/asm/module.h:62:2: error: #error unknown processor family
In file included from hpt.c:17:
/usr/src/linux/include/linux/mm.h: In function ‘lowmem_page_address’:
/usr/src/linux/include/linux/mm.h:539: warning: implicit declaration of function
 ‘__page_to_pfn’
/usr/src/linux/include/linux/mm.h:539: error: ‘CONFIG_PAGE_OFFSET’ undeclared (f
irst use in this function)
In file included from /usr/src/linux/include/linux/irq.h:22,
                 from /usr/src/linux/include/asm/hardirq.h:5,
                 from /usr/src/linux/include/linux/hardirq.h:7,
                 from /usr/src/linux/include/linux/interrupt.h:11,
                 from hpt.c:18:
/usr/src/linux/include/asm/irq.h:15:25: error: irq_vectors.h: No such file or di
rectory
In file included from /usr/src/linux/include/asm/hardirq.h:5,
                 from /usr/src/linux/include/linux/hardirq.h:7,
                 from /usr/src/linux/include/linux/interrupt.h:11,
                 from hpt.c:18:
/usr/src/linux/include/linux/irq.h: At top level:
/usr/src/linux/include/linux/irq.h:172: error: requested alignment is not a cons
tant
/usr/src/linux/include/linux/irq.h:174: error: ‘NR_IRQS’ undeclared here (not in
 a function)
In file included from /usr/src/linux/include/linux/hardirq.h:7,
                 from /usr/src/linux/include/linux/interrupt.h:11,
                 from hpt.c:18:
/usr/src/linux/include/asm/hardirq.h:12: error: requested alignment is not a con
stant
In file included from hpt.c:18:
/usr/src/linux/include/linux/interrupt.h: In function ‘cli’:
/usr/src/linux/include/linux/interrupt.h:204: warning: implicit declaration of f
unction ‘local_irq_disable’
/usr/src/linux/include/linux/interrupt.h: In function ‘sti’:
/usr/src/linux/include/linux/interrupt.h:208: warning: implicit declaration of f
unction ‘local_irq_enable’
/usr/src/linux/include/linux/interrupt.h: In function ‘save_flags’:
/usr/src/linux/include/linux/interrupt.h:212: warning: implicit declaration of f
unction ‘local_save_flags’
In file included from /usr/src/linux/include/linux/dmapool.h:14,
                 from /usr/src/linux/include/linux/pci.h:606,
                 from hpt.c:23:
/usr/src/linux/include/asm/io.h: In function ‘virt_to_phys’:
/usr/src/linux/include/asm/io.h:77: error: ‘CONFIG_PAGE_OFFSET’ undeclared (firs
t use in this function)
/usr/src/linux/include/asm/io.h: In function ‘phys_to_virt’:
/usr/src/linux/include/asm/io.h:95: error: ‘CONFIG_PAGE_OFFSET’ undeclared (firs
t use in this function)
In file included from /usr/src/linux/include/linux/pci.h:746,
                 from hpt.c:23:
/usr/src/linux/include/asm/pci.h: In function ‘pci_dac_dma_to_page’:
/usr/src/linux/include/asm/pci.h:72: warning: implicit declaration of function ‘
__pfn_to_page’
/usr/src/linux/include/asm/pci.h:72: warning: return makes pointer from integer
without a cast
hpt.c: In function ‘get_bdev’:
hpt.c:136: warning: implicit declaration of function ‘bdget’
hpt.c:136: warning: initialization makes pointer from integer without a cast
hpt.c:137: warning: implicit declaration of function ‘blkdev_get’
hpt.c:138: error: dereferencing pointer to incomplete type
hpt.c:141: warning: implicit declaration of function ‘blkdev_put’
In file included from hpt.c:185:
entry.c: At top level:
entry.c:20: error: ‘UTS_RELEASE’ undeclared here (not in a function)
In file included from hpt.c:185:
entry.c: In function ‘Check_Idle_Call’:
entry.c:216: warning: dereferencing type-punned pointer will break strict-aliasi
ng rules
entry.c: In function ‘Queue_SC’:
entry.c:225: warning: dereferencing type-punned pointer will break strict-aliasi
ng rules
entry.c:227: warning: dereferencing type-punned pointer will break strict-aliasi
ng rules
entry.c:227: warning: dereferencing type-punned pointer will break strict-aliasi
ng rules
entry.c:228: warning: dereferencing type-punned pointer will break strict-aliasi
ng rules
entry.c: In function ‘Release_SC’:
entry.c:238: warning: dereferencing type-punned pointer will break strict-aliasi
ng rules
entry.c:242: warning: dereferencing type-punned pointer will break strict-aliasi
ng rules
entry.c:243: warning: dereferencing type-punned pointer will break strict-aliasi
ng rules
entry.c:245: warning: dereferencing type-punned pointer will break strict-aliasi
ng rules
entry.c:245: warning: dereferencing type-punned pointer will break strict-aliasi
ng rules
entry.c: In function ‘do_mode_sense’:
entry.c:354: error: ‘Scsi_Cmnd’ has no member named ‘bufflen’
entry.c:354: warning: initialization makes integer from pointer without a cast
entry.c:372: warning: dereferencing type-punned pointer will break strict-aliasi
ng rules
entry.c: In function ‘OsSendCommand’:
entry.c:439: warning: dereferencing type-punned pointer will break strict-aliasi
ng rules
entry.c:455: warning: dereferencing type-punned pointer will break strict-aliasi
ng rules
entry.c:521: warning: dereferencing type-punned pointer will break strict-aliasi
ng rules
entry.c: In function ‘internal_done’:
entry.c:608: warning: dereferencing type-punned pointer will break strict-aliasi
ng rules
entry.c: In function ‘hpt3xx_Command’:
entry.c:621: warning: dereferencing type-punned pointer will break strict-aliasi
ng rules
entry.c:624: error: ‘CONFIG_HZ’ undeclared (first use in this function)
entry.c:624: error: invalid operands to binary *
entry.c:624: warning: assignment makes integer from pointer without a cast
entry.c:625: warning: dereferencing type-punned pointer will break strict-aliasi
ng rules
entry.c:627: warning: dereferencing type-punned pointer will break strict-aliasi
ng rules
entry.c: In function ‘hpt3xx_Detect’:
entry.c:823: warning: passing argument 2 of ‘request_irq’ from incompatible poin
ter type
entry.c:824: warning: passing argument 2 of ‘request_irq’ from incompatible poin
ter type
entry.c: In function ‘hpt3xx_Reset’:
entry.c:915: warning: dereferencing type-punned pointer will break strict-aliasi
ng rules
entry.c: In function ‘fOsBuildSgl’:
entry.c:1112: warning: dereferencing type-punned pointer will break strict-alias
ing rules
entry.c:1113: warning: dereferencing type-punned pointer will break strict-alias
ing rules
entry.c:1116: warning: dereferencing type-punned pointer will break strict-alias
ing rules
entry.c:1118: warning: dereferencing type-punned pointer will break strict-alias
ing rules
entry.c:1123: warning: dereferencing type-punned pointer will break strict-alias
ing rules
entry.c:1127: warning: dereferencing type-punned pointer will break strict-alias
ing rules
entry.c:1128: warning: dereferencing type-punned pointer will break strict-alias
ing rules
entry.c:1130: warning: dereferencing type-punned pointer will break strict-alias
ing rules
entry.c:1132: warning: dereferencing type-punned pointer will break strict-alias
ing rules
entry.c: In function ‘fOsCommandDone’:
entry.c:1146: warning: dereferencing type-punned pointer will break strict-alias
ing rules
entry.c:1157: warning: dereferencing type-punned pointer will break strict-alias
ing rules
entry.c: In function ‘__check_autorebuild’:
entry.c:1700: warning: pointer targets in return differ in signedness
In file included from hpt.c:186:
hptproc.c: In function ‘get_sd_name’:
hptproc.c:503: error: dereferencing pointer to incomplete type
hptproc.c:503: error: request for member ‘disk_name’ in something not a structur
e or union
In file included from ioctl.c:6,
                 from hpt.c:187:
gui_lib.c: In function ‘hpt_get_controller_info’:
gui_lib.c:427: warning: pointer targets in passing argument 1 of ‘strcpy’ differ
 in signedness
gui_lib.c:433: warning: pointer targets in passing argument 1 of ‘strcpy’ differ
 in signedness
In file included from hpt.c:187:
ioctl.c: In function ‘timer_start_for_cmd’:
ioctl.c:197: error: ‘CONFIG_HZ’ undeclared (first use in this function)
ioctl.c:197: error: invalid operands to binary *
ioctl.c:197: warning: assignment makes integer from pointer without a cast
ioctl.c: In function ‘Kernel_DeviceIoControl’:
ioctl.c:476: error: ‘CONFIG_HZ’ undeclared (first use in this function)
ioctl.c:476: error: invalid operands to binary *
ioctl.c:476: warning: assignment makes integer from pointer without a cast
ioctl.c: In function ‘hpt_set_array_state’:
ioctl.c:521: error: ‘CONFIG_HZ’ undeclared (first use in this function)
ioctl.c:521: error: invalid operands to binary *
ioctl.c:521: warning: assignment makes integer from pointer without a cast
ioctl.c: In function ‘hpt_rescan_all’:
ioctl.c:658: error: ‘CONFIG_HZ’ undeclared (first use in this function)
ioctl.c:658: error: invalid operands to binary *
ioctl.c:658: warning: assignment makes integer from pointer without a cast
ioctl.c: In function ‘hpt_rebuild_data_block’:
ioctl.c:898: error: ‘CONFIG_HZ’ undeclared (first use in this function)
ioctl.c:898: error: invalid operands to binary *
ioctl.c:898: warning: passing argument 1 of ‘schedule_timeout’ makes integer fro
m pointer without a cast
make: *** [hpt.o] Error 1

```

The only part of that which makes any sense is the "You Lose" line. I'm clearly lost.

---

### Post by Sivart832z on 2007-08-12
I've been trying to get this controller working for all weekend and still haven't made a bit of progress. If nobody can provide me with any ideas or assistance at all I'm going to have to give up on ever using Ubuntu because I am going to need my files off these disks.

I'm attaching two photos I took of the screen while trying to boot with a drive attached to the controller. The first (DSCN9669) is earlier in the boot process and looks like it is detecting the card and using what might be a correct driver for it. The second one, modprobe.jpg, shows where everything hangs. When a disk is attached it will not boot past this point. Before the crash there are several references to "hpt366". According to one of the links in my original thread, this was the wrong driver and would cause things to hang if it was used. I've done everything I can figure out to make it not be used, including adding it to a modprobe.d blacklist and then going to /lib/modules/2.6.20-16-generic/kernel/drivers/ide/pci/ and deleting the file hpt366.ko, but still, every time it boots, it hangs at that modprobe and shows lots of references to hpt366!

Seeing I haven't had any luck getting help making a new driver, can anyone help me avoid the hanging and modprobe problem? At the moment I can boot successfully only by unplugging the drives from the controller. I would consider it major progress if someone could provide me with some assistance in booting with the drives plugged in, even if I can't get them to actually work once booted. 

Anything.... Please... I really don't want to have to blow this all away after I've worked so hard on getting stuff working.

---

### Post by Croesus on 2007-08-13
I'm having practically the same problem.

What I've learned is that the chipset on the highpoint card is the same as the chipset for older motherboards. So my theory is that the kernel is detecting the drives on the Raid card first, and after loading the drivers for those drives the kernel can't find the boot partition any more.

But anyway - I have managed to boot with the drives connected. 

first open  - >  /boot/grub/menu.lst

There you will see entries - I made a new entry that tells the kernel not to scan for the drives connected by the raid controller (with the noprobe kernel parameter)
The entry looks something like this,

title           Ubuntu, kernel 2.6.20-16-generic noscan efgh
root            (hd0,0)
kernel          /vmlinuz-2.6.20-16-generic root=/dev/mapper/rootvg-lvroot ro quiet splash hde=noprobe hdf=noprobe hdg=noprobe hdh=noprobe
initrd          /initrd.img-2.6.20-16-generic
quiet


So take the entry you already have in the menu.lst file, copy it, rename it, and add the parameters 'hde=noprobe hdf=noprobe hdg=noprobe hdh=noprobe' to the kernel entry and hopefully your machine will boot, but without the hard drives on the raid controller.

---

### Post by Sivart832z on 2007-08-13
Thanks so much for trying to help!

Before I tried your suggestion, I had another thing I wanted to try. I got the instructions from [http://giggsey.com/2007/08/06/ubuntu-feisty-modprobe-solved/](http://giggsey.com/2007/08/06/ubuntu-feisty-modprobe-solved/) where someone else was having an issue with feisty hanging with a modprobe. Seeing the problem looked exactly like mine, except mine was talking about htp366 and theirs was talking about something else, I wanted to see if doing the update they mentioned would fix my issue as well. I performed the steps, reconnected my drives, and restarted. It worked! I was able to successfully boot linux with the drives attached to the controller without getting the modprobe error! Unfortunately, the drives still aren't showing up, so now it seems I still have to build the correct driver. (But if anyone has any other ideas, please share!)  Luckily, this fix allows me to boot the OS normally without the error, rather than disabling the drives. Getting the modprobe issue fixed was the first issue, and now that I'm somewhat satisfied that the problem is corrected, I can focus entirely on getting a working driver.

The update I performed changed my version to 2.6.22-9-generic so I'm going to report the errors I get when I try and make the driver. I'm hoping this is something quite simple to fix and someone with just a little more knowledge can tell me why things are failing. It looks like some files are just missing, or in the wrong location, or something like that.

Here is what I type when trying to build the driver, and the error I get back. Once this is done, no driver file has been created.

```
tdcook@tcook-1:~/hpt$ sudo make RR1520=1 NON_RAIR=1
Password:
gcc -DDRIVER_VERSION=\"2.1.060607\" -DLIST_H_INCLUDED -DMODVERSIONS -DMODULE -DLINUX -D_LINUX_ -D__KERNEL__=1 -DCONFIG_PCI -DRR1520 -DHPT3XX_SATA_RESET -DNO_CROSS_CTRL=1 -DSUPPORT_ARRAY -DDBG=0 -Wall -O2 -Wstrict-prototypes -fomit-frame-pointer -I. -I/lib/modules/2.6.22-9-generic/build/include -I/lib/modules/2.6.22-9-generic/build/drivers/scsi -c hpt.c -o hpt.o
hpt.c:1:26: error: linux/config.h: No such file or directory
In file included from /lib/modules/2.6.22-9-generic/build/include/asm/thread_info.h:16,
                 from /lib/modules/2.6.22-9-generic/build/include/linux/thread_info.h:21,
                 from /lib/modules/2.6.22-9-generic/build/include/linux/preempt.h:9,
                 from /lib/modules/2.6.22-9-generic/build/include/linux/spinlock.h:49,
                 from /lib/modules/2.6.22-9-generic/build/include/linux/capability.h:47,
                 from /lib/modules/2.6.22-9-generic/build/include/linux/sched.h:46,
                 from hpt.c:8:
/lib/modules/2.6.22-9-generic/build/include/asm/processor.h:83: error: ‘CONFIG_X86_L1_CACHE_SHIFT’ undeclared here (not in a function)
/lib/modules/2.6.22-9-generic/build/include/asm/processor.h:83: error: requested alignment is not a constant
/lib/modules/2.6.22-9-generic/build/include/asm/processor.h: In function ‘cpuid_count’:
/lib/modules/2.6.22-9-generic/build/include/asm/processor.h:618: warning: pointer targets in passing argument 1 of ‘native_cpuid’ differ in signedness
/lib/modules/2.6.22-9-generic/build/include/asm/processor.h:618: warning: pointer targets in passing argument 2 of ‘native_cpuid’ differ in signedness
/lib/modules/2.6.22-9-generic/build/include/asm/processor.h:618: warning: pointer targets in passing argument 3 of ‘native_cpuid’ differ in signedness
/lib/modules/2.6.22-9-generic/build/include/asm/processor.h:618: warning: pointer targets in passing argument 4 of ‘native_cpuid’ differ in signedness
In file included from /lib/modules/2.6.22-9-generic/build/include/linux/sched.h:51,
                 from hpt.c:8:
/lib/modules/2.6.22-9-generic/build/include/linux/jiffies.h:33:3: error: #error You lose.
/lib/modules/2.6.22-9-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.22-9-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.22-9-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.22-9-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.22-9-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.22-9-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.22-9-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.22-9-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.22-9-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.22-9-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.22-9-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.22-9-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.22-9-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.22-9-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.22-9-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.22-9-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
In file included from /lib/modules/2.6.22-9-generic/build/include/linux/aio.h:5,
                 from /lib/modules/2.6.22-9-generic/build/include/linux/sched.h:273,
                 from hpt.c:8:
/lib/modules/2.6.22-9-generic/build/include/linux/workqueue.h: In function ‘cancel_delayed_work’:
/lib/modules/2.6.22-9-generic/build/include/linux/workqueue.h:165: warning: dereferencing type-punned pointer will break strict-aliasing rules
In file included from hpt.c:8:
/lib/modules/2.6.22-9-generic/build/include/linux/sched.h: In function ‘dequeue_signal_lock’:
/lib/modules/2.6.22-9-generic/build/include/linux/sched.h:1337: warning: implicit declaration of function ‘local_irq_save’
/lib/modules/2.6.22-9-generic/build/include/linux/sched.h:1339: warning: implicit declaration of function ‘local_irq_restore’
In file included from /lib/modules/2.6.22-9-generic/build/include/linux/module.h:21,
                 from hpt.c:9:
/lib/modules/2.6.22-9-generic/build/include/asm/module.h:64:2: error: #error unknown processor family
In file included from hpt.c:17:
/lib/modules/2.6.22-9-generic/build/include/linux/mm.h: In function ‘virt_to_head_page’:
/lib/modules/2.6.22-9-generic/build/include/linux/mm.h:291: warning: implicit declaration of function ‘__pfn_to_page’
/lib/modules/2.6.22-9-generic/build/include/linux/mm.h:291: error: ‘CONFIG_PAGE_OFFSET’ undeclared (first use in this function)
/lib/modules/2.6.22-9-generic/build/include/linux/mm.h:291: error: (Each undeclared identifier is reported only once
/lib/modules/2.6.22-9-generic/build/include/linux/mm.h:291: error: for each function it appears in.)
/lib/modules/2.6.22-9-generic/build/include/linux/mm.h:291: warning: initialization makes pointer from integer without a cast
In file included from hpt.c:17:
/lib/modules/2.6.22-9-generic/build/include/linux/mm.h: In function ‘lowmem_page_address’:
/lib/modules/2.6.22-9-generic/build/include/linux/mm.h:560: warning: implicit declaration of function ‘__page_to_pfn’
/lib/modules/2.6.22-9-generic/build/include/linux/mm.h:560: error: ‘CONFIG_PAGE_OFFSET’ undeclared (first use in this function)
In file included from /lib/modules/2.6.22-9-generic/build/include/linux/irq.h:23,
                 from /lib/modules/2.6.22-9-generic/build/include/asm/hardirq.h:5,
                 from /lib/modules/2.6.22-9-generic/build/include/linux/hardirq.h:7,
                 from /lib/modules/2.6.22-9-generic/build/include/linux/interrupt.h:11,
                 from hpt.c:18:
/lib/modules/2.6.22-9-generic/build/include/asm/irq.h:15:25: error: irq_vectors.h: No such file or directory
In file included from /lib/modules/2.6.22-9-generic/build/include/asm/hardirq.h:5,
                 from /lib/modules/2.6.22-9-generic/build/include/linux/hardirq.h:7,
                 from /lib/modules/2.6.22-9-generic/build/include/linux/interrupt.h:11,
                 from hpt.c:18:
/lib/modules/2.6.22-9-generic/build/include/linux/irq.h: At top level:
/lib/modules/2.6.22-9-generic/build/include/linux/irq.h:178: error: ‘NR_IRQS’ undeclared here (not in a function)
In file included from /lib/modules/2.6.22-9-generic/build/include/linux/hardirq.h:7,
                 from /lib/modules/2.6.22-9-generic/build/include/linux/interrupt.h:11,
                 from hpt.c:18:
/lib/modules/2.6.22-9-generic/build/include/asm/hardirq.h:12: error: requested alignment is not a constant
In file included from hpt.c:18:
/lib/modules/2.6.22-9-generic/build/include/linux/interrupt.h: In function ‘cli’:
/lib/modules/2.6.22-9-generic/build/include/linux/interrupt.h:221: warning: implicit declaration of function ‘local_irq_disable’
/lib/modules/2.6.22-9-generic/build/include/linux/interrupt.h: In function ‘sti’:
/lib/modules/2.6.22-9-generic/build/include/linux/interrupt.h:225: warning: implicit declaration of function ‘local_irq_enable’
/lib/modules/2.6.22-9-generic/build/include/linux/interrupt.h: In function ‘save_flags’:
/lib/modules/2.6.22-9-generic/build/include/linux/interrupt.h:229: warning: implicit declaration of function ‘local_save_flags’
In file included from hpt.c:23:
/lib/modules/2.6.22-9-generic/build/include/linux/pci.h: In function ‘pci_register_driver’:
/lib/modules/2.6.22-9-generic/build/include/linux/pci.h:603: error: ‘KBUILD_MODNAME’ undeclared (first use in this function)
In file included from /lib/modules/2.6.22-9-generic/build/include/linux/dmapool.h:14,
                 from /lib/modules/2.6.22-9-generic/build/include/linux/pci.h:620,
                 from hpt.c:23:
/lib/modules/2.6.22-9-generic/build/include/asm/io.h: In function ‘virt_to_phys’:
/lib/modules/2.6.22-9-generic/build/include/asm/io.h:77: error: ‘CONFIG_PAGE_OFFSET’ undeclared (first use in this function)
/lib/modules/2.6.22-9-generic/build/include/asm/io.h: In function ‘phys_to_virt’:
/lib/modules/2.6.22-9-generic/build/include/asm/io.h:95: error: ‘CONFIG_PAGE_OFFSET’ undeclared (first use in this function)
In file included from /lib/modules/2.6.22-9-generic/build/include/linux/pci.h:766,
                 from hpt.c:23:
/lib/modules/2.6.22-9-generic/build/include/asm/pci.h: In function ‘pci_dac_dma_to_page’:
/lib/modules/2.6.22-9-generic/build/include/asm/pci.h:72: warning: return makes pointer from integer without a cast
hpt.c: In function ‘get_bdev’:
hpt.c:136: warning: implicit declaration of function ‘bdget’
hpt.c:136: warning: initialization makes pointer from integer without a cast
hpt.c:137: warning: implicit declaration of function ‘blkdev_get’
hpt.c:138: error: dereferencing pointer to incomplete type
hpt.c:141: warning: implicit declaration of function ‘blkdev_put’
In file included from hpt.c:185:
entry.c: At top level:
entry.c:20: error: ‘UTS_RELEASE’ undeclared here (not in a function)
In file included from hpt.c:185:
entry.c: In function ‘Check_Idle_Call’:
entry.c:216: warning: dereferencing type-punned pointer will break strict-aliasing rules
entry.c: In function ‘Queue_SC’:
entry.c:225: warning: dereferencing type-punned pointer will break strict-aliasing rules
entry.c:227: warning: dereferencing type-punned pointer will break strict-aliasing rules
entry.c:227: warning: dereferencing type-punned pointer will break strict-aliasing rules
entry.c:228: warning: dereferencing type-punned pointer will break strict-aliasing rules
entry.c: In function ‘Release_SC’:
entry.c:238: warning: dereferencing type-punned pointer will break strict-aliasing rules
entry.c:242: warning: dereferencing type-punned pointer will break strict-aliasing rules
entry.c:243: warning: dereferencing type-punned pointer will break strict-aliasing rules
entry.c:245: warning: dereferencing type-punned pointer will break strict-aliasing rules
entry.c:245: warning: dereferencing type-punned pointer will break strict-aliasing rules
entry.c: In function ‘scsicmd_buf_get’:
entry.c:271: error: ‘OS_KMAP_TYPE’ undeclared (first use in this function)
entry.c:271: error: incompatible type for argument 2 of ‘kmap_atomic’
entry.c: In function ‘do_mode_sense’:
entry.c:354: error: ‘Scsi_Cmnd’ has no member named ‘bufflen’
entry.c:354: warning: initialization makes integer from pointer without a cast
entry.c:372: warning: dereferencing type-punned pointer will break strict-aliasing rules
entry.c: In function ‘OsSendCommand’:
entry.c:439: warning: dereferencing type-punned pointer will break strict-aliasing rules
entry.c:455: warning: dereferencing type-punned pointer will break strict-aliasing rules
entry.c:521: warning: dereferencing type-punned pointer will break strict-aliasing rules
entry.c: In function ‘internal_done’:
entry.c:608: warning: dereferencing type-punned pointer will break strict-aliasing rules
entry.c: In function ‘hpt3xx_Command’:
entry.c:621: warning: dereferencing type-punned pointer will break strict-aliasing rules
entry.c:624: error: ‘CONFIG_HZ’ undeclared (first use in this function)
entry.c:624: error: invalid operands to binary *
entry.c:624: warning: assignment makes integer from pointer without a cast
entry.c:625: warning: dereferencing type-punned pointer will break strict-aliasing rules
entry.c:627: warning: dereferencing type-punned pointer will break strict-aliasing rules
entry.c: In function ‘hpt3xx_Detect’:
entry.c:715: warning: ‘pci_find_device’ is deprecated (declared at /lib/modules/2.6.22-9-generic/build/include/linux/pci.h:477)
entry.c:747: warning: ‘pci_find_device’ is deprecated (declared at /lib/modules/2.6.22-9-generic/build/include/linux/pci.h:477)
entry.c:778: warning: ‘pci_find_device’ is deprecated (declared at /lib/modules/2.6.22-9-generic/build/include/linux/pci.h:477)
entry.c:823: warning: ‘deprecated_irq_flag’ is deprecated (declared at /lib/modules/2.6.22-9-generic/build/include/linux/interrupt.h:66)
entry.c:823: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type
entry.c:824: warning: ‘deprecated_irq_flag’ is deprecated (declared at /lib/modules/2.6.22-9-generic/build/include/linux/interrupt.h:66)
entry.c:824: warning: ‘deprecated_irq_flag’ is deprecated (declared at /lib/modules/2.6.22-9-generic/build/include/linux/interrupt.h:66)
entry.c:824: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type
entry.c: In function ‘hpt3xx_Reset’:
entry.c:915: warning: dereferencing type-punned pointer will break strict-aliasing rules
entry.c: In function ‘fOsBuildSgl’:
entry.c:1112: warning: dereferencing type-punned pointer will break strict-aliasing rules
entry.c:1113: warning: dereferencing type-punned pointer will break strict-aliasing rules
entry.c:1116: warning: dereferencing type-punned pointer will break strict-aliasing rules
entry.c:1118: warning: dereferencing type-punned pointer will break strict-aliasing rules
entry.c:1123: warning: dereferencing type-punned pointer will break strict-aliasing rules
entry.c:1127: warning: dereferencing type-punned pointer will break strict-aliasing rules
entry.c:1128: warning: dereferencing type-punned pointer will break strict-aliasing rules
entry.c:1130: warning: dereferencing type-punned pointer will break strict-aliasing rules
entry.c:1132: warning: dereferencing type-punned pointer will break strict-aliasing rules
entry.c: In function ‘fOsCommandDone’:
entry.c:1146: warning: dereferencing type-punned pointer will break strict-aliasing rules
entry.c:1157: warning: dereferencing type-punned pointer will break strict-aliasing rules
entry.c: In function ‘__check_autorebuild’:
entry.c:1700: warning: pointer targets in return differ in signedness
In file included from hpt.c:186:
hptproc.c: In function ‘get_sd_name’:
hptproc.c:503: error: dereferencing pointer to incomplete type
hptproc.c:503: error: request for member ‘disk_name’ in something not a structure or union
In file included from ioctl.c:6,
                 from hpt.c:187:
gui_lib.c: In function ‘hpt_get_controller_info’:
gui_lib.c:427: warning: pointer targets in passing argument 1 of ‘strcpy’ differ in signedness
gui_lib.c:433: warning: pointer targets in passing argument 1 of ‘strcpy’ differ in signedness
In file included from hpt.c:187:
ioctl.c: In function ‘timer_start_for_cmd’:
ioctl.c:197: error: ‘CONFIG_HZ’ undeclared (first use in this function)
ioctl.c:197: error: invalid operands to binary *
ioctl.c:197: warning: assignment makes integer from pointer without a cast
ioctl.c: In function ‘Kernel_DeviceIoControl’:
ioctl.c:476: error: ‘CONFIG_HZ’ undeclared (first use in this function)
ioctl.c:476: error: invalid operands to binary *
ioctl.c:476: warning: assignment makes integer from pointer without a cast
ioctl.c: In function ‘hpt_set_array_state’:
ioctl.c:521: error: ‘CONFIG_HZ’ undeclared (first use in this function)
ioctl.c:521: error: invalid operands to binary *
ioctl.c:521: warning: assignment makes integer from pointer without a cast
ioctl.c: In function ‘hpt_rescan_all’:
ioctl.c:658: error: ‘CONFIG_HZ’ undeclared (first use in this function)
ioctl.c:658: error: invalid operands to binary *
ioctl.c:658: warning: assignment makes integer from pointer without a cast
ioctl.c: In function ‘hpt_rebuild_data_block’:
ioctl.c:898: error: ‘CONFIG_HZ’ undeclared (first use in this function)
ioctl.c:898: error: invalid operands to binary *
ioctl.c:898: warning: passing argument 1 of ‘schedule_timeout’ makes integer from pointer without a cast
make: *** [hpt.o] Error 1

```

Thanks again - I really appreciate the reply! Hopefully someone had an idea of what to try next to get this make working. Things are certainly looking up!

---

### Post by Sivart832z on 2007-08-14
I wanted to post an update in case someone looked at this and tried to help me. I've worked through a number of issues so far, some likely necessary, and others that probably were not. Anyway - Here is the current error message I'm receiving, if anyone else has some more advice.

```
sudo make KERNELDIR=/usr/src/linux-source-2.6.22 RR1520=1 NON_RAID=1
Password:
gcc -DDRIVER_VERSION=\"2.1.060607\" -DLIST_H_INCLUDED -DMODVERSIONS -DMODULE -DLINUX -D_LINUX_ -D__KERNEL__=1 -DCONFIG_PCI -DRR1520 -DHPT3XX_SATA_RESET -DNO_CROSS_CTRL=1 -DDBG=0 -Wall -O2 -Wstrict-prototypes -fomit-frame-pointer -I. -I/usr/src/linux-source-2.6.22/include -I/usr/src/linux-source-2.6.22/drivers/scsi -c hpt.c -o hpt.o
In file included from /usr/src/linux-source-2.6.22/include/asm/thread_info.h:16,
                 from /usr/src/linux-source-2.6.22/include/linux/thread_info.h:21,
                 from /usr/src/linux-source-2.6.22/include/linux/preempt.h:9,
                 from /usr/src/linux-source-2.6.22/include/linux/spinlock.h:49,
                 from /usr/src/linux-source-2.6.22/include/linux/capability.h:47,
                 from /usr/src/linux-source-2.6.22/include/linux/sched.h:46,
                 from hpt.c:8:
/usr/src/linux-source-2.6.22/include/asm/processor.h: In function ‘cpuid_count’:
/usr/src/linux-source-2.6.22/include/asm/processor.h:618: warning: pointer targets in passing argument 1 of ‘native_cpuid’ differ in signedness
/usr/src/linux-source-2.6.22/include/asm/processor.h:618: warning: pointer targets in passing argument 2 of ‘native_cpuid’ differ in signedness
/usr/src/linux-source-2.6.22/include/asm/processor.h:618: warning: pointer targets in passing argument 3 of ‘native_cpuid’ differ in signedness
/usr/src/linux-source-2.6.22/include/asm/processor.h:618: warning: pointer targets in passing argument 4 of ‘native_cpuid’ differ in signedness
In file included from /usr/src/linux-source-2.6.22/include/asm/smp.h:15,
                 from /usr/src/linux-source-2.6.22/include/linux/smp.h:19,
                 from /usr/src/linux-source-2.6.22/include/linux/sched.h:65,
                 from hpt.c:8:
/usr/src/linux-source-2.6.22/include/asm/mpspec.h:6:25: error: mach_mpspec.h: No such file or directory
In file included from /usr/src/linux-source-2.6.22/include/asm/smp.h:15,
                 from /usr/src/linux-source-2.6.22/include/linux/smp.h:19,
                 from /usr/src/linux-source-2.6.22/include/linux/sched.h:65,
                 from hpt.c:8:
/usr/src/linux-source-2.6.22/include/asm/mpspec.h: At top level:
/usr/src/linux-source-2.6.22/include/asm/mpspec.h:8: error: ‘MAX_MP_BUSSES’ undeclared here (not in a function)
/usr/src/linux-source-2.6.22/include/asm/mpspec.h:22: error: ‘MAX_IRQ_SOURCES’ undeclared here (not in a function)
In file included from /usr/src/linux-source-2.6.22/include/linux/smp.h:19,
                 from /usr/src/linux-source-2.6.22/include/linux/sched.h:65,
                 from hpt.c:8:
/usr/src/linux-source-2.6.22/include/asm/smp.h:150:26: error: mach_apicdef.h: No such file or directory
In file included from /usr/src/linux-source-2.6.22/include/linux/smp.h:19,
                 from /usr/src/linux-source-2.6.22/include/linux/sched.h:65,
                 from hpt.c:8:
/usr/src/linux-source-2.6.22/include/asm/smp.h: In function ‘hard_smp_processor_id’:
/usr/src/linux-source-2.6.22/include/asm/smp.h:154: warning: implicit declaration of function ‘GET_APIC_ID’
In file included from /usr/src/linux-source-2.6.22/include/linux/aio.h:5,
                 from /usr/src/linux-source-2.6.22/include/linux/sched.h:273,
                 from hpt.c:8:
/usr/src/linux-source-2.6.22/include/linux/workqueue.h: In function ‘cancel_delayed_work’:
/usr/src/linux-source-2.6.22/include/linux/workqueue.h:165: warning: dereferencing type-punned pointer will break strict-aliasing rules
In file included from /usr/src/linux-source-2.6.22/include/linux/irq.h:23,
                 from /usr/src/linux-source-2.6.22/include/asm/hardirq.h:5,
                 from /usr/src/linux-source-2.6.22/include/linux/hardirq.h:7,
                 from /usr/src/linux-source-2.6.22/include/linux/interrupt.h:11,
                 from hpt.c:18:
/usr/src/linux-source-2.6.22/include/asm/irq.h:15:25: error: irq_vectors.h: No such file or directory
In file included from /usr/src/linux-source-2.6.22/include/asm/hardirq.h:5,
                 from /usr/src/linux-source-2.6.22/include/linux/hardirq.h:7,
                 from /usr/src/linux-source-2.6.22/include/linux/interrupt.h:11,
                 from hpt.c:18:
/usr/src/linux-source-2.6.22/include/linux/irq.h: At top level:
/usr/src/linux-source-2.6.22/include/linux/irq.h:178: error: ‘NR_IRQS’ undeclared here (not in a function)
In file included from hpt.c:23:
/usr/src/linux-source-2.6.22/include/linux/pci.h: In function ‘pci_register_driver’:
/usr/src/linux-source-2.6.22/include/linux/pci.h:603: error: ‘KBUILD_MODNAME’ undeclared (first use in this function)
/usr/src/linux-source-2.6.22/include/linux/pci.h:603: error: (Each undeclared identifier is reported only once
/usr/src/linux-source-2.6.22/include/linux/pci.h:603: error: for each function it appears in.)
In file included from hpt.c:185:
entry.c: At top level:
entry.c:20: error: ‘UTS_RELEASE’ undeclared here (not in a function)
In file included from hpt.c:185:
entry.c: In function ‘Check_Idle_Call’:
entry.c:216: warning: dereferencing type-punned pointer will break strict-aliasing rules
entry.c: In function ‘Queue_SC’:
entry.c:225: warning: dereferencing type-punned pointer will break strict-aliasing rules
entry.c:227: warning: dereferencing type-punned pointer will break strict-aliasing rules
entry.c:227: warning: dereferencing type-punned pointer will break strict-aliasing rules
entry.c:228: warning: dereferencing type-punned pointer will break strict-aliasing rules
entry.c: In function ‘Release_SC’:
entry.c:238: warning: dereferencing type-punned pointer will break strict-aliasing rules
entry.c:242: warning: dereferencing type-punned pointer will break strict-aliasing rules
entry.c:243: warning: dereferencing type-punned pointer will break strict-aliasing rules
entry.c:245: warning: dereferencing type-punned pointer will break strict-aliasing rules
entry.c:245: warning: dereferencing type-punned pointer will break strict-aliasing rules
entry.c: In function ‘do_mode_sense’:
entry.c:354: error: ‘Scsi_Cmnd’ has no member named ‘bufflen’
entry.c:354: warning: initialization makes integer from pointer without a cast
entry.c:372: warning: dereferencing type-punned pointer will break strict-aliasing rules
entry.c: In function ‘OsSendCommand’:
entry.c:439: warning: dereferencing type-punned pointer will break strict-aliasing rules
entry.c:455: warning: dereferencing type-punned pointer will break strict-aliasing rules
entry.c:521: warning: dereferencing type-punned pointer will break strict-aliasing rules
entry.c: In function ‘internal_done’:
entry.c:608: warning: dereferencing type-punned pointer will break strict-aliasing rules
entry.c: In function ‘hpt3xx_Command’:
entry.c:621: warning: dereferencing type-punned pointer will break strict-aliasing rules
entry.c:625: warning: dereferencing type-punned pointer will break strict-aliasing rules
entry.c:627: warning: dereferencing type-punned pointer will break strict-aliasing rules
entry.c: In function ‘hpt3xx_Detect’:
entry.c:715: warning: ‘pci_find_device’ is deprecated (declared at /usr/src/linux-source-2.6.22/include/linux/pci.h:477)
entry.c:747: warning: ‘pci_find_device’ is deprecated (declared at /usr/src/linux-source-2.6.22/include/linux/pci.h:477)
entry.c:778: warning: ‘pci_find_device’ is deprecated (declared at /usr/src/linux-source-2.6.22/include/linux/pci.h:477)
entry.c:823: warning: ‘deprecated_irq_flag’ is deprecated (declared at /usr/src/linux-source-2.6.22/include/linux/interrupt.h:66)
entry.c:823: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type
entry.c:824: warning: ‘deprecated_irq_flag’ is deprecated (declared at /usr/src/linux-source-2.6.22/include/linux/interrupt.h:66)
entry.c:824: warning: ‘deprecated_irq_flag’ is deprecated (declared at /usr/src/linux-source-2.6.22/include/linux/interrupt.h:66)
entry.c:824: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type
entry.c: In function ‘hpt3xx_Reset’:
entry.c:915: warning: dereferencing type-punned pointer will break strict-aliasing rules
entry.c: In function ‘fOsBuildSgl’:
entry.c:1112: warning: dereferencing type-punned pointer will break strict-aliasing rules
entry.c:1113: warning: dereferencing type-punned pointer will break strict-aliasing rules
entry.c:1116: warning: dereferencing type-punned pointer will break strict-aliasing rules
entry.c:1118: warning: dereferencing type-punned pointer will break strict-aliasing rules
entry.c:1123: warning: dereferencing type-punned pointer will break strict-aliasing rules
entry.c:1127: warning: dereferencing type-punned pointer will break strict-aliasing rules
entry.c:1128: warning: dereferencing type-punned pointer will break strict-aliasing rules
entry.c:1130: warning: dereferencing type-punned pointer will break strict-aliasing rules
entry.c:1132: warning: dereferencing type-punned pointer will break strict-aliasing rules
entry.c: In function ‘fOsCommandDone’:
entry.c:1146: warning: dereferencing type-punned pointer will break strict-aliasing rules
entry.c:1157: warning: dereferencing type-punned pointer will break strict-aliasing rules
entry.c: In function ‘__check_autorebuild’:
entry.c:1700: warning: pointer targets in return differ in signedness
In file included from hpt.c:186:
hptproc.c: In function ‘get_sd_name’:
hptproc.c:500: warning: implicit declaration of function ‘get_bdev’
hptproc.c:500: warning: initialization makes pointer from integer without a cast
hptproc.c:504: error: expected ‘)’ before ‘__BDEV_RAW’
In file included from ioctl.c:6,
                 from hpt.c:187:
gui_lib.c: In function ‘hpt_get_controller_info’:
gui_lib.c:427: warning: pointer targets in passing argument 1 of ‘strcpy’ differ in signedness
gui_lib.c:433: warning: pointer targets in passing argument 1 of ‘strcpy’ differ in signedness
gui_lib.c: In function ‘hpt_check_autorebuild’:
gui_lib.c:1553: error: ‘MAX_ARRAY_PER_VBUS’ undeclared (first use in this function)
gui_lib.c:1553: warning: comparison between pointer and integer
gui_lib.c:1555: warning: implicit declaration of function ‘ArrayTables’
gui_lib.c:1555: warning: assignment makes pointer from integer without a cast
gui_lib.c:1555: error: ‘union <anonymous>’ has no member named ‘array’
gui_lib.c:1555: error: request for member ‘dArStamp’ in something not a structure or union
gui_lib.c:1558: error: ‘union <anonymous>’ has no member named ‘array’
gui_lib.c:1558: error: request for member ‘rf_broken’ in something not a structure or union
make: *** [hpt.o] Error 1
```

---

### Post by kev000 on 2007-12-05
I'm having the exact same issue.  I finally got it to boot with the hdx=noprobe lines in my menu.lst.  If anyone has gotten this to compile, we would greatly appreciate the howto.

thanks

---

### Post by Sivart832z on 2007-12-05
I contacted HighPoint about this on August 14th and got the following reply:

Hello,

We are looking into problems reported with this kernel.
We will release new open source drivers to address this.

Regards,

HighPoint Technologies, Inc.

===

I just looked on their website and they still haven't released an updated driver. I ended up just purchasing a different card. It was more cost effective than spending any more time trying to figure things out. I certainly wouldn't recommend highpoint to anyone. They have had more than enough time to look into this and fix it. I'm sure that isn't the solution you're looking for though - sorry. If anyone actually figures out how to make a working driver, let me know, as I've still go the old card just sitting around.

---

### Post by screaminglucy on 2008-01-05
I have Highpoint RocketRaid 454 which uses hpt374 driver.

I followed the howto at:
[http://stefan.freyr.org/?page_id=6]("http://stefan.freyr.org/?page_id=6")
with the latest driver from Highpoint

In the HOWTO among other things you have to blacklist the hpt366 driver in /etc/modprobe.d/blacklist. 

To get it working in the ubuntu 7.10 however I had to modify the source a little bit.

1. In entry.c I I added:

```
#define OS_KMAP_TYPE KM_BIO_SRC_IRQ 
```

to fix the OS_KMAP_TYPE undefined error

2. Commented out the include for  linux/config.h in hpt.c like so:
```
//#include <linux/config.h>
```

---

