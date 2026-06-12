---
title: "ubuntu 8.10 install and &quot;time zone bug&quot;"
date: 2009-04-16
forum: Installation &amp; Upgrades
---

### Post by dubhear on 2009-04-16
Sorry to bring this up, but "ubuntu 8.10, we have a problem"

Last night when i was spreading the evangelion of ubuntu to my old lady, i noticed there is a problem in the installation from live-cd;

In the section where you can pick a time zone that you prefer to use, there seems to be a error. I don't know if the correct time zone for helsinki is GMT +2 or +3 but as long as i have lived in finland it has been gmt +2.

I just wanted to report this bug here so someone might get a nice big thank you for fixing this so, everyone does not have to go trough this...

...I use my bios settings to configure my time and and time zone configuration should be more accurate, me thinks. I'm not sure if it's just a typo or something bigger but there seemed to be a spot for a bit fixing.

ps. how hard would it be to get the installation process with a bios time without timezone configuration in the installation of ubuntu would not affect the time that is set trough bios. So after istallation, you could set the correct time zone when you go to other time zones, manually of course. 

pps. I really want to discuss about this cuz it's driving me mad every time I installed ubuntu 8.10 (or 8.04)

---

### Post by mcduck on 2009-04-16
It's GMT+3 because of daylight saving time.. ;)

Also, the traditional behavior for all Unix systems has been keeping the system clock on GMT(UTC) time and then calculating the time shown to users based on their current time zone. You can change the setting, but since the developers are trying to keep the installer as easy and simple as possible I doubt that such an option would ever become available in the installer.

Using UTC instead of local time at system level avoids many problems with clock shifts and time zone differences. I wouldn't change this unless you are dual booting with Windows (which automatically assumes that system clock uses local time, and is not able to use UTC instead).

---

### Post by dubhear on 2009-04-16
> **mcduck said:**
> It's GMT+3 because of daylight saving time.. ;)

... I wouldn't change this unless you are dual booting with Windows (which automatically assumes that system clock uses local time, and is not able to use UTC instead).

I have dual boot with windows, but mostly use it because I don't want to abandon all my favorite "designed for windows"-programs and games that i need, almost as much as air ;)

that's just what I have experienced, thank for explaining this to me.

ps. btw; i'm not going to mark this thread as solved yet... because i think there should be a button to bypass time zone configuration-step in the installation process, but that is just my opinion. and yeah, i'm one of those who never reads the manual. But now i know i should.

---

