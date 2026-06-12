---
title: "How to backup the original windows partition in laptop before installing Linux? dd?"
date: 2008-10-24
forum: Hardware
---

### Post by kung fu buntu on 2008-10-24
I'm going to buy my first laptop and it comes pre-installed with windows.
I will then install Linux, but if things go wrong, for example I can't get my hardware to work I will return the laptop and get a refund... BUT for that, I need to deliver it as it was, that is, with windows.

As such, I need to know how can I make a backup of the partition in the laptop and save it to my desktop.
And I only want to backup the real data in the partition, that is, I don't want dd (or whatever program) to backup the free disk space, because otherwise I won't be able to back it up to my desktop HDD (I only have 40GB of free disk space in my desktop).

Another problem is that I don't see how can I copy data from the laptop to my computer, with the laptop's HDD unmounted.
Using a live bootcd and then connecting to my home network?

I would appreciate a lot if anyone here could give me detailed instruction on how to do this.

Thanks!


PS: buying a laptop with Linux pre-installed is not an option. I don't have them where I live. I need to buy them here. I have specific hardware needs.

---

### Post by bigken on 2008-10-24
you could clone the hdd to another hdd then clone it back it will probablys have a recovery patition leave it as it is you will also be able to create recovery cds once you have booted into windows


copying the recovery partition to your pc will not work

---

### Post by bigken on 2008-10-24
safest thing would be to use another hdd

---

### Post by MaindotC on 2008-10-24
What you want to do is use Partimage.  In order to save the copy of the winblows partition I suggest you set up an ftp server and tell Partimage to save the image on the ftp server.  I know that's not "detailed" instructions but if you read the partimage.org site it tells you how to do this.  If you don't know what an ftp server is or how to set it up try googling.

---

