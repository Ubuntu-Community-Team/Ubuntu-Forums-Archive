---
title: "Too many Bad Sectors... Ouch!"
date: 2011-01-23
forum: Hardware
---

### Post by Nitrozzy7 on 2011-01-23
Hello,
Today a friend of mine gave me his HP laptop in order for me to fix it. It used to run on Vista but now runs on Ubuntu (thank God!). Once I booted the system a message appeared saying that the disk has many bad sectors. 61411542 to be exact. This is bad.
Do you know if it is possible to save the HDD? Through BIOS maybe?

---

### Post by Nitrozzy7 on 2011-01-24
Do you know if it's possible to save the disk?

---

### Post by Nitrozzy7 on 2011-01-24
Is it possible to save the disk?

---

### Post by ronnielsen1 on 2011-01-24
> A **bad sector** is a [sector]("http://en.wikipedia.org/wiki/Disk_sector") on a computer's [disk drive]("http://en.wikipedia.org/wiki/Disk_drive") or [flash memory]("http://en.wikipedia.org/wiki/Flash_memory")  that cannot be used due to permanent damage (or an OS inability to  successfully access it), such as physical damage to the disk surface or  failed flash memory transistors.

He needs another hard drive

[http://en.wikipedia.org/wiki/Bad_sector](http://en.wikipedia.org/wiki/Bad_sector)

---

### Post by coffeecat on 2011-01-24
> **Nitrozzy7 said:**
> Once I booted the system a message appeared saying that the disk has many bad sectors. 61411542 to be exact.

If the sectors are 512 bytes ones - which they probably are - then 61411542 sectors is equivalent to 31.4 GB (as the manufacturer measures it) or 29.2 GiB! :-s. That's about 30GB of the hard drive that has gone bad. How large is the HD?

I agree with ronnielsen1.

---

### Post by Nitrozzy7 on 2011-01-24
It's 160Gb so, that leaves us with 130Gb...
Could this be linked to a bad power suply? Cause I know it has one and wikipedia makes me think it can be linked.
And is there a way to isolate the faulty sector?

---

### Post by coffeecat on 2011-01-25
> **Nitrozzy7 said:**
> And is there a way to isolate the faulty sector?

Sector[SIZE=4][COLOR=Red]s[/COLOR][/SIZE]! :wink:

The hard drive firmware has probably done that for you already. However, with about a fifth of that hard drive gone bad already, now is the time to replace it. Preferably before you lose data. It is highly likely to get  worse.

You could, of course, use Disk Utility in Ubuntu to run SMART self-tests. That is, if you like watching horror movies.

---

### Post by Nitrozzy7 on 2011-01-25
I've done Extended self-test but it came to a stall; I let it through all night but still it didn't finish. I canceled it. _What will Smart test do anyway and how?_
And _can a bad power supply cause (in any way) Bad Sectors?_
As to why we want to save the disk? Money is running short. It's not about the files. We already saved those bits...

---

### Post by ronnielsen1 on 2011-01-25
If money is tight and the hard drive appears to be half functioning, you can use it. But it is dying and it will die and any info you put on it is at high risk. You are NOT going to be able to repair this drive, only prolong a suffering death

---

### Post by Nitrozzy7 on 2011-01-25
I've done Extended self-test but it came to a stall; I let it through all night but still it didn't finish. I canceled it. _What will Smart test do anyway and how?_
And _can a bad power supply cause (in any way) Bad Sectors?_
As to why we want to save the disk? Money is running short. It's not about the files. We already saved those bits...

@Ronie,
Telling me how I'll do that is what I want to know.

---

### Post by ronnielsen1 on 2011-01-26
Hirens boot cd has a lot of hard drive tools. You can try to use it.

[http://www.hiren.info/pages/bootcd](http://www.hiren.info/pages/bootcd)

[http://www.hirensbootcd.org/files/Hirens.BootCD.13.0.zip](http://www.hirensbootcd.org/files/Hirens.BootCD.13.0.zip)

> **Active Kill Disk 4.1.2393** Securely overwrites and destroys all data on physical drive.
**Darik's Boot and Nuke (DBAN) 1.0.7** Completely deletes the contents of any hard disk it can detect.
**DiskView 2.4**  to view graphical map of your disk, allowing you to check where a file  is located or, by clicking on a cluster, seeing which file occupies it.
**DiskWipe 1.2** Securely erases the contents of a disk replacing it with random data or leaving the drive completely blank.
**ExcelStor's ESTest 4.50** ExcelStor hard disk diagnostic utility.
**Fujitsu HDD Diagnostic Tool 7.00** to check IDE drives for possible defects/problems.
**Fujitsu IDE Low Level Format 1.0** Low Level Format Tool for Fujitsu Drives.
**Gateway GwScan 5.12** Gateway hard drive diagnostic utility.
**Hard Disk Sentinel 1.00.5** Hard Disk health, performance and temperature monitoring tool.
**HDAT2 4.53**the  main function is testing and repair (regenerates) bad sectors for  detected devices. A freeware alternative of HDD Regenerator.
**HDD Capacity Restore 1.2**  This tool allows you to restore factory capacity of any hard drive. it  does not read from or write to the user data area or perform any kind of  formatting, only alters HDD firmware (HPA and DCO settings).
**HDD Erase 4.0** Secure erase using a special feature built into most newer hard drives.
**HDD Low Level Format Tool 2.36** Low-level format tool for S-ATA (SATA), IDE (E-IDE), SCSI, USB, Flash Cards and FIREWIRE external drive enclosures.
**IBM Hitachi Drive Fitness Test 4.16** quickly and reliably tests SCSI, IDE and SATA drives.
**IBM Hitachi Feature Tool 2.15** allows you to control some of the features of the the HDD.
**Maxtor amset utility 4.0** Utility for changing Acoustic Management on the hard drives.
**Maxtor Low Level Formatter 1.1** Maxtor's Low Level Format Utility works on any harddrive.
**Maxtor PowerMax 4.23** designed to perform diagnostic read/write verifications on Maxtor/Quantum hard drives.
**MHDD 4.6**  Precise diagnostic of the mechanical part of a drive, perform Low-level  format, Bad Sector Sepair, access raw sectors, manage S.M.A.R.T.  (SMART) and other drive parameters such as acoustic management,  security, Host Protected Area, etc.
**Samsung Disk Diagnose (SHDIAG) 1.28** to diagnose the disk when suspected to have failures.
**Samsung ESTOOL 3.01v** Drive Diagnostic, Automatic Acoustic Management, Enable/Disable SMART etc.
**Samsung HDD Utility(HUTIL) 2.10** The Drive Diagnostic Utility.
**SeaTools for Dos** GUI 2.22 Text 1.10 versions to test Seagate or Maxtor Parallel ATA (PATA and IDE) and Serial ATA (SATA) interface disc drives.
**SmartUDM 2.00** Hard Disk Drive S.M.A.R.T. Viewer.
**Toshiba Hard Disk Diagnostic 2.00b** Toshiba hard drive diagnostic utility.
**Victoria 3.33e and 3.52rus** a freeware program for low-level HDD diagnostics.
**Victoria 4.46** Universal program for testing storage devices
**ViVard 1.0** HDD low-level diagnostics, Surface test with remap, SMART-attributes etc.
**WDClear 1.30** Restore/Erases the drive back to a factory condition.
**Western Digital Data Lifeguard Tools 11.2** for the installation of Western Digital EIDE Hard Drives.
**Western Digital Diagnostics (DLGDIAG) 5.19** to quickly and efficiently verify the status of the drive.
**Western Digital Data Lifeguard Tools 1.22**  to perform drive identification, diagnostics, and repairs on most WD drives


---

### Post by tgalati4 on 2011-01-26
If one of the heads has gone bad, then you will lose a big chunk of the disk.  No way to recover from that.

---

### Post by Nitrozzy7 on 2011-01-27
Thanx ronnie!
I haven't tried it yet but I'm pretty sure it'll do something.
-SOLVED.

---

### Post by Nitrozzy7 on 2011-01-28
I have booted from the CD but only few of the apps you quote are available. MHDD 4.6 isn't one of them. What now?
The thing is that his Laptop (and HDD) are exactly the same with mine. Purchaised on the same year and so. How can his HDD failing so soon? The only deference between his laptop and mine is the brand name. Mine's an ACER his an HP. Mine is still good, btw.

---

### Post by ronnielsen1 on 2011-01-28
> I have booted from the CD but only few of the apps you quote are available. MHDD 4.6 isn't one of them. What now?
The thing is that his Laptop (and HDD) are exactly the same with mine.  Purchaised on the same year and so. How can his HDD failing so soon? The  only deference between his laptop and mine is the brand name. Mine's an  ACER his an HP. Mine is still good, btw. 	

They're in there. Some of them might be in the dos section, some in linux section etc. Do you know the manufacturer of the hard drive? I'll be able to offer more detailed advice. As far as age, it has nothing to do with it. Parts go bad

---

### Post by Nitrozzy7 on 2011-01-28
Hitachi is the manufacturer.
I'd didn't expected it to be under DOS so I didn't check there. Foolish me.
It runs "read and repair bad sectors" at the moment. This is gonna take a while.

---

### Post by ronnielsen1 on 2011-01-28
Yeah, if you look to the right of the tools at:

[http://www.hiren.info/pages/bootcd](http://www.hiren.info/pages/bootcd)

some of them say Freeware MS Dos, some say Freeware Windows, etc. The Hitachi tools say Freeware MS Dos

---

### Post by Nitrozzy7 on 2011-01-28
I'm running HDAT2 but it's stuck on 45% I'm guessing it must be doing the repairs on those sectors as on the READ, WRITE, READ it prints out "Controller Failure" with progressing values (e.g. 142840434 - Controller Failure).
Block of sectors is also progressing at a quick pace. At the moment is @ 101 of 127.
I'm guessing I should let it till it's finished even if it need a day or two. It's doing repairs after all.
Update: It made a sound and it printed "Possibly Error" with red letters is that normal?

How long should I expect it to run? It currently runs for about 12 hours.

---

### Post by ronnielsen1 on 2011-01-29
> Update: It made a sound and it printed "Possibly Error" with red letters is that normal?

How long should I expect it to run? It currently runs for about 12 hours.

No, normal is not sisplaying any errors. What does the error say?

---

### Post by Nitrozzy7 on 2011-01-29
> **ronnielsen1 said:**
> No, normal is not sisplaying any errors. What does the error say?

This was yesterday:
[img]http://sphotos.ak.fbcdn.net/hphotos-ak-snc6/hs048.snc6/167845_1424068980236_1788095772_825878_1345920_n.jpg[/img]

Since then I aborted the operation and restarted it;
Here's how it looks now:

[img]http://sphotos.ak.fbcdn.net/hphotos-ak-snc6/hs045.snc6/167561_1424069980261_1788095772_825884_8133199_n.jpg[/img]

[img]http://sphotos.ak.fbcdn.net/hphotos-ak-ash1/hs774.ash1/166409_1424070220267_1788095772_825885_8250379_n.jpg[/img]

As you can see it's just a "possibly error" message. "Please wait" suggests to me that it's fixing it.
Note on the last image: "Controller failure" appears now only on WRITE and the second READ whereas yesterday, on ALL three (READ WRITE READ)
"Possibly ERROR" where also appearing yesterday but only once "Block of sectors" was complete. The same it does now only deference is that when the process reached 45%, those messages where appearing every time a new sector was checked. At the moment is at yesterday's pace (like it appears on the first image). It progresses as we speak.

---

### Post by ronnielsen1 on 2011-01-29
> As you can see it's just an "possibly error" message. "Please wait" suggests to me that it's fixing it.

The possible error is an error and the please wait suggests to me that it's trying to read it and can't because of hardware error. I'm afraid that you're not going to be able to fix this. You could try another alternative partition manager like cfdisk but all of them will show errors. I do have a laptop P3 that I use that does not have a hard drive. I run puppy linux from a flash drive. I'm able to surf the net, download, everything. There's also Ubuntu persistant you should be able to do from a flash drive.

Otherwise, do what you can with the hard drive and use it keeping in mind it could die at any minute, get a different hard drive, or use a flash drive

---

### Post by ronnielsen1 on 2011-01-29
Just how much clicking and chattering does this hard drive make?

---

### Post by Nitrozzy7 on 2011-01-29
I'll keep in mind puppy linux.
As to the chattering and clicking, I'd say none.
What caused the HDD to fail anyway? Was it a faulty drive? Software caused? Faulty power supply (it does have one)? What are your thoughts?
Knowing what caused this HDD to fail could possibly save the next one.
Anyway, your help was invaluable. You have my salute!
Thunx :D

---

### Post by ronnielsen1 on 2011-01-30
[http://en.wikipedia.org/wiki/Hard-disk_failure](http://en.wikipedia.org/wiki/Hard-disk_failure)

---

### Post by Nitrozzy7 on 2011-01-30
So changing the hard drive is innevidable...
At least we saved most files.
Thunx again!
You're f@cking awesome!
It was a fun proccess! For me at least, not sure about my friend.
For now I'll try to partion a healthy part of the disk for Ubuntu and then it's up to him. New HDD or a new Puppy!!!
Cheers!

---

