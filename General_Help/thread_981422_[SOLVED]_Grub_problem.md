---
title: "[SOLVED] Grub problem"
date: 2008-11-13
forum: General Help
---

### Post by yobird42 on 2008-11-13
So today I edited the menu.lst for grub to allow it to boot from cd because my bios is unable to, and it got messed up somehow. When it boots instead of automatically booting Ubuntu which it usually does, it gives me this screen 

```
[minimal Bash-like line editing is supported.  For the first word,
TAB lists possible command completions.  Anywhere else TAB 
lists the possible completions of a device/filename]

grub>
```

Ubuntu is my only OS installed and as I said before I am unable to boot from a CD so I'm out of luck there. Any help would be greatly appreciated, and thanks in advance.

---

### Post by phidia on 2008-11-13
You need to re-set up grub I think. 
To get into your install though follow the guide [here]("https://help.ubuntu.com/community/BootOptions") titled "Change Boot Options Temporarily For An Existing Installation" There is also a howto [here]("https://help.ubuntu.com/community/GrubHowto") that duplicates some of the info from the first link but you might prefer one over the other.

BTW if your bios won't boot from a cdrom I don't believe editing grub will make it boot either-it's a hardware issue.

---

### Post by sisco311 on 2008-11-13
you can manualy load the kernel in the grub shell

1.) find the root partition:
```
find /boot/grub/stage1
```
output:
> find /boot/grub/stage1
 (hd**X**,**Y**)

2.) set the root partition:
```
root (hd**X**,**Y**)
```

3.) load the kernel:
```
kernel /boot/vmlinuz**<press tab for auto complete>** root=/dev/sd**ZW**
```

where /dev/sd**ZW** is the root partition.

> first partition on first hard drive = (hd0,0) = /dev/sd**a1** in Linux
2nd partition on first hard drive = (hd0,1) = /dev/sd**a2** in Linux
3rd partition on first hard drive = (hd0,2) = /dev/sd**a3** in Linux
4th partition on first hard drive = (hd0,3) = /dev/sd**a4** in Linux

first partition on second drive = (hd1,0) = /dev/sd**b1** ...

4.) load the initrd:
```
initrd /boot/initrd.img**<press tab ...>**
```

5.) boot:
```
boot
```

in ubuntu backup the menu.lst:
```
sudo mv /boot/grub/menu.lst /boot/grub/menu.lst-old
```

and generate a new one:
```
sudo update-grub
```

---

### Post by yobird42 on 2008-11-13
sisco311, I did that, and it loaded a bunch of numbers and what not and it just stopped. What should I do now?

edit- I waited for a while and then it went to the busybox screen

---

### Post by sisco311 on 2008-11-13
> **yobird42 said:**
> sisco311, I did that, and it loaded a bunch of numbers and what not and it just stopped. What should I do now?

edit- I waited for a while and then it went to the busybox screen

in step 3.) append the command with root=/dev/sd**XY**
assuming that sd**XY** is the root ("/") partition.

ex.:
> kernel /boot/vmlinuz-2.6.27-7-generic root=/dev/sda1

---

### Post by yobird42 on 2008-11-13
root=/dev/sdXY ok so when I did step one (hd0,0) returned. Does this mean I put root=/dev/sd00 after step 3?

---

### Post by sisco311 on 2008-11-13
> **yobird42 said:**
> root=/dev/sdXY ok so when I did step one (hd0,0) returned. Does this mean I put root=/dev/sd00 after step 3?
try *root=/dev/sda1 *

> first partition on first hard drive = (hd0,0)    = /dev/sda1 in Linux
  2nd partition on first hard drive = (hd0,1)    = /dev/sda2 in Linux
  3rd partition on first hard drive = (hd0,2)    = /dev/sda3 in Linux
  4th partition on first hard drive = (hd0,3)    = /dev/sda4 in Linux  

---

### Post by yobird42 on 2008-11-13
> **sisco311 said:**
> try *root=/dev/sda1 *

worked like a charm, I can't thank you enough for your time and effort. Again thank you.

---

### Post by sisco311 on 2008-11-13
You're welcome.

Please mark the thread solved by selecting 
**Mark this thread as solved** from the [COLOR="Red"]**Thread Tools**[/COLOR].

---

