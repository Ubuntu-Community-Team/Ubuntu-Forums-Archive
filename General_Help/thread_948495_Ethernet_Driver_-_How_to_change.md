---
title: "Ethernet Driver - How to change?"
date: 2008-10-15
forum: General Help
---

### Post by JGillTech on 2008-10-15
I have a Ubuntu Server 8.04 virtual machine within my ESX cluster.  I just installed the VMware tools, however was not able to install the vmxnet driver.  I have the module loaded, along with the pcnet module.  Any suggestions?  Output from my machine: 

root@syndemic:~# lsmod | grep net
pcnet32                35460  0 
mii                     6400  1 pcnet32
vmxnet                 19328  0 
root@syndemic:~# 

output from "lspci"
00:11.0 Ethernet controller: Advanced Micro Devices [AMD] 79c970 [PCnet32 LANCE] (rev 10)
root@syndemic:~#

---

