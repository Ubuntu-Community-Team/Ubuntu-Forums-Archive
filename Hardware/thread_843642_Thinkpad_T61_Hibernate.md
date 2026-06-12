---
title: "Thinkpad T61 Hibernate"
date: 2008-06-28
forum: Hardware
---

### Post by Nemmasis on 2008-06-28
I've managed to get Suspend to work by installing the correct Nvidia drivers, but Hibernate still seems to be the same as a reboot. I'm running EasyBCD to hand off from the Vista bootloader to Grub (on my Linux partition). NOt sure if this could be the cause because I haven't tried it any other way.

---

### Post by Computer Guru on 2008-06-29
EasyBCD doesn't affect the hibernation procedure since it hands off control to GRUB which then hands off the boot procedure to Ubuntu which is where the resume-from-hibernation procedure takes place.

I personally have no experience with hibernation issues so you'll have to wait a bit for someone to walk you through the various troubleshooting steps to get your thinkpad hibernating again.

---

### Post by Nemmasis on 2008-06-29
I wasn't sure how the two bootloaders on separate partitions would interact on hibernation. It resumes from the Vista bootloader, not grub so it must be hibernating wrong and shutting down completely. Thanks for explaining that.

---

### Post by wenuswilson on 2008-07-01
I have a T61 and use Ubuntu and I restart whenever I press hibernation (last time I did it anyway). I've looked around and cannot seem to find a solution so I gave up but I haven't checked [this]("http://www.thinkwiki.org/wiki/Installing_Ubuntu_8.04_(Hardy_Heron)_on_a_ThinkPad_T61") out in few weeks so there might be something of value on there.

---

### Post by canoe529 on 2008-07-01
My T61 acts a little bit differently in that when I restart after a hibernate, it essentially reboots, then loads the pre-hibernate state of the machine. I just assumed that this was default behavior as it is somewhat slow, but gives the expected results. Is yours acting like that, or is it a fresh reboot every time you come out of hibernate?

---

### Post by wenuswilson on 2008-07-02
Personally, mine is a fresh reboot -- I just avoid it and instead put it in Suspend -- works just fine for me.

---

### Post by Nemmasis on 2008-07-02
It comes back into the Thinkpad splash screen, then the windows bootloader and starts normally. It appears to go through the hibernate process (ie.the 'moon' light blinks, black screen with blinking cursor, then off) normally but doesn't see the power button to resume and restarts instead. If I check the 'Save session for future logins' box it will come back to the same state, but it isn't going right back into the Desktop like it does with suspend. I use my Thinkpad sporadically so leaving it suspended instead might leave me with a dead battery. I used hibernate a lot in Vista because it saved a lot of time when I turned it back on. Granted, Xubuntu probably boots faster than Vista resumed from hibernation, but it would be nice to get it working properly. I've also noticed that leaving the USB receiver for my wireless mouse plugged in throws some errors on shutdown/hibernate and also on startup (probably trying to boot from it), but it doesn't work any better unplugged. I checked Thinkwiki and haven't found a solution, but did cover lots of other small issues I was having.

---

### Post by mariner09 on 2008-07-02
There are some acpi tweaks on thinkwiki that may help for hibernation.  I really don't like the std kernel hibernate because it is so long to boot.  Suspend2 was a wonderful option, but I've had no luck getting it to work proper on Hardy.  

I also add acpi_sleep=s3_bios to the kernel options section in menus.list.

---

### Post by wenuswilson on 2008-07-03
> **Nemmasis said:**
>  I use my Thinkpad sporadically so leaving it suspended instead might leave me with a dead battery. I used hibernate a lot in Vista because it saved a lot of time when I turned it back on. 

Again, you're using xubuntu and I am not but I found this site helpful a week or so back on undervolting the pc -- it gave me about 15 minutes of extra battery life (I have a 9 cell, I think). Nice to have if you're in a pinch.

[http://ubuntuforums.org/showthread.php?t=786402&highlight=undervolt+t61](http://ubuntuforums.org/showthread.php?t=786402&highlight=undervolt+t61)

Ps -- don't flip over the pc to check the battery type with a disk in, it doesn't make happy noises.

---

### Post by Nemmasis on 2008-07-07
I've been playing around with some settings based on what I found in this post; [http://ubuntuforums.org/showthread.php?t=477091]("http://ubuntuforums.org/showthread.php?t=477091") and set fstab and resume to /dev/sda5 (my swap partition), instead of using the UUID. Now when it resumes it says;

kinit: name_to_dev_t(/dev/sda5)=sda5(8,5)
kinit: trying to resume from /dev/sda5
kinit: No resume image, doing normal boot

So it appears to be trying to resume normally but isn't saving the resume point properly.

---

### Post by feeshy on 2008-07-11
With the latest EnvyNG Nvidia drivers and the .fdi changes recommended here ([http://rende.se/index.php?n=Main.UbuntuHardyOnT61](http://rende.se/index.php?n=Main.UbuntuHardyOnT61)), suspend and hibernate work perfectly.  173.14.05 drivers and 2.6.24-19-generic kernel in Hardy.  Okay hibernate isn't exactly speedy and it does feature two beeps and some garbled video, but it does come back everytime which suspend didn't always do with older drivers.

Note: I'm running Ubuntu not xubuntu....

---

### Post by Spitting Crows on 2009-02-01
How did you resolve the problem with resuming the image?  I've got an ideapad and think that I must've hibernated it and then logged into my windows partition (Ubuntu doesn't like that) so now I get basically the same message about 
kinit: name_to_dev_t (/dev/......) = dev (8,6)
kinit: trying to resume from /dev/... 
kinit: no resume image doing normal boot

What was your resolution, Nemmasis?

---

