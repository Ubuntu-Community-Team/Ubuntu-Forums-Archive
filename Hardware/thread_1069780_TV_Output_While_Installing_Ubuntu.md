---
title: "TV Output While Installing Ubuntu"
date: 2009-02-14
forum: Hardware
---

### Post by hem_ker on 2009-02-14
I'm trying to install Ubuntu 8.10 for the first time.  The issue I'm running into is that I don't have a monitor as I use my TV as my monitor.  When I try installing Ubuntu I can only get so far.  From everythign I can see the [ATI Linux Driver package ]("http://ati.amd.com/support/drivers/linux/linux-radeon-prer200.html")looks like it should work, but apparently it's not bundled with the installation.  

Any ideas besides buying a monitor?

---

### Post by rob356 on 2009-02-14
I'm in the same boat. First, do you have a second computer? if you do then follow these steps. 
Use the Alternate installation CD. Once you get it installed from that cd, you will have to use the recovery mode option when you boot up. Then choose the root shell option. Once in the shell type 
```
sudo apt-get install openssh-server openssh-client
```
then reboot into normal mode.
Post back here how that went and I will tell you what to do next. Is that other computer Windows, Linux, or Mac?

---

### Post by hem_ker on 2009-02-15
Thanks for your reply ... I'm having second thoughts and don't think I'm going to make the switch over from Windows yet.  I'm sure there are others out there, so I'm assuming this thread will help many others if you can continue it.  Thanks again!

---

