---
title: "USB HD hotplug and eject problems"
date: 2007-07-27
forum: Hardware &amp; Laptops
---

### Post by arathorn2nd on 2007-07-27
Hello folks.

I got some serius problems with Feisty and my USB HD. Actually, a laptop PATA HD and USB 2.0 case.

If hotplug is on, it's impossible to umount it. After ejecting, it gets remounted and it's impossible to safely remove it (even with sync on mounting options) unless I shut down Ubuntu.

When hotplug is off, I always get the same message saying it can't be ejected, but at least it's umounted.
Also, I have to manually open it on Computer twice to get it mounted.

To make things worse, I have a few partitions there and all get mounted if I try to mount just one. Not much of a problem, but seems like a strange behavior.

Can anyone help me with this?

---

### Post by coffeecat on 2007-07-27
I have an answer, but it's not very satisfactory.

I've had this problem, but at the moment my install is behaving itself - I just tried it. I plugged a USB flash drive in which was automounted. Then I right-clicked and selected eject and it did. I know a lot of people have had this, but my system is fully up-to-date so I suggest you install all updates and see if that fixes what is obviously a common bug.

But if not, this is what I was doing:

Look in /media and see what the mountpoint is - it should be the same label as what appears on the desktop. Let's say this is /media/USBdrive. Open a terminal and:

```
sudo eject /media/USBdrive
```When I was having the problem this always worked so I hope it does for you.

**Edit:** The automounting of all partitions is normal. A bit of a nuisance when you've got about twelve to unmount. :(

---

