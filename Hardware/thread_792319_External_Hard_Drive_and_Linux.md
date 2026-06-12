---
title: "External Hard Drive and Linux"
date: 2008-05-12
forum: Hardware
---

### Post by papajohn37 on 2008-05-12
Alright so I for some reason thought that it would be neat to put linux on my external hard drive so I could boot up from it when I was away from home. but the drivers for my wireless card did not work. So what I am trying to do now is fix my external hard drive to be able to use it in windows but I partioned the entire 120 GB disk for linux. Is there a way to reformat the drive and use it agian?

---

### Post by unutbu on 2008-05-12
Boot the LiveCD. Run 

```
sudo gparted
```

There you can delete the linux ext3 partition and create a new FAT32 partition that Windows can read.

---

### Post by papajohn37 on 2008-05-12
ok i tried that but when i click forward it says no root file. if I change the partitions and cancel out of the install will it work?

---

### Post by unutbu on 2008-05-12
You can make changes in gparted with no consequence until you click "Apply". Only then does gparted set about doing the (potentially) dangerous things it does. By the way, be sure you are operating on your external drive. Deleting and reformating your primary drive would be bad.

What do you mean "when i click forward it says no root file"? Are you in gparted? What is there to click forward?

---

### Post by papajohn37 on 2008-05-12
no i was using the live cd and reinstallation to fix partitions is gparted in ubuntu? If I use ubuntu i do not have internet on the drive because my wireless driver is not working on it for some reason. so if gparted is not already installed i wont be able to connect to the net
unless you can fix that problem as well

---

### Post by papajohn37 on 2008-05-12
my fault i am using ubuntu

---

### Post by unutbu on 2008-05-12
Wireless problems are not always easy to solve. It depends on how patient you are, and how badly you want to explore ubuntu. If you want to, there are probably people here who will try to help you get your wireless working, but don't expect it to be a snap.

Now if you just want to reformat the external drive, boot the LiveCD. You'll come to a menu where it asks if you want to "boot and install", or something to that effect. I think that's the first option. Select it. You just want to boot, but not install. You should eventually be dumped into a screen with a orange background.  Here you are already running Ubuntu from RAM, not your hard drives.

Now go to the upper left corner. Select Applications>Accessories>Terminal.

Type in the terminal

```
sudo gparted
```

A window should pop up showing your partitions. There is a menu tab in the upper right which should say something like /dev/sda. Click on it and select your external hard drive which might be called something like /dev/sdb. Make sure you get this right or else you might erase the wrong drive. Bad. Bad. Bad.

Once you select the right drive, click on a partition. The Delete button should appear. Click it. Repeat until all partitions have been removed. Then click New to create a new partition. Choose the type of filesystem you want, probably FAT32.

Then click Apply.

---

