---
title: "Hard disk with buffer i/o errors... recover/repair?"
date: 2008-07-18
forum: General Help
---

### Post by djhobo9 on 2008-07-18
Hi,

I have a 20GB EeePC that's not doing so well recently. For anyone who doesn't know, those 20GB are housed on two separate flash/SSD disks, a 4GB (hereafter referred to as /dev/sda), and a 16GB (/dev/sdb). I put Ubuntu on the 4GB back in May and mapped /home to the 16GB (everything else split up on the 4GB)... this is my fourth computer with some variant of Linux... had no problems with this one until today.

Last night put the computer in suspend and went to bed. Woke up today and the computer was off, battery was dead. Thought that a little odd, but whatever. Went on to boot, and got this:

```
 [   54.882302] ata2.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[   54.882453] ata2.01: cmd 20/00:20:3f:00:00/00:00:00:00:00/f0 tag 0 pio 16384 in
[   54.882457]          res 00/00:00:00:00:00/00:00:00:00:00/00 Emask 0x202 (HSM violation)
[   54.882655] ata2: soft resetting link
[   54.888449] ata2.00: configured for UDMA/33
[   54.889636] ata2.01: configured for PIO0
[   54.891972] ata2.00: configured for UDMA/33
[   54.893108] ata2.01: configured for PIO0
[   54.893125] ata2: EH complete
[   54.897279] ata2.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[   54.897394] ata2.01: cmd 20/00:20:3f:00:00/00:00:00:00:00/f0 tag 0 pio 16384 in
[   54.897398]          res 00/00:00:00:00:00/00:00:00:00:00/00 Emask 0x202 (HSM violation)
[   54.897565] ata2: soft resetting link
[   54.904499] ata2.00: configured for UDMA/33
[   54.906085] ata2.01: configured for PIO0
[   54.908780] ata2.00: configured for UDMA/33
[   54.910327] ata2.01: configured for PIO0
[   54.910345] ata2: EH complete
[   54.910449] sd 1:0:0:0: [sda] 7880544 512-byte hardware sectors (4035 MB)
[   54.914950] ata2.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[   54.915061] ata2.01: cmd 20/00:20:3f:00:00/00:00:00:00:00/f0 tag 0 pio 16384 in
[   54.915065]          res 00/00:00:00:00:00/00:00:00:00:00/00 Emask 0x202 (HSM violation)
[   54.915231] ata2: soft resetting link
[   54.922081] ata2.00: configured for UDMA/33
[   54.923669] ata2.01: configured for PIO0
[   54.926431] ata2.00: configured for UDMA/33
[   54.928003] ata2.01: configured for PIO0
[   54.928020] ata2: EH complete
[   54.928130] sd 1:0:0:0: [sda] Write Protect is off
[   54.928137] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   54.932633] ata2.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[   54.932746] ata2.01: cmd 20/00:20:3f:00:00/00:00:00:00:00/f0 tag 0 pio 16384 in
[   54.932750]          res 00/00:00:00:00:00/00:00:00:00:00/00 Emask 0x202 (HSM violation)
[   54.932918] ata2: soft resetting link
[   54.950048] ata2.00: configured for UDMA/33
[   54.954339] ata2.01: configured for PIO0
[   54.961203] ata2.00: configured for UDMA/33
[   54.965499] ata2.01: configured for PIO0
[   54.965546] ata2: EH complete
[   54.975111] ata2.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[   54.975369] ata2.01: cmd 20/00:20:3f:00:00/00:00:00:00:00/f0 tag 0 pio 16384 in
[   54.975383]          res 00/00:00:00:00:00/00:00:00:00:00/00 Emask 0x202 (HSM violation)
[   54.975769] ata2: soft resetting link
[   54.992314] ata2.00: configured for UDMA/33
[   54.996608] ata2.01: configured for PIO0
[   55.003453] ata2.00: configured for UDMA/33
[   55.008008] ata2.01: configured for PIO0
[   55.008061] ata2: EH complete
[   55.008298] sd 1:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[   55.017729] ata2.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[   55.017981] ata2.01: cmd 20/00:20:3f:00:00/00:00:00:00:00/f0 tag 0 pio 16384 in
[   55.017990]          res 00/00:00:00:00:00/00:00:00:00:00/00 Emask 0x202 (HSM violation)
[   55.018375] ata2: soft resetting link
[   55.033370] ata2.00: configured for UDMA/33
[   55.036051] ata2.01: configured for PIO0
[   55.041774] ata2.00: configured for UDMA/33
[   55.045515] ata2.01: configured for PIO0
[   55.045591] sd 1:0:1:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   55.045620] sd 1:0:1:0: [sdb] Sense Key : Aborted Command [current] [descriptor]
[   55.045651] Descriptor sense data with sense descriptors (in hex):
[   55.045673]         72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[   55.045727]         00 00 00 00 
[   55.045750] sd 1:0:1:0: [sdb] Add. Sense: No additional sense information
[   55.045781] end_request: I/O error, dev sdb, sector 63
[   55.045803] printk: 30 messages suppressed.
[   55.045825] Buffer I/O error on device sdb1, logical block 0
[   55.046048] Buffer I/O error on device sdb1, logical block 1
[   55.046245] Buffer I/O error on device sdb1, logical block 2
[   55.046440] Buffer I/O error on device sdb1, logical block 3
[   55.046638] Buffer I/O error on device sdb1, logical block 4
[   55.046836] Buffer I/O error on device sdb1, logical block 5
[   55.047033] Buffer I/O error on device sdb1, logical block 6
[   55.047231] Buffer I/O error on device sdb1, logical block 7
[   55.047436] Buffer I/O error on device sdb1, logical block 8
[   55.047634] Buffer I/O error on device sdb1, logical block 9
```

