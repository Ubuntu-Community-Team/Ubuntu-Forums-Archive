---
title: "HDD temp"
date: 2010-11-01
forum: Hardware
---

### Post by xbobby_bobx on 2010-11-01
Ok for the last time I have a high HDD temp problem I'm reaching a temp of 47c please don't tell me this is normal because on windows it's not that hot so can you please tell me what to do to decrease it?
and don't tell me to type sudo hddtemp /dev/sda or install some kind of stupid sensors

I tried everything and installed everything i even tried the laptop mode which im currently using but no use 

what i should do?

---

### Post by Quackers on 2010-11-02
In normal day to day operation my HDD temp is between 46 and 58 degrees. The fan doesn't even come on until it hits 58 degrees and then it cools to 51 or so within 10 seconds. I don't think these are high temps at all. I'm certainly not concerned about them in any way.

---

### Post by P4man on 2010-11-02
They are definitely high. Most hdd are only specced to run at 60 max, and the higher the temps, the faster it will wear out. In my old case with poor hdd ventilation I would get 45-50C on my drives, I bought a new case with large intake fans blowing over the drives and they are now 25-27C.

Now Im guessing both of you have a laptop, which complicates things. There isnt very much you can do to improve temps, except realize that overheating cpu's and gpu's (and batteries) will also heat up your hdd. The actual cause and solution (if any) could be in ensuring CPU scaling is working properly and powermanagement for your GPU is actived (eg, with an ATI card, install catalyst drivers)>

---

### Post by Quackers on 2010-11-02
> **P4man said:**
> They are definitely high. Most hdd are only specced to run at 60 max, and the higher the temps, the faster it will wear out. In my old case with poor hdd ventilation I would get 45-50C on my drives, I bought a new case with large intake fans blowing over the drives and they are now 25-27C.

Now Im guessing both of you have a laptop, which complicates things. There isnt very much you can do to improve temps, except realize that overheating cpu's and gpu's (and batteries) will also heat up your hdd. The actual cause and solution (if any) could be in ensuring CPU scaling is working properly and powermanagement for your GPU is actived (eg, with an ATI card, install catalyst drivers)>

Thanks for that info P4man, I wasn't aware that these were high. I was talking about my laptop and I would also say that Sony have replaced both hard drives twice in less than 3 years without so much as a comment! I wonder if they were aware of cooling problems with my laptop.
Very interesting.

Edit; it also begs the question why aren't the fans on more? They are mostly silent, in Vista, W7 and Lucid and Maverick.

---

### Post by Quackers on 2010-11-02
An update.
I was using the conky display to gauge the temps. This uses acpi_temp as its source. I gather that this is not the hdd temp. I have booted into Windows 7 and downloaded HDD temp. At idle HDD temp reports that my temps are 35 and 36 degrees and that their highest recorded temps have been 43 and 45 degrees. So, a bit better, but not that great, it seems. I wonder why my fans come on so late? The laptop has always been like this from new.

---

### Post by P4man on 2010-11-02
Those temps seem more or less normal for a laptop. On most laptops, the fan doesnt cool the hdd and its speed is regulated by the cpu temperature (sometimes gpu temp as well).

---

### Post by coffeecat on 2010-11-02
> **Quackers said:**
> I was using the conky display to gauge the temps. This uses acpi_temp as its source. I gather that this is not the hdd temp. I have booted into Windows 7 and downloaded HDD temp. At idle HDD temp reports that my temps are 35 and 36 degrees and that their highest recorded temps have been 43 and 45 degrees. So, a bit better, but not that great, it seems. I wonder why my fans come on so late? The laptop has always been like this from new.

@Quackers, in Ubuntu you can install the package sensors-applet which gives you a panel applet listed as 'Hardware Sensors Monitor' in 'Add to panel'. It uses hddtemp as a dependency so it might be interesting to see what your HD temperatures are in Ubuntu compared with Windows. Or do you have hddtemp installed already? I've never used conky but I would have thought conky could use hddtemp data as well.

I wonder if the OP's problem might be down to fstab mount options for the root filesystem. I see that a default install no longer includes relatime or noatime (if it ever did) which would reduce HD activity.

---

### Post by Yellow Pasque on 2010-11-02
> **xbobby_bobx said:**
> Ok for the last time I have a high HDD temp problem I'm reaching a temp of 47c please don't tell me this is normal because on windows it's not that hot

While it may be warmer than windows, it's still well below the maximum spec and nothing to worry about.

