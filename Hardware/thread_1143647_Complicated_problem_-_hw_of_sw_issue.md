---
title: "Complicated problem - hw of sw issue"
date: 2009-04-30
forum: Hardware
---

### Post by Nicolas19 on 2009-04-30
Hi to all!

My problem is really complicated, and only partly Ubuntu-related, however you guys have been really helpful here, so I hoped someone might have a clue.

First, my specs: ASUS X53SR (F3SR), Intel Core2Duo T7250 2GHz, 2GB ram, 160GB Seagate SATA st9160821as HDD, ATI Mobility Radeon HD2400 GPU. Two OSs: Ubuntu 9.04 (ext4, 32bit) and WinXPSP3.

Months ago, under oem Vista, I started experiencing sudden shutdowns. There was mostly a click coming from the HDD, then the shutdown. Sometimes a click without shutdown, or shutdown without click infrequently. I reinstalled Vista, the problem persisted, changed to XP, the shutdowns remained the same. On ASUS forums they said it was overheating, and the built-in vista diagnostics confirmed ("system shutdown due to graphics card overheating"). However, shutdowns ocurred under no (aero turned off) and heavy load all the same. Sometimes just after login, everything cool. Did HDD, memory diagnostics, they returned no error. Upgraded BIOS, nothing changed.

I took my notebook to the official Asus service, as it was still under warranty, where they sat on it for two months, then returned it to me, claiming that it was cleaned and the cooling fan has been replaced, all working fine. The machine shut itself down after 5 minutes. I was outraged at this negligent "support", so I went to another shop, breaking the warranty. There, they also sat on it for a month, first saying that it was HDD problem. They changed it, but the problem remained the same. So, they gave up, saying that it was a motherboard issue, and I should just buy another. Oh, one last thing... they silently replaced my 2GB ram to 1GB. Nice, huh? I went back, complaining, so I've got the memory back, but after this little scheme, I'm a little reluctant to believe anything they've said.

Finally, "if you want something done right, do it yourself". I've installed Ubuntu, and not a single shutdown ever since. I've also installed XP (I'd like to play some games, like TDU, and couldn't get them working under Wine), and the shutdowns returned. So, I'm starting to believe, it's not a hw issue. Also note, that I haven't experienced a single shutdown in Windows safe mode either, however, I didn't do really extensive testing there.

For the first time, I installed Ubuntu to ext3 partition, worked fine. But as a complete Linux newbie, I managed to srew it up, so formatted it, and installed this time to ext4. I have the freezing problem discussed in other threads ever since, so I can't get it running for more than 10-15 minutes. But it's a common problem. I'm writing this from Ubuntu LiveCD, no freezes yet. I just want a stable OS and if possible, to know, what the hell is wrong with my beloved notebook.

What is you advice? Install Ubuntu 8.10 (which is stable) and pray for the best? I really like Ubuntu, if it were not for TDU, that'd be the only OS I'd use. Hope the freezing problem gets resolved in an update, so I can continue using this marvelous 9.04. Sorry for the long post, and thanks for your help in advance!

Miklós

---

### Post by ahbart on 2009-05-04
I suggest you reinstall Jaunty. It is pretty stable here and try the ext3 filesystem instead. Maybe that was the cause of the freezing problem. 
In Windows: It sounds like a driver problem to me. I've seen some weird White Screens of Dead on windows on a notebook with an amd Turion and ATI grafic card. Installing of the [RMClock utility](http://cpu.rightmark.org/download.shtml) fixed that problem. It had something to do with powermanagement and underpowering some of hardware. Maybe that is the problem with your setup too.

---

### Post by Nicolas19 on 2009-05-04
Thanks for the reply, Ahbart! As soon as I can access my Windows, I'll try the RMClock. Power management issue also crossed my mind to a point that I thought, ACPI might be the problem (have seen various forum posts with similar issues). Changed my existing XP installation to "Standard PC", and tested Windows for about 4 hours (something that seemed impossible before, as it didn't go 10 minutes without shutdown), thinking that I solved the problem... then it shut down. The only difference was that it displayed the "Now you can shut down your computer" instead of simply unpowering the machine. After reboot, it didn't take much to have the frequent reboot back (with the little twist above), so it didn't solve the problem. Now it just freezes during the Windows logo at startup.

I re-installed Ubuntu a few days ago, and had only 4-5 freezes, which isn't much, considering my prevous experiences. Jaunty really convinces me, and as soon as this issue gets flushed out (I've filed a bugreport), it'll get the "best OS so far" award:)

---

### Post by ahbart on 2009-05-04
And there are windows virusses that are known to reboot pc's.

---

### Post by Nicolas19 on 2009-05-05
> **ahbart said:**
> I suggest you reinstall Jaunty. It is pretty stable here and try the ext3 filesystem instead. Maybe that was the cause of the freezing problem. 
In Windows: It sounds like a driver problem to me. I've seen some weird White Screens of Dead on windows on a notebook with an amd Turion and ATI grafic card. Installing of the [RMClock utility]("http://cpu.rightmark.org/download.shtml") fixed that problem. It had something to do with powermanagement and underpowering some of hardware. Maybe that is the problem with your setup too.

Well, I installed this utility. Do I have to set something up in it, it works by default? As it's options are quite ample, and I don't want to screw my pc up by playing with the voltage settings.

---

### Post by ahbart on 2009-05-05
Just an install it okay. You do net need to do any settings. 
What are the results so far?

---

### Post by Nicolas19 on 2009-05-05
Re-installed XP and then RMClock, some minutes after that, a shutdown. Now, it's on for some time, I enabled the RMClock power management scheme, and pray that it needed a reboot to work properly...

UPDATE: Nope, it didn't help. The shutdowns remain the same. Thanks for your help anyway.

---

