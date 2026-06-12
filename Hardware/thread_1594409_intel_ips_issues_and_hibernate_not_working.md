---
title: "intel ips issues and hibernate not working"
date: 2010-10-12
forum: Hardware
---

### Post by Orion2000za on 2010-10-12
on Kubuntu 10.10 Maverick. System used to be 10.04, made a fresh install.

in konsole command dmesg would repeatedly give output:
intel ips 0000:00:1f.6: MCP power or thermal limit exceeded

Further hibernate did not work, something I suspect related to above issue. 

Googling around various kernelforums indicated a kernel issue but no immediate solution in sight. 

Eventually I installed a higher kernel from mainline  kernels ppa:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36-rc7-maverick/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36-rc7-maverick/)

this solved both issues. Note my wireless Broadcomm works as does VirtualBox with this kernel. 

hope this helps someone out there...

---

