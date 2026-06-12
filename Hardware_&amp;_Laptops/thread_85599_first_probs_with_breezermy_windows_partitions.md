---
title: "first probs with breezer:my windows partitions"
date: 2005-11-03
forum: Hardware &amp; Laptops
---

### Post by maltje on 2005-11-03
Hi,

After installing breezy on my amilo I have now on my screen
hda1,hda5 and hd6
I have no rights to see the contents of hda1
and in hda5 and 6 I only can read,not wright.
These are windows partition and I haven't mount anything yet.
How can I work with them???

How can I see the contents of my harddrive,so there where every hda is shown.

I have changed something in my /etc/fstab file,no it iis ok for hda5 and hda6,hda1 won't work because its nfts file.
Is it necesary that start the computer back after changing something in fstab,or is there a command to apply the changes???

---

### Post by frodon on 2005-11-03
When you say "windows partition" do you mean NTFS file system, if yes i have to tell you that NTFS is read only under linux, there's some projects to perform write on NTFS but it's slow and sometimes dangerous for your data.
That's why a lot of users use other file systems like : FAT32, ext3, reiserfs, ...

To mount the partitions as you specified it in fstab : ```
sudo mount -a
```

---

### Post by maltje on 2005-11-03
thnx
yes indeed,it is a ntfs partition.
But that is not necasary to use this partition.
The 2 others are ok now.
If I clear the line of ntfs partition in the fstab_file,is he then gone from my desktop???
I like to get rid of the hda1 on my dektop

---

### Post by frodon on 2005-11-03
yes, if you don't want your ntfs partition anymore you could clear the fstab line.
By the way, when you say "then gone from my desktop", do you mean that you would like to remove the icon of the drive on your desktop ?
If yes, go to Applications > System Tools > Configuration Editor, when Gconf is opened go to apps>nautilus>desktop and then untick the volumes_visible checkbox.

---

### Post by maltje on 2005-11-14
New problem here.
I put in the usbstick and I see it in nautilus.
then I put some mp3's on it but when I put out the usbstick and want to play the mp3's ,there is nothing on it!!!!!!!!!!!
I put back in the usk stick and then I see that he is empty???????
How is that possible?
How can I format my usbstick?

---

### Post by frodon on 2005-11-14
when you want to format a usb stick in nautilus don't forget to do a Ctr + H in order to see hidden files because the trash on your usb stick is a hidden file.
So maybe your usb stick was full when you wrote on it and that's why you didn't wrote anything on it.

---

### Post by maltje on 2005-11-14
The problem is:
In nautilus I do copy,past with some files but when I take the usb out,and put it back in,there are NO files on the usbstick!!!!!!!!!!!!!!!!!


With what commando can I format the usb stick?

---

### Post by frodon on 2005-11-14
That's what i said, if the trash (hidden) of your usb stick is full you will write nothing on it. You need to delete the trash of your usb stick before writing on it.
If deleting the trash and after that writing on your usb stick doesn't work, it's not a formating problem.

---

### Post by maltje on 2005-11-14
I deleted always de trashfolder also.
I paste the files an on that moment I see them in the map usb....
But when I get the usbstick out on the usbstick screen says NO FILES!!!!!!!!!!!
very strange,never had that problem in hoary,but now in breezy.......
:(

---

### Post by frodon on 2005-11-15
It's really weird.
Do you get error messages if you try to copy on it using command lines in a terminal (your usb stick should be in /media/usb).
I will make some tests this evening to see if i have the same behaviour on my computer.
Sorry, no more ideas for the moment.

EDIT : similar thread link : [http://ubuntuforums.org/showthread.php?t=89735&highlight=usb+stick](http://ubuntuforums.org/showthread.php?t=89735&highlight=usb+stick)

---

### Post by maltje on 2005-11-15
I don't get any errors

---

### Post by frodon on 2005-11-16
Follow the link i gave you in the previous post, the problem is the same, i think the problem could come from the usb disk partition, if it's NTFS it could be the problem.

---

### Post by maltje on 2005-11-16
No solution in the link you gave me.
:(

---

### Post by frodon on 2005-11-16
Yes but i'm sure it will be the case soon ;), just follow it.
I can't help you more because i never met this kind of problem and did some tests yesterday all with success.

Hope you will solve your issue soon and sorry to not help you more.

---

### Post by ispiked on 2005-11-16
[QUOTE=maltje]The problem is:
In nautilus I do copy,past with some files but when I take the usb out,and put it back in,there are NO files on the usbstick!!!!!!!!!!!!!!!!!


With what commando can I format the usb stick?[/QUOTE]I'm pretty sure that you're not unmounting the USB stick correctly which is causing all the data you put on it not to be written. Once you put data on it and you're ready to take it out, right click on the icon on the desktop and click "Unmount". This should ensure that the data is written to the disk.

For the problem with you not being able to access your Windows partitions, you just need to allow a regular user to access them. I don't know why Ubuntu doesn't do this by default, because it's pretty annoying for a new user to see their Windows partitions there and not be able to access them. Anyway, edit the options for when you mount the partition to include users. This will allow everyone to access the partition. fstab should look something like this, where the drive is *your* Windows drive, or course:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>proc            /proc           proc    defaults        0       0
/dev/sda6       /               reiserfs notail          0       1
/dev/sda5       /home           reiserfs defaults        0       2
/dev/sda1       /media/sda1     vfat    defaults        0       0
**/dev/sda2       /media/sda2     ntfs    users,ro   0       0**
/dev/sda7       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

```

---

### Post by maltje on 2005-11-17
[QUOTE=ispiked]I'm pretty sure that you're not unmounting the USB stick correctly which is causing all the data you put on it not to be written. Once you put data on it and you're ready to take it out, right click on the icon on the desktop and click "Unmount". This should ensure that the data is written to the disk.

Thnx very much,unmounting does the trick.
i read somewhere it it has something to do with the kernel that isn't using some command (subfs)

---

### Post by maltje on 2005-11-18
again a problem
How long does it take to unmount??
I unmount the stick and wait 5 sec.then I pull out the device but then I gor an error,can't unmount the device!!!

---

