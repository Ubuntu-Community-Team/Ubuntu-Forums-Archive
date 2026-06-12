---
title: "unexpected sudden shutdown on Acer laptop"
date: 2010-05-31
forum: Hardware
---

### Post by ybukhman on 2010-05-31
Hi,

I have installed Ubuntu 10.04 LTS on Acer Aspire 5315-2582 laptop.  My laptop suddenly shuts down from time to time.  This happens instantaneously, as if someone has pressed the power button.  This is not a Ubuntu-specific issue: I've had the same problem when I was running Windows 7.  How do I diagnose the problem?

Here's some info about my system:


yury@yury-acer:~$ uname -a
Linux yury-acer 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux
yury@yury-acer:~$ cat /etc/issue
Ubuntu 10.04 LTS \n \l

Thanks!

Yury

---

### Post by ajgreeny on 2010-05-31
Overheating problem?

An old acer laptop of mine will not run 10.04 sensibly, largely due to its ATI 9000 mobile graphics card, which does not support kernel power management systems used by 10.04.  The machine gets far too hot, almost to the point of being incomportably hot to rest my hand on.  Earlier Ubuntu versions did not make the laptop suffer like that, and it still runs 9.10 beautifully.

---

### Post by ybukhman on 2010-06-01
I don't think it's an overheating issue: it doesn't feel that hot.  How do I find out what it is?

Yury

---

### Post by ybukhman on 2010-07-27
Solved the problem by upgrading the BIOS to version 1.45 (Dec 2008 )  See details here: [http://ubuntuforums.org/showthread.php?p=9646303#post9646303](http://ubuntuforums.org/showthread.php?p=9646303#post9646303)  It probably was an overheating issue after all.

---

### Post by ybukhman on 2012-08-24
Upgrading BIOS didn't solve the issue after all: crashes began less frequent but continued.  What did ultimately solve it was to take the laptop to a repair shop where they blue gunk out of the ventilator.

Yury

---