> what i should do?
Nothing (or maybe enjoy some alcohol or valium to help you relax if you're so inclined).

---

### Post by xbobby_bobx on 2010-11-02
Dude this is going to make my HDD life shorter by at least 3 years I do need this laptop but I need a fix for this problem because if there is no fix that means the OS is not good and I think this is why many people don't use Linux because they don't know how to use it. It would be great if I can get my HDD temp to 43c by the way I'm using a cooling pad and without the cooling pad It reaches 53c so yeah I need help!!

---

### Post by xbobby_bobx on 2010-11-02
> **P4man said:**
> They are definitely high. Most hdd are only specced to run at 60 max, and the higher the temps, the faster it will wear out. In my old case with poor hdd ventilation I would get 45-50C on my drives, I bought a new case with large intake fans blowing over the drives and they are now 25-27C.
 
Now Im guessing both of you have a laptop, which complicates things. There isnt very much you can do to improve temps, except realize that overheating cpu's and gpu's (and batteries) will also heat up your hdd. The actual cause and solution (if any) could be in ensuring CPU scaling is working properly and powermanagement for your GPU is actived (eg, with an ATI card, install catalyst drivers)>
 
 
Scaling didn't affect at all, the proper drivers won't work for some reason, my temp1 is 57c as a maximum but it rarely reach the 57c on the normal usage it reaches 54c which i think it's warm but not hot because my windows CPU temp is 48c but the HDD temp is actually hot for a hard drive any other ideas?

---

### Post by Crazedpsyc on 2010-11-02
My asus laptop gets up to about 60-70c with normal use in ubuntu. It gets so hot my hands start sweating on the touchpad. I have seen some programs to make the fan work harder but I don't know if they are safe

---

### Post by xbobby_bobx on 2010-11-02
Wow dude don't use Ubuntu this is not good for you laptop or for your health just stop using it until there is a fix for this problem.

---

### Post by Crazedpsyc on 2010-11-02
I can't just stop using ubuntu! Windows sucks! unless you can tell me how to get rid of this (**** *******) start bar/taskbar thing and put in something resembling awn instead. I already got Nexus for my top panel but how can I completely or mostly make that ugly win7 bar go away?

---

### Post by xbobby_bobx on 2010-11-02
Autohide does that work for you so you don't need to see the ugly bar anymore I do hate windows too but this is the best you can do to save your money and keep your health better.

---

### Post by Crazedpsyc on 2010-11-02
Alright I'll try just auto hiding it but I don't think I will like it popping up every time my cursor goes to the bottom of the screen either

---

### Post by xbobby_bobx on 2010-11-02
It's OK just don't worry about it and if you didn't like it I will try to find a fix for it :D.

---

### Post by Quackers on 2010-11-02
> **coffeecat said:**
> @Quackers, in Ubuntu you can install the package sensors-applet which gives you a panel applet listed as 'Hardware Sensors Monitor' in 'Add to panel'. It uses hddtemp as a dependency so it might be interesting to see what your HD temperatures are in Ubuntu compared with Windows. Or do you have hddtemp installed already? I've never used conky but I would have thought conky could use hddtemp data as well.

I wonder if the OP's problem might be down to fstab mount options for the root filesystem. I see that a default install no longer includes relatime or noatime (if it ever did) which would reduce HD activity.

Thanks coffeecat, sensors installed and the applet is running. Temp readings show HDD1 @ 27c HDD2 @ 28c but also shows sda1 @ 26c and sdb1 @ 26c
So, slightly different info for the same devices, but all much lower than acpi_temp. And, interestingly, all considerably less than in Windows 7.

xbobby_bobx what is your GPU temp showing? It seems this can have an effect on your HDD temp. And are you using the same sensors?

---

### Post by coffeecat on 2010-11-02
> **Quackers said:**
> Thanks coffeecat, sensors installed and the applet is running. Temp readings show HDD1 @ 27c HDD2 @ 28c but also shows sda1 @ 26c and sdb1 @ 26c
So, slightly different info for the same devices, but all much lower than acpi_temp. And, interestingly, all considerably less than in Windows 7.

I *believe* acpi temp shows the CPU temp. I can't get my HDD temp above about 32C either in my (Sony) laptop or self-build desktop. Durn! And there I was hoping I could reduce the load on my central-heating boiler. :wink:

---

### Post by Quackers on 2010-11-02
> **coffeecat said:**
> I *believe* acpi temp shows the CPU temp. I can't get my HDD temp above about 32C either in my (Sony) laptop or self-build desktop. Durn! And there I was hoping I could reduce the load on my central-heating boiler. :wink:

yeah, sometimes life really sucks :)

My HDD temps have gone to 33 and 34 now, which is comparable to Windows 7 temps. GPU shows 54. ACPI temp (in conky) is showing 44, which virtually agrees with libsensors, so it looks like you're right about acpi temp showing CPU temps.

---

### Post by Yellow Pasque on 2010-11-02
> **xbobby_bobx said:**
> Dude this is going to make my HDD life shorter by at least 3 years

The heat/lifespan correlation is greatly exaggerated for normal operating temps. As long as you're well below spec (which you are), I wouldn't worry about it too much.

> Many people have assumed that high temps are bad for disks. And indeed maybe they are bad for 3-year-old disks, but disks that fail at younger ages tend to be much more traumatized by cold than by heat. Pinheiro et al. give additional data for this, and it's pretty convincing. For example, if you have a look at Fig. 4 of the paper, you'll see a bathtub curve, showing that extremes of temperature are deleterious to disk life expectancy. Ironically, the bathtub curve reaches its lowest point at around 38 deg. C -- very close to human body temperature. 
-- [http://asserttrue.blogspot.com/2009/12/unexpected-relationship-between-hard.html](http://asserttrue.blogspot.com/2009/12/unexpected-relationship-between-hard.html)

> The fan doesn't even come on until it hits 58 degrees and then it cools to 51 or so within 10 seconds.
You have a fan controlled by HD temp in a laptop? That sounds like a poorly designed algorithm if so. Rapid cooling/heating can be as bad as overheating. It would be far better if the fan ran at a constant, low RPM.

---

### Post by CharlesA on 2010-11-02
> **Quackers said:**
> Thanks coffeecat, sensors installed and the applet is running. Temp readings show HDD1 @ 27c HDD2 @ 28c but also shows sda1 @ 26c and sdb1 @ 26c
So, slightly different info for the same devices, but all much lower than acpi_temp. And, interestingly, all considerably less than in Windows 7.

That looks right now. :)

I check hard drive temp by using startcrl.

> **coffeecat said:**
> I *believe* acpi temp shows the CPU temp. I can't get my HDD temp above about 32C either in my (Sony) laptop or self-build desktop. Durn! And there I was hoping I could reduce the load on my central-heating boiler. :wink:

Yep. ;) Most of my machines run the hard drive at around 30-40C, but then most of them have a push a bunch of air across the drives.

---

