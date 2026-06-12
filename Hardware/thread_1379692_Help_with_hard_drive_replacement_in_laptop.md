---
title: "Help with hard drive replacement in laptop?"
date: 2010-01-12
forum: Hardware
---

### Post by hortstu on 2010-01-12
I just got a Dell inspiron 6000 with a broken hard drive for free.  I curerently use a desk top with a dual boot, XP and hardy heron, and I want to make this laptop 100% linux.  Hardy Heron is probably what I'm going to stick with for now as I'm newer to linux and I'm comfortable with this version.

It seems to be a stock machine from what I can gather.  Apparently, the old drive used window XP, the machine won't recognize drives over 137GB and may even have problems if you install one and partition it.  Something to do with BIOS that I don't fully understand.  Will this be an issue with hardy as well or can I go bigger than 137?  I believe the old drive is a PATA/100 9.5x70x100 40GB 4200rpm.

I can live with 120 GB I'll get an external if I have to, but can I go up 7200 rpm without any issues?

I'd be open to any hard drive suggestions that anyone might have.
Thanks for any help.
Mike

---

### Post by scytherswings on 2010-01-12
From what I know a 7200RPM drive should work fine, but it will decrease your battery life. I'm not so sure about the 137GB limit, if you have the time/patience you could open up your laptop and try a spare drive that's bigger than 137 and see what happens, just mess around with it. I would also look into BIOS updates to see whether Dell has resolved the issue or not. Hope that helps :)

---

### Post by hortstu on 2010-01-13
Thanks scytherswings,

I appreciate your input.  I will look into the BIOS update but I think I'm just going to settle for [this]("http://www.drivesolutions.com/cgi-bin/shop/store.cgi?command=listitems&kind=laptop&pos=0&type=itemid&itemid=l18") drive. 100gb 7200 rpm.  I can live with a little less battery life, I'll probably have to replace that sooner than later anyway... and I don't have any spare drives to test it with.

EDIT  Well I searched and apparently the last BIOS update available from dell for this computer was in 2005 and it doesn't say anything in the "fixes and enhancements" that seem to increase the HD capacity.  

