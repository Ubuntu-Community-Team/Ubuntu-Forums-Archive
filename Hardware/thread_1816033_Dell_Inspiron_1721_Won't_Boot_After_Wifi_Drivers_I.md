---
title: "Dell Inspiron 1721 Won't Boot After Wifi Drivers Install"
date: 2011-08-01
forum: Hardware
---

### Post by bkuhns on 2011-08-01
I've been trying to get Ubuntu to work on my brother's Inspiron 1721. It has a Dell-branded Broadcom 43xx wifi card in it. Ubuntu (11.04 Natty 32-bit) installs and runs great, until you attempt to install the restricted Broadcom drivers. After restarting the laptop, it hangs at the purple "Ubuntu" Plymouth screen.

I did some googling and it seemed like people were using Ubuntu on this model laptop just fine with older versions, so I gave 10.04.3 LTS (32-bit) a shot and... tada! Everything works fine even with wifi drivers installed. I decided then to upgrade to 10.10, after restarting, it wouldn't boot again. I tried the second entry for Ubuntu in the GRUB2 list so it would boot 10.10 using the same kernel as 10.04 and it works! Here are the kernels:

2.6.35-30 -- Doesn't work
2.6.32-33 -- Works!

Any ideas what I can do to debug this issue? I could just leave him with 10.04.3 and be done with it, but I feel like this is a fixable regression in the kernel or Broadcom drivers. I'm just not sure where to go from here. Thanks for any advice!

---

### Post by TBABill on 2011-08-01
If your goal is to end up on 11.04, instead of installing the OS and then adding the driver, add the driver up front during the live session. This will result in you having a fully operational kernel and system on the first boot.
 
To do so, and assuming you use the STA driver, run the live session. Enable the STA driver but when it says to restart, don't do that. Just open a terminal and ```
sudo modprobe wl
``` Wait a bit and see if your network is listed. If it is, the system will still appear as though it needs a restart (the blue circular arrow on the task bar)...just ignore it. Once you verify your connection via wireless is working, then go through the install process using only wireless, not wired connection. When you restart to complete the full install you should have a working wireless connection.

---

### Post by bkuhns on 2011-08-01
Interesting! I didn't realize that would work. I saw instructions similar to that in the Ubuntu Wiki, but didn't think it would persist after the install. I'll give that a shot and report back.

---

### Post by TBABill on 2011-08-01
The wiki also tells you how to do it without even connecting to ethernet. That works as well, but don't restart. Use the same modprobe command I listed and enjoy.

---

