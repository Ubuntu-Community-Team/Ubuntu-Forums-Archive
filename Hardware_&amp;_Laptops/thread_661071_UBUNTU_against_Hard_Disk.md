---
title: "UBUNTU against Hard Disk"
date: 2008-01-07
forum: Hardware &amp; Laptops
---

### Post by Logical Dream on 2008-01-07
Im prety fresh in all UBUNTU stuff, but I found some interesting research that UBUNTU has some strange power managment setting for Hard Disks , espacealy for Us , laptop users. 

1. ) 
> When switching to battery power, /etc/acpi/power.sh issues the command hdparm -B 1 to all block devices. This leads to extremely frequent load cycles. For example, my new think pad has already done well over 7000 load cycles -- in only 100 hours. That's at least one unloading per minute. Goggling for "load unload cycles notebook OR laptop" shows that most laptop drives handle up to 600,000 such cycles. As these values clearly show, this issue is of high importance and should be fixed sooner rather than later.

2. )
> 
There's a debate going on over at bugs.launchpad.net on whether it's the Ubuntu, BIOS, hard-drive manufacturer, or pick-any-player's fault, but Ubuntu (and perhaps any OS) may be dramatically shortening the life of your laptop's hard drive due to an aggressive power-saving feature / acpi bug / OS configuration. Regardless of where the fault lies or how it's fixed, you might want to take some actions now to try to prevent the damage."

3. )
> The main problem is a combination of the short spindown time, and something wanting to write out to the drive every 30 seconds or so. The main culprit could be the fact that by default, a files last access time (atime) gets updated on every read, even if that read comes from cache. So when the drive is spun down, it gets spun up even on cached reads (to write out the atime).
Add "-o noatime" to the filesystems in /etc/fstab, and that should clear up the issue.

OK, NOW , there is possibility to turn off that access time , which is basicly telling the system how many times and when did you access some fille. 

Is anybody , who knows how that can be done ?

---

### Post by Steve1961 on 2008-01-07
It should be simply a case of adding the noatime argument to the relevant line in fstab:

e.g. from:

# /dev/sdb1
UUID=ad16bbb6-c06d-4f8b-8260-f760049cd6d9 /               ext3    defaults,error=remount-ro 0 1

to

# /dev/sdb1
UUID=ad16bbb6-c06d-4f8b-8260-f760049cd6d9 /               ext3    defaults,error=remount-ro,noatime 0 1

---

### Post by Logical Dream on 2008-01-07
so, I need some lines in terminal , or How should I inplement this argument . 

Thank You for answer.

---

### Post by kendon on 2008-01-07
sudo gedit /etc/fstab

will open the fstab-file, then you can edit it. identify your hard disk partitions and add the noatime option like in the example above.

---

### Post by Logical Dream on 2008-01-07
Now is like this ,

# /dev/sda1
UUID=3854A82B54A7E9B8 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=13106D49AFDA2E49 /media/sda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1

and It should be ? ( all parameters after defaults to change?) 

Like you see There are 2 partisions , should it be change on bouth ?

---

### Post by Steve1961 on 2008-01-08
I see that both of those are windows partitions.  You can add noatime to those:

e.g. from

# /dev/sda1
UUID=3854A82B54A7E9B8 /media/sda1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1

to

# /dev/sda1
UUID=3854A82B54A7E9B8 /media/sda1 ntfs defaults,nls=utf8,umask=007,gid=46,noatime 0 1

However, your ubuntu file system is probably the most important.  It's the one mounted on / rather than /media/sda1

---

### Post by Logical Dream on 2008-01-08
Ok , great . I'm at work now , so I will try this when I get back Home . 
Thanks a lot .

---

### Post by wieman01 on 2008-01-08
Reduce load cycle by doing:

_**SOLUTION:**_
Add startup script:
```
sudo gedit /etc/init.d/local_settings
```
Make it executable:
```
sudo chmod +x /etc/init.d/local_settings
```
Now add this:
```
hdparm -B 254 /dev/sda
```
...whereas [COLOR="Red"]'sda'[/COLOR] represents your hard drive.

Create symb-link:
```
sudo ln -s /etc/init.d/local_settings /etc/rc2.d/S99local_settings
```

---

### Post by Daelyn on 2008-01-08
> **wieman01 said:**
> Reduce load cycle by doing:

_**SOLUTION:**_
Add startup script:
```
sudo gedit /etc/init.d/local_settings
```
Now add this:
```
hdparm -B 254 /dev/sda
```
...whereas [COLOR="Red"]'sda'[/COLOR] represents your hard drive.

Create symb-link:
```
sudo ln -s /etc/init.d/local_settings /etc/rc2.d/S99local_settings
```

and, don't forget
```
sudo chmod +x /etc/init.d/local_settings
``` so the script is allowed to execute :)

---

### Post by wieman01 on 2008-01-08
> **Daelyn said:**
> and, don't forget
```
sudo chmod +x /etc/init.d/local_settings
``` so the script is allowed to execute :)
Ah... yes, you're right. Thanks, mate.

---

### Post by Logical Dream on 2008-01-08
seems that this script is much serious solution than just puting noatime argument. 

I will try to find cycle reporter and than to try bouth solution and see what is hapening.

---

### Post by Logical Dream on 2008-01-08
SMART Health Status : OK 

after installation of smartmontools

I run

> sudo smartctl -a /dev/sda | grep Load_Cycle_Count

to check how fast Load_Cycle_Counter is increasing 

and 

> sudo smartctl -a /dev/sda | more


but: error Counter logging not supported

Is there other way to check this ?

---

### Post by wieman01 on 2008-01-08
> **Logical Dream said:**
> seems that this script is much serious solution than just puting noatime argument. 

I will try to find cycle reporter and than to try bouth solution and see what is hapening.
It is less serious than you might think. It actually prevents your HD from spinning down as it becomes idle. So no serious harm can be done.

---

### Post by Logical Dream on 2008-01-09
Yes , as newcomer, but everybody afraids of unknown. 
Anyway , everything set and should be working properly , tnx all for help.

---

