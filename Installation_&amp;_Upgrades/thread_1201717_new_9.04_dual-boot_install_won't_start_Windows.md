---
title: "new 9.04 dual-boot install won't start Windows"
date: 2009-07-01
forum: Installation &amp; Upgrades
---

### Post by pjm90041 on 2009-07-01
I just installed Ubuntu 9.04 in a dual-boot system with Windows XP on an Acer Aspire netbook.  Unfortunately, when I boot up the computer and select "Windows XP" from the Grub menu, the screen says "Starting Up ..." and then just sits there forever.  Windows never starts.  Any ideas?  I'm not extremely tech-savvy, but I know the basics, so please be patient.  Thanks very much in advance...

---

### Post by wrongo on 2009-07-02
Hi. I have the same problem, roughly. Dual boot, had Windows XP installed first, then followed instructions on youtube video for dual boot with Jaunty Jackelope. Ubuntu worked fine. But now Windows is broken. "Blue screen of death" and something about "IRQL." I'm thinking it has to do with the most obvious change to the harddrive: I partitioned it and made half of it Linux. Duh. Isn't that it? That's got to be it. Why else would Windows freak out? I'm thinking Windows is expecting its hard drive to have certain dimensions, speaking of how much memory it consists of, and since that's suddenly changed, it's like, "Hey, wait a minute! I'm not even sure this is the same hard-drive, dog. I ain't doin' NOTHIN' till you tell me what's up." That's what I'm thinking. But so far, no one's had a solution to this problem, and I'm a couple hours into researching it.

Thanks for any helpful suggestions in advance!

Jerit

---

### Post by merlinus on 2009-07-02
Open a terminal window and post results of these commands:

```
sudo fdisk -l
cat /boot/grub/menu.lst
```

---

### Post by okayneil on 2009-07-02
You have to have SATA Drive support turned OFF in your system bios before you can boot into windows xp. 

Check that first :)

---

