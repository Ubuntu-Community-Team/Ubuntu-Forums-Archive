---
title: "Hard Drive can't be recognized on any OS anymore"
date: 2008-11-26
forum: Hardware
---

### Post by Progressive on 2008-11-26
I have a backup hard drive that I converted to an external USB hard drive, and it had been working fine until recently.

I was helping a friend install Kubuntu and he needed to back up files and had no backup device. Thus, I brought my external hard drive. I couldn't get the live CD to recognize the drive.

I was able to back up his documents on to a flash drive, and he told me that all of his music was on his ipod, and then I informed him that Amarok could extract all these, so we went ahead and decided to erase windows since we no longer needed any of the data.

I had left the external plugged in and was in process of installing and I believe that it tried to install Kubuntu to the external drive. I was surprised since I thought it wasn't being recognized and cancelled the installation as quickly as I heard the drive start spinning.

Now, however, I am unable to get the drive recognized on my own computer or on the windows computer I am using now, since I am home for thanksgiving.

It isn't showing up in the windows device manager, and I do have ext2ifs for Windows installed. What could be the problem? The drive turns on fine and can hear it spinning with no abnormal sounds.

Is it possible that the installation overwrote the drive's master boot record or some such thing? If it did, wouldn't the drive still show up in the device manager?

Any help would be appreciated

---

### Post by taurus on 2008-11-26
Boot up Ubuntu.  Then, plug in that external harddrive and post the output of this command from a terminal.

```
sudo fdisk -l
```

---

### Post by Progressive on 2008-11-27
```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         993     7976241   83  Linux
/dev/sda2             994        1044      409657+   5  Extended
/dev/sda5             994        1044      409626   82  Linux swap / Solaris

```

---

### Post by Hellaxe on 2008-11-27
That's very strange.
It should be listed in the > fdisk -l
I recommend you to check it with some of the hardware tool (hiren's or whatever).
Try it in other computer.
If the Hdd is ok we'll try to do something more.

---

