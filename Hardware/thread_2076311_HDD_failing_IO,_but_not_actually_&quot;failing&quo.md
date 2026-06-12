---
title: "HDD failing I/O, but not actually &quot;failing&quot;, spins like a champ"
date: 2012-10-25
forum: Hardware
---

### Post by imkqm6 on 2012-10-25
So someone has probably seen this several times, I looked in the forums for a few days about all the problems, and it is like I am trying to decode War and Piece in morse code.

Anyway, I have a 2TB WD hard drive that contained only data, formatted in NTFS. It worked fine with linux mint 11 and Windows 7 dual boot. I upgraded linux mint to the new Ubuntu 12.04. Now my hard drive does not work, in either my windows 7 or ubuntu. What did it do? That dirty dirty install. 

Here is a sample output from dmesg
[http://paste.ubuntu.com/1305939/](http://paste.ubuntu.com/1305939/)

[ 1024.372239] ata6.00: status: { DRDY ERR }
[ 1024.372244] ata6.00: error: { ABRT }
[ 1024.384040] ata6.00: configured for UDMA/33
[ 1024.384062] sd 5:0:0:0: [sdd]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1024.384071] sd 5:0:0:0: [sdd]  Sense Key : Aborted Command [current] [descriptor]
[ 1024.384081] Descriptor sense data with sense descriptors (in hex):
[ 1024.384086]         72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[ 1024.384106]         00 00 00 00 
[ 1024.384115] sd 5:0:0:0: [sdd]  Add. Sense: No additional sense information
[ 1024.384124] sd 5:0:0:0: [sdd] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[ 1024.384142] end_request: I/O error, dev sdd, sector 0
[ 1024.384179] ata6: EH complete

and fdisk -l does not even see it now, I disable crypttab because I assumed it was one of the problems, since fdisk was calling it /dev/mapper/crypttab1 or something like that.
 fdisk /dev/sdd
outputs 
fdisk: unable to read /dev/sdd: Input/output error

it appears that dd_rescue is able to copy the image it seems, but I am an idiot on using it, and it appears like it is going to take until end of universe +1

Thank you all for looking, and for your help if you are patient enough to help though.

---

### Post by ahallubuntu on 2012-10-25
What does S.M.A.R.T. tell you?

Install GSmartControl:

```
sudo apt-get install gsmartcontrol
```

and see if any Attributes of the hard drive are highlighted in red.

If you suspect an incompatibility with your system, try in another system.

---

### Post by imkqm6 on 2012-10-25
No attributes were highlighted in red. Never used this program though, very nifty. Anyway, the error log output this, but it says overall health is good...
threw out error codes 24300
24299
24298
24297
24296
this was the error log, I will preform a better test after this post. 

[http://paste.ubuntu.com/1306254/](http://paste.ubuntu.com/1306254/)

Thanks for your help! I back up my hard drives, but there a few folders I didn't, so I feel like an idiot for not thinking some of the little things were important. Also don't want to lose a 2TB HDD.

---

### Post by imkqm6 on 2012-10-25
> **ahallubuntu said:**
> What does S.M.A.R.T. tell you?

Install GSmartControl:

```
sudo apt-get install gsmartcontrol
```and see if any Attributes of the hard drive are highlighted in red.

If you suspect an incompatibility with your system, try in another system.

Also it is worth noting that windows 7 on the dual boot does not see it, and neither does BT5 (triple boot) and no OS has been installed on this drive that I can remember, but is is a Western digital that was an external HDD, so I know WD is notorious about having some kind of sector issues. Anyway I believe it is a 0 size partition or something that is causing my problem. Some programs see the drive, some don't... The BIOS does see the drive though. UEFI bios btw.

---

### Post by imkqm6 on 2012-10-25
Alright, update on the tests... there was a fatal error of some kind.

[http://paste.ubuntu.com/1306261/](http://paste.ubuntu.com/1306261/)
this was extended test.

I do not believe this drive to be very old, I bought it 1.5 years ago. 
Conveyance test was same thing with this line added to errors.
# 1  Conveyance offline  Fatal or unknown error        90%     13611         -

---

### Post by imkqm6 on 2012-10-25
> **imkqm6 said:**
> Alright, update on the tests... there was a fatal error of some kind.

[http://paste.ubuntu.com/1306261/](http://paste.ubuntu.com/1306261/)
this was extended test.

I do not believe this drive to be very old, I bought it 1.5 years ago. 
Conveyance test was same thing with this line added to errors.
# 1  Conveyance offline  Fatal or unknown error        90%     13611         -

Another thing, looking at the attributes....
[http://paste.ubuntu.com/1306269/](http://paste.ubuntu.com/1306269/)

---

### Post by ahallubuntu on 2012-10-25
You may not think the drive is very old, but S.M.A.R.T. shows power-on hours of 13611.  It may be 1.5 years old but it has been *POWERED ON* for 1.5 years!  That's a lot of use.

You could try running a WD-specific diagnostic.  See what you can download from their site (burn a CD and boot it, probably).  But it appears the drive is failing.  Replace it - it's had a long life already.  Amazon has 2TB WD green drives on sale in the US right now for $90 USD shipped.

---

### Post by imkqm6 on 2012-10-26
> **ahallubuntu said:**
> You may not think the drive is very old, but S.M.A.R.T. shows power-on hours of 13611.  It may be 1.5 years old but it has been *POWERED ON* for 1.5 years!  That's a lot of use.

You could try running a WD-specific diagnostic.  See what you can download from their site (burn a CD and boot it, probably).  But it appears the drive is failing.  Replace it - it's had a long life already.  Amazon has 2TB WD green drives on sale in the US right now for $90 USD shipped.

Thank you very much for your input!
But before I mark this as solved, as I refuse to give up yet, is there any recommendations for rescuing data from an old drive, since it is not completely fried... 
Or any tips for using dd_rescue, since the last time I used it, I apparently set whatever setting to make it run for 8000 hours...I know a lot of people just scream and cry at the idea of a hard drive failing, and most alternative ways to rescue data are way too expensive for me, but I think with just a little more love and attention I may be able to squeeze the last little bit of life it has to pry my data from its cold dead magnetic disks...

Cheers!

---

