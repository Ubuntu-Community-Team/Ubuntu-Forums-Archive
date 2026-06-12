---
title: "Live Cd Frustrations, no install. What works?"
date: 2009-09-16
forum: Installation &amp; Upgrades
---

### Post by brian_va on 2009-09-16
Ok, by now I am no longer "new" to Linux. I started with Ubuntu one day thinking this is an answer to a prayer. I burn the 1st CD and it works in every machine but mine. Long story short, I move on to Linux Mint. Mint installs like a dream, however Mint has massive WEP & Wpa config problems, and you can't get online wireless. Getting frustrated with the zero help on this I move on to Fedora. Fedora gives me similar problems with creating an ISO through windows. So I create it through Mint, poof works like a champ. I install it and find out it's even less friendly to the wireless world. Ok, thinking maybe I did something wrong with Ubuntu. I burned it this way, I burned it that way. I even burned it through Fedora. I tried the iso, I tried the live cd. NOTHING WORKS. I'm sure Memorex loves me as I hit my 2nd container of blanks, but this is insane! 

So after a solid month of researching these Linux matters and a pile of CD's that do nothing, I have got to ask. Is there a flat out INSTALL Cd for Ubuntu? I just want a no fuss no muss Cd, it installs regardless of current OS and or config, 1st bootable drive 2nd 3rd etc. Such a thing? I need help in a big way.

---

### Post by AndyCee on 2009-09-16
What goes wrong? Do you get an error message or does nothing happen at all?

You could try the [alternate install]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate"), but if wireless is stuffed in Mint I'm not sure that vanilla Ubuntu will be better. You will have to burn the iso to a cd, or look into a liveUSB.

Is that any help?

---

### Post by pmlxuser on 2009-09-16
why don't you say what kind of machine you run and check the hardware section of the forums, i there shouldbe someone who face the same problem and they solved it

---

### Post by brian_va on 2009-09-16
> **pmlxuser said:**
> why don't you say what kind of machine you run and check the hardware section of the forums, i there shouldbe someone who face the same problem and they solved it

Well, while that is relevant, I've taken this to 3 or 4 other Linux forums. But for what it's worth, it's an MSI board, AMD 64 bit. The rest is typical.

---

### Post by brian_va on 2009-09-16
> **AndyCee said:**
> What goes wrong? Do you get an error message or does nothing happen at all?

You could try the [alternate install]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate"), but if wireless is stuffed in Mint I'm not sure that vanilla Ubuntu will be better. You will have to burn the iso to a cd, or look into a liveUSB.

Is that any help?

Hey, I appreciate that and I have looked into it, but again I'm tired of burning Cd's on various machines with the same result each time. If anyone else cares to back up the idea, then I'll go with it.

To answer your questions- nothing. Nothing happens at all. It shows up just fine when I check it, but when it gets down to booting, it gives ME the boot.

---

### Post by presence1960 on 2009-09-16
> **brian_va said:**
> Hey, I appreciate that and I have looked into it, but again I'm tired of burning Cd's on various machines with the same result each time. If anyone else cares to back up the idea, then I'll go with it.

To answer your questions- nothing. Nothing happens at all. It shows up just fine when I check it, but when it gets down to booting, it gives ME the boot.
If your CDs work in other machines the problem may be your optical drive. it may read data CDs/DVDs but fail when reading a bootable image. if your machine can boot from USB try making a bootable USB with [unetbootin]("http://unetbootin.sourceforge.net/"). Then go into BIOS and set your machine to have the USB boot first. Now boot off the USB.

---

### Post by brian_va on 2009-09-16
OK, please let me clarify. I am firm in the belief this is not a Kernel issue, it's not my machine. I can load Fedora and Mint, run them live or install, no problems there, this eliminates it as a Linux issue. In reading and researching on this matter several weeks ago after I started this switch to Linux endeavor back in July/Aug I soon discovered this was a distro matter. Trust me, I've Googled it 9 ways to Sunday before I broke down and brought my problem here, I'm not the only one with this issue. I have downloaded and burned it numerous times on 3 different machines. Again, if Mint and Fedora work, then why doesn't Ubuntu? So I have come to the conclusion if anyone knows they will be found here, because the Ubuntu crowd seems to be on top of things.

---

### Post by presence1960 on 2009-09-16
> **brian_va said:**
> OK, please let me clarify. I am firm in the belief this is not a Kernel issue, it's not my machine. I can load Fedora and Mint, run them live or install, no problems there, this eliminates it as a Linux issue. In reading and researching on this matter several weeks ago after I started this switch to Linux endeavor back in July/Aug I soon discovered this was a distro matter. Trust me, I've Googled it 9 ways to Sunday before I broke down and brought my problem here, I'm not the only one with this issue. I have downloaded and burned it numerous times on 3 different machines. Again, if Mint and Fedora work, then why doesn't Ubuntu? So I have come to the conclusion if anyone knows they will be found here, because the Ubuntu crowd seems to be on top of things.

did you try the usb install?

---

### Post by presence1960 on 2009-09-16
> **brian_va said:**
> Hey, I appreciate that and I have looked into it, but again I'm tired of burning Cd's on various machines with the same result each time. If anyone else cares to back up the idea, then I'll go with it.

To answer your questions- nothing. Nothing happens at all. It shows up just fine when I check it, but when it gets down to booting, it gives ME the boot.

First exactly what happens when you boot an ubuntu live cd? Be detailed please.

Secondly the [alternate text based installer]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate") works in practically every case where the Live CD will not. It isn't as pretty and you can't run a Live Ubuntu session but it gets the job done and actually has support for way more options than the Live CD does (such as RAID and LVM).

**You still have not posted your complete specs or given detailed info about what happens when you try to install via the Live CD. You have to help us help you!**

Do you get to the menu on the Live CD? if so choose "try ubuntu without any changes". When the desktop loads then try the install icon on the desktop.

Did you [MD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM") the iso prior to burning it as an image to disk?

---

### Post by brian_va on 2009-09-16
> **presence1960 said:**
> First exactly what happens when you boot an ubuntu live cd? Be detailed please.

Secondly the [alternate text based installer]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate") works in practically every case where the Live CD will not. It isn't as pretty and you can't run a Live Ubuntu session but it gets the job done and actually has support for way more options than the Live CD does (such as RAID and LVM).

**You still have not posted your complete specs or given detailed info about what happens when you try to install via the Live CD. You have to help us help you!**

Do you get to the menu on the Live CD? if so choose "try ubuntu without any changes". When the desktop loads then try the install icon on the desktop.

Did you [MD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM") the iso prior to burning it as an image to disk?

What happens, hmmm.. Nothing at all. I select a bootable drive in CMOS, make an attempt, zero. Go back to HD boot, restart, nothing. Just keeps launching the current OS like nothing ever happened. The only thing I haven't done is try it it from a really old Cd drive, mine are Asuse cd/burn and HP multiformat/burn(new).  Whaddya think, maybe? 

Can't deny you are too right. I have stated only that I have an MSI board and an AMD dual core/64 bit processor, Nvidia geforce 2.  I didn't bother with the rest because A: I don't recal it all, B: it's typical hardware, and like I said any other distro works. I was unfamiliar with MD5SUM until today, but it's looks like I'm getting in over head there.  However I think in reviewing your idea on the text based install, thats my option.

---

### Post by brian_va on 2009-09-16
Ok, did the alternate install cd. 1st burn turned to crap, 2nd came out clean, I'll do an attempt tonight and report back. Thank you all for your input, much appreciated.

---

