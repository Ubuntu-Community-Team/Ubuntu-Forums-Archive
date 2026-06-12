---
title: "Acer Aspire One ZG5 heat and battery issue"
date: 2011-04-24
forum: Hardware
---

### Post by xtremesupremacy3 on 2011-04-24
Hey,

I used to run Windows XP on my little netbook without any problems after installing all the drivers but I just cant get used to the Windows experience and decided to install UNR 10.10.

As expected everything works out of the box.
Now I liked the Unity interface but with continuous lockups, I just decided to run Desktop Edition instead which works fine.

Just as a background for you, this netbook is the cheap AA1 that comes with Linpus(?) preinstalled on it.

Now my problems are as followed:
1) When I used Windows XP I would get an average of 3 hours on a full charge (I'm told thats not as good as it should be but its fine for me). But after having installed UNR it only manages 2 hours if I'm lucky, now that's not really enough for me.

2) The heat of this thing is incredible. On XP there was nothing wrong with overheating or anything, but on here, after about half an hour its seriously warm. I have currently used it for about 15 minutes and im getting the following temperature: 54000

Also, after some usage the system tends to lock up a fair bit, I won't concentrate on this as it is most likely due to the slow SSD card it uses.

Thinking it may be a fan related problem I looked at the fan control and with dmesg get the following bit of info:
```
[    3.532153] acerhdf: Acer Aspire One Fan driver, v.0.5.22
[    3.532169] acerhdf: Fan control off, to enable do:
[    3.532174] acerhdf: echo -n "enabled" > /sys/class/thermal/thermal_zone0/mode

```

So, I ran the code I got, both as is and using sudo but get:
```
bash: /sys/class/thermal/thermal_zone0/mode: Permission denied

```

Does anyone have any tips?

---

### Post by xtremesupremacy3 on 2011-04-24
UPDATE:

I was able to execute the command using ```
sudo su
```

It now shows I have 2 1/2 hours on a full charge.
I will have to keep an eye on it all and report the findings, in the meantime, if anyone has any more ideas, please let me know

---

### Post by pakito15191 on 2011-04-24
You probably need to be root to modify it (and any file outside /home/yourusername), so just run the same line but writting sudo before:

```
sudo echo -n "enabled" > /sys/class/thermal/thermal_zone0/mode
```

Then it will ask for your password, you write it and that's all :)

(I didn't test it, I am just too used to the "Permission denied" bit, if it doesn't work, post back...)

PS: I just underclocked a computer today, and the heat decreased a lot, I followed this guide: [http://ubuntuforums.org/showthread.php?p=5815597](http://ubuntuforums.org/showthread.php?p=5815597)

If you have any problem, just ask again! I hope it helps!

---

### Post by xtremesupremacy3 on 2011-04-24
I may not have made it obvious enough, but I had tried both normal line and putting sudo in front of it, but it didn't make a difference until I went into root 'mode'.
Thank you for your help and the link, I will check that out

---

### Post by pakito15191 on 2011-04-24
Sorry I didn't see that bit! :(

Well, I hope the underclocking bit helps you, but that could be a bit extreme, first play a bit with the power management options now that the fan is working and if it's still getting too hot, you could even buy some laptop cooling pad (examples: [http://www.google.com/search?q=laptop+cooling+pad&um=1&tbm=isch](http://www.google.com/search?q=laptop+cooling+pad&um=1&tbm=isch) )

Update how the fan is working please, I'm waiting for a battery replacemente for the same netbook (windows broke the old one) :)

---

### Post by xtremesupremacy3 on 2011-04-24
you know the battery isnt heating up anymore, its staying at a constant now. It's so weird, after having run the command, the screen dims better than before and it still reads at 2:30 left on full charge...please note though that this is at least a year old battery.

I will update in detail as soon as I have given it long enough to test the changes.

God I love this thing

---

