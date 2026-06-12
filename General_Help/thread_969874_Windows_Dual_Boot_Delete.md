---
title: "Windows Dual Boot Delete"
date: 2008-11-03
forum: General Help
---

### Post by Landscapeman on 2008-11-03
I have ubuntu dual boot with windows xp. I have only used the windows part 2 times. I dont want to lose anything on the Ubuntu part but get rid of windows completely. Any ideas on how I can do this? Thank You.

---

### Post by Monotoko on 2008-11-03
Boot into the Ubuntu LiveCD then go to
(System -> Administration -> Partition Editor (you wont see this unless your on the LiveCD))

Once you have done that, just delete your windows partition (if your certain) then you can grow your ubuntu partition to take up that space if you want

---

### Post by Landscapeman on 2008-11-03
Thanks, I should of thought of that.

---

### Post by thomas228 on 2008-11-03
> **Landscapeman said:**
> Thanks, I should of thought of that.

what happens to the wubi installation and the ubuntu files sitting on the windows directory ?

I'm a newbie with a dual boot and was wondering how to get ubuntu 8.04 migrated over to a non-win partition. 

Am I missing something here ??:confused:

---

### Post by louieb on 2008-11-03
> **thomas228 said:**
> ..was wondering how to get ubuntu 8.04 migrated over to a non-win partition.:confused:
Different question: Its is better to start another thread. But from the WUBI section of the forum. 
[**LVPM: Upgrades Wubi installs to dedicated-partition Ubuntu installs**]("http://ubuntuforums.org/showthread.php?t=438591http://ubuntuforums.org/showthread.php?t=438591")

---

### Post by louieb on 2008-11-03
> **Landscapeman said:**
>  Any ideas on how I can do this? 
Use the live CD and format the partition to ext3. Then you can use it to store data. A a good idea to keep you data on a different partition in case you have to reinstall the OS.

---

### Post by thomas228 on 2008-11-03
> **Landscapeman said:**
> I have ubuntu dual boot with windows xp. I have only used the windows part 2 times. I dont want to lose anything on the Ubuntu part but get rid of windows completely. Any ideas on how I can do this? Thank You.

> **louieb said:**
> Different question: Its is better to start another thread. But from the WUBI section of the forum. 
[**LVPM: Upgrades Wubi installs to dedicated-partition Ubuntu installs**]("http://ubuntuforums.org/showthread.php?t=438591http://ubuntuforums.org/showthread.php?t=438591")

thanks for the link
I hope the OP reads it before he deletes windows partition

Thanks again And I'll migrate ubuntu following your link
If I have more questions I'll post them in the WUBI section;)

Tom

---

### Post by TeXtonyx on 2008-11-03
thomas228 wrote: "thanks for the link
I hope the OP reads it before he deletes windows partition"

TeX: I didn't read anything in the OP's posts that suggested he
was using Wubi. The OP said "dual boot" and most people use that
term to mean booting from either the Windows partition or the
Ubuntu partition which are logically&physically separate. Sometimes 
they say dual boot to mean booting each OS from different drives.

I've read a description as Wubi creating a file within the Windows partition.
Ubuntu installed to its own partition is outside of the Windows Partition.
Only in the unlikely event that Ubuntu's grub was installed to its own
/boot partition, and Windows booted Ubuntu from boot.ini or bcd would
there be a problem; unlikely because he likely has grub in the MBR.

---

### Post by thomas228 on 2008-11-03
> **TeXtonyx said:**
> thomas228 wrote: "thanks for the link
I hope the OP reads it before he deletes windows partition"

TeX: I didn't read anything in the OP's posts that suggested he
was using Wubi. The OP said "dual boot" and most people use that
term to mean booting from either the Windows partition or the
Ubuntu partition which are logically&physically separate. Sometimes 
they say dual boot to mean booting each OS from different drives.

I need to change my signature as I thought I was using grub to dual boot ie either windows vista or ubuntu.
Like I said previously I'm a newbie to linux.
What is the correct way of id'ing a virtual disk installation??
or should I ask this in a new thread ??

Tom

---