some of which repeats, obviously. The last lines in particular look bad. I can boot into Ubuntu, but my /dev/sdb1 (which is mounted to /home) will not mount, so I have no /home directory. I tried running fsck on it, and got this:

```
root@zuul:/# fsck /dev/sdb1
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /dev/sdb1
Could this be a zero-length partition?
```

so following some advice I read online, tried to locate and repair the superblock on sdb1, with:

*e2fsck -b 294912 /dev/sdb1*

where 294912 is a superblock backup i found with *mke2fs /dev/sdb1*

but fsck still won't run, complaining;

```
root@zuul:/# e2fsck -b 294912 /dev/sdb1
e2fsck 1.40.8 (13-Mar-2008)
e2fsck: Device or resource busy while trying to open /dev/sdb1
Filesystem mounted or opened exclusively by another program?

```

even though I've removed /dev/sdb from my fstab and rebooted, in an attempt to keep the computer from trying to mount it. Whenever I run these commands, I get additional "buffer i/o" errors put onto the end of dmesg, indicating that something is messed up while trying to read from the disk, even though fdisk still sees it as a Linux partition of the proper size.

I really need that data back, but would like to avoid having to reformat the entire partition (don't know if that'd even help as this might be a hardware problem) if at all possible. Is there some way to get fsck to run on the disk even though it's supposedly being accessed, or am I hosed at the hardware level?

