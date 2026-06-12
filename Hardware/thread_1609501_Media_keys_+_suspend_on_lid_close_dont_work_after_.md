---
title: "Media keys + suspend on lid close dont work after suspend"
date: 2010-10-30
forum: Hardware
---

### Post by akshayas1986 on 2010-10-30
I have Ubuntu 10.10 running on a Dell Studio 1458. This is what I have noticed.

All keys including multimedia keys work fine when you boot the machine (Restart or power on your laptop). When you close the lid, it suspends for the very first time. But once you open the lid, all the multimedia keys stop responding. This can be verified by going to System -> Preference -> Keyboard Shortcuts. If you try to reassign the multimedia keys to their usual control, the multimedia key don't respond. 

Similarly, if you try to close the lid, the system does not suspend either. It remains turned on. Any ideas on how to fix it?

---

### Post by akshayas1986 on 2010-11-01
Bump!

Also I noticed that if I restart xwindows (Ctrl + Alt + Backspace), the media keys and "suspend on closed lid" start working again. Again, if you suspend the system, they stop working.

---

### Post by akshayas1986 on 2010-11-01
Ok there is a bug posted for this issue. The link is given below

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/657338](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/657338)

---

### Post by akshayas1986 on 2010-11-01
There is an exception though. The media key associated with F12 works fine. All other hotkeys dont work after one suspend.

---

