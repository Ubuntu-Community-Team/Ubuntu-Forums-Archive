---
title: "System Botched after Swap upgrade"
date: 2008-10-13
forum: General Help
---

### Post by shafin on 2008-10-13
I had a RAM upgrade and then changed my swap partition. I went for a bigger one to support hibernating. The new swap partition didnt work. So I had to manually  use tune2fs and mkswap to generate a new uuid and used it in fstab and /etc/initramfs-tools/conf.d/resume. Now my system is totally botched. The problems are:

1. Usplash is not showing, instead there is a blinking cursor. It was searching to solve this problem that brought me to the problem that swap was not mounting. after using uuid on fstab, swap mounts, but usplash is still missing.

2. But after I changed fstab and /etc/initramfs-tools/conf.d/resume, a more serious problem is there. Suspend is not working. After the computer goes to suspend mode, mouse, keyboard, nothing works,The numlock key no longer changes the LED state on keyboard.
 I can not bring my pc back from suspend. It worked fine with the previous swap, even when the new swap didnt work, but now its totally bricked. 

I have my pc set to never suspend, and I leave it on for long durations to keep downloading. But somehow it goes to suspend mode and no more downloading!!

Here is the output of update-initramfs, it shows an error, maybe its related to my problem.
```
$ sudo update-initramfs -u
[sudo] password for shafin: 
update-initramfs: Generating /boot/initrd.img-2.6.27-2-generic
/etc/initramfs-tools/conf.d/resume.save: 2: ec16da3f-4fad-406f-92d7-36667c0fa413: not found

```
Thanks in advance:)

---

### Post by shafin on 2008-10-17
Bump:(

---

