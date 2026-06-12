---
title: "Acer Aspire One Battery"
date: 2010-05-19
forum: Hardware
---

### Post by exod40 on 2010-05-19
Hello,

I'm running Ubuntu Netbook Remix on Acer Aspire one. I charged my netbook and it was on full battery when i started it and the battery indicator showed 100% and more than 5 hours battery power remaining. After a few minutes of using the laptop the battery indicator was red and empty and a message came to the screen that said "Battery critically low. Hibernating". This happened a few times for the past few hours. I tried to remove the battery to hibernate/turn off the computer, but this thing happens over and over. Is this hardware or software problem?

---

### Post by nickyap on 2010-06-06
Have the same problem with my Acer Aspire One and would appreciate any help on this.  Was running Windows 7 prior to installing Ubuntu and never had a battery issue.  I therefore believe it is software related.  I have however switched the option from Hibernate to Suspend when it reaches critically low power and that saves a re-boot at least.

---

### Post by foxhound6 on 2010-06-09
+1.  Running Lucid Netbook Remix on an Acer Aspire 532h.  2GB of RAM.  Netbook is 6 months old.  Did not have the issue on Jauunty.

EDIT: forgot to mention that the girlfriend has the same exact setup (with 1GB of RAM) and the same exact problem.

---

### Post by 5BallJuggler on 2010-06-09
Click on the battery icon in the top panel(its there by default, but you can move it) and then click on the first option. this is the current state of the battery.

when the Gnome power manager window opens, click on the "details" tab, this will give you info about the battery, if you scroll down to the bottom of the screen it will give you two percentage figures. The first figure is the Charge percentage, the 2nd figure is the capacity of the battery.

As the battery get older the capacity reduces through general use, if the value gets too low the battery will become unusable.

My capacity is 79%, and is causing no problems, check yours and see if it significantly lower. if so then maybe you should consider changing the battery.

---

### Post by foxhound6 on 2010-06-09
The battery is full functional for myself and my gf.  The computer turns right back on after it goes to sleep.  This also does not happen in Win7 or Jaunty I believe.

---

### Post by sailingboarder on 2010-06-10
I have a brand new Acer Aspire One 532h, it is maybe two weeks old now.
I have had this problem since the first day I bought it and installed UNR. On first boot, within the first 5 minutes, the battery will drop from whatever charge it currently has to critically low and hibernate. If I let this process go, or hard restart, when the computer returns the battery is fine, back to the charge it should have, and life can continue on. 

This is really frustrating to basically start up my computer twice before I can actually start doing work on it.

---

### Post by exod40 on 2010-06-10
> **5BallJuggler said:**
> Click on the battery icon in the top panel(its there by default, but you can move it) and then click on the first option. this is the current state of the battery.

when the Gnome power manager window opens, click on the "details" tab, this will give you info about the battery, if you scroll down to the bottom of the screen it will give you two percentage figures. The first figure is the Charge percentage, the 2nd figure is the capacity of the battery.

As the battery get older the capacity reduces through general use, if the value gets too low the battery will become unusable.

My capacity is 79%, and is causing no problems, check yours and see if it significantly lower. if so then maybe you should consider changing the battery.

My laptop was brand new when this problem started happening. Now i think i resolved it when i removed gnome-power-manager from startup list, because it caused the problems. I have installed acpi and I can look at the battery remaining time through terminal.

---

### Post by wilee-nilee on 2010-06-10
I have a aspire 250 netbook the only problem I have had was with the bios firmware, there was a bug that if you unplugged the ac the computer shutdown abruptly.

Check that you have the latest firmware and be very careful if you decide to upgrade it, really from the MS side is best.Upgrading or changing firmware can brick the computer I hear if done incorrectly. Never has happened to me but I knock on my wooden skull.

---

### Post by foxhound6 on 2010-06-11
I have the most current firmware version.  Upgraded it a few weeks ago.  Don't remember the version # off the top of my head.

---

