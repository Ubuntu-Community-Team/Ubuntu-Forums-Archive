---
title: "Change Ownership on Paritions using udev"
date: 2009-09-09
forum: Hardware
---

### Post by russell-ault on 2009-09-09
Basically, I want to permanently set user:group permissions on a specific partition. As near as I can tell, by default all partitions are assigned root:disk ownership. From what I've seen what I want to do is to create a udev config file that tells the system to change ownership on "/dev/sda1" to root:vboxusers instead of the default root:disk, but I don't have any udev experience and the code examples I've seen are confusing me quite a bit. Can anyone help me?


Full details:
I have VirtualBox up and running and I want it to be able to access a physical ("raw") partition that contains a Windows XP installation. As far as VirtualBox is concerned this isn't particularly difficult to set up.

The problem is that the XP partition (/dev/sda1) is assigned root:disk ownership by default, and any changes to ownership revert to default when the computer is rebooted. Conversely, I don't want a normal user added to the group "disk" (this strikes me as being an enormous security risk), so I am trying to figure out how I can configure udev to change this particular partition's ownership to root:vboxusers.

---

