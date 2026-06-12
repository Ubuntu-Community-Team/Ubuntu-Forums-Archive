---
title: "No grub after Live CD install"
date: 2009-04-02
forum: Installation &amp; Upgrades
---

### Post by Nobel on 2009-04-02
Hi guys.

I've come across a problem trying to install Ubuntu 8.10 after being away from Ubuntu from some time (ubuntu did not play well with my former hardware). But now i'm back and ready to get serious. My problem is this:

I was running Windows XP Pro on a 120 gb SATA drive. I also have a 500gb drive with data on it (music, film etc).

I installed Ubuntu from a live CD on to the 120gb drive, assigning 50gb to the ext3 filesystem, and 2gb swap. I used manual partitioning, because the gparted pre-defined settings were giving me a headache. (This might be part of the problem.. I'm not very wise when it comes to how the Ubuntu filesystem works and such).

To my surprise, when i rebooted from the live cd, the machine booted straight in to windows. It seems grub is not proberly installed.

I tried following the following guide, replacing all the variables with values specific to my system (as defined in the thread):
[http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")
I completed all the steps without any odd error messages.

Any ideas as to what might be going wrong? Any help is appriciated

Thanks in advance!
Nobel

---

### Post by cariboo on 2009-04-02
Did the

```
find /boot/grub/stage1
```

command actually find anything? The final step:

```
setup (hd0)
```

Should actually write the data to the mbr.

You can't run the commands from you install they have be done running the LiveCD. You shouldn't get any erros at all if you are doing right.

Jim

---

### Post by Nobel on 2009-04-02
> **cariboo907 said:**
> Did the

```
find /boot/grub/stage1
```

command actually find anything? The final step:

```
setup (hd0)
```

Should actually write the data to the mbr.

You can't run the commands from you install they have be done running the LiveCD. You shouldn't get any erros at all if you are doing right.

Jim

Hi Jim, thanks for replying.

```
find /boot/grub/stage1
```
This command returned hd1,4

I then ran

```
setup (hd0)
```

Without any erros. Is it supposed to be
```
setup (hd1)
```
Or something similar, since the find command returned hd1,4? Or are those two things not connected?

Thanks.

---

### Post by Nobel on 2009-04-02
After reading around a bit, it became apparent to me that grub might be installed to the wrong hard drive. I did not think of this possibility before, because I thought grub would be installed to the hard drive that had an existing boot loader (the windows one) by default.

I'm now booting grub from the 500gb data drive, and everything seems to be running perfectly.

Should i leave grub on this drive, or install it on the other one?

Thanks

---

