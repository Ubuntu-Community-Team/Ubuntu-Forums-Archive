---
title: "URGENT: Problem with Booting my Laptop - Please help!"
date: 2008-10-14
forum: Hardware
---

### Post by Sebastian12 on 2008-10-14
Hi,

I recently formatted one of my internal hard drives on my other laptop.

I was in Vista, and I was formatting the other hard drive which contained Ubuntu (I was installing it on an external).  Everything seemed to go well, the hard drive was left blank for my storage needs and the Vista one was left untouched and still full.

Then, after I shut it down and restart it there's a huge problem.  It says "Loading GRUB... Error Loading GRUB... Error 17".  I think this has to do with the fact that I had the Ubuntu OS up higher on the boot order (Ubuntu first, Vista last).

I tried to change the boot order through the options my computer gives me without an OS but it only gives me the option of the "Laptop Hard Drive" which doesn't help because there's two.

I know Vista is still installed on my laptop because it was working before, I just don't know how to access it from this position and it's very fustrating - I need it for school!

Please help me out on this one; I'd really appreciate it!

---

### Post by darrenn on 2008-10-14
Dont worry this is really easy to fix.

---

### Post by darrenn on 2008-10-14
Here is the answer.

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by xENO_ on 2008-10-14
It looks like your MBR isn't doing it's job anymore, since it either contained or pointed to a GRUB installation that is no longer complete.

Since you removed Ubuntu, you probably don't want to use GRUB anymore, so darrenn's answer isn't the way to go.

If you didn't install GRUB to your MBR, it's an easy fix: reset the active partition to the Vista partion in a tool like fdisk; cfdisk should work nicely.

If youd *did* install GRUB to your MBR, you have three options:
(a) Reinstall Vista
(b) Reinstall Ubuntu
(c) Do some system voodoo using a Windows Vista DVD or an Ubuntu CD and put a Microsoft-style MBR on the hard drive.

---

### Post by darrenn on 2008-10-14
All you have to do is restore your grub using a live cd. Follow my link I posted in the previous post.

---

### Post by Sebastian12 on 2008-10-14
It won't let me boot from a live CD.  It still says the same thing.

---

### Post by xENO_ on 2008-10-14
> I tried to change the boot order through the options my computer gives me without an OS but it only gives me the option of the "Laptop Hard Drive" which doesn't help because there's two.
If there's a CD/DVD/whatever-ROM option, you need that to be the first one in that boot order list or it won't boot from a CD.

---

### Post by Sebastian12 on 2008-10-14
Nevermind, my mistake.  Wrong burned CD.

---

### Post by darrenn on 2008-10-14
You could also erase grub by using a vista cd. Not sure how to do it. But a quick google search should show you how to do it. You shouldn't have to reinstall vista.

---

