---
title: "SCSI Tape drive SIIG inito scsi card not being detected"
date: 2005-07-11
forum: Hardware &amp; Laptops
---

### Post by ferrgle on 2005-07-11
I'm in a bit of trouble.
I have 2 scsi cards.
an adaptec card is working fine the other a SIIG with a FCC identity of SCSI350P.
When I boot up the PC both cards are detected by the BIOS but Ubuntu isnt detecting the SIIG at all.

I cannot find any help on the card or what to do and so any suggestions would be nice.

Thanks

PS the SIIG is marked Initio but I thing they just stick thier logo on it.
I cannot find any info on either the SIIG or Initio sites

---

### Post by alastair on 2005-07-11
It looks like you are not the only one with problems : 

google : SIIG scsi linux

[http://www.ussg.iu.edu/hypermail/linux/kernel/9712.2/0587.html](http://www.ussg.iu.edu/hypermail/linux/kernel/9712.2/0587.html)
[http://www.ussg.iu.edu/hypermail/linux/kernel/9712.2/0587.html](http://www.ussg.iu.edu/hypermail/linux/kernel/9712.2/0587.html)

Maybe try the "advansys" module i.e.

Have one shell open and :

sudo tail -f /var/log/syslog

In another shell :

sudo modprobe advansys

See if anything's found.

Or try :

sudo modprobe initio

---

### Post by ferrgle on 2005-08-01
errr...
I have seemed to have 'fixed' it.
If by fix you accept that I ripped out the stupid SIIG card and put the Tape Drive on the Hard Drive SCSI card which works fine.

Its backing up nicely and the server seems happy enough, so if you know anybody who wants a spare SIIG SCSI card ...

---

### Post by ferrgle on 2005-08-01
[QUOTE=ferrgle]errr...
I have seemed to have 'fixed' it.
If by fix you accept that I ripped out the stupid SIIG card and put the Tape Drive on the Hard Drive SCSI card which works fine.

Its backing up nicely and the server seems happy enough, so if you know anybody who wants a spare SIIG SCSI card ...[/QUOTE]
 But thanks for the quick response

---

### Post by guy_uk on 2005-08-14
Hi

I was wondering if you could tell me how you are backing up to the tape drive?

I want to be able to back up to my HP surestore 24i scsi drive, attached to an iWill 2930 scsi card

this seems to be the only post about scsi tape drives...

ubuntu identifies the card as an 'ABP940-U/ABP960-U' but the attached drive is id'd simply as 'scsi device'

Could anyone offer any help? or point me in the right direction?

Thanks

---

### Post by ferrgle on 2005-12-19
This site should help you
[http://thegoldenear.org/toolbox/unices/tape-backup.html](http://thegoldenear.org/toolbox/unices/tape-backup.html)
Very easy to follow info

---

