---
title: "Failing to boot with Ubuntu install"
date: 2010-02-06
forum: Hardware
---

### Post by bamdl001 on 2010-02-06
Hi all.
 
Well I took the bull by the horns and attempted to install KK 9.10 on my NEC Versa Laptop. It went through the install beautifully, I answered all the usual questions and was eagerly waiting to set it all up for when the desktop appeared BUT it didn't appear. After install it informed me that it needed to reboot, I took the disk out, changed the boot sequence back to HDD 1. Ubuntu even got to the menu where you hit enter for the OS then this error message appeared:
 
"error: no such device: 03313058-8eb1-4869-b4b9-db61706ae937. 
 Failed to boot default entries.
 Press any key to continue"
 
So I just go round in circles... has anyone ever had this happen? I reinstalled KK but got the same error message. It's almost like the HDD is not recognised or something?????
 
Cheers :)

---

### Post by pi/roman on 2010-02-06
[SIZE=4]I don't know why the uuid would be wrong but you would need to boot from your cd and chan[/SIZE][SIZE=4]ge it. [/SIZE][SIZE=4]Im not sure what v[/SIZE][FONT=Arial][SIZE=4]ersion you are using but it is probably in /boot/grub/menu.lst
You need to get the uuid of your drive you are [/SIZE][/FONT][FONT=Arial][SIZE=4]trying to install to with:
ls -l /dev/disk/by-uuid/[/SIZE][/FONT]

Then go into menu.lst and replace  03313058-8eb1-4869-b4b9-db61706ae937 with the uuid of your drive.

---

### Post by bamdl001 on 2010-02-06
> **pi/roman said:**
> [SIZE=4]I don't know why the uuid would be wrong but you would need to boot from your cd and chan[/SIZE][SIZE=4]ge it. [/SIZE][SIZE=4]Im not sure what v[/SIZE][FONT=Arial][SIZE=4]ersion you are using but it is probably in /boot/grub/menu.lst
You need to get the uuid of your drive you are [/SIZE][/FONT][FONT=Arial][SIZE=4]trying to install to with:
ls -l /dev/disk/by-uuid/[/SIZE][/FONT]

Then go into menu.lst and replace  03313058-8eb1-4869-b4b9-db61706ae937 with the uuid of your drive.

Thanks for the reply, I almost thought that this might be in the too hard basket. By "what version" do you mean what version of linux? (it's Karmic Koala 9.10). Getting to a command prompt when I use the CD to boot from.. is that reasonably straight forward?

Thanks :)

---

### Post by pi/roman on 2010-02-06
Well by version I meant your Grub version.  And I'm not really sure exactly what configuration each version uses but I am thinking that probably the one your using would use a menu.lst file. Some of them use a gub.cfg file which is a little different configuration.
When you boot from the cd there should be an option to try Ubuntu without installing. You can do that and it will bring you into into a live cd desktop similar to the one you get with a new install. Hopefully you should be able to re-establish your network connection from the live cd.
So now open a terminal and type:
sudo fdisk -l
which will list all of your drives.  Your hard drive will most likely be the one with the most blocks, my hard drive is "/dev/sda1". So you will want to mount the drive if it is not already mounted so you can have access to it. Here is the mount command and you should substitute your drive address for mine:
sudo mount /dev/sda1 /mnt
So now your hard drive is accessible through the /mnt directory you can press alt/f2 to get the "run application" window and type:
sudo gedit /mnt/boot/grub/menu.lst
now you need to be very careful with editing this file and only change what is necessary to allow you to boot from the correct drive which would be changing this device number, "03313058-8eb1-4869-b4b9-db61706ae937" to the actual uuid of your hard drive.
remember the command to find the uuid of your drive is:
[FONT=Arial][SIZE=4]ls -l /dev/disk/by-uuid/[/SIZE][/FONT]
and you may notice this command will list the current drive you are booting from as root and also tells you the address of the drive so if you run this command from live cd then your cd will be listed as root.

---

### Post by bamdl001 on 2010-02-06
OK thanks I will have a go at this tonight... Thanks so much for your help it's really appreciated! I am so looking forward to having Ubuntu on my laptop.

Many thanks.. I'll get back to you soon

---

### Post by bamdl001 on 2010-02-07
Ok, I typed in the command "sudo fdisk -l" and got the proper response of "/dev/sda1 etc" then I typed in the next command "sudo mount /dev/sda1 /mnt" and got the response of "mount: you must specify the filesystem type" then it went back to the command prompt of "ubuntu@ubuntu:~$"

Is it asking me to type a certain file system? if so what file system do I type in and what do I actually type into the command line? under the heading System after I first typed in "sudo fdisk -l" it tells me that my system is HPFS/NTFS, does this make any sense?

You know when you said "So now your hard drive is accessible through the /mnt directory you can  press alt/f2 to get the "run application" window and type: sudo gedit /mnt/boot/grub/menu.lst. Now you need to be very careful with editing this file and only change  what is necessary to allow you to boot from the correct drive which  would be changing this device number,  "03313058-8eb1-4869-b4b9-db61706ae937" to the actual uuid of your hard  drive".

I did this and when the menu list opened it is blank.. is this what it's suppose to look like? There is a tab at the top that says menu.lst and the cursor is inside the box just blinking away. Am I suppose to type something in this window?

