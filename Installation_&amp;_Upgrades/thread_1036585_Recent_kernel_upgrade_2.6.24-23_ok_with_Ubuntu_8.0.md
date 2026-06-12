---
title: "Recent kernel upgrade 2.6.24-23 ok with Ubuntu 8.04.1 LTS ?"
date: 2009-01-11
forum: Installation &amp; Upgrades
---

### Post by lptr on 2009-01-11
Somebody any troubles?

rob*

---

### Post by dgermann on 2009-01-11
lptr--

Have over this weekend upgraded 2 plain vanilla boxes, one laptop (System76), one server, and one box with nVidia dual screens. All 5 seem to be running OK.

Good to have kernel upgrade that works, yes?

---

### Post by Egi_Power on 2009-01-12
Hi!

I'm using Ubuntu 8.04.1.
After the kernel upgrade my nVidia drivers are gone in the new kernel.
In 2.6.24-22 everything works as it should.
At boot up between the splash screen and the login screen i got an option to set up the screen resolution, but can't set it higher than 800x600.

Any tips on how to fix it, how to get the nVidia driver?

Any help would be appreciated.

Egi_Power

---

### Post by johnnyhostile on 2009-01-12
I manually added the new kernel to menu.lst and it never booted.. Here is my GRUB entry:

#title           Ubuntu 8.04.1, kernel 2.6.24-23-generic
#root            (hd0,0)
#kernel          /boot/vmlinuz-2.6.24-23-generic root=UUID=e27ac836-80df-4000-9b$
#initrd          /boot/initrd.img-2.6.24-23-generic
#quiet

#title           Ubuntu 8.04.1, kernel 2.6.24-23-generic (recovery mode)
#root            (hd0,0)
#kernel          /boot/vmlinuz-2.6.24-23-generic root=UUID=e27ac836-80df-4000-9b$
#initrd          /boot/initrd.img-2.6.24-23-generic


