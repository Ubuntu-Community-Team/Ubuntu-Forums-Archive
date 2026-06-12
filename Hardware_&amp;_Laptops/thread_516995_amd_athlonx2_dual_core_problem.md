---
title: "amd athlonx2 dual core problem"
date: 2007-08-03
forum: Hardware &amp; Laptops
---

### Post by porl on 2007-08-03
hi there. i have searched through other posts about this but none of them seem to help.

i have just recieved a computer with an athlon x2 processor. unfortunately it appears only one core is being used:

$ cat /proc/cpuinfo 
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 43
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 4200+
stepping        : 1
cpu MHz         : 1000.000
cache size      : 512 KB
physical id     : 0
siblings        : 1
core id         : 0
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt lm 3dnowext 3dnow up pni lahf_lm ts fid vid ttp
bogomips        : 2001.61
clflush size    : 64

i am running feisty and am currently using the lowlatency kernel, but the generic kernel had the same problem when i tried it as well.

i don't know if this helps, but i'm not sure if this is normal:

$ dmesg | grep SMP
[    0.000000] Linux version 2.6.20-16-lowlatency (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP PREEMPT Thu Jun 7 20:23:03 UTC 2007 (Ubuntu Unofficial)
[    0.000000] found SMP MP-table at 000f5ad0
[   50.648616] SMP alternatives: switching to UP code
[   50.648813] Freeing SMP alternatives: 9k freed

any suggestions?

thanks in advance

porl

---

### Post by killroy on 2007-08-13
I'd just like to say that you're not alone... if it makes you feel any better... I'm having the same problem with an AMD athlon x2 3800+.

~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 75
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
stepping        : 2
cpu MHz         : 2009.281
cache size      : 512 KB
physical id     : 0
siblings        : 1
core id         : 0
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow up pni cx16 lahf_lm cmp_legacy svm extapic cr8legacy ts fid vid ttp tm stc
bogomips        : 4028.67
clflush size    : 64

~$ dmesg | grep SMP
[    0.000000] Linux version 2.6.22-9-generic (buildd@palmer) (gcc version 4.1.3 20070718 (prerelease) (Ubuntu 4.1.2-14ubuntu1)) #1 SMP Fri Aug 3 00:50:37 GMT 2007 (Ubuntu 2.6.22-9.25-generic)
[   36.542431] SMP alternatives: switching to UP code
[   36.542602] Freeing SMP alternatives: 11k freed
[   36.821800] SMP motherboard not detected.

~$ uname -a
Linux hound 2.6.22-9-generic #1 SMP Fri Aug 3 00:50:37 GMT 2007 i686 GNU/Linux

Gnome system monitor shows only 1 cpu.

I'm using the generic kernel as shown above.  When i'm booting, it says it detects 2 cpus, so my mobo is dual cpu compatible (and it says so on the box).  Also, i'm using the latest Gutsy release (tribe 3 as of now), but I can only boot using noapic, nolapic, irqpoll commands.  Maybe related?  Any help is... helpful.

---

### Post by shad0w_walker on 2007-08-13
I have a Athlon X2 here, no problem like this but i would suggest you check your grub config files to make sure there isn't an option such as nosmp enabled. If you have windows installed as well, does windows detect the second core?

As for your having to boot with noapic have a check to see if there is a bios update for your motherboard, i had exactly the same problem, fixed with an update. If memory serves it was a bug in the original specifications that never got fixed before shipping, the update should help out with the apic side atleast.

---

### Post by killroy on 2007-08-14
> I have a Athlon X2 here, no problem like this but i would suggest you check your grub config files to make sure there isn't an option such as nosmp enabled. If you have windows installed as well, does windows detect the second core?

Grub only has noapic, nolapic, and irqpoll options.  I just updated BIOS yesterday and still no go.  I'd hate to resort to booting windows again (I had to install it to update BIOS as I have no floppy drive), but I might have to.  Thanks for the suggestions, shad0w_walker.

*Just booted windows (in under 10 seconds) and it does show both cpus are being used.  It took 5 minutes and 15 seconds for Ubuntu to boot, after having to alt+ctrl+backspace (ouch!).  I don't think I like this new kernel.

I did notice that in "/sys/devices/system/cpu" there is only the "cpu0" folder and not a "cpu1" folder, while I did try to make a new folder using sudo, it gave me a permission denied error, so I thought that messing with stuff in that directory might harm my hardware, so I stopped.

---

### Post by Handssolow on 2007-08-14
Same here. I changed my motherboard recently but kept running Feisty 2.6.20-16-386 so I expected my system wasn't optimal. Perhaps generic might be better.  I'll  also  check what's on my 64 bit Ubuntu on the other hard drive.
Anyway here's what I've got on my 32 bit 386 Ubuntu.
 
$ cat /proc/cpuinfo 
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 35
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 4200+
stepping        : 2
cpu MHz         : 1000.000
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni lahf_lm cmp_legacy ts fid vid ttp
bogomips        : 2001.35
clflush size    : 64

$ dmesg | grep SMP
[    0.000000] found SMP MP-table at 000ff780
[    0.000000] Using ACPI (MADT) for SMP configuration information

My "/sys/devices/system/cpu" has only cpu0 visible.

---

### Post by Handssolow on 2007-08-14
My /var/log/kern.log has this which seems significant-
Aug 14 15:41:07 localhost kernel: [    0.000000] Processor #0 15:3 APIC version 16
Aug 14 15:41:07 localhost kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Aug 14 15:41:07 localhost kernel: [    0.000000] Processor #1 15:3 APIC version 16
Aug 14 15:41:07 localhost kernel: [    0.000000] WARNING: NR_CPUS limit of 1 reached.  Processor ignored.

---

### Post by Handssolow on 2007-08-14
A quick Google before my bedtime suggests we might need a Linux kernel with a SMP tweek.

---

### Post by shad0w_walker on 2007-08-14
I believe that the generic kernel option would be the best choice, to my knowledge it has SMP enabled by default along with a few other things.

---

### Post by davidsrsb on 2007-08-14
The standard kernel works for me with a X2 5200 on Asus motherboard

---

### Post by Handssolow on 2007-08-15
I'm reading in the forum that generic is essentially the 386, so I'm not sure what to consider next. I've an Asrock 939 Dual-Vsta with  AMD Athlon 64 x2 4200.
Has anyone been through a process to enable their second cpu to function running 386?

---

### Post by Handssolow on 2007-08-15
Looks like this issue might be linked to [this](http://www.segundanariz.com/ubuntu/?p=44).

---

### Post by shad0w_walker on 2007-08-15
I'm pretty sure this isn't the problem. Hyperthreading (If memory serves) is a Intel technology so wouldn't matter with AMD chips. Also having run my dual core straight of the box with out doing anything this doesn't look like a matter of default configurations.

---

### Post by davidsrsb on 2007-08-15
I think that Hanssolow is thinking that Ubuntu is treating the (real) 2nd core as being the (partial) hyperthreading core in error.

---

### Post by nss0000 on 2007-08-15
Gents:

Running Dapperx64 ( std kernel ) on AMD5400+/ASUS-m2n with both processors cranking as needed. Seems that CPU usage/speed is automagically determined by applied 'load'.

---

### Post by Handssolow on 2007-08-15
I hear the message about hyperthreading being an Intel feature not with AMD based systems. We need another answer.
Some observations about my own 32 bit Feisty version.
$ cat /proc/cpuinfo
does not list the line, cpu core, a line which others have reported, but at least I seem to have got SMP features recognised.
next up my  /var/ log/kernell.log has this line-
WARNING: NR_CPUS limit of 1 reached.  Processor ignored.

It's not just about "Quiet and Cool" I have only one cpu core enabled under Feisty whilst I should have two?

My 64bit Feisty lists my two cpu cores and no error messages in the /var/ log/kernel.log.

---

### Post by Handssolow on 2007-08-18
As an experiment I booted up a  live CD of Feisty 386 desktop to see if both my AMD cpu cores would be recognised.
uname -r showed the kernel was 2.6.20-15 -generic
System Log>kern.log showed both of my cpu cores appeared to be recognised and functional.

So what's happening with my installed 2.6.20-386 version? Why is only one cpu core working and the other ignored? Was it because I upgraded from earlier Ubuntu versions and/or me changing motherboard with an AMD 64 without a fresh install?

---

### Post by Spartan.II.117 on 2007-08-18
the 386 version does not recognise 2 cpu's, you need to switch back to generic, generic and 386 are simaler but not the same.

---

### Post by Handssolow on 2007-08-18
Not much progress to report since changing from 386 to generic. Rather than use Synaptic I chose sudo apt-get linux-generic in the terminal. I noticed two messages in the terminal during the process- 
W: mdadm no array defined in configuration file
W: falling back to emergency procedure in initramfs

I'm not sure of the significance of this or what needs to be addressed.

There was also a message to follow the instructions in /usr/share/doc/grub/News.Debian.gz about the need to update the file /etc/kernel-img.conf before Etch stable is released/. This I've now done.

But I'm still only using one cpu core even though I've changed to 2.6.20-16-generic. So I checked again with a Feisty live CD and I've two cores active.

I've just noticed that cat /proc/cpuinfo now shows I've two cores recognised.
kernel.log still reports that one of the processors is being ignored.
Also 
$ dmesg | grep SMP

[    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Thu Jun 7 20:19:32 UTC 2007 (Ubuntu 2.6.20-16.29-generic)

[    0.000000] found SMP MP-table at 000ff780

[    0.000000] Using ACPI (MADT) for SMP configuration information

[   21.285563] SMP alternatives: switching to UP code

[   21.585296] SMP alternatives: switching to SMP code

[   38.796000] apm: disabled - APM is not SMP safe.



Any suggestions?

---

### Post by Handssolow on 2007-08-18
Thanks Spartan.II.117 as you suggested changing to the generic kernel means I am using both cores of my AMD 64. After a cold restart I noticed that System Monitor Resources  showed both cpu 1 and cpu 2 active, this too was confirmed in my kernel.log. Not sure why it needed a cold reboot to get things working.
Now cat /proc/cpuinfo has data on both processors though $ dmesg | grep SMP shows the same as in my last posting.

---

### Post by porl on 2007-09-04
sorry i took so long to respond. i have been away from this pc a while.

finally got a bios update working, so i am updated to the last bios update they did for this m/b.

still get the same problems:

porl@euclid:~$ cat /proc/cpuinfo 
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 43
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 4200+
stepping        : 1
cpu MHz         : 2200.346
cache size      : 512 KB
physical id     : 0
siblings        : 1
core id         : 0
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt lm 3dnowext 3dnow up pni lahf_lm ts fid vid ttp
bogomips        : 4403.47
clflush size    : 64

porl@euclid:/sys/devices/system/cpu$ dmesg | grep SMP
[    0.000000] Linux version 2.6.20-16-realtime (root@godzilla) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP PREEMPT Fri Jun 15 04:43:25 CEST 2007 (Ubuntu 2.6.20-16.29-realtime)
[    0.000000] found SMP MP-table at 000f5aa0
[    0.000000] Using ACPI (MADT) for SMP configuration information
[   47.514843] SMP alternatives: switching to UP code
[   47.515058] Freeing SMP alternatives: 9k freed


i can't try windows on here as it isn't installed (and this machine is too important at the moment to install it on, as i need every bit of free space available to me).
i have tried realtime, lowlatency and the generic kernels to be sure it wasn't an issue with the lowlatency/realtime variants and even tried using the official feisty livecd to no avail.

i'm beginning to think there may be a hardware issue. i might have to bite the bullet and install windows on another hd or something :(

porl

---

