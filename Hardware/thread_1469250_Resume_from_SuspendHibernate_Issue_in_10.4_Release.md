---
title: "Resume from Suspend/Hibernate Issue in 10.4 Release"
date: 2010-05-02
forum: Hardware
---

### Post by Remwen on 2010-05-02
I installed the 32-bit Lucid Lynx release on my Dell Inspiron 1501 a couple days ago. Using the open source drivers, everything works nicely except resume from suspend/hibernate; I get to a black screen and can't get to GDM at all, forcing a manual reboot. My card, a Radeon Xpress 1150, is only legacy supported by ATI at this point, so the proprietary driver is no longer a viable option. Using the s2ram/s2disk program(I currently forget the name, but it is a common solution to my problem) results in a black backlit screen with a blinking cursor.

---

### Post by LJarvis on 2010-05-08
Im experiencing the same issue on my inspiron 9200. I think the issue stems from the (lack of) support for my mobility radeon 9700 gfx card. Has there been any fixes for this issue? Im really enjoying lucid but if I cant suspend my laptop, im going to have to return to karmic...

---

### Post by Killerah on 2010-05-09
I have the same computer (Inspiron 1501) and I'd just like to chime in and say that I have the same problem. I can't resume from suspend all the time and it's really really annoying. I have Arch installed on a separate partition and the suspend doesn't work there either. I have Vista installed on another partition where suspend works flawlessly.

Everything else in Ubuntu 10.04 is fantastic, I absolutely love it, but this suspend issue is driving me insane. It's so annoying to suspend my computer, put it in my backpack, get to class and open up the lid not known if it'll resume from suspend properly or not this time. I haven't tried uspsusp yet, but if it didn't work for you it probably won't work for me (I might try it anyway though).

Why can't linux have decent working suspend support? It's very frustrating. It's really the only thing that doesn't work perfectly on my laptop, but it's extremely important to me. If someone knows of a way to get suspend going correctly I'd love to hear it.

EDIT: Tried uspsusp and it didn't work. It actually took longer and then ultimately still crashed. Oi.

---

### Post by /Michael/ on 2010-05-10
I had ArchLinux installed on my Lenovo S10 netbook with an Intel graphic chip. Did you once try to boot in console mode with the kernel option "nomodeset" ? Search the Arch Wiki, also for Kernel Mode Setting (KMS). With Ubuntu 10.4 UNR, things seems to be (at least for me) more complicated (see [https://bugs.launchpad.net/ubuntu/+s...ux/+bug/568711]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/568711")). At the moment, I can "pm-suspend" from console without problems (there was a kernel update some days ago that could have had some positive effects).

---

### Post by koymack on 2010-05-10
I upgraded from 9.10 to 10.04... At first SUSPEND/RESUME works great(and resumes fast)... after several usage I experienced the BLACK SCREEN... so far nobody has posted any support or solution about this that RESOLVED this issue... i'm just using HYBERNATE as of now, its slower but does the job well... 

I'm using a VAIO VGN-SR35G with INTEL 4500M video card....

---

### Post by pmos69 on 2010-05-10
File a bug report or mark one as affecting you.
Here's one I filed: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/568711](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/568711)

Someone reported purging grub2 and reverting to grub-legacy as a workaround.

---

### Post by anachoret on 2010-05-15
> **koymack said:**
> I upgraded from 9.10 to 10.04... At first SUSPEND/RESUME works great(and resumes fast)... after several usage I experienced the BLACK SCREEN... 

I found the topic that help me "resolve" the issue with suspend/hibernate:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/568711](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/568711)

---

### Post by StuartN on 2010-05-15
> **anachoret said:**
> I found the topic that help me "resolve" the issue with suspend/hibernate:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/568711](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/568711)

What steps from that bug report helped you resolve the suspend and resume issue?

---

### Post by anachoret on 2010-05-15
> **StuartN said:**
> What steps from that bug report helped you resolve the suspend and resume issue?
Do suspend/hibernate without mounted SD-card.

