---
title: "Problem Reinstalling Ubuntu"
date: 2009-02-23
forum: Installation &amp; Upgrades
---

### Post by Wofo on 2009-02-23
First of all, hello people.

I'll tell you the problem I have.

I installed Ubuntu Hardy about 5 months ago, then I updated it to Intrepid Ibex. I made many changes in lots of configurations, sometimes not knowing what I was doing, so at this moment my Ubuntu is a little bit messed up and there are many programs that don't work well.
Under this circumstances I decided to reinstall Ubuntu. So I booted from the Live CD, opened the setup program and found out that Ubuntu didn't recognise the ext3 partition I use, same happened with the NTFS partition. So the only alternative I have now is to make the partitions all over again, the problem is I can't do that because I have Windows XP and don't want it to be eliminated in the proccess.

So, my question is: How can i reinstall Ubuntu without touching the other partitions?

I will appreciate very much your help.
Thanks in advance.

---

### Post by Elfy on 2009-02-23
Does the livecd not see any of your existing partitions?

```
sudo fdisk -l
``` whould show all the partitions on your drives.

To install over the top of the existing partition pick manual when the partitioner starts - 

then right click the old ubuntu partition and Edit partition - 
pick ext3 from the Use As dropdown menu and / from the Mountpoint dropdown menu - 

not sure if there is a format option in edit partitions, if not then tick the correct box on the partition list to format it.

---

### Post by taurus on 2009-02-23
When you get to the partition screen, what happens if you pick the Manual option?  Does it show all the partitions on your harddrive?

---

### Post by Wofo on 2009-02-25
Thanks forestpixie, but I can't do what you say because (also answering to taurus) when i get to the partitioner screen and click in the manual option it doesn't show all the partitions, it shows the entire HD without any partition, even the GNU one.

I hope there's any solution.

Thanks again

---

### Post by Elfy on 2009-02-25
Can you post the result of

```
sudo fdisk -l
```

---

