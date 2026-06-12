---
title: "Ubuntu 9.04 boot problem"
date: 2009-07-06
forum: Installation &amp; Upgrades
---

### Post by amsum on 2009-07-06
I am fresh installing Ubuntu 9.04.
My system: 2.4GHz 32 bit AMD, 1GB RAM, NVidia Geforce, 160 GB HDD
My Requirement: 18GB Root, 2GB Swap, 60GB Home, 40GB /usr, 40GB /var (all in Ext4 File System except Swap)

But these are the problems I faced during installation:
1) During Live CD install, the interface was half visible and it was stretched below my monitor's visible area. So, the [OK] or [Back] tab was not at all visible and I was moving to the next step blindly by pressing [Enter]. But after install and with all updates, it worked fine.
2) I messed up my Pysdm by [checking] some mouting options for /usr and /var partitions. Now my system is not booting and its halting inbetween with some messages
 
*Starting periodic command scheduler crond
start-stop-daemon: Unable to start /usr/sbin/cron: permission Denied (permission Denied)
.... fail
.
.
/usr/bin/sbin/dmidecode: Permission Denied

So, can you help me in recovering my Ubuntu with just commands or do I need to re-install Ubuntu.

I am not bother much about 1st problem but I would appreciate solution for 2nd one.

---

### Post by amsum on 2009-07-07
So nobody has clue? Looks like I will have to reinstall Ubuntu from scratch. One more development, I am getting one more option "Chainload into Grub 2" in Grub Bootloader Menu. What does it mean and what should I do.

I think I can solve my previous problem if I can access Pysdm Storage Manager from command prompt (during booting) and changing the permissions. Can you suggest me how to do that.

---

### Post by amsum on 2009-07-18
Alright guys, I re-installed and everything seems fine now.

---

