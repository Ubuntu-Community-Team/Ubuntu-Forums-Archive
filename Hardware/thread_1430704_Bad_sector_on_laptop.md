---
title: "Bad sector on laptop"
date: 2010-03-15
forum: Hardware
---

### Post by tonythemushroom on 2010-03-15
Hello i've just used my palimsect disc utiliy for the first time and i got the foLlowing message coming up ( see screen shot) saying i've  a bad sector on my hard drive ?? its a packard bell igo 4451 , 20gb hard drive , pretty basic and about 10 years old but it does my needs , does any one know  what it means or how to fix it ??  im not technalically minded and dont have  a clue about hard drives i just no they make laptop work lol any help would be most appricated ta

from tony :D

---

### Post by 2hot6ft2 on 2010-03-15
There's no "screen shot" but you can't fix bad sectors. It's an indication that your hard drive may be beginning to fail.

---

### Post by soupowl on 2010-03-15
Hi there, it sounds to me like your hard disk is failing.  It is easy to replace, and worth doing, but if you get time before it fails then quickly back up anything vital.

Good luck.

---

### Post by dearingj on 2010-03-15
I wouldn't say you need to replace your hard drive just yet (I have a computer which has been showing these warnings since I first started testing Ubuntu Karmic, no noticeable problems yet). Just remember to keep up-to-date backups, and be ready to replace your drive when it does go bad.

---

### Post by soupowl on 2010-03-15
By the way, it's not worth paying a fortune for a new one - if you put the name of your drive into a site like ebay, you'll find cheap replacements that should be fine (in my opinion). When you receive the new one, if the pins look wrong you may have to pull the top set off & reveal the other underneath - I think it's worth watching a 'how to' video first.

My other advice is to put the ubuntu CD in the CD drive while it's all still working, so that after you have installed the new hard drive it will boot up straight away and reinstall the operating system.  I hope this helps.

---

### Post by tonythemushroom on 2010-03-15
have added screen shot sorry having probs adding it , hopefully will last cant afford new or used hard drive for it at the moment , funds running low , lol (expensive wife and kid to look after lol ) , thanks for advice though .:p

---

### Post by srs5694 on 2010-03-15
I've never done this myself, but....

You could use the -c option to e2fsck to map out the bad blocks from the drive. This should keep Linux from attempting to use the bad blocks, which could have anywhere from annoying to disastrous results, depending on what it tried to put in the bad blocks. If I'm reading the man page correctly, the correct syntax would be:

```

sudo e2fsck -c /dev/sda1

```

Change /dev/sda1 to whatever partition(s) you're using. (You may need to run this command multiple times if you've created more than one Linux data partition.) This command will probably take several minutes to a few hours to run, since it's got to read the whole partition.

It should be emphasized, though, that this is far from a guarantee of long-term safety. It could be that your hard drive is just beginning to develop problems, and more bad blocks will develop over time. If so, files you've already stored in sectors that are currently good could become inaccessible tomorrow, next week, or next month. 2.5-inch PATA (IDE) hard drives now seem to be hard to find; I don't see any at NewEgg, for instance. Still, once you've got the cash, you should track one down and replace your failing drive.

---

### Post by tonythemushroom on 2010-03-16
> **srs5694 said:**
> I've never done this myself, but....

You could use the -c option to e2fsck to map out the bad blocks from the drive. This should keep Linux from attempting to use the bad blocks, which could have anywhere from annoying to disastrous results, depending on what it tried to put in the bad blocks. If I'm reading the man page correctly, the correct syntax would be:

```

sudo e2fsck -c /dev/sda1

```Change /dev/sda1 to whatever partition(s) you're using. (You may need to run this command multiple times if you've created more than one Linux data partition.) This command will probably take several minutes to a few hours to run, since it's got to read the whole partition.

It should be emphasized, though, that this is far from a guarantee of long-term safety. It could be that your hard drive is just beginning to develop problems, and more bad blocks will develop over time. If so, files you've already stored in sectors that are currently good could become inaccessible tomorrow, next week, or next month. 2.5-inch PATA (IDE) hard drives now seem to be hard to find; I don't see any at NewEgg, for instance. Still, once you've got the cash, you should track one down and replace your failing drive.


