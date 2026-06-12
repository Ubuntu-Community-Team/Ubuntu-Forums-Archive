---
title: "Help Restoring Grub after installing WinXP."
date: 2009-05-20
forum: Installation &amp; Upgrades
---

### Post by translucent juicebox on 2009-05-20
I can't figure out how to do it. :(  I tried the following from the xubuntu livecd...

sudo grub
find /boot/grub/stage1
root (hd0,0)
setup (hd0,0)
quit

but it didn't work.  It seemed to go smooth and fine, but when I restarted the computer it still automatically boots straight into windows.  What other ways are there to restore grub?

---

### Post by labinnsw on 2009-05-20
1. Reboot with Alternative CD
2. Select Rescue a broken System line and press enter.
3. Select your language and Keyboard. (You could auto detect this but it takes longer)
4. Let the computer detect the network. (It is OK to use the default host name Ubuntu.
5. Note carefully which disk and which partition your Ubuntu installation is on.
6. Select it and press enter
7. At the command prompt type mount -a
8. At the next prompt type df
9. Look for the single character /, it should correspond with something like /dev/hda2
10. At the prompt type grub-install /dev/hda omitting the 2 and replacing the rest with your partition.
11. When the process is finished, type exit at the next prompt.
12. Eject the CD and reboot.

---

### Post by teonghan on 2009-05-20
I faced this problem before, back then I was using Hardy and reinstall my XP. I went to [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/) and download the bootable cd image of "super grub disk" and restore my grub. There is an auto run-in-windows version but I haven't try that.

---

### Post by presence1960 on 2009-05-20
> **translucent juicebox said:**
> I can't figure out how to do it. :(  I tried the following from the xubuntu livecd...

sudo grub
find /boot/grub/stage1
root (hd0,0)
setup (hd0,0)
quit

but it didn't work.  It seemed to go smooth and fine, but when I restarted the computer it still automatically boots straight into windows.  What other ways are there to restore grub?

Assuming windows is on the first partition of your first hard disk try putting GRUB on your MBR with setup (hd0). all other steps above remain the same.

P.S. 

> 1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>

4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,1)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or 
   whatever your hard disk + partition # is, to install GRUB to a 
   partition.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.

---

### Post by translucent juicebox on 2009-05-20
labinnsw:  after typing grub-install /dev/sda1 (which is the partition with xubuntu on it), the command line says...

Probing devices to guess BIOS drives. This may take a long time.
Could not find device for /boot: Not found or not a block device.

presence1960:  is there a difference between hd0 and hd0,0?  Is this proceedure different if XP is installed on the second partition, and xubuntu on the first?

---

### Post by devosion on 2009-05-20
> **translucent juicebox said:**
> labinnsw:  after typing grub-install /dev/sda1 (which is the partition with xubuntu on it), the command line says...

Probing devices to guess BIOS drives. This may take a long time.
Could not find device for /boot: Not found or not a block device.

presence1960:  is there a difference between hd0 and hd0,0?  Is this proceedure different if XP is installed on the second partition, and xubuntu on the first?

From what I understand the difference is that passing hd0 installs grub to the drive, while passing hd0,0 will only install it to that partition.

---

### Post by translucent juicebox on 2009-05-21
I retried what I did in the first post but with hd0 instead of hd0,0 and it worked somewhat.  I can boot up with grub now, but in the grub menu, my only options are various versions of Xubuntu 8.10, how do I add Windows XP to the grub list?

---

### Post by labinnsw on 2009-05-21
> **translucent juicebox said:**
> labinnsw:  after typing grub-install /dev/sda1 (which is the partition with xubuntu on it), the command line says...

Probing devices to guess BIOS drives. This may take a long time.
Could not find device for /boot: Not found or not a block device.

presence1960:  is there a difference between hd0 and hd0,0?  Is this proceedure different if XP is installed on the second partition, and xubuntu on the first?

Leave off the 1

Try:

```
grub-install /dev/sda 
```

---

### Post by labinnsw on 2009-05-21
> **translucent juicebox said:**
> I retried what I did in the first post but with hd0 instead of hd0,0 and it worked somewhat.  I can boot up with grub now, but in the grub menu, my only options are various versions of Xubuntu 8.10, how do I add Windows XP to the grub list?

You will need to edit your menu list.
Open a terminal (Applications >> Accessories >> Terminal)
Type:
```
sudo gedit /boot/grub/menu.lst
```
Supply your administration password
Add the following information at the bottom changing (hd0,0) to match the location of your Windows partition:

