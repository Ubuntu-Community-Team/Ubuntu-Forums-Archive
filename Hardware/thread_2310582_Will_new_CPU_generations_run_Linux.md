---
title: "Will new CPU generations run Linux?"
date: 2016-01-20
forum: Hardware
---

### Post by trash1464 on 2016-01-20
According to a recent PC Mag article, "All next-generation processors built by Intel, AMD, Qualcomm, or others, will only support Windows 10"

[http://www.pcmag.com/article2/0,2817,2498097,00.asp?mailing_id=1549405&mailing=DailyNews&mailingID=394E191E029AB32390186E3917024D83](http://www.pcmag.com/article2/0,2817,2498097,00.asp?mailing_id=1549405&mailing=DailyNews&mailingID=394E191E029AB32390186E3917024D83)

What does this mean for Linux?

---

### Post by QIII on 2016-01-20
Likely nothing at all.

There are *many, many times more* installations of Linux over the breadth of devices than there are Windows desktops.  Windows owns the desktop.  Linux owns the server world, the Internet backbone, cell phones (as Android), embedded devices, supercomputers, etc.

Rather than "will only support Windows 10" it is more likely to be "will not support Windows prior to Windows 10".

---

### Post by trash1464 on 2016-01-20
Understood. I didn't do a good job of asking the question. What I am wondering is if my next desktop machine build uses an Intel "Kaby Lake" processor, will I be able to install and run Linux on it? Taking the PCMag article at face value, I have to wonder.

---

### Post by The Cog on 2016-01-20
I think it means that earlier versions of windows will not be updated to run on new processors.

Edit: Thinking about it, it also suggests that earlier versions of windows have been written to specifically check the CPU version and refuse to run on later versions. One can only suspect that they had "upgrade" fees in mind when they wrote the cripple-ware.

---

### Post by QIII on 2016-01-20
Unfortunately, my crystal ball is in the shop for scheduled maintenance.  ;)

But I would very surprised indeed if Intel and other chip manufacturers cut themselves out of the billions of dollars in revenue produced by contracts for hardware other than for desktops.  So I am pretty sure Linux is in no danger in this case.

This appears to be a Microsoft thing, not something the chip manufacturers are conspiring on.

---

### Post by QDR06VV9 on 2016-01-20
> **trash1464 said:**
> Understood. I didn't do a good job of asking the question. What I am wondering is if my next desktop machine build uses an Intel "Kaby Lake" processor, will I be able to install and run Linux on it? Taking the PCMag article at face value, I have to wonder.

> [COLOR=#666666][FONT=Droid Sans]The new rules will mean that anyone who buys a PC powered by one of Intel&#8217;s, Advanced Micro Devices Inc. (AMD)&#8217;s or Qualcomm Inc.&#8217;s next-generation processors will be forced to run Windows 10 (unless they want to install a Linux-based OS, of course).[/FONT][/COLOR]
From Here [http://siliconangle.com/blog/2016/01/18/microsoft-decrees-that-new-pcs-will-only-be-able-to-run-windows-10/](http://siliconangle.com/blog/2016/01/18/microsoft-decrees-that-new-pcs-will-only-be-able-to-run-windows-10/)
It is likely that most Windows users won't notice a difference at all, and the move seems to be more of a scare tactic by Microsoft to continue its push to Windows 10.
Happy Linux-ing..;)

---

### Post by weatherman2 on 2016-01-20
Remember that Intel CPUs are used in servers and embedded systems, not just desktops and laptops.  Why would Intel purposely exclude Linux?

I agree: the article simply meant that *Microsoft* isn't going to support Windows versions prior to Windows 10 on the new Intel CPUs.  Has nothing to do with Linux.

---

### Post by Yellow Pasque on 2016-01-21
It means that using an OS or kernel that's significantly older than your hardware is a bad idea, regardless of whether you use Windows, Linux, or some other OS.
For example, Intel has pushed KabyLake graphics support to kernel 4.5 ( [http://www.phoronix.com/scan.php?page=news_item&px=Linux-4.5-DRM-Update](http://www.phoronix.com/scan.php?page=news_item&px=Linux-4.5-DRM-Update) ), so if you run a kernel < 4.5, don't be surprised if it doesn't work or only gives you basic graphics functionality.

---

### Post by tokyobadger on 2016-01-21
Intel are a contributor to the linux kernel, have their own linux distro (aimed at cloud/server), have a partnership with Apple for the Mac desktop and laptop lines running OSX which has roots in FreeBSD, and more

The article is clearly aimed at the Windows user as a warning that MS will stop supporting older versions of Windows for new chips [see here](http://arstechnica.com/information-technology/2016/01/skylake-users-given-18-months-to-upgrade-to-windows-10/)

For linux I see no issue, the kernel devs will support the hardware they choose, Torsvalds will add to mainline if he chooses to, worst case someone releases a patch

---

### Post by yoshii on 2016-01-21
In the recent past, I bought a Gateway computer right around the time that Windows Vista came out.  None of the vendors in my entire town had anything for sale without Windows Vista as the Operating System.  Windows XP was just not available from the local vendors, so I bit the bullet and got the Gateway with Vista on it.  

Then I checked the Gateway website to see if the hardware was compatible with Windows XP.  There had been some online articles warning that new hardwares and BIOSes couldn't run Windows XP.  It just so happened that I had an old copy of 32-bit  Windows XP SP2 OEM Home.  

So I decided to be adventurous and I tried to install Windows XP on the new computer even though Gateway claimed it wouldn't work and didn't provide any BIOS or firmware support for it.  Well guess what happened?  It installed perfectly and without any issues whatsoever for any aspect of the firmwares or softwares or BIOS or OS.  

So the moral of the story is:  They lie.  Sometimes stuff works.  

A similar happened with an old Memorex CD-R drive I had.  I bought it for Windows 98 SE and the manual claimed that it and it's CD-burning software wouldn't work on newer operating systems.  But in fact, it worked in XP and Vista.  So yeah, they lied.  I kept using that CD-R drive and the burning software for a long time.  

Ultimately, you kind of have to trust your instincts.  Sometimes these vendors and manufacturers just lie because they are busy pushing newer products to sell and don't want any competition from their older wares.  

As for Linux....
Linux developers are very talented and you can find a linux kernel to run on just about anything.  
I wouldn't worry about it much.

---

