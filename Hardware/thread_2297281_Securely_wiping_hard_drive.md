---
title: "Securely wiping hard drive"
date: 2015-10-02
forum: Hardware
---

### Post by A Traveller on 2015-10-02
Hi all.

Does writing zeros to a hard disk wipe EVERYTHING just the same as using DBAN, for example, or is it less thorough in any way?

If using DBAN with a bootable USB drive, what's the smallest size USB drive that could be used?

I have looked at the following thread but it makes it seem a complicated process!

Thanks.

---

### Post by sudodus on 2015-10-02
There are different opinions about wiping a hard disk drive to make it impossible for an advanced lab to recover information from it. Some people claim that it is enough to overwrite (once) with zeros, but I think enough people claim that it is not enough, to make me doubt that, and prefer a more advanced method, for example using DBAN or hdparm.

I don't know, if there is a minimum size for ***DBAN*** to work, but I remember problems using it with an external drive. ***hdparm*** works for external HDD and SSD drives, see this link [Ubuntu Forums thread 'best way to wipe a drive' Post #12](http://ubuntuforums.org/showthread.php?t=2124829&p=12555068#post12555068)

It is also possible to use [mkusb - wipe the whole device](https://help.ubuntu.com/community/mkusb#Wipe_the_first_megabyte_or_the_whole_device) to wipe USB pendrives. I cannot guarantee that there are no traces left, but except for extreme cases, I think it is wiped enough (overwritten with zeros) because flash memory does not behave like magnetic memory.

---

### Post by A Traveller on 2015-10-02
Thanks for the info, sudodus.

Forgot to include the link in my last post:

[http://ubuntuforums.org/showthread.php?t=1701757](http://ubuntuforums.org/showthread.php?t=1701757)

Anyhow, I am currently asking about internal drives that will be used again. Internet search keeps throwing up results giving info for when you want the drive to be usable afterwards. Does that mean that there is software that can render a drive unusable and if so, how do make sure I don't use one of those by mistake? Or do they just mean not smashing the drive to bits?

I didn't know there would be different processes for doing external drives or USB drives. I'm looking for something that doesn't take days to run!

Thanks.

---

### Post by sudodus on 2015-10-02
If you heat a HDD (magnetic memory) above the curie temperature, it will be wiped and destroyed completely. If you submerge it into an alternating strong magnetic field, it will also be wiped and destroyed completely. You don't want to do that.

DBAN is a software method, that overwrites the drive to remove traces from the previous content. After that you can create a new partition table and re-use it. ***hdparm*** uses the manufacturer's system to map between the logical and the physical memory. After re-mapping with hdparm, there is no way to recover the previous content. The hdparm method is faster because it is so close to the hardware - much faster than overwriting with zeros using for example cp or dd (or mkusb that uses dd under the hood), and I think also faster than DBAN.

---

### Post by A Traveller on 2015-10-02
> **sudodus said:**
> You don't want to do that.

Haha!

Ok, I think you've sold me the hdparm method. I will try to give it a try first. Thanks for your help.

---

