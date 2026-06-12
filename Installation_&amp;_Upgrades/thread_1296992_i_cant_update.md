---
title: "i cant update"
date: 2009-10-21
forum: Installation &amp; Upgrades
---

### Post by .Don on 2009-10-21
i cant update my linux. when i try to update it say that there is :/: m space left in my hdd. i insatalled the linux like 2 weeks ago and  *cant update it. can you help*

---

### Post by Mark Phelps on 2009-10-21
Did you install using Wubi, that is, inside an existing MS Windows install? If so, did you let it use the default space allocation? 

If so, it allocated only enough space to install itself and not enough to allow for growth and updates.

The Wubi guide (link below) has information about increasing the allocated space:

[https://wiki.ubuntu.com/WubiGuide%C2%A0]("https://wiki.ubuntu.com/WubiGuide%C2%A0")

---

### Post by stlsaint on 2009-10-21
also if you did not due wubi, please explain in detail the steps you took to install ubuntu. Last i remember ubiquity has a issue with allocating space for root and will only give about 2.5gb for filesystem. This may have been what happened to you but im not sure so i wont go into explainging, just please post how you installed ubuntu.

---

### Post by .Don on 2009-10-21
i didn't used wubi and i cant remember exsacly how did i installed the linux. i remember that it took about 1h to install it. :-x

---

### Post by stlsaint on 2009-10-21
please run this cmd in terminal: 

```
sudo fdisk -l
```

and post results here

---

### Post by .Don on 2009-10-21
this is in finish sorry D:

Levy /dev/sda: 81.9 Gt, 81964302336 tavua
255 päätä, 63 sektoria/ura, 9964 sylinteriä
Yksiköt = 16065 * 512 = 8225280 -tavuiset sylinterit
Levyn tunniste: 0xcdb6cdb6

    Laite Käynn     Alku          Loppu    Lohkot   Id  Järjestelmä
/dev/sda1   *           1         655     5261256   83  Linux
/dev/sda2             656        9964    74774542+   f  W95 Laaj (LBA)
/dev/sda5            2492        6227    30009388+   7  HPFS/NTFS
/dev/sda6            6228        9638    27398826    7  HPFS/NTFS
/dev/sda7             656        2408    14080909+  83  Linux
/dev/sda8            2409        2491      666666   82  Linux-sivutus / Solaris
/dev/sda9            9639        9942     2441848+  83  Linux
/dev/sda10           9943        9964      176683+  82  Linux-sivutus / Solaris

---

### Post by stlsaint on 2009-10-21
ok well it seems that you 3 instances of ubuntu on 3 partitions.

to clarify please post the entire text of this cmd:

[code]gksudo gedit /boot/grub/menu.lst[/code[

this will bring up a file that you can copy and paste the contents of here.

---

### Post by .Don on 2009-10-21
it says the device doesn't have any more space and something else

---

### Post by .Don on 2009-10-21
also i cant delete stuff = hdd is filling up. it said: Failed to delete the item from the trash

---

### Post by snowpine on 2009-10-21
Hi .Don, first back up everything important to an external drive. Then, you need to reboot using an Ubuntu Live CD. From the Live CD, run the gparted Partition Editor and resize the partition that's full. Good luck!

---

### Post by stlsaint on 2009-10-21
you shouldnt need anymore space to post the contents of your menu.lst
or run this in terminal :

```
cat /boot/grub/menu.lst
```

and copy and paste the output of it here...

---

### Post by slakkie on 2009-10-21
> **stlsaint said:**
> ok well it seems that you 3 instances of ubuntu on 3 partitions.

to clarify please post the entire text of this cmd:

```
gksudo gedit /boot/grub/menu.lst[/code[

this will bring up a file that you can copy and paste the contents of here.

Simply running 
[code]
cat /boot/grub/menu.lst

```

will show the complete file, without having to open something with read/write access as root. 

Could you please run the output of:

```

df -kh

```

Also, have a look at the following thread for some pointers: [http://ubuntuforums.org/showthread.php?t=1238309](http://ubuntuforums.org/showthread.php?t=1238309)

---

### Post by stlsaint on 2009-10-21
> **slakkie said:**
> Simply running 
```

cat /boot/grub/menu.lst

```

will show the complete file, without having to open something with read/write access as root. 

Could you please run the output of:

```

df -kh

```

Also, have a look at the following thread for some pointers: [http://ubuntuforums.org/showthread.php?t=1238309](http://ubuntuforums.org/showthread.php?t=1238309)


yep yep...hence the comment right above yours! :)

---

### Post by slakkie on 2009-10-21
> **stlsaint said:**
> yep yep...hence the comment right above yours! :)

You're doing the exact same thing here: [http://ubuntuforums.org/showpost.php?p=8140075&postcount=5](http://ubuntuforums.org/showpost.php?p=8140075&postcount=5)

Don't do it, use cat or less for these things. Don't open editors just to view the contents of a file as root. If you need to look at a file which is owned by root, sudo cat, but opening an editor just to view files.. Open it as a regular user so no changes can be committed by the users.

---

