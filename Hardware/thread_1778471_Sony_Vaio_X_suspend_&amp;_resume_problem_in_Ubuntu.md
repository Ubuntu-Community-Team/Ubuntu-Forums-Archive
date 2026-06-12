---
title: "Sony Vaio X suspend &amp; resume problem in Ubuntu 11.04"
date: 2011-06-09
forum: Hardware
---

### Post by MishnayicHacker on 2011-06-09
I recently installed Ubuntu 11.04 on a friend's Sony Vaio X (the exact  model number is VPCX131KX).  He told me about a few issues he has found,  and I haven't found the solution for them in the forums.  So I'm going  to post each one as a separate thread here, in hopes of finding the  answer and perhaps helping future searchers with the same issue.

The problem here is that after suspending his netbook by closing the  cover, and later opening it again, it doesn't resume.  Pressing the  power button also doesn't cause it to resume.

There is also an option to hibernate the laptop by pressing Fn-F12, and  after that it's possible to resume from hibernation by pressing the  power button.  That works fine.

But after closing the cover and opening again, apparently the only  option is to hold the power button until it turns off, and start from  scratch.

In Power Management, in "When laptop lid is closed", the option chosen is "Suspend" for both AC and battery power.

Is there another way to do it that I should know about?

Thanks!

---

### Post by vmajor on 2011-06-25
I have what seems to be the same problem with my Acer aspire 5553. It appears to resume once the lid is opened, the status lights come on, the HDD spins up, but the display remains blank and the only way to recover is to force reboot by holding the power switch down.

I also did not manage to find a solution that works after trawling the internet. I submitted a bug in LP [https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/802074](https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/802074)

As a suggestion, post in that bug so we will hopefully get some attention. A similar sounding bug on LP was "expired" due to no activity for 15 days.

V.

---

### Post by conservasian on 2011-07-01
On my Lenovo T61, this worked for me!  :D
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/598664/comments/25](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/598664/comments/25)

It resumes properly from closing the lid on my laptop, the keyboard suspend and going to the menu.

Prior to this, I would get a messed up/squiggly screen when I tried to resume.  But, despite not seeing anything coherent on my screen, I typed in my user name [enter], then my password [enter] and then it would resume to my desktop like normal.

Hope this works for you too!

---

### Post by federico_hyo on 2011-08-07
hi guys, 
I just installed on my sony vaio X  vpcx13kx ubuntu 11.04 and I also have the same problem.. the computer doesn't start after resume or hibernation. 

Anyone found a solution for this? Do you know if with the previous version of ubuntu was working?

thanks

---

