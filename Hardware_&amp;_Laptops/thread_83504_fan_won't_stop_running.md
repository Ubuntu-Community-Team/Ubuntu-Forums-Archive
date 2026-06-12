---
title: "fan won't stop running"
date: 2005-10-28
forum: Hardware &amp; Laptops
---

### Post by jamieson on 2005-10-28
I'm running breezy on my Dell Latitude L400 and the fan won't stop running.  I'm able to set the CPU freq down to 500MHz but the fan continues to run.

Poking around in some of the acpi stuff: in /proc/acpi/thermal_zone/THRM/

polling is disabled; setting to 30 seconds makes no difference.
temperature always reads 50C
trip_points contains only one value: critical S5 and cannot be changed

there is a fan listed in /proc/acpi but that directory is empty.  No fan control.  Tried the i8kutils but no joy either.

I've found the only thing that works is booting the kernel with acpi=off

Is this notebook PC just too old to use ACPI?  Do I have to recompile the kernel with some special dell notebook option turned on?

---

### Post by shidai.liu on 2005-11-05
I found that after wakup from suspension to ram, the fan won't stop. Just a note. I don't know the fix.

---

### Post by Mikey248 on 2005-12-31
Simply take four small-sized pads of Post-It notes and place them directly beneath the four rubber nodgets on the bottom of your laptop (positioning them elsewhere risks putting them under a hotspot or and uneven spot).  This will raise your laptop 1/2-inch above your desk.  It may not result in stopping your fan, but my fan did slow down a little and the hottest spots beneath my laptop cooled down a little, which certainly reduces "fry" risk.

---

### Post by ysse on 2006-01-06
Don't know if it works on your L400, but I had a Latitude C800, which always had the fan on full speed after wake-up from suspend. Fn - Z used to take it down to normal revs. But I never could use acpi on it, had to go with apm.

---

### Post by etjazz on 2006-09-16
I've made many tentatives with some kernels and powermanagers, the l400 seems to be working well with apm (acpi=off) at boot but you can not read the thermal value of the processor.
It seems to be a bios problem, I've tried with A09 and A06 with any success; Now it works for me with bios A02 from dell site and acpi; thermal_zones works with this commands:

 echo -n "90:0:58:65:60" > /proc/acpi/thermal_zone/THRM/trip_points
 echo 30 >  /proc/acpi/thermal_zone/THRM/polling_frequency

---

