---
title: "can not adjust brightness. Acer Aspire 7715."
date: 2012-05-27
forum: Hardware
---

### Post by carsten888 on 2012-05-27
I can only use Kubuntu in save mode, else I need a torch to the screen to see anything at all. In the system config >  energy management I found the brightness settings, but changing them has no effect at all.

I googled and searched  this forum for days and this is clearly a big problem with a lot of people.

I tried my laptops Fn + F6 button, but that only works in save mode.

I did a check for driver updates, but all was fine.

I found various thread pointing to changing etc/default/grub like:
[http://ubuntuforums.org/showpost.php?p=11158182&postcount=13](http://ubuntuforums.org/showpost.php?p=11158182&postcount=13)
but that file seems to be a root file which I can not edit. I tried with sudo gedit, but do not get access to edit the file. Maybe I'm doing something wrong. This is my first Kubuntu experience, and I find this a bit of a steep learning curve.

Should I just wait for the next version of Kubuntu in which this is fixed? Or does anyone know how to get rights to edit that file?

---

### Post by carsten888 on 2012-05-28
I was able to edit the file with 'sudo nano', updated the grub and rebooted, same problem.

ready to give up on Ubuntu.:(

---

### Post by carsten888 on 2012-10-21
When will there be a next version of Ubuntu in which this issue is hopefully fixed.

I reading about windows 8 and it scares the wits outof me. really want to try Ubuntu.

---

### Post by carsten888 on 2013-01-22
Does anyone know if this issue has been solved in Ubuntu 12.10?

---

### Post by Simeo on 2013-02-19
> **carsten888 said:**
> Does anyone know if this issue has been solved in Ubuntu 12.10?

I have Ubuntu 12.10 and an Aspire 4830TG. I had the same issue. This worked for me: [http://www.refreshit.info/2012/08/solved-brightness-increase-and-decrease.html](http://www.refreshit.info/2012/08/solved-brightness-increase-and-decrease.html)

I can now use the fn key to change brightness. Hope this helps.

---

