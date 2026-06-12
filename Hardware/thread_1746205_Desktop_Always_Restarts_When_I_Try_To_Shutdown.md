---
title: "Desktop Always Restarts When I Try To Shutdown"
date: 2011-05-01
forum: Hardware
---

### Post by geever27 on 2011-05-01
So I haven't been using Ubuntu very long, just since 10.04. I built a desktop a while ago:

Gigabyte H55M-D2H Motherboard
Intel Core i3 540
Western Digital 1.5TB Hard Drive

I dual booted Windows 7 and Ubuntu 10.10. With Windows I can always shut down no problem, but with Ubuntu 10.10 whenever I would try to shutdown, it would just restart the computer. I thought that maybe it would be fixed in 11.04, but the problem remains. 

I've tried changing in grub: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
to
GRUB_CMDLINE_LINUX_DEFAULT="quiet acpi=force"

But that doesn't work. I've also tinkered with my BIOS settings, but I cant find a solution.  Any ideas?

---

### Post by superdaveozzborn on 2011-05-01
i to am having this problem after update a few days ago. i have 6 dell dimension L1000R pcs and now none of them will shutdown properly. I have to do "sudo init 0" to get them to compleatly power down, did the above with no results.:popcorn:
 
 
p.s. my HP Pavilion dv6 is working fine with all updates.
 
oh ya and all are running ubuntu 10.10

---

### Post by jspiers on 2012-06-09
I'm also having this problem, running UbuntuStudio 11.10.  Has anyone figured out a solution yet?

---

