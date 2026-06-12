---
title: "Suspend works but hibernate doesn't - how to diagnose?"
date: 2010-05-08
forum: Hardware
---

### Post by paol05 on 2010-05-08
Hi, I'm looking for help in diagnosing a hibernate problem on my laptop. Like the title says, suspend (ie to RAM) works perfectly(*) out of the box, but hibernate (ie to disk) does not. Instead of resuming, it does a normal boot.

I have very little experience with suspend/hibernate in linux. Where should I start looking for the problem? I'm assuming hibernate has to work in principle, since suspend to RAM does work.

System information:
[LIST]
[*] Lenovo Thinkpad T500:
- 4Gb RAM
- using the intel graphics instead of ATI
[*] Ubuntu 10.4 (64bit)
[*] Swap partition is 6.5Gb
[*] Anything else just ask :)
[/LIST]

Thanks,
Pedro

(*) actually, usb devices are not being initialized after resume, but that doesn't bother me too much because they work after unplugging and plugging in again

---

### Post by pmos69 on 2010-05-08
try this: [https://wiki.ubuntu.com/DebuggingKernelSuspendHibernateResume](https://wiki.ubuntu.com/DebuggingKernelSuspendHibernateResume)

---

### Post by paol05 on 2010-05-09
Thanks a lot! I figured out the problem: I had changed the swap partition location after installing the system.

For future reference: If you change the swap partition, it turns out that it's necessary to manually edit /etc/initramfs-tools/conf.d/resume. This file should contain the UUID of the swap partition (compare against /etc/fstab in case of doubt)

After changing the initramfs configuration, run sudo update-initramfs -u and reboot.

---

