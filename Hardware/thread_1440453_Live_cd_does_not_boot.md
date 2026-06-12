---
title: "Live cd does not boot"
date: 2010-03-27
forum: Hardware
---

### Post by Linux Lover II on 2010-03-27
Hi everyone!

Another issue I experience is the following:

When I insert the Ubuntu Live CD into my laptop cd drive, it is recognized, as it shows the menu where I can choose to install, to try it without installing etc. However, when I choose install, it says that something is not empty... and it won't install, neither does the live version start up.

I thought for a while that there was an error on the cd, but when I test the same cd in my desktop machine, it experiences no problem at all.

Does anyone have a solution for this?


Thanks in advance!

---

### Post by khelben1979 on 2010-03-27
What filesystem is it on the harddrive which you try to install Ubuntu on?

---

### Post by Linux Lover II on 2010-03-27
> **khelben1979 said:**
> What filesystem is it on the harddrive which you try to install Ubuntu on?

ext3

But it should not be a problem if it were not, since it even won't start the live (=try) version?

Or am I wrong?

---

### Post by khelben1979 on 2010-03-27
> **Linux Lover II said:**
> ext3

But it should not be a problem if it were not, since it even won't start the live (=try) version?

Or am I wrong?

No, you're right. I don't know what the problem is, but maybe it's a hardware problem? For instance, it could be that the dvd/cd-rom isn't working correctly. What do you think about that theory?

---

### Post by Linux Lover II on 2010-03-27
> **khelben1979 said:**
> No, you're right. I don't know what the problem is, but maybe it's a hardware problem? For instance, it could be that the dvd/cd-rom isn't working correctly. What do you think about that theory?

I don't think so, since it lets me see the menu where to choose try/install/mem test.

It just doesn't start it when i select the option.

And on my dektop he behaves perfectly :o

Strange, isn't it?

---

### Post by coffeecat on 2010-03-27
> **Linux Lover II said:**
> However, when I choose install, it says that something is not empty...

Can you tell us what the something is? That might give a clue.

---

### Post by Linux Lover II on 2010-03-27
> **coffeecat said:**
> Can you tell us what the something is? That might give a clue.
Youre absolutely right:

ACPI: EC: Input buffer  *not empty*, aborting transaction" **.**

---

### Post by coffeecat on 2010-03-27
With the live CD, you could press F6 for other options and choose "acpi=off". This is not an ideal solution but it might get the live CD booted up.

I tried googling, "ACPI: EC: Input buffer not empty, aborting transaction ubuntu" and got quite a few hits, the first being:

[http://ubuntuforums.org/showthread.php?t=1257067](http://ubuntuforums.org/showthread.php?t=1257067)

You might get some leads there or from some of the other google hits.

---

### Post by khelben1979 on 2010-03-27
> **Linux Lover II said:**
> Strange, isn't it?

I don't think so. I still think the problem is hardware related. How the Linux kernel uses the hardware is different depending on what's in there and how the kernel is compiled.

Have you tried installing Ubuntu on a usb stick instead?

---

### Post by Linux Lover II on 2010-03-27
> **khelben1979 said:**
> I don't think so. I still think the problem is hardware related. How the Linux kernel uses the hardware is different depending on what's in there and how the kernel is compiled.

Have you tried installing Ubuntu on a usb stick instead?

Yes, without luck :(

---

