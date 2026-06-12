---
title: "/bin/sh: can't access tty; job control turned off"
date: 2006-11-25
forum: Hardware &amp; Laptops
---

### Post by Bosonator on 2006-11-25
**Edit: Ok, I repeated step 3, but used "sudo apt-get install ubuntu-minimal" instead, and now my computer boots fine. I do, however, get an error message saying "unable to find swap space signature". What the heck does that mean, is it bad, and how do I fix it :) ?**

Hello,

I started up my kubuntu system the other day, and I got an error message during boot-up saying

```

target filesystem doesn't have /sbin/init

Busybox v1.1.3 (Debian 1:1.1.3-2ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
(initramfs)

```

The last line is some type of command prompt. 

My harddrives are mountable with a live-cd, so I tried some of the fixes prescribed in other posts.

1. For one, I checked "/boot/grub/menu.lst". As some others have reported, I got a line saying "root=UUID=a-bunch-of-hex-garbage" instead of "root=/dev/hdb1" as it's supposed to. I repaired this, but it did not fix my problem.

2. I then checked my "/etc/fstab" and "/etc/inittab" files. They contained similar errors, which I fixed, but still my system won't start properly.

3. I then tried using aptitude to do a "sudo aptitude reinstall ubuntu-minimal", but that didn't fix it either. 

My question is this: are there any more files that are used at boot time that I should be checking for errors? Or is there anything else you might recommend trying? I'm really, really not keen on reinstalling! Thanks in advance for advice.

Also, if you've seen my previous post, I've started this new one so I can frame my question a little more clearly than I originally did (I'm not just trying to be obnoxious :) )

---

### Post by outofnicks on 2006-12-02
I find myself in the same boat--has your problem been resolved, and could you offer any help?
Thanks!

---

### Post by jimbone on 2006-12-03
Yikes.  This just happened to me as well.  Fortunately I can still boot into other OSes.  I will try your suggestions tomorrow and report back if I can get some free time.

This happened right after a hard shutdown, so I'm not entirely surprised.

---

### Post by DougieFresh4U on 2006-12-03
I have had a thread going **ALL NITE **w/this. I have at least got my grub in front of me now. Waiting for some one to tell me what to do next. I wonder what is causing this tty thing? My thread is in 'General Help' so if you get it fixed give me a 'Holler" please.

---

### Post by jimbone on 2006-12-03
Following the OP's instructions worked great.  Thanks.

---

