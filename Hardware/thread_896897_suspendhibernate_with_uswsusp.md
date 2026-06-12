---
title: "suspend/hibernate with uswsusp"
date: 2008-08-21
forum: Hardware
---

### Post by gusanto on 2008-08-21
Hi there,
I have suspend/hibernation problem with Hardy. It worked on may laptop (Sony Vaio VGN-NR120E) when I was using Gutsy. After update, the capability of suspend/hibernate has gone.  I then fresh installed the Hardy, the same problem remains unsolved.
I have tried to follow some guides (for example [http://ubuntuforums.org/showthread.php?t=750216]("http://ubuntuforums.org/showthread.php?t=750216") ) using uswsusp, but it did not help.  When I execute s2disk, it says "s2disk: Could not lock myself. Reason: Cannot allocate memory". It turns off when I execute s2both, but when try to wake it up, it boots up like normal (not wake up from hibernation).
I edited /etc/uswsusp.conf and change from UUID style to /dev/sda6 (this is my swap partition) style. Here is my /etc/uswsusp.conf file:
> # /etc/uswsusp.conf(8) -- Configuration file for s2disk/s2both 
resume device = /dev/sda6/by-UUID=c9df300f-7943-44d8-b3dd-8181f5517bf6
splash = y
compress = y
early writeout = y
image size = 483307765
RSA key file = /etc/uswsusp.key
shutdown method = platform

and my /boot/grub/menu/lst
> title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=c9df300f-7943-44d8-b3dd-8181f5517bf6 resume=UUID=614cf15e-0b01-414c-9da4-d36f9c93adcd ro quiet splash vga=normal
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

and my /etc/initramfs-tools/conf.d/resume 
> RESUME=UUID=614cf15e-0b01-414c-9da4-d36f9c93adcd

Any idea how to solve this problem is much appreciated. 
"Laptop without suspend/hibernate utility is like coffee without sugar"
Thanks.

---

### Post by cro.smiley on 2008-09-03
Hi, here is your problem:
```
resume device = /dev/sda6/by-UUID=c9df300f-7943-44d8-b3dd-8181f5517bf6
```

It should be /dev/**disk/by-uiid/**c9df300f-7943-44d8-b3dd-8181f5517bf6

Hope this helps, because I know how much time i spent fixing suspend problem and I'm still fixing it :)

---

### Post by gusanto on 2008-09-05
> **cro.smiley said:**
> Hi, here is your problem:
```
resume device = /dev/sda6/by-UUID=c9df300f-7943-44d8-b3dd-8181f5517bf6
```

It should be /dev/**disk/by-uiid/**c9df300f-7943-44d8-b3dd-8181f5517bf6

Hope this helps, because I know how much time i spent fixing suspend problem and I'm still fixing it :)

It still did not solve the problem. Thanks any way.
Any other idea?

---

### Post by maximi89 on 2009-05-17
> **gusanto said:**
> It still did not solve the problem. Thanks any way.
Any other idea?

hi, 
maximi89@Maximiliano:~$ cat /sys/power/disk
[platform] test testproc shutdown reboot

maximi89@Maximiliano:~$ cat /etc/uswsusp.conf
# /etc/uswsusp.conf(8) -- Configuration file for s2disk/s2both
resume device = /dev/sda6
compress = y
early writeout = y
image size = 427135303
RSA key file = /etc/uswsusp.key
shutdown method = shutdown


change "platform" with "shutdown"
and tell me if that works.

---

