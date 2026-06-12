---
title: "Brigded Network --&gt; 8.10 Virtualbox"
date: 2008-09-08
forum: General Help
---

### Post by Peque on 2008-09-08
Hey Guys. 

I've just installed the upgrade to 8.10 - and ran into a problem with VMware - so instead I installed VirtualBox. 

BUT - I NEED brigded networking at work - so tried the Documentation - But haven't been able to make it work - So have someone else made it work here ?? 
The docs I've tried: 
[https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)

Can someone give me a hint in the right direction??? 
Thanks

---

### Post by forger on 2008-09-08
Their manual covers a lot of "how to" concerning networking:
[http://download.virtualbox.org/virtualbox/2.0.0/UserManual.pdf](http://download.virtualbox.org/virtualbox/2.0.0/UserManual.pdf)

Otherwise, you might want to try [VMWare Server]("http://www.vmware.com/products/server/"), it comes with pre-installed bridged networking (I think)

..or you could even try the kvm:
[https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM)

---

### Post by Peque on 2008-09-08
Well - The problem I ran into with VMware - is that the kernel in 8.10 is NOT compiling the vmmon - and it won't start and from the docs there's no solution yet - otherwise I've haven't tried anything else. 
But I cannot make a roolback and needing the machine monday morning at work ? 
So No VMware -unless the problem is solved.

The problem is - can you have a virtual network interface - which gets its own seperate IP-address from DHCP and afterwards make it connected directly to that interface ??? But haven't got a clue about how I do that trick??

---

