---
title: "apt-get doesn't work.."
date: 2008-09-26
forum: General Help
---

### Post by MNT on 2008-09-26
Hi everyone,

I 'm a new member here and I know it's not a good way to start but I have a problem...

I 'm a Linux newbie BUT I know how to search and I did but it didn't solve my problem. So here I am..

So I have a dedicated server running Ubuntu 8.04 Desktop TLS. I just got it and as always the first thing to do was to update everything. So I did. And now apt-get doesn't work, neither Synaptic.

For example I go to the terminal and type
 apt-get install wine
It returned this:
[img]http://img407.imageshack.us/img407/4467/27158517el0.jpg[/img]

So I type what it said to type and it gave me this:
[img]http://img101.imageshack.us/img101/7941/75329469uv9.jpg[/img]

I did some research and I found this but still nothing: 

[img]http://img527.imageshack.us/img527/743/22932634qa6.jpg[/img]

I keep searching and I found a thread in here that says to type these commands together. So I did. And it returned this:
[img]http://img101.imageshack.us/img101/9996/12760014hx8.jpg[/img]

I really don't know what to do and I can't use my server. :(

Any help would be truly appreciated.

---

### Post by Pro-reason on 2008-09-26
Unfortunately, the APT/DPKG system often gets itself into a situation whereby it can't fix itself.  You have to manually remove any packages which are not working.  Then, you can run one of the two repair commands you tried.

Please post the output of the following commands:

```

uname -a
ls /boot/
ls -l /vm* /in*

```

And please post it as text, not a screenshot.

---

### Post by MNT on 2008-09-26
OK, sorry for the screen. I'll do it through Putty so I can copy paste the results.

uname -a:
```

Linux ******.Kimsufi.com 2.6.24.5-xxxx-std-ipv4-32 #3 SMP Wed May 28 09:10:48 CEST 2008 i686 GNU/Linux

```

I covered up the  hostname....

ls /boot/ :
```

boot.0300                          debianlilo.bmp
boot.0800                          map
boot.0801                          sarge.bmp
bzImage-2.6.24.5-xxxx-std-ipv4-32  sid.bmp
coffee.bmp                         System.map-2.6.24.5-xxxx-std-ipv4-32
debian.bmp                         System.map-2.6.24-8-generic

```


ls -l /vm* /in*:

```

root@******:~# ls -l /vm* /in*
ls: cannot access /vm*: No such file or directory
/initrd:
total 0

```

---

### Post by Pro-reason on 2008-09-26
OK, I'm a little confused. Your output bears little relation to what I was expecting.  It looks more like Debian than Ubuntu.  Here's what I get on one of my machines:

```

Linux [COLOR="SlateGray"]****[/COLOR] 2.6.24-21-generic #1 SMP Mon Aug 25 17:32:09 UTC 2008 i686 GNU/Linux

```
```

abi-2.6.24-16-generic         initrd.img-2.6.24-16-generic.bak  System.map-2.6.24-21-generic
abi-2.6.24-21-generic         initrd.img-2.6.24-21-generic      vmlinux-debug-2.6.24-21-generic
config-2.6.24-16-generic      initrd.img-2.6.24-21-generic.bak  vmlinuz-2.6.24-16-generic
config-2.6.24-21-generic      invaders                          vmlinuz-2.6.24-21-generic
grub                          memtest86+.bin
initrd.img-2.6.24-16-generic  System.map-2.6.24-16-generic

```
```

lrwxrwxrwx 1 root root   33 2008-08-16 15:40 /initrd.img -> boot/initrd.img-2.6.24-21-generic
lrwxrwxrwx 1 root root   33 2008-08-13 14:30 /initrd.img.old -> boot/initrd.img-2.6.24-16-generic
lrwxrwxrwx 1 root root   30 2008-08-16 15:40 /vmlinuz -> boot/vmlinuz-2.6.24-21-generic
lrwxrwxrwx 1 root root   30 2008-08-13 14:30 /vmlinuz.old -> boot/vmlinuz-2.6.24-16-generic

/initrd:
total 0

```

I wanted to see what kernel you were running, what kernels you had installed, and thus work out what we could do about the kernel which DPKG/APT keeps on failing to configure.

---

### Post by MNT on 2008-09-26
hahaha....I'm pretty sure I ordered an Ubuntu and it also says it on the screen..:P

Anyway, what now? Any ideas?

---

### Post by Pro-reason on 2008-09-26
You could give this a try:

```

sudo apt-get -f remove linux-headers-2.6.24-16 linux-image-2.6.24-16-generic linux-ubuntu-modules-2.6.24-16-generic
```

---

### Post by MNT on 2008-09-26
And yes its the classic answer:

```

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

```

---

### Post by davidryder on 2008-09-26
Have you tried using Synaptic?

---

### Post by MNT on 2008-09-26
As I already said, Synaptic  doesn't work either. It gives the  same error message as the terminal..

Anything else?

Is there a way to install programs without these two?
Maybe  manually copying files ..left and right?? :P

---

