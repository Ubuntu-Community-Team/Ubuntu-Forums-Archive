---
title: "Wubi vs gparted + install"
date: 2011-10-31
forum: Hardware
---

### Post by anataraj on 2011-10-31
I am trying to install Ubuntu on my brand new Thinkpad. My colleague suggested I use gparted to partition first and then install Ubuntu. I think Wubi figures this out in its installation pipeline.

Are there any specific advantages in using one approach over another?

---

### Post by bcbc on 2011-10-31
Wubi doesn't partition - it installs to a virtual partition (a file on the host windows file system).
That's great if you just want to try out Ubuntu as it's easy to uninstall later.

If you want a normal dual boot then you can use the Ubuntu CD/USB to partition as you install. If you have vista/7 then I recommend creating free space first using Windows' Disk Management utility.

It's also a good idea to boot from an Ubuntu CD/USB in live mode - select "Try it" without installing - just to make sure that it's fully compatible or to figure out what special boot options you might need for your hardware.

Also see how compatible your computer is for Ubuntu 11.10: [http://friendly.ubuntu.com/?desktops=on&laptops=on&stars=1&release=4&popularity=any&term=Thinkpad](http://friendly.ubuntu.com/?desktops=on&laptops=on&stars=1&release=4&popularity=any&term=Thinkpad)

---

### Post by warlock43 on 2011-10-31
I would use Wubi especially if you are going to dual boot. Using Wubi eliminates errors that can be made if you ever needed to remove/reinstall Ubuntu!

---

### Post by anataraj on 2011-11-01
Thank you for your responses. I apologize if this question is very naive but apart from the ease of installing / uninstalling what is the BIG difference between running Ubuntu from a virtual partition compared to a hard partition: performance? interference between OSes if any?

---

### Post by Rhizoid on 2011-11-01
Are you restricted to a single HDD (i.e. most laptops) or can you install another?

If you can add another disk then leaving windows and it's bootloader on one disk and installing Ubuntu and grub2 to the other disk will completely avoid any interplay between them other than planned activity.  It also prevents Windows startup recovery from blitzing your bootloader and stopping you from starting Ubuntu.

Most BIOS have a tool to choose a temporary boot device which you can then use to start your secondary OS - whichever that may be.

---

### Post by bcbc on 2011-11-01
> **anataraj said:**
> Thank you for your responses. I apologize if this question is very naive but apart from the ease of installing / uninstalling what is the BIG difference between running Ubuntu from a virtual partition compared to a hard partition: performance? interference between OSes if any?

There is no noticeable difference - unless you run them together and have a stopwatch you'll see that a normal install is faster.

The big difference is that the virtual partition is *a single file containing a virtual file system and many files within it*, as opposed to *a real partition with many separate files*. You can probably see the risk in that: all your data and settings and programs with a wubi install are held in a single file and if it is accidentally deleted (unlikely) or corrupted (which does happen to some - but generally happens if you force a poweroff) then you can lose the entire install.

Many people use wubi longterm without issues. I have never lost a virtual disk, but there are some who have and the reasons aren't always clear (in some cases it may be a minor hardware compatibility - pure speculation). In a lot of these cases, but not all, running chkdsk from windows will fix the corruption and you can recover the lost root.disk as well.

Oh yeah, and you can't hibernate on a wubi install. Standby is supported.

So my advice - if you use Wubi - take backing up data really seriously and avoid hard poweroffs (**Alt + SysRq R-E-I-S-U-B** will do a safe reboot in most cases if things hang up).

---

### Post by Atomic-Fanboy on 2011-11-01
I would suggest Wubi.

Previous posters have discussed how easy it is to uninstall, should you wish to.

**However-** Should you like Ubuntu so much that you're willing to keep it permanently, all you have to do is create a new, formatted, empty partition using a Linux file system (eg. Ext4), then find and run Wubi-move (a very useful script someone posted on Ubuntuforums that moves the virtual partition to a partition that you choose).  The advantage of this is that your partition could easily be much more than 30GB (the maximum virtual partition size supported by Wubi).

---

### Post by anataraj on 2011-11-02
Thank you everyone for your suggestions. I partitioned my hard disk using Windows Disk manager and installed Ubuntu successfully!

My life was made easy following instructions from this lady
[http://www.youtube.com/watch?v=GhnLk3gviWY](http://www.youtube.com/watch?v=GhnLk3gviWY)

The little detail you need to pay attention to is the file system ... you will need to choose between ext3 OR ext4.

---