```
title		Other operating systems:
root

title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
#map		(hd0) (hd1)
#map		(hd1) (hd0)
chainloader	+1
```

Save and close the file.

---

### Post by presence1960 on 2009-05-21
> **translucent juicebox said:**
> labinnsw:  after typing grub-install /dev/sda1 (which is the partition with xubuntu on it), the command line says...

Probing devices to guess BIOS drives. This may take a long time.
Could not find device for /boot: Not found or not a block device.

presence1960:  is there a difference between hd0 and hd0,0?  Is this proceedure different if XP is installed on the second partition, and xubuntu on the first?

well your GRUB menu is up, that is good. why don't you run this command in terminal>  sudo fdisk -l and post the output here. This way we know for sure which partition windows is on and you can edit your windows entry correctly in menu.lst

Run that command I asked for and lets get a look at your hard drive(s) and their partitions.

---

### Post by translucent juicebox on 2009-05-21
here are the results of fdisk -l


Disposit. Inicio    Comienzo      Fin     Bloques   Id  Sistema
/dev/sda1               1        2454    18547011   83  Linux
/dev/sda2   *        2455        4950    18869760    7  HPFS/NTFS
/dev/sda3            4951        5168     1646662+   5  Extendida
/dev/sda5            4951        5168     1646631   82  Linux swap / Solaris

Sorry, I don't know how to use the code tags because none of the buttons in submit reply form work for me, and using spaces didn't work :(.  But sda1 is xubuntu, sda2 is windows, sda3 is the xubuntu extension partition, and sda5 is xubuntu's swap partition.

Are (hd0, hd1) , (hd1, hd0)  the correct map locations for the windows partition(sda2)?  I still don't really understand what (hdX) refers to.

OK, I just restarted and tried booting up XP, with the (hd0, hd1) , (hd1, hd0) as the map location, and I now know that those are not the right locations as grub booted from /dev/sda1 (Xubuntu) when I selected XP.

---

### Post by labinnsw on 2009-05-21
So this is what you will add: (Just copy and paste)

```
title		Other operating systems:
root

title		Microsoft Windows XP Professional
root		(hd0,1)
savedefault
#map		(hd0) (hd1)
#map		(hd1) (hd0)
chainloader	+1
```

Your Windows partition is on sda2

Check your device map

```
sudo gedit /boot/grub/device.map
```

See if it is like this

```
(hd1)	/dev/hdf
(hd0)	/dev/sda
```

or

```
(hd0)	/dev/sda
(hd1)	/dev/hdf
```

In hdX you are meant to replace the X with a number.

If you only have one hdd, then you should not have a hd1
You have a SATA hdd. I have not figured out yet how to dual boot Windows on SATA drives. (Other Linux works. I tried Mint and Kubuntu) What works to the IDE does not seem to be working on SATA.

There are some forum posts which suggests installing GRUB on some kind of external media, but I have not tried this yet.

---

### Post by translucent juicebox on 2009-05-21
Thanks, Changing root (hd0,0) to (hd0,1) worked like a charm.  I finally got XP up and running alongside Xubuntu. :D

---

### Post by labinnsw on 2009-05-22
I am happy for you. It was my pleasure to be able to help. Thanks presence1960 for your contribution as well.

---

### Post by presence1960 on 2009-05-22
> **labinnsw said:**
> I am happy for you. It was my pleasure to be able to help. Thanks presence1960 for your contribution as well.

We are all here to help each other. :p

---

### Post by labinnsw on 2009-05-22
> **presence1960 said:**
> We are all here to help each other. :p

And this is one instance where in giving help I also helped myself.

It did not dawn on me that my own problem might not be SATA related until this worked. Then I realized that the problem I am having dual booting might be related to the size of the Linux partition I am using. I backed up the system, deleted the Linux partitions and re-installed in a smaller space. Abra-ca-da-bra, it works! I will provide more information on that once I have restored my system.

---

### Post by labinnsw on 2009-05-22
The attached is the error I was getting, apparently because Windows was uncomfortable with the size of the Ubuntu partition. I have reduced the Ubuntu partition to 70GB and now Windows is happy.

[ATTACH]114665[/ATTACH]

---

### Post by presence1960 on 2009-05-22
> **labinnsw said:**
> The attached is the error I was getting, apparently because Windows was uncomfortable with the size of the Ubuntu partition. I have reduced the Ubuntu partition to 70GB and now Windows is happy.

[ATTACH]114665[/ATTACH]
That's just like windows isn't it?

---

