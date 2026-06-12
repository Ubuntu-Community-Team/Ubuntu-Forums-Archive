---
title: "kacpid &amp; kacpi_notify eating up CPU"
date: 2009-01-23
forum: Hardware
---

### Post by mexp on 2009-01-23
I've got this problem of kacpid & kacpi_notify processes eating up some 70-80% of CPU on my Latitude D620 running 8.10. I found out that this seems to be a kernel bug ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/280088](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/280088)) and that there is a patch available. 

So if I patch the kernel with a patch proposed on that bug report, how would that affect the future updates? What if that patch would not work, how would I revert to the old kernel? 

Or does anyone know of another workaround for this issue? 

Some forum posters suggested disabling acpi altogether, but then I saw that it would not work on dual core machines, as then only one core gets active. Also not sure how that would work with the fans, are they not run by BIOS? I guess disabling acpi would affect suspend too?

Thanks!!

---

### Post by mexp on 2009-02-22
Any ideas, anyone?!

---

### Post by nexus_2006 on 2009-03-04
Anyone?  I'm suffering the exact same issue....

---

### Post by leandromartinez98 on 2009-03-11
I have a cluster of 19 nodes build on ubuntu server 8.10 and one,
and only one of the nodes, displays the same problem. The nodes have the
same hardware. I don't know how to solve it.

Leandro.

---

### Post by leandromartinez98 on 2009-03-30
Actually I found out that, indeed, the CPU was heating up. Therefore, I found the problem because of those programs running and the messages they left on /var/log/messages. I'm not sure if they continuous and high-cpu usage is a bug. Reinstaling the CPU with a little more of that white paste solved the problem.

---

### Post by mexp on 2009-05-04
Well finally, this seems to be solved in Jaunty 9.04... Great :)

---

### Post by mezcla on 2009-05-10
I just installed Jaunty 64 bit and am having a problem with kacpid eating up 100% of cpu.  I have searched and tried deactivating acpi services to no avail.  Any help would be greatly appreciated.  I have run Dapper, Feisty, and Hardy in the past with no problem.

---

### Post by Sabrtooth on 2009-06-28
I'm runing Jaunty Jackelope 9.04 on my netbook and experience the same issues expressed here, but only when my laptop lid is closed.

At first I thought it had to do with heat of the processor, but it happens at any temperature. (I like how it looks with the lid closed on my desk) 

I'm going to dig around a bit more, but I wanted to say something when I saw this thread. I have the power options set to do nothing when the lid is closed in case that's a question on a potential solution provider's mind.

Any recommendations?

---

### Post by BubbaNW on 2009-10-25
I had the same problem with my D250.  When I closed the lid kacpid and kacpi_notify would spin up and eat 100% of my CPU, eventually leading to it overheating and freezing.  I did a bit of research and discovered that this has been identified as a BIOS issue ([http://bugzilla.kernel.org/show_bug.cgi?id=13802](http://bugzilla.kernel.org/show_bug.cgi?id=13802)).

I upgraded to the latest BIOS (available on the Acer support page), using the DOS install instructions inside the ZIP file from Acer, and these helpful step by step instructions on how to make a DOS bootable CD ([http://www.linuxinsight.com/how-to-flash-motherboard-bios-from-linux-no-dos-windows-no-floppy-drive.html](http://www.linuxinsight.com/how-to-flash-motherboard-bios-from-linux-no-dos-windows-no-floppy-drive.html)).  Search down in the comments for the one with "The following is a brief" as the subject.

The issue is now resolved for me.

Hope that helps.

---

