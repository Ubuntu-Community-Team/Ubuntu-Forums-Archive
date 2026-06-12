---
title: "Grub help needed"
date: 2008-10-12
forum: General Help
---

### Post by davideotape on 2008-10-12
I want to install ubuntu on my second hard drive, which at the moment is blank and formatted. on my first hard drive I have windows, and I was wondering if there was a way in which I could install grub to the second hard drive without altering the mbr of the first hard drive.

---

### Post by fooman on 2008-10-12
you could disconnect the ide cable from the first drive and then install onto the second drive.

after you all settled installing/updating...you can shut down, reattach the first hard drive and manually add it to your grub menu. 

that is the way i originally set this machine up (i had xp on a raid0 array and did not want to mess it up).  xp raid is gone now,  but ubuntu, suse and vista are installed here on three separate drives using that method.

---

### Post by TeXtonyx on 2008-10-12
When installing Ubuntu from the live cd choose largest unallocated space and
then, at step 7, under "Advanced" do not choose hdo, which is the MBR, instead
select the boot partition which you installed Ubuntu into that will be given as a 
choice. You will need to download the free Bootpart which will make this fairly 
simple, it copies the first 512 "booting" bytes and writes an entry to the boot.ini

[http://forums.majorgeeks.com/showthread.php?t=108021](http://forums.majorgeeks.com/showthread.php?t=108021)
A one page howto on Bootpart and link to the download.

[http://www.linux.com/feature/113945](http://www.linux.com/feature/113945)
Read under "Boot Sector Transplant"

davideotape wrote: .."I have windows, and I was wondering if there was a way in 
which I could install grub to the second hard drive without altering the mbr of the 
first hard drive?"

[http://ubuntuforums.org/archive/index.php/t-499904.html](http://ubuntuforums.org/archive/index.php/t-499904.html) Guide : 
How To Dual Boot Windows XP And Ubuntu Without disturbing Windows Boot Loader
The following command can be very useful in determining partition locations/numbers. 
code: sudo fdisk -l
Linux will refer to your first drive partition as sda1 and second drive as sdb1.
The drive itself is sda (hd0) or sdb (hd1).

---

### Post by caljohnsmith on 2008-10-12
If you can set your BIOS to boot your second drive where you will be installing Ubuntu, you don't have to install the Grub boot loader to the Windows boot loader like TeXtonyx is suggesting; that method could work, but booting directly from your second HDD I think is more ideal, because then you can leave your Windows drive entirely untouched. Also, it is easy to add an entry in your Grub menu to boot your Windows drive if you want. :)

So if you want to boot from your Ubuntu drive and leave your Windows drive alone, then just install Grub to the MBR (Master Boot Record) of the Ubuntu drive by choosing the "advanced" button in the final installation stage, and there tell Grub to install to /dev/sdb or whichever is your Ubuntu drive (and make sure it is the drive, and not a partition like sdb1). If you are unsure which drive is the Ubuntu drive, you can open a terminal (applications > accessories > terminal), and do:
```
sudo fdisk -lu
```
And that will show all your drives. Let me know how it goes or if you run into problems. :)

---

### Post by bodhi.zazen on 2008-10-12
To be honest it is far far easier to go with the defaults and install grub into the MBR of your windows drive.

The defaults work just fine and will allow you to boot either OS. In addition, if needed, it is quite easy to restore your windows MBR.

IMO many of the grub "problems" occur when new users try to change the default behavior when they do not understand grub, let alone the windows boot loader.

IMO, This irrational fear of installing grub and changing the default behavior is the number 1 reason why people end up with problems with grub.

If you are going to change the defaults you should understand how to manage grub.

I suggest you start here :

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

/end rant

---

### Post by meierfra. on 2008-10-12
> [http://ubuntuforums.org/archive/index.php/t-499904.html](http://ubuntuforums.org/archive/index.php/t-499904.html) Guide :
How To Dual Boot Windows XP And Ubuntu Without disturbing Windows Boot Loader 

> that method could work, 

Actually that method will not work in this case. Since Ubuntu and XP are on different hard drives, grub needs to installed in a special way. The supergrub wiki has a guide that actually will work:

[http://www.supergrubdisk.org/wiki/Howto_Boot_Grub_from_windows](http://www.supergrubdisk.org/wiki/Howto_Boot_Grub_from_windows)

[rant] I disagree with   bodhi.zaren's  opinon that  

> This irrational fear of installing grub and changing the default behavior is the number 1 reason why people end up with problems with grub" 

IMO,  that is not even close to the truth [/rant]


Anyway, just follow caljohnsmith's advice. That is the best  way to go.

---

### Post by davideotape on 2008-10-13
> **bodhi.zazen said:**
> To be honest it is far far easier to go with the defaults and install grub into the MBR of your windows drive.

The defaults work just fine and will allow you to boot either OS. In addition, if needed, it is quite easy to restore your windows MBR.

IMO many of the grub "problems" occur when new users try to change the default behavior when they do not understand grub, let alone the windows boot loader.

IMO, This irrational fear of installing grub and changing the default behavior is the number 1 reason why people end up with problems with grub.

If you are going to change the defaults you should understand how to manage grub.

I suggest you start here :

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

/end rant

Just ended up installing GRUB to the windows mbr, and editing the lst file in ubuntu so windows was set as default with a timer with 2 seconds. Thanks a lot for everyone's help.

---

