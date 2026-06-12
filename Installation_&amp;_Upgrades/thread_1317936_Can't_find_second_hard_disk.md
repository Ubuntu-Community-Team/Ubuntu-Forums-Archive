---
title: "Can't find second hard disk"
date: 2009-11-07
forum: Installation &amp; Upgrades
---

### Post by patatje on 2009-11-07
I installed the new ubuntu alongside Windows XP. But now in ubuntu I can't find my second hard disk and in Windows it works just fine. Do I have to mount it?

I'm a total newbie to linux. Please help :D

---

### Post by Rambar on 2009-11-07
Go to the *Places *tab, and a list of all hard drives and connected devices will appear. If it's an internal HD, you will have to mount it (just double click it and you'll be asked your user password). Then you will be able to access it.

 As a side note, all mounted devices are accessed via the /media/ folder in the filesystem once they are mounted.

---

### Post by Lateralis on 2009-11-07
If you want the devices to be automounted at start up you will need to edit the file /etc/fstab.  If you are new to Linux you probably don't want to do this yourself.  However, there is a programme that will automatically configure fstab for you.  Fire up a terminal (Applications -> Accessories -> Terminal) and type the following into the command line:

```
sudo apt-get install ntfs-config
```

You will be asked to type your password in your passward after typing that command. 

Once it has been downloaded and installed, just type 

```
sudo ntfs-config
```

into the command line.  Make sure that the Windows partition you want automounted isn't mounted when you do this.  You'll be presented with a dialogue box where you can select which partitions you want automounted at start up.  Select your Windows XP partition, click apply and make sure that "write support for interal devices" is checked.  Click OK and then everything should be sorted!  The partition will be automounted at start up. =)

---