After typing in ls -l /dev/disk/by-uuid I got the response of:

"lrwxrwxrwx 1 root root 10 2010-02-07 13:15 1cbc4975-ee5f-4fb3-947f-846a6294161f
-> ../../sda5
"lrwxrwxrwx 1 root root 10 2010-02-07 13:15 de2e0cfb-1999-4f57-97bd-e5ac59d26264
-> ../../sda1"

Cheers

---

### Post by pi/roman on 2010-02-07
[FONT=Arial][SIZE=2]Ok the menu.lst was blank because the drive was not mounted so the file did not exist in that path.  So to mount with file system type use:
sudo mount -t ntfs /dev/sda1 /mnt
If that doesn't work then try hpfs:
sudo mount -t hpfs /dev/sda1 /mnt

Now if it is mounted something I forgot before is that it may be write protected, so open up nautilus in root by pressing alt/f2 and typing:
gksudo nautilus

In nautilus go to "file system" then open up "mnt" folder then "boot" then "grub" then, if you switch to compact or list view it may be easier to see, and right click on menu.lst select "properties" go to "permissions" tab and under "Owner root" change "Access read" to "Access read and write" then click on menu.lst and you should be able to change "03313058-8eb1-4869-b4b9-db61706ae937" to your hard drive uuid which is I believe? "de2e0cfb-1999-4f57-97bd-e5ac59d26264"[/SIZE][/FONT]

---

### Post by m4nm4n on 2010-02-07
Similar to pi: [http://ubuntuforums.org/showpost.php?p=8755145&postcount=23](http://ubuntuforums.org/showpost.php?p=8755145&postcount=23)

---

### Post by pi/roman on 2010-02-07
> **m4nm4n said:**
>  [http://ubuntuforums.org/showpost.php?p=8755145&postcount=23](http://ubuntuforums.org/showpost.php?p=8755145&postcount=23)
Ok I notice this method is using the grub.cfg file so that may be the file you need to edit. whether it is grub.cfg or menu.lst only 1 of them will be present so just look for either one.

---

### Post by bamdl001 on 2010-02-07
> **pi/roman said:**
> Ok I notice this method is using the grub.cfg file so that may be the file you need to edit. whether it is grub.cfg or menu.lst only 1 of them will be present so just look for either one.

Thanks for being patient (pi/roman and m4nm4n).

Since we last spoke I have tried a reinstall of KK 9.10 and as usual it installed with ease but unfortunately still doesn't recognise the HDD. So now when I boot from CD then select try without installing and bring up a terminal window then type in "sudo fdisk -l" it tells me that my system is now Linux. However, after typing in "sudo mount /dev/sda1 /mnt" I didn't get any error messages and it went straight back to the command prompt. I was getting a little excited about now thinking that it has now recognised the HDD, but alas when I did the sudo gedit /mnt/boot/grub/menu.lst I got the blank box again.

I even tried the [FONT=Arial][SIZE=2]gksudo nautilus thing then followed all your instructions pi/roman but still the menu.lst file is empty. I am probably doing something wrong (I call it the chair to keyboard interface). Thanks for the links I will study the post but it may take me some time to get my head around it. Do you guy's have any more suggestions I could try... once again your help is much appreciated. BTW my grub version is 1.97 bets4 I think!

One more thing. I did sudo nautilus and navigated to [/SIZE][/FONT]boot/grub/grub.cfg but I found that I didn't have a brub.cfg but instead I have a grubenv file. I opened this up and the only information inside is:
#GRUB Environment Block
######################################################################which goes on forever...
[FONT=Arial][SIZE=2] 
Cheers
[/SIZE][/FONT]

---

### Post by pi/roman on 2010-02-07
I am now thinking i probably directed you wrong when i said to edit menu.lst, I think the file you need to edit is grub.cfg. So when you open up /mnt/boot/grub in nautilus look for "grub.cfg", I believe itis grub2 and there is a wealth of information on it here:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Another file you may want to check while your in live cd is your fstab which is located at /mnt/etc/fstab. This file should not be changed unless you are sure what you are doing also. Here is what the entry for my hard drive looks like in my fstab
 UUID=9c0134d5-9207-40c8-9838-4c105ed44a9e /               ext3    errors=remount-ro 0       1

---

### Post by bamdl001 on 2010-02-07
> **pi/roman said:**
> I am now thinking i probably directed you wrong when i said to edit menu.lst, I think the file you need to edit is grub.cfg. So when you open up /mnt/boot/grub in nautilus look for "grub.cfg", I believe itis grub2 and there is a wealth of information on it here:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Another file you may want to check while your in live cd is your fstab which is located at /mnt/etc/fstab. This file should not be changed unless you are sure what you are doing also. Here is what the entry for my hard drive looks like in my fstab
 UUID=9c0134d5-9207-40c8-9838-4c105ed44a9e /               ext3    errors=remount-ro 0       1

Sorry I missed this one....

[FONT=Arial][SIZE=2]I did sudo nautilus and navigated to [/SIZE][/FONT]boot/grub/grub.cfg  but I found that I didn't have a brub.cfg but instead I have a grubenv  file. I opened this up and the only information inside is:
#GRUB Environment Block
##################################################   ####################which goes on forever...

I will have a look at fstab.. thanks

---

