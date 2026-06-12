---
title: "Windows partition read-only"
date: 2011-11-01
forum: Hardware
---

### Post by Draven501 on 2011-11-01
I needed some extra space on my windows 7 partition, so I deleted a file storage partition using GParted and transferred the unallocated space to my C: drive. Then when I tried to move some files to my windows partition in Ubuntu it said the partition was read only. I prayed for it not to be true but Windows does not boot, it says that the partition is not readable. It also gave me an error code which I cannot remember now; I can post it if it helps. 

I know I'm kind of a noob but could you please help me with this?

---

### Post by coffeecat on 2011-11-01
> **Draven501 said:**
> It also gave me an error code which I cannot remember now; I can post it if it helps. 

Yes, it might.

I presume from your description that you resized the Windows partition. It sounds as though this may have caused filesystem damage and Ubuntu will mount damaged fileystems read-only.

First thing to try. After selecting Windows from the grub menu, press F8 quickly and repeatedly. You have to get the timing right to get the white on black Windows Advanced Boot Options. The first option is "Repair Your Computer". Try that.

Another thing to check, but I doubt whether this is relevant since Windows itself doesn't boot. If you are running Ubuntu 11.10, check that you still have the ntfs-3g package installed which gives you NTFS read-write capability. Some people are reporting it as having disappeared from their systems, possibly because they installed a conflicting package.

---

### Post by Draven501 on 2011-11-01
Ok the error code is: 0xc0000225 (actually its a status code)

It says that I need my windows install disk to enter recovery (btw I have win7 x64 enterprise) but I have no idea where the disk is.

This could be a partition order problem as well, because the partition that I deleted was sda1 but I deleted it so now there is no sda1 and the Msoft "SYSTEM RESERVED" partition is sda2 and C: is sda3

I could make a small dummy partition in sda1 and see if that fixes it?

EDIT:  I just discovered that "SYSTEM RESERVED" is also read only

---

### Post by coffeecat on 2011-11-02
> **Draven501 said:**
> Ok the error code is: 0xc0000225 (actually its a status code)

It says that I need my windows install disk to enter recovery (btw I have win7 x64 enterprise) but I have no idea where the disk is.

Googling suggests that the status code is associated with a damaged boot sector. Some of the hits are from people experiencing this after resizing a Windows partition with a Linux partitioner. From what I can remember (which is hazy) Windows doesn't like one or more of its boot files moving.

If the problem really is as simple as repairing the Windows partition(s) boot sectors and you can't find your install disc, then you should be able to do this with a Windows 7 repair CD which you can create from any Windows 7 system. Can you get access to another Windows 7 system to make this?

> **Draven501 said:**
> This could be a partition order problem as well, because the partition that I deleted was sda1 but I deleted it so now there is no sda1 and the Msoft "SYSTEM RESERVED" partition is sda2 and C: is sda3

If System Reserved is sda2 and your C: partition is sda3, then sda1 was probably a manufacturer's restore partition. 

> **Draven501 said:**
> EDIT:  I just discovered that "SYSTEM RESERVED" is also read only

Did you check to see if you have ntfs-3g installed in Ubuntu? You shouldn't be writing to System Reserved anyway.

Lastly, did you try F8? You don't say.

---

### Post by Draven501 on 2011-11-02
Yes I do have ntfs-3g and I did try F8 to no avail, it just made an error noise for about 15 seconds then I was greeted with the same error screen. I did manage to mount sda2 and 3 as read and write using the method here: 
[http://ubuntuforums.org/showthread.php?t=624943]("http://ubuntuforums.org/showthread.php?t=624943")

using this command:
sudo ntfs-3g -o rw /dev/sda3 /media/windows

I can get access to a Win 7 x86 machine easily and a x64 machine with greater difficulty. I know this must sound very noobish, but can I use a disk made with an x86 system with my x64 one?

---

### Post by coffeecat on 2011-11-02
> **Draven501 said:**
> I can get access to a Win 7 x86 machine easily and a x64 machine with greater difficulty. I know this must sound very noobish, but can I use a disk made with an x86 system with my x64 one?

That's a good question and, to be honest, I don't know, but I think you have to use 64-bit for 64-bit. If you look at the links on this site for paid-for repair CDs...

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

You'll see that there are separate 32-bit and 64-bit versions of both the Windows 7 and Vista repair CDs.

---

### Post by Draven501 on 2011-11-02
Ok I'll make a 64 bit repair cd and get back to you.

EDIT: I found the installation DVD while looking for a blank cd lol. It was a boot file problem and the install disk fixed the problem so now I have Win 7 back thanks for all the help!

---

