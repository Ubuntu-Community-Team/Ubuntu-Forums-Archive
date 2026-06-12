---
title: "read-only file system on USB drive"
date: 2011-03-28
forum: Hardware
---

### Post by vitalix on 2011-03-28
Hello!  I don't know if there is this kind of topic already, I couldn't find it, if it exists, please show me.  My problem is I have an external USB drive Toshiba (320gb). It worked just fine before, but now I can't write on it because of &quot;read-only file system&quot;. This message shows up on both my laptops when I'm trying to do some operations with it.  Can somebody help me with that? Thanks in advance!

---

### Post by coffeecat on 2011-03-28
What is the filesystem on it? If you are not sure, plug the drive in and then open a terminal. Post the output of this command:

```
sudo fdisk -lu
```

Also, what is the exact message you get when you try to write to it from Ubuntu?

---

### Post by vitalix on 2011-03-28
> **coffeecat said:**
> What is the filesystem on it? If you are not sure, plug the drive in and then open a terminal. Post the output of this command:

```
sudo fdisk -lu
```Also, what is the exact message you get when you try to write to it from Ubuntu?

for this drive output is:
/dev/sdd1            2048   625137344   312567648+   c  W95 FAT32 (LBA)

and the message is:

an error ocured during creation directory in /media/TOSHIBA EXT

and below this:

error when opening the file in "/media/TOSHIBA EXT/new file": Read-only file system
(it is not the original messages, it's translation, but meaning is the same)

---

### Post by coffeecat on 2011-03-28
If Ubuntu detects an unclean filesystem on a FAT32 partition it will mount it read-only. You need to exclude that as a possibility first.

You could use dosfsck in Ubuntu but if that was my drive I would prefer to use chkdsk in Windows. Do you have access to Windows? FAT32 is a Microsoft filesystem so chkdsk is preferable to dosfsck.

---

### Post by stefangr1 on 2011-03-28
I've also had this a few times with usb-sticks. It seems that it's not always simple to correct, but as a simple workaround you can always mount it manually in an empty folder with the option umask=0.

To do this, you open a terminal and locate the appropriate device using```
sudo fdisk -l
``` after which you mount it with```
sudo mount -t vfat umask=0 /dev/sd## empty_folder
```

---

### Post by vitalix on 2011-04-05
Thank you all guys for the help!:D

---

### Post by xandrani2 on 2013-02-10
I know this is an old thread BUT Google sent me here when searching for this problem, and so I want to leave a solution to others in the future.

For me I did the following (Do this at your own risk).

1. sudo fdisk -l            <--- this tells you the device name i.e. /dev/sdc1 or whatever.
2. umount /dev/sdc1         <--- You MUST unmount the device.
3. sudo fsck -y /dev/sdc1   <--- Automatically fix any issues.

I had been having more and more problems with this particular USB stick. It was FAT format. I was having occasional copy problems AND more rarely the read only issue. This has fixed all those problems.

I hope this helps someone in the future. May we create good karma by leaving solutions like this! :)

Best wishes
Mike :)

---

