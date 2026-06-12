---
title: "GRUB will not display menu, prompt is okay"
date: 2008-07-16
forum: General Help
---

### Post by Zyrshnikashnu on 2008-07-16
My /boot partition ran out of space for a kernel update, so I deleted some old kernel entries from the partition and ran an update script (it may have been update-grub, but I can't remember now).

That messed up my menu.lst, but I managed to generate a new one. I've attached it for reference.

Now, GRUB will not show my menu. Pressing ESC (as if it were hidden) does nothing. The prompt works just fine, so I can manually specify the kernel, but this computer belongs to my parents and they certainly don't want to learn to do that. :P

I've tried reinstalling GRUB to the MBR, running grub-install, update-grub... nothing lets my menu show. Any suggestions are appreciated.

---

### Post by CrusaderAD on 2008-07-17
Are you able to log on and get to your desktop?

---

### Post by dracayr on 2008-07-17
have you ever tried installing grub to the mbr by executing sudo grub, and then setup (hdX)?

dracayr

---

### Post by caljohnsmith on 2008-07-17
When you login to Ubuntu (or use a Live CD), try the following:
```
$ sudo grub
grub>find /boot/grub/menu.lst
[this should hopefully return (hd0,0)]
grub>root (hd0,0)
grub>cat /boot/grub/menu.lst
```
Does it show your menu.lst OK? If not then maybe you don't have the permissions set correctly on menu.lst.

---

### Post by Zyrshnikashnu on 2008-07-19
raptormanad: Yes, I can boot up by manually specifying a kernel. After that, everything operates normally.

dracayr: I've done that, and no progress was made.

caljohnsmith: Yes, grub finds and cats menu.lst just fine. What are the proper permissions? It's currently:
```
$ ls -l | grep menu.lst
-rw-r--r-- 1 root root   4247 2008-07-16 14:28 menu.lst
```

---

### Post by flavor on 2009-01-22
TRY
$ cp /boot/grub/menu.lst /boot/grub/grub.conf

---

### Post by Zyrshnikashnu on 2009-01-22
Hey there!

I tried that ages ago with no luck. Fortunately, I found the problem!

For reasons unknown to me, GRUB was installed to /boot/boot/grub instead of /boot/grub. It was looking for menu.lst in the former directory. Rather than screw with the installation even more, I just copied menu.lst to the latter.

---

