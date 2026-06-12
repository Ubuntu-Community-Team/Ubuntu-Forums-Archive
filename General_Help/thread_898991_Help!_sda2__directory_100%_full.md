---
title: "Help! sda2 / directory 100% full"
date: 2008-08-23
forum: General Help
---

### Post by MeanStreak on 2008-08-23
Hi,

I have run out of space on my sda2 / directory (see attached snapshot). I need to free up some space urgently as I cannot install updates!

---

### Post by munkyeetr on 2008-08-24
Considering that drive is !! 45GB !! you have quite some cleaning up to do. And your /home directory is on it's own partition. wow.

I would use something like Disk Usage Analyzer (which should be installed on your system, I am using Arch, so don't hate me if I am wrong.) I think you can launch it either through the menus or by typing the following command in the terminal:
```

baobab &

```

then press the **Scan Filesystem** button and start looking around.

Try to find out where all that space is being used. **If you are unsure what you can delete, post back and ask.**

---

### Post by LateNiteTV on 2008-08-24
> **munkyeetr said:**
> Considering that drive is !! 45GB !! you have quite some cleaning up to do. **And your /home directory is on it's own partition. wow.**

I would use something like Disk Usage Analyzer (which should be installed on your system, I am using Arch, so don't hate me if I am wrong.) I think you can launch it either through the menus or by typing the following command in the terminal:
```

baobab &

```

then press the Scan Filesystem button and start looking around.

Try to find out where all that space is being used. If you are unsure what you can delete, post back and ask.

do u see a problem with this? in my freebsd systems, i have partitions for /home /etc /usr /tmp and /
this is smart because if something happens to... say that / partition and you dont have a seperate /home partition, say gbye to all your ****.

---

### Post by munkyeetr on 2008-08-24
> **LateNiteTV said:**
> do u see a problem with this? in my freebsd systems, i have partitions for /home /etc /usr /tmp and /
this is smart because if something happens to... say that / partition and you dont have a seperate /home partition, say gbye to all your ****.

I certainly know the pro of seperate filesystems. What amazes me is mean streak has used up an entire 45GB partition for /. I mean, I could see it happening if /home was not seperated (a music collection and a few dvd's).

But geeze, I allocate 14GB for my entire system, then store my important things on another drive, and currently I have 10.8GB free.

...Unless, of course, he's been hozed and someone is using him for Storage. But, alas, we should just wait and see what he comes back with.

---

### Post by LateNiteTV on 2008-08-24
lol oh ok i see what ur saying. i thought you meant like "geez this guy shouldnt have a seperate /home partition".
i run freebsd on 6 of my 7 systems and on all of them i have allocated 512mb for /
i still have over 400mb on all of my systems for /

and i know guys that have <=100mb / partitions.

---

### Post by dexter.deepak on 2008-08-24
> **MeanStreak said:**
> Hi,

I have run out of space on my sda2 / directory (see attached snapshot). I need to free up some space urgently as I cannot install updates!

try :
```
sudo apt-get clean
```
this will remove the downloaded packages from the /var/cache/apt/archives

---