### Post by EricBellavance on 2010-06-11
Same problem here with my acer 532h bought 2 week ago running Netbook edition 10.04

Eric

---

### Post by FearsomeOrange on 2010-06-18
> **exod40 said:**
> My laptop was brand new when this problem started happening. Now i think i resolved it when i removed gnome-power-manager from startup list, because it caused the problems. I have installed acpi and I can look at the battery remaining time through terminal.
 
 
Could you give us n00bs a step by step on how to do what you did, please?  That would be great!

---

### Post by exod40 on 2010-06-19
> **FearsomeOrange said:**
> Could you give us n00bs a step by step on how to do what you did, please?  That would be great!

First install acpi, by writing in terminal "sudo apt-get install acpi".

Then go to System - Startup Applications and find "Gnome Power Manager" or something like that and delete it (actually it should work when you just uncheck it) and reboot.

After that you won't have the battery indicator in the top right corner, but you can check your battery state with writing "acpi -V" in terminal.

---

### Post by nickyap on 2010-07-02
Found a way to turn off the Power Manager through an option available in the Startup Applications.  I went to the System tab and then launched Startup Applications.  In there, I turned off the Power Manager, which is essentially a check box.

---

### Post by ubugrrl on 2010-07-13
Same here. I have an acer aspire one 532h and have gotten the same "battery critically low - hibernating" line. I've disabled power management, so I'll see if that works.

My battery indicator also reflected lots less batter life than it did under win7 starter (not that i want that back !!).

---

### Post by libssd on 2010-07-13
AA1 D150, purchased June 2009, currently running 10.04. Absolutely no problems with year-old 6-cell or 3-cell batteries. 

In my experience, gnome power manager in 10.04 reports slightly more accurate battery life figures than earlier versions. As a previous poster reported, Li-ion battery capacity deteriorates over time, especially if you run the battery into the ground. I have my power manager settings to shutdown when the battery gets critically low.

---

### Post by Mathieup75 on 2010-07-14
I also have an Acer Aspire One 532 and I'm getting the "Battery critically low - Hibernating" issue.

Will check my Bios, but ran with Win7 for a couple of weeks and never had that issue.

It has to be something with Ubuntu right?

---

### Post by ubugrrl on 2010-07-16
Yes, seems that way. I do still get that message now and then. I have it set to suspend and not hibernate. When I get the message, I immediately click "suspend" from the shut down menu and when it comes out of suspend it's usually fine. 

Doesn't seem that anyone's found the exact cause yet.

---

### Post by turbovolkswagen on 2010-07-22
+1 i am also having this issue.  I removed the gnome power manager from startup applications, but its a bit of an annoyance to have to monitor battery usage from the terminal. 

I would be happy with even just the tray icon telling me the current level of the battery and not trying to hibernate or suspend.

---

### Post by Maximus559 on 2010-07-24
I had the same problem on my AO532h, but I think I may have found a fix:  BIOS update. If you're dual booting Ubuntu and Windows, just boot into  Windows and run the update utility provided by Acer in the downloads  section of their support site. If you're like me and are running Ubuntu  exclusively, it's a bit of a roundabout process. First, follow the  instructions [here]("http://www.bay-wolf.com/usbmemstick.htm")  to create a bootable DOS USB flash drive. Then, copy the folder  containing the DOS BIOS update utility to the flash drive. Next, simply  boot from the USB flash drive and run the batch file provided by Acer.  Hope this helps. For reference, this also fixed a warning message I'd  been receiving at boot time: "acer-wmi: Unable to detect available WMID devices".

---

### Post by MarsEvader on 2010-07-26
I have the same issue with my Packard Bell dot s2 and I can confirm that the culprit is gnome-power-manager that issues these power alert dialog boxes. I have actually downloaded the latest version of the gnome-power-manager source code for UNR 10.04 (Karmic) and modified it to suppress these warnings. Within this week I will make proper changes to allow it to work better, and rather look at the overall trend of the battery charge before issuing an alert. I won't submit this patch to Ubuntu yet but if anyone that uses Karmic, is interested I can email them the diff file or the complete source package including the changes made by myself.

