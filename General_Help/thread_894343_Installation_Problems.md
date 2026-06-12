---
title: "Installation Problems"
date: 2008-08-19
forum: General Help
---

### Post by alexgamerz on 2008-08-19
I was looking at an online walkthough on installing linux on a vista computer without losing your data. it told me to shrink my vista partition using the onboard vista partition manager. i was able to shrink it by 7.49 GB. It said that when i booted to the live cd I would have the option to use the free space for my ubuntu partition. I did not have this option. I have two hard drives on my XPS M1730 and they are merged into one (raid). The options i was given were: use entire drive, then it listed my drives, i guess if i only wanted to use one, and then manual. The walkthough said one of the options would be use available space. In the vista manager it says that the 7.49 GB is unallocated. I have the latest version of ubuntu on the live disc. how do i put it on my computer using the 7.49 GB without losing any of my other data? tyvm

---

### Post by fjgaude on 2008-08-19
I'm not sure but if you use the liveCD to format the freespace to ext3 you will then be able to find the options to actually install Ubuntu onto that partition.

I tell you, these motherboards with fake-raid makes life somewhat complicated, with lots to learn.

Let us know how you are doing.

---

### Post by alexgamerz on 2008-08-24
as i said i have a DELL XPS M1730 with two hard drives. I cannot figure out what you mean, maybe because i am a noob to ubuntu. but it need a more thurough explination of this please, ty

---

### Post by fjgaude on 2008-08-25
The liveCD is what you use to install Ubuntu. Before you install use the program called **gparted**, Partition Editor, in the System/Administration drop-down menu to see your drives.

You may have to actually install dmraid while you are still in the liveCD so that you can mount the two drives.

I tell you, there's lots to learn to get to where you wish to go, and I'm sure you can get there. Most of us have little experience using dmraid and especially trying to have a spare partition with **ext3** Ubuntu on it with the rest being a raid1 **ntfs** partition.

---

