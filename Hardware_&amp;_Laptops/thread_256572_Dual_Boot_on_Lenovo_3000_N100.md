---
title: "Dual Boot on Lenovo 3000 N100"
date: 2006-09-13
forum: Hardware &amp; Laptops
---

### Post by lisigef on 2006-09-13
I would like to get the Lenovo 3000 N100 and have seen a bunch of posts that Ubuntu 6 installs fine on this system.

Does anyone run a dual boot with WinXP (no flames please, I'm sharing the computer with someone who needs this!)? I was told that IBM has software to save the current system state and can be used for reinstalling or rolling back to a previous state. 

If new partitions are created after WinXP is installed, and another OS put on one of them (there will be a third partition with data to be sahred by WinXP and UBUNTU) will this rollback software be able to deal with it?

If you have any experience with this please let me know.

Thanks,

-Lisi

---

### Post by wjp.reg on 2006-09-13
> **lisigef said:**
> I would like to get the Lenovo 3000 N100 and have seen a bunch of posts that Ubuntu 6 installs fine on this system.

Does anyone run a dual boot with WinXP (no flames please, I'm sharing the computer with someone who needs this!)? I was told that IBM has software to save the current system state and can be used for reinstalling or rolling back to a previous state. 

If new partitions are created after WinXP is installed, and another OS put on one of them (there will be a third partition with data to be sahred by WinXP and UBUNTU) will this rollback software be able to deal with it?

If you have any experience with this please let me know.

Thanks,

-Lisi

Lisi;

I have a Lenovo 3000 N100 dual booting Windows XP Pro (NTFS) and Ubuntu Dapper (EXT3) with a shared (FAT32) partition.

Yes, the IBM recovery software works great so long as you don't accidently remove it when setting up your new partitions :)

No you won't be able to use it to to restore your dual-boot configuration; it can only return you to the factory setup (so you loose ubuntu and any other partitions).

I suggest you use a good backup utility instead.

The setup procedure I used is as follows:

1) Make a set of recovery CD's or DVD, whatever your case may be.
2) Defrag Windows
3) Using the Ubuntu Install CD, resize the windows partition ( I shrunk it to half).
4) Next, create a /boot partition; I used 200MB
5) Create an extended partition of type FAT32 for your shared data (whatever size you feel you require).
6) Create a swap partition in the extended area (size is normally double your RAM)
7) Create the / (root) and /home partitions in the extended area

Follow through with the install.  You don't want anything installed to the Master Boot Record (MBR), as you will likely loose access to the IBM reovery partition (that's the purpose of the /boot partition).  Your window and recovery partitions and Shared partition should automatically be mounted and appear as icons on your desktop.

You will have to install the wide screen (915resolution) module using synaptic.  You may find your soundMAX card isn't working, but is recognized and you can find a fix for that by searching this forum.  The wireless and ethernet nics should work  fine "out of the box".

Hope this helps, Enjoy!!

---

### Post by lisigef on 2006-09-30
OK, so I got the laptop a couple of days ago and tried the Ubuntu installation yesterday.

I followed your partitioning instructions, and the installation seemed to go OK. It never asked me, BTW, where I wanted to install grub, which I'm pretty sure it did with the previous version I installed on another machine.

When I restarted it seemed to boot into Linux just fine but when I rebooted and tried to go into Windows it went straight to the Lenovo Restore software.

Obviously something got installed in the wrong place - is there a way to fix this so I can boot into WinXp or do I have to restore the system to it's original state and then try the installation again? What would I have to do differently to get around this next time?

I'm sure you need more info to answer this so let me know.

Thanks!

-Lisi

---

### Post by lisigef on 2006-09-30
OK, Never Mind - apparently Grub entered WinXp and the recovery partition as two separate OSs and as long as I choose the correct entry it does boot into WinXP.

Now I just have to figure out how to get it to connect to the wireless network...I'm sure this is in the forums.

Thanks!

-Lisi

---

### Post by Kefas on 2007-01-12
> **wjp.reg said:**
> 
No you won't be able to use it to to restore your dual-boot configuration; it can only return you to the factory setup (so you loose ubuntu and any other partitions).


This is not true. When opting to restore to the factory setup, you get the option to choose to roll it out on either the entire hard disk or only the C: drive. I've done this a couple of times and did not loose any data on my other partitions when choosing the latter option.

---

