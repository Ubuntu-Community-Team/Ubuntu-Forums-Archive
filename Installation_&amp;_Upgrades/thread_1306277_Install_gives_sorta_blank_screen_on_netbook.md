---
title: "Install gives sorta blank screen on netbook"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by dawik on 2009-10-30
I'm trying to install Karmic Koala on 

Acer Aspire one 250 - 1585

1 - Downloaded ISO
2 - Check md5sums - Match
3 - Use USB creator
4 - Change boot option one aspire One
5 - Boot from USB : I get "Installer boot menu"
5a If I select Check disk for defects : It works, no defect
5b If I select Test memory : It works memory is OK
5C If I select Try or Install, I get the logo for few seconds, then a blank screen...nothing happening and I need to manually reboot

Any idea of where I might be wrong or anything to change....

---

### Post by raven01 on 2009-10-30
thats the same issue im having on the desktop version. and so far no one has really gave an answer to this. so i guess we are stuck for now

---

### Post by dawik on 2009-10-30
I've tried with new USB formatting (Fat and Fat32) same result.

I've also tried disabling AHCI SATA in BIOS (one of the few options in bios...) but it doesn't change anything

---

### Post by abz1 on 2009-10-30
Yes, same problem. I have been searching for a solution, but had no luck.

I have a dell 2209WA lcd and nvidia 7600gs graphics.

I have tried the desktop version and the alternative. Hope someone can help.

---

### Post by ikacer on 2009-10-31
here is a thread which may help:

[http://ubuntuforums.org/showthread.php?t=1307169]("http://ubuntuforums.org/showthread.php?t=1307169")

---

### Post by eduardoq on 2009-10-31
I have the same problem with my aspire one netbook. If in installer boot menu i choose help option/F6/write "live-install noapic nolapic" i get a different error that said "can not mount /dev/loop1 on /cow".

---

### Post by Goofy_2 on 2009-11-01
PROBLEM confirmation:
bootable USB-drive with UNR 9.10 made with usb-creator (Ubuntu 9.04).
Same problem with this bootable USB-drive as described on Dell 5150 laptop:
"can not mount /dev/loop1 on /cow"
Tried almost every combination of starting options.

CLUES (maybe) for solution:
1) Starting with bootable USB-drive with UNR 9.04 does not give any problem on the same laptop.
2) Starting UNR 9.10 from CD-rom made from the same iso-file succeeds.

Conclusion: created USB-drive UNR 9.10 has something to do with the problem

Do you have any idea???

---

### Post by Revelate on 2009-11-02
I had the same problem, solved by not using any reserved space for documents and settings on the USB disk (choose "discarded on shutdown, unless you save them elsewhwere").

---

### Post by eduardoq on 2009-11-02
Thanks, choose "discarded on shutdown, unless you save them elsewhwere" solved my problem too.

---

### Post by Goofy_2 on 2009-11-03
Thanks Revelate, after recreating the USB-drive with "discarded on shutdown, etc." UNR 9.10 could be started up normally. :D

---

### Post by Comodidit on 2009-11-08
> **Revelate said:**
> I had the same problem, solved by not using any reserved space for documents and settings on the USB disk (choose "discarded on shutdown, unless you save them elsewhwere").

Thanks a million. Worked perfectly for me.

---

### Post by SeyelentEco on 2009-12-05
Awesome.  This worked perfectly.  Maybe they should put this into the instructions! :-P

---

### Post by ScionofJudah on 2010-01-11
Never mind.

---

### Post by xoltrix2000 on 2010-01-20
Yeah but what if you want to save stuff on the USB? Can we still do that?

---

### Post by aka_zedweb on 2010-01-27
Recreated USB drive with the option to discard and behavior changed a bit, after white ubuntu logo it went to blank black screen, now my acer aspire one ZG5 keeps blinking disk acticity led still with white ubuntu logo on screen and no activity on usb drive.
Any thoughts?

---

### Post by audichris on 2010-01-27
thanks revelate.... worked like a charm on acer aspire one netbook.

---

### Post by syncopated on 2010-04-30
On an HP mini 210 1080sf, installing Ubuntu netbook remix from a USB memory stick,
I was able to boot from USB to the "installer boot menu" but the machine would lock up when I launched the install. 

The problem was solved by recreating the USB drive with "discarded on shutdown". 
It was also necessary to boot with help -> special machines -> "live-install vga=771 noapic nolapic"

Thanks for the information.

---

