---
title: "ubuntu 10.10 64 bit and SATA Raid setup"
date: 2010-12-02
forum: Hardware
---

### Post by bryan.smith.355 on 2010-12-02
Hi all,
 
I have a gigabyte motherboard that I setup with a RAID 1 mirror. I believe this is called a fake RAID (even though its done on the mobo)? please correct me if I am wrong.
 
I have windows 7 installed on it and I also installed ubuntu 10.10 (So no, I cannot use soft RAID). However, I read that older versions of ubuntu need something installed or the metadata could get corrupted and screw up the entire array. Is this true for ubuntu 10.10? If it is true, could someone please point me in the right direction? It saw the array correctly on Ubuntu installation (after windows) and everything appears to be working. 
 
I still havent moved the data from my old desktop because after reading that I am nervous (although I have a backup). I apologize if this has been answered somewhere but I couldnt find it.
 
Also, if anyone could recommend a real SATA RAID controller (Is there such a thing?) that isnt too expensive that would be great. 
 
Thanks,
Bryan

---

### Post by coffee412 on 2010-12-02
> **bryan.smith.355 said:**
> Hi all,
 
I have a gigabyte motherboard that I setup with a RAID 1 mirror. I believe this is called a fake RAID (even though its done on the mobo)? please correct me if I am wrong.
 
I have windows 7 installed on it and I also installed ubuntu 10.10 (So no, I cannot use soft RAID). However, I read that older versions of ubuntu need something installed or the metadata could get corrupted and screw up the entire array. Is this true for ubuntu 10.10? If it is true, could someone please point me in the right direction? It saw the array correctly on Ubuntu installation (after windows) and everything appears to be working. 
 
I still havent moved the data from my old desktop because after reading that I am nervous (although I have a backup). I apologize if this has been answered somewhere but I couldnt find it.
 
Also, if anyone could recommend a real SATA RAID controller (Is there such a thing?) that isnt too expensive that would be great. 
 
Thanks,
Bryan

Im sorry but I do not know anything about the problems associated with ubuntu and raid corruption. I can say that I have been running software raid 5 with 4 320 gig disks for over 5 years and find it easier to work with - mdadm used.

But, They certainly do make Sata raid cards. depends on what features you want and all. The 3ware line of cards come highly recommended by linux users. However, Your gonna spend about 280 bucks on the card for anything with raid5 capabilities. Hardware raid is not cheap. Thats why I went software raid. Kinda glad I did.

As for the corruption issue I guess you can google it and do some research there. Why not stress test your raid before moving your backups? Run it and see if it corrupts for about a week. If no problems then call it good and transfer your data to it.