---

### Post by ubugrrl on 2010-08-04
I tired this. Booted from the usb stick. But when I tried to run the  update I got a message that I couldn't run the program in DOS mode. Any  ideas?

Thanks!

oops... this was in reply to Maximus:
I had the same problem on my AO532h, but I think I may have found a fix:   BIOS update. If you're dual booting Ubuntu and Windows, just boot into   Windows and run the update utility provided by Acer in the downloads   section of their support site. If you're like me and are running Ubuntu   exclusively, it's a bit of a roundabout process. First, follow the   instructions [here]("http://www.bay-wolf.com/usbmemstick.htm")   to create a bootable DOS USB flash drive. Then, copy the folder   containing the DOS BIOS update utility to the flash drive. Next, simply   boot from the USB flash drive and run the batch file provided by Acer.   Hope this helps. For reference, this also fixed a warning message I'd   been receiving at boot time: "acer-wmi: Unable to detect available WMID  devices".

---

### Post by Maximus559 on 2010-09-09
@ubugrrl: Sorry I didn't respond sooner... haven't been to these forums in a while. Which I guess is a good, because that means I haven't been having any Ubuntu-related problems! So, you've gotten the bootable DOS USB stick to work... are you sure you're running the DOS update utility? The download from Acer contains two versions of the update program, one for DOS and one for Windows, so make sure you copy the DOS version. Also, check that [this]("http://global-download.acer.com/GDFiles/BIOS/BIOS/BIOS_Acer_1.25_A_A.zip?acerid=634139072709889300&Step1=Netbook&Step2=Aspire%20One&Step3=AO532h&OS=722&LC=en&BC=Acer&SC=PA_6") is the file you're using. The DOS version is a .bat file, if I remember correctly.

---

### Post by ynaught on 2010-10-28
> **Maximus559 said:**
> I had the same problem on my AO532h, but I think I may have found a fix:  BIOS update. If you're dual booting Ubuntu and Windows, just boot into  Windows and run the update utility provided by Acer in the downloads  section of their support site. If you're like me and are running Ubuntu  exclusively, it's a bit of a roundabout process. First, follow the  instructions [here]("http://www.bay-wolf.com/usbmemstick.htm")  to create a bootable DOS USB flash drive. Then, copy the folder  containing the DOS BIOS update utility to the flash drive. Next, simply  boot from the USB flash drive and run the batch file provided by Acer.  Hope this helps. For reference, this also fixed a warning message I'd  been receiving at boot time: "acer-wmi: Unable to detect available WMID devices".

I've had this problem since I got my AO532h, but only searched for fellow sufferers yesterday.

I updated my BIOS from 1.10 to 1.25 last night.  Since then, I've entered standby/suspend 20 or so times (trying to make it fail) and I have not seen the problem yet.  I'd say it's too soon to call it fixed but I'm cautiously optimistic at this point.

FWIW, I'd read that in order to upgrade to 2G RAM, this machine required a BIOS update....so two birds with one stone, should I ever decide the 1G isn't enough!

Thanks for the info, Maximus--will repost in a week or so if it's fixed (sooner if not).

---

### Post by MadPriest on 2010-11-01
I tried to upgrade BIOS on my AO-532h to 1.25 (the latest one) yesterday, but when getting to about 60%, the battery is reported as empty 
UNR 10.10 on AO-532h

---

### Post by ynaught on 2010-11-03
> **MadPriest said:**
> I tried to upgrade BIOS on my AO-532h to 1.25 (the latest one) yesterday, but when getting to about 60%, the battery is reported as empty 
UNR 10.10 on AO-532h

Did you succeed in upgrading your BIOS?

---

