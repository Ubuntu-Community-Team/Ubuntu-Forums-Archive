---
title: "I have a problem."
date: 2008-10-26
forum: General Help
---

### Post by Helmi_17 on 2008-10-26
Ok guys, please forgive me for not doing an exhaustive search of the forums for this particular issue... But I am in need of advice from those of you who are much wiser than I.

To start this off, I am a VERY NOVICE ubuntu user... as in, this will be my first hurrah into the usage of this particular OS.  I'm using it as a sort of "last ditch effort" to try and recover some data for a friend.

Here is the issue:

I have a compaq laptop that is running Windows XP. Windows had an auto-update and is now stuck in a boot loop.  It will not boot safe mode or any derivitives thereof.  At my disposal I have an external USB hard drive and another laptop running XP pro.  

I am able to boot Ubuntu from the disk on the broken laptop. I am able to see and access my USB HDD. I am unable to mount the HDD in the broken laptop, the partition that has all the data that must be recovered on it.  

When I attempt to acces the HDD with the data that needs saving I get this error message:
-
$LogFile indicates unclean shutdown (0, 1) Failed to mount '/def/sda1': Operation not supported Mount is denied because NTFS is marked to be in use. Choose one action: Choice 1: if you have windows then disconnect the external devices by clicking on the 'safely remove hardware' icon in the Windows taskbar then shutdown Windows cleanly. Choice 2: If you don't have Windows then you can use the 'focre' option for your own responsibility. For example type on the command line: mount -t ntfs-3g /dev/sda1 /media/disk -o force Or add the option to the relevant row in the /etc/fstab file: /dev/sda1 /media/disk ntfs-3g force 0 0
-

I am unable to do a clean shutdown on windows, so option one is a no go.  

I have attempted using the command line provided in the 'terminal' application, but i get the error "Only Root can do that"

So now I ask those of you more wise than I in the ways of Ubuntu to guide me in this momentus task.

Thank you in advance for all your help, and I appreciate you taking the time to read my long-winded issue.

---

### Post by Amazona aestiva on 2008-10-26
> **Helmi_17 said:**
> ... "Only Root can do that" ...

I've hardly any experience with mounting and partitions, but use```
sudo <some command here>
```to run a program as root.

Regards

---

### Post by lisati on 2008-10-26
> **Helmi_17 said:**
> 
I have a compaq laptop that is running Windows XP. Windows had an auto-update and is now stuck in a boot loop.  It will not boot safe mode or any derivitives thereof.  At my disposal I have an external USB hard drive and another laptop running XP pro.  

I am able to boot Ubuntu from the disk on the broken laptop. I am able to see and access my USB HDD. I am unable to mount the HDD in the broken laptop, the partition that has all the data that must be recovered on it.  

I had a similar problem on my desktop this morning after resizing its XP partition, where both the regular XP and the recovery partition wouldn't boot to completion (they restarted the machine instead). The solution included booting up from an XP setup disk in recovery mode and entering the following:
```

chkdsk c: /r
fixboot
fixmbr C:

```
Hope this helps.

As an aside: be very cautions of setup disks of the "don't ask too many questions where they came from" variety: there's too many opportunities for legal hassles and malware.

---

### Post by Helmi_17 on 2008-10-26
when i use sudo <mount -t ntfs-3g /dev/sda1 /media/disk -o force> I recieve a syntax error.

Any ideas what I may be doing wrong?

I may have to try the Windows recovery disk after all, but I've never had any luck with using them.

---

### Post by The Cog on 2008-10-26
The options go before the device name. Try this:
mount -t ntfs-3g -o force /dev/sda1 /media/disk

And it it's hardy, I don't think you need the -3g, try this:
mount -t ntfs -o force /dev/sda1 /media/disk

And ou course you need to create the folder /media/disk first, if its not already there:
mkdir /media/disk

All those commands must be run as root. On a live CD, you can get a root prompt by opening a command prompt (Accessories->Terminal) and entering the command **sudo -i** at the prompt.

---

### Post by lswb on 2008-10-26
Don't use the angle brackets < > in the actual command, just the text you have shown between them.

---

