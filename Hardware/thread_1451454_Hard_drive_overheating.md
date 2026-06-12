---
title: "Hard drive overheating"
date: 2010-04-10
forum: Hardware
---

### Post by ubik89 on 2010-04-10
I've tried Ubuntu since 2 years and every distribution is overheating my hard drive. Why?

```
ubik@Guybrush:~$ sudo hddtemp /dev/sdb
/dev/sdb: WDC WD2500BEVS-60UST0: 57°C
```Is there any solution for my problem?

CPU runs fine @ 50 °C.

I have not this problems with windows.

I'm using a HP Pavilion dv7-1110eg

---

### Post by tgm4883 on 2010-04-10
> **ubik89 said:**
> I've tried Ubuntu since 2 years and every distribution is overheating my hard drive. Why?

```
ubik@Guybrush:~$ sudo hddtemp /dev/sdb
/dev/sdb: WDC WD2500BEVS-60UST0: 57°C
```Is there any solution for my problem?

CPU runs fine @ 50 °C.

I have not this problems with windows.

I'm using a HP Pavilion dv7-1110eg

I don't see how a operating system would overheat your hard drive. Perhaps the fans are on all the time in windows or your CPU is throttleing in windows?

---

### Post by ubik89 on 2010-04-10
Well, it's not the CPU. CPU has temperature of 50°C, but hard drive has 57°C.

The fan is always on.

---

### Post by tgp1994 on 2010-04-10
> **ubik89 said:**
> Well, it's not the CPU. CPU has temperature of 50°C, but hard drive has 57°C.

The fan is always on.

Are there lots of wires surrounding the hard drive? Does it look like it would have adequate airflow?

EDIT: I also noticed the unusual three letter device name for it, do you have other devices (HDDs, CDs) surrounding the hard drive? What are their temps?

---

### Post by ubik89 on 2010-04-10
> **tgp1994 said:**
> Are there lots of wires surrounding the hard drive? Does it look like it would have adequate airflow?

Yes, it has!

> **tgp1994 said:**
> EDIT: I also noticed the unusual three letter device name for it, do you have other devices (HDDs, CDs) surrounding the hard drive? What are their temps?

There is another hdd, but not used. The temperature of this hdd is:

```
ubik@Guybrush:~$ sudo hddtemp /dev/sda
/dev/sda: WDC WD2500BEVS-60UST0: 54°C

```

That's really a nightmare!

```
ubik@Guybrush:~$ sudo hddtemp /dev/sdb
/dev/sdb: WDC WD2500BEVS-60UST0: 60°C
```

```
ubik@Guybrush:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +56.0°C  (crit = +100.0°C)  
```

---

### Post by tgp1994 on 2010-04-10
Ahh, I just realised we're working with a laptop here. I think in general laptops tend to get warmer, mostly because of less breathing room.

However, you might want to check and make sure that none of the ventilation grills/fans are blocked, even partially, and try moving the wires aside, too.

If you're not using that second hard drive, I would recommend removing it and putting it in storage, just so the first hard drive has that extra breathing room.

---

### Post by ubik89 on 2010-04-10
> **tgp1994 said:**
> However, you might want to check and make sure that none of the ventilation grills/fans are blocked, even partially, and try moving the wires aside, too.

All fans are working fine. But I haven't this problem on windows. :(

---

### Post by tgp1994 on 2010-04-10
Could you post the temperatures that windows reports? Also, can you tell a difference in the sound the fans are making when you're in Ubuntu, then when you're in windows?

---

### Post by ubik89 on 2010-04-10
The sound of the fans is the same. Windows works at 45°C.

---

### Post by tgp1994 on 2010-04-10
> **ubik89 said:**
> The sound of the fans is the same. Windows works at 45°C.

Interesting... and you left windows running for the same amount of time Ubuntu was, when you took the readings? Perhaps Ubuntu is, for whatever reason, using Swap quite a bit. Next time you're in Ubuntu's neighbourhood, check out the Resources tab of the System Monitor, and watch the Swap usage for awhile.

---

### Post by ubik89 on 2010-04-10
> **tgp1994 said:**
> Interesting... and you left windows running for the same amount of time Ubuntu was, when you took the readings?

Yes. I'm running windows for 12 hours and it's fine.

[QUTOE] Perhaps Ubuntu is, for whatever reason, using Swap quite a bit. Next  time you're in Ubuntu's neighbourhood, check out the Resources tab of  the System Monitor, and watch the Swap usage for awhile.[/QUOTE]

No, it isn't. Swap is 0 bytes.

The hard drive LED of my notebook is showing, that the hdd is not working hard. It idles.

---

### Post by tgp1994 on 2010-04-10
I'm confused... how is it that you managed to start up windows at the time I asked for it's temperature reading, wait for 12 hours, take the reading, then go back in time and tell me the temperature? :P

---

### Post by ubik89 on 2010-04-10
> **tgp1994 said:**
> I'm confused... how is it that you managed to start up windows at the time I asked for it's temperature reading, wait for 12 hours, take the reading, then go back in time and tell me the temperature? :P

I tested it some days ago. And I'm not joking! :D

