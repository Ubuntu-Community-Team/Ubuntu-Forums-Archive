---
title: "battery indicator showing &quot;battery (not present)&quot; even though it is"
date: 2011-12-12
forum: Hardware
---

### Post by f_padia on 2011-12-12
A few days ago my laptop seems to have stopped recognising my battery and now it inly works when plugged into the mains. When I click the battery indicator it reads "battery (not present)" but the battery is definitely there. 
Output of dmesg | grep BAT:
```

[    0.556734] ACPI: Battery Slot [BAT0] (battery present)

```
clearly it knows the battery is there. Also cat /proc/acpi/battery/BAT0/info gives:
```

present:                 yes
design capacity:         5100 mAh
last full capacity:      3520 mAh
battery technology:      rechargeable
design voltage:          10800 mV
design capacity warning: 182 mAh
design capacity low:     110 mAh
cycle count:          0
capacity granularity 1:  10 mAh
capacity granularity 2:  25 mAh
model number:            Primary
serial number:            
battery type:            LION
OEM info:                Hewlett-Packard

```
and finally cat /proc/acpi/battery/BAT0/state gives:
```

present:                 yes
capacity state:          ok
charging state:          charging
present rate:            unknown
remaining capacity:      0 mAh
present voltage:         10634 mV

```

so the kernel/OS can see the battery but at the same time its behaving as though its not there. Does anyone have any clues?

---

### Post by f_padia on 2011-12-14
I've noticed the same problem on another 2 laptops so im wondering if this is something to do with an update. Im surprised no one else has reported this problem though. Has no one had any trouble with laptop batteries on ubuntu recently??

Edit: Only 1 other laptop actually the other was ok after a while charging

---

### Post by Ravelair on 2011-12-14
> **f_padia said:**
> I've noticed the same problem on another 2 laptops so im wondering if this is something to do with an update. Im surprised no one else has reported this problem though. Has no one had any trouble with laptop batteries on ubuntu recently??

What did you update? I will try to apply the same thing and see what happens.

---

### Post by f_padia on 2011-12-14
> **Ravelair said:**
> What did you update? I will try to apply the same thing and see what happens.

im not sure if and what was updated, I was referring to update manager updates. Could've been anything. To be honest, it might just be that the battery is reached the end of its life but its just a little confusing that the outputs I gave in the OP show that the battery is present even though the laptop is behaving as though there isnt one there.

---

### Post by pwm5js on 2012-03-13
I have the same problem. I'd be grateful to anybody who has a solution! I have a Dell XPS M1330 running Ubuntu 11.10 with gnome classic rather than unity, and if i take out the power adapter plug, it immediately powers off. 

On startup I get an error screen that says:
 "The AC power adapter wattage and type cannot be determined.
The battery may not charge.
The system will adjust the performance to match the power available.
Please connect a Dell 65W AC adapter or greater for best system performance.
To resolve this issue, try to reseat the power adapter."

So, I replaced my power adapter with a new one from dell, which is the stock 65W adapter, to no avail.

The battery icon on the tool bar on the login screen says "Battery (not present)" and when I login it says "Laptop battery is charging (0%)"

using the same terminal commands as you did, it is clear that the kernel sees the battery

cat /proc/acpi/battery/BAT0/info gives:
```

present:                 yes
design capacity:         5200 mAh
last full capacity:      5200 mAh
battery technology:      rechargeable
design voltage:          11100 mV
design capacity warning: 520 mAh
design capacity low:     157 mAh
cycle count:          0
capacity granularity 1:  52 mAh
capacity granularity 2:  52 mAh
model number:            DELL NX5117
serial number:           31307
battery type:            LION
OEM info:                TP-PP
pwmurphy@pwmurphy-XPS-M1330:~$ cat /proc/acpi/battery/BAT0/state
present:                 yes
capacity state:          ok
charging state:          charged
present rate:            1 mA
remaining capacity:      0 mAh
present voltage:         11246 mV
```and cat /proc/acpi/battery/BAT0/state gives:
```
present:                 yes
capacity state:          ok
charging state:          charged
present rate:            1 mA
remaining capacity:      0 mAh
present voltage:         11245 mV
```

---

### Post by kiatoa on 2012-03-21
I have this same problem. In my case I believe it happened after leaving the netbook in suspend for a long time and the battery was exausted.

