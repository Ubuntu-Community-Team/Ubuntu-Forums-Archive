---
title: "I Need Some Help With This..."
date: 2011-01-26
forum: Hardware
---

### Post by throese on 2011-01-26
I'm going to buy this: [http://www.newegg.com/Product/Product.aspx?Item=N82E16822136197](http://www.newegg.com/Product/Product.aspx?Item=N82E16822136197) on Saturday or Monday once I have the necessary $20 put in my checking account. Anyway, my current hard drive is 120 GB and it isn't cutting it anymore. Hence why I'm buying the 320 GB hard drive. My question is, how do I backup my current system with all the programs and such on it into an ISO file or w/e so I can just burn it to a disc and install it onto the new HDD so I don't have to DL all the updates and programs for the umpteenth time?

Thank you in advanced for all the replies and help.

---

### Post by Vi3tHoneyX on 2011-01-26
[http://clonezilla.org/](http://clonezilla.org/)

**:D**

---

### Post by throese on 2011-01-26
I have CloneZilla on a disk, but don't know how to use it. =P

---

### Post by sidzen on 2011-01-27
Just take out the old 2.5" hdd and put in one of [these]("http://www.newegg.com/Product/Product.aspx?Item=N82E16817816016") -- there is your backup.
Install new 2.5" hdd.
Then learn how to use Clonezilla from a live CD.
Backup original on new, wipe old one from command line with 
[PHP]dd if=/dev/zero of=/deb/(sdb or whatever your external USB hdd is now called) bs=4096 conv=notrunc,sync[/PHP] no parentheses.  Format old hdd as FAT32, entire drive.
Transfer *-img Clonezilla backup file to now-clean and formatted original 2.5" hdd from terminal as root or with sudo (mv command)
Easy!

Enjoy!

---

### Post by Kirboosy on 2011-01-27
Just be careful with dd because if you reverse the **if** (input file) and the **of** (output file) you will wipe out the drive that you want to copy. Trust me I know from personal experience...

Clonezilla isn't hard. It really explains itself. Just do the easy method and you will be fine. For God's sake my dad used it and he has not a clue how to use Linux. It can't be that hard. ;)

---

### Post by throese on 2011-02-02
Well, I need to reinstall CloneZilla or something b/c the CD doesn't want to work and says there is some kind of error on the CD.

---

### Post by sidzen on 2011-02-02
Download [file]("http://clonezilla.org/downloads/alternative/iso-zip-files.php")
Burn at no more than 8X

---

### Post by throese on 2011-02-03
Thank you. I'll try it this weekend. =)

---

