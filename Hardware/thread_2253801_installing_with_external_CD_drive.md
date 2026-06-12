---
title: "installing with external CD drive"
date: 2014-11-22
forum: Hardware
---

### Post by chopra on 2014-11-22
I was just wondering, I'm considering getting a new laptop, and many of the new ones don't have built-in CD/DVD drives.  I have installed Ubuntu on my previous laptops using a CD.  However, I would suspect that an external drive might not be work the same way during boot-up time. So is it possible to install Ubuntu 12 or 14 using an external CD drive?  If so, what are dual boot and installation within windows both options?

Thanks, Chopra

---

### Post by yancek on 2014-11-22
It is possible to install Ubuntu or any Linux using an external DVD drive.  Most of the major distribtuions are too large to fit on a CD.

> If so, what are dual boot and installation within windows both options?

I have no idea what you mean by that.  If you want to install within windows rather than an actual install on its own partition, download and install virtual software such as Virtualbox within windows.  You can also use software such as unetbootin or universal usb installer to put a bootable Linux CD on a flash drive and boot from it and install from it.  If you want to install to an external drive that should not be a problem.  You probably will need to give more details on your system such as the number of hard drives, which one you want to install Ubuntu on and which windows you have.

---

### Post by oldfred on 2014-11-22
I stopped using CDs/DVD a long time ago. But I always made several repair CD like gparted, knoppix, parted magic etc as I wanted to be sure I could boot something. And not long after all those CDs were outdated. 
So I only use flash drives and now with multiple hard drives I directly boot ISO from another hard drive.
Flash drives are reusable and faster than the DVD.

If a new computer it will be the new Windows 8 using UEFI with the new gpt partitioning. Lots of changes and you will want to read up on  that. Many links in the link in my signature.

---

### Post by chopra on 2014-11-23
> **yancek said:**
> It is possible to install Ubuntu or any Linux using an external DVD drive.  Most of the major distribtuions are too large to fit on a CD.



I have no idea what you mean by that.  If you want to install within windows rather than an actual install on its own partition, download and install virtual software such as Virtualbox within windows.  You can also use software such as unetbootin or universal usb installer to put a bootable Linux CD on a flash drive and boot from it and install from it.  If you want to install to an external drive that should not be a problem.  You probably will need to give more details on your system such as the number of hard drives, which one you want to install Ubuntu on and which windows you have.

Things obviously have changed a lot since I last installed Ubuntu. I never installed Ubuntu 12, I just upgraded from Ubuntu 10. When I installed Ubuntu 10 there were three options with the  installation CD: one was to wipe out windows, one to install Ubuntu  side-by-side with windows on a dual boot, and one was to install Ubuntu  within windows, so windows would boot up first, then Ubuntu would be  booted up from windows.  

I haven't purchased a new laptop yet, I'm still looking around.  It will only have one hard drive, and I was planning on getting a Windows machine.  If it's brand new, this will be Windows 8, although there are still Windows 7 machines on the market.  

Installing from a CD is just the way I'm used to, and CD's are cheaper than flash drives.  I would want a dual boot.  Hope this gives more information.

Chopra

---

### Post by chopra on 2014-11-23
> **oldfred said:**
> I stopped using CDs/DVD a long time ago. But I always made several repair CD like gparted, knoppix, parted magic etc as I wanted to be sure I could boot something. And not long after all those CDs were outdated. 
So I only use flash drives and now with multiple hard drives I directly boot ISO from another hard drive.
Flash drives are reusable and faster than the DVD.

If a new computer it will be the new Windows 8 using UEFI with the new gpt partitioning. Lots of changes and you will want to read up on  that. Many links in the link in my signature.

Thanks for the links.  If I do get a brand new one, it looks like I'll have to do a lot of reading up.

---

### Post by yancek on 2014-11-24
>  When I installed Ubuntu 10 there were three options with the   installation CD: one was to wipe out windows, one to install Ubuntu   side-by-side with windows on a dual boot, and one was to install Ubuntu   within windows, so windows would boot up first, then Ubuntu would be   booted up from windows.  

When I installed 14.04 I saw the first two options plus the manual option which is called 'Something Else' which is what I used.  The install inside windows which is a wubi install is just meant to test Ubuntu and not meant as a permanent installation from what I've read about it.  Also, it is no longer supported.  Installing VirtualBox within windows and then installing Ubuntu in VirtualBox is a possibility.  A better method is to install Ubuntu on its own partition but if you use windows 8, you will have the added complication of UEFI/GPT booting which oldfred mentioned above.  I would read up on that and try to find some tutorials before installing.  If you have questions after your reading, post here as there are a number of members who are very familiar with the problems you can encounter.

---

