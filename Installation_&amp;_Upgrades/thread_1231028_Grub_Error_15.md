---
title: "Grub: Error 15"
date: 2009-08-04
forum: Installation &amp; Upgrades
---

### Post by 1/0 on 2009-08-04
I've managed to bork grub. I got a new hard drive with 9.10 but decided to downgrade to 9.04. At the same time I installed Windows on it in order to use a CAD program and went after that for a full reinstall of Ubuntu.

All I get at boot is ''Error 15 File not found''.

I've got three disks: sda, sdb and sdc. Sda contains the new ubuntu installation (9.10), sdb has an old ubuntu version I haven't deleted yet, sdc has windows on it. On sda, sda1 is swap, sda2 is /boot, sda3 is root, sda4 is extended hence nothing, sda5 is empty and sda6 is home.

I've tried all sorts of ways to deal with this, including reinstallation. The latest attempt was to chroot from the live startup disk:

```

root@ubuntu:/home/ubuntu# mkdir /media/root
root@ubuntu:/home/ubuntu# mount /dev/sda3 /media/root/
root@ubuntu:/home/ubuntu# mount /dev/sda2 /media/root/boot/
root@ubuntu:/home/ubuntu# mount -o bind /proc/ /media/root/proc/
root@ubuntu:/home/ubuntu# mount -o bind /sys/ /media/root/sys/
root@ubuntu:/home/ubuntu# mount -o bind /dev/ /media/root/dev/
root@ubuntu:/home/ubuntu# mount -o bind /dev/pts /media/root/dev/pts
root@ubuntu:/home/ubuntu# chroot /media/root/ /bin/bash
```


```
# grub-install /dev/sda2
Searching for GRUB installation directory ... found: /boot/grub
Installing GRUB to /dev/sda2 as (hd0,1)...
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc
(hd3)	/dev/sdd
(hd4)	/dev/sde
```

In grub:

```
grub> find /boot/grub/stage1
```

Nothing found so I tried:

```
grub> find /grub/stage1
 (hd0,1)
 (hd1,1)
```

I made a sym link in /boot with an extra level, i.e. /boot/boot/grub. Without it I got the following:

```
grub> root (hd0,1)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,1)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.
```

With the sym link:

```
grub> root (hd0,1)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,1)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.
```

I moved menu.lst and updated a new one:

```
root@ubuntu:/# update-grub 
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... 

Could not find /boot/grub/menu.lst file. Would you like /boot/grub/menu.lst generated for you? (y/N) y
Searching for splash image ... none found, skipping ...
Found kernel: /vmlinuz-2.6.28-11-generic
Found kernel: /memtest86+.bin
Updating /boot/grub/menu.lst ... done
```

Still I got error 15...

I even tried to erase the mbr and start over:

```
# dd if=/dev/null of=/dev/sda bs=446 count=1
```

The only thing that will work now is Windows. I haven't used windows in 9 years. This is freaking me out. It's like a prison. PLEASE HELP!!

---

### Post by zvacet on 2009-08-05
I find [this]("http://members.iinet.net.au/~herman546/p15.html#15") and hope it will be helpful to you.

---

### Post by 1/0 on 2009-08-06
> **zvacet said:**
> I find [this]("http://members.iinet.net.au/~herman546/p15.html#15") and hope it will be helpful to you.

Thanks for the reply. I managed to solve it yesterday night. It turned out BIOS put the PATA drive as master. Grub was on sda but the first drive for BIOS was sdc so I switched that and it worked. 

I thought of BIOS but it feels like going back to norton commander or something. Something inside screams "GET ME OUTTA HERE!" everytime I enter Bios so I avoid it.

---

### Post by oldfred on 2009-08-06
It looks like you have a separate /boot partition, but the directory structure does not have /boot just /grub - from your
find /grub/stage1
this is where grub finds stage1 and there will be no symlink when you are booting, so this is where the MBR needs to look to continue booting. Then do you also have a /boot in your root? Also are all the normal grub files in the same place?
Error 15 is saying it cannot find everything, so something is in the wrong directory.

---

### Post by 4Foot on 2009-08-09
This post from Dorian ( Sorry I don't have the link anymore ) saved me from pulling out all of my hair. I hope you find it useful next time. 4Foot


 April 22nd, 2008	   #10
D0R1AN
First Cup of Ubuntu

 
Join Date: Mar 2008
Beans: 4
Re: Grub Error 15 File Not Found
Quote:
Originally Posted by Ralphie  
I have found an easier way to do this.


(from budman)

One of these commands will give you an answer like
Code:
root (hd0.0)
Now press Esc.
Select the first boot option and press "e"

Press "e" again on the root option
Change the hd(X,X) to whatever you got above. for me it was hd (0,0).
Press Enter.
Now press "b"

Ubuntu should load up.

Now that you are in, you need to change this for good.
Open a terminal and enter
Code:
sudo gedit /boot/grub/menu.lst
or, depending on your setup
Code:
sudo gedit /grub/menu.lst
Scroll down towards the bottom of the file, and you will find the same "root (hdX,X)" change it appropriately, and you can save!

Also while editing, you can go ahead and change all of the root options for the different ubuntu modes, because they are all most likely wrong.

---

### Post by 1/0 on 2009-08-11
Well, Ubuntu boots fine as long as I have that sym-link present. If I remove it, I get error 15 and I can't access grub at all. Hence, it is impossible to change root by pressing *e*. 

When I boot via the Live CD / contains the folder *boot*, and the folder is empty. 

As I wrote before, I've tried to reinstall grub on */dev/sda*, i.e. *(hd0)* but with the same result. 

It's really weired that grub is not properly started. It's as if grub is installed on */dev/sda* but it can't access the boot partition. I just don't get why the sym-link helps if it is not used when grub boots... maybe it's that I created a folder called *boot* in */boot* with a sym-link pointing to the folder *grub*?

---