[http://www.newegg.com/Product/Product.aspx?Item=N82E16816116076](http://www.newegg.com/Product/Product.aspx?Item=N82E16816116076)

BTW -- > You will need to buy a breakout cable with this card. I didnt see one for internal connections either. But I didnt really look that hard.

:p

---

### Post by ronparent on 2010-12-03
Welcome to the forum.

You do have a 'fakeraid' setup. It is accessed using software called dmraid which emulates the manufactures drivers found in Windows for that purpose. The 10.10 installation disk comes with dmraid provided. A bug still seem to be blocking the ability of gparted to see the raid. You can verify that the raid1 is detected by booting to the live cd and first installing kparts for the session and then running gparted. A raid array will show with all the individual raid partitions. 

As long as gparted can see the raid you can install to the raid with good assurance that data will remain synchronized between the component raid disks. Post if you run into trouble.

---

### Post by ewa8949 on 2011-01-21
I don't know if anyone is following this thread still or not but I have had a lot of problems with my fakeraid setup. I am trying to do a dual win 7/ubuntu 10.10 setup and I have a 4 drive raid5 setup on an Intel ICH10R motherboard.  The drives have GPT partitions and were created in windows 7 with NTFS on them (I need dual OS support). Both the Windows and Linux OS are on a dedicated drive for booting and the array is for data storage only. 

Ubuntu only see's the first drive of the array.  If I kpartx -a -v /dev/mapper/ich_abababab_vol0 that drive it exposes the large partition and a smaller one at the end but gives GPT errors.  I can then mount the array and am seemingly ok. I seem to be able to read/write data to it and windows can see it.  However, after a few days the array metadata got corrupted and windows could no longer see it.  I rebuilt the array and have spent days copying data over to it after trying to restore from it. Before there was any data on it Ubuntu could see it fine and see all the partitions. However, once I started adding a bunch of data I ran into the same problems. After a couple days the metadata got corrupted and windows could not see the array. Ironically Ubuntu still could. 

Now I am scared to deal with mounting my fakeraid in Ubuntu 10.10 anymore.  Are things more stable with a raid card?  I still can't figure out why it always tells me I have partitions errors and that the NTFS signature is missing.

---

### Post by dpellegrini on 2011-03-05
I'm hoping that this thread is not dead, because I'm having RAID issues with ICH10R too.

One thing I noted as different in your case is that your volume begins with "ich_" whereas mine begin with "isw_".  Just for grins I tried specifying "ich" as a format for dmraid, but no luck.  Now I'm curious how that came about for you...

Also, did you set up your RAID in BIOS?

Cheers!

David

---

### Post by dpellegrini on 2011-03-11
"Currently Linux is not supported in Rapid Storage Technology (RST) RAID. Plans are to provide Linux support in a future release of RST."

from [http://www.intel.com/support/motherboards/server/sb/cs-032032.htm](http://www.intel.com/support/motherboards/server/sb/cs-032032.htm)
Date Created: 17-Nov-2010
Last Modified: 18-Feb-2011

Rapid Storage Technology is the new name for Matrix RAID.

So it would appear that any attempts to get it working were doomed from the start.  I think my RAID1 volume works only because mirroring is relatively simple and the disks comprising the volume are treated as just regular disks.

It remains to be seen when this "future release of RST" materializes with Linux support.

---

### Post by wnadgob on 2011-04-29
Did somebody of you tried the approach described in the [_FakeRaidHowto_]("https://help.ubuntu.com/community/FakeRaidHowto") wiki from Ubuntu documentation?

---

### Post by Zeggi on 2011-05-15
Well now im really confused...
Will intel RST Fakeraid work with ubuntu or not?

I have been playing around with my new NAS setup and been testing with, ubuntu 11.04, suse, freenas, xubuntu... well a few distro.

My setup,
ASUS P8H67-M PRO B3
Corsair XMS3 Vengeance 16GB DDR3 PC3-12800 1600MHz
Intel Core i3-2100T 2,5Ghz
Lian Li PC-V354B

with 6hdd, WD20EARS runing at raid5, fakeraid setup by mobo, intel RST.
OS on usb2.0 hdd

The issue im having is that i can't partition the raid array.
in the bios for the fakeraid i see all drives in the array but they are in a initializing state, which means i have to finish the initializing setup in what ever os i will run, but i don't know how its done in ubuntu.

I gave a go with windows 7 and intel has the RST application that lets the array to continue, what it does is a resync and rebuild.

In ubuntu i can see the array but i cant format it, i use disk utility in ubuntu and when i try to format the drive as MBR, GPT or Not partioned i get a error. But the difference is that i can still create a partion on the array IF i choose the option "not partioned" which sounds wrong to me.

Anyway i manage to create a partion table and i can mount the drive but at reboot i still see intel bios state that the discs are initilazing " continue this step in OS"

So my question is what is wrong and how do i get the array fully functional, i want the array to be stated as "normal" in intel bios not initilizing, which i can but only running windows, and i really don't want that mainly because its windows but also with linux distro i can use all 6 hdds and have the OS on a usb drive.

this is also something i found on intels site,
[http://www.intel.com/support/chipsets/imsm/sb/cs-020663.htm](http://www.intel.com/support/chipsets/imsm/sb/cs-020663.htm)

so i need mdadm? but isn't that only for software raid?

---

### Post by gesti on 2011-06-30
> **ewa8949 said:**
> I don't know if anyone is following this thread still or not but I have had a lot of problems with my fakeraid setup. I am trying to do a dual win 7/ubuntu 10.10 setup and I have a 4 drive raid5 setup on an Intel ICH10R motherboard.  The drives have GPT partitions and were created in windows 7 with NTFS on them (I need dual OS support). Both the Windows and Linux OS are on a dedicated drive for booting and the array is for data storage only. 

Ubuntu only see's the first drive of the array.  If I kpartx -a -v /dev/mapper/ich_abababab_vol0 that drive it exposes the large partition and a smaller one at the end but gives GPT errors.  I can then mount the array and am seemingly ok. I seem to be able to read/write data to it and windows can see it.  However, after a few days the array metadata got corrupted and windows could no longer see it.  I rebuilt the array and have spent days copying data over to it after trying to restore from it. Before there was any data on it Ubuntu could see it fine and see all the partitions. However, once I started adding a bunch of data I ran into the same problems. After a couple days the metadata got corrupted and windows could not see the array. Ironically Ubuntu still could. 

Now I am scared to deal with mounting my fakeraid in Ubuntu 10.10 anymore.  Are things more stable with a raid card?  I still can't figure out why it always tells me I have partitions errors and that the NTFS signature is missing.

I've run in to the same thing not so long ago. After wasting a week on this eventually I was advised to use FAT instead of NTFS. It seams Microsoft uses a new type of NTFS that they don't advertise.

And when both linux and Win7 write on to the same partition eventually the filesystem on that partition will get damaged...

So I ended up with a 800 Gb FAT partition that is a pain some times, as you can change rights and owners to files and directories on it. Just if you remount it...

---

