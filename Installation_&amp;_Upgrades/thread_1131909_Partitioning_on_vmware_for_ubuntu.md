---
title: "Partitioning on vmware for ubuntu"
date: 2009-04-21
forum: Installation &amp; Upgrades
---

### Post by budoor on 2009-04-21
Hello  all 

I opened a new virtual machine for ubuntu on the vmware, but afer installing ubuntu, an icon called installation occured on the desktop .. One of the steps is to do partitioning, so how can i manage that? what is the concept exactly and can I do partitioning if i am using vmware? how??

---

### Post by mwacky on 2009-04-21
When you setup a new virtual machine with VMware it will want you to specify where and how much space to allocate to the VM harddrive (this is how big the filesystem can be and will use on your physical drive).

Then you will want to use a live cd or iso and install ubuntu, during the installation process you will parition the Virtual Drive just as you would a physical drive(you can accept the default for swap and ext3/4) or you may want to tweek it.  

The concept of partitioning is the same whether you are physical or virtual, the extra step in setting up a VM is making the virtual hard drive (which is just stored in your filesytem).

---

### Post by avathar7 on 2009-04-22
hi! i'm new here on forum and i didn't figure out how to make a new thread(yet).  my problem is:
when i've installed ubuntu(inside w) i didn't allocate all the space available for ubuntu and now i like to change that but i don't know how...is there any command for this?

---

### Post by budoor on 2009-04-25
> **mwacky said:**
> When you setup a new virtual machine with VMware it will want you to specify where and how much space to allocate to the VM harddrive (this is how big the filesystem can be and will use on your physical drive).

Then you will want to use a live cd or iso and install ubuntu, during the installation process you will parition the Virtual Drive just as you would a physical drive(you can accept the default for swap and ext3/4) or you may want to tweek it.  

The concept of partitioning is the same whether you are physical or virtual, the extra step in setting up a VM is making the virtual hard drive (which is just stored in your filesytem).

Ok .. what if I choose 8 GB for the memory? What is the best space to have for each partition (D and C) and how many partitiotns I have to do? Are they only 2 or it could be more?

---

