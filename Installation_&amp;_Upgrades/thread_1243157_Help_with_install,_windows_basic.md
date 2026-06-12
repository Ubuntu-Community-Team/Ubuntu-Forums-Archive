---
title: "Help with install, windows basic"
date: 2009-08-18
forum: Installation &amp; Upgrades
---

### Post by moobie1992 on 2009-08-18
I just installed ubuntu 8.04 on my acer aspire 5515 laptop. I installed it inside windows since I want to keep Windows Vista Basic. I rebooted my laptop when prompted and hit F10 to get in the boot menu, but when I got there the only choice was to boot to vista. Can anyone help me with this? If you have anymore questions post them on here.

---

### Post by riazrahaman on 2009-08-18
When you say installed inside windows, what are you trying to say?

Install in windows that is in virtual machine of installed using wubi or created a seperate partition for ubuntu?

Install easybcd software in windows and check the windows partition manager.

---

### Post by BCPlanner on 2009-08-18
** Ubu installed OK by loading CD, running trial and then allowing the trial to be installed.  **
 
When the Ubu 9.04 CD is recognized it offers installation into Vista AS IF Ubu was a Vista app. The caveat is that (according to the CD info) there is some degradation of disk functions. 
 
MY problem is
Have new Toshiba Satellite (notebook nee laptop) L355 with Vista Home Basic.
Have 9.04 CD
Partitioned (using Vista "shrink") "C" to create "E" for Ubu (lousy MS help-less info lacks some steps)
Inserted Ubu CD and rebooted - back into Vista.
PROBLEM 1: I can't seem to convince Vista to load from the Ubu CD (I tried the F10/F12 "access bios" but apparently not successfully)
PROBLEM 2: In adding "E" drive I did **NOT** format same (e.g., as a Windows drive) - correct or do I need to go back and format drive (and what option to use??)?
 
