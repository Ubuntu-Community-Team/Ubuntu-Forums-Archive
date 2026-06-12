---
title: "Is my power supply bad?"
date: 2009-07-15
forum: Hardware
---

### Post by ddixonr on 2009-07-15
When I woke up this morning, my desktop (web server) was powered off. I turned it on, watched the bios screen pop up then disappear. Got to the Grub bootloader screen and selected Windows XP from the list. Immediately after hitting ENTER and without any other errors or screens, the PC shut down without warnings or delays.

My immediate reaction was a dying power supply was the culprit, but I have some doubts. Here's why: I inserted an Ubuntu disk and prepared to load it at boot. Got the boot to disk option- great; got the language select and menu screen- awesome; selected the first option to load without changes and watched the progress bar shoot to %100- nice; PC shuts down- SON OF A..!

The next step was disconnecting peripherals. I don't have many so the first idea was the hard drive- no luck. Then tried with just a keyboard- no luck either. Then finally I caught a break. I put Ubuntu back in and selected mem test- it loaded! Went through a full memory test without any errors. 

How can this still be a power supply issue? My only guess is that the power required for booting an OS is a lot more than is required for a memory test and the power supply has just enough juice for certain processes. Anybody else?

---

### Post by landy rover on 2009-07-15
Hi ddixonr I am A Ex windows xp and vista user for a couple of years now i was on windows and then started to dual boot xp and ubuntu

My thoughts is maybe your windows bootsector is maybe faulty because there is not a lot of power difference booting up in xp or ubuntu and ubuntu says the RAM is fine..

my 400watt power packed up a while ago at the beginnig it was nice and quiet and after two years it made a noise etc so then i couldnt start up in ubuntu nor xp..:guitar:
because you said it boots up in ubuntu and then later shuts down!!
just try to repair your windows bootsector ...

i hope it works because i am newb to ubuntu and linux 

regards 

landy rover

---

### Post by ian dobson on 2009-07-15
Hi

So the system switches off when you do alot of disk access (Boot OS/ Try to install OS).

It could be a bad PSU or maybe the harddisk is going bottom up or maybe bad cables. I know it's alot of maybe's but problems like this are a pain to solve.

Regards
Ian Dobson

---

### Post by ddixonr on 2009-07-15
> My thoughts is maybe your windows bootsector is maybe faulty because there is not a lot of power difference booting up in xp or ubuntu and ubuntu says the RAM is fine..

Thanks for the reply, but I think you may have misunderstood what I was doing when I booted Ubuntu. Neither OS on the dual boot hard drive will boot at all. The only thing I was able to do with success was the Ubuntu mem test on the live cd. Not even able to boot the live distro, just the mem test option from the menu. Thanks. I'm not ruling out Windows being the problem here, because it was what was running when it died.

---

### Post by ddixonr on 2009-07-15
> It could be a bad PSU or maybe the harddisk is going bottom up or maybe bad cables. I know it's alot of maybe's but problems like this are a pain to solve.

I disconnected the hard drive while trying to boot the Ubuntu live cd. I hope it's just a PSU because I cannot afford to replace much else.

---

### Post by landy rover on 2009-07-16
> **ddixonr said:**
> Thanks for the reply, but I think you may have misunderstood what I was doing when I booted Ubuntu. Neither OS on the dual boot hard drive will boot at all. The only thing I was able to do with success was the Ubuntu mem test on the live cd. Not even able to boot the live distro, just the mem test option from the menu. Thanks. I'm not ruling out Windows being the problem here, because it was what was running when it died.

yip i think i misunderstood your question ddxinor.
i think Ian dobson maybe right i had a hard drive 160 gig added to my pc already having a 160gig in my pc then when i tried to reinstall windows or boot up it shut down my pc within 2 minutes....
so what i did i remove that other 160 gig that i just put in and voila it was back to normal that hard drive was faulty and beginnig to say goodbye....
2 weeks later i bought myself a 400watt instead of a 300w and try that 160(faulty) in there and it shut down my pc so maybe your hard drive is going


Regards

Landy rover(Iain)

---

