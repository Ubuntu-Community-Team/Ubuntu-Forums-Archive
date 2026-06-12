---
title: "Are Ubuntu Live CDs Make HDs Read Only?"
date: 2008-08-06
forum: General Help
---

### Post by Killtodie on 2008-08-06
When you load off the Ubuntu CD, does it make the HDs read only? If so, anyway around that? I'm trying to copy data to this MacBook that has a password on that no one knows...

---

### Post by hermes0710 on 2008-08-06
You should re-mount the device you want using uid=1000,gid=1000. If you want help on how to do this read the "mount" command documentation ([http://linux.about.com/od/commands/l/blcmdl8_mount.htm]("http://linux.about.com/od/commands/l/blcmdl8_mount.htm"))

---

### Post by mb_webguy on 2008-08-06
Yes, you should be able to edit the files on your hard drive using the LiveCD, but if the MacBook in question has Ubuntu installed on it (which I'm not entirely clear about from reading your post), then you can boot into recovery mode at the GRUB menu, which puts you at a command prompt as root.

---

### Post by nbayiha on 2008-08-06
> I'm trying to copy data to this MacBook that has a password on that no one knows... 
Really hard to understand what you mean.
> When you load off the Ubuntu CD, does it make the HDs read only?
Do you mean when you install the live CD ? And you system is protected with your password ? so be more precise please cause i don't understand what you mean.

---

### Post by Killtodie on 2008-08-06
MacBook. Has OS X 10.x.x

Account has password, client wont pickup the phone.
I need to xfer 30GB to it of an external.

I am trying an Ubuntu CD. Load of CD, "try it before install"

It sees the Mac HD but is read only. I cant copy or create any directories on it.

I just tried Ubuntu recovery remix and it wont even see the Mac HD.


What do I need to copy data to the mac HD aside from physically taking it out

---

### Post by mb_webguy on 2008-08-06
Hrm.  Sounds like the drive is being mounted without write permissions.  You should be able to unmount the drive and remount it with write permissions.

Could you boot from the LiveCD, open the terminal, and post the results of "mount"?

---

