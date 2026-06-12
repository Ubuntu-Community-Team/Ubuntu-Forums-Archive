---
title: "HP Storageworks autoloader"
date: 2009-11-22
forum: Hardware
---

### Post by styleruk on 2009-11-22
Hi all

Here's a tricky one...
I've aquired an old HP stoarageworks autoloader tape backup machine, it's big but I have room for it.
What I'd like to know is if I could use it or would it be easier to sell it and buy something else.

My use would be for backup.  It has a dozen 200GB tapes with it and all works.

Questions:

1) I think it's a scssi drive, therefore I would need to fit a sccsi card.  Any advice on what to use here?

2) What software could I use to access this, on the HP site there is software for SUSE and Red hat but nothing for Ubuntu.

3)  I use Adobe software in windows with Sun Virtual box, would it be easier to use it in this and what problems would I have connecting a ssci to this?

Any help would be appreciated, my initial thoughts are...'sell it', but I am going to give it a go first as it's quite a thing.

Regards
Simon

Ubuntu 9.04 64bit
Quad core intel processor
3 x 74gb raptor drives.

---

### Post by styleruk on 2010-01-07
Nobody can help it seems, I've just updated to 9.10.  If anyone can help it would be appreciated.

Si

---

### Post by Paul Stone on 2010-01-07
Can you figure out what model of autoloader you have?

Is it this?

[INDENT]1/8 G2 LTO-2 Ultrium 448

[http://h18000.www1.hp.com/products/quickspecs/12630_na/12630_na.PDF](http://h18000.www1.hp.com/products/quickspecs/12630_na/12630_na.PDF)[/INDENT]


What are you planning on doing with the autoloader?

---

### Post by Paul Stone on 2010-01-08
Oh, I see where you said that you would like to use the autoloader for backup.

I'm not sure how practical or necessary it is for an individual to use an autoloader for personal backup.  However, it should not be that difficult to hook up, and I can probably help you figure out how to do that.

But, I need to know what model autoloader you have and whether you have any cables which go with it or not.

Most likely, you will need an LVD SCSI Host Bus Adapter (HBA) and cable, plus the power cable to the autoloader.  Also, there may be a serial cable as well.

---

### Post by styleruk on 2010-01-09
Great, someone that can help. 

It is an HP Ultrium LTO 1  with a ton of 200GB tapes.  Can't seem to find any documents on it though.

I'm still in 2 minds as whether to sell it or keep it.  I think it would be great to dump all my photos, music and docs onto separate cartridges (have 20 of them), then I have them backed up.  Maybe then I could do regular weekly backups of my documents.


First things first, I contacted a company that repairs them and asked them a few questions, at the end of this message is their reply.  They mention a particular SCSI card, would I be able to get any SCSI card working in Ubuntu because you can buy them quite cheap.  It has a cable with it so I will not need to get a cable.  And I'm pretty sure which type of card to get but not sure which works with Linux best.

[I]
Hi Simon

I will have a go at answering your points in order but give me a call if you
want to go through something or need more help.



1) I think its a scsi drive, therefore I would need to fit a scsi card. Any
advice on what to use here?
I would suggest an Adaptec SCSI card something like a AHA29/39160 which we
can do for £45 refurb

2) What software could I use to access this, on the HP site there is
software for SUSE and Red hat but nothing for Ubuntu.
When it comes to windows things are fairly easy - install drivers, install
software, select files to backup, load tape and hit GO

For linux things are a bit more long winded but linux boys like it that way
it seems.  You should be able to use either the redhat or suse drivers to
get it to work in ubuntu since they are all pretty similar.  After that you
can use the TAR or CPIO commands in a terminal window to copy your data to
the library.

3) I use Adobe software in windows with Sun Virtual box, would it be easier
to use it in this and what problems would I have connecting a ssci to this?
Err What is Sun Virtual Box?  I do knopw that SCSI devices and tape drives
are usually well supported in virtual environments.

Any help would be appreciated, my initial thoughts are...sell it, but I am
going to give it a go first as its quite a thing.
Although i am not yet convinced that i understand what you are trying to
achieve, I am not sure you should be so keen to sell the unit.  The LTO
drive is the most popular tape drive format with over 80% market share.  I
would suggest that this is a perfect unit to play with since you will
encounter the same setup issues with this as any other drive and any scripts
/ software will also be OK to work on any replacement you purchase later.

Let me know if you need more help

Best Regards
Chris Whitehead.[/I]

---

### Post by Paul Stone on 2010-01-09
Is this what your system looks like?

[http://www.provantage.com/hewlett-packard-hp-ah163a~7HEWS379.htm](http://www.provantage.com/hewlett-packard-hp-ah163a~7HEWS379.htm)

I would seriously consider selling it if you can get a good offer, but it might be difficult to sell since it is older technology.  It's really your own personal decision whether to hang onto it, but individuals can generally take care of their backup needs with hard disks.  Autoloaders like this one are designed for mid-sized companies, which have to back up large amounts of data on a nightly basis.  It's way overkill for an individual.

The AHA29160 is autodetected and works perfectly under Ubuntu 8.10.  Maximum block size is limited to 4MB, which is very good.  It is an older card, but maybe you can pick one up second-hand on the internet (such as on eBay or a reseller).  This card should work perfectly for you.

The AHA29320 has a smaller block size limit (I can't immediately recall what it is), so I do not recommend that Host Bus Adapter (HBA).

I haven't tried the AHA 39160.

I had difficulty using an LTO tape drive with Ubuntu 9.04.  I found that blocks of size greater than 1kB were corrupted, but the bug may have only affected my QLogic Fibre Channel HBA.  So, I can't say whether Ubuntu 9.04 or 9.10 would work for you.  I am planning to evaluate 9.10 in the next few weeks, so I could let you know how it goes.

I will try to ask around about Linux software for running an autoloader.  I think you can pay for some pretty sophisticated backup applications, but I'm not sure about what you can get for free or cheap.

You will also need to connect the ethernet or USB cable, in order to be able to send commands to the autoloader.  The SCSI connection only communicates with the the tape drive inside of the autoloader.  The autoloader inserts and removes cartridges from the tape drive, and you have to be able to instruct it to select particular cartridges, etc.  You do that via the ethernet or USB interface.  I think you only need one or the other, and I would probably try the USB interface first.

I think it should also be possible to manually select cartridges from the front panel of the unit, in which case you probably don't need the autoloader connection.  But, that kind of defeats the purpose of the unit, because you don't want to have to manually select cartridges each time you back up.  You would like to have the backup application take care of that automatically.

---

### Post by Paul Stone on 2010-01-09
If you can't obtain the AHA29160, I think the AHA29320 would work for you as well.  I *think* the largest block size you can use with it is 512kB, but that should be plenty big enough.

Presumably, the AHA39160 would work as well, but I have no experience with it.

---

### Post by styleruk on 2010-01-10
OK, thanks for your help so far, I would be interested to hear what you find when you try 9.10.  I am edging on the side of selling the unit and maybe updating my 80gb external drive to a bigger one and use that to back up.
Thanks for your help so far, I will keep an eye on this post.

The unit that you linked to is a rack type, the one I have is not its a big unit, but stands on it's own.

Regards
Simon

---

