---
title: "Reboot during automatic updates?"
date: 2009-04-01
forum: Installation &amp; Upgrades
---

### Post by oudalrich on 2009-04-01
Hello everybody,

does anybody know what Ubuntu will do if automatic updates are enabled ("Install security updates without confirmation" ticked in Software Sources) and the user reboots or shuts down the machine while it's being updated? Will it shut down after the update is done? Or warn that an update is running? Or just shut down and thus risk breaking the system? [This]("https://answers.launchpad.net/ubuntu/+question/31423") question on launchpad seems to suggest that at least in the case of manual updates, Ubuntu will happily reboot and mess things up badly.

Thanks in advance for your answers!

EDIT: I just tried this in a virtual machine. While the automatic update was running, I shut down the VM using the fast user switch applet. The shutdown happened immediately, no questions asked. There seemed to be no problems when I booted the VM afterwards, but this behaviour does not seem safe to me.

---

