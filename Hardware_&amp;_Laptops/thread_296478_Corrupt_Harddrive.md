---
title: "Corrupt Harddrive"
date: 2006-11-09
forum: Hardware &amp; Laptops
---

### Post by niko7865 on 2006-11-09
Edgy locked up (control + alt + F* worked but I couldn't log in and control + alt + delete was unresponsive) so I pressed the reset button. When it got past post I got a Grub error 17 so I loaded up the Dapper live CD. In the live CD it says my hard drive is unformatted, any good commands I can run to try to recover it? I'm reading about fsck but it's still somewhat confusing to many. Any help is appreciated, thanks.

It's a 120GB IDE drive that had one ext3 partition taking up the entire drive.

---

### Post by niko7865 on 2006-11-13
72 Hour Bump

---

### Post by niko7865 on 2006-11-13
found the answer, corrupt superblock

[http://ubuntuforums.org/showthread.php?t=243525](http://ubuntuforums.org/showthread.php?t=243525)

> 
Thanks Pea for your help!
I finally got it to work again. I have no idea what caused the error, but I just love Linux more and more... it's way easier to fix a harddrive than it is in Windows. I had some serious data loss with NTFS hard drives on my windows server, but now with linux, everything just works fabulous!

Here's the way I got it to work again
Code:

mke2fs -n /dev/hdc1

That command put out the super block backups, knowing that I ran this command...
Code:

e2fsck -b 32768 /dev/hdc1

Whereas the number was the "coordinate" of the super block
It detected some errors, I said "yes" three times and that's it...
The HDD is finally back on, and everything seems to be there.
I don't know if anything is missing but it seems to be ok

Thanks for your help anyways.
Flo

---

