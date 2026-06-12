---
title: "battery power is much less in gutsy than in vista"
date: 2008-03-24
forum: Hardware &amp; Laptops
---

### Post by GSMX on 2008-03-24
hey,

I have a problem with the powerconsumption of gutsy. This laptop is an Acer Aspire 7520G, dualboot Vista and Gutsy. In Vista I have 2,5 hours of battery time, but in Gutsy only 1 hour and 10 minutes!!! I think this is unacceptable low... How can I fix this?

greetz

---

### Post by teaker1s on 2008-03-24
by default laptop mode is disabled due to concerns about issues. you can get more time with cpu scaling like powernowd
laptop mode I believe you need to


```
sudo gedit /etc/default/acpi-support
```


To reenable laptop mode, edit /etc/default/acpi-support and set ENABLE_LAPTOP_MODE=true.

---

### Post by GSMX on 2008-03-24
doesn't seem to make any difference :(

---

### Post by sillyxone on 2008-03-24
Did you measure actual battery time or just rely on the estimated amount left by the OS? It's hard to tell by that number, some report more, some report less.

Since you replied with 10 minutes of teaker1s, I assume you just read the estimated time?

---

### Post by GSMX on 2008-03-24
yes, i do assume the estimated time is right?!? why wouldn't it? but, I'll check out by pulling out the plug and set all powermanagement to "do nothing"... hope it will work...

---

### Post by eumetaxas on 2008-03-24
i have the same problem too compared to M$ XP both with gutsy and debain testing. also heard for other people with other distros having the same problem.

---

### Post by sillyxone on 2008-03-24
I'm not sure what might be wrong, but my Dell D620 is kind of opposite. On full charge, Ubuntu report 2:44 left, and most of the time I can only use about 2:20 and the laptop goes to suspend. On full charge, XP reports 1:50 but I never test it so I don't know.

Even when I lower the LCD brightness, the estimated changes are also different between Ubuntu and XP.

---

### Post by GSMX on 2008-03-24
OK, I now tried and i've completely unloaded the battery 2 times, both times it was only 1 hour and 10 minutes, not the 2 hours and 30 minutes from vista! help!

---

### Post by Whiffle on 2008-03-24
Power management in linux is still rather undeveloped as far as I'm concerned.  Its possible to get awesome battery times out of it, but it takes tweaking.  A good place to start is [www.lesswatts.org](www.lesswatts.org) , and with the powertop program.

---

### Post by sillyxone on 2008-03-24
so Vista does let your laptop stays more than double the time in Ubuntu. Well, with that much difference, let's look at a few things that could be the power eater(s):

- LCD backlight: assuming you let the LCD on all the time with same brightness level in both OS so no need to check this one.

- Fan: do you notice the fan runs constantly or more frequent in Ubuntu?

- HDD: this is a tricky one, Ubuntu used to have a bug that set hdparm to slow down more frequent so it should save more power. Search for more information if you want to tweak on it.

- CPU; as teaker1s suggested, probably Ubuntu doesn't have your CPU scaled down properly. Again, search for more information on it. I would check more on CPU since I usually get only half the battery time when I play CPU intensive games.

I don't know what else might make that big difference in power saving. The video chipset could be but not much of a big problem. Do you have any other peripherals that might eat up power (webcam, e.g.)? Also anything mechanical connect to your computer such as CD/DVD drives.

---

### Post by GSMX on 2008-03-25
> **sillyxone said:**
> - LCD backlight: assuming you let the LCD on all the time with same brightness level in both OS so no need to check this one.

Because i'm in a very light environment, I always put backlight to lowest possible setting.

> **sillyxone said:**
> - Fan: do you notice the fan runs constantly or more frequent in Ubuntu?

Well, by putting ENABLE_LAPTOP_MODE=true as mentioned above, I do hear less cpu-fan startups, but this has no effect on the power :(

> **sillyxone said:**
> - HDD: this is a tricky one, Ubuntu used to have a bug that set hdparm to slow down more frequent so it should save more power. Search for more information if you want to tweak on it.

I'll google this one, but with a quick search, it seems it has to do with the ENABLE_LAPTOP_MODE=true again?

> **sillyxone said:**
> - CPU; as teaker1s suggested, probably Ubuntu doesn't have your CPU scaled down properly. Again, search for more information on it. I would check more on CPU since I usually get only half the battery time when I play CPU intensive games.

I'll search for it... No other ideas??

---

### Post by luvit on 2008-03-26
> **Whiffle said:**
> [COLOR="Red"]Power management in linux is still rather undeveloped as far as I'm concerned.  Its possible to get awesome battery times out of it, but it takes tweaking.  A good place to start is [www.lesswatts.org](www.lesswatts.org) , and with the powertop program.[/COLOR]

This is the direction I'm going to start with ;) **[COLOR="Red"]Is there a similar project?[/COLOR]**
I have the same power management problem and can now give it attention since I now have working wireless and visual effects . I believe CPU tweak will be the big battery saver.

I could easily get 3hrs out of my laptop battery on Vista because I set all the power requirements to the lowest. My laptop ran cool.
With Ubuntu my laptop is much warmer and I get about an hour. After I tweak my cpu I'll look at Hard Drive power-management.

---

### Post by luvit on 2008-03-30
My Short Battery Life problems are solved and I have as much control of ensuring maximum power saving using ubuntu tweak, and monitoring system activities.:)
It's easy installs direct from the webpages!
I have outlined these 3 packages in the tweaking section of my **[COLOR="RoyalBlue"][Ubuntu Blog]("http://www.yay4u.com/search/label/Tweaking")[/COLOR]**. ;)

My screen brightness and hard drive power saving settings wer optimal by default in Ubuntu.

---