Thanks for reading (sorry it's so wordy) and for any help...

---

### Post by TSJason on 2008-07-18
Hi,


 Is your /dev/sdb actually a SDHC card stuck in the side? I've found this to be problematic if you try and put the eee into sleep. I ran into a similar issue with mine. I wasn't able to get the SDHC card to even by recognized on my desktop machine with a card reader anymore. Luckily it was still under warrantee and I returned for a new one. I have since just disabled sleep mode on my eee to avoid this problem. Sadly I don't have a better suggestion.

---

### Post by djhobo9 on 2008-07-18
Thanks for the suggestion. I actually think I had that problem with an SDHC card and this computer before... I had to reformat it to make it work in any computer again.

Unfortunately, in this case, it's a 16gb disk inside the case itself. :(

---

### Post by Eccentric Iconoclast on 2008-07-19
I've been having the exact same problem — same computer, same situation in which it occurred and everything — and finally said to hell with it and tried to reformat the disk, but it won't let me; it just stops during the reformatting process until I get sick of it.  I'm starting to think it's a hardware problem.

---

### Post by djhobo9 on 2008-07-20
I guess I'm glad I'm not the only one with this problem. I'm still within warranty, obviously, but I'm not bold enough to try and reformat before making a good effort to retrieve some of the data on the disk. Unfortunately I'm stuck in the middle of Thailand without a sufficiently large enough external media to try and recover data to. Quite a mess.

Anyone else having this problem?? Any luck with ASUS about getting it repaired?

---

### Post by Eccentric Iconoclast on 2008-07-20
I finally left the thing to reformat overnight and it said it went through but had the same messages in dmesg as in boot (same as in the OP), and it acts the same now as it did before I reformatted.  I'm currently in the process of submitting an online technical query.  I'll keep you posted.

I'm glad I didn't have too much stuff to lose on the 16GB drive that wasn't backed up, just some notes on a conlang.

---

### Post by djhobo9 on 2008-07-21
I also sent a tech inquiry to ASUS yesterday, so we'll see what happens. 

What's interesting is that the device still shows up in the BIOS and during POST, still appears as */dev/sdb* and */dev/sdb1* in my */dev* directory, but is absent from my */dev/disk/by-uuid* directory. The fact that the BIOS sees it normally and it's still in */dev* is the only thing making me think there might be hope that it's not a hardware issue. Well, that and the fact that my hardware hasn't suffered any abuse that should lead to this.

Let you know if I hear anything...

---

### Post by Eccentric Iconoclast on 2008-07-22
I just got an automated response telling me to call their support line for a hardware failure, even though I asked if it might not be a hardware failure.  Oy.  I guess I'll call then.

---

### Post by djhobo9 on 2008-07-26
Better than what I've received so far, which is nothing.

I'm curious... are you having the same behavior I described in my last post (shows up in */dev* folder but not in other places)? This is assuming ASUS hasn't helped you resolve the problem yet, which is probably a fair assumption.

---

### Post by Eccentric Iconoclast on 2008-07-30
Yes, I am.  As far as I can tell our problems are completely identical.

I keep forgetting to call, I ought to stop doing that.

---

### Post by djhobo9 on 2008-08-08
So, some interesting news. I just got back to the States the other day and finally had the necessary facilities (i.e. another computer, USB hard drive), to begin working on recovering my data, which includes about 6GB of photos from the summer in Asia :(

I wrote a full image of the 16GB drive out to my USB external drive, and started using a more powerful computer to try and pull data off this image (since, ideally, the image should be no different than my broken drive).

And this is where things got interesting. I figured since I had a copy of the drive image, I'd give reformatting the 16GB a try.

and... it worked like a charm. I lost all the data in my /home directory (pending any possible recovery from the image I saved), but all the errors have disappeared and I can now mount the wiped drive cleanly onto /home.

So mine *appears* to have not been a hardware failure, which is a relief. It seems like you weren't so lucky in trying to reformat. I used mkfs.ext2 followed by gparted (didn't believe it had actually worked the first time, so I actually wiped it twice, I think). If those are the same tools you tried to reformat with, it looks like our situations were slightly different after all.

Good luck, and let me know what happens with ASUS.

---

### Post by tangletooth on 2008-08-14
Exact same model/problem here, too!

I was about to give in and start badgering ASUS, but decided to try mkfs.ext2 (I hadn't bothered trying it since gparted had failed).

It seems to be working. Thanks... :)

---

### Post by djhobo9 on 2008-08-17
Yeah this fix even works over hard resets using the power button, which is good because those can't necessarily be avoided entirely.

However, I did have the problem appear one more time (necessitating yet another reformat)  when I drained my battery completely with the computer turned on... so it seems that allowing the computer to run out of battery while active (and maybe even in sleep mode) should be avoided to prevent this from happening again. Just my guess, at least.

---

### Post by yason- on 2009-02-10
> **djhobo9 said:**
> Yeah this fix even works over hard resets using the power button, which is good because those can't necessarily be avoided entirely.

However, I did have the problem appear one more time (necessitating yet another reformat)  when I drained my battery completely with the computer turned on... so it seems that allowing the computer to run out of battery while active (and maybe even in sleep mode) should be avoided to prevent this from happening again. Just my guess, at least.

Anything else found about this issue? I experienced the same thing and now my Eee PC is spitting out nasty I/O errors to the console and slowing down everything.

I expect to crash my Ubuntu or drain the battery many times in the future so I'm very much interested in finding the final cause.

I would be pretty amazed to fix this by simply reformatting since it seems like a case of a bad hardware access, requiring correcting arguments to the sata modules or tuning hdparm or something like that. But I wouldn't be wrong for the first time... :)

cheers,
y

---

