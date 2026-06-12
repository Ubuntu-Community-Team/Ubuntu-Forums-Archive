---
title: "Mounting Error"
date: 2005-05-04
forum: Hardware &amp; Laptops
---

### Post by radu on 2005-05-04
i recently installed  ubuntu 5.04 on the win xp partiton .. i now have 1 ext3 partition and 2 ntfs partitions . the problem is : it gives me this error while i give the mount command :[COLOR=Green]Could not mount device. 
 The reported error was: 
 mount: can't find /dev/hda5 in /etc/fstab or /etc/mtab[/COLOR]
ok...so i go to the fstab file to edit it ...now it tells me that i don't have the permission , so i try to change the file permisions , but i can't because it gives me another error  while tring to change group or others , permission (i think that with root it works -but another "but" -when i login with root and password , the login tells me that it's not permited to login as boot  :mad: )
what can i do to acces the ntfs partitions data? :-|  :-?

---

### Post by Xerampelinae on 2005-05-04
Normal users can't change system related stuff.  You have to prefix your commands with "sudo" to elevate your permissions to root.

```

sudo gedit /etc/fstab

```

To mount an ntfs partition, you could do a manual way of entering this command

```

mkdir /mnt/win
mount -t ntfs /dev/hda5 /mnt/win

```

Or edit your /etc/fstab and add this line

```

/dev/hda5       /mnt/win        ntfs    ro      0 0

```

This is all assuming, of course, that /dev/hda5 is your windows partition.  You said you have 1 ext3 and 2 ntfs, so I'm not sure how it would get up to hda5, but.... *shrug*

---

### Post by radu on 2005-05-04
i can't edit the file .
about the drives :
1 partition of 1 kb ( i can't explain how it apeared)-hda2
the linux partition-hda1
swap partition -hda7
and the two ntfs drives : hda5 and hda6
i wrote the su root and now it's mounted but it gives another error :
Could not enter folder /mnt/win.

ps . no , it isn't the windows operating sistem partition , it's a ntfs partition , left because i installed ubuntu on the win . partition and left the data on the other two partitions

---

### Post by Nylira on 2005-05-05
I think I had a similar problem with my NTFS mounts. Try mounting with the option umask=0222. In fstab I have the following line for my scsi disk with my windows partion.

/dev/sda1       /mnt/win     ntfs    umask=0222      0       0

This works like a charm for me. 
So try opening a root terminal (Applications - System Tools - Root Terminal) and enter:

mount -t ntfs -o umask=0222 /dev/hda5 /mnt/win

If that works you should be able to add the line as noted earlier to fstab using /dev/hda5. From that same root terminal you should be able to edit /etc/fstab. Try nano or if you installed it joe (one of my favorite) to edit the file.

---

### Post by radu on 2005-05-06
[QUOTE=Nylira]I think I had a similar problem with my NTFS mounts. Try mounting with the option umask=0222. In fstab I have the following line for my scsi disk with my windows partion.

/dev/sda1       /mnt/win     ntfs    umask=0222      0       0

This works like a charm for me. 
So try opening a root terminal (Applications - System Tools - Root Terminal) and enter:

mount -t ntfs -o umask=0222 /dev/hda5 /mnt/win

If that works you should be able to add the line as noted earlier to fstab using /dev/hda5. From that same root terminal you should be able to edit /etc/fstab. Try nano or if you installed it joe (one of my favorite) to edit the file.[/QUOTE]
 you mean the console ....
been there , done that
the permission is still not changing and it's giving me the same error and headakes .
i think i will put again win xp , i will copy the hole ntfs drive on a dvd and after that i'll put ubuntu on the hole hard-disk

---

