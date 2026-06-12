---
title: "Installation Problem"
date: 2006-01-25
forum: Installation &amp; Upgrades
---

### Post by carbon on 2006-01-25
I start installing ... select language... and when it gets to loading modules  "Detecting hardware to find cd-rom drives    loading module 'ide-cd' for 'linux atapi cd-rom'... gets to 86% and it freezes....    anyone know the problem? i tried reg install and server still froze.

---

### Post by Who on 2006-01-25
Have you checked that the CDs are good? If you burnt them yourself then they may not be...

---

### Post by n00b on 2006-01-25
I have this problem too and believe me, its not the CDs. I have burned copies  and copies sent to me in the post and both dont work . I believe it has something to do with me having a sata HD and an IDE CDRom. Whats your configuaration like?

---

### Post by Sutekh on 2006-01-25
[QUOTE=n00b]I have this problem too and believe me, its not the CDs. I have burned copies  and copies sent to me in the post and both dont work . I believe it has something to do with me having a sata HD and an IDE CDRom. Whats your configuaration like?[/QUOTE]

I have a SATA HDD and an IDE CDROM and I have never had problems installing Ubuntu with this configuration.  I also have never had a bad CD burnt.  Ever.

How long does the installation freeze before you've had enough?  Seconds?  Minutes?  Hours? (God forbid) Days?

---

### Post by carbon on 2006-01-25
it takes a few minutes not even... after i select the keyboard and its start loading modules.

---

### Post by J Frazer on 2006-01-25
Just a little bit of info on the CDs... I tried with two ShipIt CDs and a of couple CD-RWs without any luck. I finally burned a DVDR and it installed without a hitch. No explanation why this was the case. Just thought I'd throw that out there.

---

### Post by n00b on 2006-01-25
[QUOTE=J Frazer]Just a little bit of info on the CDs... I tried with two ShipIt CDs and a of couple CD-RWs without any luck. I finally burned a DVDR and it installed without a hitch. No explanation why this was the case. Just thought I'd throw that out there.[/QUOTE]

Sounds crazy but I'm desperate. I'll give that a shot and let the forum know the resualts. 

Just for interestest sakes im running AMD 64 3000+, 512MB DDR 400 RAM, 120GB Sata HD, BenQ IDE DVD/CD Rom.


Edit:
Did nothing for me. Exact same place that instalation fails.

---

### Post by Sutekh on 2006-01-25
[QUOTE=carbon]it takes a few minutes not even... after i select the keyboard and its start loading modules.[/QUOTE]
I meant how long do you wait, after it gets stuck at 86% before you restart?

[Ubuntu Forums - Install gets "stuck" when detecting CD-ROM]("http://ubuntuforums.org/showthread.php?t=76482&page=2&highlight=86%25")
At least there are a couple of options to try.

---

### Post by carbon on 2006-01-25
like 15 min  and then the screen went just blue with grey and i was able to type  whatever iwant and just couldnt do anything .....

---

### Post by Sutekh on 2006-01-25
What about the link?  Have you tried the options; noapic, nolapic, ircpoll, and the others?

---

### Post by carbon on 2006-01-25
?

---

### Post by Sutekh on 2006-01-26
Yeah I guess its all mumbo jumbo, sorry.

Look at this post;
[http://ubuntuforums.org/showpost.php?p=415290&postcount=12&highlight=irqpoll+noapic+nolapic]("http://ubuntuforums.org/showpost.php?p=415290&postcount=12&highlight=irqpoll+noapic+nolapic")

1) DISABLE PnP OS in the BIOS

Before using the install CD, see if you can find this option in your BIOS.

2) On boot: linux irqpoll noapic nolapic

This means that when the installation screen comes up type
```
linux irqpoll noapic nolapic
```
then go on with the installation.

Hope this works.

---

### Post by carbon on 2006-01-26
Scaning CD-ROM
/cdrom/pool/main/l....  22%   

 Froze At that  =(   PnP  is disabled.

Creative CDROM so i dont think it should be the cd drive ....

---

### Post by carbon on 2006-01-28
yeah nothing seems to work =(

---

### Post by icehot on 2006-01-28
I have the exact same problem, u select the languages, and it suggests your keyboard layout then after that it starts loading modules for the CD drive, then when it gets to about 77% to around 83% when it loads the ide-atapi module (i think that's what it's called, did this last night and cant quite remember), it just sits there doing nothing for as long as it can, i'm going to try again with the noscsi option in a minute to see if it's that, but not a good start really.

---

### Post by icehot on 2006-01-28
ok that didnt work either... however if u press Alt-F3 during the install you get to see which kernel modules it's failing on, (or rather the last one it tried to load).  And it fails past the generic-ide module actually, but on the drivers/scsi/sr_mod.ko.  Then after waiting several minutes I got the following message:

[4294751.011000] Disabling IRQ #18

Although on the install screen (Alt-F1) the whole thing just looks blank as though it's frozen.  Can anyone help with skipping that module?

---

### Post by carbon on 2006-01-28
im about to install fedora if this doesnt work

---

