---
title: "Problem with Hybrid Graphics"
date: 2011-05-07
forum: Hardware
---

### Post by DigitalNinja2012 on 2011-05-07
Hey guys I'm brand new to Ubuntu, and just have one problem so far. 
Keep in mind I'm a total newbie lol.
I'm trying to switch graphic processors within Ubuntu. I have an HP Envy 14 with integrated intel, and ATI 5650.
When I type in terminal:
grep -i switcheroo /boot/config-2.6.*

I get:

CONFIG_VGA_SWITCHEROO=y

Then when I type in:

ls -l /sys/kernel/debug/vgaswitcheroo/switch

I get:

ls: cannot access /sys/kernel/debug/vgaswitcheroo/switch: Permission denied

Any idea of what is going on here?
If anyone can provide me step by step newbie instructions that would be great!

Thanks!

---

### Post by willsomebody on 2011-05-07
Try 
```
sudo ls -l /sys/kernel/debug/vgaswitcheroo/switch
```

That will let you run that command as an administrator.

On my computer, I have to use sudo -i and then enter my password before I use the vgaswitcheroo commands.

```

sudo -i
(Enter Password)
echo OFF > /sys/kernel/debug/vgaswitcheroo/switch

```

Hope that helps.

---

### Post by DigitalNinja2012 on 2011-05-07
Thanks! That got it to work. 

Only issue now is there a way that I can tell which one is being used?

---

### Post by madjr on 2011-05-07
cool, i was also looking for this

---

### Post by willsomebody on 2011-05-07
To tell which one is being used:

From [http://ubuntuforums.org/archive/index.php/t-1629799.html](http://ubuntuforums.org/archive/index.php/t-1629799.html)

> First you need to know the BusID of the cards:
lspci | grep VGA
This will give you an output similar to this:
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18)
02:00.0 VGA compatible controller: ATI Technologies Inc Redwood [Radeon HD 5600 Series] (rev ff)

To see the status of the switch for the cards:
cat /sys/kernel/debug/vgaswitcheroo/switch
The output will look something like this:
0: :Off:0000:02:00.0
1:+:Pwr:0000:00:02.0
In this output you can see that my intel card is powered on (indicated with "Pwr") and the ati card is powered off (indicated with "Off"). The "+" sign show which gpu is being used.

---

### Post by DigitalNinja2012 on 2011-05-07
Hey, sorry for bugging again. There is only one more thing to keep me from using Ubuntu has my main OS. 

I have my monitor plugged into the HDMI on my laptop. It is an Envy 14 so only has HDMI and mini displayport out. 

I have no image showing on my main monitor. Any way to get this?

---

### Post by madjr on 2011-05-07
i think you need to restart with the monitor already plugged in and on.

then search for monitors in system settings if you want to configure it.

---

### Post by DigitalNinja2012 on 2011-05-07
Sorry for the double posting but I don't think this switcheroo is working for me.

Here is what I got when I identified the VGA controllers:

00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Redwood [Radeon HD 5600 Series]whic

So the system is recognizing both. So I type in to see which one is in use.

And I get:

0:DIS: :Pwr:0000:01:00.0
1:IGD:+:Pwr:0000:00:02.0

Which would mean that the intel one is in use.

So I go to switch it by typing in:

echo ON > /sys/kernel/debug/vgaswitcheroo/switch

And get: Nothing. It just goes back to root@*******-HP-Envy-14 and is waiting for me to type something else.

So just to check I see if it did switch:

0:DIS: :Pwr:0000:01:00.0
1:IGD:+:Pwr:0000:00:02.0

Same thing like it isn't switching :(

I think that this has to do with my issue with no video through HDMI, as the ATI card needs to be active for the HDMI to work...

EDIT: Sorry for the smileys, I don't know how to get rid of them.

---

### Post by ultimatebuster on 2011-05-07
I made a thread about it and it's getting somewhere..

[http://ubuntuforums.org/showthread.php?t=1739199](http://ubuntuforums.org/showthread.php?t=1739199)

---

### Post by DigitalNinja2012 on 2011-05-07
I ended up deleting Ubuntu, this is one option I need to work right away... I'll keep checking back with your thread and reinstall once there is a fix.

Thanks everyone!

---