### Post by 99butcher99 on 2010-11-03
> **MadPriest said:**
> I tried to upgrade BIOS on my AO-532h to 1.25 (the latest one) yesterday, but when getting to about 60%, the battery is reported as empty 
UNR 10.10 on AO-532h


 Mine upgraded fine and it appears to have fixed the problem.   So far no more shut downs but as these were random to start with who knows?

:confused:

---

### Post by MadPriest on 2010-11-04
> **ynaught said:**
> Did you succeed in upgrading your BIOS?

indeed

> **99butcher99 said:**
> Mine upgraded fine and it appears to have fixed the problem.   So far no more shut downs but as these were random to start with who knows?

:confused:

actually, I was wrong...
the BIOS upgrade did make the difference and solved the problem
so, at least for AO-532h it is the solution.

---

### Post by ynaught on 2010-11-07
> **ynaught said:**
> I've had this problem since I got my AO532h, but only searched for fellow sufferers yesterday.

I updated my BIOS from 1.10 to 1.25 last night.  Since then, I've entered standby/suspend 20 or so times (trying to make it fail) and I have not seen the problem yet.  I'd say it's too soon to call it fixed but I'm cautiously optimistic at this point.

FWIW, I'd read that in order to upgrade to 2G RAM, this machine required a BIOS update....so two birds with one stone, should I ever decide the 1G isn't enough!

Thanks for the info, Maximus--will repost in a week or so if it's fixed (sooner if not).

I have to say it definitely seems to have been fixed--thanks again for the tip, Maximus.

---

### Post by desaivarun_104lts on 2011-02-19
Hi Friends,

I am a new user of ubuntu 10.04.I recently converted from xp to ubuntu.I am very happy with ubuntu.I am using acer aspire one 532h.Though ubuntu is rocking,i have a serious issue with the battery and SD card reader.

Regarding SD Card reader,i bought an external card reader,it is working fine.it's not a big problem.the main problem is with the battery,it takes several hours for full charging.It charges upto 67% and it stops there,never completes 100%.After 1 hour or some time the battery icon becomes red and it says,battery is critically low and need to switch on the power.I am really annopyed with this.

For this reason,i gone through google and all the ubuntu forums,i found a solution,that is to upgrade the bios to 1.25 latest  version.I tried upgrading bios with freedos,but i am unable to do it,i tried a lot.

Please,can any one tell me the detailed steps to upgrade the bios and to solve this frustating battery problem.Plese keep in mind,give me the detailed steps to upgrade the bios,as i am not a n expert computer use.The detailed steps of upgrading bios  will be usefull for several people who are facing issue like me

---

### Post by desaivarun_104lts on 2011-02-19
> **Maximus559 said:**
> @ubugrrl: Sorry I didn't respond sooner... haven't been to these forums in a while. Which I guess is a good, because that means I haven't been having any Ubuntu-related problems! So, you've gotten the bootable DOS USB stick to work... are you sure you're running the DOS update utility? The download from Acer contains two versions of the update program, one for DOS and one for Windows, so make sure you copy the DOS version. Also, check that [this]("http://global-download.acer.com/GDFiles/BIOS/BIOS/BIOS_Acer_1.25_A_A.zip?acerid=634139072709889300&Step1=Netbook&Step2=Aspire%20One&Step3=AO532h&OS=722&LC=en&BC=Acer&SC=PA_6") is the file you're using. The DOS version is a .bat file, if I remember correctly.
Hi,

I downloaded the free dos from unetboot in and added my dos bios files to the usb and booted through usb,the unetboot in asked me to install os,i selected ok,and it shown a:,i entered into c: and searched for the .bat file,everything went good,but i am uanble to execute the .bat file,please how to execute the .bat file,give me the detailed way to upgrade the bios with freedos,it will helpfull to many people who are using acer aspire one 532h..
Tahnks in advance..

---

### Post by funfrank on 2011-12-09
Hi All,

I have the BIOS 1.25 installed.

My battery charges to about 70-80% according to Ubuntu and won't go any further.  Just started doing this a month or two ago.

Any one have any suggestions?

Frank

---

