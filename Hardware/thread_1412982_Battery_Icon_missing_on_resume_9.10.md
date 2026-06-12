---
title: "Battery Icon missing on resume 9.10"
date: 2010-02-21
forum: Hardware
---

### Post by VideoRoy on 2010-02-21
I have been running 9.10 on my new HP dv4 laptop and for the most part everything is working great but I just noticed my battery icon disappears on a resume from standby.

If I change the behavior to always show the icon, it shows it is plugged in instead of being on battery on resume.

Anyone else experience this behavior?

Thanks in advance.

---

### Post by russianbandit on 2010-02-25
Came here looking for the same issue. I'm also on HP dv4t. After I restart, the icon begins working, but I usually close the lid on my laptop when I don't use it and it suspends. After suspend the battery icon does not appear when the computer is unplugged. I've noticed this issue for about a month now.

---

### Post by VideoRoy on 2010-02-27
> **russianbandit said:**
> Came here looking for the same issue. I'm also on HP dv4t. After I restart, the icon begins working, but I usually close the lid on my laptop when I don't use it and it suspends. After suspend the battery icon does not appear when the computer is unplugged. I've noticed this issue for about a month now.
Thanks for the reply.  I close my lid as well.

I was busy this week so did not have a chance to work on it but I will try a few things this weekend to see if I can get it to come back on resume.

---

### Post by VideoRoy on 2010-02-27
So far I have only proved it also disappears when plugged in.  Still trying to figure out how to restart the process and see if that helps.

---

### Post by BrockStrongo on 2010-02-27
I have experienced this problem as well, with an Acer laptop running 9.10 64bit. 
I came across a silly workaround. By running the ACPIBattery screenlet the  battery icon shows itself again. I could then close the screenlet and everything would work fine until the next reboot, then I would have to launch the screenlet again. For some reason Gnome power manager doesn't update itself until you launch this screenlet.
Cheers

---

### Post by VideoRoy on 2010-02-28
> **BrockStrongo said:**
> I have experienced this problem as well, with an Acer laptop running 9.10 64bit. 
I came across a silly workaround. By running the ACPIBattery screenlet the battery icon shows itself again. I could then close the screenlet and everything would work fine until the next reboot, then I would have to launch the screenlet again. For some reason Gnome power manager doesn't update itself until you launch this screenlet.
Cheers
 
Could you give a little more info on the screenlet?  Do you just execute ACPIBattery from a terminal prompt?  I am not running my Ubuntu setup right now so cannot check it at the moment.
 
BTW, I noticed now that the the power manager does not seem to even know I am on a device that has a battery.  When I unplugged the laptop after a resume, it does not know to dim the screen, etc.  I was wondering if it was the HAL or maybe you have told me the answer with ACPIBattery.

---

### Post by BrockStrongo on 2010-03-01
I just downloaded "screenlets" from the software center. In that app is the ACPIbattery screenlet. Sorry I should have been more specific.
   Ubuntu also has an ACPI laptop mode option that is worth checking out.
It gives you more options than gnome power manager alone.
[http://www.thinkwiki.org/wiki/Installing_Ubuntu_9.04_(Jaunty_Jackalope)_on_an_X61_Tablet#Useful_Task:_Enable_Laptop_Mode](http://www.thinkwiki.org/wiki/Installing_Ubuntu_9.04_(Jaunty_Jackalope)_on_an_X61_Tablet#Useful_Task:_Enable_Laptop_Mode)
this link is for Jaunty but seemed to work fine for Karmic as well.
here is the forum page it came from [http://ubuntuforums.org/showthread.php?t=1256557](http://ubuntuforums.org/showthread.php?t=1256557)
hopes this helps a bit.

---

### Post by VideoRoy on 2010-03-03
> **BrockStrongo said:**
> I just downloaded "screenlets" from the software center. In that app is the ACPIbattery screenlet. Sorry I should have been more specific.
   Ubuntu also has an ACPI laptop mode option that is worth checking out.
It gives you more options than gnome power manager alone.
[http://www.thinkwiki.org/wiki/Installing_Ubuntu_9.04_(Jaunty_Jackalope)_on_an_X61_Tablet#Useful_Task:_Enable_Laptop_Mode]("http://www.thinkwiki.org/wiki/Installing_Ubuntu_9.04_%28Jaunty_Jackalope%29_on_an_X61_Tablet#Useful_Task:_Enable_Laptop_Mode")
this link is for Jaunty but seemed to work fine for Karmic as well.
here is the forum page it came from [http://ubuntuforums.org/showthread.php?t=1256557](http://ubuntuforums.org/showthread.php?t=1256557)
hopes this helps a bit.

Thank you very much for your reply!  Rough week at work so I have not been able to spend much time on fun stuff but should be able to get back to over the next couple of days.

Thank you :cool:

---

