---
title: "HP ENVY - Ubuntu Boot Issues"
date: 2015-12-15
forum: Hardware
---

### Post by Dave_Antoine on 2015-12-15
I have a HP ENVY m6 Notebook (m6-p113dx). It has an AMD processor (AMD FX-8800P [Carrizo]) with Radeon R7 graphics. I'm trying to install Ubuntu 15.10 on my laptop but almost everytime I try to boot the install media the kernel either crashes or panics. The kernel errors sometime vary everytime I try to boot.  Errors include "generic protection fault", "invalid opcode" or kernel paging errors. I'm guessing it may be an issue with the graphics drivers. But, I tried adding the nomodeset/radeon.modeset option, and other acpi options but it didn't help.Also, don't know if this means anything but the 32-bit version can boot without crashing but has graphical issues.

---

### Post by deepakdeshp on 2015-12-18
Just FYI 14.04 version is LTS and has support till 2019. 
Try booting in recovery mode and booting from the working kernel , (pre-upgrade).
Please check md5 hash for accuracy of the downloaded image.

Try installing latest Kernel by chrooting to the partition if you are not able to boot from  it.
[http://www.ubuntumaniac.com/2015/11/how-to-upgrade-to-linux-kernel-43.html](http://www.ubuntumaniac.com/2015/11/how-to-upgrade-to-linux-kernel-43.html)
httpst from it://help.ubuntu.com/community/VideoDriverHowto

---

### Post by MassStash on 2016-02-03
Alright! someone else has this notebook and is trying to get ubuntu on it! So, from my research, I can only get ubuntu to boot multiple times with acpi=off and nomodeset. I've tried all acpi debug tries, and ht doesn't work, but off does, so according to ubuntu site there is a acpi table parsing error. I've spent the last 2months back and forth with HP trying to get someone to get me to an engineer, but they won't let me talk to them, and play messenger with me. So official response is "BIOS not powerful enough" which is ********, then after another 5 days of badgering, I got "it's not supported on that model." Grrrr, so I do some more research and come to find out, HP has a "we support ubuntu, machines with ubuntu preinstalled" page. On this page, is a 15-ah155nr. It is a envy, FX-8800P, blah blah same exact everything as P113DX except it has cd drive and fingerprint scanner. Soooooo I downloaded the BIOS for ah155nr, and p133dx, MD5 hashed checked em, they are the exact same file. So I installed it for shits and giggles. Didn't add anything obviously, but eh. So, this is where I'm at currently, and have yet to had to try and find who supports the ah155nr, and speak to them and see if they will help with a few tips of how that machine runs ubuntu preinstalled.....

Currently making 14.04.3 install media to see if that'll boot easier... Was trying 15.10 the whole time before. So boot no commands, get stall and entry blah blah, sometiems get cpu stall errors, sometimes get kernel panic, but the main error it stalls on is the entry one. Really hope someone can shine some light on this situation. Been dyin without ubuntu on this new machine, I'm loving this p113dx a lot. Just been some linux in my life to continue my android kernel building

---

### Post by smeagol44 on 2016-06-29
I'm sorry to necrobump a topic, really. But I need to know if anyone has any news on this, as I have the same laptop (HP ENVY M6-P113DX) and I'm having a lot of problems to install any linux distro to it. I managed to install Ubuntu (with acpi=off) but can't boot as it freezes as soon as it boots. 

Any news, please?

Again, sorry for breaking the rules. ú_ù

---

