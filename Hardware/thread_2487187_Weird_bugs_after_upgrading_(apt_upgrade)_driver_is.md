---
title: "Weird bugs after upgrading (apt upgrade) driver issues"
date: 2023-05-26
forum: Hardware
---

### Post by zarosath on 2023-05-26
I dont know if i am running on damaged hardware, with a fresh install without upgrading packages seems the nvidia driver is selected and runs fine, on the settings (Details) it shows it is running my nvidia geforce rtx 3050 mobile GPU.

But i've been suffering weird bugs like apps not working as intended (Blitzmax Enet network module failing to connect localhost) but many other issues.

im running ubuntu 22.04.2.

Can you explain? like after applying changes to graphics driver and rebooting, it wont boot! i've reinstalled 10 times and with slow internet its difficult.

sorry :P point is.. what is causing the incompatibility? It seems some packages havent been tested on my system.. like when the software issues prevent me from running from my GPU and instead its utilizing intel UHD integrated graphics when i have these issues and it just wont boot.

I had to set Date & Time manually, for some reason it isnt syncing with the time zone. Ubuntu is my preferred OS

---

### Post by zarosath on 2023-05-26
Point: I CANT upgrade to the latest packages without BOOT problems and GPU issues. HOW DID THESE PACKAGES GET APPROVED?

Are there any solutions? So.. I can make a partition (Part of this began after robbing space from windows, when in windows the partition manager wouldnt do that for me because it was protecting critical files)

So.. i've since reinstalled a fresh copy of windows and used its partition manager to give back 20gb i stole from its partition.

to test upgrades.. i am really not sure of what it could be.

---

### Post by QIII on 2023-05-27
You are likely running into three issues:

1.  You appear to have a hybrid Intel/Nvidia system.  The equipment OEMs have not made this easy for Linux users.  You will likely need to blacklist your Intel graphics using your UEFI settings at the motherboard level to force the use of the Nvidia GPU.

2.  Nvidia's driver is proprietary and Canonical can do nothing to modify it to work.  On installation, without installing the proprietary package, Ubuntu will activate the black-box back engineered module.  This is likely not as capable as the proprietary driver.  Not much the Linux community can do about that, either.  The open source driver will generally work, but it will be hobbled.

3.  Nvidia has expressed no intention of supporting Wayland, which is replacing X.  Again, not much the Linux community can do.

Linus Torvalds has expressed an opinion of Nvidia that I cannot repeat here without violating our policy forbidding vulgar language.
[B][I]
Moved to Hardware[/I][/B] for that.  There are plenty of people who can give you specific advice on how to deal with the proprietary Nvidia driver.

As for your date/time setting, you are probably running into a known issue with Windows dual boots.  Please start a separate thread (in General Help) regarding that issue.  Each thread is best served by dealing with a single issue only.

Please bear in mind that this is a family- and workplace friendly forum and mind that you don't use vulgarity or profanity no matter how you might obfuscate it.

---

### Post by zarosath on 2023-05-27
if it is not my hardware gone bad, it is the software. There are nothing  wrong with proprietary drivers until i upgrade packages. so.. i assume, if it isnt windows critical files/robbing file space, then the proprietary driver isnt up to date with the packages.

---

### Post by QIII on 2023-05-27
Again -- the proprietary driver cannot be changed or modified by Canonical.  Sometimes it takes some fiddling to find just the right version of the proprietary driver.  AMD supplies an open source driver to the Linux kernel developers, so it is included and used when you install on a system with an AMD GPU.

Someone will be along to help with your Nvidia issue.  Please be patient.  Everyone here is a volunteer with a life outside of these forums, so they may not get to your issue immediately.

I commiserate with the slow connection frustration.  I live on our family farm far out in the boonies and I depend on surplus cell bandwidth.

---

### Post by zarosath on 2023-05-27
Look i have to downgrade to ubuntu 18 where iubuntu is most stable with my system  Intel/nvidia are some of the best builds but i can see your point.. perhaps next time i'll choose a amd card.

so i am having those issues again! sometimes it wont shutdown and my graphical app isnt working as intended now. I am not sure what is causing this.. so some packages were installed and/or updated when installing github-desktop from a package, it started after that and i dont know if it is the packages. I think my app isnt working as intended (as it were before this) is because the system is using the inTEL integrated graphics causing the app to behave differently.

i were able to snap a few photos, you'll have to zoom in to read them. Does anyone have insight into this?

booting up:

shutting down:

---

### Post by zarosath on 2023-05-27
Somehow it is a bios problem? I am going to install ubuntu 18 on a new partition and see if i have any issues there.. but let me know so we can maybe fix this.

---

### Post by mIk3_08 on 2023-05-27
> **zarosath said:**
> I am going to install ubuntu 18 on a new partition and see if i have any issues there.. but let me know so we can maybe fix this.
Ubuntu 18 is nearly out of support. The support schedule is only until next month. I prefer you choose the latest release. Regards and cheers

---

### Post by zarosath on 2023-05-27
its a con that it isnt the latest software But ubuntu 18 software and drivers were stable with my hardware.. is there any way to test whether these issues is the hardware or the software? as it stands windows is running without any bugs so far.

