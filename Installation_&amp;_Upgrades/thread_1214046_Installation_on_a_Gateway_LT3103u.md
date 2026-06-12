---
title: "Installation on a Gateway LT3103u"
date: 2009-07-15
forum: Installation &amp; Upgrades
---

### Post by ste1969 on 2009-07-15
I had no problems installing Ubuntu 9.04 onto my Gateway LT3103u. WIFI did not work however. Using a wired connection, I updated everything and rebooted, still no wireless. I then installed the linux-backports-modules-2.6.28-13-generic package. After another reboot everything works fine!

---

### Post by mynameinc on 2009-07-15
> **ste1969 said:**
> I had no problems installing Ubuntu 9.04 onto my Gateway LT3103u. WIFI did not work however. Using a wired connection, I updated everything and rebooted, still no wireless. I then installed the linux-backports-modules-2.6.28-13-generic package. After another reboot everything works fine!

Including wireless?  If so, this probably needs moved to the testimonials section...

---

### Post by scudder2u on 2009-07-25
Yep, I can confirm the same.. wireless works after installing the backports module... Unfortunately, the bios doesnt support CPU scaling and the batter life is short...a bit over 2 hours for me.

---

### Post by yoshiki2 on 2009-07-26
How do i install the backports module. sorry my 1st time trying to install ubuntu

---

### Post by stryker719 on 2009-07-26
I'm going to give this a friendly 'bump'.  I just picked up my Gateway LT3103u, and can't get wireless to work.  How do I go about installing this backports module?

And also, scudder2u, is your battery life still crummy?  

Thanks!

---

### Post by mrojas73 on 2009-08-01
> **ste1969 said:**
> I had no problems installing Ubuntu 9.04 onto my Gateway LT3103u. WIFI did not work however. Using a wired connection, I updated everything and rebooted, still no wireless. I then installed the linux-backports-modules-2.6.28-13-generic package. After another reboot everything works fine!

Worked for me...thanks for posting this!:P

---

### Post by jcsteele on 2009-08-05
This worked for me - however power management was a deal killer - the machine cannot even determine when the ac adapter is plugged in....battery life is miserable.

Since I don't want to kill the machine prematurely, ubuntu will have to wait.

---

### Post by nomes on 2009-08-07
My installation went smoothly as well, with back ports but i cannot get the built in microphone to record...have all of u got the microphone working?

---

### Post by rspangler on 2009-08-09
did you install from CD or USB?  I've been trying to install and I always get dropped to busybox when trying to launch the livecd.

---

### Post by rspangler on 2009-08-16
I finally got it installed.  I had to use the alternate cd and install from network,

---

### Post by maddmike on 2009-08-18
What version did you install?  I have tried both Xubuntu 9.04 AMD64 desktop and alternate image and both drop out to a busybox shell after booting the kernel, i.e. no installation, this is the installer boot it craps out on.

Thanks,

Mike

---

### Post by jcsteele on 2009-08-18
I was using the alternative installer for 9.04.  What version is your BIOS?  I have heard some chatter about some problems in that area...  //jcs

---

### Post by maddmike on 2009-08-18
My bios version is v1.3201.  Where is there discussion about the BIOS version?  Does Gateway have an upgrade?

---

### Post by jcsteele on 2009-08-18
I am not sure exactly where I seen it - I have been googling for days to try to solve this problem, or at least find out some more information about it...perhaps on this forum, or on a launchpad bug report.

Anyways, we do have a different version...mine is v. 1.3103 and was released on 05/27/2009...

---

### Post by rspangler on 2009-08-19
I installed using Ubuntu 9.04 32 bit alternate install and my bios is 1.3201

---

### Post by naujokas on 2009-08-20
Mic works in skype with alsa 1.0.20 drivers

---

### Post by maddmike on 2009-08-21
> **rspangler said:**
> I installed using Ubuntu 9.04 32 bit alternate install and my bios is 1.3201

Yep - I figured this was a possibility because I ran into the same issue on a Compaq dc5800 Minitower that had a Core2 Duo chip.  The bad thing is that I specifically bought this machine because it had the AMD64 chip in it to run a 64-bit version of Linux and to avoid buying Intel.  :wink:

Going to try the trick I used to get Jaunty on the Compaq, which is to install a 64-bit 8.04 install like suggested previously then perform an upgrade.  I'll update the thread after my "test".  :)

---

### Post by Minimalist360 on 2009-08-23
re: power management...

Apparently [this guy]("http://www.pow.za.net/index.html") figured out how to get power management working on the Gateway LT3103u under Linux (Gentoo). He doesn't say whether he's submitted his changes, and I don't know enough about Linux to know where power management resides, but I'd imagine it's a kernel level thing. I'd love to see that incorporated into future kernels or appropriate modules, but I have no idea how to go about doing that.

So I thought I'd post the info here in case someone else can handle that.

---

### Post by jcsteele on 2009-08-24
Has anyone been experiencing wifi problems?  The connection seems to randomly drop, which requires a reboot to reconnect...similar to what this person reported:

 [http://ubuntuforums.org/showthread.php?t=1239809&highlight=lt3103u](http://ubuntuforums.org/showthread.php?t=1239809&highlight=lt3103u)

At home, the connection won't stay active overnight...when I am at various places around my area (i.e. school), the connection MIGHT last 10 minutes....very annoying.

Just curious what everyone is experiencing.

---

### Post by Minimalist360 on 2009-08-24
I've had the same issue with wireless overnight.

---

### Post by rspangler on 2009-08-26
I got powermanagement to work on mine.  I used the 2.6.30 kernel though.  first I downloaded his dsdt source and comiled it into the .aml format.  Then I applied his powernow-k8 patch and a patch to all the kernel to load a dsdt from the initrd image.  Once I compiled and installed the kernel, I added the dsdt file to the initrd image.  I then had to install powernowd.

This is a brief description of what I had to do to get it working.

---

### Post by Prikolchik on 2009-08-30
If someone is still looking for a solution to power-management problems I've written a [How-to: Getting power management to work on Gateway LT31]("http://ubuntuforums.org/showthread.php?p=7868889").

---

### Post by yoshiki2 on 2009-11-08
Any news about this netbook? planing to buy it from best buy.. any problems with 9.10?

---

### Post by maddmike on 2009-11-08
I have not tried 9.10 myself but if I were you I would take a USB key loaded with it into BestBuy and try it on the demo model.  I know the BestBuy's in mind area don't seem to being carrying this model anymore.  Not sure if it has been dropped or what???

Good luck,

Mike

---

### Post by yoshiki2 on 2009-11-08
there's a new one.. with xp and 1 gib ram. Netbook doesn't overheat if u are watching youtube videos?

---

### Post by jcsteele on 2009-11-10
I plan on installing 9.10 sometime in the next couple of days, so I will post back here with my results.  

When I had the beta/RC installed, the wireless issues seemed to be gone, but power management remains an issue.

---

### Post by kluffinator on 2009-11-11
I've had Karmic running on mine for a while and most everything works.

Audio, microphone, webcam, wireless* are working though. 

*Wireless doesn't drop so much but, download speeds from the repositories and web seem to crawl on it when compared to other machines.

---

