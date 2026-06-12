---
title: "ipod and external hdd is invisible/undetectable"
date: 2008-06-16
forum: Hardware
---

### Post by parrhesiastes on 2008-06-16
sudo fdisk -l


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4f274f27

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60050   482351593+  83  Linux
/dev/sda2           60051       60801     6032407+   5  Extended
/dev/sda5           60051       60801     6032376   82  Linux swap / Solaris

It seems to me as if it only recognizes my internal HDD

---

### Post by Odrodzona-Sarmacja on 2008-06-16
Try "sudo blkid". It should show you all hds that can be mounted on your os.
If your os doesnt show there, then install gparted and check with it what is wrong with hd.

Maybe you miss some file system driver on your xubuntu.
Maybe partitions on your hds are damaged.

Good luck!

---

### Post by parrhesiastes on 2008-06-16
/dev/sda1: UUID="20acfd3f-b281-4a07-a3a9-75dbe4eee8a4" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="b5b82264-726a-4428-83c0-0eda0f061163" 

I get this when I run the code you mentioned. I honestly don't know what this means.
I installed the program you mentioned but it doesn't show up in applications (or anywhere else obvious) so I am lost there as well.

---

### Post by parrhesiastes on 2008-06-17
umm.... help, please, anybody.

---

### Post by rossmoore on 2008-06-17
It looks like your iPod and external hard drives are not being recognised as disk devices by the linux kernel at all.

I think we need to examine your usb and system message logs. Try this:
With nothing plugged in, type:
lsusb
Now plug in your external hard drive and try again:
lsusb

Now type:
dmesg | tail

and post the output of all of that.

---

### Post by Odrodzona-Sarmacja on 2008-06-17
Gparted on my Xubuntu's desktop appears in "system->partition editor".

However if your Linux kernel doesn't see your hard drives (Gparted can't find it automatically on your system either, when you start that program up)... then maybe you should boot up your computer with your Ubuntu livecd and with your external drivers connected and see if it can see (auto detect) them at all. Maybe Ubuntu just doesn't support them... yet. It is sad, but not every piece of hardware is supported by Linux... yet. If livecd doesn't see your external drives... well... then wait for few years and try again. After all it is only matter of time before Linux will support hardware like windows xp does right now.

---

### Post by parrhesiastes on 2008-06-18
I re-installed Ubuntu because I noticed that occasionally it wasn't loading properly on start-up. My computer can now recognize my externall HDD on some USB ports and not others. I am still having difficulty with my ipod.
I wonder why some USB ports work and not others.

---

### Post by Odrodzona-Sarmacja on 2008-06-21
If Ubuntu can recognize hd only on some USB ports, then maybe you should check your BIOS settings for USB and see if all options are enabled for it.

---

