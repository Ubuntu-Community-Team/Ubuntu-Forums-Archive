---
title: "Wubi Install"
date: 2009-10-17
forum: Installation &amp; Upgrades
---

### Post by sushemsu on 2009-10-17
Okay for my main hard drive I only have 150 gb and then i have a couple of secondary 1tb hd's and I was wondering with wubi if I can install ubuntu with wubi inside windows on a separate hard drive(the one without windows)?

Ie : Windows 7 ultimate - C:/
Want to Install on - E:/ but still have the boot option on load up without having to deal with another partition

(also not sure how I would go about allowing both os's on boot choices without having to manually change hd boot priority each time or selecting boot hard drive)

---

### Post by unmole on 2009-10-17
Since you are currently using Windows, I believe your secondary HD is formatted as NTFS. As long as you can access the specific HD from Windows I see no reason why you can't install Wubi on it. AFAIK you don't have to worry about changing boot priority as Wubi uses a loop file instead of a partition.

---

### Post by sushemsu on 2009-10-17
ty

---

