---
title: "Which RAID card of these three"
date: 2006-11-19
forum: Hardware &amp; Laptops
---

### Post by Unit01 on 2006-11-19
Hey everyone

I'm in the plans of doing a complete migration to ubuntu and not going back to windows and i thought i had planned almost everything but now i'm in the thoughts of going raid 5 for storage and am considering using hardware raid.
So i'm wondering if anyone has any idea how either of those 3 cards will work under ubuntu.

Adaptec 2410SA
PCI
6 SATA150 Ports

Highpoint RocketRAID 2220
PCI
8 SATAII Ports

Highpoint RocketRAID 2310
PCI-E
4 SATAII Ports

Cause the main issue that i have at the moment is that i'm unsure how either brands products works under linux. So any comments regarding compatibility or performance of the 3 above mentioned RAID cards would be great :)

Or other not so expensive RAID cards would also be good to hear feedback about.

Regards
Unit01

---

### Post by tribaal on 2006-11-19
Well I guess any *hardware raid* card would be completely transparent to the OS you use... since the RAID's setup utility probably is going to be at BIOS level...

- trib'

---

### Post by esaym on 2006-11-19
you should look into software raid: [http://www.rage3d.com/board/showthread.php?t=33866415](http://www.rage3d.com/board/showthread.php?t=33866415)

---

### Post by Unit01 on 2006-11-19
Are there any advantages to doing hardware raid then?

Cause my mainboard is an A8N32-SLI Deluxe. The mainboard says it supports RAID 5 but i'm abit skeptical about that. So my two options are either hardware or software RAID. Any advantages/disadvantages besides costs?
Ease of use?

Kind Regards
Unit01

---

### Post by vgrisham on 2006-11-26
> **esaym said:**
> you should look into software raid: [http://www.rage3d.com/board/showthread.php?t=33866415](http://www.rage3d.com/board/showthread.php?t=33866415)

> my mainboard is an A8N32-SLI Deluxe

I have the same board, Unit01. I've spent the last week trying to get Ubuntu (Dapper and Edgy) to recognize either the silicon or nvraid fake/software/bios raid controllers. Ubuntu sees it when I abandon raid 10 and configure with raid 1 ONLY from the live cd installer (after installing dmraid), but it inevitably locks up. gParted never sees the array (unless I'm running the installer from the live cd). I've also tried the alternative cd's. 

After the frustrations of the last week, I'm looking into pci raid hardware solutions (and I'm still wanking around on xp64).

Esaym, the link you cite mentions that any decent linux installer should be able to handle raid, but so far, it ain't happening. Moreover, if you google nvraid and ubuntu, there are some apparent bugs with software raid and ubuntu at the moment. ](*,)

---

### Post by rogblake on 2006-11-26
> **vgrisham said:**
> 
After the frustrations of the last week, I'm looking into pci raid hardware solutions (and I'm still wanking around on xp64).


3Ware cards are well-supported in Linux, drivers are in the mainstream kernel. (These are true hardware RAID cards, though, and therefore a bit pricey compared to the fake-RAID variety.)

---

### Post by vgrisham on 2006-11-27
rogblake, when I look at manufacturer specs, I note that many list linux support, but only one manufacturer (Areca) specifically lists supported software drivers for debian (which is the core of Ubuntu, right?). Is there a general rule of thumb as far as hardware compatibility and ubuntu? In other words if something works in *insert distro here*, it generall works in Ubuntu?

Edit: rogblake, you're right about 3ware: [http://www.3ware.com/support/OS-support.asp](http://www.3ware.com/support/OS-support.asp)

---

### Post by hkgonra on 2006-11-27
I can only speak for the high-point cards , I have a few of them and they work great in windows but linux support is terrible. I have never been able to get them to work in ubuntu, I got one of them to work is suse but the next time I ran updates it broke it again.

---

### Post by vgrisham on 2006-11-27
I just ordered a [3ware 8006]("http://www.3ware.com/products/serial_ata8000.asp"). According to their [os support page]("http://www.3ware.com/support/OS-support.asp"), linux kernel 2.6.x and above comes with the driver.

I paid $101.08 with shipping from buy.com. 

I'll post my experience.

---

### Post by c8h10n4o2 on 2007-06-18
DO NOT go with HighPoint RocketRaid. It is made for Windows and although they have Linux drivers, it is near impossible to get it running correctly.

---

### Post by hackeron on 2007-07-13
> **c8h10n4o2 said:**
> DO NOT go with HighPoint RocketRaid. It is made for Windows and although they have Linux drivers, it is near impossible to get it running correctly.

I second that. I have a RocketRaid 2310 and I had to downgrade to 2.6.19 for the kernel not to hang on boot with their crappy driver built in. And don't even bother compiling it as a module, it won't happen.

They say their driver is opensource, but it's just an opensource wrapper around a closed source driver. Avoid this card!

---