[Maybe I'm wrong?]("http://support.dell.com/support/downloads/download.aspx?c=us&cs=19&l=en&s=dhs&releaseid=R109329&SystemID=INS_PNT_6000&servicetag=&os=WW1&osl=en&deviceid=6999&devlib=0&typecnt=0&vercnt=3&catid=&impid=&formatcnt=1&libid=1&typeid=-1&dateid=-1&formatid=-1&fileid=142094")

Thanks
Mike

---

### Post by hortstu on 2010-01-13
So intel has [this]("http://www.techspot.com/vb/all/windows/t-6526-137-GB-128-GB-binary-limit-Help.html") download to allow the entire capacity of hard drives larger than 137GB to be recognized by the operating system.  

I'm trying to figure out if this is going to be an issue on my 100% linux laptop.  Intel doesn't seem to have an update for linux.  Will I be able to use a HD larger than 137GB without partitioning it or should I just stick with a 100 or 120?

---

### Post by scytherswings on 2010-01-13
Well, your best bet would be to do a little research on your laptop and see what type of HDD controller Dell used in it. Also, depending on the age of your bios, it may be a good idea to upgrade it anyway (might help battery life etc), just make sure that you have stable power and you follow the instructions. I always back up my system before any major upgrade too.

Also, if you have a removable CD/DVD drive, you might be able to find a drive bay on eBay which you could plug in a nice HDD and use that instead of your DVD drive. eBay has been pretty good for my old IBM ThinkPad T21 from 2002. I don't know if those are limited by the laptop's controller or not, that would be a good question for a seller of such products..

---

### Post by cascade9 on 2010-01-14
> **hortstu said:**
> It seems to be a stock machine from what I can gather.  Apparently, the old drive used window XP, the machine won't recognize drives over 137GB and may even have problems if you install one and partition it.  Something to do with BIOS that I don't fully understand.  Will this be an issue with hardy as well or can I go bigger than 137?  I believe the old drive is a PATA/100 9.5x70x100 40GB 4200rpm.


 That is a BIOS issue more than a windows issue. 

IIRC, WinXP (original) cant see any more of the hdd than 137GB but as long as the BIOS sees the drive, it will still work. The 137GB issue was fixed in SP1, and I doubt that your going to be running vanilla XP original. 

As foe the BIOS issue...that was a circa 2002/2003 problem. Its was fixed by 2004, and your chipset is later than 2004, so you should see any 2.5'' drive you want, and be able to use the whole drive.

---

### Post by hortstu on 2010-01-16
Well I bought a 160 gb drive, recieved it and installed it today.  Just for future reference and anyone thinking/searching about this same thing it shows up as 137gb. 

After all the updates are done I'm going to get gparted and partition the drive so that the linux part is 80 and then maybe somewhere down the road I'll use the other 80 for something else.  Maybe even try a different flavor in there.

Thanks for any help again.

---

### Post by lukeiamyourfather on 2010-01-16
> **hortstu said:**
> Well I bought a 160 gb drive, recieved it and installed it today.  Just for future reference and anyone thinking/searching about this same thing it shows up as 137gb. 

After all the updates are done I'm going to get gparted and partition the drive so that the linux part is 80 and then maybe somewhere down the road I'll use the other 80 for something else.  Maybe even try a different flavor in there.

Thanks for any help again.

The 137GB limit is a hardware limitation of the controller, has nothing to do with the operating system or BIOS. The controller uses 28-bit (2^28 total sectors) addresses for sectors which are 512 bytes each (or 137.4GB total). Newer controllers use 48-bit addresses which allows for substantially greater capacity disks not to mention some disks have larger 4 kilobyte sectors. Cheers!

---

### Post by hortstu on 2010-01-17
Thanks,  I wish you saw this thread before.  Is there any way around this limitation?  I've read something about changing a card or something.

---

### Post by lukeiamyourfather on 2010-01-17
> **hortstu said:**
> Thanks,  I wish you saw this thread before.  Is there any way around this limitation?  I've read something about changing a card or something.

The disk controller is typically built on the motherboard. In a desktop a newer controller can be installed in an expansion slot (PCI-Express, PCI, etc.). In a notebook you're pretty much stuck with what's on the motherboard because there's nowhere to put another one. As far as I know there's no way around this limitation in a software or firmware level since its a design limitation of the controller chipset. If its not a boot disk and you just want more storage, an external USB drive could be used since it would have its own controller which would likely be 48-bit if its in the last 5 years or so. Cheers!

---

### Post by hortstu on 2010-01-17
Thanks Luke,

I appreciate your input.  I can live with 137 but is it true that I will still be limited to 137 even if I partition the drive?  Is there anyway to make the system think there are 2 drives?  Probably going to run a dual boot on here eventually anyway.

---

### Post by CharlesA on 2010-01-17
Could be the BIOS. Is it detecting a 137GB drive, or is the formatted capacity 137GB?

You can try partitioning it into 2 drives at 75GB each and see if it takes it.

---

### Post by lukeiamyourfather on 2010-01-17
Sorry to sound like a broken record, but that won't work because ***the limitation is the hardware***, not the software. This explains it pretty good.

[http://www.48bitlba.com/faq.htm#FAQ1](http://www.48bitlba.com/faq.htm#FAQ1)

If you want a larger boot drive, you need a newer computer, end of story. Either that or use an external enclosure that has its own controller that works with larger drives but you wouldn't be able to boot from it. Cheers!

---

### Post by hortstu on 2010-01-17
ok then that settles it.  Thanks again for all your help everyone.

---

### Post by cascade9 on 2010-01-20
> **lukeiamyourfather said:**
> The 137GB limit is a hardware limitation of the controller, has nothing to do with the operating system or BIOS. The controller uses 28-bit (2^28 total sectors) addresses for sectors which are 512 bytes each (or 137.4GB total). Newer controllers use 48-bit addresses which allows for substantially greater capacity disks not to mention some disks have larger 4 kilobyte sectors. Cheers!

LOL, no, actualy its all 3. Controller, BIOS and OS. They all need to be LBA 48bit for hdds bigger than 137GB to be recognised. 

> Windows 2000 Service Pack 2 (SP2) and earlier versions of Windows 2000 do not support 48-bit Logical Block Addressing (LBA) as defined in the ATA/ATAPI 6.0 specification. 

[http://support.microsoft.com/kb/305098](http://support.microsoft.com/kb/305098)

> Windows XP does not support 48-bit LBA support unless you are running Windows XP SP1. If you want to use 48-bit LBA support, you must apply Windows XP SP1 or later.

[http://support.microsoft.com/default.aspx?scid=kb;en-us;q303013](http://support.microsoft.com/default.aspx?scid=kb;en-us;q303013)

Windows 2000 need SP3+ to use LBA 48bit, and windows XP needs SP1+. 

Theres 'known BIOS issues' as well- 

> [FONT=Arial, Helvetica][SIZE=2]There's also an issue with the BIOS where it may be necessary to install a BIOS upgrade  												for your system in order for the system to work properly with the new hard drive[/SIZE][/FONT]

[http://www.48bitlba.com/](http://www.48bitlba.com/)

I have _no_idea_ why the inspriron 6000 doesnt support LBA 48bit. Its got a intel 915 (GM or PM) chipset/Ich6 controller, and Ich6 does support LBA 48bit (but maybe only on SATA ports). Its probably just dell couldnt be bothered to make a new LBA 48bit driver for the PATA ports.....

---

### Post by hortstu on 2010-01-20
[QUOTE=cascade9]I have _no_idea_ why the inspriron 6000 doesnt support LBA 48bit. Its got a intel 915 (GM or PM) chipset/Ich6 controller, and Ich6 does support LBA 48bit (but maybe only on SATA ports). Its probably just dell couldnt be bothered to make a new LBA 48bit driver for the PATA ports.....[/QUOTE]

Thank you Cas for that in depth and understandable explanation.  

So I bought and received a 160GB hard drive for this computer.  Installed Hardy and ran it for a little over 24 hours.  Worked great... dive only showed up as 137 but no big deal.  All of the sudden it started clicking and froze.  The hardy boot disc wouldn't even work any more.  I had to remove the drive to get the boot disc to work.

Is it possible that the computer hardware or BIOS somehow caused this problem or is this 100% definitely just a bunk drive?  I believe I've read of people having problems when they install 250gb HD in this insprion 6000.  If I get another 160 is it just going to happen again?

---

