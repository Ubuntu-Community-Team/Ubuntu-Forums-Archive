---
title: "Hard drive detection"
date: 2011-03-15
forum: Hardware
---

### Post by thomasdsc on 2011-03-15
Okay, this may be in the wrong section, but I don't know where this go to.
So anyway, I installed ubuntu 9 on my external hard drive a year ago, and had been booting it with many different computers, I used it all the time, till now.
I recently had a friend of mine who has full access of my hard drive wanted to put some files on my hard drive and he wanted to access them from windows. However, I figured out no windows os can detect the hardrive. Its was confirmed when I used my disk manager and found out that it has no format. Not even NTFS or FAT32, (i remember ubuntu has a unique format but whatever it is , it didn't show up). So any ideas how can I access my hard drive on windows?

---

### Post by Jonker on 2011-03-15
Hi, 
 
I haven't tried these programs, but I think they schould work. If I understood you correctly, you want to acces your Ubuntu partitions from Windows. 
 
Incase your Partitions are formated as ext2 / ext3, you could try this program: 
 
[http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html)
 
I hope I could help...

---

### Post by Jonker on 2011-03-16
and, did it work?

---

### Post by thomasdsc on 2011-03-18
Sort of yes, sort of no.
Um, I am accessing the drive from a WIN7 machine, and I installed that software, I had to use compatibility mode. 
But now, instead of not showing up at all, my computer can detect the external HD. But still cannot recognize the format. It is probably the OS's fault. Know any alternatives?

---

### Post by pricetech on 2011-03-18
Boot to live CD with the drive connected and use gparted to downsize your Ubuntu partition and create another partition, formatted NTFS for use with windows.

I've never used anything to make windows see Linux file systems, so I can't recommend anything.

---