I have the message "(not present)" next to the battery icon. Unplugging from power causes the netbook to die immediately.

My netbook is an Asus 1215N.

---

### Post by f_padia on 2012-04-08
bump... can anyone help with this?
I replaced the battery thinking it was just my battery but after a few weeks of working ok the same problem is back.

---

### Post by mzunguInKenya on 2012-04-19
I had the same problem with battery "not present"

now i cant even turn the laptop on with the battery in, as soon as i log in the laptop reboots.

I have tried with another battery and it worked till the battery charge depleted (still connected to ac). now the same thing happens with the second battery. i know its not the battery or the charger because the second battery is a travel battery and has a charging port which will still charge if not connected to the laptop.

is there anyone that knows whats going on with this problem? is there any solution?

---

### Post by DannyD.Fl on 2012-04-24
Owner of a compaq CQ56 erre, having the same issue.
Wat I do in order to be able to use my laptop is I log in as a guest so know the system asks for a password before sutting off.
The issue is widely reported and still no solution.
I've had Ubuntu for 2 years and my battery is still ok.
What is taking so long to find a solution on this? It has been reported for longer then 6 months....

---

### Post by f_padia on 2012-05-15
I still dont know why this problem occurs but it seems a similar problem exists in windows because when I booted into the windows partition it too was telling me there was no battery present. However, I was able to find a fix for the windows problem after a bit of googling and somehow it fixed it in Ubuntu too! Here's what I had to do (in Windows).
First, I had to delete the acpi driver  
then reboot with the battery out
then power down the laptop and put the batter back in
boot up (into windows)
let windows re-install the battery driver
and voila it worked again. Then reboot into Ubuntu and magically the problem was fixed. No idea why re-installing a windows driver had any effect on Ubuntu but it seemed to work. It may have just been a coincidence but it might be worth a shot if anyone else is having similar troubles

---

### Post by endlesssnowfall on 2012-05-16
> **kiatoa said:**
> I have this same problem. In my case I believe it happened after leaving the netbook in suspend for a long time and the battery was exausted.

I have the message "(not present)" next to the battery icon. Unplugging from power causes the netbook to die immediately.

My netbook is an Asus 1215N.

Same exact problem here on an HP Mini 1000 running 12.04.  I've noticed that sometimes after leaving it plugged in for 20 minutes, the system will detect the battery again, but other times it never does until I restart.

---

### Post by brain90 on 2012-08-20
Hello, same issues happen with HewlettPackard hp5220m powerbook. 

Looks like this issue occured when the battery energy are very empty, so the applet cant detect the battery precisely. After some minutes charging it going back normally.

A Bugs !, has confirmed at launchpad.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1034627](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1034627)

:guitar:

---

### Post by VoiceOvGod on 2012-12-27
I'm having the same issue with an HP G60.

```

~$ dmesg | grep BAT
[    0.939348] ACPI: Battery Slot [BAT0] (battery present)
[    1.479818] ACPI: Battery Slot [BAT0] (battery present)

```

After that, I did a cat

```

cat /proc/acpi/battery/BAT0/info
cat: /proc/acpi/battery/BAT0/info: No such file or directory

```

I did an ls and got the following:
```

ls -l /proc/acpi
total 0
dr-xr-xr-x 3 root root 0 Dec 27 21:51 button
-r-------- 1 root root 0 Dec 27 21:42 event
-rw-r--r-- 1 root root 0 Dec 27 21:51 wakeup

```

I am using 12.10. This issue started with 12.04, and I figured do the updates first to see if it would fix it. Alas, no bueno.

Also, that bug is showing as expired.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1034627](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1034627)

---

### Post by nullus on 2013-01-10
Seeing the same issue with an hp pavilion dm4 on ubuntu 12.04. Just started recently too.

---

### Post by amtrakuk on 2013-05-02
My Fujitu Esprimo Mobile D9510 reports Battery not present only when its fully charged.  Using 12.04

---

