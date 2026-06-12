---
title: "Best to use built-in Ubuntu drivers, or compile from Intel/LSI? How about irqbalance?"
date: 2014-04-26
forum: Hardware
---

### Post by paraviz on 2014-04-26
Hello there world of Ubuntu,

I've been running Ubuntu server for a few years in production as a VM host and also iSCSI server.  (Two thumbs up!)  Just spent the past week and a half upgrading all of the VMs to Trusty Tahr (14.04), leaving the VM host and iSCSI server at Saucy Salamander (13.10).  After all the VM upgrades, and before I rebuild the physical boxes from scratch, I want to ask a couple questions that have been on my mind for quite a while.

- Is it a best practice to compile drivers using the manufacturer or vendor's most recent release, or should I stick with the provided Ubuntu drivers?

The hardware in question is an Intel RS25SB008 RAID card (built on LSI 2208), Intel X540-T2, and Intel I350-T4.  Being about as far from a hardware guru as you can get, I would truly appreciate some valuable tips on the matter.

My concerns started recently with the dual-CPU VM host, equipped with an Intel X540-T2 directly connected to the iSCSI server (also using X540).  The X540 seems to struggle with irqbalance and distributing the interrupts across both physical processors.  In syslog: "irq 227 affinity_hint subset empty".  I don't recall ever seeing this until re-compiling a newer version of the Intel-provided drivers after running an "apt-get dist-upgrade".

- Should I disable irqbalance?  How necessary is it?
- Are the warnings benign, or should I be concerned about the hardware's ability to live peacefully together?

Thanks to all for any advice or wisdom!  Take care.
~Laz

---