But I noticed, that @ windows the hard drive clicks. It doesn't click @ ubuntu.

---

### Post by tgm4883 on 2010-04-10
> **ubik89 said:**
> I tested it some days ago. And I'm not joking! :D

But I noticed, that @ windows the hard drive clicks. It doesn't click @ ubuntu.

Hmm. Maybe the drive has some sort of power save features that Ubuntu isn't managing.

---

### Post by tgp1994 on 2010-04-10
> **ubik89 said:**
> I tested it some days ago. And I'm not joking! :D

But I noticed, that @ windows the hard drive clicks. It doesn't click @ ubuntu.

Ah. (Thinks changing testing environment, but I won't go there...)

At some point ago we passed my actual knowledge of linux in general, so now most of what I'm doing is guesswork :P
I think clicking is a bad thing for hard drives, it could mean the read/write head is sitting on one of the platters. Due to that the speed may be slower, lowering the amount of heat generated.

My last swing at this problem is to ask for you to download GUI hard drive tools, for both platforms. I don't know if it's possible, but I'd like you to compare the rotational speeds in Ubuntu and windows. Also, some harddrives come with SMART monitoring, so try to get a tool for that.

Otherwise, best of luck to you :S

(As kind of a last minute sanity check, have you always had the laptop sitting on a flat, solid surface?)

---

### Post by ubik89 on 2010-04-10
> **tgp1994 said:**
> (As kind of a last minute sanity check, have you always had the laptop sitting on a flat, solid surface?)

Yes! :D

I've tried something with laptop-mode. I'll report tomorrow, running ubuntu over night.

---

### Post by ubik89 on 2010-04-11
Something wrong with hdparm -B value. It was set to 254. But which value is acceptable and does not overheat my hard drive?

---

### Post by ubik89 on 2010-04-11
When I set a lower value for hdparm -B the temperature goes down. But the problem is that the Load_Cycle_Count is stepping up very fast.

So, what now?

---

### Post by tgp1994 on 2010-04-11
> **ubik89 said:**
> When I set a lower value for hdparm -B the temperature goes down. But the problem is that the Load_Cycle_Count is stepping up very fast.

So, what now?

Well, as I've just read, the lower that number, the harder your computer attempts to save energy by stopping the hard disk. (This can inadvertently ruin your hard drive, according to [this thread.]("http://www.linuxquestions.org/questions/linux-hardware-18/alarmingly-high-load_cycle_count-have-you-checked-637422/")) So it looks like you're in a bit of a pickle here; lower numbers will put more stress on your hard drive, yet higher numbers make it warmer?

According to that thread, windows overrides that param value with one of it's own, so that explains why your temperature is different.

Apparently valid values are from 255 to 0. 255 Means that the hard drive heads will never "park" themselves, then starting at 254, and progressing down, the computer will begin to try more aggressively to save power, via stopping the hard disk when not in use.

Try experimenting with this value. Start it at 255, and see where the temperature goes. Then put it at 254, record the temperature, then continue on down. If the temperature begins to increase, you know you've gone too far.

Good luck!

---

### Post by Rebelli0us on 2010-05-01
You're not dreaming, my hard disks also run hotter in Ubuntu compared to Windows, about 10 deg C.

[http://ubuntuforums.org/showthread.php?t=839998](http://ubuntuforums.org/showthread.php?t=839998)

It's probably the device drivers. Manufacturers give Linux inferior drivers or none at all (see link below). e.g. Ubuntu's AMD video driver uses 10-12 watts more power at idle than Windoz because AMD has poor support for Linux.

[http://ubuntuforums.org/showthread.php?t=1233249](http://ubuntuforums.org/showthread.php?t=1233249)

---

### Post by mikewhatever on 2010-05-01
Try **sudo hdparm -M 128 /dev/sdX**, where X is a,b,c or whatever corresponds to the actual hdd.

If the feature is supported by the drive, it should run quieter and cooler.

---

### Post by worldsayshi on 2010-05-05
I have experienced problems of this kind ever since I switched to ubuntu, resulting in hard drive wear. I've replaced it once, then after just maybe three months the hard drive failed again.

sudo hdparm -M 128 /dev/sda

 setting acoustic management to 128
 HDIO_DRIVE_CMD:ACOUSTIC failed: Input/output error
 acoustic      = not supported

:(

---

### Post by mikewhatever on 2010-05-05
> **worldsayshi said:**
> I have experienced problems of this kind ever since I switched to ubuntu, resulting in hard drive wear. I've replaced it once, then after just maybe three months the hard drive failed again.

sudo hdparm -M 128 /dev/sda

 setting acoustic management to 128
 HDIO_DRIVE_CMD:ACOUSTIC failed: Input/output error
 acoustic      = not supported

:(

Sorry, not all drives support that particular feature. If you have a desktop, and you thing the hdd overheats, open it up and clean the dust to facilitate air flow.

---

### Post by jmate24 on 2010-05-06
if it is clicking in windows that means that the hard drive is experiencing the "Click of Death". so windows will not be operative for very much longer but ubuntu will. This same thing happened to my brother and his 1TB hdd.

so i suggest you install fresh on your other hard drive.

---

