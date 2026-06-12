---
title: "Before installing Ubu I need to shrink Vista partition, but page files won't let me!"
date: 2009-04-29
forum: Installation &amp; Upgrades
---

### Post by porinoco on 2009-04-29
Hello,
I am not a very knowledgeable laptop user, so I have this question. I have a Dell Inspiron 1545 laptop, with Vista installed on a 280 G partition. I want to install Ubuntu 9.04 and let it have three quarters of the hard drive, since I think once I have installed it, I won't be using Vista very often. I have already done that before so the actual creation of the partition and installation is not a problem.

My problem is that it won't let me shrink the partition by more than 120 G (Ubuntu would have only less than half hard drive), apparently because of the page files. I was wondering if it is possible to move this page files and make the partition more 'compact', and if you know of any good tutorial which might explain in simple terms how to do it. Or do you think it is not advisable and I should leave things as they are now (installing Ubuntu in the meagre partition)?

Thank very much!
Riccardo

---

### Post by Kareeser on 2009-04-29
Ubuntu usually doesn't require much in terms of space. Many people have their entire / partition (excuding /home) on 8 GB, which leaves plenty of room for large programs such as KDE or OpenOffice.org.

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             9.4G  3.2G  5.8G  36% /
...
/dev/sda6              98G  8.0G   85G   9% /home

```

I've allotted 10 GB to my system partition, and only 36% of it is used!

/home itself is highly dependant on what you put on it, such as media files and documents. By default, I believe it is empty (verify?)

---

### Post by coffeecat on 2009-04-29
This might be what you are looking for:

[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)

Before you start, make sure you have restore DVDs or a working restore partition in case Vista gets corrupted.

Just one comment. You say that the 280GB Vista partition will only shrink by 120GB, and that means you'll have to install Ubuntu in this "meagre" space. 120GB?! Meagre?! :shock:

:wink:

Tch. Tch. Youngsters these days. My first PC with a hard drive (and it wasn't my first PC either) had a hard drive of - wait for it! - 10MB. Yes - TEN MEGAbytes. :p

**Edit:** seriously though, if you do manage to shrink Vista down some more, think about making a shared NTFS data partition. That's what I do. Ubuntu has no problems reading and writing to NTFS these days (although it's best not to write to a Vista C: partition), and Vista will see it as E: or whatever. That way, you only need a small Ubuntu root partition. I usually set up one of about 15GB and rarely use more than half of that so long as I store personal files on the data partition.

---

### Post by hockman5 on 2009-04-29
In Vista, remove all but your most recent system restore points, then turn off system restore, then defrag. This will free up more space for you. Remember to turn system restore back on if you want it when you are done.

---

