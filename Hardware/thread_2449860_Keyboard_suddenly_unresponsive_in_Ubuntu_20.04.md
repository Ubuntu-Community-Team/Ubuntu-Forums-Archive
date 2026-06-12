---
title: "Keyboard suddenly unresponsive in Ubuntu 20.04"
date: 2020-09-03
forum: Hardware
---

### Post by tapasray on 2020-09-03
My Keyboard has suddenly become unresponsive in Ubuntu 20.04. I ran the terminal command given on [https://askubuntu.com/questions/1261848/20-04-mouse-click-and-keyboard-unresponsive](https://askubuntu.com/questions/1261848/20-04-mouse-click-and-keyboard-unresponsive). At first 19 packages were not upgraded. By using Synaptic, etc., I was able to upgrade 17 ofthose, but two are proving very stubborn. Because of this or for some other reason, the step did not solve the problem. The terminal output is below. Would appreciate help with this. Thanks.

abcd:~$ sudo apt-get install xserver-xorg-input-all
[sudo] password for abc: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xorg-input-all is already the newest version (1:7.7+19ubuntu14).
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
abcd:~$

---

### Post by drpjkurian on 2020-09-03
I presume that these two packages are kept back to prevent dependencies inconsistencies.

---

### Post by tapasray on 2020-09-03
> **drpjkurian said:**
> I presume that these two packages are kept back to prevent dependencies inconsistencies.

Ok!

---

### Post by tapasray on 2020-09-03
Following crip720's advice in another thread, I rolled back my kernel from version 5.4.0-45-generic to 5.4.0-42 generic. That solved the problem. That is, the keyboard is working again.

---

### Post by drpjkurian on 2020-09-05
> **tapasray said:**
> Following crip720's advice in another thread, I rolled back my kernel from version 5.4.0-45-generic to 5.4.0-42 generic. That solved the problem. That is, the keyboard is working again.

Good to hear that you resolved your issue. Hence please mark your thread as 'Solved'

---

### Post by tapasray on 2020-09-10
> **drpjkurian said:**
> Good to hear that you resolved your issue. Hence please mark your thread as 'Solved'

The problem persists with version 47. Starting a new thread.

---

### Post by tapasray on 2020-09-10
Like kernel version 5.4.0-45-generic, version 5.4.0-47-generic also does not recognize my laptop keyboard and touchpad. Luckily, I still have 5.4.0-42 generic, which does. But booting with 5.4.0-42 is very inconvenient, as the default is 5.4.0-47. I would appreciate it if something could be done about this problem.

---

### Post by P-I H on 2020-09-11
You may try to change grub to use GRUB_DEFAULT=saved and GRUB_SAVEDEFAULT=true
See this page
[https://askubuntu.com/questions/148662/how-to-get-grub2-to-remember-last-choice](https://askubuntu.com/questions/148662/how-to-get-grub2-to-remember-last-choice)

---

