---
title: "Hard Drive Failure w/ 10.04"
date: 2011-11-02
forum: Hardware
---

### Post by nerdybrunette on 2011-11-02
Hey everyone, 

I just recently started using my external hard drive again, a Seagate Freeagent Pro 500GB drive, to move music from one computer (Ubuntu 10.04 desktop) to another computer (Windows XP laptop). Last night, I had the drive plugged into my desktop, and it was running updates. I left it plugged in all night. Tonight, I unmounted it and quickly unplugged it from the desktop - I realized I had gotten an error message on the unmount, but it was too late, I had already unplugged it. I don't remember what it said but the drive hasn't worked since. I've plugged it into the laptop and the desktop, tried other power outlets, etc. Nothing works. I've been searching in my log files for some errors that occurred today and I found all of this:

```

syslog.1:Nov  2 19:21:10 nikki-desktop ntfs-3g[5601]: Unmounting /dev/sdf1 (Pickle!)
syslog.1:Nov  2 19:21:16 nikki-desktop kernel: [18519.694001] sd 3:0:0:0: [sdf] Unhandled error code
syslog.1:Nov  2 19:21:16 nikki-desktop kernel: [18519.694006] sd 3:0:0:0: [sdf] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
syslog.1:Nov  2 19:21:16 nikki-desktop kernel: [18519.694014] sd 3:0:0:0: [sdf] CDB: Read(10): 28 00 00 00 00 3f 00 00 08 00
syslog.1:Nov  2 19:21:16 nikki-desktop kernel: [18519.694036] end_request: I/O error, dev sdf, sector 63
syslog.1:Nov  2 19:21:16 nikki-desktop kernel: [18519.694046] Buffer I/O error on device sdf1, logical block 0
syslog.1:Nov  2 19:21:16 nikki-desktop kernel: [18519.694054] Buffer I/O error on device sdf1, logical block 1
syslog.1:Nov  2 19:21:16 nikki-desktop kernel: [18519.694061] Buffer I/O error on device sdf1, logical block 2
syslog.1:Nov  2 19:21:16 nikki-desktop kernel: [18519.694068] Buffer I/O error on device sdf1, logical block 3

```

It looks like the unmount caused all of the error messages. Can anyone figure out exactly what happened and/or know how to fix it? The OS doesn't see the hard drive AT ALL. Not under fdisk, not in lsusb, not in /dev/sd*... nothing. 

Of course, I have everything from my entire life on this drive... and I don't have a backup. So if anybody has any advice at all, I'd appreciate it so incredibly much. Thanks so much in advance.

---

### Post by nerdybrunette on 2011-11-03
Nobody? :(

---

### Post by Grenage on 2011-11-03
It's far more likely that the error on unmount was down to hard drive failure, rather than the unmount causing any hard drive issues.

Does the BIOS see the drive?  If not, it's toast.
If it does, does a liveCD/whatever list the drive with *fdisk -l*?  If not, it's toast.

---

### Post by nerdybrunette on 2012-01-06
Hey Grenage. Sorry I've taken so long to respond. I got married on November 11th and I have been hesitant to touch my hard drive since because I'm so annoyed about it!

Anyway, I actually plugged it into my Ubuntu system and fdisk doesn't see it. I changed the enclosure and it doesn't even spin. The power light doesn't even come on. :(

Any other ideas? I'm a software engineer and I can deal with technical stuff. There's no way I can fix this at home?

Thanks again for your help.

---

### Post by Basher101 on 2012-01-06
to put it short:

your drive is fried and no way to save it.

If there is critical data on it you should give it to some data recovery lab (consider this a last resort as this will cost you 5000$ +)

---

### Post by nerdybrunette on 2012-01-06
Really? That's it?

and is it seriously $5,000+?

---

### Post by Basher101 on 2012-01-06
those labs take their toll...and i am not sure about the price it can be probably alot more...thats why i said only when it is critical data and to go there as a last resort.

no way to save the data otherwise

note: even if you give the HDD to a data recovery lab, it is not garuanteed you will see all your data again...

---

### Post by nerdybrunette on 2012-01-06
Aw man. :-( Thanks for your help, I appreciate it.

---

### Post by Basher101 on 2012-01-06
> **nerdybrunette said:**
> Aw man. :-( Thanks for your help, I appreciate it.

re-reading Grenage's post, you only checked if the disk showed up in fstab? You should take a look if it is displayed in BIOS or not. (if not, it is fried 100%)

---

### Post by collisionystm on 2012-01-06
you said its an external drive?

Just take the drive out of the casing and put it directly into the computer. The usb interface could be bad.

---

### Post by Basher101 on 2012-01-06
> **collisionystm said:**
> you said its an external drive?

Just take the drive out of the casing and put it directly into the computer. The usb interface could be bad.

possible too

but considering its an external usb drive, you will have to open the case (which could break it if you do not know how to do)

---

### Post by upchucky on 2012-01-07
I suggest booting your machine with a ubuntu live cd or knoppix 5.1
Knoppix has both qparted and gparted partitioners on it.
I have had drives that did not respond to gparted but responded to qparted and vice versa.
This is just to test if the drive can be talked to.
If any of the partitioners can read the drive information on the drive then it is likley ok.
You do not want to partition the drive at this moment, you just want to prove it is still somewhat functioning.
Next I would try one or more of the following free live drive forensic cds and try to recover the data from the drive.

forensicswiki.org/wiki/Tools#Forensics_Live_CDs

Lastly I would disassemble the drive and use a usb adaptor kit to connect it to a known good USB port on your computer and then try the partitioners and forensic cd's again.

In the event that the data is unrecoverable but the partitions can be read, you may have to bite the bullet and delete the drive partition(S) and create new partitions. deleting the partitions will permanently erase the data.

---

