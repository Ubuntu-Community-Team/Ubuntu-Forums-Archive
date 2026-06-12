---
title: "Problems with hibernate after moving to a new HD"
date: 2009-08-25
forum: Hardware
---

### Post by rienesl on 2009-08-25
Hi out there.
I have a problem and tried to Google after it, but no success. I'm just starting with Linux, so please be patient :D
OK, here is, what I've done:
Installing Ubuntu to a X300 on a SSD. SDA1 was the Operating System (XP) and SDA2 the IBM System Partition. So I created SDA3 with ext2 and SDA4 as a swap partition (2GB). Everything worked fine, even the hibernate.
Yes, I know, never touch a running system, but I had to:
After installing the RC1 of W7 on SDA1 on a fresh Hard drive I copied the Linux Partition to SDA2 and after that that IBM System Partition to SDA3. Then I created a extended Partition (SDA4) and in that one Data Partition (NTFS/SDA6) and a SWAP (SDA5).
  Now Ubuntu (9.04) wasn't able to hibernate, terminated the try with an error.
After I changed the UUID Entrys in /etc/fstab and /etc/initramfs-tools/conf.d/resume that works again, but instead of wakening up again it simply restarts. 
So I tried to run "sudo update-initramfs -u". No change...
Any Ideas?
Greetings,
Martin

---

### Post by rienesl on 2009-08-25
OK, found a solution:
The UUID Entry in /etc/initramfs-tools/conf.d/resume is case sensitive! Failsafe method: copy the UUID from GParted and paste it in there. Then run "sudo update-initramfs -u" and then restart your system. After that, everything should work fine!

---

