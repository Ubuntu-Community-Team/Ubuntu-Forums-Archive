---
title: "dual boot that is very unusual- please help"
date: 2009-01-16
forum: Hardware
---

### Post by larryweeks on 2009-01-16
I have a machine that has the ability to switch the drives in the bios. I can change which is read first. I have two hard drives, one has xp home and the other ubuntu 7.10 both work great. But I want to setup the grub to access the drives from startup. 
I have already edited the standard commands...Ubuntu sees its disk as hd0/0

the xp just starts up when first. In actuality my second physical drive is the ubuntu one. 
Will i have to switch them physically or can i leave it set to start on the second drive so ubuntu will start grub and then choose xp or what?

I cannot get grub to recognize xp drive on startup.

---

### Post by pizmooz on 2009-01-16
What you want to do is set the HD with Ubuntu on it as the first disk in the boot order in the BIOS.  Then configure grub to boot the HD with windows on it, you'll need to use the invoke chainloader from grub to do this.  If you post your menu.lst file we can help you configure it.  So post the output of:
```
cat /boot/grub/menu.lst
```

---

### Post by logos34 on 2009-01-16
Set the ubuntu drive first in the bios hard disk boot priority and boot into it.  Edit the windows entry [like this]("http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk"), so you can boot XP on the other drive without having the manually change the Bios order everytime.

enjoy

---