(commented because it didn't work :p)

any ideas?

Thanks!

---

### Post by Egi_Power on 2009-01-12
@johnnyhostile

my menu.lst looks like this:

```
title		Ubuntu 8.04.1, kernel 2.6.24-23-generic
root		(hd0,3)
kernel		/vmlinuz-2.6.24-23-generic root=UUID=12345678-95c8-4552-a627-12345678915f ro quiet splash
initrd		/initrd.img-2.6.24-23-generic
quiet
```

I don't have /boot in the kernel and initrd lines. Does it matter?

Egi_Power

---

### Post by kranny on 2009-01-12
> **johnnyhostile said:**
> I manually added the new kernel to menu.lst and it never booted.. Here is my GRUB entry:

#title           Ubuntu 8.04.1, kernel 2.6.24-23-generic
#root            (hd0,0)
#kernel          /boot/vmlinuz-2.6.24-23-generic root=UUID=e27ac836-80df-4000-9b$
#initrd          /boot/initrd.img-2.6.24-23-generic
#quiet

#title           Ubuntu 8.04.1, kernel 2.6.24-23-generic (recovery mode)
#root            (hd0,0)
#kernel          /boot/vmlinuz-2.6.24-23-generic root=UUID=e27ac836-80df-4000-9b$
#initrd          /boot/initrd.img-2.6.24-23-generic


(commented because it didn't work :p)

any ideas?

Thanks!

Do you have your backed up menu.lst.Just change kernel number from your previous one to 23 or if you want both the kernels to work Just copy and paste the previous kernel lines..

My Previous Menu.lst says
```
title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=d4b7a9dc-848e-4ead-b029-b09eefb5be22 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet
```

I just changed 16 to 23

---

### Post by kranny on 2009-01-12
> **Egi_Power said:**
> @johnnyhostile

my menu.lst looks like this:

```
title		Ubuntu 8.04.1, kernel 2.6.24-23-generic
root		(hd0,3)
kernel		/vmlinuz-2.6.24-23-generic root=UUID=12345678-95c8-4552-a627-12345678915f ro quiet splash
initrd		/initrd.img-2.6.24-23-generic
quiet
```

I don't have /boot in the kernel and initrd lines. Does it matter?

Egi_Power

Perfectly right provided you have the intrd and the other file in the root filesystem

---

### Post by kranny on 2009-01-12
If you Dont want to manually edit the menu.lst and want the grub to automaticall do it for you..Try the following

sudo apt-get purge grub
sudo apt-get install grub
sudo update-grub

---

### Post by Egi_Power on 2009-01-12
> **kranny said:**
> Perfectly right provided you have the intrd and the other file in the root filesystem

I think I have both files in /boot.

```
***@***-desktop:~$ ls -la /boot/
total 53953
drwxr-xr-x  4 root root    3072 2009-01-12 07:37 .
drwxr-xr-x 21 root root    4096 2009-01-12 01:33 ..
-rw-r--r--  1 root root  422838 2008-10-22 05:12 abi-2.6.24-21-generic
-rw-r--r--  1 root root  422838 2008-11-24 23:47 abi-2.6.24-22-generic
-rw-r--r--  1 root root  422838 2008-11-27 23:13 abi-2.6.24-23-generic
-rw-r--r--  1 root root   80062 2008-10-22 05:12 config-2.6.24-21-generic
-rw-r--r--  1 root root   80062 2008-11-24 23:47 config-2.6.24-22-generic
-rw-r--r--  1 root root   80051 2008-11-27 23:13 config-2.6.24-23-generic
drwxr-xr-x  2 root root    1024 2009-01-12 07:37 grub
-rw-r--r--  1 root root 7480599 2008-11-25 22:42 initrd.img-2.6.24-21-generic
-rw-r--r--  1 root root 7480469 2008-11-25 22:41 initrd.img-2.6.24-21-generic.bak
-rw-r--r--  1 root root 7480935 2008-11-28 06:58 initrd.img-2.6.24-22-generic
-rw-r--r--  1 root root 7480778 2008-11-28 06:58 initrd.img-2.6.24-22-generic.bak
-rw-r--r--  1 root root 7480536 2009-01-12 07:37 initrd.img-2.6.24-23-generic
-rw-r--r--  1 root root 7480619 2009-01-12 07:31 initrd.img-2.6.24-23-generic.bak
drwx------  2 root root   12288 2008-11-25 23:16 lost+found
-rw-r--r--  1 root root  103204 2007-09-28 12:06 memtest86+.bin
-rw-r--r--  1 root root  905617 2008-10-22 05:12 System.map-2.6.24-21-generic
-rw-r--r--  1 root root  905617 2008-11-24 23:47 System.map-2.6.24-22-generic
-rw-r--r--  1 root root  905633 2008-11-27 23:13 System.map-2.6.24-23-generic
-rw-r--r--  1 root root 1920760 2008-10-22 05:12 vmlinuz-2.6.24-21-generic
-rw-r--r--  1 root root 1921176 2008-11-24 23:47 vmlinuz-2.6.24-22-generic
-rw-r--r--  1 root root 1921976 2008-11-27 23:13 vmlinuz-2.6.24-23-generic
```

Am I wrong?

Egi_Power

---

### Post by lptr on 2009-01-12
Thanks to your answers:

Ok - upgraded some minutes ago. Seems all ok on this machine. Before upgrade I looked into config and saw, that I am using nv drivers (not proprietary), anyway. I disabled it some time ago - didn't remember this until rereading.

Will upgrade production servers this evening. 

@dgermann:
 > Good to have kernel upgrade that works, yes?

As this systems are absolutely vital to my business this is the case. Yes.
I would not have asked otherwise.

rob*

---

### Post by kranny on 2009-01-12
> **Egi_Power said:**
> I think I have both files in /boot.

```
***@***-desktop:~$ ls -la /boot/
total 53953
drwxr-xr-x  4 root root    3072 2009-01-12 07:37 .
drwxr-xr-x 21 root root    4096 2009-01-12 01:33 ..
-rw-r--r--  1 root root  422838 2008-10-22 05:12 abi-2.6.24-21-generic
-rw-r--r--  1 root root  422838 2008-11-24 23:47 abi-2.6.24-22-generic
-rw-r--r--  1 root root  422838 2008-11-27 23:13 abi-2.6.24-23-generic
-rw-r--r--  1 root root   80062 2008-10-22 05:12 config-2.6.24-21-generic
-rw-r--r--  1 root root   80062 2008-11-24 23:47 config-2.6.24-22-generic
-rw-r--r--  1 root root   80051 2008-11-27 23:13 config-2.6.24-23-generic
drwxr-xr-x  2 root root    1024 2009-01-12 07:37 grub
-rw-r--r--  1 root root 7480599 2008-11-25 22:42 initrd.img-2.6.24-21-generic
-rw-r--r--  1 root root 7480469 2008-11-25 22:41 initrd.img-2.6.24-21-generic.bak
-rw-r--r--  1 root root 7480935 2008-11-28 06:58 initrd.img-2.6.24-22-generic
-rw-r--r--  1 root root 7480778 2008-11-28 06:58 initrd.img-2.6.24-22-generic.bak
-rw-r--r--  1 root root 7480536 2009-01-12 07:37 initrd.img-2.6.24-23-generic
-rw-r--r--  1 root root 7480619 2009-01-12 07:31 initrd.img-2.6.24-23-generic.bak
drwx------  2 root root   12288 2008-11-25 23:16 lost+found
-rw-r--r--  1 root root  103204 2007-09-28 12:06 memtest86+.bin
-rw-r--r--  1 root root  905617 2008-10-22 05:12 System.map-2.6.24-21-generic
-rw-r--r--  1 root root  905617 2008-11-24 23:47 System.map-2.6.24-22-generic
-rw-r--r--  1 root root  905633 2008-11-27 23:13 System.map-2.6.24-23-generic
-rw-r--r--  1 root root 1920760 2008-10-22 05:12 vmlinuz-2.6.24-21-generic
-rw-r--r--  1 root root 1921176 2008-11-24 23:47 vmlinuz-2.6.24-22-generic
-rw-r--r--  1 root root 1921976 2008-11-27 23:13 vmlinuz-2.6.24-23-generic
```

Am I wrong?

Egi_Power

Change the lines in the menu.lst starting with boot

---

### Post by Egi_Power on 2009-01-12
> **kranny said:**
> Change the lines in the menu.lst starting with boot

Why should I change it?

It's working perfectly.

---

### Post by johnnyhostile on 2009-01-16
> **kranny said:**
> Perfectly right provided you have the intrd and the other file in the root filesystem

Yea, everything is in /boot:

-rw-r--r-- 1 root root 413K 2008-08-20 23:46 abi-2.6.24-19-generic
-rw-r--r-- 1 root root 413K 2008-10-21 22:12 abi-2.6.24-21-generic
-rw-r--r-- 1 root root 413K 2008-11-24 16:47 abi-2.6.24-22-generic
-rw-r--r-- 1 root root 413K 2008-11-27 16:13 abi-2.6.24-23-generic
drwxr-xr-x 2 root root 4.0K 2008-12-01 23:56 backgrounds
-rw-r--r-- 1 root root  79K 2008-08-20 23:46 config-2.6.24-19-generic
-rw-r--r-- 1 root root  79K 2008-10-21 22:12 config-2.6.24-21-generic
-rw-r--r-- 1 root root  79K 2008-11-24 16:47 config-2.6.24-22-generic
-rw-r--r-- 1 root root  79K 2008-11-27 16:13 config-2.6.24-23-generic
drwxr-xr-x 2 root root 4.0K 2009-01-09 01:18 grub
-rw-r--r-- 1 root root 7.2M 2008-08-27 07:38 initrd.img-2.6.24-19-generic
-rw-r--r-- 1 root root 7.2M 2008-08-25 00:26 initrd.img-2.6.24-19-generic.bak
-rw-r--r-- 1 root root 7.2M 2008-11-09 17:36 initrd.img-2.6.24-21-generic
-rw-r--r-- 1 root root 7.2M 2008-10-29 14:56 initrd.img-2.6.24-21-generic.bak
-rw-r--r-- 1 root root 7.2M 2008-12-11 03:02 initrd.img-2.6.24-22-generic
-rw-r--r-- 1 root root 7.2M 2008-11-30 00:56 initrd.img-2.6.24-22-generic.bak
-rw-r--r-- 1 root root 7.2M 2009-01-15 01:10 initrd.img-2.6.24-23-generic
-rw-r--r-- 1 root root 7.2M 2009-01-09 01:18 initrd.img-2.6.24-23-generic.bak
-rw-r--r-- 1 root root 101K 2007-09-28 05:06 memtest86+.bin
-rw-r--r-- 1 root root 884K 2008-08-20 23:46 System.map-2.6.24-19-generic
-rw-r--r-- 1 root root 885K 2008-10-21 22:12 System.map-2.6.24-21-generic
-rw-r--r-- 1 root root 885K 2008-11-24 16:47 System.map-2.6.24-22-generic
-rw-r--r-- 1 root root 885K 2008-11-27 16:13 System.map-2.6.24-23-generic
-rw-r--r-- 1 root root 1.9M 2008-08-20 23:46 vmlinuz-2.6.24-19-generic
-rw-r--r-- 1 root root 1.9M 2008-10-21 22:12 vmlinuz-2.6.24-21-generic
-rw-r--r-- 1 root root 1.9M 2008-11-24 16:47 vmlinuz-2.6.24-22-generic
-rw-r--r-- 1 root root 1.9M 2008-11-27 16:13 vmlinuz-2.6.24-23-generic

when i tried to boot the new kernel, it loaded into the xterm and just hung there... for the suggestion to change 32 to 16, i do  not see a kernel listed as 16 anywhere.. ill try it when i get outta work!

---

### Post by johnnyhostile on 2009-01-16
> **kranny said:**
> If you Dont want to manually edit the menu.lst and want the grub to automaticall do it for you..Try the following

sudo apt-get purge grub
sudo apt-get install grub
sudo update-grub

nah, i have a custom menu with a triple boot. ;)

---

