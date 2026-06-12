---
title: "Cannot create array on Adaptec RAID card"
date: 2009-10-06
forum: Hardware
---

### Post by matt_b on 2009-10-06
Hi all,

I am trying to install Hardy server on my whitebox machine, but can't get that far because I cannot create the RAID array I need.

I have a new Adaptec 2410SA hardware RAID card with two new Samsung Spinpoint F3 1TB drives connected to it.

In the Adaptec RAID manager I initialize the drives, then create a 1TB RAID1 array, at which point it begins a "clear" operation. It gets to about 13%, then fails and leaves the array with a status of IMPACTED. From reading the Adaptec site, this status means that the clear/build operation did not complete successfully (but doesn't say what the cause could be).

Given that it always fails at around 13% I thought it may be a defective disk, but have run the Samsung drive test utility in full surface scan mode on both disks and they are good.

What is also odd is that if I create two 500GB volumes instead, the first fails but the second does not. Likewise if I create four 250GB volumes instead, the first fails but the other three do not. It is almost as if there is a problem around the 130GB point on the disk(s) which causes the build/clear operation to fail.

Can anyone shed some light onto this problem? I'm totally baffled as to what could be at fault.

Thanks
Matt

---

### Post by nice68dude on 2009-10-15
Matt,
i'm going to install a 2410SA on a low-end machine in the next week and i really hope not to deal to same problems you encountered.

The only difference will the drives (apart from the CPU/MB you use): i'm gonna build a RAID5 with 3 Seagate 1 TB drives.

Anyway i'll keep your post updated and read your progresses as well.

Nice68.

---

### Post by SlugSlug on 2009-10-15
You may need dmraid

---

### Post by StevieD on 2009-10-17
Hi Matt,  
 
I have the same problem but using the SA2610 card.  You don't need to be building an array.  If you cntrl-a as the card posts then go to the disk utilities menu and set it to verify the disk.  Fails at the same point.  If I create a single disk volume ~931GB then ntfs format, then use a verify using HB Util it fails at 131071MB.   
 
If i move the disk to and ICH7 controller boot and run the official samsung estool the disk verifies fine (estool never has never work through the SA2610 so I can't repeat this test using the SA2610).   The test using HB util passes fine.
 
I dont think the disk is faulty as such just a combination of a 1TB Samsung F3 HD503SJ and adaptec raid controllers.  
 
At the moment I've adjusted the raid layouts so the I use the first 125GB on each disk, have a junk 5GB section, the use the remaining ~800GB.   And all seems to work perfectly.
 
I think Seagate had problems with some early versions of the 7200.11 series disk that they fixed with an update to the disk firmware eventually.
 
Have you made any progress with a fix?
 
Cheers
 
Stephen

---

### Post by malnic on 2009-10-18
Hi guys, i have the exact same issue, and have been searching the web for 2 weeks looking for a fix!!
 
I have an Adaptec 2610SA RAID controller and a Highpoint 1820 RAID controller.
 
Whether its a RAID 1, or 5, gets to 13% and fails, even using the BIOS to build the array.
 
I wonder if there is a newer firmware for the drive? I've e-mailed Samsung, but not hopefully i'll get a reply.
 
Will try your workaround which seems to work for you guys :)

---

### Post by malnic on 2009-10-21
Splitting the drive up as detailed above worked for me\\:D/
 
Not the ideal situation, but a workaround which will do for now.

---

### Post by chris33 on 2009-10-21
Hi, 
I have the same problem but I guess even blocked before you guys.
I have an adaptec 2420SA, with 4 SAMSUNG 154U 1.5TB.
When going into the adpatec BIOS, Array configuration utility, all menus Create array, initialize drives, rescan drives return no disk found
When going in disk utilities, it finds the 4 disks, I can format them.
Also if I let the system boot, it displays all 4 disks on the 4 SATA ports of the adaptec.
Any clue ? :confused:

---

### Post by SlugSlug on 2009-10-21
have any of you tried dmraid?

```
sudo apt-get install dmraid
```

---

### Post by malnic on 2009-10-21
> **SlugSlug said:**
> have any of you tried dmraid?
 
```
sudo apt-get install dmraid
```
 
Not gonna work on my Windows server :wink:

---

### Post by StevieD on 2009-10-21
Hi Chris,
In my digging around I remember seeing that the sa2n10 cards won't recognised disks bigger than 1TB (I think this was in an adaptec FAQ somewhere.  It could be the same limit applies to your controller.
 You could try plugging a sample 1.5tb disk into a normal sata port.  Samsungs Estool allows you to reduce the number of blocks presented. Then swap the reduced sized disk back to the SA2420, if its now recognised then you'll know its the same 1TB limit.
Cheers
Stephen

---

### Post by chris33 on 2009-10-21
> **StevieD said:**
> Hi Chris,
In my digging around I remember seeing that the sa2n10 cards won't recognised disks bigger than 1TB (I think this was in an adaptec FAQ somewhere.  It could be the same limit applies to your controller.
 You could try plugging a sample 1.5tb disk into a normal sata port.  Samsungs Estool allows you to reduce the number of blocks presented. Then swap the reduced sized disk back to the SA2420, if its now recognised then you'll know its the same 1TB limit.
Cheers
Stephen


Oops you're right, max size is 1TB... I was planning to buy 2TB disks first but too expensive, so I bought these 1.5TB.
I will check using [Estools]("http://www.samsung.com/global/business/hdd/support/utilities/ES_Tool.html") and let you know... I hope it will work... otherwise I will build a raid system from windows disk management.
Thanks for your advice.

---

### Post by malnic on 2009-10-22
Doesn't explain why some people are having trouble with 1TB HDD's though.

---

### Post by chris33 on 2009-10-30
> **chris33 said:**
> Oops you're right, max size is 1TB... I was planning to buy 2TB disks first but too expensive, so I bought these 1.5TB.
I will check using [Estools]("http://www.samsung.com/global/business/hdd/support/utilities/ES_Tool.html") and let you know... I hope it will work... otherwise I will build a raid system from windows disk management.
Thanks for your advice.

This works perfectly ! Thanks a lot.

---

### Post by matt_b on 2009-12-11
Just as a follow-up to this post, I did not get any success with creating an array on the 2410SA card using 1TB Spinpoint F3 disks, so I purchased an LSI card on ebay and that's working fine.

Glad to know it wasn't just me having problems though!

---

### Post by jarthurs on 2010-11-01
> **matt_b said:**
> Hi all,

I am trying to install Hardy server on my whitebox machine, but can't get that far because I cannot create the RAID array I need.

I have a new Adaptec 2410SA hardware RAID card with two new Samsung Spinpoint F3 1TB drives connected to it.

In the Adaptec RAID manager I initialize the drives, then create a 1TB RAID1 array, at which point it begins a "clear" operation. It gets to about 13%, then fails and leaves the array with a status of IMPACTED. From reading the Adaptec site, this status means that the clear/build operation did not complete successfully (but doesn't say what the cause could be).

Given that it always fails at around 13% I thought it may be a defective disk, but have run the Samsung drive test utility in full surface scan mode on both disks and they are good.

What is also odd is that if I create two 500GB volumes instead, the first fails but the second does not. Likewise if I create four 250GB volumes instead, the first fails but the other three do not. It is almost as if there is a problem around the 130GB point on the disk(s) which causes the build/clear operation to fail.

Can anyone shed some light onto this problem? I'm totally baffled as to what could be at fault.

Thanks
Matt

I have the same problem and have discovered that it's a issue related to the way a hard drive handles addressing capacities above 137Gb. The manufacturers have different ways of handling the old 28bit addressing versus the new 48bit addressing to allow capacities over 137Gb.

There is a known fault with Hitachi 500Gb drives, and when you reach the 137Gb boundary the build/clear operation fails and the array status is set to IMPACTED. Your figure of 13% ties in very well with the 137Gb boundary on a 1Tb drive.

It would be wise to check if there is an updated firmware for these drives, otherwise it's a case of finding a different drive.

Regards,
Jason.

---

### Post by alabin on 2011-07-25
same problem here with brand new samsung 500GB F3, but went over 50%. will try a build/verify next

---

