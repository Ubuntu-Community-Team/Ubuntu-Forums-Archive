---
title: "Formatting IPOD, getting errors"
date: 2011-10-08
forum: Hardware
---

### Post by aliensrule77 on 2011-10-08
Hello. I'm trying to format my 120GB Ipod Classic, and I'm having a lot of trouble with it. GParted formats it successfully, but during the format I get this error in kern.log:

```
aliensrule77 kernel: [ 1591.259736] Buffer I/O error on device sdb1, logical block 96
Oct  8 15:56:53 aliensrule77 kernel: [ 1602.602517] sd 8:0:0:0: [sdb] Unhandled sense code
Oct  8 15:56:53 aliensrule77 kernel: [ 1602.602528] sd 8:0:0:0: [sdb]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Oct  8 15:56:53 aliensrule77 kernel: [ 1602.602536] sd 8:0:0:0: [sdb]  Sense Key : Medium Error [current] 
Oct  8 15:56:53 aliensrule77 kernel: [ 1602.602545] Info fld=0x0
Oct  8 15:56:53 aliensrule77 kernel: [ 1602.602549] sd 8:0:0:0: [sdb]  Add. Sense: Unrecovered read error
Oct  8 15:56:53 aliensrule77 kernel: [ 1602.602558] sd 8:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 01 60 00 00 01 00
Oct  8 15:56:53 aliensrule77 kernel: [ 1602.602574] end_request: I/O error, dev sdb, sector 2816
```Also, it won't mount correctly, and using "check" on the hard drive after formatting it gives errors. Is there anything I can do to fix this?

---

### Post by Redblade20XX on 2011-10-08
Have you previously formatted the ipod with Gparted or is this the first time? :)

-Red

---

### Post by wolfen69 on 2011-10-08
The ipod is a highly proprietary piece of hardware. Are trying to restore it? You will need to do that in iTunes.

---

### Post by aliensrule77 on 2011-10-09
I have formatted it in GParted before, and I was just trying to fix it because, before, I was able to copy up to around 2GB of files until the file transfers grinded to a halt. Also, the files would not show up on the IPod as music files, even though it detects that the files are on the hard drive. It was really weird, and I was just wondering if I was formatting it wrong. Also, I've tried restoring it in ITunes already but it didn't help.

---

### Post by aliensrule77 on 2011-10-09
Ok, I decided to just restore it with Itunes again, and it worked, except that I still have my original problem. I'm thinking that this is due to bad sectors on the hard drive. I'm going to run the program "badblocks" but I don't know if that will fix my problem or not. If not, then this is no longer an ubuntu-related issue haha.

---

### Post by nbajordan on 2011-10-09
very nice [:)]("http://www.nba-jordan.com/")

---

### Post by aliensrule77 on 2011-10-10
With badblocks, one question I have is what exactly the output means? For instance, it will either output the number of the block to the console, or else it will output the number plus the word "done" and the time elapsed. What exactly does that mean?

---

