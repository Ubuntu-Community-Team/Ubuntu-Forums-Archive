---
title: "AMD Ryzen 5000 APU support"
date: 2021-03-17
forum: Hardware
---

### Post by minhna on 2021-03-17
I just got a new ryzen 5000u laptop. It's HP HZAN (HP Probook 445 G8) with ryzen 5800u. The problem is the system doesn't reccognize the GPU. I can't set the screen brightness, hdmi port doesn't work. usb-c either

I tried Ubuntu 20.04, 20.10 and the linux 5.11.6 kernel but not any of them works properly.

Thank you.

---

### Post by TheFu on 2021-03-17
Welcome to the bleeding edge. If you want an easier time with any Linux distro, it is best to wait 6-12 months for the distros to catch up with the newest hardware.  Before you try 5.12, be certain you read all the warnings about data loss from Linus.  At least with AMD, the vendor will try to get current GPU drivers into the kernel tree at some point.

Back when Ryzen was first available, there were a number of Linux issues.  Until a number of kernel developers actually got their hands on the hardware, they didn't do too much. It is very hard to make software for hardware you don't have.

---

### Post by minhna on 2021-03-17
Thank you for your reply. You are right, I use Ubuntu as the only one OS since 8.04 LTS released. My last Windows OS was Xp. It's 13 years ago. It's okay when you use a laptop 2 - 5 years old but but when you have opportunity to get the latest and fastest laptop then you feel the pain.
I don't want to go back to windows. Hopefully AMD and Linux kernel developers do something quickly.

---

### Post by minhna on 2021-03-18
WOW, after install the kernel 5.11.7 and latest `linux-firmware` 1.187.10 but the it doesn't solve the problem. I google something and found this post: [https://forums.linuxmint.com/viewtopic.php?f=49&t=336958](https://forums.linuxmint.com/viewtopic.php?f=49&t=336958) Then I tried to comment out the

[HTML]blacklist amdgpu[/HTML]

in

[HTML]/etc/modprobe.d/blacklist-amdgpu.conf[/HTML]
then run the command

[HTML]sudo modprobe amdgpu[/HTML]
BOOM, it works. Now I can change the screen brightness, HDMI port works. AWESOME.

---

### Post by ajgreeny on 2021-03-18
**Great news! **

Please mark as **SOLVED** from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to other users searching the forum.

---

### Post by mastablasta on 2021-03-18
why is AMDGPU driver blacklisted for loading/probing on new install? just because the kernel doesn't recognise the hardware?

---

### Post by TheFu on 2021-03-18
a) thanks for posting a solution that you found
b) Please help the community by using the "Thread Tools" button to make it SOLVED, so the community knows.

Out of curiousness, did you ever run **sudo ubuntu-drivers autoinstall** or use the "Look for proprietary hardware drivers" in the GUI?
In theory, that should have accomplished the same things you've manually done.  It would be good to understand if there is a flaw in that in 20.10 and later.

---

### Post by minhna on 2021-03-23
The problem solved. Sorry for late updating.
I tried to install Ubuntu again:
1. Install new/fresh Ubuntu 20.04
2. Install 5.11.7 kernel
3. Reboot => It works.

---