---

### Post by elitenoobboy on 2010-05-22
suspend with karmic on my inspiron 1501 worked all the time, but it is broken on lucid.

---

### Post by StuartN on 2010-05-22
> **elitenoobboy said:**
> suspend with karmic on my inspiron 1501 worked all the time, but it is broken on lucid.

Have you tried the mainline kernel fix for the freeze issue? Follow [https://wiki.ubuntu.com/KernelTeam/MainlineBuilds](https://wiki.ubuntu.com/KernelTeam/MainlineBuilds) to try it. Suspend and resume are working fine on my Dell Inspiron 1501 since applying this fix.

---

### Post by timosha on 2010-05-22
It worked fine in Lucid for a couple of weeks on my Thinkpad R51.

Since two days I can only suspend once. That, means after a first suspend (after boot) resume works fine. All next suspends fail with a blinking moon led and a power off/power on cycle is the only way to get things working again.

A very funny bug indeed.

---

### Post by elitenoobboy on 2010-05-22
> **StuartN said:**
> Have you tried the mainline kernel fix for the freeze issue? Follow [https://wiki.ubuntu.com/KernelTeam/MainlineBuilds](https://wiki.ubuntu.com/KernelTeam/MainlineBuilds) to try it. Suspend and resume are working fine on my Dell Inspiron 1501 since applying this fix.

I tried 33 when it first came out, but that did not solve the problem, and wireless was broken in that build. I am assuming 34 fixed it? Also, have you encountered colored vertical bars on bootup with lucid as well? That one forced me to put radeon.modeset=0 option on grub to be able to get it to boot up.

---

### Post by StuartN on 2010-05-22
> **elitenoobboy said:**
> I tried 33 when it first came out, but that did not solve the problem, and wireless was broken in that build. I am assuming 34 fixed it? Also, have you encountered colored vertical bars on bootup with lucid as well? That one forced me to put radeon.modeset=0 option on grub to be able to get it to boot up.

2.6.34-lucid is working absolutely fine for me. I also tried one of the 2.6.33 release candidates some weeks ago and did not have wireless or a stable system, and I have had a variety of static and strobing bars, depending on when the graphics initialization is interrupted. I now have wireless and stability.

These are the links for installing:
[https://wiki.ubuntu.com/KernelTeam/MainlineBuilds](https://wiki.ubuntu.com/KernelTeam/MainlineBuilds)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/)

Ubuntu 9.10 Karmic (on a different machine) is still a problem - kernel v2.6.34-rc2-karmic is not suspending, rc3 is incomplete. I am considering trying 2.6.33 (which does not seem specifically Lucid or Karmic). EDIT: kernel 2.6.33 from [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33/) is working fine in Ubuntu 9.10 Karmic.

---

### Post by elitenoobboy on 2010-05-22
> **StuartN said:**
> 2.6.34-lucid is working absolutely fine for me. I also tried one of the 2.6.33 release candidates some weeks ago and did not have wireless or a stable system, and I have had a variety of static and strobing bars, depending on when the graphics initialization is interrupted. I now have wireless and stability.

These are the links for installing:
[https://wiki.ubuntu.com/KernelTeam/MainlineBuilds](https://wiki.ubuntu.com/KernelTeam/MainlineBuilds)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/)


Just tried the 34 on a new install, and suspend is still broken. Wireless is also broken on that. Are you using the sta or the b43 (or whatever number that was) wireless driver? I've had trouble with the latter in the past, so I've been sticking with the sta wireless driver. I think that is proprietary one.

---

### Post by Tingvan on 2010-05-23
My computer works fine except frozen touchpad after resume from suspend in 10.4 release. Is there any solutions?

---

### Post by StuartN on 2010-05-23
> **elitenoobboy said:**
> Are you using the sta or the b43 (or whatever number that was) wireless driver?

I am using b43-fwcutter and it works fine - I also had problems with it in the past. The bcmwl-kernel-source driver causes some failure with the mainline kernels.

I have identical Inspiron 1501 laptops with Lucid 10.4 using kernel 2.6.34-lucid and Karmic 9.10 using kernel 2.6.33 and they are running absolutely fine, after a few months of serious annoyance.

---

### Post by yurkie on 2010-05-23
> **anachoret said:**
> Do suspend/hibernate without mounted SD-card.


Sir you fixed my suspend issue. I have a bad habit of leaving the SD card for my digital camera inserted. Took it out of the slot....closed the lid...waited a minute opened lid. Came out of suspend perfect. 

I have a Dell Vostro A860

I too was very frustrated. Suspend worked when I first installed 10.04, then stopped working.(was leaving SD card in) It had always worked with my previous install of 9.04

**Thanks a million!**

---

### Post by elitenoobboy on 2010-05-23
> **StuartN said:**
> I am using b43-fwcutter and it works fine - I also had problems with it in the past. The bcmwl-kernel-source driver causes some failure with the mainline kernels.

I have identical Inspiron 1501 laptops with Lucid 10.4 using kernel 2.6.34-lucid and Karmic 9.10 using kernel 2.6.33 and they are running absolutely fine, after a few months of serious annoyance.

Switching to b43 fixed the wireless, although suspend is still broke. Maybe it is differing bios versions that are causing the problem? Assuming that all 1501s have the same motherboard, what bios version are you running on your 1501s? I am using Bios version 2.4.1

---

### Post by StuartN on 2010-05-23
> **elitenoobboy said:**
> Switching to b43 fixed the wireless, although suspend is still broke. Maybe it is differing bios versions that are causing the problem? Assuming that all 1501s have the same motherboard, what bios version are you running on your 1501s? I am using Bios version 2.4.1

According to **sudo dmidecode -s bios-version** I have bios version 2.6.3, which unfortunately I think is still most easily a Windows or DOS install. It is at [http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R174470&SystemID=INS_PNT_1501&servicetag=&os=WW1&osl=en&deviceid=13120&devlib=0&typecnt=0&vercnt=9&catid=-1&impid=-1&formatcnt=0&libid=1&typeid=-1&dateid=-1&formatid=-1&source=-1&fileid=236967](http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R174470&SystemID=INS_PNT_1501&servicetag=&os=WW1&osl=en&deviceid=13120&devlib=0&typecnt=0&vercnt=9&catid=-1&impid=-1&formatcnt=0&libid=1&typeid=-1&dateid=-1&formatid=-1&source=-1&fileid=236967)

But also I have Compiz disabled (Visual Effects set to None), samba file sharing installed to prevent a silly .xsession-errors message, screensaver set to Pictures Folder and no SD Cards, CD/DVDs or USB devices mounted. All these seem to help - full notes at [http://www.iol.ie/~stuartneilson/Bootup_fsck.html](http://www.iol.ie/~stuartneilson/Bootup_fsck.html)

Incidentally, I also did a clean up yesterday and disabled startup of Bluetooth Manager, Evolution Alarm Notifier, Gnome Login Sound, Remote Desktop, Ubuntu One and Visual Assistance for a massive whack of extra memory, and set my fstab to relatime on both / and /home for (significantly) faster disk read access.

---

### Post by timosha on 2010-05-23
I am getting a bit tired about this suspend/hibernate issue in Ubuntu !

It doesn't work, then it works, then it doesn't work again, then it works again and then there is another so called "update" and it doesn't work again :confused:
Suspend/hibernate is an elementary function for every laptop. Again, I getting a bit upset about this fix-break-fix-break-fix-break cycle.

---

### Post by elitenoobboy on 2010-05-25
> **StuartN said:**
> According to **sudo dmidecode -s bios-version** I have bios version 2.6.3, which unfortunately I think is still most easily a Windows or DOS install.

I tried updating the bios a while back, but it would not work at all on win7, even when using xp compatibility mode, so I ignored it for a while. It finally updated when I got around to putting xp on there. 

After updating to the most recent bios, suspend seems to be working again, so updating the bios was worth all the trouble of installing xp. I have only tried it a couple of times, but it is still better than not working at all as it was before. This is with the 34 version kernel; I haven't tried the 32 that come with lucid, but I would assume that it wouldn't work.

---

### Post by bruxxist on 2010-05-28
> **Remwen said:**
> I installed the 32-bit Lucid Lynx release on my Dell Inspiron 1501 a couple days ago. Using the open source drivers, everything works nicely except resume from suspend/hibernate; I get to a black screen and can't get to GDM at all, forcing a manual reboot. My card, a Radeon Xpress 1150, is only legacy supported by ATI at this point, so the proprietary driver is no longer a viable option. Using the s2ram/s2disk program(I currently forget the name, but it is a common solution to my problem) results in a black backlit screen with a blinking cursor.


I have a Dell Latitude D600 with the EXACT same problem. are there any solutions to this problem? I am a Linux newb so if you tell me to type stuff into a terminal i need detailed instructions.

---

### Post by elitenoobboy on 2010-05-28
> **bruxxist said:**
> I have a Dell Latitude D600 with the EXACT same problem. are there any solutions to this problem? I am a Linux newb so if you tell me to type stuff into a terminal i need detailed instructions.

Considering that a bios update fixed my problem, I'd make sure the bios is up to date before anything else.

---

### Post by bruxxist on 2010-05-29
just updated my BIOS and this didnt work. The BIOS upgrade description did say there was an issue with resuming from suspend that it fixed so i had high hopes but the same thing is happening. I can hit ctrl+alt+f7 to get sign in window back but I would rather not have to do this every time I close the lid. hopefully they fix this bug.

oh by the way you can install a new bios from a windows .exe file by burning a FreeDos image to a CD and putting the .exe file on a thumbdrive.

follow these instructions:[URL="http://liquidat.wordpress.com/2007/05/20/howto-update-bios-on-linux/"]http://liquidat.wordpress.com/2007/05/20/howto-update-bios-on-linux/
[/URL]

---

### Post by elitenoobboy on 2010-05-29
> **bruxxist said:**
> just updated my BIOS and this didnt work. The BIOS upgrade description did say there was an issue with resuming from suspend that it fixed so i had high hopes but the same thing is happening. I can hit ctrl+alt+f7 to get sign in window back but I would rather not have to do this every time I close the lid. hopefully they fix this bug.


Try upgrading to a newer kernel: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/)
If you have 32 bit ubuntu installed, just download the four packages that say i386.deb and all.deb at the end, and install those. The newer kernel seems to have fixed the problem some people.

---

### Post by bruxxist on 2010-05-29
> **elitenoobboy said:**
> Try upgrading to a newer kernel: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.34-lucid/")
If you have 32 bit ubuntu installed, just download the four packages that say i386.deb and all.deb at the end, and install those. The newer kernel seems to have fixed the problem some people.

THANKS! Kernel updates works for the Dell Latitude D600. Came back from suspend just fine.

---

### Post by grapedaddy on 2010-05-29
I don't know what I may have done differently than you, but on my Dell Latitude D600, updating to the latest mainline kernel AND updating BIOS from A12 to A16 didn't help my crash on resume issue.

---

### Post by bruxxist on 2010-05-31
> **grapedaddy said:**
> I don't know what I may have done differently than you, but on my Dell Latitude D600, updating to the latest mainline kernel AND updating BIOS from A12 to A16 didn't help my crash on resume issue.

I tried one thing to fix this problem that didnt work but perhaps it affected my system.

from: [URL="http://ubuntuforums.org/showthread.php?p=9369766#post9369766"]http://ubuntuforums.org/showthread.php?p=9369766#post9369766
[/URL][B]
1. Go to System -> Preferences -> Appearance
2. Choose Tab "Visual Effects" 
3. Make sure option "None" is chosen, if not choose it
4. Change to "Extra", this makes the system searching for drivers  automatically
5. Change back to the configuration you prefer[/B]

---

### Post by thierry.machet on 2010-06-13
I discovered that the problem is related to the modules intel_agp and nouveau in relation to my chipset.   Installing NVidia proprietary drivers did not solve the problem at first because I was doing it the wrong way.   The remedy is quite simple: install NVidia driver, have it use its agp own driver, blacklist intel_agp and associated drivers.   Though simple, the complete precise steps is much too long to post it hear.   I wrote a 14 pages procedure you can read at url [http://thierrymachet.lescigales.org/...ep-suspend.php](http://thierrymachet.lescigales.org/...ep-suspend.php)  Sorry it is in French. In need some 4 hours to traduce it in English, witch I will do if you find it useful for the community, let me know.

---

### Post by shiftbit on 2010-07-21
> **yurkie said:**
> Sir you fixed my suspend issue. I have a bad habit of leaving the SD card for my digital camera inserted. Took it out of the slot....closed the lid...waited a minute opened lid. Came out of suspend perfect. 

I have a Dell Vostro A860

I too was very frustrated. Suspend worked when I first installed 10.04, then stopped working.(was leaving SD card in) It had always worked with my previous install of 9.04

**Thanks a million!**



I have a Vostro 220S.  Everything so far with 10.04 works great, except resume via keyboard.  The only way I can get resume to work is hitting the power button.  However, every device does in fact come back to a working state just fine, including network connections etc. 

I am having similar trouble (see this thread) but unmounting an external USB drive and a USB hub, then suspending.  Still, resume only works when I hit the power button.

---

### Post by bruxxist on 2010-07-22
I updated my system a few weeks ago and the problem returned on my Dell. Also everytime I reboot the wireless adapter is disabled and i have to enable it by clicking the wireless bars on the top of the desktop. really annoying. Is there a way to downgrade to Ubuntu 9?

---

### Post by FredSmithWasHere on 2010-07-28
I have Ubuntu 10.04 on a Dell D600 and have the same issue with being unable to resume after going into suspend.  As for the wireless adapter issue bruxxist mentions, the wireless adapter is disabled when the computer goes into suspend.  Because the computer is unable to resume, the wireless adapter is not re-enabled.  So after rebooting, the wireless adapter is still in the "disabled" state.  If you change your preferences to only hibernate (never suspend), the wireless adapter remains enabled after waking-up.

---

### Post by Vimmander on 2010-07-28
I also have a 1501, and have found that possibly the combination of setting visual effects to "none" and using "Fn+esc" to suspend works just fine.  I am able to resume via the power button and by opening the lid.  I also tried "Fn+F1" for hibernate.  It stopped with the  screen still lit and the fans still going, so I had to potentially  damage my installation by holding the power button.  Sleep works,  hibernate is busted.

It may also be due to reinstalling and skipping the 2.6.32-23-generic kernel (I have 2.6.32-21-generic and 2.6.32-24-generic).  I *would* change my setting back to allow suspend on lid closings, but I have no idea how to recover from whatever disaster caused me to reinstall in the first place (a kernel panic, I believe) after trying to resume that way.  I can fix a corruption in Windows with the install disc, but not in Ubuntu...I just don't know how

---

### Post by StuartN on 2010-07-29
> **GrogTheDreamer said:**
> I also have a 1501, and have found that possibly the combination of setting visual effects to "none" and using "Fn+esc" to suspend works just fine.

I have a couple of Dell Inspiron 1501s. Kernel 2.6.34 from the mainline repository has been fine, with the exception that resume fails if an SD card is still mounted.

I have tested each new release of 2.6.32 and all freeze and fail to suspend / resume.

---

