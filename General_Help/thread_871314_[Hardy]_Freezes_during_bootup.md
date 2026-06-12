---
title: "[Hardy] Freezes during bootup"
date: 2008-07-26
forum: General Help
---

### Post by 0liv on 2008-07-26
_Summary:_ Hardy *doesn't* boot with the kernel 2.6.24-**20** but *does* boot with the 2.6.24-**19**. Why?

Hi,

It's been a few days now that Hardy freezes during the bootup process.

When in normal mode, it prints "Starting up..." then freezes.
When in recovery mode, it stops after "Checking 'hlt' instruction ... **OK**".

So, what's just after this step?

Weirdly it's only on kernel 2.6.24-20 that I encouter the problem
as I still can boot without any problem 
when I select the 2.6.24-19 kernel in the Grub menu.

:confused:

So what's happening? What can I do to diagnose and solve this problem?

Thanks in advance!

---

### Post by caljohnsmith on 2008-07-26
I would boot into the 2.6.24-20 kernel, let it hang, then boot from a Live CD, mount the Ubuntu partition, and then view the /var/log/dmesg and /var/log/kern.log files from the partition. Those files record the system errors and other messages that the kernel records at boot time and should help you find out what is causing it to hang.

---

### Post by Kowloon on 2008-07-26
I have same problem when booting 2.6.24-20 but normal with the 2.6.24-19. I've searched the forum and confirmed this is known bug and only affecting AMD cpu.

---

### Post by 0liv on 2008-07-27
So, I assume that there is no other choice than :
-- waiting the upcoming 2.6.24-21
-- 'till then, changing my Grub default to 2.6.24-19

Will Hardy automatically update from 2.6.24-19 to 2.6.24-21?

---

### Post by geirha on 2008-07-27
Do you have the hardy-proposed repository enabled? In the hardy-main, the latest kernel is 2.6.24-19. I suggest you stick to 2.6.24-19 until a proper 2.6.24-20 is released in the main-repository. The hardy-proposed is mainly intended for testing packages before they are released, and in this case your "test" failed.

---

### Post by 0liv on 2008-07-27
I don't see this "hardy-proposed" in my repository list.

Moreover, I only have these five 2.6.24-20 packages installed:
1. linux-headers-2.6.24-20
2. linux-headers-2.6.24-20-generic
3. linux-image-2.6.24-20-generic
4. linux-ubuntu-modules-2.6.24-20-generic
5. linux-restricted-modules-2.6.24-20-generic

Obviously, the package 1 to 4 come from the "main" repository
whereas the 5th one come from the "restricted" repository.

Do I uninstall them?

---

### Post by geirha on 2008-07-27
In System -> Administration -> Software Sources, hardy-proposed is listed in the third tab "Updates"

Also, this command in a terminal should reveal whether you have it added
```
grep proposed /etc/apt/sources.list{,.d/*}
```

There's no -20-version listed at packages.ubuntu.com [http://packages.ubuntu.com/search?keywords=linux-image-2.6.24&searchon=names&section=all](http://packages.ubuntu.com/search?keywords=linux-image-2.6.24&searchon=names&section=all) , and ```
aptitude search linux-image-2.6.24-20
``` on my machine yields no results ...


And it should be safe to uninstall those five packages you listed above. Since they are not working, you don't need them. 2.6.24-19 will become the top/default boot entry (again) after that.

---

### Post by 0liv on 2008-08-04
Thanks!

---

