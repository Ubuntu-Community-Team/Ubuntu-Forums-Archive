---
title: "Partitioning going wrong..."
date: 2008-10-05
forum: General Help
---

### Post by vazrui on 2008-10-05
Hello, 
I'm new to ubuntu, just installed from live cd, but it seems i've screwed up with the partitioning, 'cause the partition where I had old files from windows xp just disappeared... That's not how it was supposed to go...

Is there a way to recover it? Still personal files missing and as I explore the disk, I can only find the new directories created by ubuntu.

Thanks for any help!

---

### Post by ghantoos on 2008-10-05
Hi,

What partitoning do you have now?

can you paste here the output of this command in a terminal?
```

sudo fdisk -l

```Cheers,

---

### Post by vazrui on 2008-10-06
Hi ghantoos
Thank you for your help. I don't know much about technical things, but I'm loving to use ubuntu so far, just out of the box (except for this one thing about my old files...). 

When I type sudo fdisk -l in a terminal this is what I get:

Disk /dev/hdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd39ad39a

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       14240   114382768+  83  Linux
/dev/hdb2           14241       14593     2835472+   5  Extended
/dev/hdb5           14241       14593     2835441   82  Linux swap / Solaris

Is there anything I can do to recover some files of the disk?
Thanks!

---

### Post by Titan8990 on 2008-10-06
Looks like your Windows install and all the files on it are gone.

---

### Post by ghantoos on 2008-10-06
First of all, don't write ANYTHING on your disk so you don't completely overwrite your data.

Then, there are multiple ways to recover data from a lost partition, even after a format was done. I did this many times already (for friends mostly, I don't always format my data partitions).

You should get an external hard disk to put the recovered data on it. Again, don't put the recovered data straight on your drive, you may erase information.

Try using *foremost*. It is able to recover jpg, gif, zip doc, rar, mgp and wmv. Open a terminal, and type:
```

sudo apt-get install foremost
sudo foremost -t all -i /dev/hdb -o /media/USBBLA
(you can try it with /dev/hdb1 and /dev/hdb3)

```This will dump all the recovered file on your external hard drive. Of course all the recovered files will be in the same folder. So you'll have to take some time to check it all out. 

You can also try out *testdisk*. It was very useful to a friend who had his hardrive partitions completely lost. Here recovered a lot of data! Here are some links that can be useful. They explain how to use *testdisk*[B][I]:
[/I][/B]1- [http://www.psychocats.net/ubuntucat/recovering-windows-files-with-a-ubuntu-cd-iii-deleted-files/](http://www.psychocats.net/ubuntucat/recovering-windows-files-with-a-ubuntu-cd-iii-deleted-files/)
2- [http://www.linux.com/articles/56588](http://www.linux.com/articles/56588)

Another application that was useful to me after I had formated my memory card from fat32 to ext3: *recoverjpeg*. I even recored pictures a had deleted many month before. But it only recovers pictures.

Hope this gives you hope, and specially a way to recover your data.

One last link, [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

Goodluck,

Cheers,

---

### Post by vazrui on 2008-10-06
Thanks a lot for the help, ghantoos! I'm going to follow your suggestions and cross my fingers...

---

### Post by vazrui on 2008-10-12
Just finished the process, I've got most of the important stuff back!
Thanks again for the helpful hand, ghantoos!

After using ubuntu for a week, now, I wonder why in the hell I didn't do it before...

---

### Post by ghantoos on 2008-10-13
Thanks for the follow up. I'm glad to read that you got most of your data back, and that you enjoying Ubuntu!

Cheers,

---

