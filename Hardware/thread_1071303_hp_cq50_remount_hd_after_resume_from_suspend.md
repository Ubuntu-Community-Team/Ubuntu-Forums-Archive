---
title: "hp cq50 remount hd after resume from suspend"
date: 2009-02-16
forum: Hardware
---

### Post by fuzzyworbles on 2009-02-16
Hopefully not the same sad story of not being able to suspend laptops. normally the problem is with video cards and wifi. in the past i've been able to work around those hiccups, but this is the first time i've had a problem with a hard drive not remounting (?) when resuming from suspend.

upon resuming, i have to go to a virtual console (ctrl alt f1) because all i get is my mouse on X, nothing else. in the virtual terminal, when i try to login, it tells me this over and over again: 

end_request: I/O error sda sector [number]

at first i flipped out thinking that the hd on my new laptop was failing. so i did a read/write test w/ fsck and everything is fine. no bad clusters. 

the only thing i can think of is that pm-utils isn't remounting my hd or something.

it looks like laptop-mode.conf and acpi-support.conf are both configured correctly.

could anybody suggest what else i could look into to get her to remount on resume (if that is indeed what's happening)?

model is a hp cq50-116la

btw, i've googled the hell out of this with no avail. closest thing i found was [http://ubuntudemon.wordpress.com/category/english/page/2/]("http://ubuntudemon.wordpress.com/category/english/page/2/") but i don't think it's applicable.

---

### Post by fuzzyworbles on 2009-03-22
hooray! after some time searching, i found [http://bugzilla.kernel.org/show_bug.cgi?id=11178]("http://bugzilla.kernel.org/show_bug.cgi?id=11178") where there's a post suggesting that I include pci=nomsi as a kernel boot option. it worked! i can now standby and hibernate the compaq cq50-116LA. i guess nvidia (once again), the maker of my sata controller, is to blame.

---