### Post by Landscapeman on 2008-11-03
Virtualbox is really easy. I would compile at source, [www.virtualbox.org](www.virtualbox.org). It will basically tell you step by step. Good Luck

---

### Post by TeXtonyx on 2008-11-04
thomas228 wrote: Like I said previously I'm a newbie to linux.
What is the correct way of id'ing a virtual disk installation??
or should I ask this in a new thread ??
-----------------------

As I understand it, since I'm not using Wubi, Wubi runs as a program
which can be deleted by Windows Add/Remove programs utility. That 
is much different than a filesystem which is physically present on
the hard disk and persists. One can run the Ubuntu live cd also and
have the use of Ubuntu but it doesn't persist. I don't think "dual
boot" is an apt term to describe the ability to run Windows, or 
Ubuntu from a live cd from the same computer. Do you? When you
run, sudo fdisk -lu when in the Wubi demesne ;-)does it report
Wubi as existing within or without the Windows (sda1?) partition?

Perhaps your question has existential import and ought to be asked
in the Cafe. Did you see The Matrix? How does one distinguish 
when one is in a simulation that appears to be reality. Really,
I posted because you assumed Wubi was in play when I don't think 
more than half of the dual booters, and 60% of Ubuntu users dual 
boot, run Ubuntu by the Wubi style. Maybe that assumption isn't
so bad because I thought anybody who ran Wubi would know enough
not to delete Windows and expect to still have Ubuntu. Maybe my
opinion is too charitable. :p

---

### Post by thomas228 on 2008-11-06
> **TeXtonyx said:**
> thomas228 wrote: Like I said previously I'm a newbie to linux.
What is the correct way of id'ing a virtual disk installation??
or should I ask this in a new thread ??
-----------------------

As I understand it, since I'm not using Wubi, Wubi runs as a program
which can be deleted by Windows Add/Remove programs utility. That 
is much different than a filesystem which is physically present on
the hard disk and persists. One can run the Ubuntu live cd also and
have the use of Ubuntu but it doesn't persist. I don't think "dual
boot" is an apt term to describe the ability to run Windows, or 
Ubuntu from a live cd from the same computer. Do you? When you
run, sudo fdisk -lu when in the Wubi demesne ;-)does it report
Wubi as existing within or without the Windows (sda1?) partition?

Perhaps your question has existential import and ought to be asked
in the Cafe. Did you see The Matrix? How does one distinguish 
when one is in a simulation that appears to be reality. Really,
I posted because you assumed Wubi was in play when I don't think 
more than half of the dual booters, and 60% of Ubuntu users dual 
boot, run Ubuntu by the Wubi style. Maybe that assumption isn't
so bad because I thought anybody who ran Wubi would know enough
not to delete Windows and expect to still have Ubuntu. Maybe my
opinion is too charitable. :p

If I offended you I apologize.

I am running a WUBI installation and I thought I was dual booting.

Here is what you asked for:
sudo fdisk -lu

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x39633962

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048     3074047     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *     3074048   234440703   115683328    7  HPFS/NTFS

Disk /dev/mmcblk0: 2045 MB, 2045247488 bytes
47 heads, 46 sectors/track, 1847 cylinders, total 3994624 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1             247     3994623     1997188+   6  FAT16

I'm using the following thread to change to a better installation

[http://ubuntuforums.org/showthread.php?t=438591](http://ubuntuforums.org/showthread.php?t=438591)

With that this will be my last post on this thread 

[http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy) #1, #4 & #7

Good luck
Tom

---

### Post by TeXtonyx on 2008-11-06
thomas228 wrote: "If I offended you I apologize."

You didn't offend me. I don't think you understood that I changed
my mind about whether the warning from you would be useful. You
knew not to delete Windows. Maybe other Wubi users wouldn't know it.
So I came more to your point of view. I never objected to asking
on this forum ... I mentioned the Cafe because they discuss a wider
variety of issues and philosophical opinions. I thought that Wubi
didn't qualify as dual booting. I don't think of that as a fact but
more philosophical or a custom. That is why I mentioned the movie
"The Matrix" which is how do you tell physical reality from virtual
reality if one is embedded in the simulation. Good luck to you too.

---