I (may) need Vista for some drivers (I have some old stuff that Ubu may recognize, but perhaps not, and a Cisco/Linksys wireless router that works fine with Windows XP and Vista, so it's a "CYA" issue.
 
Any/All help from someone who's "been there/done that" will be MOST appreciated.
 
BCPlanner @ gmail dot com

---

### Post by moobie1992 on 2009-08-18
What i mean by installed inside windows is, I clicked the opition to install inside windows when I put the cd in. So I installed it by creating a partition.

---

### Post by presence1960 on 2009-08-18
> **moobie1992 said:**
> What i mean by installed inside windows is, I clicked the opition to install inside windows when I put the cd in. So I installed it by creating a partition.

is [this]("https://help.ubuntu.com/community/Wubi") what you did? if so that is not a partition that is wubi - installed inside of windows. In either case you don't need to hit F10 to boot. if you used wubi you will get a choice from the windows bootloader (see #10 on that link) to use either Vista or Ubuntu. if you shrunk Vista's partition to create space for Ubuntu you will get a GRUB menu with choices to choose Ubuntu or vista. Either method will not require you to hit F10.

---

### Post by presence1960 on 2009-08-18
> **riazrahaman said:**
> When you say installed inside windows, what are you trying to say?

Install in windows that is in virtual machine of installed using wubi or created a seperate partition for ubuntu?

Install easybcd software in windows and check the windows partition manager.

Stay away from Easy BCD. GRUB is more versatile and easy to configure to boot multiple OSs. IMO Easy BCD is for those who want to use Linux but don't want to learn how to use it or don't want to take the time to learn it.

---

### Post by riazrahaman on 2009-08-19
I could see 2 ubuntu entries in the windows bootloader after upgrade from 8.10 to 9.04. ( ubuntu running using wubi )
The easy way to fix that was using easy bcd.

Is there a way of editing windows bootloader from Linux? 

For those with seperate partition for Ubuntu the ideal way is to configure the grub from command line but not a possibility for those who run Ubuntu using Wubi since the first level entry is in the windows bootloader.

For your question, if you installed ubuntu in windows check if you see ubuntu folder in c:. In that case there is no need to resize the c drive and create a e drive.

To load Ubuntu from cd you have to change the first boot device to cd in bios. Try pressing del key on restart, this should enter into bios or check with the your laptop manual for the key to enter into bios

---

### Post by joaquinx on 2009-08-19
I am surprised that the gurus don't know of the "install inside windows option". This is the option that I have used without success. No boot menu on restart. Apparently wusi can not modify the boot. Is there any way to get a boot menu to boot to an "install inside windows option"?

Ubuntu 9.04 64 bit, Windows Vista

---

### Post by riazrahaman on 2009-08-19
are you referring to [http://blogs.zdnet.com/hardware/?p=1570&tag=nl.e622](http://blogs.zdnet.com/hardware/?p=1570&tag=nl.e622)

"Install in windows" uses wubi. The screenshots that you see if wubi installer. Open your ubuntu cd and search for wubi.exe

Regarding your bootloader I have already mentioned about easybcd that will show your windows bootloader options.

---

### Post by joaquinx on 2009-08-19
I have already ran wubi.exe to make the install. My problem in the Microsoft Boot Loader. It doesn't come up when I reboot. Do I have to use EasyBCD to modify the boot loader? Why would this be necessary? Can't wubi do the job?

---

### Post by presence1960 on 2009-08-19
> **joaquinx said:**
> I am surprised that the gurus don't know of the "install inside windows option". This is the option that I have used without success. No boot menu on restart. Apparently wusi can not modify the boot. Is there any way to get a boot menu to boot to an "install inside windows option"?

Ubuntu 9.04 64 bit, Windows Vista

Wubi is not meant to be a permanent install or solution. It is meant to be a trial without partitioning your hard disk. Wubi is also subject to to performance degradation due to windows filesystem fragmentation. See [here]("https://help.ubuntu.com/community/Wubi") for more info on what I say.

---

### Post by joaquinx on 2009-08-19
> **presence1960 said:**
> Wubi is not meant to be a permanent install or solution. It is meant to be a trial without partitioning your hard disk. Wubi is also subject to to performance degradation due to windows filesystem fragmentation. See [here]("https://help.ubuntu.com/community/Wubi") for more info on what I say.
 
I know this. This not the question that I asked. I want a "trail" installation. My concern is that I can not get it to boot. Can you address this problem?

---

### Post by presence1960 on 2009-08-19
> **joaquinx said:**
> I know this. This not the question that I asked. I want a "trail" installation. My concern is that I can not get it to boot. Can you address this problem?

I was responding to the part where you typed > I am surprised that the gurus don't know of the "install inside windows option". 

I don't know a whole lot about wubi. I installed it for a look see a few months back but then I uninstalled it as I already had a dedicated multi-boot installation.

---

### Post by raymondh on 2009-08-19
> **joaquinx said:**
> I know this. This not the question that I asked. I want a "trail" installation. My concern is that I can not get it to boot. Can you address this problem?

Hi,

Have you browsed thru the [wubiguide]("https://wiki.ubuntu.com/WubiGuide#Cannot%20boot%20into%20Ubuntu") and the troubleshooting section?

---

### Post by riazrahaman on 2009-08-19
It might be possible that wubi has not done itz job!

Checking the boot loader does no harm right? You could have tried it before replying back to the thread.

Also you do you see a ubuntu folder in c drive?

---

### Post by riazrahaman on 2009-08-20
wubi should have updated your windows bootloader.

EasyBCD is read your bootloader inorder to check if something has gone wrong.

BTW do you have admin privilige in the login that you are using to install ubuntu in windows?

---

### Post by riazrahaman on 2009-08-20
not sure why but my previous post got missed out.

This might be a dumb question since every windows user has admin access, "Do you have admin privilige for the user account that you are using for installing ubuntu?

---