so.. i installed nvidia driver open kernel 530 proprietary (the latest driver version) onto ubuntu and after rebooting the mouse of my laptop wasnt recognized.. and a bunch of text at boot. so as my ubuntu system was disabled, im on windows downloading ubuntu 18 to give that a shot i dont understand how software could fudge a system so bad but windows is running fine. i dont know if its my hardware or the software running the hardware.

---

### Post by QIII on 2023-05-27
What con?  It is the driver. 

Nvidia grovels before Redmond.  Linux != Windows.  Nvidia spends vastly more of its resources developing their Windows driver because that is where the money is.  Microsoft, by the way, does exactly nothing to make the Nvidia drivers work.  Either Nvidia does, or the driver does not get put into the Windows driver base.

Again: Nvidia's driver is proprietary.  There's nothing anyone in Linux world can do about that.  A number of driver versions are available in the repos, but there is no guarantee Nvidia has made them work with Linux.

If you will be patient, there are those who have worked with the Nvidia drivers and should be able to help when they are able.

---

### Post by #&amp;thj^% on 2023-05-27
> **zarosath said:**
> its a con that it isnt the latest software But ubuntu 18 software and drivers were stable with my hardware.. is there any way to test whether these issues is the hardware or the software? as it stands windows is running without any bugs so far.

so.. i installed nvidia driver open kernel 530 proprietary (the latest driver version) onto ubuntu and after rebooting the mouse of my laptop wasnt recognized.. and a bunch of text at boot. so as my ubuntu system was disabled, im on windows downloading ubuntu 18 to give that a shot i dont understand how software could fudge a system so bad but windows is running fine. i dont know if its my hardware or the software running the hardware.

So what have you now? nVidia or nouveau?
Can you show me this please:
```
inxi -G
```

---

### Post by zarosath on 2023-05-27
So to be more specific, software running the hardware or damage/fault in the hardware itself.?

---

### Post by #&amp;thj^% on 2023-05-27
Most likely software running the hardware, As Qlll states it's "Again: Nvidia's driver is proprietary"
If you answer my request I may help you sort this out "But"if you want to complain I'll wait for you to finish that first. ;)

---

### Post by zarosath on 2023-05-27
yes, sorry. ;0 so as the mouse were disabled it i were limited at what i could run, just keyboard. So i tried installing Inxi and apt update but i got a bunch of errors i were not able to copy and paste.  i think i have to reinstall again.

i like nouveau but i dont know whether it has 3d acceleration/video game capability as a display driver.

Could this be related to windows critical files and partition space? i had not booted windows prior to the issues.

---

### Post by #&amp;thj^% on 2023-05-27
> **zarosath said:**
> 
i like nouveau but i dont know whether it has 3d acceleration/video game capability as a display driver.



It's very limited, but with nVidia you will enjoy your experience better.
But I agree a fresh new install would be the best suggestion ATM.
Good Luck

---

### Post by zarosath on 2023-05-28
Okay so i downloaded the ubuntu 22.04 iso to be sure that the flash drive has been flashed correctly.

i upgraded the system sudo apt upgrade.
 
No errors, my only issue is that now under settings> about it only lists the integrated UHD cpu graphics and not the graphics card. lspci | grep VGA. shows it is recognized though. I want to be sure my system is using my graphics card for game dev.

so i dont know that its using the actual card. i am going to try installing a newer driver.

---

### Post by zarosath on 2023-05-29
Running buntu 18, latest nvidia-driver-530 my system is working no errors or anything. i would bet nvidia developed the drivers for ubuntu 18. the card was released 2022 the same year i bought the laptop. Installing that driver on ubuntu 22.04 with my system causes critical errors and wouldnt boot or shut down or use the proper video device.

---

### Post by TheFu on 2023-05-30
D.A.F. needed.

Data and Facts.  Without those, nobody can help.  Facts come by running and posting the command output requested.  Until that happens, nobody can really help ... except you get to vent.

Rather than reinstalling all the time, can you run 22.04 for a day using the "Try Ubuntu" mode?  How does that work?

Next, do a fresh install, but don't install anything from nvidia.  How does that work?  Are there errors or warnings in the system log files?  Fix them.

Step by step changes are needed.  Loading 50 new things into a fresh install doesn't provide the needed separation to determine what is causing issues.  

There isn't anything to be done to "fix" nvidia drivers.  Only nvidia can fix it.  Complain to them.  It probably won't help and will just make you more frustrated.  I was using nvidia from 2005 - 2022. A few times a year, the proprietary driver would screw up the system.  This happened more since 2019 and I noticed it. 
In 2021, I got an AMD APU and was happily using it without issues.  When I upgraded the hardware in another system, I specifically got an AMD APU so I could pull the nvidia GPU out.  I have 1 system remaining with an nvidia GPU inside (430 GT).  I've been planning to retire it over 3 yrs, but haven't migrated everything it does to the other systems. Mainly it is a storage migration issue, since it has an external RAID array connected.

Nvidia hasn't just made Linux users unhappy. They've also made EVGA (a hardware manufacturer) unhappy.  [https://www.theverge.com/2022/9/16/23357031/evga-nvidia-graphics-cards-stops-making](https://www.theverge.com/2022/9/16/23357031/evga-nvidia-graphics-cards-stops-making)

Anyway, I'll be doing what I can to avoid giving nvidia any money. We each have to decide for ourselves on that matter.  I have a few companies where I strive to avoid them making money from me, as much as possible.

---

