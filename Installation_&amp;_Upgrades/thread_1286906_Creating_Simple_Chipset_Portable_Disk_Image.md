---
title: "Creating Simple Chipset Portable Disk Image"
date: 2009-10-09
forum: Installation &amp; Upgrades
---

### Post by jboehm on 2009-10-09
Hi,

I would like to create a generic disk image that can be moved between motherboards with different but similar chipsets.  (The video card would always be nvidia.)  My plan is to install Ubuntu from cd, install the latest nvidia driver, then install the HW test I need.  

During the install or post processing how much HW specific things are installed?  My thought is none to very little since I believe most of this is dynamic in the kernel.  Is this correct?

When I've moved a boot disk between HW in the past I've noticed this triggers a disk scan on boot but I don't know if the disk can be trusted to perform on the new system the same as if it was installed on that system from scratch.

Thanks,
Jon

---

### Post by dannyboy79 on 2009-10-09
> **jboehm said:**
> Hi,

I would like to create a generic disk image that can be moved between motherboards with different but similar chipsets.  (The video card would always be nvidia.)  My plan is to install Ubuntu from cd, install the latest nvidia driver, then install the HW test I need.  

During the install or post processing how much HW specific things are installed?  My thought is none to very little since I believe most of this is dynamic in the kernel.  Is this correct?

When I've moved a boot disk between HW in the past I've noticed this triggers a disk scan on boot but I don't know if the disk can be trusted to perform on the new system the same as if it was installed on that system from scratch.

Thanks,
Jon
i have moved a HD from one set of hardware to a new set of hardware with no issues in the past. the hardware obviously has to be x86 32bit based though. good luck

---

### Post by jboehm on 2009-10-12
Bump... Thanks dannyboy.  Any one have a more definitive technical answer to this question?

---

### Post by dannyboy79 on 2009-10-13
> **jboehm said:**
> Bump... Thanks dannyboy.  Any one have a more definitive technical answer to this question?

how much more technical can I put it? if all the chipsets are either x86 32 bit or x86 64 bit then you can move an image of an OS throughout various hardware. if you make the image with the most generic video card (using vesa module maybe) then you should be all set.

---

### Post by dannyboy79 on 2009-10-13
> **jboehm said:**
> Bump... Thanks dannyboy.  Any one have a more definitive technical answer to this question?

how much more technical can I put it? if all the chipsets are either x86 32 bit or x86 64 bit then you can move an image of an OS throughout various hardware. if you make the image with the most generic video card (using vesa module maybe) then you should be all set.

---

### Post by tgalati4 on 2009-10-13
Windows would perform a disk scan and usually vomit when swapping disks between 2 different machines.

Linux enumerates all hardware during boot and normally can run well on all hardware of the same hardware:  x86 for instance.  A PPC version of linux would not work on an x86 version.

You can print out the modules used by both machines to see the differences:

```

cd
lsmod > modules_that_I_have_inserted_for_this_machine.txt

```

By comparing the two, you will quickly see the differences between the running kernels.

---