### Post by comradetimkin on 2013-05-25
> **f_padia said:**
> I still dont know why this problem occurs but it seems a similar problem exists in windows because when I booted into the windows partition it too was telling me there was no battery present. However, I was able to find a fix for the windows problem after a bit of googling and somehow it fixed it in Ubuntu too! Here's what I had to do (in Windows).
First, I had to delete the acpi driver  
then reboot with the battery out
then power down the laptop and put the batter back in
boot up (into windows)
let windows re-install the battery driver
and voila it worked again. Then reboot into Ubuntu and magically the problem was fixed. No idea why re-installing a windows driver had any effect on Ubuntu but it seemed to work. It may have just been a coincidence but it might be worth a shot if anyone else is having similar troubles

Have you any idea how one would do that in Ubuntu/Xubuntu? As mentioned above, I am windowless. 

Further update - after hours of searching about and no experience in doing such operations, I was successful in flashing the last BIOS version released for the machine, and it has unfortunately made no difference at all (other than probably taking a few minutes off my life expectancy when watching the machine turn itself off at the end of the process - it took me a couple of seconds to find out this was in fact to be expected). 

I have to say that the issue seems pretty widespread, with loads of people reporting such problems, and yet there is virtually nothing out there suggesting any solution. For something as basic and necessary as this, it seems surprising that a fix doesn't appear to be being aggressively pursued. It's a fundamental piece of hardware!

EDIT: Interrogating ACPI shows the battery is detected (battery present) but percentages are all 0%, so absolutely no idea how much juice is there. The icon on the panel says 0% too, and conky shows empty status. Grrr.

---

### Post by davethebrave on 2013-07-01
Just adding my name to the list of people with this problem who have no idea about a solution. I had a similar but different issue after an update that got pushed through last year where it did not recognize my battery **at all** unless it was plugged in, and when it was plugged in it recognized the battery fine, and that it was fully charged (which it nearly always was since if it disconnected from an outlet it would shut down). Still don't know which update caused/which update fixed that issue, and it was over a month of updates before it corrected itself. 

This is slightly different, the battery shows as (not present) with the red-lined dead battery when I power on without connecting to an outlet, but when it's connected it still says (not present), except it shows the battery charging symbol with the lightning bolt and a little grey filled in (no percentages or hours remaining available). It's really frustrating because I have zero idea how much my battery is charged at any given time. It seems to have started after updates I put through yesterday, but I had been putting them off for a week or two, so there was a bit of a build-up. So, once again, I have no idea which update(s) caused this issue, and who knows when and if this issue will be fixed via update...but no one seems to know how to fix this in the meantime, or even what it is.

---

### Post by banago on 2013-11-03
Same here.

I'm into "Battery not present" mode for several months now and I can use my laptop unly conected to an outlet. That sucks!

I'm using Lemur Ultra form System76 and running Ubuntu 12:04

---

### Post by Jonah Bron on 2014-01-10
I too am experiencing this issue.  I even bought a new battery, but it still shows as "not present".  HP Pavilion dm1z.  Could this be a hardware failure?  Maybe the component responsible for charging the battery has failed?

---

### Post by piripiri2 on 2014-02-09
Asus k56c with the same issue and it started just recently.

---

### Post by piripiri2 on 2014-02-09
I've just installed IBAM (The Intelligent Battery Monitor for Laptops) and the battery "got back".

---

### Post by yacketayakking on 2014-02-28
> **piripiri2 said:**
> I've just installed IBAM (The Intelligent Battery Monitor for Laptops) and the battery "got back".

Hey could you explain what you did with IBAM to get the battery back ? I am only getting "[COLOR=#333333][FONT=Lucida Grande]No apm data available"...[/FONT][/COLOR]

---

### Post by son-of-lysander on 2014-03-05
Running Ubuntu 13.10 x64bit

This is my first time running into this problem myself and this was the first thread to come up. I'm not 100% sure if I have the same issue as everyone else (I left my laptop suspended, yet plugged-in and charging, all night and through the day while at work. When I came home my computer wouldn't start without the cable. When I plugged it in it then turned on and stated that my battery wasn't present. I was doing some investigating and came across this thread, but at that point my battery regained some charge and started reporting 1%. Like I said, I'm not sure why it came across as not-present in the widge, still reported present in the terminal, yet had been plugged in for close to 20 hours.

I'm not sure if this will recur, if I can replicate it later I'll report back. In the mean time, to install ibam:

```
sudo apt-get install ibam
```

---

