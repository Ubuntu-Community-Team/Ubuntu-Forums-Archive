---
title: "hotplug subsystem on ASUS A6VM"
date: 2006-02-22
forum: Hardware &amp; Laptops
---

### Post by nhoca on 2006-02-22
Hi!

There's a problem about installing linux in a friend's laptop. I have this exactely problem as the asus A6VA  [http://www.ubuntuforums.org/showthread.php?t=134300&highlight=hotplug+subsystem]("http://www.ubuntuforums.org/showthread.php?t=134300&highlight=hotplug+subsystem")
but there's no option in the bios screen. Help please....:p

---

### Post by dhalgren on 2006-02-27
I have a different model asus, but had the same problem with the hotplug subsystem.  My questions is: have you disabled snd-hda-intel in the /etc/hotplug/blacklist? If you have, you should be able to boot into the system, there just won't be any sound.

If you haven't been able to boot into the system, the advice I was given was to press alt+sysreq+e to get past the hotplug hang. I did this and was then able to boot into the system and edit the hotplug/blacklist file, which then anabled me to boot into the system.

If you haven't been able to boot into X, then you might think about trying this.

Please note: I am *****not* an expert, I am merely telling you what I did. If you have any real doubts (I did ;-)) then go to the ubuntu irc help channel and ask for more help there. They are a very helpful lot of people.

After getting into x and editing the file, I messed around for almost a week trying different things to get the sound working. I finally found the following information [http://ubuntuforums.org/showthread.php?t=76307]("http://ubuntuforums.org/showthread.php?t=76307")
and did everything kbuel said, and it all came together with sound.

This may help, I hope it helps, but please be careful and make sure you have a realtek card before tyring to use their driver, and otehr simple precautions like that. Also, make sure to substitute the model number of your laptop for the model number Kbuel has written in his advice.

Hope this is of some use, and Good Luck.

cheers

---

