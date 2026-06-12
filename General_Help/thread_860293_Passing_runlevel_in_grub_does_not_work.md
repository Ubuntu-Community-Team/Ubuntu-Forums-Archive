---
title: "Passing runlevel in grub does not work?"
date: 2008-07-15
forum: General Help
---

### Post by frj on 2008-07-15
Hi,

I have recently installed Ubuntu 8.04 on a box where i want one custom runlevel. I want to be able to boot into runlevel 4, i want to be able to choose ubuntu default or runlevel 4 in Grub. I have done same thing on other distros using Grub and Sysinit. I guess my problem can be related to the usage of Upstart in Ubuntu. 

According to a slightly old (pre upstart?) thread, [http://ubuntuforums.org/showthread.php?t=271800](http://ubuntuforums.org/showthread.php?t=271800) , it should be enough to add a 4 to the end of my kernel line, as i usually do. According to other reading i have done regarding Upstart and Ubuntu i have understood that Upstart in Ubuntu should mimic sysinit. Is it possible to choose runlevel in grub under Ubuntu with Upstart, how is it done?

Here is an excerpt from my menu.lst ```
title           kernel 2.6.24-19
root            (hd0,0)
kernel          /vmlinuz-2.6.24-19-generic root=UUID=## ro quiet splash 4
initrd          /initrd.img-2.6.24-19-generic
quiet
```It is placed above the automatic kernels list. UUID is striped in the post. 

One of my guesses is that it may be a problem bypassing /etc/event.d/rc-default?

Cheers

---

### Post by frj on 2008-07-15
Did some more research found this one:
[https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/85014](https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/85014)

So i added my custom if grep statement to /etc/event.d/rc-default. Since i have UUID in my kernel line i do not grep for a number. Instead i pass a custom string which is unlikely to appear on the kernel line. It works as intended, my box can now boot defaul runlevel or my custom rc4. 

Frj

---

