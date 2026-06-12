---
title: "Linux overheats my SSD"
date: 2017-03-29
forum: Hardware
---

### Post by thegreatcabbage on 2017-03-29
I have a laptop with a Sandisk M.2 SSD which I dual boot with Windows 10 and KDE neon, but have tried other Ubuntu flavours such as Budgie, and they all have the same problem. When booting from the SSD, its temperature keeps increasing and I'm not comfortable with it going over 50 degrees Celsius. This means that I have to manually activate maximum fan speed every 10 minutes or it jumps up to over 55 degrees, which is hardly ideal. I really like Linux but because of this issue (and a few Windows-specific programs), I am mainly confined to Windows 10, because it keeps the SSD below 50 degrees unless under a heavy load.
Is there anything that I can do to resolve this problem? Many thanks for any advice.

---

### Post by Tadaen_Sylvermane on 2017-03-29
I'd say faulty sensor or something. That is hotter than my cpu gets under load. Something is seriously wrong with either your ssd or the hardware reading the temp.Hell I can't even think of a reason an ssd would get that hot. They aren't heat machines...

---

### Post by efflandt on 2017-03-29
Not sure how you are detecting temperature of your M.2. But if you see things like this in /var/log/syslog, that is not degrees C, there is some conversion factor, but I do not know specifically what it is at the moment:```
Mar 29 15:30:58 msata512-1610 smartd[819]: Device: /dev/sdb [SAT], SMART Usage Attribute: 194 Temperature_Celsius changed from 71 to 72
```This is for mSATA SSD card in a SATA adapter, but when I did not have my hard drive in standby I seem to remember numbers like 112 at times which concerned me until I realized that it is some other units (hddtemp is not installed by default, I just installed it now to check this).```
efflandt@msata512-1610:~$ sudo hddtemp /dev/sdb
/dev/sdb: Crucial_CT512M550SSD3: 27°C
```

---

### Post by Bucky Ball on 2017-03-30
Welcome. Not sure where you're checking the temp as you don't say specifically, but easy way to check is to open 'Disks', click on the drive and it will give you a temperature along with other info about the drive.

---

### Post by thegreatcabbage on 2017-03-30
> **Tadaen_Sylvermane said:**
> I'd say faulty sensor or something. That is hotter than my cpu gets under load. Something is seriously wrong with either your ssd or the hardware reading the temp.Hell I can't even think of a reason an ssd would get that hot. They aren't heat machines...

Well, the laptop gets pretty warm in the area where I believe the SSD to be when its temperature is meant to be high (I'm not certain though), and M.2 SSDs are known to get hotter than other types. My CPU goes to over 95 degrees when it's under load, even though my laptop has pretty powerful dual fans and I can manually set them to run at maximum. It seems to have been set to start throttling at that temperature so it doesn't usually go higher than 97 degrees, haha.

> **efflandt said:**
> Not sure how you are detecting temperature of your M.2. But if you see things like this in /var/log/syslog, that is not degrees C, there is some conversion factor, but I do not know specifically what it is at the moment:```
Mar 29 15:30:58 msata512-1610 smartd[819]: Device: /dev/sdb [SAT], SMART Usage Attribute: 194 Temperature_Celsius changed from 71 to 72
```This is for mSATA SSD card in a SATA adapter, but when I did not have my hard drive in standby I seem to remember numbers like 112 at times which concerned me until I realized that it is some other units (hddtemp is not installed by default, I just installed it now to check this).```
efflandt@msata512-1610:~$ sudo hddtemp /dev/sdb
/dev/sdb: Crucial_CT512M550SSD3: 27°C
```

I've been using hddtemp to check the temperatures, and it's always given me readings for my HDD that seem sensible. When I check the temperature of the SSD straight after booting, it's similar to the temp of the SSD when booting into Windows, so I think that it's being reasonably accurate for the SSD too.

Thanks for the replies, everyone :) Another piece of info: my SSD cools down quickly when I put the laptop to sleep, so it's not like it's always reading as being over 40 degrees.

---

### Post by sudodus on 2017-03-30
You may want to browse the internet for "m2 ssd cooling" (without quotes). I checked and found some interesting links. Have a look, maybe you will find a solution for your computer.

---

### Post by paulisdead on 2017-03-31
Might try turning off atime and diratime on the filesystem if you haven't.  With those on your SSD is getting written to with every file access.  Add ,noatime,nodiratime to the options for the filesystem in your /etc/fstab like this
```

UUID=aa7c3575-02ad-4d31-b6c5-be30e1b9798e /               ext4    errors=remount-ro,noatime,nodiratime 0       1
```

---

### Post by thegreatcabbage on 2017-04-02
Thanks, I'll backup the file and try that :-)

---

### Post by thegreatcabbage on 2017-04-03
> **paulisdead said:**
> Might try turning off atime and diratime on the filesystem if you haven't.  With those on your SSD is getting written to with every file access.  Add ,noatime,nodiratime to the options for the filesystem in your /etc/fstab like this
```

UUID=aa7c3575-02ad-4d31-b6c5-be30e1b9798e /               ext4    errors=remount-ro,noatime,nodiratime 0       1
```
It seems to make a difference to the SSD temperature but I can't be sure. Anyway, I think it's an improvement :-)

---

