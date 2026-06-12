---
title: "Kernel panic ...  on copiing specific file"
date: 2007-04-28
forum: Hardware &amp; Laptops
---

### Post by djamu on 2007-04-28
On making a backup of a corrupt file system ( before running --rebuild-tree ) i'm getting a kernel panic. 
I've pinpointed it down ( trying copiing files manually > one by one ) to a specific corrupt file not wanting to be copied ( not move, copy, filesystem is read only ).

I got 2 questions, 

-Where do I find the log of the kernel panic ? ( is there one ? )


I'm a little worried that a corrupt filesystem can halt a computer / server.

- Is there a way to force a sytem to continue even after such a major error ? ( thinking of a server that should continue operating after such an event ? )

Whenever I find the log file, I'll attach it here
( it doesn't appear in any dmesg log)
[COLOR="Red"]
:Edit[/COLOR]
I could repeat this with the same file, but after I restarted samba on the remote fileserver to reset any possible filelocks the problem with this file disappeared. ( CIFS mounted partition on local computer )

Still, my local computer did freeze up on a similar earlier event causing the filelock on this specific file to be set.
I got about 6 kernel panics today, and meanwhile I disabled any apic / escd in my bios ( I first thought of a IRQ conflict )

hope not to be continued...... 

[COLOR="Red"]
:Edit[/COLOR]

well it still does freezes....  anyone ?

Thanks

---

### Post by WilliamAnderson on 2007-04-28
Hi djamu,

To answer your first question, it is not possible nor desirable to force a Linux system to try to continue after an error bad enough to cause a kernel panic. After an error this bad the kernel cannot assure the success of any operation reading or writing to RAM or the results of processor instructions, much less disk or network I/O. Under these conditions, it is safest for data integrity to hard crash rather then to try to write to disk.

Because there is no disk I/O, a kernel panic does not log anything. Instead it generates a crash dump containing the contents of RAM at the instant of the panic event. A debugger is then used to determine what function was running when the crash occurred and looking at the source code one can diagnose the problem. This is not something that can be easily explained in a forum message.

Fortunately. unless you are doing kernel development, the cause of your panics is most likely caused by a hardware problem. Examining a crash dump caused by a hardware malfunction can be useful or can be a colossal waste of time.

The first thing to do is to rule out the presence of bad RAM. Assuming that you are running a system that uses Intel x86 processors (or compatible), Ubuntu installed a utility called memtest86 that runs an intensive  test of the system RAM. If memtest86 finds a problem, that is likely the cause of your panics.

To access memtest86, restart the computer and press the 'Esc' key to access the boot menu when Grub prompts. Then select the “Ubuntu, memtest86+”  option and let the program run at least one complete pass. This will take tens of minutes to hours to run depending upon how much RAM the system has and how fast the system is. 

If memtest86 finds errors in the RAM, this must be fixed first and will likely resolve the problem. 

Note that this assumes that you are not doing kernel development or using a development or test kernel. If you are, then diagnosing the trouble will involve analyzing the crash dump (if the RAM tests out OK).

William

---

### Post by djamu on 2007-04-30
K thanks.
I'm not that familiar with linux kernels, but I do know something :) about hardware development.
Since I couldn't pinpoint the exact point of the kernel panic ( read I couldn't repeat the error ), failure should be either hardware / firmware. Knowing that electrical contacts corrode I cleaned & re-attached all connectors, removed the battery from the BIOS & CMOS reset....

It works just fine now...

---