i dont think il try that , not that brave but thank you for the suggestion anyway :D , theres a few second hand laptop shops in my area , ill give them a ring when the funds are availible ( just have to prize my wages and wallet out the wifes hands lol) ,  i phoned one of the shops  this morning ,  and i got reply from them , saying it might be possible that my laptop might take a  sata ? drive , but they would have to have a nosiey at it to see if it would be compatible ,, will pop in and see them at some point .:p

---

### Post by srs5694 on 2010-03-16
IMHO, it's far riskier to *not* use the fsck -c command on a drive that you know has bad blocks.

---

### Post by kalasoka on 2010-03-16
I  too had some problems with the hard disk of my laptop (its 10 yrs old now). At times it would fail to read certain files and would make a lot of noise. I used fsck to fix those bad blocks, and now its working fine. Try something like this:

sudo fsck.ext3 -pcfv /dev/sda3

assuming you have ext3 filesystem, and the bad blocks are on the partition /dev/sda3.

IMP: The drive MUST not be mounted while performing disk check. Otherwise, boot from a Live CD and do the scanning.

---

### Post by psusi on 2010-03-16
Sometimes, like if the power goes out in the middle of a write, sectors can become corrupted and unreadable.  If you run the long smart test and find out exactly which two sectors are bad, you can use dd to write all zeros to them.  This will force the drive to try and rewrite the sector, which may work if it just got garbled, or if it is physically damaged and can not be written to, the drive will automatically remap that sector to a spare one.

The old badblocks test and fix ( which is what fsck -c does ) is obsolete and should not be used on disks that support SMART.  If you do, then it will detect the unreadable sector and just flag that sector as unusable to the filesystem.

---

### Post by 2hot6ft2 on 2010-03-16
2 bad sectors. That's not bad here are 2 of mine...;)
Both are still in use by the way and the one with over 655,000 bad sectors came out of my laptop.

Just keep an eye on it and if the number starts going up then you'll have to start shopping for a new one like I did.

---

### Post by tonythemushroom on 2010-03-17
> **kalasoka said:**
> I  too had some problems with the hard disk of my laptop (its 10 yrs old now). At times it would fail to read certain files and would make a lot of noise. I used fsck to fix those bad blocks, and now its working fine. Try something like this:

sudo fsck.ext3 -pcfv /dev/sda3

assuming you have ext3 filesystem, and the bad blocks are on the partition /dev/sda3.

IMP: The drive MUST not be mounted while performing disk check. Otherwise, boot from a Live CD and do the scanning.
  

i could try that i have a live c.d . as i dont want to unmount the hard drivr inase i cant get it mounted again as i dont know wher the bad blocks are .

---

### Post by tonythemushroom on 2010-03-17
> **2hot6ft2 said:**
> 2 bad sectors. That's not bad here are 2 of mine...;)
Both are still in use by the way and the one with over 655,000 bad sectors came out of my laptop.

Just keep an eye on it and if the number starts going up then you'll have to start shopping for a new one like I did.


yeah i will , ive checked it again today and still the same no numbers going up lol.

---

### Post by tonythemushroom on 2010-03-17
> **psusi said:**
> Sometimes, like if the power goes out in the middle of a write, sectors can become corrupted and unreadable.  If you run the long smart test and find out exactly which two sectors are bad, you can use dd to write all zeros to them.  This will force the drive to try and rewrite the sector, which may work if it just got garbled, or if it is physically damaged and can not be written to, the drive will automatically remap that sector to a spare one.

The old badblocks test and fix ( which is what fsck -c does ) is obsolete and should not be used on disks that support SMART.  If you do, then it will detect the unreadable sector and just flag that sector as unusable to the filesystem.
  

sorry dont understand that ?  what is dd and how do you wrie all zeros to them  ?

---

### Post by kavirajan on 2010-03-17
I had chosen to erase a HD (bad sectors problems i recovered data) using external secure erase commands writes zeros to entire area using Erase Disk tool comes with parted magic. It said that my HD is in frozen state and gave me some other option to do it (HD was making click and grinding noise) i opted for it now my questions is will i be able to use the HD once again a normal fashion after this process. IS there a method or procedure for that? Its a 320GB HD so i assume its going to take lot of time... Thanks in advance...

