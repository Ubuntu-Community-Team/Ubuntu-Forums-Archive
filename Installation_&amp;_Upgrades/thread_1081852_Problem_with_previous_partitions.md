---
title: "Problem with previous partitions"
date: 2009-02-27
forum: Installation &amp; Upgrades
---

### Post by Guus1982 on 2009-02-27
I did something really stupid.

I removed the partition table and then rebooted. After that the installation of kubuntu was gone of course.

I tried to reinstall and created new partitions. Now i get the message that the installer cant unmount the partitions /target and throws me back to the beginning of the installation.('the installer needs to commit to partition tables, but cannot do so because partitions on the following mount points could not be unmounted: /target please close any applications using these mount points would you like the installer to try to unmount these partitions again? -continue -go back'

If i do a guided installation (full harddisk) it installs kubuntu as if it where run from the usb stick (might be handy to mention that im installing from a usb drive)

How can i fix this.

Is there a way to format my harddisk completely?

---

### Post by lindsay7 on 2009-02-27
If you have windows original install disk you can put it in your cd drive and start the computer.  From there you can reformat you hard drive. you do not need to install windows.  Also you can download a windows start up/repair program on the internet and burn it to a cd and do the same as above. I am sure there are other ways to do this. but if you have a windows disk around or a friend has one this is simple.

---

### Post by lindsay7 on 2009-02-27
I just thought of another way to reformat you drive.  If you can a live cd install with the usb drive, you could use the partition tool that is on it and format the whole drive.

---

### Post by Guus1982 on 2009-02-27
I do not have a cd/dvd drive on my laptop (its a small one).

How can i format the drive from the terminal? Which commands do i need to type?

I can not install any programs using the package manager (gives me errors).

---

### Post by Mark Phelps on 2009-02-27
If you can boot from USB, dowload GParted, install on USB, boot using that, and use that to partition your drive.  Link is below:

[http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php")

---

### Post by Guus1982 on 2009-02-27
ill try that out when im get home. to be continued

---

### Post by Guus1982 on 2009-02-27
no luck it says disk error press any key blablabla

Installing the image on the usb disk went fine tho

I think ive broken my hard disk

---

### Post by lindsay7 on 2009-02-27
Before you give up on the hard drive in you laptop, you could try this.  Get an adaptor like the one shown here, [http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=3012908&CatId=3770](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=3012908&CatId=3770), take the drive out of the laptop and see if you can format it by connecting it to another computer using the usb connection.  If you can format it put it back in the computer and install ubuntu.  If you can not format or read anything on the drive it may be doa. You can also download diagnostic software from the drive mfg to check the condition of the drive. It will tell you if it is bad.  At least you will have a good tool to use in the future with the adaptor. You can use it with cd or dvd drives too.

---

### Post by Guus1982 on 2009-02-28
Thanks for your support. I thought about that solution and figured that an adapter aint that costly so i will giv that a try later i guess, problem is i gave my desktop away to my lil brother and we only got laptops now (or are there usb to 2.5 adapters around, [COLOR="Red"]yes there are look at the link:) edit[/COLOR]

I came up with another id. I took the hard drive from the laptop and placed it in my ps3. The ps3 formatted the hd and i placed it back in my laptop. 

After a full install on a hard disk that seemed totally clean it still gives a non-system disk error when i try to reboot.

Since ive replaced my 40gb ps3 hard drive recently ive made an install on this 40gb hard drive which runs fine.

That counts out the usb stick as being invalid (i thought about that too because, when installing it remembered the username i wanted to use)

Does a harddrive has a bootsector of something that can be damaged? So that i am able to place stuf on it but i cannot boot? That might be the thing why my ps3 had no problem with using it.

Other solution is to swap harddisks with my ps3 but then i got a 320gb hard disk in my laptop and ill be running out of space for my ps3 soon probably.

---

### Post by Guus1982 on 2009-03-01
SOLVED:

fdisk /mbr seem to have done the trick.

---

