---
title: "HD mounting problem"
date: 2005-05-14
forum: Hardware &amp; Laptops
---

### Post by Phoenix590 on 2005-05-14
Hello, thanks for reading this post. I'm a newbie to linux (I finnaly got mad enough with how crappy windows was), and any comments are appreciated.

 After running the live CD, I realized that, even though it was the only thing that failed, Kubuntu live-cd loader stated something like Temporary Name finder failed, and when kubuntu loaded I noticed the only drive I could mount was my main CD-Rom drive. Now I am loading the install version the same Temporary Name thing failed again, and now, even though it isnt as severe, Kubuntu will not mount either of my NTFS partions or my second CD rom drive. If I've something really stupid or forgot to take some simple step just let me know. Thanks.

Here are the specs:
KDE Ubuntu
Asus Motherboard
AMD Athlon XP 2400+
2 logical drives, one 80gb, the other 160gb
HDA1: NFTS Bootable w/ Win2000 80gb
HDB1: NTFS Non-Boot 61gb
HDB2: Ext2 Kubuntu drive 20gb
HDB3: 133mb Swap partition
2 CD-Rom drives (one a cd-burner the other a DVD-Reader)
A floppy drive
MSI Nvidea FX 5200
D-Link Wireless G card.

---

### Post by spd106 on 2005-05-14
Hi, could you post your /etc/fstab and/or "$dmesg | grep hd" output.

Also, have you tried samba?

---

