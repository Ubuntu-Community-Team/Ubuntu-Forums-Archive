---
title: "How to Remove?"
date: 2009-01-14
forum: Installation &amp; Upgrades
---

### Post by Hoom@n on 2009-01-14
Hello!
I have Ubuntu, Kubuntu & Windows XP installed on my computer. I have 2 swap, 2 ext3 & 1 ntfs filesystems. My bootloader is Grub. Now I want to remove linux. How can I do that?!
(I think I know what to do with filesystems, I will use Gparted. But, what can I do with grub?)
Thank you.

---

### Post by Partyboi2 on 2009-01-14
You can use a windows xp disk to fix the mbr after you have deleted the ubuntu paritions.
Boot the windows xp installation disk into recovery then at the prompt type
```
fixmbr
```Or you can use [[COLOR=Blue]supergrub[/COLOR]]("http://supergrub.forjamari.linex.org/")

[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

---

### Post by Hoom@n on 2009-01-16
> **Partyboi2 said:**
> You can use a windows xp disk to fix the mbr after you have deleted the ubuntu paritions.
Boot the windows xp installation disk into recovery then at the prompt type
```
fixmbr
```Or you can use [[COLOR=Blue]supergrub[/COLOR]]("http://supergrub.forjamari.linex.org/")

[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

I've installed Ubuntu on my old laptop. I only have the laptop's recovery disk. It can recover the computer completely, but it can't act like a windows disk. What can I do?!
+Please explain Super Grub Disk more.
Thanks.

---

### Post by Partyboi2 on 2009-01-16
Supergrub disk is a program that can be used to fix grub issues, however it also has the ability to restore the windows boot loader which will remove grub.
You can read more on how super grub works from [[COLOR=Blue]here[/COLOR]]("http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html")
To fix use the winodws boot loader you can boot the Super grub disk and select "english super grub" then choose "windows" and finally "Fix Boot of windows"

---

