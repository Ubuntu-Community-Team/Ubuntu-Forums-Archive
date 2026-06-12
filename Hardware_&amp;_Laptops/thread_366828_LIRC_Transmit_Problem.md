---
title: "LIRC Transmit Problem"
date: 2007-02-21
forum: Hardware &amp; Laptops
---

### Post by SyvanX on 2007-02-21
I have functional mythtv (Edgy) box, with an IR blaster, it's been working fine since I set it up 6 months or so ago.  I decided to upgrade the kernel to 2.6.17-11-server from 2.6.17-10-server, because I have compulsion to keep apt happy.  

Now, after the upgrade, when I send a channel change command through a serial IR Transmitter, the transmitter lights up (it has a red led), but the command is not received by the cable box, the only difference is the change in kernel.  After upgrading, I ran the module-assistant commands to recompile the ivtv and lirc (0.8.0-9ubuntu0unofficial1 [superm1's repo]) packages.  My remote is working, the serial irblaster appears to be working.  
I know I had this problem the first time I installed mythtv on ubuntu, I just can't remember what the fix was, and I can't find a reference in the Community Help Documents.  I've searched the forums and google, and applied the ir-common.ko fix from hexion.

For now, I'm booting back into 2.6.17-10-server and the transmitter is working just fine.  If anyone has any idea it would be greatly appreciated.

---