### Post by walopower on 2006-12-16
Kernel 2.6.15.27-686
Dell L400
With me, bios v. A03 work fine, but A09 no (not update if you not must)...
So i compile new DSDT, and then acpi work 100% correctly.
Follow this guide:
[https://help.ubuntu.com/community/ACPIBattery](https://help.ubuntu.com/community/ACPIBattery)

I must also compile synaptics driver manually, but now works.
[http://web.telia.com/~u89404340/touchpad/](http://web.telia.com/~u89404340/touchpad/)

Because i don't have any external boot devices, I install with PXE. I updated bios also with PXE+freedos.
I have 80GB, so I made extra partition for root partition backup (6GB) and boot (100MB), so i don't need use PXE anymore.

---

### Post by jfdarv on 2007-03-28
Just a little question; is A03 the latest stable BIOS available? Has anyone had success with more recent BIOS?

---

### Post by walopower on 2007-03-30
I updated from Dapper ro Edgy, no acpi hangs. Then very quickly updated to Feisty. In Feisty is newest kernel (2.6.20.13), 

-No acpi proplems (DSDT is automaticly removed when I updated new kernel?).
-Now dynamic! speedstep (less heat) and laptop mode work OOTB.
-Glxgear score increased 35%, but still no direct rendering work (4096 RAM).
-Touchpad work

---

### Post by jfdarv on 2007-03-30
> **walopower said:**
> I updated from Dapper ro Edgy, no acpi hangs. Then very quickly updated to Feisty. In Feisty is newest kernel (2.6.20.13), 

-No acpi proplems (DSDT is automaticly removed when I updated new kernel?).
-Now dynamic! speedstep (less heat) and laptop mode work OOTB.
-Glxgear score increased 35%, but still no direct rendering work (4096 RAM).
-Touchpad work
So with Dell L400, bios A09 (newest) and at least Edgy, is highly recommendable combination.

I have doubt about what you say. In Edgy, I could not login because the laptop was going into suspend mode automatically. I also use Slax 6 with kernel 2.6.20. The suspend problem doesn't not appear but the fan never starts. Then the laptop shuts down because of over heating. So there is definitely a problem with BIOS A09 because the fan and suspend problems has been related by many users, in the French forums as well. After flashing the BIOS back to A03, all the problems were gone. I can login to Edgy and the fan is now starting. I can even check the temperature, something that wasn't working with A09.

By the way, DRI only works in 800x600. Not very useful.

Thanks for your reply. I am very curious to put some light on this issue. What I don't understand is that a few months ago, you suggested not to use A09 and now you say that it works flawlessly... obviously not the case for me.

---

### Post by walopower on 2007-03-30
Because i updade to feisty, and new kernel and everythink still working and also powernowd governors. But if everythink is working, you don´t have to update of course.
Removing lm-sensors can help too...

---

### Post by mertle on 2007-03-31
I had a similar problem w/ my fans on my Dell i9300. I was using BIOS A02 and all was well... then I updated it to A05 via Dell's support site. The fans would work fine until something made them kick on to high, then they never stopped until I rebooted. I know ya said i8kutils was no joy for ya, but I used it with gkrell to regulate my fan speeds and it's worked very well so far. 

And even if you cannot regulate them automatically, you can manually set the speed of each fan with i8kutils... very useful, in my case.

Here's a link to my post and the solution someone gave me that worked very well. I hope it helps.

[http://ubuntuforums.org/showthread.php?p=2381637](http://ubuntuforums.org/showthread.php?p=2381637)

To manually change the fan speed if/when you use i8kutils is:

```
 $ i8kctl fan 1 2 
```

Translation: turn left fan to low and right fan to high.

0 - Off
1 - Low
2 - High
 You can also use a dash ( - ) in place of a number to leave that fan as is.

Also be aware that some systems report your fans opposite- on mine, what is considered left is /physically/ right.

BTW, does anyone know where I can find versions of old Dell BIOS? I may just revert back to A02 as it seemed to work without all the extras.

---

### Post by jfdarv on 2007-04-10
i8kutils does not work with Dell Latitude L400.

You can find all Dell's BIOS on their ftp site.

---

### Post by jfdarv on 2007-04-11
> **walopower said:**
> Because i updade to feisty, and new kernel and everythink still working and also powernowd governors. But if everythink is working, you don´t have to update of course.
Removing lm-sensors can help too...

Just a little question about powernowd governors. I tried to use ondemand and conservative governors but when the CPU change frequency, I get the following errors from dmesg and the mouse freezes for a second or two:

```
[17179883.112000] cpufreq: change failed with new_state 1 and result 0
[17179883.620000] psmouse.c: resync failed, issuing reconnect request
[17179899.836000] psmouse.c: Wheel Mouse at isa0060/serio1/input0 lost synchronization, throwing 2 bytes away.
[17179899.836000] cpufreq: change failed with new_state 0 and result 0
```

What governors do you use? Do you get the same errors? Also, I cannot set these two governors from the command line. Everything is set up properly because other governors work ok.

In still on Edgy. I will give a try with Feisty in a few days when the Final Release is out. If you can give me some explanations about this problem I would be very grateful. I searched all over the forums and on google but I didn't find any resolutions.

Thanks!

---

### Post by ktulu1115 on 2007-09-02
Hey all, I've got a similar problem with my L400, except that my fans don't turn on period.  Got A07 BIOS (IIRC) and ACPI is basically not working at all.  It only reports thermal @ 50C and AC adapter online (both of which are "fixed" and inaccurate - values dont change).

Got i8k module to force load but still doesn't help any.  After short usage, laptop gets too hot and need to shut down.  Running Gutsy development right now, any suggestions from anyone?  About to try booting with acpi=off

---

### Post by kyalpani on 2007-09-02
I have the same problem on a sony viao vgn-fz18m with dual core celeron processors. cpu temp. is very 'normal' at around 35 (celsius) when I am not doing to much on the laptop, (e.g. just browsing text) and if i am editing, it goes up to about 43 celsius. The fan kicks in and then just stays on for an extended period. I was not able to install lm-sensors as some posts have suggested, but it seems there quite a few others that have similar problems on different laptops. Perhaps we should all get organized and hash out this problem together. One of the things that still puzzle's me is have reliable information as to what is the normal fan behaviour and what is normal cpu heat?

---

### Post by walopower on 2007-09-02
DSDT patch work.
[http://acpi.sourceforge.net/dsdt/view.php?id=391](http://acpi.sourceforge.net/dsdt/view.php?id=391)
[http://www.saunalahti.fi/~maalehti/compiled.rar](http://www.saunalahti.fi/~maalehti/compiled.rar)
(already compiled to L400 P700)
[https://help.ubuntu.com/community/ACPIBattery](https://help.ubuntu.com/community/ACPIBattery)

---

