---
title: "Problem booting up due to Kernel changes"
date: 2008-08-09
forum: General Help
---

### Post by Ederico on 2008-08-09
Hello,

I'm getting desperate (or rather, angry at this). My problems started when I had the great idea of wanting to go back to computer gaming, but I didn't want to install Windows again. So I decided to give a try to VirtualBox. Unfortunately I had some problems due to my Kernel.

My Kernel was supposedly an older one, but I always make sure to do all the updates. Given that I had to install some VirtualBox modules that matched the Kernel I had a problem because the older Kernel didn't have matching VirtualBox modules in Synaptic. So I decided to try and upgrade the Kernel and I purged the older Kernel version. Result was that GRUB was changed with a long list of Ubuntu with different Kernels. Problem is, none of actually loads! I get an Error 22 no matter what choice I make.

I need to be able to boot up my system (obviously!). Now, I would have tried using SuperGRUB but **problem is my laptop's dvd drive isn't working!** What can I do?

Thanks beforehand,
Ederico.

---

### Post by Ederico on 2008-08-10
Can't anybody help? I'm basically stuck without my computer here and if I didn't got used to Ubuntu I would have already decided to wipe it out and reinstall Windows. I hope that PC gaming will start getting serious on Linux soon enough, it is a major drawback!

---

### Post by dexter on 2008-08-10
Grub error 22:
> 
22 : No such partition This error is returned if a partition is requested in the device part of a device- or full file name which isn't on the selected disk.


It seems like grub tries to load a kernel from an invalid partition. 
You could start with a live cd. Look in /boot/grub/menu.lst, you'll find a list there with all the installed kernels and the partition it can be found. e.g.
```

title           Ubuntu 8.04.1, kernel 2.6.24-19-generic
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.24-19-generic root=UUID=18fb7cac-d32a-4ae7-a81d-e81c9c79cff4 ro quiet splash
initrd          /boot/initrd.img-2.6.24-19-generic
quiet

```
In this case the root partition is located on hd1, partition 0. Try playing with these values to select the correct partition where your root is located.

---

### Post by Ederico on 2008-08-10
> **dexter said:**
> Grub error 22:


It seems like grub tries to load a kernel from an invalid partition. 
You could start with a live cd. Look in /boot/grub/menu.lst, you'll find a list there with all the installed kernels and the partition it can be found. e.g.
```

title           Ubuntu 8.04.1, kernel 2.6.24-19-generic
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.24-19-generic root=UUID=18fb7cac-d32a-4ae7-a81d-e81c9c79cff4 ro quiet splash
initrd          /boot/initrd.img-2.6.24-19-generic
quiet

```
In this case the root partition is located on hd1, partition 0. Try playing with these values to select the correct partition where your root is located.

As I said before my **"dvd drive isn't working"** so I cannot use a live cd. Thanks anyways.

---

### Post by jimv on 2008-08-10
Oops.  Wrong post.

---

