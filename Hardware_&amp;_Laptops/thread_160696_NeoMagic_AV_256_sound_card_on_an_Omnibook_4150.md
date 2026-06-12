---
title: "NeoMagic AV 256 sound card on an Omnibook 4150"
date: 2006-04-15
forum: Hardware &amp; Laptops
---

### Post by panth0r on 2006-04-15
Hello, I've been trying to get sound to work on my old Omnibook 4150, which has one of those NeoMagic 256AV cards.  Of lately, my computer has hung up on a related issue, so I cannot provide more information.  What I do remember is that it was rev 12 of the card, which I have found nothing on these forums that got that card working (seems rev 20 is going strong, but rev 12 owners aren't so lucky).  In a few hours I should be able to provide more information, but if anyone has any advice, I'm desparate, and would be greatly appreciative.  Cheers!

---

### Post by panth0r on 2006-04-15
Here is some more information, I really hope it helps ;)

output from lspci |grep Neomagic:

0000:01:00.0 VGA compatible controller: Neomagic Corporation NM2200 [MagicGraph 256AV] (rev 12)
0000:01:00.1 Multimedia audio controller: Neomagic Corporation NM2200 [MagicMedia 256AV Audio] (rev 12)
output from dmesg:
[4294711.784000] nm256: The device is blacklisted.  Loading stopped

As always, if anyone willing to help would like me to post more info, I'd be more than happy...

---

### Post by grumpymole on 2006-04-17
panth0r,

Not an expert on this device, but it appears that, if nm256 is the module for this device, then it might be blacklisted.

This would probably be in /etc/modprobe.d/blacklist.  Look for a line with nm256 and perhaps try commenting it out.

Hope that helps.

Cheers

Warren

---

### Post by panth0r on 2006-04-17
Thank you for the suggestion, but I did already try that.  Thanks again!

---

### Post by eddie303 on 2006-05-06
I looked for the lspci output, I have the same chip in my 4150, so please try the way with the ad1848 module, which I wrote in the other topic for bernardfrancois, because it will surely work for you too.

---

### Post by pwii on 2007-11-23
**This post could be related to an Ubuntu bug filed at**: 65247 [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> **eddie303 said:**
> I looked for the lspci output, I have the same chip in my 4150, so please try the way with the ad1848 module, which I wrote in the other topic for bernardfrancois, because it will surely work for you too.

Hello, I am new to Ubuntu, using Gutsy [7.10] and stumbled about this same problem. Apparently a bug has been filed but so far no cure.  I am interested to try the ad1848 workaround, but when I try

```
sudo modprobe ad1848 io=0x530 irq=5 dma=1 dma2=0
```

I get the following error:

```
FATAL: Error inserting ad1848 (/lib/modules/2.6.22-14-generic/kernel/sound/oss/ad1848.ko): No such device
```

Can somebody offer me help on this error?

Thanks!

---

