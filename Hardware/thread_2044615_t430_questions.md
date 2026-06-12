---
title: "t430 questions"
date: 2012-08-19
forum: Hardware
---

### Post by alecbenzer on 2012-08-19
I'm planning on picking up a Thinkpad T430 and throwing Ubuntu on it. I'd like to try out an ssd, but seeing as I'll likely end up dual-booting ubuntu and windows, a ~128G SSD that I can configure the laptop with seems a bit tight.

So I'm planning on ordering the thing from lenovo with the standard 320GB HDD as the primary drive. My question is, what SSD solution would be best? Lenovo has an option to get a 16 GB mSATA SSD. Should I use that for core OS and other important files, and just fall back on the hdd for more serious storage? Or would it be better to just only get the 320 GB HDD and buy an SSD myself and throw it in the disk drive bay? Is it hard/annoying to set up Ubuntu to work well with a micro-SSD?

---

### Post by typhoon_tip on 2012-08-20
Just my two cents: buy a normal T430 laptop with 320 GB HDD, then throw in a Seagate Momentus XT 750 (750 GB space with integrated, automatic SSD for boot), performances are fantastic, even for data. I am using it on my T400 and I am ultra-happy with it, boot in under 10 seconds. And my controller is SATA II, this thing can double speeds on SATA III !

EDIT: with Seagate HDD/SSD, install is hassle-free. Just install normally, HDD Bios will take care of putting boot files into the SSD portion of the disk. I guess it puts other files as well, very optimized. All those software that you use most frequently will end up in that section of the disk (many reads/few writes, I guess that's the way they do it !).

---

### Post by alecbenzer on 2012-08-20
Hm, why would you recommend this over a 16GB mSATA and then a normal HDD? From what I can tell, it's something like 8GB of SSD space on the Seagate? Is the additional space somehow different than standard 7200RPM hdd space?

---

### Post by typhoon_tip on 2012-08-21
Because with Momentus the SSD is managed by the HD BIOS, with a pure SSD is managed by the OS. Whether is Windows or Ubuntu, I don't care. I think SSD portion managed by the BIOS is far better than managed by the OS and having the risk of screwing up the SSD because of some wrong settings ;) Moreover, the normal part of Momentus HD is extremely faster compared to any other 7.2k RPM 2.5" drive, in my opinion.

---

### Post by BDNiner on 2012-08-21
I was looking to buy a SSD as well. I will look into this hybrid drive. It looks amazing at first glance. I was going to use this for OSX. I need to check to see whether it can fit on 8GB of space.

---

### Post by typhoon_tip on 2012-08-21
Actually it doesn't matter whether entire OS can fit in 8G or not. Nothing matters with this drive, because it can move single files to the SSD portion according to real usage, that's the biggest advantage ! Even your OS is 20G, I seriously doubt all the files will be used at boot. The BIOS of the drive will optimize the boot so that frequently used files are stored on SSD portion. In my case, part of Thunderbird and Chrome also end up in there (most frequently used app after a cold boot).

You notice this behavior by the way it boot: first 3 or 4 boots are almost normal, fast because the drive is fast, but not incredible. Then after a while, it gets down to SSD speeds. After some system update, it gets to HDD speed before returning to normal after 2~3 boots (enough for the drive to update its SSD portion).

Moreover, you never see a SSD partition in the drive. Just a plain, 750 GB drive.

---

### Post by prichard6 on 2012-08-24
Guys, I just got a T430 a couple of weeks ago and was planning of replacing the HDD with the Momentus XT 750Go that I was using with my T410. Unfortunately, the disk used in the T430 is a few milimeters thinner and therefore the Momentus does not fit inside the T430...
So do not buy one if you plan to use it with the T430. It is however an amazing drive that I would recommend for another computer.

---

