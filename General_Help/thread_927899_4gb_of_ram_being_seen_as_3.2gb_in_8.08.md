---
title: "4gb of ram being seen as 3.2gb in 8.08"
date: 2008-09-23
forum: General Help
---

### Post by ali_williams on 2008-09-23
Hey guys,

I just bought 4gb of ram when i am on boot up my pc it sees all 4gb and I am running Ubuntu 8.04 32bit and it only sees it as 3.2gb when i check in the system monitor. What did I do wrong???

---

### Post by hyper_ch on 2008-09-23
ntohing... by default you won't see all the 4gb ram on a 32bit system. So you have two options:

(1) recompile the kernel with PAE enabled or install and use the server kernel

or

(2) install a 64bit system.

Besides, there is no 8.08 version. Normal releases are in april and october... to that leads to x.04 and x.10 (the exception is dapper as 6.06)

---

### Post by ali_williams on 2008-09-23
> **hyper_ch said:**
> ntohing... by default you won't see all the 4gb ram on a 32bit system. So you have two options:

(1) recompile the kernel with PAE enabled or install and use the server kernel

or

(2) install a 64bit system.

Besides, there is no 8.08 version. Normal releases are in april and october... to that leads to x.04 and x.10 (the exception is dapper as 6.06)

opps i meant 8.04. I will look at loading the PAE kernel do you think anything is going to blow up by doing this?

---

### Post by hyper_ch on 2008-09-23
nothing will blow up... but you'll have to recompile the kernel and then use that kernel to boot from (you still have the "normal" ones onto which you can fall back if it doesn't boot (properly).

Simplest way would be to install a 64bit OS...

---

### Post by Titan8990 on 2008-09-23
Do you really have a need for the extra RAM?

---

### Post by hyper_ch on 2008-09-23
800mb = 1 VM ;)

---

### Post by Titan8990 on 2008-09-23
Yes, but you could easily run a VM with less, depending on what OS the VM is running.

---

### Post by ali_williams on 2008-09-23
i found a good tutorial 
[http://www.ubuntugeek.com/how-to-use-more-than-3gb-ram-on-32-bit-ubuntu.html](http://www.ubuntugeek.com/how-to-use-more-than-3gb-ram-on-32-bit-ubuntu.html)
after doing this it worked
Also the reason for that much ram is that I run vmware with 3 Windows Sever OS's 1 winxp and 2 ubuntu servers. So for most of the day I am in VMWARE so because i normally run 2 or 3 of these vm's at one time i wanna make sure I am getting the most out of my pc.

---

### Post by hyper_ch on 2008-09-23
you changed from the generic to the server kernel. The server kernel has PAE enabled by default however it has some other settings that one could call not that desired on a desktop... but if you don't notice and performance drop then it's ok...

And I was right about the VMs... it was just a guess ;)

---

### Post by Titan8990 on 2008-09-23
Lucky you....

---

