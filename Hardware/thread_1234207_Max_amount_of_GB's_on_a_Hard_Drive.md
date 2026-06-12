---
title: "Max amount of GB's on a Hard Drive?"
date: 2009-08-07
forum: Hardware
---

### Post by billytalent on 2009-08-07
Hi guys, this might be a little "off topic" but you have always been good to me. 

I would like to upgrade my HDD and slip in a new one with more GB's. Is there a way via ubuntu i can check what the max amount of GB's is that i can install i.e how much is compatible. 


Any help is good :)

---

### Post by sanderj on 2009-08-07
With ext3, the max size of the *file system* is 8 TB, with ext4 is much larger.

[http://en.wikipedia.org/wiki/Ext3#Size_limits](http://en.wikipedia.org/wiki/Ext3#Size_limits)
[http://en.wikipedia.org/wiki/Ext4#Large_file_system](http://en.wikipedia.org/wiki/Ext4#Large_file_system)

---

### Post by billytalent on 2009-08-07
> **sanderj said:**
> With ext3, the max size of the *file system* is 8 TB, with ext4 is much larger.

[http://en.wikipedia.org/wiki/Ext3#Size_limits](http://en.wikipedia.org/wiki/Ext3#Size_limits)
[http://en.wikipedia.org/wiki/Ext4#Large_file_system](http://en.wikipedia.org/wiki/Ext4#Large_file_system)

Na that is not what i mean.

---

### Post by hansdown on 2009-08-07
Hi billytalent.

Is this what you're looking for?

[http://www.dewassoc.com/kbase/hard_drives/hard_drive_size_barriers.htm](http://www.dewassoc.com/kbase/hard_drives/hard_drive_size_barriers.htm)

---

### Post by gordintoronto on 2009-08-07
> **billytalent said:**
> Na that is not what i mean.

However, it was the answer to your question.  Perhaps you could explain what you meant?

---

### Post by Revolutionary101 on 2009-08-07
Do you mean the largest hard drive size that you can buy? The largest hard drive you can buy (that I know of) is the Western Digital Caviar Green 2 TB.

---

### Post by billytalent on 2009-08-07
> **Revolutionary101 said:**
> Do you mean the largest hard drive size that you can buy? The largest hard drive you can buy (that I know of) is the Western Digital Caviar Green 2 TB.

I mean, is every model not different, computer i mean in the sense that it may only hold a certain hard drive memory limit?

---

### Post by DownTown22 on 2009-08-07
I'm not following the question here.

Say you buy a 500GB hard drive, do you want to know how much of that will be usable by Ubuntu?

---

### Post by Revolutionary101 on 2009-08-07
> **billytalent said:**
> I mean, is every model not different, computer i mean in the sense that it may only hold a certain hard drive memory limit?

No I don't think they have a limit

---

### Post by KinKiac on 2009-08-07
The only limit I know if is regarding RAM, 32 bit OS's can not use anything over 4gig, they just dont see it.  64bit OS's can see more than 4gig RAM.  Is this what you were thinking of?

---

### Post by billytalent on 2009-08-08
sorry guys, maybe i have made things a little confusing. 

The question is not so much about ubuntu, more about my laptop. 

I went to the store today to ask about a hard drive update, the dude said to me "what kind of drive i had already installed"...its a SATA drive. "He said what is the limit in gb's it can take...". I didnt know there was a limit to the size of the hard drive you could install/replace. He said i needed to check how big of a hard drive my laptop hardware would support. 

That is my question...is there a way i can check this? (using ubuntu)

---

### Post by DownTown22 on 2009-08-08
As far as I know, there's no limit to hard drive size that you could install in your laptop.

---

### Post by billytalent on 2009-08-08
> **DownTown22 said:**
> As far as I know, there's no limit to hard drive size that you could install in your laptop.

Are you sure, i dont want my MB to explode :(

---

### Post by billytalent on 2009-08-08
Can i get confirmation on this?

---

### Post by khelben1979 on 2009-08-08
> **billytalent said:**
> Are you sure, i dont want my MB to explode :(

The thing which is interesting here, in my opinion, is how much power the harddrive needs and that the laptop is able to deliver enough power for this.

Older laptops don't like harddrives which takes too much power. So take a look at the harddrive specifications and choose a harddrive which consumes little power. This will also give you a longer battery time.

---

### Post by DownTown22 on 2009-08-08
> **billytalent said:**
> Are you sure, i dont want my MB to explode :(

I have never once worried about this when building computers.  I've put 160, 320 and 500GB on motherboards without a worry.  I think the guy at the electronics store was on crack...

---

### Post by cariboo on 2009-08-08
What the salesman was asking, is if there is a bios limit on hard drive size, Older systems had a bios limit of 32Gb hard drives, most of todays systems do not have a limit on hard drive size. The only way to find out is to check the laptop manufacturers web site to see if there are any limits.

---

### Post by billytalent on 2009-08-09
Thank you everyone. After checking system spec over @ HP i think i can install whatever I want. It doesn't mention any limits. 

Your all a big help!

---

### Post by highspider on 2011-03-14
IT not so much Operating system as the FILE SYSTEM aka FAT32, NTFS, EXT3, EXT4
 when comes to HARD DRIVE MAX SIZE

Large file system (this can be done with ubuntu)
The ext4 filesystem can support volumes with sizes up to 1 [exabyte]("http://en.wikipedia.org/wiki/Exabyte") and files with sizes up to 16 terabytes.[[9]]("http://en.wikipedia.org/wiki/Ext4#cite_note-8") The current [e2fsprogs]("http://en.wikipedia.org/wiki/E2fsprogs") can only handle a filesystem of 16 [TB]("http://en.wikipedia.org/wiki/Tebibyte"),[[10]]("http://en.wikipedia.org/wiki/Ext4#cite_note-9") but support for larger drives is under development.
SO what ever you plan on with your laptop search the FILE SYSTEM MAX
[http://en.wikipedia.org/wiki/Ext3#Large_file_system](http://en.wikipedia.org/wiki/Ext3#Large_file_system)
[http://en.wikipedia.org/wiki/Ext4#Large_file_system](http://en.wikipedia.org/wiki/Ext4#Large_file_system)

and as [[COLOR=#d40000]**cariboo907**[/COLOR]]("http://ubuntuforums.org/member.php?u=77104") said BIOS

---

