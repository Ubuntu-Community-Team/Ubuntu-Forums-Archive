---
title: "How do I format a USB drive?"
date: 2005-06-01
forum: Hardware &amp; Laptops
---

### Post by zugvogel on 2005-06-01
Hi,

Can anyone tell me how I convert the format of my USB hard-drive (which is currently NTFS) to FAT? Is there a program that will do this? I looked at fdisk, but I'm not sure how to use it (if it is indeed the correct program).

Any help / guidance on how to do this would be very much appreciated.

Thanks.

---

### Post by Alexander Kirillov on 2005-06-01
[QUOTE=zugvogel]Hi,

Can anyone tell me how I convert the format of my USB hard-drive (which is currently NTFS) to FAT? Is there a program that will do this? I looked at fdisk, but I'm not sure how to use it (if it is indeed the correct program).

Any help / guidance on how to do this would be very much appreciated.

Thanks.[/QUOTE]
 Take a look at gparted. I've used it with hard drives, but not with USB ones, though.

Warning: AFAIK, you can not "convert" NTFS filesystem to a FAT one - you will have to copy data elsewhere, then reformat the drive (erasing all data!)

---

### Post by arunsub on 2005-06-01
You can't convert NTFS to FAT32. Though there are couple of tools available, it's not advisable and you might loose your data. Take a backup and reformat the drive. You can use [http://visopsys.org/partlogic/index.html](http://visopsys.org/partlogic/index.html) which is similar to partition magic in windows. I haven't tried this on USB drive. You can give it a try.

---

### Post by az on 2005-06-01
Reformat it into fat.  The windows nonsense about once a hard drive is ntfs, there is no going back only refers to you if you want to keep your data.  It's a pen drive, how big can it be.  It should be easy to copy all your files.

[http://packages.ubuntu.com/hoary/otherosfs/dosfstools](http://packages.ubuntu.com/hoary/otherosfs/dosfstools)


sudo mkdosfs /dev/sda1 (or whatever your drive is...

---

### Post by zugvogel on 2005-06-01
Thanks for all your prompt replies.

I looked for the two programs, but they were not in the add/remove list (maybe because I'm using a Live-CD?). In any case, the command-line command worked well.

Unfortunatly, I had another drive plugged in at the time, and first off I re-formatted that by accident, using that command line (although it was already FAT-format). Is there any way to recover the information (about 200mb)? I've set someone back quite a few hours of work...

Thanks.

---

### Post by az on 2005-06-01
I am sorry.  I did mention to use that if /dev/sda1 is your drive.  In this case your drive may have been /dev/sdb1.  You may have formatted your primary hard drive had you made a typo (or had I...)

You are screwed.   Your data is not recoverable by any means I know.

---

### Post by zugvogel on 2005-06-01
[QUOTE=azz]I am sorry.  I did mention to use that if /dev/sda1 is your drive.  In this case your drive may have been /dev/sdb1.  You may have formatted your primary hard drive had you made a typo (or had I...)

You are screwed.   Your data is not recoverable by any means I know.[/QUOTE]

Ok, thanks anyway. I don't blame anyone except myself - I know enough about the different sda1 sdb1 etc that I shouldn't have made that mistake. Since the drive was hidden behind the laptop screen, I didn't see it was plugged in, which is unfortunate, to say the least. Thanks for your help though. The information was good.

---

