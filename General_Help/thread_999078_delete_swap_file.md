---
title: "delete swap file"
date: 2008-12-01
forum: General Help
---

### Post by Richardarkless on 2008-12-01
Hey all, let me start by saying that I have 100% switched to Ubuntu Linux and am happy with it. Problem is I got 1GB RAM and dont do much hardcore stuff on there so I dont need a swap file, so was just wondering if I could delete it.

I chose the default option to use the whole hard drive option in the GUI installer so dont know or remember the file name of the swap file

Thanks in advance
Richard

---

### Post by ncanna1 on 2008-12-01
You should always keep a swap file around so that the system can allocate low priority processes to the swap and use the RAM for higher priority jobs.  I think if you run out of RAM and don't have a swap partition, it may even cause a kernel panic.  

So no, it's not a good idea to remove the swap.

---

### Post by Richardarkless on 2008-12-01
> **ncanna1 said:**
> You should always keep a swap file around so that the system can allocate low priority processes to the swap and use the RAM for higher priority jobs.  I think if you run out of RAM and don't have a swap partition, it may even cause a kernel panic.  

So no, it's not a good idea to remove the swap.

ok fair point, problem is I have installed it on a netbook and it has only 4GB hard drive so is there a way of reducing it

---

### Post by spcwingo on 2008-12-01
You can boot back up with the live cd and use gparted to resize your partitions...including swap.

---

### Post by Richardarkless on 2008-12-01
> **spcwingo said:**
> You can boot back up with the live cd and use gparted to resize your partitions...including swap.

Thanks that worked perfectly, just to let you know that I found out that you dont need to boot off the live cd, just install it in synaptic package manager but problem is that you cant resize the OS partition

someone can close it now if they want

---

### Post by albandy on 2008-12-01
if you're using a dual boot machine (windows/Linux) you can make a swap file in the windows partition in this way:

(this will create a 1GB file)
sudo dd if=/dev/zero of=/windows/swap.file bs=1024 count=1310720
sudo mkswap /windows/swap.file

you can start it manually by typing
swapon /windows/swap.file
or you can add it to fstab.

---

### Post by snowpine on 2008-12-01
> **Richardarkless said:**
> Thanks that worked perfectly, just to let you know that I found out that you dont need to boot off the live cd, just install it in synaptic package manager but problem is that you cant resize the OS partition

someone can close it now if they want

You can resize the OS partition if you boot from a Live CD.

---

### Post by lswb on 2008-12-01
You can deactivate swap and reduce the size of the partition from your normal environment but to "grow" your working paritition into the freed space the it must be unmounted. You can't unmount / from a running system so the easiest thing is to do all the steps from a live CD or gparted live CD.

I would suggest booting from a live CD, use gparted to first backup your your working partition by cloning it to a usb stick (just in case). After backing up by this or other method, you can use gparted to select & shrink the swap partition, shrinking it "away" from the working partition, then select and grow the working partition into the freed space.

FYI my notebook has 1GB memory and I have only once seen any swap being used, it was less than 100MB as I recall.

It is also possible to use a swap file instead of a swap partition. The file has to "reserve" space in the filesystem so you don't gain any more space for regular file storage, but it does make it much easier to experiment with different size swap, since the size can be changed right from your normal working environment (no live CD or alternate booting method needed)

---

