---
title: "SD card not working"
date: 2008-08-18
forum: Hardware
---

### Post by one_ro on 2008-08-18
Hi all,

I read all posts I could find about this issue, but no matter what I do the card will not be read.

Info:
My laptop is a HP 8710w mobile workstation, with this SD card controller:

$ lspci | grep SD
02:06.3 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 20)

The SD card I'm trying to read is a Kingston SDHC 8GB which works flawlessly under Windows XP (same laptop, dual boot). The card is also read very well in a Asus EEE laptop, but I just can't get it working under my Kubunty Hardy.

If yuo have any hints, is would be highly welcome (I already lost about four hours before posting this message...)

Thanks in advance,
Adrian

---

### Post by coffeecat on 2008-08-18
Insert a card that you know works (such as the Kingston) and then have a look at the output of...

```
dmesg | tail
```... to see if it was detected. You might have to preface that command with sudo. I'm in Gentoo atm, and it works as an ordinary user, but I'm not sure about Ubuntu.

Another possibility is that Ubuntu can't cope with a SDHC card in that particular reader. Have you tried an ordinary SD card?

My only other suggestion is to try googling for the SD host controller in [http://www.google.com/linux](http://www.google.com/linux) . I've had a quick look myself and there seem to be others on other forums with similar issues, and you might find a fix.

---

### Post by silkstone on 2008-08-18
Also, have you tried the same card in an external USB card reader? I have heard of issues with internal readers, where external ones work OK.

---

### Post by SuperSonic4 on 2008-08-18
I agree, plus the converters are cheap, I got mine from the local £1 shop :p

---

### Post by coffeecat on 2008-08-18
> **SuperSonic4 said:**
> I got mine from the local £1 shop

I got mine free with a 2GB card. Can't get much cheaper than that. :p

---

### Post by one_ro on 2008-08-18
Hi again,

> **silkstone said:**
> Also, have you tried the same card in an external USB card reader? I have heard of issues with internal readers, where external ones work OK.

Thanks very much for all your replies. I didn't try with an external USB card reader because... I want to use the internal reader since I do have it... Honestly, I see no point in using something else since the laptop has a working hardware.

For cofeecat, the output didn't yield anything:
```

$ sudo dmesg | tail
[sudo] password for adi:
[  309.893751]  [<c02952fc>] cpuidle_idle_call+0x7c/0xb0
[  309.893768]  [<c0102695>] cpu_idle+0x45/0xd0
[  309.893832]  =======================
[  309.893834] handlers:
[  309.893837] [<f8b1e830>] (yenta_interrupt+0x0/0xe0 [yenta_socket])
[  309.893852] [<f8c01be0>] (sdhci_irq+0x0/0x5c0 [sdhci])
[  309.893863] [<f8969e60>] (ata_interrupt+0x0/0x1f0 [libata])
[  309.893903] Disabling IRQ #19
[ 6346.278861] VMBlock warning: DentryOpRevalidate: invalid args from kernel
[ 6346.278915] VMBlock warning: DentryOpRevalidate: invalid args from kernel

```However, after:

```

$ modprobe wbsd

```the output of dmesg changed (or I didn't wait long enough after inserting the card, ont or the other)

```

$ dmesg | tail
[  309.893837] [<f8b1e830>] (yenta_interrupt+0x0/0xe0 [yenta_socket])
[  309.893852] [<f8c01be0>] (sdhci_irq+0x0/0x5c0 [sdhci])
[  309.893863] [<f8969e60>] (ata_interrupt+0x0/0x1f0 [libata])
[  309.893903] Disabling IRQ #19
[ 6346.278861] VMBlock warning: DentryOpRevalidate: invalid args from kernel
[ 6346.278915] VMBlock warning: DentryOpRevalidate: invalid args from kernel
[ 7534.366699] VMBlock warning: DentryOpRevalidate: invalid args from kernel
[ 7534.366720] VMBlock warning: DentryOpRevalidate: invalid args from kernel
[ 7735.557503] wbsd: Winbond W83L51xD SD/MMC card interface driver
[ 7735.557512] wbsd: Copyright(c) Pierre Ossman

```There is a **[COLOR=Red]Winbond W83L51xD SD/MMC card interface driver[/COLOR]** at the end, but I can't figure out what to do with it and there is still nothing in /dev to mount...
I agree an external USB card reader could be a solution, but I still want to see this internal one. It's bothering me that a small and cheap laptop like Asus EEE, with a small version of Xandros has an out-of-the-box working card reader while a full blown ubuntu doesn't...

It's just not fair to a decent end user...

Thanks again for any hint,
Adrian

---

### Post by lhorace on 2009-06-14
I feel you pain Adria, My SD card work perfectly fine, Kubuntu 9.04 detected it, even 9.10... I used it over and over fine, it work.... Well just all of sudden, Kubuntu doesn't detect it anymore, even after reinstall....

---

### Post by dranoweb on 2010-06-17
this fixed mine after upgrade from 9.04 to 9.10,

reboot, 

press f2 for bios menu

change os status to "complete" instead of "start"

---

