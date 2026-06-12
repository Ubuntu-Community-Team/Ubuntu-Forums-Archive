---
title: "What is ubuntu virtual machine host?"
date: 2009-08-31
forum: Installation &amp; Upgrades
---

### Post by kameelperdza on 2009-08-31
When i install ubuntu 9.04 server i get this option that i can install virutla machine host.
 
What is that? Can i install windows inside linux to run windows applications?

---

### Post by zvacet on 2009-08-31
I think [this]("https://help.ubuntu.com/community/JeOS") will give you some answers.Yes,you can install Windows in virtual machine.

---

### Post by lptr on 2009-12-02
Hi,

I read this JeOS article, but it seems not to answer the question. I also would like to know what Virtual Machine Host is for.

As I know VMware workstation running on a Linux or Windows box (Fusion on Mac behaves something differently) I am wondering, how this does work and what is needed to get things run.

Does this mean:
Ubuntu does provide with this, some sort of virtualization engine on top of hardware, needed to install VMware server.

Or is VMware selling with their server solution another method to be placed directly on top of Intel VM technology so that Ubuntu server pluggs into this.

I do remember something about XEN as a virtualization platform (hypervisor??). Was pretty abstract for me that time of reading.

Could pls anyone clarify what this stuff can do - what it does provide and what additional products (f.i. payware from VMware) are needed to get things working for different OSs to be installed on one server box?

Thanks

rob*

---

### Post by hewhocutsdown on 2009-12-02
It's a KVM setup

---

### Post by BigBananaMan on 2010-11-04
I believe it creates virtual Ubuntu machines complete with their own virtual processor and separate kernel.  [https://help.ubuntu.com/community/KVM/Installation](https://help.ubuntu.com/community/KVM/Installation)

---

