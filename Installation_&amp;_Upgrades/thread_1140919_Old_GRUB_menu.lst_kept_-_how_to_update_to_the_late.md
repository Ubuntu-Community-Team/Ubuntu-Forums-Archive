---
title: "Old GRUB menu.lst kept - how to update to the latest version"
date: 2009-04-28
forum: Installation &amp; Upgrades
---

### Post by ak-buntu on 2009-04-28
Hi,

Yesterday I upgraded from 8.04 to 9.04. When the question appeared about the menu.lst file, I mistakenly chose for "Keep the version currently stored". The result of this is that Ubuntu 9.04 does not appear...

How can I get 9.04 on the list? Or is there a way to download the latest version? I do not have a Live CD.

Here is the most recent entry on the Menu.lst:

title        Ubuntu 8.04.1, kernel 2.6.24-21-generic
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.24-21-generic root=UUID=2f6246e9-4e54-4d9f-a204-d9656d35850c ro quiet splash
initrd        /boot/initrd.img-2.6.24-21-generic
quiet

title        Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.24-21-generic root=UUID=2f6246e9-4e54-4d9f-a204-d9656d35850c ro single
initrd        /boot/initrd.img-2.6.24-21-generic

---

### Post by ittiam on 2009-04-28
Run

```
sudo update-grub
```

then verify the menu.lst file

---

### Post by ak-buntu on 2009-04-28
It seems something happens, but the menu.lst file is still the same. Any idea why?



Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.24-23-generic
Found kernel: /boot/vmlinuz-2.6.24-22-generic
Found kernel: /boot/vmlinuz-2.6.24-21-generic
Found kernel: /boot/vmlinuz-2.6.24-19-generic
Found kernel: /boot/vmlinuz-2.6.24-17-generic
Found kernel: /boot/vmlinuz-2.6.24-16-generic
Found kernel: /boot/vmlinuz-2.6.22-14-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... Updating the default booting kernel
done

---

### Post by ittiam on 2009-04-28
I think several of them have seen this problem doing jaunty upgrade

```
lsb_release -a
```

the above command will show you what version of ubuntu you are running on. pretty sure it will be jaunty.

Then there are two options

1) manually update the menu.lst file
2) reinstall the kernel. sudo aptitude reinstall linux-image-2.6.28-11-generic. This simple reinstall of kernel should pretty much fix it.

---

### Post by ak-buntu on 2009-04-29
The kernel was already found after running **sudo update-grub**:
[INDENT]Found kernel: /boot/vmlinuz-2.6.24-23-generic
[/INDENT]
But when I try **lsb_release -a** the following appears:
[INDENT]Distributor ID:    Ubuntu
Description:    Ubuntu 8.04.2
Release:    8.04
Codename:    hardy
[/INDENT]It seems the new kernel is there, but as it is not listed in GRUB, I can't boot it. Can someone paste the lines that I should add in the menu.lst file, above the Ubuntu 8.04.1, kernel 2.6.24-21-generic entry?

---

### Post by ak-buntu on 2009-05-03
Anybody?

---

### Post by ittiam on 2009-05-04
You can copy paste your already existing kernel and just change the kernel version number alone

for example you have something like the following already existing
```
title Ubuntu 8.10, kernel 2.6.24-23-generic
root (hd0,6)
kernel /boot/vmlinuz-2.6.24-23-generic root=UUID=e7910a931-108d-5091-b7b4-1a83a8bad99 ro quiet splash
initrd /boot/initrd.img-2.6.28-23-generic

```

you can copy **(copy, not overwrite or modify)**the above and change it to

```
title Ubuntu 8.10, kernel **2.6.28-11**-generic
root (hd0,6)
kernel /boot/vmlinuz-**2.6.28-11**-generic root=UUID=e7910a931-108d-5091-b7b4-1a83a8bad99 ro quiet splash
initrd /boot/initrd.img-**2.6.28-11**-generic

```

The title,  you can keep .anything you want
NOTE that the UUID and the root values must not be changed. I have highlighted the things you need to change in bold

---

