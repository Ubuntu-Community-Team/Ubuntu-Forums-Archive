---
title: "Ubuntu driver supported motherboard help"
date: 2021-12-03
forum: Hardware
---

### Post by garnold on 2021-12-03
I'm hoping to build a home server to do some development work on. Ubuntu is the OS that I have chosen to use for this machine. I know that getting hardware that works well with this OS is really important and I don't want to buy something that is only going to give me trouble when trying to put the machine together. Here is what I'm looking for and I hope the users here can help me.

[LIST]
[*]First, if there is a place that has this information already, a link would be great and I could start there 
[*]Compatible motherboard with Ubuntu. I'm not a super star when it comes to trouble shooting drivers so something plug and play is top of mind 
[*]On board video. 
[*]On board NIC 
[*]Up to 128g memory 
[*]M.2 / NVMe support. Would be great if there was more than one 
[/LIST]

I guess that's my starting point. It's been years since I have built a machine so I'm sure I have forgotten something but I'll get there. Is there any other hardware I should be worried about with regards to compatibility? I was hoping since most items are on board I would have a better chance of drivers working since the mother board was supported.

---

### Post by oldfred on 2021-12-03
Some have posted that a Raspberry Pi works as a server. Or lowest end Intel or AMD based system.

But for development that is not the same requirements as a server.
Almost all motherboard manufacturers seem to say they do not support Linux, but work.
I have both 2014 Asus and 2016 Gigabyte that have worked without issue.

Best to check NIC, many have had driver issues with some models/brands.

This site regularly does reviews.
[https://www.phoronix.com/scan.php?page=home](https://www.phoronix.com/scan.php?page=home)
And is related to this site where users post performance and specs of their system.
[https://openbenchmarking.org/](https://openbenchmarking.org/)

I used pcpartpicker when building my system. It saved me from wrong HDD as I wants SFF, which needed laptop 2.5"drive, but I was selecting standard 3.5" drive. 

These are now older, but examples of what you can research.
oldfred's new SFF system with skylake i5-6500 and 16.04
[http://ubuntuforums.org/showthread.php?t=2315007&p=13449024#post13449024](http://ubuntuforums.org/showthread.php?t=2315007&p=13449024#post13449024)
[http://pcpartpicker.com/p/8QKkCJ](http://pcpartpicker.com/p/8QKkCJ)
TheFu's AMD build
[https://ubuntuforums.org/showthread.php?t=2438507](https://ubuntuforums.org/showthread.php?t=2438507)
[https://thepcbuild.net/best-custom-pc-builder-websites/](https://thepcbuild.net/best-custom-pc-builder-websites/)

---

### Post by rsteinmetz70112 on 2021-12-03
My personal recommendations other may disagree.

GPU: Stay away from Nvidia use AMD if possible.
NIC: IBM seems to be the best in performance and compatibility. 

Most motherboards will work and Ubuntu will usually just load the correct drivers, although newly released hardware may not have drivers yet.

---

