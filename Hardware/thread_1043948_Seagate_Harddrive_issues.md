---
title: "Seagate Harddrive issues"
date: 2009-01-19
forum: Hardware
---

### Post by Messyhair42 on 2009-01-19
after reading this article [http://www.computerworld.com/action/article.do?command=viewArticleBasic&taxonomyName=storage&articleId=9126280&taxonomyId=19&intsrc=kc_top]("http://www.computerworld.com/action/article.do?command=viewArticleBasic&taxonomyName=storage&articleId=9126280&taxonomyId=19&intsrc=kc_top") i checked my model numbers and my big drive (where most of my media is) is one of the affected models. so i go through the seagate website [http://seagate.custkb.com/seagate/crm/selfservice/search.jsp?DocId=207951]("http://seagate.custkb.com/seagate/crm/selfservice/search.jsp?DocId=207951") and get the drive detector. it's an executable and it runs in wine, but none of the drives show up, i look at the program info and it checks drives that have been connected to the registry, so i think, great, my harddrive company produces fixes for windows customers only. anybody else run into this? got a way around it? do i go ahead and just get the .iso and update?

---

### Post by theozzlives on 2009-01-19
Is itt just firmware? Is the ISO bootable?

---

### Post by Messyhair42 on 2009-01-19
website instructions say to boot to the burned disk, yes.

---

### Post by logos34 on 2009-01-19
> 
Seagate Barracuda 7200.11
	
ST3500320AS
ST3640330AS
ST3750330AS
ST31000340AS
	
SD15, SD16, SD17, SD18, SD19, AD14
	
SD1A

...

If your drive has one of the following **firmware revisions: SD15, SD16, SD17, SD18, SD19, or AD14,** click here to download the SD1A update.

...

If your drive matches one of the models listed in this article **[COLOR="Red"]and does not match any of these versions of firmware, your drive is not affected. [/COLOR]**

run

**sudo lshw -C disk**

it'll show the firmware version, like mine:

>  *-disk                  
       description: ATA Disk
       product: Maxtor 6L120P0
       vendor: Maxtor
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
      [COLOR="Red"] version: BAJ4[/COLOR] **<--Firmware Revision #**
       serial: L31TK1LG 
       size: 114GiB (122GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=a9bfd07a
  *-cdrom
       description: DVD writer
       product: DRW-1608P2
       vendor: ASUS
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrom1
       logical name: /dev/dvd
       logical name: /dev/dvd1
       logical name: /dev/scd0
       logical name: /dev/sr0
       [COLOR="Red"]version: 1.41[/COLOR] **<--Firmware Revision #**
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: ansiversion=5 status=open

---

### Post by Messyhair42 on 2009-01-19
i switched over to windows to fix this problem. i burned the iso and booted to it, and it tells me the specific drive could not be recognized, still looking for troubleshooting from seagate. I have FW V#SD15 btw

---

### Post by Messyhair42 on 2009-01-19
i've checked the drive type and FW ver. but when i try to update from the cd it kicks me out. i've followed the steps to the T. i built the computer myself so i knew what i had put in it. and the HD shipped from tigerdirect on 3 Dec. they said it affected drives manufactured in december 08 so i'm pretty sure it's not affected i just wanted to try.

---

### Post by Messyhair42 on 2009-01-19
i tried the update once more. i had to unhook my 2nd HD (dedicated to ubuntu) as per the instructions. after i couldn't do anything i hooked everything back up and booted into ubuntu and now i can't mount the HD i was trying to update the firmware on. it appears in /media/ but says i don't have permission to access it and my /ect/fstab file is empty. i was using NTFS config before so it would mount automatically. what did i do and how do i fix this problem.

---

### Post by xmastree on 2009-01-20
> **Messyhair42 said:**
> my harddrive company produces fixes for windows customers only. anybody else run into this? got a way around it? do i go ahead and just get the .iso and update?

Boot from the disc you downloaded and you can run the identify tool from there.

However, mine didn't quite work...

The program identified the drive:
[[IMG]http://i50.photobucket.com/albums/f341/chrispollard/seagate/th_seagate1.jpg[/IMG]](http://i50.photobucket.com/albums/f341/chrispollard/seagate/seagate1.jpg)

I selected option 'D':
[[IMG]http://i50.photobucket.com/albums/f341/chrispollard/seagate/th_seagate2.jpg[/IMG]](http://i50.photobucket.com/albums/f341/chrispollard/seagate/seagate2.jpg)

But then:
[[IMG]http://i50.photobucket.com/albums/f341/chrispollard/seagate/th_seagate3.jpg[/IMG]](http://i50.photobucket.com/albums/f341/chrispollard/seagate/seagate3.jpg)
'Specific model not found, ST3500320AS expected'

:(

---

### Post by Messyhair42 on 2009-01-20
I'm getting the exact same thing xmastree. either we have the same problem or seagate messed up again. i saw they removed the firmware update today to be 'validated' so maybe it's a temporary thing.

---

### Post by xmastree on 2009-01-21
More about it here:

[http://www.tomshardware.co.uk/seagate-500gb-1tb-firmware-update,news-30071.html](http://www.tomshardware.co.uk/seagate-500gb-1tb-firmware-update,news-30071.html)


Incidentally, after trying that and failing, my drive still works fine.

I'm still worried about it though...
[img]http://bestsmileys.com/paranoid/4.gif[/img]

---

### Post by Messyhair42 on 2009-01-21
same same

i checked out the article. i have a 1TB drive but the update won't work, nothing to do but wait i guess.

---

### Post by electrogeist on 2009-01-21
Slashdot has had several stories recently regarding Seagate issues.  The latest one is regarding the 500GB 3500320AS models being bricked by flashing the updated firmware: 

[http://it.slashdot.org/article.pl?sid=09/01/21/0052236](http://it.slashdot.org/article.pl?sid=09/01/21/0052236)

A rep from Seagate going under the name **maxtorman** made a number of interesting posts, detailing internal policy/politics and much technical discussion.

It is worth a read if you have a recent Seagate drive or are curious.

---

### Post by RJARRRPCGP on 2009-01-21
Looks like it's not being found, because the program crashed.

Thus, another component complains about the model not being found.

---

### Post by xmastree on 2009-01-22
It seems they fixed it.

[http://forums.seagate.com/stx/board/message?board.id=ata_drives&message.id=6584#M6584](http://forums.seagate.com/stx/board/message?board.id=ata_drives&message.id=6584#M6584)

> **RJARRRPCGP said:**
> Looks like it's not being found, because the program crashed.
If that's the case then I had a lucky escape. Most users on that forum experienced bricked drives when they applied the upgrade.

---

### Post by Messyhair42 on 2009-01-22
thx for the update. i'll try this on mine as soon as i boot into windows.

---

### Post by xmastree on 2009-01-22
> **Messyhair42 said:**
> thx for the update. i'll try this on mine as soon as i boot into windows.

Windows? why?

You just d/l the ISO, burn the CD, shutdown, disconnect any other HDD's, boot into FreeDOS from the CD and run the update.

---

### Post by Messyhair42 on 2009-01-22
i know i could have done it through ubuntu, except the drive that ubuntu is on doesn't need to be updated. it was a success anyway.

---

### Post by Messyhair42 on 2009-01-23
the tool is disabled as of this moment but my problem is solved as well as most other people having this problem i think with seagate's new FW release

---