---

### Post by psusi on 2010-03-17
dd is a swiss army knife command line tool that you can use to move data from anywhere to anywhere.  If you run the long smart test the results should give you the exact sector that has the problem.  You can try to have dd read that sector with:

```

sudo dd if=/dev/sda of=/dev/null bs=512 count=1 skip=sector

```

Assuming the drive in question is sda of course, and sector is the number of the bad sector.  This should fail with an IO error.  If it does, then you know you have the right place.  To write that sector full of zeroes, you do:

```

sudo dd if=/dev/zero of=/dev/sda bs=512 count=1 seek=sector

```

Make sure you type it exactly.  Getting it wrong can have very bad results.  Notice the skip becomes seek in the second version.  Do not forget the count=1 option or it will keep keep going until the end of the disk.

If it is successful you should be able to read the sector again and have it not fail this time.  You should then see the smart numbers change.  The pending sector count should go down by one, and depending on whether the drive had to remap because the sector was physically bad or not, the reallocated sector count should go up by one.

---

### Post by tonythemushroom on 2010-03-17
> **psusi said:**
> dd is a swiss army knife command line tool that you can use to move data from anywhere to anywhere.  If you run the long smart test the results should give you the exact sector that has the problem.  You can try to have dd read that sector with:

```

sudo dd if=/dev/sda of=/dev/null bs=512 count=1 skip=sector

```Assuming the drive in question is sda of course, and sector is the number of the bad sector.  This should fail with an IO error.  If it does, then you know you have the right place.  To write that sector full of zeroes, you do:

```

sudo dd if=/dev/zero of=/dev/sda bs=512 count=1 seek=sector

```Make sure you type it exactly.  Getting it wrong can have very bad results.  Notice the skip becomes seek in the second version.  Do not forget the count=1 option or it will keep keep going until the end of the disk.

If it is successful you should be able to read the sector again and have it not fail this time.  You should then see the smart numbers change.  The pending sector count should go down by one, and depending on whether the drive had to remap because the sector was physically bad or not, the reallocated sector count should go up by one.


thank you , psusi now i know what you mean , ive noted all that down , and will give it a try later on today when i get home from work . and get peace to do it frommy lovable but menacing 2 year old son :D

---

### Post by tonythemushroom on 2010-03-17
> **kavirajan said:**
> I had chosen to erase a HD (bad sectors problems i recovered data) using external secure erase commands writes zeros to entire area using Erase Disk tool comes with parted magic. It said that my HD is in frozen state and gave me some other option to do it (HD was making click and grinding noise) i opted for it now my questions is will i be able to use the HD once again a normal fashion after this process. IS there a method or procedure for that? Its a 320GB HD so i assume its going to take lot of time... Thanks in advance...


pass dont know , am new to this myself . sorry

---

### Post by dE_logics on 2010-03-17
The HDD SMART has not given a warning yet, but the current pending sector count is 2...that is a matter of concern. It might be that all reserved sectors are used up...but the HDD SMART subsystem could have been just evaluating them.

Overall, I don't think you need to buy a new HDD. Post the output of - 

> smartclt -a <your HDD>

2 Bad sectors are not bad you know, for e.g. mine -

---

### Post by psusi on 2010-03-17
> **dE_logics said:**
> The HDD SMART has not given a warning yet, but the current pending sector count is 2...that is a matter of concern. It might be that all reserved sectors are used up...but the HDD SMART subsystem could have been just evaluating them.


Pending means the drive has noticed that it can not read that sector, but has not yet tried to do anything to correct it.  This is why I told the OP to try writing to the sector, since that is what causes the drive to attempt to correct it.  Only then can it try to remap to the spare pool if needed.

---

### Post by tonythemushroom on 2010-03-18
> **psusi said:**
> Pending means the drive has noticed that it can not read that sector, but has not yet tried to do anything to correct it.  This is why I told the OP to try writing to the sector, since that is what causes the drive to attempt to correct it.  Only then can it try to remap to the spare pool if needed.


oh rite okdokey , ta

---

