---
title: "Partitioner hangs and killdisk doesn't work either??"
date: 2009-11-11
forum: Installation &amp; Upgrades
---

### Post by imari2542 on 2009-11-11
I'm trying to help someone remotely install 9.10.  He's obviously fustrated and today I get this email from him:

I spent about 6 hours trying to load the system, then gave up. I was loading it over linux 6.06. I have not been able to do anything except load. The disk will load until disk partitioner starts , then everything stops. It will just sit there and do nothing. I tried it on 2 different computers with the same results. It would not let me get the cd out so I hooked up one of my windows hd s to get it to eject. I now have a hd that  will not even let me run killdisk to try to save it. Any suggestions ? It looks to me like linux is a large pile of garbage !!

I've made a few of my own but as of yet it is not working.  Does anyone have any suggestions that could help?  

I ran into this problem but my turned out to be a bad hard drive.  He tried it on 2 different pc's with the same outcome so I think there is a different problem.

Thanks for the help.

---

### Post by efflandt on 2009-11-11
Not sure if he has not enough RAM or incompatible hardware.  But Western Digital has a utility that can boot from floppy or CD that can zero out the beginning of a drive to make it appear to be a fresh drive with nothing on it  (if he cannot boot Linux and/or does not know how to use dd).  No need to zero the whole drive (may take forever), but zeroing out a MB should do the trick.  Although, Ubuntu install partitioner seemed to find remnants of Linux versions on on my drive after I manually partitioned it differently and they were no longer at the beginning of existing partitions.

For example see [http://support.wdc.com/product/download.asp?groupid=502&lang=en](http://support.wdc.com/product/download.asp?groupid=502&lang=en)

---

### Post by imari2542 on 2009-11-17
He hasn't been in contact with me for a few days but just got back to me.  He tried a different hardrive and it still got hung up.  He's running 1GB of ram so I Don't think memory is the problem.  

Do you think maybe something needs to be changed in the BIOS?  Like LBA enabled or disabled or maybe something else?

---

### Post by imari2542 on 2009-11-17
This is the email he sent today:
Tried one of the Ubuntu discs again today. It did the same thing. It started to install and when disk partitioner started it stopped. Would not partition the HD. I rebooted the computer with the same drive I was trying to install linux on.  It still had windows xp on it so I am using it to send this email. I was trying to install linux over xp. Does linux work ?????????? Is it worth the trouble ??????

I'm stumped, any suggestions???

---

### Post by louieb on 2009-11-17
1st thing to do is check the install CD. All it takes is a few twisted bits in the wrong place to give weird results.  Have him run the [COLOR=Magenta]**check media for defects **[/COLOR]option.

---

### Post by imari2542 on 2009-11-17
Hi, thanks for the quick reply.  He has 4 different CD's and I told him to do that.  He checked the integrity and they are all fine.  So I know he can rule that out.  

I came up with some other suggestions which I am waiting for him to get back to me after he tries. Here is what I am suggesting to him:

[COLOR="Blue"]1.  Try an ealier version of Ubuntu - maybe a bug?

2.  Do you have anything (like a printer) connected to the USB ports of the PC while you're trying to install?  I've read that some Dell USB and Lexmark USB printers can cause the partitioner to hang. If the partitioner still hangs try disconnecting any USB devices.

3.  How long does the system stay in a frozen state?  Is it minutes or hours?  I know resizing NTFS can take a long time. By a long time I don't mean hours but I"m sure you know what I mean.

4.  It&#8217;s possible the power-saving feature or the advanced programmable interrupt controller (APIC) in your comptuer is causing problems.  After you insert the CD rom and it boots, at the menu, Press the F6 key, and type the following at the end of the Boot Options line that appears:

acpi=off noapic nolapic

Press Enter when you&#8217;ve finished to boot Ubuntu.[/COLOR]


I'll send an update after I hear back from him once he tries these out.  Keep your fingers crossed and feel free to suggest anything else in the meantime.  Thanks.

---

