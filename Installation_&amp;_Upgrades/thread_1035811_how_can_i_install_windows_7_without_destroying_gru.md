---
title: "how can i install windows 7 without destroying grub?"
date: 2009-01-10
forum: Installation &amp; Upgrades
---

### Post by yurib on 2009-01-10
hello,

i have xp and ubuntu 8.10 running and im using grub as a boot manager, i'd like to give windows 7 a try but since i've had problems with booting in the past i would like to know how should i do it in such a way that i will still be able to boot to all os's

---

### Post by vandorjw on 2009-01-10
1. Backup everything you want to save.

2. Install Windows 7. (When you get to the partitioning point, leave room for ubuntu, so that instead of Ubuntu resizing your partition, just do it yourself right away.

3. Install ubuntu to the empty partition.
--------------------------------------------------------------------------

If you are not interested in re-installing ubuntu. Then, install windows 7, overtop of XP? (I just realized you might want to keep XP)....do you?
I'll assume you don't since that would be pointless.

So, when XP is overwritten, grub will likely be skipped.
Restore grub by using this guide.

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Cheers - CC7

---

### Post by yurib on 2009-01-10
actually i was planing to keep xp as well, i wanted to see how windows 7 was like before switching...
but if its a complicated process i guess i could install it over xp and just reinstall xp if i dont like it....
thanks alot for your help :)

---

### Post by K4emic on 2009-01-11
Why would you remove ubuntu completely? It's unnecessary and reinstalling ubuntu takes time.

You can use the ubuntu livecd to resize your partitions (Be careful) and install windows seven on an empty NTFS partition.

Keep in mind that windows seven will make its own bootloader the default one instead of GRUB, so you'll have to deal with that once it's installed.

This guy wrote a post that might give you some insight.
[http://blog.lokonopa.com/grub-up-windows-7/](http://blog.lokonopa.com/grub-up-windows-7/)

Nevertheless, backing up your files is always a good thing.

-- k4emic

---

