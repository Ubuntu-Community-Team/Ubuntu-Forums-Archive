---
title: "Recovering a corrupt NTFS System"
date: 2010-04-17
forum: Hardware
---

### Post by Biddlesby on 2010-04-17
Hello All,

A friend of mine had some problems with her windows laptop...blue screen saying "unmountable volume".

So I put my faith in Ubuntu, and loaded a live CD. It comes up with the hard drive having bad sectors and lots of lovely errors.

I got the Ubuntu Rescue Remix and ran testdisk. Repair MFT, that kind of stuff. Not exactly sure what I am doing, there's a lot of jargon involved with hard disk repair.

How am I best getting the hard drive in good shape so I can reinstall windows?


An alternative is to ditch the inbuilt drive and use an external hard drive to boot up, but this would have to be from a USB key and the BIOS does not have an option for that. Will I have to upgrade the bios to do this?


I am sorry this is not so connected to Ubuntu, but you guys were very helpful when I set up my dual boot system, so I have posted here rather than techsupportguy :).

Harry

---

### Post by Mark Phelps on 2010-04-18
> **Biddlesby said:**
>  ... How am I best getting the hard drive in good shape so I can reinstall windows? Harry
If the drive has hardware errors (which would account for the lots of bad sectors), you're NOT going to get it in good shape.

You best best would be to contact the website for the drive manufacturer to see if they have a utility you can run the test the health of the drive.  If that checks out, the drive is usable.

---

### Post by djchandler on 2010-04-19
Make sure all connections and jumpers are correctly connected by  downloading that information from the manufacturer's site.

If I was trobleshooting this, I would mount the drive under Windows on another computer first and see if I could recover the partition(s) using **chkdsk X: /f **from the Windows command prompt (where X: is the letter assigned to the drive by the system).  Remember this requires administrator privileges if using Vista or 7. If the hard drive itself is failing, it may not show properly in the BIOS setup. I have seen drives detected, but capacity and model numbers not properly identified. That's a sign of failing hardware too. So connect it internally, then check to see it's properly detected in the BIOS. Make sure all virus software on the host computer is current with the latest definitions.

Make sure you run a through virus scan on the client's hard drive too.

I've had very good success doing this in the past as long as the hard drive itself is not failing. But I usually put the client's drive in an external USB adapter.

There are a lot of things that can cause an un-bootable system besides outright hard drive failure. At the very least, you may be able to recover some data even if the drive is going bad.

Do you know how old the drive is besides make and model? If it's over a couple of years old and known to cause problems, you may be able to save some time and trouble with a google search using the make and model as search parameters.

Reading and writing NTFS to a healthy drive is one thing with Linux. But software that can actually rebuild tables and so forth could violate MS patents if there's no permission from MS.

You can find more support and forums at [MS Technet]("http://technet.microsoft.com/").

---

