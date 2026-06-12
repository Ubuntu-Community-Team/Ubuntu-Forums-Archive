---
title: "Load Cycle Count"
date: 2009-12-28
forum: Hardware
---

### Post by Mosabama on 2009-12-28
Hello Every one, I think to solve my issue I need to contact the guy who invented the HD or maybe god.

I really got tired of this. I posted about this issue alot of times with out any solution.

I have a laptop HP compaq Presario with a western digital HDD. I had overheating in that HD with a temp some times exceeded 55 and some times 60. the load cycle count didnt even move it was fixed all the time. maybe that what made it get hot but anyway. after a year of suffering and cooling pads, I decided to change the HDD to see if it would solve the issue.

I got a samsong HDD installed and the temp this time is alot better. it reached 45 maximum which is acceptable but the problem is: (take alook at this)

```

mosab@mosab-laptop:~$ sudo smartctl -a /dev/sda|grep "\(Load_Cycle_Count\|Power_On_Hours\)"
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       4
225 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       3706

```

its increasing 1000 every hour !!!! the HDD operating time is only 4 hours until now. and hdparm -B 255 or 254 is not stoping it at all, it doesnt effect the load cycle count!

Now I have 2 things to do, either find a fix for this  or  I need a list of HDD which work fine by you guys ... tell me what HDD you are using with the above command and the temp.


Please help me...

Thank you

---

### Post by Mosabama on 2009-12-28
current load cycle count :

```

mosab@mosab-laptop:~$ sudo smartctl -a /dev/sda|grep "\(Load_Cycle_Count\|Power_On_Hours\)"
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       5
225 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       4020


```

after refreshing a firefox page :

```

mosab@mosab-laptop:~$ sudo smartctl -a /dev/sda|grep "\(Load_Cycle_Count\|Power_On_Hours\)"
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       5
225 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       4031


```

:-(

---

### Post by Mosabama on 2009-12-28
look at it now! this is after 2 hours !!

```

mosab@mosab-laptop:~$ sudo smartctl -a /dev/sda|grep "\(Load_Cycle_Count\|Power_On_Hours\)" 
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       7
225 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       6022


```

---

### Post by david916 on 2010-01-04
Hi Mosabama,

Me too..Struggling for the last 2 days also, with:

Ubuntu:Karmic
MoBo:a7n8x Deluxe (i know, very old mobo..with AGP)
HDD1: seagate 320Gb (Pata)
HDD2: seagate 80Gb (Pata)
HDD3: WD800JD 80Gb (Sata1)
HDD4: WD10EADS 1TB(Sata 1 with jumper)

my concern is about my new Drive HHD4 (WD 1TB), as below:
```
david916@david916-karmic:~$ sudo smartctl -a /dev/sda|grep "\(Load_Cycle_Count\|Power_On_Hours\)"
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       26
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       873
```

I spent hours and hours, reading forums for the last 2 days, tried many things (tricks)...count is still increasing.
- Hdparm stuff (-B 254...-B 255 ) doesnt work on this drive (apm is built in the hdd firmware, it seems..)
- ACPI disable in BIOS --> no effect.
- ACPI=OFF as "Kernel option" at boot time --> no effect.
- Remove all apps like Laptopmode, pm-utils,...--> no effect.
- Mount ext4 partition (hdd4) with "defauts,noatime" option --> no effect.

PS:
The increasing rate drop a lot, once I killed conky (it was querying HDD temp or free space, so disk 'woke up" & "Sleep" again at every query..)...if it can help somebody.

Will be great to get some geeks help on this...i don t want to kill my new drive...within few weeks/months.

Thanks,
David916.

---

### Post by david916 on 2010-01-05
YES...managed to FIX IT.

I used the fantastic WDIDLE3 tools (DOS only) to Disable the timer responsible for the head parking after 8 seconds(default value for my drive model)

1] I made a usb pendrive "dos bootable" (done on xp computer, was easier for me...i am still beginner on linux).
2] Copy wdidle3.exe (V1.03) on it, also.
3] Boot karmic PC, on USB pen drive , to access DOS.
4] Run wdidle3 /r (read status) ==> feedback was 8 seconds.
5] Run wdidle3 /d (disable) ==> feedback is 62 minutes.(max value u can get..)
6] Boot on karmic...run sudo smartctl -a /dev/sda|grep "\(Load_Cycle_Count\|Power_On_Hours\)" ==> feedback was 920..
7] Wait 5 minutes, then run again sudo smartctl -a /dev/sda|grep "\(Load_Cycle_Count\|Power_On_Hours\)" ==> feedback is still 920.
8] Wait 1 hour, then run again sudo smartctl -a /dev/sda|grep "\(Load_Cycle_Count\|Power_On_Hours\)" ==> feedback is still 920.
9] Had a beer...

Hope will help someone.

---

### Post by Mosabama on 2010-02-16
is your HDD heating ? have you checked it? actually I can stop the count but it will result in HDD heating .. so I had to choose HEATING or KILLING MY HDD !!!

and I think Both will kill it lol.

---

### Post by golfindigo on 2010-09-15
> **david916 said:**
> YES...managed to FIX IT.
 
I used the fantastic WDIDLE3 tools (DOS only) to Disable the timer responsible for the head parking after 8 seconds(default value for my drive model)
 
1] I made a usb pendrive "dos bootable" (done on xp computer, was easier for me...i am still beginner on linux).
2] Copy wdidle3.exe (V1.03) on it, also.
3] Boot karmic PC, on USB pen drive , to access DOS.
4] Run wdidle3 /r (read status) ==> feedback was 8 seconds.
5] Run wdidle3 /d (disable) ==> feedback is 62 minutes.(max value u can get..)
6] Boot on karmic...run sudo smartctl -a /dev/sda|grep "\(Load_Cycle_Count\|Power_On_Hours\)" ==> feedback was 920..
7] Wait 5 minutes, then run again sudo smartctl -a /dev/sda|grep "\(Load_Cycle_Count\|Power_On_Hours\)" ==> feedback is still 920.
8] Wait 1 hour, then run again sudo smartctl -a /dev/sda|grep "\(Load_Cycle_Count\|Power_On_Hours\)" ==> feedback is still 920.
9] Had a beer...
 
Hope will help someone.
 
 
 
To completely disable the Idle3 Timer, type "wdidle3 /S[10000000000]
That is a 1 followed by 10 zeros, this disabled the timer for me, where as /D only set it to 62 minutes.
 
Other details:
- WD20EARS - 2TB
- Used Ultimate Boot CD with both wdidle3.exe and wdidle3.exe compressed as .zip then renamed to .cab placed in the /dosapps folder (to learn how to do this, search Google for "wdidle3 ultimate boot cd" for tutorials.
- Only the original Ultimate Boot CD worked, modified one gave ISOLINUX checksum error, so I booted with the original, started FreeDOS in silent mode, then switched the cd to the modified one
- Type "T:", then "cd ubcd\dosapps" the carry out the command written in the first line of this post
- You can double check by typing "wdidle3 /R"
 
Good Luck

---

