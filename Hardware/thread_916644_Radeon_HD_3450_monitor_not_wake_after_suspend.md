---
title: "Radeon HD 3450 monitor not wake after suspend"
date: 2008-09-11
forum: Hardware
---

### Post by grege on 2008-09-11
I decided to replace my Nvidia 8400GS as it has a minor hardware fault and purchased an ASUS EAH3450 pcie card.

Installation was straight forward with a minor tweak to get the fglrx driver to work with xv.

BUT, it puts the monitor into standby as it should but no amount of wiggling the mouse or tapping the keyboard will wake it up. The computer is still running fine, the xserver is no longer responding properly. I can ctrl-alt-bkspce to kill x and the monitor comes back on at the log in screen.

"sudo vbetool dpms off" works and "sudo vbetool dpms on" works as well, the monitor fires up and x is working, even though you cannot see what you are typing to achieve it.

I grabbed the latest fglrx from ATI, made a deb and installed - same issue.

I think I might be able to alter one of the acpi scripts to use vbetool to overcome this issue, but before I do that - does anybody have a solution?

:(

---