### Post by amrypma on 2009-05-04
With update-grub you've updated the menu listing for the kernels you have.
Now you need to write it to the MBR ( in most cases).

Usually this is done with

```

grub-install hd0

```

But grub only lists available kernels, not the complete OS.
An upgrade will not replace the kernels you already have. They haven't changed and are still of the 8.10 release. They'll work just fine so don't worry.

Newer kernels will be labeled Jaunty or 9.04. And if you build a custom kernel you can label it any way you please.

---

### Post by ak-buntu on 2009-05-06
Thanks, it worked!

---

### Post by maryus88 on 2009-05-07
I have the same problem and I followed all these steps, but still nothing. 
menu.lst is the same: 

title        Ubuntu 8.10, kernel 2.6.27-9-generic
uuid        dd204e67-15e9-425e-8601-5fc67967fa40
kernel        /boot/vmlinuz-2.6.27-9-generic root=UUID=dd204e67-15e9-425e-8601-5fc67967fa40 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-9-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid        dd204e67-15e9-425e-8601-5fc67967fa40
kernel        /boot/vmlinuz-2.6.27-9-generic root=UUID=dd204e67-15e9-425e-8601-5fc67967fa40 ro  single
initrd        /boot/initrd.img-2.6.27-9-generic

What else should I do?

---

### Post by amrypma on 2009-05-07
Open up synaptic and search for "linux image generic". ( i think.)
If there is a newer one install it.

The install script will notice grub is in stalled and do the rest.

But if you are lazy like me just install the linux package which always depends on the latest kernel complete with modules and restricted modules.

---

### Post by Zeffy on 2009-05-28
Thanks!  I have had to update my menu.lst manually twice now, you would think I would remember how!  

I will try and remember for the next time.. Here's hoping there is not a next time though! ;)

---

### Post by uligraf on 2009-06-19
Hi,

I just updated to the newest kernel 2.6.28-13-generic, and made the error to reply <yes> to the answer if I want to keep my manually edited menu.lst (I changed it to redirect to a copy which can be accessed from other OS to toggle which OS should automatically boot). 

I know want to manually edit /boot/grub/menu.lst to load the new kernel. Where can I find the complete menu entries including <uuid>. My, probably stupid, question is: Does this uuid change, and where can I find it. My Ubuntu related entries in the menu.lst after installing, but before reooting the new kernel is:

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        d5bb16db-01d3-4bac-997e-0f09d9fdbd8f
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=d5bb16db-01d3-4bac-997e-0f09d9fdbd8f ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        d5bb16db-01d3-4bac-997e-0f09d9fdbd8f
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=d5bb16db-01d3-4bac-997e-0f09d9fdbd8f ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

Many thanks in advance. Maybe a good soal can just copy the new entries from his menu.lst into a response.

Uli

---

### Post by VastOne on 2009-06-19
> **uligraf said:**
> Hi,

I just updated to the newest kernel 2.6.28-13-generic, and made the error to reply <yes> to the answer if I want to keep my manually edited menu.lst (I changed it to redirect to a copy which can be accessed from other OS to toggle which OS should automatically boot). 

I know want to manually edit /boot/grub/menu.lst to load the new kernel. Where can I find the complete menu entries including <uuid>. My, probably stupid, question is: Does this uuid change, and where can I find it. My Ubuntu related entries in the menu.lst after installing, but before reooting the new kernel is:

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        d5bb16db-01d3-4bac-997e-0f09d9fdbd8f
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=d5bb16db-01d3-4bac-997e-0f09d9fdbd8f ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        d5bb16db-01d3-4bac-997e-0f09d9fdbd8f
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=d5bb16db-01d3-4bac-997e-0f09d9fdbd8f ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

Many thanks in advance. Maybe a good soal can just copy the new entries from his menu.lst into a response.

Uli

No, the UUID's do not change on their own. They can be changed if necessary.

To see what your UUID's are run

```

blkid
```

---

### Post by uligraf on 2009-06-19
Thanks a lot VastOne! Helped me a lot to try out the new Kernel ... and to switch back to Kernel 2.6.28-11, because Skype (the champion of buggy but unavoidable apps) is not running on the  new one.

---

