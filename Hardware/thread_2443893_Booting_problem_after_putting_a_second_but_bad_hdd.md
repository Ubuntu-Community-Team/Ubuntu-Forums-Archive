---
title: "Booting problem after putting a second but bad hdd into my pc"
date: 2020-05-21
forum: Hardware
---

### Post by chrisnk on 2020-05-21
Hi!
After I put a second hdd to my pc where Lubuntu is the OS and booted the OS everything worked fine for some minutes.
After some time I got a msg something like "... read-only file system...".
Ok, I rebooted the OS and it hang on something called GRUB menu or so.
Ok, I figured out maybe my second hdd made a problem. I took it out and tried again but without success.

After investigating the problem I got a msg from some sort of advanced menu from GRUB:
"Root file system requires manual fsck".
Ok, I managed that too.

There was several errors on my hdd file system as I understood. I fixed them by pressing "Y".
Rebooted the OS and now everything is fine.

BUT!
It turned out does my second hdd which has NTFS file system actually it has tons of bad sectors.
I assume, this triggered the msg of "... read-only file system...".
After I took out the hdd maybe the file system of linux remembered that hdd and tried to mount it or whatever and that cos the not booting problem.

Can somebody maybe give me an explanation what was happened in there?

Now is everything fine and in working condition. :KS

I just wanna know something what could cause this kind of problem.
I'm a Linux user but with not much administrating skill in linux.

Thanks.

---

### Post by yancek on 2020-05-21
ntfs is a proprietary microsoft windows filesystem and it is highly unlikely you will be able to repair it from any Linux OS.  Usually, boot windows and run chkdsk.
If you don't know what GRUB is, you need to do some reading on it.  It's been  in use for decades and most Linux systems use it. Massive amounts of info on it if you do an online search.  Grub2 manual is at the link below which would be a good starting point.

[https://www.gnu.org/software/grub/manual/grub/grub.html](https://www.gnu.org/software/grub/manual/grub/grub.html)

> "Root file system requires manual fsck". 

The message above indicates problems on your Ubuntu system partition.  You need to use fsck on it and again, lots of sites with info on how to use and examples for different situations.

You indicate that you have a 2nd hard drive with an ntfs filesystem but do not indicate that you have any windows OS installed.  If not, why use ntfs?  If you have a windows OS installed such as 10, it leaves the system hibernated by default and you won't be able to mount it from Linux due to the high risk of data loss.  So either turn hibernation off or don't access the ntfs partition from Ubuntu.

---

