---
title: "usb 2.0 &amp; network issues"
date: 2008-12-26
forum: Hardware
---

### Post by jjgy on 2008-12-26
I'm running Ubuntu 8.10 on an eMachines T3612, which seems to have some major bios flaws.  After installation of Nvidia drivers, the processes kapcid and kacpid_notify began eating 99% cpu.  Booting with acpi=off fixed the issue, but disabled my network interface.  To fix this, I added irqpoll to the boot options, but noticed that USB 2.0 seemed to stop working.  Transfers worked, but at speeds < 900kb/s.  Also, the network interface cuts out randomly and my cpu spikes for a few seconds, but a reconnection to the network fixes this.  

At this point, I added routeirq to the boot options, which seems to have fixed the network issues and returned usb to full speed, but I lose all usb and network functionality roughly 30 minutes into my session.

Any ideas?

---

