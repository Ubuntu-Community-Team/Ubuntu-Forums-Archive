---
title: "laptop harddrive Load_Cycle_Count issue"
date: 2008-05-24
forum: Hardware
---

### Post by ubuntu_demon on 2008-05-24
**Don't apply any unofficial ugly fixes unless you understand what you are doing and you understand how to revert. Only apply this fix if you are heavily affected. After applying this fix keep an eye on your Load_Cycle_Count and on your harddrive temperature and make sure it remains below the maximum temperature specification of your harddrive. Also don't forget that having your harddisk head park protects your harddrive if you experience any bumps (which is especially nice if you are on the road and therefor probably working on battery). [COLOR="Red"]Everything you do is on your own risk.**[/COLOR]

Please give me feedback so I can improve this post.

**Not everyone is affected but here's a little bit of background.**

A lot of laptop drives are affected. Almost no desktop drives are affected except :
* possibly some "very green" drives which use very aggressive power management
* possibly some external drives which use laptop drives.

If your harddrive spins down and spins up again your Load_Cycle_Count increases by one. If your harddrive head parks and unparks again your Load_Cycle_Count increases by one. This is done to save power. Laptop harddrives can handle a limited number of Load_Cycles. Most of harddrives can handle at least 600.000 Load_Cycles but you should look it up for your specific model.

Laptop harddrives use more aggressive power management than desktop harddrives. Some laptop harddrives are using very aggressive power management (set by the laptop harddrive firmware or possibly by some laptop BIOS'es). Aggressive power management will cause your laptop's harddrive head to park quickly. Disk activity will unpark it again.

No disk activity at all will keep it parked. Constant disk activity won't park your harddrive head but this also causes wear and tear (MS Windows might be doing this). 

Regular disk activity with periods of no disk activity such as caused by ext3 journalling (which is safer for your data) or such as caused by firefox will park and unpark your harddrive head often. This combination of aggressive power management and regular disk activity is causing too rapidly increasing Load_Cycle_Counts for some people.

Look up how many Load_Cycle_Counts your harddrive can handle (most harddrives can handle 600.000 Load_Cycles but be sure to look it up). Calculate the average difference in Load_Cycle_Count per day. Now calculate what your Load_Cycle_Count will be in three years of harddrive use to determine whether you need to apply the ugly fix. This is explained inside the unofficial ugly fix.

So the causes for the problem are as follows :
* a lot of laptop harddrive firmwares set too aggressive power management settings
* this is probably not a problem for windows because there is probably almost constant disk activity (almost no head parks) so probably laptop harddrive manufacturers don't take this problem seriously
* the average linux laptop doesn't access the disk as often as windows but accesses it too often for a nice and long head park. 

The result for some laptop harddrives :
* increasing the Load_Cycle_Count beyond the specifications and therefor risking an early dead.

What we can do now :
* watch our Load_Cycle_Count and harddisk temperature
* we can report unnecessary disk activity bugs which will make our harddrive heads park longer
* for those of us who are heavily affected : the ugly fix is to disable harddrive power management while  on AC (no protection from bumps,increased heat) and enable harddrive power management while on battery (increased battery life,protection from bumps, less heat, fast rising Load_Cycle_Count)

The future :
* when linux becomes bigger and bigger on the laptop harddrive manufacturers will take this problem seriously
* flash storage is the future for laptop harddisks and doesn't have this problem (no moving parts)

**Unofficial Ugly Load_Cycle_Count Fix for Gutsy **
[http://ubuntuforums.org/showpost.php?p=5031046&postcount=2](http://ubuntuforums.org/showpost.php?p=5031046&postcount=2)

**Unofficial Ugly Load_Cycle_Count Fix for Hardy **
[http://ubuntuforums.org/showpost.php?p=5031046&postcount=3](http://ubuntuforums.org/showpost.php?p=5031046&postcount=3)

**Idea #288: Fix Hard Drive Load Cycle Problem in Laptops**
* [http://brainstorm.ubuntu.com/idea/288/](http://brainstorm.ubuntu.com/idea/288/)

**If you think Load_Cycle_Count didn't rise that quickly before :**
* See whether your swap is used (if there's a lot of swapping going on you might want to buy more ram): $ free -m 
* Try disabling tracker (system->preferences->search and indexing)

**More information :**

**The bug**
People should also consider reading the bug. It contains a lot of noise but some posts are very informative such as those by Bart Samwel who maintains laptop-mode-tools and acpi-support in Debian.
[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695)
[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/17216](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/17216) (same story here. this was the bug while 59695 was slashdotted)

**How to help finding disk activity bugs with blktrace (you can also use lm-profiler in addition) :**
[http://ubuntuforums.org/showpost.php?p=3722850&postcount=375](http://ubuntuforums.org/showpost.php?p=3722850&postcount=375)
[http://ubuntuforums.org/showpost.php?p=3805320&postcount=479](http://ubuntuforums.org/showpost.php?p=3805320&postcount=479)

**Possible disk activity bugs :**
* the commit interval for the ext3 filesystem should be higher than 5 seconds for laptop users by default (at least while on battery)
[https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/160448](https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/160448)

* ext3 partitions should be mounted with noatime or relatime 
[https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/160450](https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/160450)

* acpid : Log output far too verbose
[https://bugs.launchpad.net/ubuntu/+source/acpid/+bug/31512](https://bugs.launchpad.net/ubuntu/+source/acpid/+bug/31512)

* liferea might cause unnecessary disk activity
[https://bugs.launchpad.net/ubuntu/+source/liferea/+bug/160460](https://bugs.launchpad.net/ubuntu/+source/liferea/+bug/160460)

* thunderbird might cause unnecessary disk activity
[https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/160466](https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/160466)

* tracker : the index delay should be set to a higher value for laptop users
[https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/160468](https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/160468)

* firefox might cause unnecessary disk activity when going to a new website
[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/160513](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/160513)

* hddtemp might cause unnecessary disk activity
[https://bugs.launchpad.net/ubuntu/+source/hddtemp/+bug/160621](https://bugs.launchpad.net/ubuntu/+source/hddtemp/+bug/160621)

* tracker and cronjobs (updatedb, update-notifer,...) fight for the hard disk
[https://bugs.launchpad.net/ubuntu/+bug/152051/](https://bugs.launchpad.net/ubuntu/+bug/152051/)

* Don't install slocate by default on Desktops
[https://bugs.launchpad.net/ubuntu/+bug/140493/](https://bugs.launchpad.net/ubuntu/+bug/140493/)

* Firefox 3 keeps forcing disk to spin up when browsing because its sqlite storage calls fsync() for every recorded entry
[https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/221009/](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/221009/)

* liferea is slow on updating feeds if you have lots of feeds. multiple threads are needed for updating feeds.
[https://bugs.launchpad.net/ubuntu/+source/liferea/+bug/227976](https://bugs.launchpad.net/ubuntu/+source/liferea/+bug/227976)

**Other related bugs** :

laptop-mode-tools uses hparm -B 255 instead of 254 please sync laptop-mode-tools from Debian to fix this
[https://bugs.launchpad.net/ubuntu/+source/laptop-mode-tools/+bug/172282](https://bugs.launchpad.net/ubuntu/+source/laptop-mode-tools/+bug/172282)

hdparm's feedback about -B values is misleading
[https://bugs.launchpad.net/ubuntu/+source/hdparm/+bug/172287](https://bugs.launchpad.net/ubuntu/+source/hdparm/+bug/172287)

using laptop-mode causes system hangs for some people
[https://bugs.launchpad.net/ubuntu/+source/laptop-mode-tools/+bug/172293](https://bugs.launchpad.net/ubuntu/+source/laptop-mode-tools/+bug/172293)

laptop-mode should default to *always* use relatime for ext3 partitions while keeping the CONTROL_NOATIME option
[https://bugs.launchpad.net/ubuntu/+source/laptop-mode-tools/+bug/172301](https://bugs.launchpad.net/ubuntu/+source/laptop-mode-tools/+bug/172301)

scripts in /etc/pm/power.d should be called after resuming/ thawing
[https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/235105](https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/235105)

Please give me feedback so I can improve this post.

**Don't apply any unofficial ugly fixes unless you understand what you are doing and you understand how to revert. Only apply this fix if you are heavily affected. After applying this fix keep an eye on your Load_Cycle_Count and on your harddrive temperature and make sure it remains below the maximum temperature specification of your harddrive. Also don't forget that having your harddisk head park protects your harddrive if you experience any bumps (which is especially nice if you are on the road and therefor probably working on battery).[COLOR="Red"]Everything you do is on your own risk.**[/COLOR]

---

### Post by ubuntu_demon on 2008-05-24
**Unofficial Ugly Load_Cycle_Count Fix for Gutsy**

**Don't apply any unofficial ugly fixes unless you understand what you are doing and you understand how to revert. Only apply this fix if you are heavily affected. After applying this fix keep an eye on your Load_Cycle_Count and on your harddrive temperature and make sure it remains below the maximum temperature specification of your harddrive. Also don't forget that having your harddisk head park protects your harddrive if you experience any bumps (which is especially nice if you are on the road and therefor probably working on battery).[COLOR="Red"]Everything you do is on your own risk.**[/COLOR]

Please read why I'm recommending this solution if you are heavily affected : 
[http://ubuntuforums.org/showthread.php?p=5038155#post5038155](http://ubuntuforums.org/showthread.php?p=5038155#post5038155)

**Now to determine whether you actually suffer from this problem :**

To query S.M.A.R.T. data you need to install smartmontools :
```

$ sudo aptitude install smartmontools

```

If smartctl says your drive isn&#8217;t healthy anymore (for any reason) your harddrive might start dying soon.
```

$sudo smartctl -H /dev/sda

```

Now check how fast your Load_Cycle_Count is increasing (the last number is your Load_Cycle_Count) :
```

$ sudo smartctl -a /dev/sda | grep Load_Cycle_Count

```

Look up how many Load_Cycle_Counts your harddrive can handle (most harddrives can handle 600.000 Load_Cycles but be sure to look it up). Calculate the average difference in Load_Cycle_Count per day. Now calculate what your Load_Cycle_Count will be in three years of harddrive use to determine whether you need to apply the ugly fix. 

The smartctl values aren&#8217;t always easy to interpret. If the Load_Cycle_Counter value behaves as a counter and increments by steps of 1 and is below impossible to reach values it&#8217;s probably the right number.

You can also look at &#8220;WORST&#8221; and &#8220;THRESHOLD&#8221; (|more instead of |grep to easily see which value is &#8220;WORST&#8221; and which value is &#8220;THRESHOLD&#8221;) :
```

$ sudo smartctl -a /dev/sda | more

```

If WORST is lowering (too fast) than you might be suffering from this problem. You can roughly calculate how long it will take for WORST to reach THRESHOLD if you keep watching those values daily/weekly. The closer WORST is to THRESHOLD the likelier it is for your drive to die from a high Load_Cycle_Count. WORST often starts at 100 or 200 from what I have seen.

From [https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/17216/comments/40](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/17216/comments/40) :
[quote=Brian Visel]
Something to bear in mind as well:

smartmon does not always report SMART values as you might think. Different values are stored in different ways by different manufacturers.

Namely, if you do the smartctl check, wait for the click, and do it again immediately after, you may find that the amount has increased by more than one. In this case, it&#8217;s a pretty safe bet that the number you&#8217;re seeing isn&#8217;t accurate.

Also, it&#8217;s a pretty safe bet (though not guaranteed) that you can get the real value by dividing by the amount it increments by. So, if the value you see first is 477,296, and then it clicks once, and the value is 477,312 (difference of 16), it&#8217;s a pretty safe bet that the number you&#8217;re really dealing with is more along the lines of 29,831 to 29,832, in which case you have no worries.
[/quote]

If you think you might be suffering from this problem you might want to apply the ugly fix.

If you think your harddrive might start dying soon you should make backups of all your data and run the diagnostic tool of your harddrive manufacturer (which is probably included on the ultimate boot cd-rom).

**The ugly fix :**

**You should only apply this fix if you feel your Load_Cycle_Count is increasing too fast. You should only apply this fix if you understand what you are doing so that you can reverse it. Apply this fix on your own risk. Also don't forget that having your harddisk head park protects your harddrive if you experience any bumps (which is especially nice if you are on the road and therefor probably working on battery).**

Try the following :
```

$ sudo hdparm -B 254 /dev/sda

```

```

$ sudo hdparm -B 255 /dev/sda

```

One of these two will cause the drive will never be spun down and up again. 

If hdparm solved your problem let's make these settings permanent. But first read why I'm recommending this :
[http://ubuntuforums.org/showthread.php?p=5038155#post5038155](http://ubuntuforums.org/showthread.php?p=5038155#post5038155)

1) revert any previous fixes. remove all 99-hdd-spin-fix.sh files if any. comment the lines you added in /etc/hdparm.conf to fix this issue if any.
2) make a file named "99-hdd-ugly-fix.sh". The important thing is starting with "99".
```

$sudo gedit 99-hdd-ugly-fix.sh

```
3) make sure the file contains the following lines (fix it if you have PATA HDD):
```


#!/bin/bash
if on_ac_power; then
  # on AC so don't do any head parking
  hdparm -B 254 /dev/sda # you might need 255 or a different value
else
  # either on battery or power status could not be determined
  # so quickly park the head to protect the disk
  hdparm -B 128 /dev/sda
fi


```
4) copy this file to 4 locations:
```

$sudo install 99-hdd-ugly-fix.sh  /etc/acpi/resume.d/
$sudo install 99-hdd-ugly-fix.sh  /etc/acpi/start.d/
$sudo install 99-hdd-ugly-fix.sh  /etc/acpi/ac.d/
$sudo install 99-hdd-ugly-fix.sh /etc/acpi/battery.d/

```
By using install the file 99-hdd-ugly-fix.sh should have the x-bit set.

You probably shouldn't turn of head parking when on battery so **you probably shouldn't use 254** when on battery. You should want your harddisk to park/unpark in order to safe power and protect your harddisk from bumps while on battery that's why we are using 128 while on battery. You might want to experiment with numbers between 128 (most head parks, best protection from bumps, lower power usage) and 254 (no protection from bumps,no head parks,best performance,increased heat). All values below 254 still can do much head parks (depending on the harddrive) so you should keep watching your Load_Cycle_Count.

**Keep an eye on your harddisk temperature (for example using hddtemp) to make sure it doesn't exceed the harddisk's specifications. Keep an eye on your Load_Cycle_Count. ** If your Load_Cycle_Count is already close to it's specification (and behaves as a normal counter thus increments by 1) or your WORST is already at your THRESHOLD or very close to your THRESHOLD you should consider changing the "number for apm while on battery" (128) to 254 but you will lose any protection from bumps.

To get my disk temperature without disk activity (hddtemp causes disk activity) I'm using :
sudo smartctl -a /dev/sda | grep Temp

If you are worried about the temperature of your disk you might want to consider buying a laptop cooler. For my experiences with the Zalman ZM-NC2000 read : 
[http://ubuntuforums.org/showthread.php?t=818040](http://ubuntuforums.org/showthread.php?t=818040)
[http://ubuntuforums.org/showpost.php?p=5126803&postcount=4](http://ubuntuforums.org/showpost.php?p=5126803&postcount=4)

I didn't came up with this fix. Some contributions to this fix :
[https://launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/14](https://launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/14)
[https://launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/25](https://launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/25)
[https://launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/99](https://launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/99)
[http://www.linuxquestions.org/questions/showthread.php?p=2939397#post2939397](http://www.linuxquestions.org/questions/showthread.php?p=2939397#post2939397)
[http://ubuntuforums.org/showpost.php?p=3816734&postcount=487](http://ubuntuforums.org/showpost.php?p=3816734&postcount=487)

**Don't apply any unofficial ugly fixes unless you understand what you are doing and you understand how to revert. Only apply this fix if you are heavily affected. After applying this fix keep an eye on your Load_Cycle_Count and on your harddrive temperature and make sure it remains below the maximum temperature specification of your harddrive. Also don't forget that having your harddisk head park protects your harddrive if you experience any bumps (which is especially nice if you are on the road and therefor probably working on battery).[COLOR="Red"]Everything you do is on your own risk.**[/COLOR]

---

### Post by ubuntu_demon on 2008-05-24
**Unofficial Ugly Load_Cycle_Count Fix for Hardy (and later Ubuntu versions) **

**Don't apply any unofficial ugly fixes unless you understand what you are doing and you understand how to revert. Only apply this fix if you are heavily affected. After applying this fix keep an eye on your Load_Cycle_Count and on your harddrive temperature and make sure it remains below the maximum temperature specification of your harddrive. Also don't forget that having your harddisk head park protects your harddrive if you experience any bumps (which is especially nice if you are on the road and therefor probably working on battery).[COLOR="Red"]Everything you do is on your own risk.**[/COLOR]

Please give me feedback so I can improve this post.

First read the first two posts of this thread which explain the problem and the fix for Gutsy :
[http://ubuntuforums.org/showpost.php?p=5031046&postcount=1](http://ubuntuforums.org/showpost.php?p=5031046&postcount=1) 
[http://ubuntuforums.org/showpost.php?p=5031046&postcount=2](http://ubuntuforums.org/showpost.php?p=5031046&postcount=2) 

acpi-support is being switched over to pm-utils. So the Gutsy fix might work for you in Hardy but it will probably not work any more in future releases (AFAIK). So the the Hardy fix is a work in progress to find a clean solution which will not depend on acpi-support but only on pm-utils in order to make it future proof. But the same principles apply so be sure to read the fix for Gutsy so you understand what you are doing. 

Here's the fix for Hardy :
[http://en.opensuse.org/Disk_Power_Management](http://en.opensuse.org/Disk_Power_Management)

The temperature of the disk seems a little bit higher for me in Hardy. Watch it very carefully!

I'm experimenting with these values but you might need different values :
```

DEVICES_DISK_PM_POWERSAVE_OFF="hdparm -q -B 254 -q -S 0"
DEVICES_DISK_PM_POWERSAVE_ON="hdparm -q -B 128 -q -S 0"

```

Also read about why I am recommending these values :
[http://ubuntuforums.org/showpost.php?p=5038155&postcount=15](http://ubuntuforums.org/showpost.php?p=5038155&postcount=15)

hddtemp bug :
[http://ubuntuforums.org/showpost.php?p=5049492&postcount=27](http://ubuntuforums.org/showpost.php?p=5049492&postcount=27)

This probably doesn't work for suspend/resume. We'll have to figure out what's the cleanest pm-utils based solution which works for suspend/resume. My laptop doesn't reliably suspend/resume so I can't test any suggested solutions myself. 

The cleanest way I can currently think of is that this should be fixed is by making pm-utils call the scripts in /etc/pm/power.d after resuming/thawing. If that's done then Suse's workaround will work even after suspend/resume without any adaption.

I just reported this bug against pm-utils :
[https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/235105](https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/235105)
[quote=ubuntu_demon]
scripts in /etc/pm/power.d should be called after resuming/ thawing

Why ?
* the laptop might have switched from AC to battery or the other way around
* the harddrive 's apm settings might be reset to the default state
* this is needed for a clean workaround for the Load_Cycle_Count issue
[/quote]

To make sure your drive's apm settings are correct do the following after resume on battery :
```

sudo hdparm -B 128 /dev/sda

```

To make sure your drive's apm settings are correct do the following after resume on AC :
```

sudo hdparm -B 254 /dev/sda

```
To get your disk temperature without disk activity (hddtemp causes disk activity) use :
sudo smartctl -a /dev/sda | grep Temp

If you are worried about the temperature of your disk you might want to consider buying a laptop cooler. For my experiences with the Zalman ZM-NC2000 read :
[http://ubuntuforums.org/showthread.php?t=818040](http://ubuntuforums.org/showthread.php?t=818040)
[http://ubuntuforums.org/showpost.php?p=5126803&postcount=4](http://ubuntuforums.org/showpost.php?p=5126803&postcount=4)

Please give me feedback so I can improve this post.

**Don't apply any unofficial ugly fixes unless you understand what you are doing and you understand how to revert. Only apply this fix if you are heavily affected. After applying this fix keep an eye on your Load_Cycle_Count and on your harddrive temperature and make sure it remains below the maximum temperature specification of your harddrive. Also don't forget that having your harddisk head park protects your harddrive if you experience any bumps (which is especially nice if you are on the road and therefor probably working on battery).[COLOR="Red"]Everything you do is on your own risk.**[/COLOR]

---

### Post by hotweiss on 2008-05-24
I have a problem, the load cycle count issue comes back after I resume my computer from suspend. I'm using Ubuntu 8.04.

---

### Post by sam_delta on 2008-05-24
> **hotweiss said:**
> I have a problem, the load cycle count issue comes back after I resume my computer from suspend. I'm using Ubuntu 8.04.

you copied the script to resume.d? ```
 sudo install 99-hdd-ugly-fix.sh  /etc/acpi/resume.d/ 
```

sam

---

### Post by Arthur Archnix on 2008-05-24
I have a similar problem with the SUSE fix using Hardy as Hotweiss, but only if I resume while on ac. If I resume from suspend on battery the SUSE fix applies the hdparm setting of B at 200 correctly. This is regardless of whether I suspended while on battery or on AC. If I resume while on AC it reverts to 128. From boot on either battery or ac the correct settings are applied (e.g., 200 on Battery, disabled on AC). This is a pretty clean install of Hardy with the following changes:

I've uninstalled cron, anacron, sysklog, klogged, trackered, and mapped acpid logging to /dev/null. I've upped ext3 committ time to 30 seconds and set data mode to write back while using noatime on all partitions. While having nothing open or running but my gnome desktop load/cycle counts increase by about once per 3 or 4 seconds. 

Unfortunately in my case, this is almost certainly a case of bad HD firmware. I appreciate all the hard word demon put into his Gutsy fix. Aside from the minor annoyance of having to manually unplug the power cord and plug it back in after suspend, the suse fix works fine for me under Hardy. Perhaps one day soon we'll have a reliable script that will trick Ubuntu into thinking that the plug has been removed and inserted after a suspend. Until then, thanks again Ubuntu Demon.

Hotweiss, have you checked before suspend, after suspend, while on a/c and battery, and the various combinations? And after resume fom suspend if you unplug and plug back in does it adopt correct settings?

I'm using the following command to query the setting:
```
sudo hdparm -I /dev/sda | grep level
```If you use the command on the SUSE link to check there is no way to tell if a setting of 128 or 200 is applied, because it only shows on versus off for power management. The command above will give you the exact power saving number, or disabled.

EDIT: re sam's comment above, that only applies to gutsy. Those scripts aren't used nor installed to those locations on Hardy. At least, that's my understanding and someone will correct me if I'm mistaken.

---

### Post by garoth2 on 2008-05-24
I'm not certain whether Hardy is actually using pm-utils. Using the instructions on the opensuse site - placing that script in /etc/pm/config.d did not execute/change my PM settings.

I tried putting the scripts in /etc/acpi/* and it seems to have worked

---

### Post by Rayaz on 2008-05-24
> **garoth2 said:**
> I'm not certain whether Hardy is actually using pm-utils. Using the instructions on the opensuse site - placing that script in /etc/pm/config.d did not execute/change my PM settings.

I tried putting the scripts in /etc/acpi/* and it seems to have worked

Can confirm putting scripts in /etc/acpi/* works for Hardy. 
Though am concerned about the HDD temperature which has gone from 29 C to 46 C in 30 minutes just browsing the net.:(

---

### Post by garoth2 on 2008-05-24
Are you sure about that first reading?

My HDD temp seems to not have changed much. About 40-45 deg C

---

### Post by hotweiss on 2008-05-24
> **Arthur Archnix said:**
> I have a similar problem with the SUSE fix using Hardy as Hotweiss, but only if I resume while on ac. If I resume from suspend on battery the SUSE fix applies the hdparm setting of B at 200 correctly. This is regardless of whether I suspended while on battery or on AC. If I resume while on AC it reverts to 128. From boot on either battery or ac the correct settings are applied (e.g., 200 on Battery, disabled on AC). This is a pretty clean install of Hardy with the following changes:

I've uninstalled cron, anacron, sysklog, klogged, trackered, and mapped acpid logging to /dev/null. I've upped ext3 committ time to 30 seconds and set data mode to write back while using noatime on all partitions. While having nothing open or running but my gnome desktop load/cycle counts increase by about once per 3 or 4 seconds. 

Unfortunately in my case, this is almost certainly a case of bad HD firmware. I appreciate all the hard word demon put into his Gutsy fix. Aside from the minor annoyance of having to manually unplug the power cord and plug it back in after suspend, the suse fix works fine for me under Hardy. Perhaps one day soon we'll have a reliable script that will trick Ubuntu into thinking that the plug has been removed and inserted after a suspend. Until then, thanks again Ubuntu Demon.

Hotweiss, have you checked before suspend, after suspend, while on a/c and battery, and the various combinations? And after resume fom suspend if you unplug and plug back in does it adopt correct settings?

I'm using the following command to query the setting:
```
sudo hdparm -I /dev/sda | grep level
```If you use the command on the SUSE link to check there is no way to tell if a setting of 128 or 200 is applied, because it only shows on versus off for power management. The command above will give you the exact power saving number, or disabled.

EDIT: re sam's comment above, that only applies to gutsy. Those scripts aren't used nor installed to those locations on Hardy. At least, that's my understanding and someone will correct me if I'm mistaken.

I'm still having the same problem even after applying the ugly fix. I ran sudo hdparm -I /dev/sda | grep level after suspend and resume, and got this:

> Advanced power management level: 128

Since I'm on AC power shouldn't it be 254?

---

### Post by hotweiss on 2008-05-24
OK, I found a fix! This worked for me:

[http://ubuntuforums.org/showpost.php?p=4897802&postcount=842](http://ubuntuforums.org/showpost.php?p=4897802&postcount=842)

This actually by far is the best fix. I only used the above instructions after a clean install and now my hard drive has stopped clicking; even after resuming from suspend.

---

### Post by BandD on 2008-05-25
@ hotweiss:

That is the fix that I also use.  But it is not ideal for all people.  Some people desire to have different settings when on AC vs. Battery power.  This fix doesn't allow for that.  It rather just locks the defualt hdparm value to 254 (or whatever number you put there).

But for anyone who doesn't care about different values between AC and Battery power, it works just as well.

---

### Post by hotweiss on 2008-05-25
> **BandD said:**
> @ hotweiss:

That is the fix that I also use.  But it is not ideal for all people.  Some people desire to have different settings when on AC vs. Battery power.  This fix doesn't allow for that.  It rather just locks the defualt hdparm value to 254 (or whatever number you put there).

But for anyone who doesn't care about different values between AC and Battery power, it works just as well.

I don't think you'll get more than an extra 5 minutes of life even with the most aggressive hard drive power management settings. The only problem with the other solution posted here is that it doesn't work after you resume from suspend. None the less, a true fix would be nice.

---

### Post by Rayaz on 2008-05-25
> **garoth2 said:**
> Are you sure about that first reading?

My HDD temp seems to not have changed much. About 40-45 deg C


Yep, quite sure about the readings. Just started up my laptop and the readings jumped from 36 C to 40 C in 10 minutes. Should I disable uglyfix? My hard drive temperature range is from 5 to 60 C according to manufacturer specs.

---

### Post by ubuntu_demon on 2008-05-25
**Don't apply any unofficial ugly fixes unless you understand what you are doing and you understand how to revert. Only apply this fix if you are heavily affected. After applying this fix keep an eye on your Load_Cycle_Count and on your harddrive temperature and make sure it remains below the maximum temperature specification of your harddrive. Also don't forget that having your harddisk head park protects your harddrive if you experience any bumps (which is especially nice if you are on the road and therefor probably working on battery). [COLOR="Red"]Everything you do is on your own risk.**[/COLOR]

**Why I am recommending 128 while on battery and 254 while on AC** as values to try first for those who are heavily affected.

For most disks the default is 128 which is important to have while on battery (protection from bumps,less heat,less power) compared to a higher value.

The solution in the unofficial ugly fix I encourage uses 128 while on battery and uses 254 while on AC. 254 turns power management down or off (high I/O) for most harddrives and thus stops increasing the load_cycle_count while on AC. But please only do this kind of thing if you understand what you are doing. Also please keep monitoring your harddisk temperature.

If you get better results (less heat without rapid increasing Load_Cycle_Count) by using a different apm value you are free to experiment with values between 128 and 255 while on AC. The reason I'm advocating 254 (highest I/O) is that it works for a lot of harddrives. Another value which works for a lot of harddrives is 255 (disabling power management altogether). Harddrive manafucturars do different things for values between 128 and 254 so it's impossible to recommend a single number between 128 and 254. "man hdparm" gives a little bit of explanation about these values.

In most cases it is unwise to use a different value than 128 while on battery. The biggest reason to use an apm of 128 while on battery would be to protect the harddisk from bumps. Even if the laptop is used on battery everyday for four hours the Load_Cycle_Count would have to increase with 137 per hour to be able to reach 600.000 within three years of usage. Most people don't see their Load_Cycle_Count increase that fast (although some might). Most people don't use their laptop for four hours on battery each day. Those people who are afraid they will still reach the maximum Load_Count as specified by their manufacturer within three years of usage do need to tweak the "apm number while on battery".

I'm using a laptop cooler (Zalman ZM-NC2000) while using my laptop on AC. If you are worried about the temperature of your disk you might want to consider buying a laptop cooler. For my experiences with the Zalman ZM-NC2000 read :
[http://ubuntuforums.org/showthread.php?t=818040](http://ubuntuforums.org/showthread.php?t=818040)
[http://ubuntuforums.org/showpost.php?p=5126803&postcount=4](http://ubuntuforums.org/showpost.php?p=5126803&postcount=4)

If I use my laptop on my lap with AC plugged in I often manually issue a "hdparm -B 128 /dev/sda" to get protection from bumps.

From :
[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/232](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/232)
[quote=ubuntu_demon]
I'm currently recommending this to people who are heavily affected :
* use apm 128 while on battery (most head parks, best protection from bumps, lower power usage)
* use apm 254 while on AC (no protection from bumps,no head parks,best performance,increased heat)

The biggest reason to do so would be to protect the harddisk from bumps. Even if the laptop is used on battery everyday for four hours the Load_Cycle_Count would have to increase with 137 per hour to be able to reach 600.000 within three years of usage. Most people don't see their Load_Cycle_Count increase that fast (although some might). Most people don't use their laptop for four hours on battery each day. Those people who are afraid they will still reach the maximum Load_Count as specified by their manufacturer within three years of usage do need to tweak the "apm number while on battery".
[/quote]

**Don't apply any unofficial ugly fixes unless you understand what you are doing and you understand how to revert. Only apply this fix if you are heavily affected. After applying this fix keep an eye on your Load_Cycle_Count and on your harddrive temperature and make sure it remains below the maximum temperature specification of your harddrive. Also don't forget that having your harddisk head park protects your harddrive if you experience any bumps (which is especially nice if you are on the road and therefor probably working on battery). [COLOR="Red"]Everything you do is on your own risk.**[/COLOR]

---

### Post by calraith on 2008-05-25
laptop: Acer Aspire 4520 (info probably relevant to the 5520 and 7520 as well)
hdd: Toshiba MK1246GSX 120GB SATAII
hdd firmware revision: LB213J

What I've noticed is that using any hdparm -B value from 192 - 254 will make the drive run near or at its maximum temperature (52C), but will cause Load_Cycle_Count to decrease to next to nothing.  Values 128 - 191 make the drive run at around 45C, but Load_Cycle_Counts to Minutes ratio is about 3:2.  There seems to be no incremental difference in the values.  Results are the same for any value from 128 to 191 (temp around 45C,  15 load cycles every 10 minutes); and the same for 192 to 254 (temp around 51C, fewer load cycles).

I ran my tests using the following command:
```
date; sudo smartctl -a /dev/sda | grep -i -E '(load_cycle|temp)'
```Powertop suggests a few other tweaks which could be relevant:
> Suggestion: increase the VM dirty writeback time from 5.00 to 15 seconds with:
  echo 1500 > /proc/sys/vm/dirty_writeback_centisecs
This wakes the disk up less frequenty for background VM activity

Suggestion: Enable SATA ALPM link power management via:
  echo min_power > /sys/class/scsi_host/host0/link_power_management_policy

Suggestion: Disable 'hal' from polling your cdrom with:
hal-disable-polling --device /dev/cdrom
'hal' is the component that auto-opens a window if you plug in a CD but disables SATA power saving from kicking in.An acquaintance of mine (micr0c0sm on EFnet) also suggests mounting /tmp and /var/tmp into RAM:
> 11:39 < micr0c0sm> its easy, just make sure you dont have anything in /var/tmp that expects to be persistent
11:39 < micr0c0sm> relevant lines from my /etc/fstab:
11:39 < micr0c0sm> shm          /dev/shm     tmpfs     nosuid,mode=1777,noatime 0 0
11:39 < micr0c0sm> /dev/shm     /tmp          none     bind               0 0
11:39 < micr0c0sm>  /tmp          /var/tmp     none     bind               0 0
11:41 < micr0c0sm> shm is shared memory (aka ram)
11:41 < micr0c0sm> mode=1777 nosuid makes sure its safe from executing silly things
11:41 < micr0c0sm> noatime means don't write the time any file in there is accessed, theres no point to there
11:42 < [BAFtop]> w.t.f.
11:42 < [BAFtop]> [http://farm3.static.flickr.com/2279/2386684684_9db54ab0e2.jpg](http://farm3.static.flickr.com/2279/2386684684_9db54ab0e2.jpg)
11:42 < [BAFtop]> ^ WTF
11:42 < micr0c0sm> bind lets you bind a mount, kind of like a softlink but much better when mounting
11:42 < micr0c0sm> so i bind my shared memory to /tmp/ and /var/tmp
11:42 < micr0c0sm> so both of those are the same directory, and they grow as necessary
11:42 < Twintop> [BAFtop]: WTF is right
11:42 < micr0c0sm> i also have 4gb of ram and never go above 1.2gb with caches so its safe
He also notes the following:
> 11:11 < micr0c0sm> i'll check my cycles soon, but heres the thing: 600,000 is the minimum cycles that most hard drives could fail
11:11 < micr0c0sm> the actual numbers are close to twice that
11:12 < micr0c0sm> what happens is the manufacturers try out 1,000 drives, and the first five failures, whichever has the highest number of cycle writes is the spec they rate at
11:12 < micr0c0sm> while the other 995 cycle 2x that
11:12 < micr0c0sm> this is all very rough heard from a friend/forum stuff but the gist is, you drive isn't gonna die at exactly 600k
11:13 < micr0c0sm> still, its a good idea to keep the heads parked or keep them readingCan anyone help confirm or deny his observation?

I'm thinking the only way truly to balance operating temperature with power saving would be for me to crontab a script to run every 5 or 10 minutes, similar to this:
```
#!/bin/bash
## Save to a file, chmod +x, and run as root or with sudo.
## example root crontab entry:
## */10 * * * *    /path/to/hdd_power.sh >/dev/null 2>&1

HDPARM_POWERSAVE=128
HDPARM_PERFORMANCE=254
HDPARM_HDD="/dev/sda"
## degrees within the maximum temperature to switch to power saving
## For instance, if max operating temp is 52 and this value is 1,
## when the drive reaches 51 degrees or higher, power save will
## activate...
HDPARM_DEGREES_WITHIN_MAX_HIGH=1

## ... until the drive has cooled to at least this many degrees
## below max temp.
HDPARM_DEGREES_WITHIN_MAX_LOW=5

### END OF VARIABLES ###

function fnPowerSave {
    echo "Configuring for power save / frequent head parking."
    hdparm -B $HDPARM_POWERSAVE $HDPARM_HDD
}

function fnPerformance {
    echo "Configuring for performance / infrequent head parking."
    hdparm -B $HDPARM_PERFORMANCE $HDPARM_HDD
}

function fnInstall {
    apt-get install -y --force-yes $1
}

if [ `whoami` != "root" ]; then {
    echo "$0 should be run as root or with sudo."
    exit 1
}; fi

if [ ! -f "`which smartctl`" ]; then fnInstall smartmontools; fi
if [ ! -f "`which hdparm`" ]; then fnInstall hdparm; fi
if [ ! -f "`which on_ac_power`" ]; then fnInstall powermgmt-base; fi

on_ac_power
RETVAL=$?
if [ $RETVAL -eq 255 ]; then {
    echo "Power state could not be determined.  Skipping hdparm."
    exit 1
} elif [ $RETVAL -eq 1 ]; then {
    echo -n "Running on battery power.  "
    fnPowerSave
    exit 0
}; fi
strSMART=`smartctl -n standby -a /dev/sda | grep -i 'temp'`
currTEMP=`echo $strSMART | awk '{ print $10 }'`
maxTEMP=`echo $strSMART | sed -r -e 's/.+(..).$/\1/'`
echo "Temperature: $currTEMP celsius ($maxTEMP max)"
if [ $currTEMP -ge $(($maxTEMP - $HDPARM_DEGREES_WITHIN_MAX_HIGH)) ]; then {
    fnPowerSave
    exit 0
}; fi
if [ $currTEMP -le $(($maxTEMP - $HDPARM_DEGREES_WITHIN_MAX_LOW)) ]; then {
    fnPerformance
}; fi

exit 0
```

---

### Post by frodon on 2008-05-25
I desactivated laptop_mode to try the fix proposed on the suze page however applying the fix with the vlues suggested by ubuntu_demon heads do not park anymore (i added relatime parameter to the ubuntu partition).
Temperature seems fine however (around 46C max).

This is on acer aspire 5720G, anyone noticed such behaviour too with the unofficial hardy fix ?

---

### Post by garoth2 on 2008-05-25
> **Rayaz said:**
> Yep, quite sure about the readings. Just started up my laptop and the readings jumped from 36 C to 40 C in 10 minutes. Should I disable uglyfix? My hard drive temperature range is from 5 to 60 C according to manufacturer specs.
I'm not sure of the significance of the temperature... it's still below the maximum by a large margin. I installed sensors-applet and hddtemp (run as daemon), which shows my hdd temperature on my gnome menu bar which I find quite handy for monitoring it.

I don't remember my hard drive ever running that cool (~30 deg C) except when it's been off for a while and just boots. I have my power management level at 200 now and it sits between 40-45 deg.

Also to others - I installed the latest laptop-mode-tools (not necessary to install the latest) to control my HDD power management. It doesn't seem to mess up my system at all like it suggests in /etc/default/acpi-support in the comments. You have to edit that file to allow laptop-mode to operate. Then edit all of the config files in /etc/laptop-mode/conf.d and /etc/laptop-mode/laptop-mode.conf. The HDD settings are in laptop-mode.conf.

One thing I found though is that even when laptop mode enabled, the power.sh script forces the power management level anyway. So you also have to change the values in /etc/acpi/power.sh (in the lines where it specifies $HDPARM -B value) in order for the settings in laptop-mode.conf to stick.

---

### Post by hotweiss on 2008-05-26
Hmmm, I just ran smartmon in Vista, and the problem is there to.

---

### Post by BandD on 2008-05-26
@ calraith:

On this thread's predecessor a member named blackhole54 made similar observations about the way HD manufacturers calculate the maximum number of load cycles.  And it makes sense.  It's kinda like 100,000 mile warranties on cars, by the time you get there it should last quite a bit longer, but it does have some wear and tear--it certainly isn't new any more.



On another note, I can confirm hotweiss's observations about the Suse ugly fix not working properly when resuming from Suspend when on AC.  So now I'm going back to the fix from jakon referenced by hotwiess at the top of page two.

---

### Post by Arthur Archnix on 2008-05-26
> **ubuntu_demon said:**
> For most disks the default is 128 which is important to have while on battery (protection from bumps,less heat,less power) compared to a higher value.... In most cases it is unwise to use a different value than 128 while on battery. 

In that case Demon, you should confirm the finer points of the SUSE fix you're recommending. They appear to use a setting of 200 while on battery. Perhaps a rewrite with sudo appropriate commands and your recommended battery settings?

If you do use a setting of 200, as opposed to 128. And you check using Level instead of just Advanced Power Management, then the following strange problem appears with the SUSE fix: 

After resuming from suspend, if you are on AC power, incorrect settings are applied. 128 is applied. If you resume while on battery, the correct settings are applied (e.g., I have battery set to 200, and that is applied to the disk correctly). After resuming from suspend on AC and finding that the wrong settings are applied, everything works as it should regarding power changes. So, if you switch to battery power the correct settings will be applied. And if you switch to battery then AC quickly, the correct AC settings are applied.

Some people have "confirmed" that settings are not restored after suspend. Can you please confirm that this is only while on AC, and that it works fine resuming from battery. Also, does switching power sources apply the correct settings? Eg., fix it. Remember to use the command I gave above instead of the command on the SUSE page, and you may also need to temporarily change your Battery setting to 200 just to see the difference more clearly. After your "experiment", please remember to restore it to whatever default battery setting you've chosen.

PS. I'm on one of those cursed machines that mysteriously hang when using laptopmode. So I'm a little more limited in terms of what solutions I can try.

PPS. I've edited the Suse Fix to save you some work Demon. If you choose to go that way. The only changes are the use of sudo, renaming the script with a sh extension, and setting battery to 128.

And I tried editing my own configuration file to see if playing with the 255 254 values would help with my resume from suspend problem and it did not.

---

### Post by barbarian on 2008-05-26
thank you a lot guys, me just going to install kubuntu on Dell XPS m1330..

---

### Post by Kestol on 2008-05-26
Well... I really hope people can help me out here.. Got some questions...

1. If i put my powermangement to 254 while on AC, do i get any benefits besides the lower parking count?

2. If i want to achieve a parking count of 5-15 per hour while on AC, what should i try to add? Since 254-255 disables it tottally... And i think 5-15 parkings per hour sounds save for smaller bumps.
And does a count lower then 254/255 have any negative effects?

3. With bumps, do you mean smaller things like an elbow accidently hitting the laptop.. Or do it have to be bigger impacts?

4. Is a HD tempature from 40-45 alright while idle?

That's all for now...
Hope really people can help me,... I'll definatly be gratefull:popcorn:

---

### Post by hotweiss on 2008-05-26
> **Kestol said:**
> Well... I really hope people can help me out here.. Got some questions...

1. If i put my powermangement to 254 while on AC, do i get any benefits besides the lower parking count?

2. If i want to achieve a parking count of 5-15 per hour while on AC, what should i try to add? Since 254-255 disables it tottally... And i think 5-15 parkings per hour sounds save for smaller bumps.
And does a count lower then 254/255 have any negative effects?

3. With bumps, do you mean smaller things like an elbow accidently hitting the laptop.. Or do it have to be bigger impacts?

4. Is a HD tempature from 40-45 alright while idle?

That's all for now...
Hope really people can help me,... I'll definatly be gratefull:popcorn:

I don't understand how the power management parking can protect the hard drive from damage caused by bumps. This sort of protection can only be achieved with a shock sensor. I had a shock sensor in my old Toshiba but I disabled it due to the fact that ever little movement would cause my drive to park, thus slowing down my computer. The glitch that we are discussing here causes the hard drive to park randomly and then immediately to restart.

---

### Post by frodon on 2008-05-26
When the heads are parked they are not close to the disk making thus the disk is more protected against bump as the heads has really few chance to hit the disk. However there are others way how bumps can damage a drive and head parking won't help on this.

---

### Post by Kestol on 2008-05-26
Well thx for the comment on my post... But i would really apreciate a answer for all 4 questions:)

> **Kestol said:**
> Well... I really hope people can help me out here.. Got some questions...

1. If i put my powermangement to 254 while on AC, do i get any benefits besides the lower parking count?

2. If i want to achieve a parking count of 5-15 per hour while on AC, what should i try to add? Since 254-255 disables it tottally... And i think 5-15 parkings per hour sounds save for smaller bumps.
And does a count lower then 254/255 have any negative effects?

3. With bumps, do you mean smaller things like an elbow accidently hitting the laptop.. Or do it have to be bigger impacts?

4. Is a HD tempature from 40-45 alright while idle?

That's all for now...
Hope really people can help me,... I'll definatly be gratefull:popcorn:

---

### Post by ubuntu_demon on 2008-05-26
> **garoth2 said:**
> I'm not sure of the significance of the temperature... it's still below the maximum by a large margin. I installed sensors-applet and hddtemp (run as daemon), which shows my hdd temperature on my gnome menu bar which I find quite handy for monitoring it.


Running hddtemp as a deaemon is not a good idea because hddtemp causes unnecessary disk activity itself which can cause an increase in Load_Cycle_Count. See :
[https://bugs.launchpad.net/ubuntu/+source/hddtemp/+bug/160621](https://bugs.launchpad.net/ubuntu/+source/hddtemp/+bug/160621)

I can get the temperature without an increase of Load_Cycle_Count with my harddisk in the following way :
sudo smartctl -a /dev/sda | grep emperature

---

### Post by ubuntu_demon on 2008-05-26
I updated the post which explains the unofficial ugly fix for Hardy regarding suspend/resume :
[http://ubuntuforums.org/showpost.php?p=5031047&postcount=3](http://ubuntuforums.org/showpost.php?p=5031047&postcount=3)

---

### Post by BandD on 2008-05-26
> **Kestol said:**
> Well... I really hope people can help me out here.. Got some questions...

1. If i put my powermangement to 254 while on AC, do i get any benefits besides the lower parking count?

2. If i want to achieve a parking count of 5-15 per hour while on AC, what should i try to add? Since 254-255 disables it tottally... And i think 5-15 parkings per hour sounds save for smaller bumps.
And does a count lower then 254/255 have any negative effects?

3. With bumps, do you mean smaller things like an elbow accidently hitting the laptop.. Or do it have to be bigger impacts?

4. Is a HD tempature from 40-45 alright while idle?

That's all for now...
Hope really people can help me,... I'll definatly be gratefull:popcorn:

1.  You could see slightly lower HD temps.  Which is always good.

2.  You can try any value between 124 and 255.  Different HD manufacturers assign different values for different behaviors, so you'll have to experiment a little.

3.  Probably bigger impacts, though I suppose it depends on how hard you hit it with your elbow.  The heads float above the actual disk via a magnetic field, so it has to be powerful enough to break that field.

4.  Most drives' higher range operating temperature is some where around 50 C.  So an idle temp of 45 is perhaps a little warm, but still within the 'normal' bounds.

---

### Post by frodon on 2008-05-27
Seagate disks are in general made for a maximum temperature of 60C, after an hour of use my hdd temp has always been around 45-47C this without and without head parking, i guess it mainly depends on how good is your laptop cooling system.

---

### Post by gloryplastic on 2008-05-27
Thanks for your ideas, good for us~

---

### Post by SupaSonic on 2008-05-27
I was just wondering if it's an issue on windows xp / vista. A guy at work just lost a hard drive on a dell laptop running xp. There's a million reasons for this I'm sure, but this is the first thing that came to my mind.

---

### Post by efplaya on 2008-05-27
I dont seem to have load_cycle_count i only have power_cycle_count, is this the same thing?

---

### Post by Kestol on 2008-05-27
> **ubuntu_demon said:**
> **Unofficial Ugly Load_Cycle_Count Fix for Hardy**

**Don't apply any unofficial ugly fixes unless you understand what you are doing and you understand how to revert. Only apply this fix if you are heavily affected. After applying this fix keep an eye on your Load_Cycle_Count and on your harddrive temperature and make sure it remains below the maximum temperature specification of your harddrive. Also don't forget that having your harddisk head park protects your harddrive if you experience any bumps (which is especially nice if you are on the road and therefor probably working on battery).[COLOR="Red"]Everything you do is on your own risk.**[/COLOR]

Please give me feedback so I can improve this post.

First read the first two posts of this thread which explain the problem and the fix for Gutsy :
[http://ubuntuforums.org/showpost.php?p=5031046&postcount=1](http://ubuntuforums.org/showpost.php?p=5031046&postcount=1) 
[http://ubuntuforums.org/showpost.php?p=5031046&postcount=2](http://ubuntuforums.org/showpost.php?p=5031046&postcount=2) 

Hardy switched to pm-utils so the fix is a little bit different for Hardy. But the same principles apply so be sure to read the fix for Gutsy so you understand what you are doing. But putting 99-hdd-ugly-fix.sh in /etc/acpi/* won't work for Hardy.

Here's the fix for Hardy :
[http://en.opensuse.org/Disk_Power_Management](http://en.opensuse.org/Disk_Power_Management)

The temperature of the disk seems a little bit higher for me in Hardy. Watch it very carefully!

I'm experimenting with these values but you might need different values :
```

DEVICES_DISK_PM_POWERSAVE_OFF="hdparm -q -B 254 -q -S 0"
DEVICES_DISK_PM_POWERSAVE_ON="hdparm -q -B 128 -q -S 0"

```

Also read about why I choose these values :
[http://ubuntuforums.org/showpost.php?p=5038155&postcount=15](http://ubuntuforums.org/showpost.php?p=5038155&postcount=15)

hddtemp bug :
[http://ubuntuforums.org/showpost.php?p=5049492&postcount=27](http://ubuntuforums.org/showpost.php?p=5049492&postcount=27)

This probably doesn't work for suspend/resume. We'll have to figure out what's the cleanest solution for this in Hardy. Since acpi-support is replaced by pm-utils and I'm not sure whether /etc/acpi/* solutions will work in Hardy and will remain working in the future (Intrepid,Interpid+1,...). My laptop doesn't reliably suspend/resume so I can't test any suggested solutions myself. 

Cleanest way I can currently think of is that this should be fixed is by making pm-utils call the scripts in /etc/pm/power.d after resuming/thawing. If that's done Suse's workaround will work even after suspend/resume without any adaption.

I just reported this bug against pm-utils :
[https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/235105](https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/235105)


Please give me feedback so I can improve this post.

**Don't apply any unofficial ugly fixes unless you understand what you are doing and you understand how to revert. Only apply this fix if you are heavily affected. After applying this fix keep an eye on your Load_Cycle_Count and on your harddrive temperature and make sure it remains below the maximum temperature specification of your harddrive. Also don't forget that having your harddisk head park protects your harddrive if you experience any bumps (which is especially nice if you are on the road and therefor probably working on battery).[COLOR="Red"]Everything you do is on your own risk.**[/COLOR]

Hmmm I have hardy but i am using the gutsy fix.. And it seems to work... 
Why do u say it doesnt work then?

---

### Post by Thorzilla on 2008-05-27
> **SupaSonic said:**
> I was just wondering if it's an issue on windows xp / vista. A guy at work just lost a hard drive on a dell laptop running xp. There's a million reasons for this I'm sure, but this is the first thing that came to my mind.


I think it is. I do know for a fact that my Toshiba was crashed by Vista for the same reason - whenever I told someone I thought my computer was clicking too much, they looked at me like I was crazy.

---

### Post by efplaya on 2008-05-27
can anyone tell me if load_count_cycle is the same as power_count_cycle since i do not have load_count_cycle as one of my attributes

---

### Post by hotweiss on 2008-05-27
> **SupaSonic said:**
> I was just wondering if it's an issue on windows xp / vista. A guy at work just lost a hard drive on a dell laptop running xp. There's a million reasons for this I'm sure, but this is the first thing that came to my mind.

Yes, I have the same glitch in Vista.

---

### Post by bajun on 2008-05-27
Fix for Hardy (OpenSuse maintained) [http://ubuntuforums.org/showpost.php?p=5031047&postcount=3]("http://ubuntuforums.org/showpost.php?p=5031047&postcount=3") works wery well for me in any situation on laptop with 2.6.24-17-rt kernel. Independently from power events, whether the battery has been switched off or on during suspend or hypernate (EDIT: afte suspend und hypernate hdparm was set to 128 again).

Of course, after some test with different -B values I have applied suitable with my disk and environment as here:
```
# Powersave mode off
#  Disable APM and set spin-down for 2 hours
#
DEVICES_DISK_PM_POWERSAVE_OFF="hdparm -q -B 254 -q -S 244"
#
# Powersave mode on
# Enable APM to conservative 128 and set spin-down for 21 minutes
#
DEVICES_DISK_PM_POWERSAVE_ON="hdparm -q -B 128 -q -S 252"
```

Thank you for this link, ubuntu_demon

---

### Post by BandD on 2008-05-27
> **efplaya said:**
> can anyone tell me if load_count_cycle is the same as power_count_cycle since i do not have load_count_cycle as one of my attributes


Power_Cycle_Count is NOT the same as Load_Cycle_Count.  Power_Cycle_Count merely counts how many times you turn the disk on and off (system shutdown, restart, standby, resume, boot, etc).

Load_Cycle_Count counts the number of times the drive parks the heads.

I don't know if there is anything you can do to find this value.  If it isn't showing up in smartmontools then your drive may not support that Smart value.

You should be able to hear the heads parking rapidly if you are experiencing this issue.  It's usually a decent clicking on and off pretty close together.  If you think you hear more than several clicks a minute, then try running:

```
sudo hdparm -B 254 /dev/sda
```

and see if the clicks stop. If they don't try a value of 255 instead.  If they stop, then the "ugly fix" will work for you.

---

### Post by AbtZ on 2008-05-27
I have found a solution that works for me.

I first used [this guide]("http://vale.homelinux.net/wordpress/2007/10/24/potential-risk-for-your-nx6325s-harddrive/") to get laptop mode going. This will deal with the parking issue as such.

However, after resuming from suspending hdparm was set to 128 again, unless I unplugged the computer from AC power and then reconnected it.

With [Jakon's guide]("http://ubuntuforums.org/showpost.php?p=4897802&postcount=842") this is remedied. The problem here is that if you resume while running on battery power hdparm will be set to 254 and you have to plug & unplug from AC to get power saving mode going again.

This works fine for me, however, since I mostly run my laptop on AC power, only occasionally disconnecting it.

---

### Post by ubuntu_demon on 2008-05-29
> **Kestol said:**
> Hmmm I have hardy but i am using the gutsy fix.. And it seems to work... 
Why do u say it doesnt work then?

I updated my post which will answer your question :
[http://ubuntuforums.org/showpost.php?p=5031047&postcount=3](http://ubuntuforums.org/showpost.php?p=5031047&postcount=3)

---

### Post by dodecaman on 2008-05-30
> **frodon said:**
> Seagate disks are in general made for a maximum temperature of 60C, after an hour of use my hdd temp has always been around 45-47C this without and without head parking, i guess it mainly depends on how good is your laptop cooling system.

I want to second Frodon's statement - before you get too excited about your temperature, be sure you know your manufacturer's specs.  My WD Scorpio has a max temp of 60C.  It takes about 45 minutes on my kitchen table to get up to 40-45C and hovers around there, but I've only seen it top 50C once.  Now, if you're the type who actually sits with your laptop ON YOUR LAP - you're probably making the temp rise faster due to poor circulation - invest in a lap board.

---

### Post by Keyper7 on 2008-05-31
I can also confirm that the unofficial ugly fix for Hardy works for me even after a suspend or hibernate. Everything seems to be perfect.

I have a Dell Vostro 1400 with a Samsung HD.

---

### Post by Thorzilla on 2008-05-31
Hi Everyone, from what little I understood of all the discussion about this issue, I managed to extract the following info from my computer. Would someone be kind enough to tell me whether I need to apply the fix or not?
I ran the sudo hdparm -B 254 command and the clicking reduced noticeably.
But it still clicks quite often...
I've installed Ubuntu Hardy 8.04, and I dual boot with Vista. It's a Toshiba A215-S4747 and the following...


---------------------------
Model Family:     Toshiba 2.5" HDD series (80 GB and above)
Device Model:     TOSHIBA MK2035GSS
Serial Number:    773IF90TS
Firmware Version: DK020M
User Capacity:    200,049,647,616 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Sat May 31 15:09:55 2008 EDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled
----------------------------


ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      
UPDATED  WHEN_

FAILED RAW_VALUE

  1 Raw_Read_Error_Rate     0x000b   100   100   050    Pre-fail  Always       -
       0
  2 Throughput_Performance  0x0005   100   100   050    Pre-fail  Offline      -
       0
  3 Spin_Up_Time            0x0027   100   100   001    Pre-fail  
Always       -
       1176
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -
       49
  5 Reallocated_Sector_Ct   0x0033   100   100   050    Pre-fail  Always       -
       0
  7 Seek_Error_Rate         0x000b   100   100   050    Pre-fail  Always       -
       0
  8 Seek_Time_Performance   0x0005   100   100   050    Pre-fail  Offline      -
       0
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -
       77
 10 Spin_Retry_Count        0x0033   100   100   030    Pre-fail  Always       -
       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -
       46
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -
       0
193 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -
       1383
194 Temperature_Celsius     0x0022   100   100   000    Old_age   Always       -
       37 (Lifetime Min/Max 15/49)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -
       0
197 Current_Pending_Sector  0x0032   100   100   000    Old_age   Always       -
       0
198 Offline_Uncorrectable   0x0030   100   100   000    Old_age   Offline      -
       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -
       1
220 Disk_Shift              0x0002   100   100   000    Old_age   Always       -
       8267
222 Loaded_Hours            0x0032   100   100   000    Old_age   Always       -
       67
223 Load_Retry_Count        0x0032   100   100   000    Old_age   Always       -
       0
224 Load_Friction           0x0022   100   100   000    Old_age   Always       -
       0
226 Load-in_Time            0x0026   100   100   000    Old_age   Always       -
       318
240 Head_Flying_Hours       0x0001   100   100   001    Pre-fail  Offline      -
       0






I tried to include as much information, while excluding what seemed pointless, do tell me if you need anything else.

Thanks a million!

TZ

---

### Post by BandD on 2008-05-31
@ Thorzilla

It's hard to say exactly how bad the issue is for you.  If you take your current Load_Cycle_Count and divide it by Power_On_Hours you get a lifetime average of about 17 cycles/hour...which isn't really all that bad.  But lifetime average my not be all that accurate...  

If I were you I'd experiment with the hdparm values a little.  Fist don't set any value, let the drive just be. Note the number of Load_Cycle_Count and then let it run for an hour (or 30 minutes, etc) and see what it averages out to be.  If it seems high to you (keep in mind that many people seem to be comfortable with 5-50/hour, or a little more, depending on how much you are using the computer and how aggressive you want power management to be), then try out some different hdparm values and notice how much the Load_Cycle_Count jumps by after an hour or so.

---

### Post by quanumphaze on 2008-06-01
The Hardy/OpenSUSE hack works fine for me except for after suspend/resume where it resets to 128. I can also confirm that (un)plugging the power supply will run the scripts and fix it.

I am willing to try any hacks to make it run the script after resume.

---

### Post by Thorzilla on 2008-06-01
> **BandD said:**
> @ Thorzilla

It's hard to say exactly how bad the issue is for you.  If you take your current Load_Cycle_Count and divide it by Power_On_Hours you get a lifetime average of about 17 cycles/hour...which isn't really all that bad.  But lifetime average my not be all that accurate...  

If I were you I'd experiment with the hdparm values a little.  Fist don't set any value, let the drive just be. Note the number of Load_Cycle_Count and then let it run for an hour (or 30 minutes, etc) and see what it averages out to be.  If it seems high to you (keep in mind that many people seem to be comfortable with 5-50/hour, or a little more, depending on how much you are using the computer and how aggressive you want power management to be), then try out some different hdparm values and notice how much the Load_Cycle_Count jumps by after an hour or so.


Thanks! I did some experimentation, and the numbers seemed rather scary to me. With a bit more searching, I found that my hard drive is listed among those affected - also, it was Vista that crashed my drive with the same symptoms.So I went ahead and applied the ugly fix, and now the count barely ever increases and all is well with the world.

---

### Post by armitage1337 on 2008-06-01
> **Thorzilla said:**
> it was Vista that crashed my drive with the same symptoms.

So this is a problem in Windows too? I thought the issue was tied to ext3. What if I'm using the ext3 driver for Windows available at [http://www.fs-driver.org/](http://www.fs-driver.org/) , would that result in the same issue?

And to be clear, this isn't a problem when the battery is removed and I'm using outlet power, correct?

---

### Post by BandD on 2008-06-01
Double Post.  See Below.

---

### Post by BandD on 2008-06-01
> **armitage1337 said:**
> So this is a problem in Windows too? I thought the issue was tied to ext3. What if I'm using the ext3 driver for Windows available at [http://www.fs-driver.org/](http://www.fs-driver.org/) , would that result in the same issue?

And to be clear, this isn't a problem when the battery is removed and I'm using outlet power, correct?


The problem seems to be with the firmware hard drive manufacturers ship with their hard drives.  The problem has been reported across all major operating systems, including Windows and OSX.  

Some think it is more prevalent on Linux systems because Linux is more efficient and actually gives the drive some time to rest, where as Windows many times doesn't (bloatware).  

With regards to being on ac/battery power, it depends on your drive.  Some drives' firmware is so bad, that nothing will fix the problem.  The best way to find out is to use smartmontools (you can install via Synaptic):

```
sudo smartctl -a /dev/sda
```

Make a note of the Load_Cycle_Count and then let the system run normally and check again after an hour.  Ideally, depending on how heavy your usage was during that time you shouldn't be in upwards of 50 cycles/hour--and that might be a little high.  If you are below 20/hour I'd say there is nothing to worry about.  At that rate your drive should last well over 3 years, assuming it's on 24/7.  Try it with AC plugged in once, and then test it while on battery.  If you have questions report back.

---

### Post by Kokopelli on 2008-06-01
To see how fast load count is going up on my laptops I usually do
```

 while (true); do date;sudo smartctl -a /dev/sda |grep Load;sleep 600; done

```

Then leave it running. You can then get an idea of what the load count is increasing by every 10 min,  (Amusingly enough on my spare laptop the load count ia at 378693.)

---

### Post by UTPanda on 2008-06-02
Sorry, I'm a total Noob here.  I've done the SUSE fix for Hardy and it works with the exception of when I resume from sleep while on AC.  I was going to try to copy the scripts to /etc/acpi/* as suggested in earlier posts but does that mean I need to copy both of the scripts to all of the subfolders?

Do I copy the scripts to 
/etc/acpi/ac.d
/etc/acpi/battery.d
/etc/acpi/events 
and so on 

or do I just copy the scripts to 
/etc/acpi/resume.d

or do I just copy the scripts to:
/etc/acpi


Sorry for such an elementary question.
Thanks,

---

### Post by Zetheroo on 2008-06-02
ubuntu_demon:

I have a Thinkpad T60 and the drive was clocking about 150 cycles in 15 min.

I applied the following ([https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/14]("https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/14")) and now it seems completely fixed.

Was this fix ok... or are there some cons to using this particular fix?

Thanks:KS

---

### Post by BandD on 2008-06-02
@ Zetheroo

The fix you've applied is basically the fix for Gutsy that Ubuntu Demon offers, minus /etc/acpi/battery.d location, and there aren't really any cons for HARDY.  

On the first page of this thread, post #3 Ubuntu Demon writes his reasoning for offering a different fix for Hardy:

> acpi-support is being switched over to pm-utils. So the Gutsy fix might work for you in Hardy but it will probably not work any more in future releases (AFAIK). So the the Hardy fix is a work in progress to find a clean solution which will not depend on acpi-support but only on pm-utils in order to make it future proof. But the same principles apply so be sure to read the fix for Gutsy so you understand what you are doing.

So while it may still work in Hardy, he's trying to provide a long term fix.

---

### Post by Zetheroo on 2008-06-02
BandD:

Ok thanks! Should I copy the script to the battery.d/ folder as well?

Also how does this script effect the hard drive when on battery power? ... like does the hdd slow down when on battery power etc?

Thanks:KS

---

### Post by BandD on 2008-06-03
The script you are using uses a value of 255 ALWAYS, which turns power management off all together.  So make sure to watch you HD temperature.  If you want things to change while on battery power, see the fix for Gutsy in post #2 of this thread, 

How your computer reacts on battery is up to you.  If you want you can completely disable power management (as your script does), but some people report high hard drive temperatures, which is worse than Load Cycles (normal working temps are between 35-60 C depending on the drive), and you are also less protected from bumbs which can damage the drive.  Ubuntu Demon recommends a setting of 128 while on battery power, which is arrgessive.  You can experiement with numbers here if you want.

---

### Post by BandD on 2008-06-03
> **UTPanda said:**
> Sorry, I'm a total Noob here.  I've done the SUSE fix for Hardy and it works with the exception of when I resume from sleep while on AC.  I was going to try to copy the scripts to /etc/acpi/* as suggested in earlier posts but does that mean I need to copy both of the scripts to all of the subfolders?

Do I copy the scripts to 
/etc/acpi/ac.d
/etc/acpi/battery.d
/etc/acpi/events 
and so on 

or do I just copy the scripts to 
/etc/acpi/resume.d

or do I just copy the scripts to:
/etc/acpi


Sorry for such an elementary question.
Thanks,


If you want to try the Gutsy fix on Hardy, you could try just putting them in resume.d.  If that doesn't work then try adding them to all the subfolders  listed in the Gusty fix of post #2 of this thread.

---

### Post by athiwatc on 2008-06-03
I wonder why MS does not have this problem??
  Its using the disk all the time??
So why dont we use make linux kernel use the disk all the time like MS.

---

### Post by frodon on 2008-06-03
Any OS (windows included) has this issue, some more than others.

---

### Post by Zetheroo on 2008-06-03
> **BandD said:**
> The script you are using uses a value of 255 ALWAYS, which turns power management off all together.  So make sure to watch you HD temperature.  If you want things to change while on battery power, see the fix for Gutsy in post #2 of this thread, 

How your computer reacts on battery is up to you.  If you want you can completely disable power management (as your script does), but some people report high hard drive temperatures, which is worse than Load Cycles (normal working temps are between 35-60 C depending on the drive), and you are also less protected from bumbs which can damage the drive.  Ubuntu Demon recommends a setting of 128 while on battery power, which is arrgessive.  You can experiement with numbers here if you want.

OK. I might be getting this wrong .... but are you saying that I can put a different script in effect for the machine when on battery power?
Do I do this by the following:

Create a file named 99-hdd-spin-fix.sh
Enter the following to lines of code into the file ..

#!/bin/sh
hdparm -B 128 /dev/sda

and then copy the newly created file in the battery.d folder?

Thanks:KS

---

### Post by Zetheroo on 2008-06-03
> **frodon said:**
> Any OS (windows included) has this issue, some more than others.

Is this really the case? I looked it up online and found close to nothing about it in relation to MS Windows!?

Do you have any documentation of the issue being prevalent in MS Windows?
:KS

---

### Post by frodon on 2008-06-03
Yes it is the case and no except tones of feedback everywhere on internet (including here) i have nothing such as MS documentation.

Unfortunately there's no published study about which OS is the most impacted by this head parking annoyance, so all we have is user feedback reporting this on MS, MACOS and linux.

---

### Post by BandD on 2008-06-03
> **Zetheroo said:**
> OK. I might be getting this wrong .... but are you saying that I can put a different script in effect for the machine when on battery power?
Do I do this by the following:

Create a file named 99-hdd-spin-fix.sh
Enter the following to lines of code into the file ..

#!/bin/sh
hdparm -B 128 /dev/sda

and then copy the newly created file in the battery.d folder?

Thanks:KS

That should do the trick. But I can't be sure if Hardy will still use the scripts in that folder or not...

It seems that it may still work, but as Ubuntu Demon points out, it might not work for future releases.

---

### Post by Zetheroo on 2008-06-03
> **frodon said:**
> Yes it is the case and no except tones of feedback everywhere on internet (including here) i have nothing such as MS documentation.

Unfortunately there's no published study about which OS is the most impacted by this head parking annoyance, so all we have is user feedback reporting this on MS, MACOS and linux.

The thing is that I have not seen anyone posting the test results from a MS Windows machine .... anywhere on the internet. This leadds me to wondering if it happens much at all in Windows or maybe the average Windows user is a lot less clued in on some of these and other more technical issues.

I am also wondering if perhaps MS Windows alone on a PC would still cause the hdd to be effected by this issue, but that maybe with the customized tools and utilities (made by Lenovo, Toshiba etc....) may "repair" the issue!? Or does it not work this way?

---

### Post by frodon on 2008-06-03
> **Zetheroo said:**
> The thing is that I have not seen anyone posting the test results from a MS Windows machine .... anywhere on the internet.My advice :
Search better (a simple ubuntuforums search will give you results)

This is something most users following this bug since it exists know. I wonder why but for some users this is something they don't want to believe.

---

### Post by Alfred_McGee on 2008-06-03
This fix did not work at first- my load cycle count continued to rise by 160 or more per hour, and then suddenly, a few days later, after a few restarts and suspends and several thousand more load cycle counts, it suddenly stopped rising. All's well that ends well, I guess.

---

### Post by sergiom99 on 2008-06-03
Hey there, I just found this thread and now I am really worried.
I have an HP Laptop (specs in signature) with a **TOSHIBA MK1637GSX HDD**.
I am fairly new to Ubuntu on laptops, I always used Linux in servers.

Anyway, I am worried about this thing, and I am not sure if I am affected or if I should do something.

Here are my count cycles:
```
Tue Jun  3 21:13:23 ART 2008
193 Load_Cycle_Count        0x0032   099   099   000    Old_age   Always       -       **16607**
194 Temperature_Celsius     0x0022   100   100   000    Old_age   Always       -       36 (Lifetime Min/Max 13/51)
sergio@kubuntu:~$ date; sudo smartctl -a /dev/sda | egrep '(Load_Cycle_Count|Temperature)'
Tue Jun  3 22:24:28 ART 2008
193 Load_Cycle_Count        0x0032   099   099   000    Old_age   Always       -       **16725**
194 Temperature_Celsius     0x0022   100   100   000    Old_age   Always       -       37 (Lifetime Min/Max 13/51)

```
My system:
Kubuntu HH
2.6.24-17-generic i686 kernel
KDE 3.5.9
Qt 3.3.8b

Thanks for your help, i really appreciate it. Laptops are not cheap in Argentina, so I am really concerned about HDD lifespan.

---

### Post by swarup on 2008-06-03
I am a bit confused: does this bug only affect newer systems that use Sata drives and ACPI (which only started post-2002)? I did also see on the bug description, reference to "advanced APM" also affecting systems. As I understand, APM refers to the power management system that was used before ACPI. And computers will not have both-- either they have APM, or ACPI. 

My laptop is vintage 1999 (Gateway 9300)-- so I assume it uses "APM". I wanted to confirm whether my laptop is affected by this rapid load cycles phenomenon.

So I installed smartctl using Synaptic, and then did:

```
swarup@swarup-laptop:~$ sudo smartctl -a /dev/hda5 | grep Load_Cycle_Count
swarup@swarup-laptop:~$ 
```

As you see, there was no output whatsoever.

So I tried

```
swarup@swarup-laptop:~$ sudo smartctl -H /dev/sda5
smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

Warning! Drive Identity Structure error: invalid SMART checksum.
=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED
```

What is the bottom line from all this? Did I get any meaningful information? Is my computer being affected by the bug, or was the smartctl test for some reason unable to check for it on my system? How come it didn't give a load cycle count report?

---

### Post by athiwatc on 2008-06-04
> **Zetheroo said:**
> The thing is that I have not seen anyone posting the test results from a MS Windows machine .... anywhere on the internet. This leadds me to wondering if it happens much at all in Windows or maybe the average Windows user is a lot less clued in on some of these and other more technical issues.

I am also wondering if perhaps MS Windows alone on a PC would still cause the hdd to be effected by this issue, but that maybe with the customized tools and utilities (made by Lenovo, Toshiba etc....) may "repair" the issue!? Or does it not work this way?

Yes, i think MS does not have any problem (i guess)
  I TESTED first i install ubuntu 8.04 I test on both ac and battery both give me the sound of parking and spin up and down but i see one think on ac it will give the sound less often

But on window vista ultimate 32x there is no sound of parking on both ac and battery but there is sound of spin up and down

But in the same time that mean MS is using the hard disk all the time and not parking the head. And that should not be good right??

This doesn't mean it function this way I TESTED FROM SOUND THAT COME OUT FROM MY HD ONLY!!!!!

---

### Post by athiwatc on 2008-06-04
Dubble post sorry

---

### Post by Alfred_McGee on 2008-06-04
Could someone please tell me how to undo this fix? Yesterday, there was a time when it appeared to have worked, but now my load cycle count has gone back to continuous increase -whether running on battery or not- about 200 cycles per hour. Once, on a previous install of Ubuntu, I used the load cycle count fix posted by nicedude, and it worked perfectly. I don't know if it was any different from this one, but it seems like I ought to try it again.

---

### Post by rabusmar on 2008-06-04
I've just found this issue on my new Compal IFL92, hd Seagate ST9200420AS, and the Load_Cycle_Count increased over 140 per hour. I applied the fix on ubuntu hardy x64 and the counter stopped, but the temperature increased up to stable at 48 (max 60). Thanks for the support

---

### Post by BandD on 2008-06-04
> **sergiom99 said:**
> Hey there, I just found this thread and now I am really worried.
I have an HP Laptop (specs in signature) with a **TOSHIBA MK1637GSX HDD**.
I am fairly new to Ubuntu on laptops, I always used Linux in servers.

Anyway, I am worried about this thing, and I am not sure if I am affected or if I should do something.

Here are my count cycles:
```
Tue Jun  3 21:13:23 ART 2008
193 Load_Cycle_Count        0x0032   099   099   000    Old_age   Always       -       **16607**
194 Temperature_Celsius     0x0022   100   100   000    Old_age   Always       -       36 (Lifetime Min/Max 13/51)
sergio@kubuntu:~$ date; sudo smartctl -a /dev/sda | egrep '(Load_Cycle_Count|Temperature)'
Tue Jun  3 22:24:28 ART 2008
193 Load_Cycle_Count        0x0032   099   099   000    Old_age   Always       -       **16725**
194 Temperature_Celsius     0x0022   100   100   000    Old_age   Always       -       37 (Lifetime Min/Max 13/51)

```
My system:
Kubuntu HH
2.6.24-17-generic i686 kernel
KDE 3.5.9
Qt 3.3.8b

Thanks for your help, i really appreciate it. Laptops are not cheap in Argentina, so I am really concerned about HDD lifespan.


sergiom99,

Your Load_Cycle_Count is increasing by about 100 per hour.  That is high.  Ideally it should be between 5-50 per hour.  There are several fixes available that seem to work with Hardy Heron.  I would recommend trying Ubuntu Demon's fix in [post #3]("http://ubuntuforums.org/showpost.php?p=5031047&postcount=3") on the first page of this thread.  The actual fix is found [here]("http://en.opensuse.org/Disk_Power_Management"), on the OpenSUSE support site.

Some people have noticed that if you resume from suspend or hibernate that the fix stops working while on AC power until you either restart, or unplug and plug back in the power cord.

This problem won't kill your laptop.  The only thing it could do is cause your hard drive to die earlier than expected.  It is usually very easy and cheap to replace the hard drive in a laptop.  So don't worry too much.

---

### Post by BandD on 2008-06-04
> **Alfred_McGee said:**
> Could someone please tell me how to undo this fix? Yesterday, there was a time when it appeared to have worked, but now my load cycle count has gone back to continuous increase -whether running on battery or not- about 200 cycles per hour. Once, on a previous install of Ubuntu, I used the load cycle count fix posted by nicedude, and it worked perfectly. I don't know if it was any different from this one, but it seems like I ought to try it again.


To remove the fix all you have to do is delete the two files you created:

```
sudo rm /etc/pm/config.d/disk
```
```
sudo rm /etc/pm/power.d/disk
```

Be careful, make sure you type these commands exactly as they are written!!!

You can always set the hdparm value manually by typing the following in a terminal:

```
 sudo hdparm -B 254 /dev/sda
```

Any time you notice your drive is parking its heads like crazy, then run that command.  If that doesn't work, try a value of 255.  If that doesn't work, then your drive just doesn't respond to hdparm and there's not a lot you can do...

---

### Post by sergiom99 on 2008-06-04
> **BandD said:**
> sergiom99,

Your Load_Cycle_Count is increasing by about 100 per hour.  That is high.  Ideally it should be between 5-50 per hour.  There are several fixes available that seem to work with Hardy Heron. 

Thanks BandD, glad you answered. I am really worried about this. Laptops and laptop parts are not that cheap here.

When I upgraded to HH, it really messed my install, so I am wondering about doing a fresh HH install or doing a fresh GG install. (compiz/emerald not working nice, the only way to reboot/powroff is from Konsole b/c from Kmenu I get a black screen, and others)

---

### Post by Alfred_McGee on 2008-06-04
Thanks BandD. I guess I'll continue to use Ubuntu_Demon's fix, but set my hdparm value manually, as you suggest, though actually I think my problem is the one that you mention in #72: My load cycle count continues to escalate following a suspend. I don't recall being able to solve the problem by momentarily unplugging, however, but I'll try it again.

---

### Post by Zetheroo on 2008-06-05
BandD:

Ok... I was just told by someone that using the *hdparm -B 255 /dev/sda* script completely disables the HDD Parking feature leaving your HDD vulnerable to bumps and jolts ... which is not cool at all.

Is there no other alternative to the 255? -- something not as aggressive as 128 but also something that does not render your HDD defenseless to bumps and the like!?

---

### Post by BandD on 2008-06-05
Zetheroo:

You can use ANY number between 1 (most advanced) and 255 (completely disabled), though depending on the drive manufacturer different values will have different results.  Ubuntu Demon recommends a value of 254 (least aggressive, but not disabled) while on AC power.  Perhaps I should have tried to make a little more clear in my previous post to you.  This is from the man page of hdparm:

```
-B      Set Advanced Power Management feature, if the drive supports it.
              A low value means aggressive power management and a  high  value
              means better performance.  Possible settings range from values 1
              through 127 (which permit spin-down), and values 128 through 254
              (which  do  not  permit spin-down).  The highest degree of power
              management is attained with a setting of 1, and the highest  I/O
              performance  with a setting of 254.  A value of 255 tells hdparm
              to disable Advanced Power Management  altogether  on  the  drive
              (not all drives support disabling it, but most do).
```

But different drives react differently to the different settings.  Some drives will not respond to ANYTHING except a 255 value, some see noticeable changes incrementally.  

My advice is to try manually, with out any scripts or fixes.  Set different hdparm -B values ranging from 128-254 by using the following in a terminal:

```
sudo hdparm -B 200 /dev/sda
``` 

as an example.  Play around with differnt values, monitor the number of cycles you have in an hour period, and see what you feel comfortable with.  

I personally ALWAYS (on and off battery) use a value of 254.  My rationale: as soon as the heads park, they un-park again almost immediately, so protection from bumps seems null and void to me.  Others disagree.  I also don't notice any increase in battery life with a lesser value.  So its easier for me to always be on 254.

---

### Post by Arthur Archnix on 2008-06-05
I tried the Gutsy fix on a clean Hardy install and it worked fine. So, for those of you less concerned about being future proof and more concerned about it just working right now, give the Gutsy fix a try.

I switched over to Lenny because of stability issues and it seems to be fixed on a default install. That is, if you choose to install the laptop components during setup, it automatically adjusts your hdparm settings to either 254 or 128 based on power. This is true after a suspend / resume cycle as well. So, once intrepid hits the stores they should have synced with debian and resolved this as well.

Hopefully. ;)

---

### Post by Zetheroo on 2008-06-05
> **BandD said:**
> Zetheroo:

You can use ANY number between 1 (most advanced) and 255 (completely disabled), though depending on the drive manufacturer different values will have different results.  Ubuntu Demon recommends a value of 254 (least aggressive, but not disabled) while on AC power.  Perhaps I should have tried to make a little more clear in my previous post to you.  This is from the man page of hdparm:

```
-B      Set Advanced Power Management feature, if the drive supports it.
              A low value means aggressive power management and a  high  value
              means better performance.  Possible settings range from values 1
              through 127 (which permit spin-down), and values 128 through 254
              (which  do  not  permit spin-down).  The highest degree of power
              management is attained with a setting of 1, and the highest  I/O
              performance  with a setting of 254.  A value of 255 tells hdparm
              to disable Advanced Power Management  altogether  on  the  drive
              (not all drives support disabling it, but most do).
```

But different drives react differently to the different settings.  Some drives will not respond to ANYTHING except a 255 value, some see noticeable changes incrementally.  

My advice is to try manually, with out any scripts or fixes.  Set different hdparm -B values ranging from 128-254 by using the following in a terminal:

```
sudo hdparm -B 200 /dev/sda
``` 

as an example.  Play around with differnt values, monitor the number of cycles you have in an hour period, and see what you feel comfortable with.  

I personally ALWAYS (on and off battery) use a value of 254.  My rationale: as soon as the heads park, they un-park again almost immediately, so protection from bumps seems null and void to me.  Others disagree.  I also don't notice any increase in battery life with a lesser value.  So its easier for me to always be on 254.

I entered the line ```
sudo hdparm -B 200 /dev/sda
``` into the terminal and then checked my cycle count. Then hours later I checked it again and it had not changed. What does this mean?

---

### Post by Sealbhach on 2008-06-05
I've got 59 load cycles in the last hour so I'm not too worried.

I've set the power management to 254 anyway, since I hardly ever use battery.

I've got a Fujitsu MHY2200BH

> === START OF INFORMATION SECTION ===
Device Model:     FUJITSU MHY2200BH
Serial Number:    K41KT7A28DC4
Firmware Version: 0000000B
User Capacity:    200,049,647,616 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  Not recognized. Minor revision code: 0x42
Local Time is:    Thu Jun  5 20:58:52 2008 BST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

It says my device is not in smartctl database. ??

I was just wondering how to find out if this drive is affeced by the bug. Is there a list of affected drives???


.

---

### Post by BandD on 2008-06-05
Zetheroo:

It means your heads haven't parked.  If you would like them to park then try a lesser value.  Start at 128 and work your way up to a value that suits your needs.


Sealbhach:

I'm not sure about a list of drives affected.  I get the same thing about my drive not being in the database (Western Digital). The easiest way to tell is to monitor the Load_Cycle_Count value from smartmontools.  If you are averaging 59/hour under decent usage, then you probably don't need to worry too much.  As your drive begins to age, you may want to apply some sort of constraint, but if the drive is relatively new, you don't have a whole lot to worry about in my opinion.

But it's totally up to you.  The most important thing here is to find a balance that suits your needs.

---

### Post by ZapalacX on 2008-06-06
I set hdparm to 254 and it stopped the cycles, but after a while my HD temp got up to 55C from ~35C so I turned it off. Is there any way to keep the temperature down as well as stop the rapid cycling?

---

### Post by frodon on 2008-06-06
@ZapalacX, try other values than 254, maybe 220 or less, make some test and try to find the best compromise between reducing head parking and temperature.
Now if you have a standard drive and get 55C after an hour or two of use then i would say this is normal. As told before in this thread common maximum drive temperature is 60C (seagate drives taken as reference), my drive idle temperature is around 47-48C but i can make it go to 55C or more easily just if i put my laptop on my knees an thus reduce the fan air input.

---

### Post by Zetheroo on 2008-06-06
> **BandD said:**
> Zetheroo:

It means your heads haven't parked.  If you would like them to park then try a lesser value.  Start at 128 and work your way up to a value that suits your needs.



OK... I ma trying that out as I am writing this...

Just wondering.... what is a healthy amount of cycles within a time frame of 15 min?
Some say 2-4 loads cycles in 15 min is too much.... is this true?

Also isn't the head only supposed to park when a jolt or a jerky movement is felt?

---

### Post by ubuntu_demon on 2008-06-06
I'm using a laptop cooler (Zalman ZM-NC2000) while using my laptop on AC. If you are worried about the temperature of your disk you might want to consider buying a laptop cooler. For my experiences with the Zalman ZM-NC2000 read :
[http://ubuntuforums.org/showthread.php?t=818040](http://ubuntuforums.org/showthread.php?t=818040)
[http://ubuntuforums.org/showpost.php?p=5126803&postcount=4](http://ubuntuforums.org/showpost.php?p=5126803&postcount=4)

I also updated the following post about why I am recommending 128 and 254 (to try first if you are heavily affected) :
[http://ubuntuforums.org/showthread.php?p=5038155#post5038155](http://ubuntuforums.org/showthread.php?p=5038155#post5038155)

---

### Post by ubuntu_demon on 2008-06-06
> **Zetheroo said:**
> OK... I ma trying that out as I am writing this...

Just wondering.... what is a healthy amount of cycles within a time frame of 15 min?
Some say 2-4 loads cycles in 15 min is too much.... is this true?


That's probably not too much. But you should probably look at a bigger timeframe to be sure (days or weeks for example).

Look at the specification of your harddrive and your current Load_Cycle_Count (if your Load_Cycle_Count seems to behave as a normal counter) and compare these two values. Keep watching your Load_Cycle_Count and if you feel (calculate) your Load_Cycle_Count is approaching the specifications of your drive too fast you might want to take action (if you understand what you are doing).

For example : 
If the specifications for your drive say 600.000 for Load_Cycle_Count and you are running Ubuntu for a month (with the default apm value for the drive) with a Load_Cycle_Count of 10.000 then you are probably save for at least 60 months. But you should keep watching your Load_Cycle_Count and see how it develops. 

> **Zetheroo said:**
> 
Also isn't the head only supposed to park when a jolt or a jerky movement is felt?

Sadly this isn't suppored in GNU/Linux yet. A little bit of explanation in this video : 
[http://www.archive.org/details/LRL_USA_2008_Power_Management_Anger](http://www.archive.org/details/LRL_USA_2008_Power_Management_Anger)

---

### Post by Zetheroo on 2008-06-06
OK... I have been trying different hdparm commands and what I have come up with is not at all consistent!

For example in one test using *sudo hdparm -B 152 /dev/sda* in the terminal I clocked an average of 4 cycles every 15 minutes. But then another time with the exact same hdparm -B value of 152 I clocked an average of 45 cycles per 15 minutes.

Why the inconsistency?

Here is my drive info:

```
Model Family:     Hitachi Travelstar 5K100 series
Device Model:     HTS541010G9SA00
Serial Number:    MP2ZXAXLH306US
Firmware Version: MBZIC60R
User Capacity:    100,030,242,816 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  ATA/ATAPI-7 T13 1532D revision 1
Local Time is:    Fri Jun  6 15:55:05 2008 SAST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled
```


Here are the other tests I have done:

```

hdparm -B 130 /dev/sda

1 min -- 7 cycles
(10 min -- 70 cycles)

hdparm -B 140 /dev/sda

10 min -- 10 cycles

hdparm -B 150 /dev/sda

10 min -- 19 cycles

hdparm -B 180 /dev/sda

12 min -- 28 cycles

hdparm -B 190 /dev/sda

10 min -- 28 cycles

hdparm -B 150 /dev/sda

10 min -- 14 cycles

hdparm -B 155 /dev/sda

10 min -- 26 cycles

hdparm -B 151 /dev/sda

100 min -- 61 cycles

10 min -- 6 cycles

hdparm -B 152 /dev/sda

16 min -- 4 cycles

100 min -- 326 cycles
```

---

### Post by inderjeetk on 2008-06-07
Hi Everyone
I am using ACER laptop Aspire 3682NWXCi
My laptop is not charging as soon as power goes it gives message of critical battery it shows battery charged 9% but on system tray it shows on AC power and also while charging it does not show orange light for charging it shows yellow to indicate on fully charged

May i know the solution for this
I had tried my battery on other same laptop it is working and other battery is also not working on my laptop
i had restarted my laptop and placed again battery

Thanks in advance

---

### Post by sergiom99 on 2008-06-07
applied the GG fix and everything seems stable now. (im on AC)
I used a value of 228 for battery. what does it mean? is that OK?
I dont use mi laptop as much in battery, and when I use it that way I am usually lying in bed or something quiet like that.


what should I do if the HDD temp goes up?
Im clueless on that one.

Thanks y'all for your help on this issue.

---

### Post by Fnyx on 2008-06-07
I have an additional problem, Samsung drive if that helps. 

When giving a value of 254 to hdparm the clicking goes away but is replaced by a less frequent but much louder (and rather unhealthy sounding) clonk.

When the value is not 254 the Load_Cycle_Count is increased by one for every tick. When the value is 254 the Calibration_Retry_Count is increased by one for every clonk but the Load_Cycle_Count is constant. Non 254 values makes the Calibration_Retry_Count constant.

Have tried enabling SMART Automatic Offline Testing too (as suggested somewhere for Samsung drives) but no change.

Had a clicking problem in Vista aswell but all my fiddling around with hdparm and such in Ubuntu fixed it, no clonks no nothing.

So... whats a Calibration_Retry_Count and is it harmful?

What to choose? Clicks or clonks? :(

---

### Post by L337_K3y5 on 2008-06-11
Ok, now which of these are my Load_Count_Cycle?
[IMG]http://i302.photobucket.com/albums/nn102/Keyblade_frog/Screenshot-2.png[/IMG]
I'm having trouble following this...I have a laptop also, and it looks as if in the detailed step at the beginning the WORST is always over the Thres.  :confused:  I don't know if I should continue using Ubuntu now...:(

---

### Post by sam_delta on 2008-06-11
your load cycle is the "7054", wait 15 mins and run the command again, and youll know aprox how much loads you getting with respect to time,

sam

---

### Post by L337_K3y5 on 2008-06-11
Whoah, this is wierd...I did the load count and I got the same number as the time 15 min. before...wow, is this even possible?  The whole time I've been browsing the internet, uninstalling some programs, and installing new ones...:confused:  Well, at least its good!:)

---

### Post by sam_delta on 2008-06-11
yeah, its possible that means that your laptop never parked the hdd head, and your good with your hdd then

however, when you restar your pc/resume from hibernate, youll note that itll increase probably by 1, (because when you hibernate/suspendor shut down your pc, it always stop spinning and park the head)

sam

---

### Post by olskar on 2008-06-16
225 Load_Cycle_Count        0x0012   001   001   000    Old_age   Always       -       1003601




:(

I have tried everything but the valu just keep increasing!

sudo hdparm -B 254 /dev/sda and sudo hdparm -B 255 /dev/sda..tried it all and nothing works :( ideas?

---

### Post by BandD on 2008-06-16
It is possible that your drive doesn't respond to hdparm values.  I had a drive, that was already on its way out, that refused to accept the hdparm values I threw at it.  

You could try configuring laptop-mode and change the perceived idle time, or spin-down time.  

Or first, try looking through    man hdparm    for the -S option and try soem different values there.  That is the spin down time option.  It's worth a shot.

---

### Post by sroland81 on 2008-06-18
Hello, i'm running Hardy on a Presario F700 laptop and i hear a very nasty noise, quite loud when i'm not doing anything.... i think it is not the constant clicking produced by the load cycle count.... a applied some fix to it and the Load Cycle Count does not increase.... Imagine this: i'm almost sleep with the laptop en the desk... no sounds.... i'm leting ubuntu to download movies for me during the night... and suddenly a noise like the CD drive is ejected... but it comes from the hard drive... i hear it duriong the day... when i stop and start to read a PDF and a couple of minutes passed... again that sound... it occurs one a while.... but it is not constant... any ideas? this is the output info of smartctl, the device name and the smart info... i heard that the samsung disks need some -F  samsung or samsung2 parameter... please tell me if i'm doing something wrong... the temperature is not right y think... is a long number... 

what should i do to determine the source of this sound? i ran smartctl once and after one of this huge ticks, i ran again and found that the only number that increased was the Calibration Retry Count.... is this possible? may be other parameter not showed? thanks for your help.

santiago@quasar:~$ sudo smartctl -i /dev/sda -F samsung2
[sudo] password for santiago: 
smartctl version 5.37 [x86_64-unknown-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF INFORMATION SECTION ===
Device Model:     SAMSUNG HM121HI
Serial Number:    S18JJD0PB06947
Firmware Version: LZ100-10
User Capacity:    120,034,123,776 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  ATA/ATAPI-7 T13 1532D revision 0
Local Time is:    Wed Jun 18 05:08:05 2008 UYT

==> WARNING: May need -F samsung or -F samsung2 enabled; see manual for details.

SMART support is: Available - device has SMART capability.
SMART support is: Enabled

santiago@quasar:~$ sudo smartctl -A /dev/sda -F samsung2
smartctl version 5.37 [x86_64-unknown-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF READ SMART DATA SECTION ===
SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   100   051    Pre-fail  Always       -       249
  3 Spin_Up_Time            0x0007   252   252   025    Pre-fail  Always       -       2125
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       929
  5 Reallocated_Sector_Ct   0x0033   252   252   010    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   252   252   051    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0025   252   252   015    Pre-fail  Offline      -       0
  9 Power_On_Hours          0x0032   252   252   000    Old_age   Always       -       519
 10 Spin_Retry_Count        0x0033   252   252   051    Pre-fail  Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       581
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       494
184 Unknown_Attribute       0x0033   252   252   070    Pre-fail  Always       -       0
187 Unknown_Attribute       0x0032   252   252   000    Old_age   Always       -       0
188 Unknown_Attribute       0x0032   252   252   000    Old_age   Always       -       0
190 Temperature_Celsius     0x0022   058   050   040    Old_age   Always       -       214749282346
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       6803
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       239
193 Load_Cycle_Count        0x0032   098   098   000    Old_age   Always       -       22762
194 Temperature_Celsius     0x0022   058   050   000    Old_age   Always       -       42 (Lifetime Min/Max 14/50)
195 Hardware_ECC_Recovered  0x001a   100   100   000    Old_age   Always       -       12605
196 Reallocated_Event_Count 0x0032   252   252   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0012   252   252   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   252   252   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0036   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x000a   100   100   000    Old_age   Always       -       0
201 Soft_Read_Error_Rate    0x0032   252   252   000    Old_age   Always       -       0

---

### Post by the_doc on 2008-06-19
From what I've read an increase of the value associated with the Calibration Retry Count can indicate:

>  problem with motor, bearings or power supply.

---

### Post by sroland81 on 2008-06-19
bearings? what's that... power supply? it's a laptop and i used mostly plugged in... you mean something wrong internally with power supply?

whatever it is, it isn't a good sign... right?

thanks... and what about the -F samsung parameter...?

---

### Post by pixelot on 2008-06-23
I ran the commands posted in [this thread]("http://ubuntuforums.org/showthread.php?t=795327"), and it worked.

I went from ~25 cycles in 15 minutes to none. :D

I have a Dell Vostro 1400 with the affected TOSHIBA MK8037GSX.

---

### Post by edajai on 2008-06-23
is this problem specific to ubuntu only or to all linux in general?? i'm a novice and i'm pretty curious about the life of my new dell laptop, but still want to run linux though (suse 11 seems promising)

---

### Post by quanumphaze on 2008-06-23
> **edajai said:**
> is this problem specific to ubuntu only or to all linux in general?? i'm a novice and i'm pretty curious about the life of my new dell laptop, but still want to run linux though (suse 11 seems promising)

It's a problem specific to certain hard disk firmware and effects *all* operating systems. Mostly Samsung and Western Digital (maybe Hitachi ???)

---

### Post by sroland81 on 2008-06-24
I have confirmed the Cycle Load Issue on my Samsung HM121HI hard drive and i found that there is no response to the fix posted in this thread [http://ubuntuforums.org/showthread.php?t=795327](http://ubuntuforums.org/showthread.php?t=795327)
I tested the fix using parameters from 200 to 253 in the hdparam, and the Cycle Load Counting increades always by about 120 per hour or more. When i tried -B 254, it stopped Cycling at all. The counter stopped and i have the heads of my hard drive always flying on the disk. That's not what i wanted... i wanted to reach some reasonable counting rate, like 20 or 30 per hour... but this was impossible for me...

any other alternative?
This fix doesn't worked for me.

Thanks.-

---

### Post by frodon on 2008-06-24
Heads can't park correctly on linux and most OS so the best is to disable this feature till laptop makers, hard drive manufacturers and OS developpers can reach an interesting compromise between efficiency, power saving and disk protection.

Having your head parking 20 or 30 per hours is almost useless on linux as because the kernel in its current state polls too often the disk so that they will unpark almost immediately and thus make you lose the interest of parking the heads anyway.

So if you can't reach the value you target just use -B 254.

BTW if you use hardy the fix presented in the thread you linked is obsolete and could explain why you can't reach your goal.

---

### Post by frodon on 2008-06-24
BTW i have a question about the hardy fix, is the laptop supposed to switch to ${DEVICES_DISK_PM_POWERSAVE_OFF} when power adaptator plugged in and to DEVICES_DISK_PM_POWERSAVE_ON when working on battery ?

Or do you just set it manually with "pm-powersave true" and "pm-powersave false" ?

---

### Post by w4tch0 on 2008-06-26
> **frodon said:**
> BTW i have a question about the hardy fix, is the laptop supposed to switch to ${DEVICES_DISK_PM_POWERSAVE_OFF} when power adaptator plugged in and to DEVICES_DISK_PM_POWERSAVE_ON when working on battery ?

Or do you just set it manually with "pm-powersave true" and "pm-powersave false" ?

Yes, thats exactly how it works. The scripts in /etc/pm/power.d are executed if the AC gets connected/disconnected (and the $1 variable of the scripts gets a true or false value depending on whether we are on AC or on Battery).

Also the scripts in /etc/pm/sleep.d are executed on hibernate, suspend, resume, thaw (and the $1 variable of the scripts gets a value of hibernate, suspend, resume, thaw). 
[note: thaw = resume from hibernate, resume = resume from suspend]

And this brings me to my improvement on the [opensuse fix](http://en.opensuse.org/Disk_Power_Management).

Lets take another script, and lets call it disk again.
```
#!/bin/bash
. /usr/lib/pm-utils/functions
. /etc/pm/config.d/disk



if test -z ${DEVICES_DISK_PM_NAMES}; then
        exit 1
fi

case "$1" in
        hibernate|suspend)
                echo "**nothing i need here fo now"
                ;;
        thaw|resume)
                /usr/bin/on_ac_power;
                if [ "$?" -eq 0 ]; then
                echo "**disabled PM for harddisk"
                for DISK_NAME in `echo ${DEVICES_DISK_PM_NAMES}`; do
                        ${DEVICES_DISK_PM_POWERSAVE_OFF} ${DISK_NAME}
                done
                elif [ "$?" -eq 1 ]; then
                echo "**enabled PM for harddisk"
                for DISK_NAME in `echo ${DEVICES_DISK_PM_NAMES}`; do
                        ${DEVICES_DISK_PM_POWERSAVE_ON} ${DISK_NAME}
                done
                fi
                ;;
        *)
                echo "**this shoudn't be called right now..."
        ;;
esac
```

And place it in /etc/pm/sleep.d/

Now lets make it executable
```
$ sudo chmod +x /etc/pm/sleep.d/disk
```

This ensures, that when the computer wakes up from hibernate/suspend it will set APM according to our settings in /etc/pm/config.d/disk depending on whether we are on AC or on battery.

Well at least it works that way for me, dunno if it's universal... my bash scripting skills are somewhere between none and lame :)

Now i need to solve mi final problem, and that is if i have laptop mode enabled in /etc/default/acpi-support the evil /etc/acpi/power.sh keeps setting hdparm when i plug in/out the power cord. Now i want to keep laptop mode for battery because is reduces disk polling significantly thus making disk APM more efficient, but i want pm-utils (SUSE scripts) to handle the hdparm settings not the old scripts in /etc/acpi/ .

This is what happens when ubuntu/debian devs just take something (pm-utils) and slap it on the system with just glue and duct tape ;D

---

### Post by frodon on 2008-06-26
Thanks, i have still to test things as for me applying the fix just stop head parking whatever the value i put for "DEVICES_DISK_PM_POWERSAVE_ON", but that's not a big problem as heads don't park in a useful way on linux anyway.

---

### Post by edajai on 2008-06-26
> **quanumphaze said:**
> It's a problem specific to certain hard disk firmware and effects *all* operating systems. Mostly Samsung and Western Digital (maybe Hitachi ???)

then why is it that nothing about this problem seems to be seen in the opensuse forums?

---

### Post by w4tch0 on 2008-06-26
> **frodon said:**
> Thanks, i have still to test things as for me applying the fix just stop head parking whatever the value i put for "DEVICES_DISK_PM_POWERSAVE_ON", but that's not a big problem as heads don't park in a useful way on linux anyway.

They do park in a useful way, but only if laptop-mode is enabled and properly configured as it prevents unneeded disk I/O. Without laptop-mode, for some strange reason they get unparked right away as as they park (almost seems like "oh the disk parked, i must write a log to disk that it parked).

BTW: more info on pm-utils scripting: [http://en.opensuse.org/Pm-utils](http://en.opensuse.org/Pm-utils)

---

### Post by frodon on 2008-06-26
laptop-mode does not play well at all with pm-util (i tested this myself) in hardy and doesn't work after suspend/hibernate, in addition my previous laptop-mode config is way less efficient than it was before with gutsy. On top of this laptop mode doesn't prevent most of the most important and regular IO pollings which are deeper in the kernel.

These are the reasons why they do not park in useful way, parking in a useful way would be parking the heads and keeping them parked as long as the kernel do not have important things to do, thus protecting the disk, decreasing power consumption and decreasing the disk temperature.

So for the moment head parking is more a problem than a useful tool unfortunately, hopefully OS developpers will fix this in next version, lets wait a year and see.

---

### Post by w4tch0 on 2008-06-26
Yes, the old acpi-support script /etc/acp/power.sh doesn't get called upon thaw/resume, which causes the fact that laptop-mode does not get enabled after hibernate/sleep. And because pm-utils in hardy is quite unfinished (noone wrote proper scripts/hooks for it, noone migrated old scripts from acpi-support to pm-utils) it does not play with laptop-mode well. This could be easily fixed with addining laptop-mode start/stop to my /etc/pm/sleep.d/disk script and to the /etc/pm/power.d/disk scipt and after that we could get rid of power.sh all together.

Also note, that laptop-mode in hardy is quite an old version heavily patched (crippled :P ) as well (see laptop-mode website for more information). 

This power management madness needs to come to an end, pm-utils needs to get polished and acpi-support needs go away :)

---

### Post by conphara on 2008-06-28
I didn't knew about this problem until I read about the cons of using laptop-mode. My Load Cycle Count on my SAMSUNG MP0804H (Firmware YS200-06) had a total count of 192774 :(. That's the result of using this laptop dual boot (XP, Opensuse-> Feisty-> Gutsy-> Hardy) for the last 2 years. Anyway I had an average count of 10 per minute. But after setting it to "hdparm -B 254" it stopped at 192774 and has not changed since thursday. Is that normal? 
Now my problem is my desktop. After the 8.04.1 release in the next couple of weeks, I'm planning to relocate my hard drives so I can get Hardy instead of Gutsy in a dualboot setting, but my two SATA Seagates (ST3320620AS, firmware 3.AAK & ST3320620AS, firmware ). Using hdparm and smartctl, both of them appear to not having APM (=0). And "smartctl -A /dev/sdb" doesn't show load cycle. And trying the hdparm -B 254 command shows me an error (/dev/sdb:
setting Advanced Power Management level to 0xfe (254) HDIO_DRIVE_CMD failed: Input/output error). Using the "hdparm -I /dev/sda" command it displays "Recommended acoustic management value: 254, current value: 0".
So I can't tell what the load cycle count is, neither on Linux or in Windows (using some freeware apps). So the problem might be the firmware, which I don't like to flash to a new version (if there is one) because of warranty.

Have anyone of you guys had problems with a high increase in load cycles on an Ubuntu desktop or does this problem only occur on laptops using Linux? 

What should I do? :confused:


The Seagate which is running Gutsy shows this:

```
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   111   087   006    Pre-fail  Always       -       37547317
  3 Spin_Up_Time            0x0003   096   095   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   099   099   020    Old_age   Always       -       1250
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   072   060   030    Pre-fail  Always       -       20439123
  9 Power_On_Hours          0x0032   099   099   000    Old_age   Always       -       1424
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       759
187 Unknown_Attribute       0x0032   068   068   000    Old_age   Always       -       32
189 Unknown_Attribute       0x003a   100   100   000    Old_age   Always       -       0
190 Temperature_Celsius     0x0022   048   045   045    Old_age   Always   In_the_past 874774580
194 Temperature_Celsius     0x0022   052   055   000    Old_age   Always       -       52 (Lifetime Min/Max 0/12)
195 Hardware_ECC_Recovered  0x001a   079   060   000    Old_age   Always       -       223863805
197 Current_Pending_Sector  0x0012   001   001   000    Old_age   Always       -       4294967295
198 Offline_Uncorrectable   0x0010   001   001   000    Old_age   Offline      -       4294967295
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0000   100   253   000    Old_age   Offline      -       0
202 TA_Increase_Count       0x0032   100   253   000    Old_age   Always       -       0

```

---

### Post by BandD on 2008-06-28
Generally Desktop drives don't have a need to park the heads as they are not vulnerable to bumps nor do they need to conserve power.  So your desktop drives probably don't have a head parking feature.  So I wouldn't worry about the desktop drive.

Also regarding the laptop 200,000 cycles doesn't seem too bad to me for a 2 year old drive.  But it's hard to tell where those cycles come from because you have run so many different OS's on it.  The main thing to watch with changing the hdparm -B values on a laptop is the temperature of the drive.  So keep an eye on that and make sure it isn't exceeding the manufacturer's specs.  

Also, one other thing to note.  This problem with Load Cycle Counts affects ALL OS's.  It has been documented numerous times on this forum and on several other places.  Yes even Windows.

---

### Post by conphara on 2008-06-28
I read about a Linux developer who said that it's better to have a hot drive than a drive which load cycle too often. My laptop drive starts with a temperature between 25-27 C and goes up to around 45-47 C (after some heavy downloading and general internet usage). Remember my laptop drive doesn't support APM (only SMART), so either way it would still be quite hot. It's only around 25-30 C IF I use the laptop-mode and the drive spins down, but I've read that that isn't a good thing long term, because a drive can only spin up and down x amount of times (like the shutdown hard drives in Windows). When I was using laptop-mode (not since -B 254) it would spin up and down constantly which made me worry.
So a good advice from me, is adjusting the setting to -B 254 can be a good thing, and in my case I could even lower it to 192 since I haven't used that many cycles.

Regarding the desktop load cycle count. Are you sure that it doesn't behave in the same way, since my drives don't support APM and therefore are set to 0 (aggressive power management). When I used the Seagate floppy tool yesterday there was a feature to test a spin down (acoustic) and it did, so the drives do support that behavior. But still I'm a bit worried since I can't read the load cycle count either in Linux (hdparm 7.5-1 with Gutsy) or Windows (freeware), I can't know for sure if the count goes up faster than I can adjust it to.

But it's rather comforting in a way that it also happens both in Windows and Mac OS. I read that the fix in mac was also the hdparm -B 254 setting. And Windows just writes to disk constantly that it never gets a chance to park. At least in Vista.

---

### Post by conphara on 2008-06-28
According to Seagate's hard drive manuals my two desktop drives don't support Advanced Power Management (APM) and Automatic Acoustic Management (AAM) features. Does this mean that as desktop users we shouldn't have to worry about this load cycle count bug? 
I was under the impression that all drives counted load cycles, apm or no apm.

---

### Post by frodon on 2008-06-28
As far as i know this annoyance is laptop only. I don't think desktop computers hard drives have this feature at all.

---

### Post by conphara on 2008-06-29
Thanks,

so the morale of this story is: if your drive, a desktop or a laptop drive, supports Advanced Power Management (APM), you will experience problems with a high increase in load cycles because of APM. 
And adjusting the drive via "hdparm -B 254" will solve the problem by disabling APM. The cost of this is more power and a hotter drive (just a few degrees), because it doesn't park the heads all the time. Short term solution until they come up with a proper long term fix.

In my case, I was worried that acoustic management was a big deal. First of all I didn't know what it was, [http://en.wikipedia.org/wiki/Automatic_Acoustic_Management]("http://en.wikipedia.org/wiki/Automatic_Acoustic_Management"), and apparently it's only noise control vs performance. Not a huge deal.

---

### Post by aldeby on 2008-06-29
hddtemp bug seems to be fixed upstream (not yet backported to hardy though)

0.3-beta15-43
Superseded in intrepid-release on 2008-05-11

hddtemp (0.3-beta15-43) unstable; urgency=low

  * Don't wake up SATA drives if not asked (closes: #479840). 

 -- Ubuntu Archive Auto-Sync <email address hidden>   Sun,  11 May 2008 15:33:02 +0100

Thanks for the useful guide ubuntu_demon!

---

### Post by I_can_see_the_light on 2008-07-02
Hello everyone, newibe here. I have been reading about this problem back and forth but I'm not sure which solution I should use.

Smartmontools reports that my Load_cycle_count is close to 360 000 and it seems to rise by 3-6 cycles/minute. I have only been running Ubuntu Hardy for just over a month and prior to that I've been running Win Xp for 2,5 years. I have however calculated that the last 50 000 cycles have happened since I started running Ubuntu.

My question is which solution I should choose. The ugly-fix for Gutsy seemed easier to me, but I'm not sure what ubuntu_demon meant with it not being future proof. Was he talking about Hardy upgrades or when upgrading to Intrepid Ibex? 'Cause I'll probably stick with Hardy for a while since it's (basically) my first experience with GNU/Linux

Hope to hear from y'all soon ;)

---

### Post by I_can_see_the_light on 2008-07-02
Ok, so I tried to set the APM manually by using ```
sudo hdparm -B 254 /dev/sda
``` but the output I got was ```
/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 HDIO_DRIVE_CMD failed: Input/output error
```

I googled the error message and found a command to check whether my HDD support APM: *sudo hdparm -i /dev/sda | grep AdvancedPM*. Apparently it doesn't, as the output I got was: *AdvancedPM=no WriteCache=enabled*

What do I do now? Is there any other way to force the drive not to park as often? I started *synaptic* and apparently *laptop-mode-tools* are installed. Could that be why the disk is parking so often (4.5 cycles/minute on average). I remember reading something about that somewhere, though I could be wrong.

---

### Post by dumas045 on 2008-07-09
I just read about this problem yesterday, and I'm worried about my harddrive failing any minute.

Here's my numbers:
190 Temperature_Celsius 0x0022 059 047 045 Old_age Always - 690159657
193 Load_Cycle_Count 0x0032 001 001 000 Old_age   Always - 1669901
194 Temperature_Celsius 0x0022 041 053 000 Old_age Always - 41 (Lifetime Min/Max 0/13)

Should I just wait till the harddrive gives or call up Lenovo about the problem and ask for a replacement?

Edit: I checked the health of the drive with the -H flag and it says it passed. Also ran the diagnostic tests of the bios and Seatools, both of which it passed. With these sort of numbers, shouldn't my laptop be acting crazy?

---

### Post by I_can_see_the_light on 2008-07-09
> **I_can_see_the_light said:**
> Ok, so I tried to set the APM manually by using ```
sudo hdparm -B 254 /dev/sda
``` but the output I got was ```
/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 HDIO_DRIVE_CMD failed: Input/output error
```

I googled the error message and found a command to check whether my HDD support APM: *sudo hdparm -i /dev/sda | grep AdvancedPM*. Apparently it doesn't, as the output I got was: *AdvancedPM=no WriteCache=enabled*

What do I do now? Is there any other way to force the drive not to park as often? I started *synaptic* and apparently *laptop-mode-tools* are installed. Could that be why the disk is parking so often (4.5 cycles/minute on average). I remember reading something about that somewhere, though I could be wrong.

My problems have been temporarily solved by using the workaround at Ubuntu Wiki: [https://wiki.ubuntu.com/PowerManagement]("https://wiki.ubuntu.com/PowerManagement"). Can't believe I missed to check that site. Have been searching the net like a mad man for a solution since none of the ugly fixes worked for me. Load_cycle_count is still increasing a little to fast, but nothing like the the way it was before.

Can't believe how quiet the computer is when the HDD spins down ;)

---

### Post by I_can_see_the_light on 2008-07-09
> **dumas045 said:**
> I just read about this problem yesterday, and I'm worried about my harddrive failing any minute.

Here's my numbers:
190 Temperature_Celsius 0x0022 059 047 045 Old_age Always - 690159657
193 Load_Cycle_Count 0x0032 001 001 000 Old_age   Always - 1669901
194 Temperature_Celsius 0x0022 041 053 000 Old_age Always - 41 (Lifetime Min/Max 0/13)

Should I just wait till the harddrive gives or call up Lenovo about the problem and ask for a replacement?

Edit: I checked the health of the drive with the -H flag and it says it passed. Also ran the diagnostic tests of the bios and Seatools, both of which it passed. With these sort of numbers, shouldn't my laptop be acting crazy?


Those values might not necessarily be true. If you haven't already done this i suggest you check how much Load_cycle_count increase each time the head parks. If it increases by, say 16 there is a good chance your true value is 16 times lower than the output you got.

As my HDD didn't support Advanced power management I couldn't use any of the ugly fixes but [[COLOR="Blue"]this[/COLOR]]("https://wiki.ubuntu.com/PowerManagement") link seem to have provided me with a breath of air.

---

### Post by Arthur Archnix on 2008-07-10
> **w4tch0 said:**
> This is what happens when ubuntu/**debian** devs just take something (pm-utils) and slap it on the system with just glue and duct tape ;D

Errr.... not to nitpick, but have you tested this on Debian? On my Lenny system laptop-mode and pm-utils work very nicely together. Acpi-tools is uninstalled (the source of the hated power.sh script) and unecessary.

I'd like to correct my post above though, and say that it does not apply the correct settings when resuming from suspend on AC. Not asking for support, just wanted to chime in with the status of things in Debian.

---

### Post by davarse on 2008-07-16
hi mate i check my load circle load and i got this:
[I]
smartctl version 5.37 [x86_64-unknown-linux-gnu] Copyright (C) 2002-6 Bruce Alle
n
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF INFORMATION SECTION ===
Device Model:     WDC WD2500BEVS-22UST0
Serial Number:    WD-WXEZ07W92272
Firmware Version: 01.01A01
User Capacity:    250,059,350,016 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Wed Jul 16 17:43:57 2008 EST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00)	Offline data collection activity
					was never started.
					Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		 (8760) seconds.
Offline data collection
capabilities: 			 (0x7b) SMART execute Offline immediate.
					Auto Offline data collection on/off supp
ort.
					Suspend Offline collection upon new
					command.
					Offline surface scan supported.
					Self-test supported.
					Conveyance Self-test supported.
					Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					General Purpose Logging supported.
Short self-test routine 
recommended polling time: 	 (   2) minutes.
Extended self-test routine
recommended polling time: 	 ( 106) minutes.
Conveyance self-test routine
recommended polling time: 	 (   5) minutes.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_
FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   200   200   051    Pre-fail  Always       -
       0
  3 Spin_Up_Time            0x0003   188   188   021    Pre-fail  Always       -
       1558
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -
       556
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -
       0
  7 Seek_Error_Rate         0x000f   100   253   051    Pre-fail  Always       -
       0
  9 Power_On_Hours          0x0032   099   099   000    Old_age   Always       -
       1412
 10 Spin_Retry_Count        0x0013   100   100   051    Pre-fail  Always       -
       0
 11 Calibration_Retry_Count 0x0012   100   100   051    Old_age   Always       -
       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -
       540
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -
       374
193 Load_Cycle_Count        0x0032   175   175   000    Old_age   Always       -
       76953
194 Temperature_Celsius     0x0022   109   088   000    Old_age   Always       -
       38
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -
       0
197 Current_Pending_Sector  0x0012   200   200   000    Old_age   Always       -
       0
198 Offline_Uncorrectable   0x0010   100   253   000    Old_age   Offline      -
       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -
       0
200 Multi_Zone_Error_Rate   0x0009   100   253   051    Pre-fail  Offline      -
       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
No self-tests have been logged.  [To run self-tests, use: smartctl -t]


SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.

[/I]

do you think i have to apply it???

cheers'

---

### Post by Arthur Archnix on 2008-07-16
Ok, I've gotten the correct hdparm settings to be applied after suspend. There's a discussion about this on the laptop-mode malling list for July. I'm not sure if this fix will work for Ubuntu, as there are apparently some problems with how Ubuntu has chosen to integrate laptop-mode according to its maintainer. I'm also not sure if Ubuntu has given the laptop-mode service the same name and place. 

This script is only for those running Hardy and using PM-utils and laptop-mode. Try adding the following script to your users pm/sleep.d directory. On debian, that's /etc/pm/sleed.d/ however, it may be different on your system.

Create a file called 01-laptopmode-service and paste the following in there:
```
#!/bin/sh

. "${PM_FUNCTIONS}"

case "$1" in
   hibernate|suspend)
       ;;
   thaw|resume)
    invoke-rc.d laptop-mode restart
       ;;
   *) exit $NA
       ;;
esac
```

Make it executable, suspend, resume on ac power and then check with ```
hdparm -I /dev/sda | grep level

```

Again, I can't make any promises because I can't test this on Ubuntu. The instructions are intentionally a bit vague at the moment because I think that if you can't figure out how to do the steps not clearly spelled out you probably shouldn't try this until others have, and reported their results.

Best,

---

### Post by Rui Pais on 2008-07-16
> **Arthur Archnix said:**
> Ok, I've gotten the correct hdparm settings to be applied after suspend. There's a discussion about this on the laptop-mode malling list for July. I'm not sure if this fix will work for Ubuntu, as there are apparently some problems with how Ubuntu has chosen to integrate laptop-mode according to its maintainer. I'm also not sure if Ubuntu has given the laptop-mode service the same name and place. 

This script is only for those running Hardy and using PM-utils and laptop-mode. Try adding the following script to your users pm/sleep.d directory. On debian, that's /etc/pm/sleed.d/ however, it may be different on your system.

Create a file called 01-laptopmode-service and paste the following in there:
```
#!/bin/sh

. "${PM_FUNCTIONS}"

case "$1" in
   hibernate|suspend)
       ;;
   thaw|resume)
    invoke-rc.d laptop-mode restart
       ;;
   *) exit $NA
       ;;
esac
```

Make it executable, suspend, resume on ac power and then check with ```
hdparm -I /dev/sda | grep level

```

Again, I can't make any promises because I can't test this on Ubuntu. The instructions are intentionally a bit vague at the moment because I think that if you can't figure out how to do the steps not clearly spelled out you probably shouldn't try this until others have, and reported their results.

Best,

Hi.
I tried on Hardy (yes, the paths you mention are the same on Debian and ubuntu) but here it wont work.
It always wakes to "Advanced power management level: 128"

I didn't see what else, as extra steps you mention, would be needed. I just created the scrit on /etc/pm/sleed.d/ made it executable and suspended.


What i do, _as a workaround_, for this issue it's create a cron job for: 
```
sudo /etc/acpi/resume.d/99-hdd-ugly-fix.sh
```
with a recurrence of 2 min, after add a 
>  ALL=NOPASSWD:  /etc/acpi/resume.d/99-hdd-ugly-fix.sh
to visudo.
Not a clean way, of course, but it works.

---

### Post by Arthur Archnix on 2008-07-16
Can you check in your pm log if the script was run successully?

If so, try passing the command to restart the service from the command line. Does it work?

---

### Post by Rui Pais on 2008-07-16
> **Arthur Archnix said:**
> Can you check in your pm log if the script was run successully?

If so, try passing the command to restart the service from the command line. Does it work?

Hi again.
Yes, i checked and script run. Not sure of successfully:
> ===== Wed Jul 16 17:37:45 WEST 2008: running hook: /usr/lib/pm-utils/sleep.d/00clear =====
===== Wed Jul 16 17:37:45 WEST 2008: running hook: /etc/pm/sleep.d/01-laptopmode-service =====
===== Wed Jul 16 17:37:45 WEST 2008: running hook: /usr/lib/pm-utils/sleep.d/05led =====
===== Wed Jul 16 17:37:45 WEST 2008: running hook: /usr/lib/pm-utils/sleep.d/10NetworkManager =====
===== Wed Jul 16 17:37:45 WEST 2008: running hook: /usr/lib/pm-utils/sleep.d/20video =====
kernel.acpi_video_flags = 0
===== Wed Jul 16 17:37:45 WEST 2008: running hook: /usr/lib/pm-utils/sleep.d/49bluetooth =====
===== Wed Jul 16 17:37:45 WEST 2008: running hook: /usr/lib/pm-utils/sleep.d/50modules =====
===== Wed Jul 16 17:37:45 WEST 2008: running hook: /usr/lib/pm-utils/sleep.d/90clock =====
===== Wed Jul 16 17:37:47 WEST 2008: running hook: /usr/lib/pm-utils/sleep.d/94cpufreq =====
===== Wed Jul 16 17:37:47 WEST 2008: running hook: /usr/lib/pm-utils/sleep.d/95led =====
===== Wed Jul 16 17:37:47 WEST 2008: running hook: /usr/lib/pm-utils/sleep.d/99video =====
Wed Jul 16 17:37:47 WEST 2008: done running suspend hooks.
Wed Jul 16 17:38:01 WEST 2008: running resume hooks.
===== Wed Jul 16 17:38:01 WEST 2008: running hook: /usr/lib/pm-utils/sleep.d/99video =====
===== Wed Jul 16 17:38:01 WEST 2008: running hook: /usr/lib/pm-utils/sleep.d/95led =====
===== Wed Jul 16 17:38:01 WEST 2008: running hook: /usr/lib/pm-utils/sleep.d/94cpufreq =====
===== Wed Jul 16 17:38:01 WEST 2008: running hook: /usr/lib/pm-utils/sleep.d/90clock =====
===== Wed Jul 16 17:38:02 WEST 2008: running hook: /usr/lib/pm-utils/sleep.d/50modules =====
 * Reconfiguring network interfaces...
SIOCDELRT: No such process
   ...done.
===== Wed Jul 16 17:38:02 WEST 2008: running hook: /usr/lib/pm-utils/sleep.d/49bluetooth =====
===== Wed Jul 16 17:38:02 WEST 2008: running hook: /usr/lib/pm-utils/sleep.d/20video =====
===== Wed Jul 16 17:38:02 WEST 2008: running hook: /usr/lib/pm-utils/sleep.d/10NetworkManager =====
===== Wed Jul 16 17:38:02 WEST 2008: running hook: /usr/lib/pm-utils/sleep.d/05led =====
**===== Wed Jul 16 17:38:02 WEST 2008: running hook: /etc/pm/sleep.d/01-laptopmode-service =====**
===== Wed Jul 16 17:38:02 WEST 2008: running hook: /usr/lib/pm-utils/sleep.d/00clear =====
Wed Jul 16 17:38:02 WEST 2008: done running resume hooks.

I run it from command line, passing argument suspend, and it changes nothing.

So i replaced the line
```
invoke-rc.d laptop-mode restart
```
by
```
/etc/acpi/resume.d/99-hdd-ugly-fix.sh
```

and that, finally make it work :)

Many thanks for point me to the /etc/pm/sleed.d/01-laptopmode-service!
It works much better then my previous solution of running a command each 2 minutes.
:)

---

### Post by Polygon on 2008-07-18
Hi, im confused on determining if my laptop suffers from this problem or not, i ran the command once:

> 
mark@Australis:~$ date; sudo smartctl -a /dev/sda | egrep '(Load_Cycle_Count|Temperature)'
Fri Jul 18 13:27:03 MST 2008
190 Temperature_Celsius     0x0022   059   048   000    Old_age   Always       -       689700905
193 Load_Cycle_Count        0x0032   098   098   000    Old_age   Always       -       29616
194 Temperature_Celsius     0x0022   134   100   000    Old_age   Always       -       41 (Lifetime Min/Max 22/52)



then 15 min later:

> 
mark@Australis:~$ date; sudo smartctl -a /dev/sda | egrep '(Load_Cycle_Count|Temperature)'
Fri Jul 18 13:44:21 MST 2008
[sudo] password for mark: 
190 Temperature_Celsius     0x0022   059   048   000    Old_age   Always       -       706478121
193 Load_Cycle_Count        0x0032   098   098   000    Old_age   Always       -       29650
194 Temperature_Celsius     0x0022   134   100   000    Old_age   Always       -       41 (Lifetime Min/Max 22/52)



then i ran it again about 3 hours later:

> 
mark@Australis:~$ date; sudo smartctl -a /dev/sda | egrep '(Load_Cycle_Count|Temperature)'
Fri Jul 18 16:39:41 MST 2008
[sudo] password for mark: 
190 Temperature_Celsius     0x0022   053   048   000    Old_age   Always       -       790364207
193 Load_Cycle_Count        0x0032   097   097   000    Old_age   Always       -       30506
194 Temperature_Celsius     0x0022   117   100   000    Old_age   Always       -       47 (Lifetime Min/Max 22/52)
mark@Australis:~$ 



do you think that im suffering from this problem? my laptop is a compaq presario f767nr and my hard drive according to lshw is a Hitachi HTS54252

---

### Post by BandD on 2008-07-18
Hi Polygon,

Your laod_cycles are increasing pretty fast.  However, some drives report the load_cycle count strangely (i.e. for one cycle the value changes by 3 or 5).  So the best thing to do is note your load_cycle count then as soon as you here a little click from your drive check the smartctl command again and see how much your load_cycle count increases by.

---

### Post by Polygon on 2008-07-19
i listened and every time i hear my hard drive make noise i checked it, and its going up by one each time =/

ill try some of these methods

---

### Post by Polygon on 2008-07-19
i dont think the hardy fix is working, i followed the instructions in the opensuse guide and used ubuntu_demons's numbers but its still showing * power management set even if i set it to false..

the config.d/disk script:

```
# Configure disk power management settings to ensure both
# long disk life and good power management.
#
# Space delimited list of disk devices this affects.
#
DEVICES_DISK_PM_NAMES="/dev/sda"
#
#
# Power management modes
#
# Powersave mode off
#  Disable APM and spin-down
#
DEVICES_DISK_PM_POWERSAVE_OFF="hdparm -q -B 254 -q -S 0"
#
# Powersave mode on
# Enable APM to conservative 200 and set spin-down for 21 minutes
#
DEVICES_DISK_PM_POWERSAVE_ON="hdparm -q -B 128 -q -S 0"

```

the power.d/disk script:

```

#!/bin/bash
. /usr/lib/pm-utils/functions
. /etc/pm/config.d/disk

if test -z "${DEVICES_DISK_PM_NAMES}"; then
        exit 1
fi

case "$1" in
        true)
                echo "**enabled pm for harddisk"
                for DISK_NAME in `echo ${DEVICES_DISK_PM_NAMES}`; do
                        ${DEVICES_DISK_PM_POWERSAVE_ON} ${DISK_NAME}
                done ;;
        false)
                echo "**disabled pm for harddisk"
                for DISK_NAME in `echo ${DEVICES_DISK_PM_NAMES}`; do
                        ${DEVICES_DISK_PM_POWERSAVE_OFF} ${DISK_NAME}
                done ;;
esac


```

and the power.d/disk script is executable: 

-rwxr-xr-x 1 root root 602 2008-07-19 11:40 /etc/pm/power.d/disk

but even after all that, if i try and disable powermanagement it still says its on:

> 
mark@Australis:~$ sudo pm-powersave false
**disabled pm for harddisk
**SetLowPower OFF
**sched policy powersave OFF
mark@Australis:~$ sudo hdparm -I /dev/sda | grep 'Advanced Power'
	   *	Advanced Power Management feature set
mark@Australis:~$ 


---

### Post by olskar on 2008-07-20
Does not work for me either

---

### Post by cnolanAU on 2008-07-20
> **I_can_see_the_light said:**
> My problems have been temporarily solved by using the workaround at Ubuntu Wiki: [https://wiki.ubuntu.com/PowerManagement]("https://wiki.ubuntu.com/PowerManagement"). Can't believe I missed to check that site. Have been searching the net like a mad man for a solution since none of the ugly fixes worked for me. Load_cycle_count is still increasing a little to fast, but nothing like the the way it was before.

I just found this site also, tried it out and it worked flawlessly, so came back here to see if it'd been mentioned.  The solution on the wiki does appear to be cleaner.

---

### Post by Polygon on 2008-07-20
ill try that way in the wiki...is there any way to test that it works?

edit: it seems to not work, i went up 5 load cycles in 8 minutes.

EDIT: forget it, i'm just going to have to put vista back on this laptop. I don't want to, but i NEED this laptop to last as long as it can and this bug (wherever it lies) has already taken 30,000 out of the magic 60,000 and my laptop is not even a month old.

hopefully this bug will be fixed in future releases =/

---

### Post by I_can_see_the_light on 2008-07-21
> **Polygon said:**
> ill try that way in the wiki...is there any way to test that it works?

edit: it seems to not work, i went up 5 load cycles in 8 minutes.

EDIT: forget it, i'm just going to have to put vista back on this laptop. I don't want to, but i NEED this laptop to last as long as it can and this bug (wherever it lies) has already taken 30,000 out of the magic 60,000 and my laptop is not even a month old.

hopefully this bug will be fixed in future releases =/


Your drive is probably rated for 600,000 cycles, not 60,000 ;)

Anyway, did you enable *LAPTOP_MODE_ON_AC* in *laptop-mode.conf*? That's what I did and I also changed the HDD spin down value to 60 seconds when on AC

---

### Post by frodon on 2008-07-21
Don't mix laptop_mode and pm-util they don't play well together.

I used the laptop mode way in gutsy but swiched to the pm-util way with hardy for 2 reasons :
1- The fix with laptop_mode were less efficient for me under hardy.
2- Laptop_mode will be dumped soon in favor of pm-util so it's rather an unmaintained tool in the ubuntu scope.

---

### Post by phend-one on 2008-07-21
Just how serious is this issue? I want to put ubuntu on my laptop (LG R500) but I am worried about this Load_Cycle_Count killing the HDD.

---

### Post by frodon on 2008-07-21
It is serious to fix it if you have the issue, maybe you're already having this on your windows install. At least with ubuntu you will know how to fix it.

It will take you 10 minutes to takes 2 samples and identify if you have the issue and 5 more minutes to aplly the fix. So it will cost you around 15 minutes, this is acceptable IMO.

---

### Post by cnolanAU on 2008-07-22
> **frodon said:**
> 
1- The fix with laptop_mode were less efficient for me under hardy.

What exactly do you mean by less efficient?

> **frodon said:**
> 
2- Laptop_mode will be dumped soon in favor of pm-util so it's rather an unmaintained tool in the ubuntu scope.
I hadn't heard this -- I thought pm-utils was just a consolidated suspend and resume tool -- but be that as it may, the solution in the wiki still appears to be less of a hack at this stage.  Three packages seem to be involved; laptop-mode-tools, acpi-support and pm-utils.  Of these three packages, laptop-mode-tools seems to be working as expected, whereas both acpi-support (power.sh) and pm-utils (laptop-tools) have hardcoded values that are unfortunately overwriting any user-configured values.

---

### Post by frodon on 2008-07-22
laptop_mode uses acpi-support as far as i know and acpi support is the one supposed to be dumped. pm-util has been introduced as purpose to provide a more appropriate solution to power saving matters.

Basically, nothing succeeded for me to get laptop_mode working after suspend and hibernate and in some cases the head parking control was less accurate than it was before. This is to add to the fact that laptop_mode, according to its dev, produces hang issue on some configurations, i never experienced this though.

This is why it's better to go with pm-util IMO as this tool should be actively developed in the future but i agree with you that in the current state laptop_mode has more features. Unfortunately laptop_mode is likely to disappear as no development effort seem to be put on it (feel free to add some more fresh news if you have some).

---

### Post by Arthur Archnix on 2008-07-22
I no expert Frodon, but what I think I know conflicts with what you think you know, and since you can't know what isn't true, one of us is not knowing what we think we do. 

Capiche? No? Let me try to be more clear...with what I believe to be true.

First, it's being actively developed. Latest changes implemented were done on July 15th. A week ago. Here's the [change log]("http://samwel.tk/laptop_mode/changelog").

Second, Ubuntu just merged laptop-mode from Sid, as shown [here]("https://launchpad.net/ubuntu/+source/laptop-mode-tools"), so it's not being phased out of Ubuntu nor is it being phased out of Debian. 

AFAIK pm-utils is replacing acpi. But the links provided by UbuntuDemon at the start of this thread have links to discussions involving Bart Samwell, current developer and maintainer in Debian who goes into much better detail about the relationship between acpi, acpi-support, apm, and laptop-mode. From what I recall, Ubuntu had bastardized his program to somehow depend on acpi-support. By merging from sid all that ugliness is gone and in intrepid you should be able to just enable laptop mode and forget about all this.

Just out of interest, I don't have that suse script installed anywhere, neither do I have acpi-support installed. Laptop-mode handles it all. 

Earlier I posted how I restrart laptop-mode, but you're certainly right that it doesn't make sense on this thread. But the fellow below me used it to rerun his suse hack which probably is the right way to go.

EDIT: And if it turns out I'm right about some or all of this, then demon's concern about using pm-utils is moot. The correct way may end up being to enable laptop-mode, and only on strange configurations where this runs into problems would you need to create those suse scripts and have them run by pm-utils. Time will tell.

---

### Post by frodon on 2008-07-22
Ok no need to restart this again, previous thread on this was closed for a good reason. I will leave you the link to laptop_mode developer comment himself, it says it rather well :
[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/224](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/224)

Let's go back on topic and talk about general stuff elsewhere.

Laptop_mode and pm-util fix both works as long as you don't use them at the same time. About laptop_mode future it depends of its dev and luck in finding the root cause of the hang issue.

---

### Post by mgph on 2008-07-23
hello, sorry for my stupid question but should I apply the ugly fix for my hard disk ? I'm totally novice for this and don't even know what numbers showing what things!

When I run "$ sudo smartctl -a /dev/sda | grep Load_Cycle_Count", I got this result -

193 Load_Cycle_Count        0x0032   200   200   000    Old_age Always       -       2303


thanks in advance

---

### Post by crtlbreak on 2008-07-23
mgph
you need to compare the load cycle count that you have just taken to another one in say 15 minutes - currently you only have one snapshot and cannot compare it anything else -  the change in load over a set time will indicate whether the patch is applicable to you.
that will be the only way of knowing.
regards

---

### Post by kva on 2008-07-24
Is it possible to solve this problem using powertop ?

Thanks

---

### Post by muadnu on 2008-07-28
I'm running Hardy on a Dell Vostro 1400. I used the Hardy (OpenSUSE) fix, but still haven't got it to work after resuming from suspend/hibernate. I know this has been asked several times already, but after reading many threads I'm still not sure as to whether there is a fix for this or not. Anyone knows?

---

### Post by crtlbreak on 2008-07-28
My IBM T40 with Hitachi Travelstar HD has definitely changed the Load Cycle since the patch application.

---

### Post by Arthur Archnix on 2008-07-28
> **muadnu said:**
> I'm running Hardy on a Dell Vostro 1400. I used the Hardy (OpenSUSE) fix, but still haven't got it to work after resuming from suspend/hibernate. I know this has been asked several times already, but after reading many threads I'm still not sure as to whether there is a fix for this or not. Anyone knows?

If there were a reliable way to do this I'm sure demon would have updated his original post. Have you tried copying the disk script you created in the Suse workaround from the power.d directory, to the sleep.d directory?

---

### Post by shrndegruv on 2008-07-28
hey i have a new M1530.  I am seeing some wierd results.  

When I have the computer on battery my LCC increases slowly.  when i plug it in it increases like crazy.  opposite of what it should be doing.  also when i set the mode to either 128 or 254 the LCC doesn't increase.  does this sound normal?

---

### Post by muadnu on 2008-07-29
> **Arthur Archnix said:**
> If there were a reliable way to do this I'm sure demon would have updated his original post. Have you tried copying the disk script you created in the Suse workaround from the power.d directory, to the sleep.d directory?

Ok, thanks, I'll try it and post back. But now I found out that the fix is not working at all, and I think the problem is that powersave mode is set to true even when I'm on AC power. Indeed, if I manually set it to false the hdparm value goes to the desired 254 instead of 128. I don't know if I'm missing something...

---

### Post by ThaRabbit on 2008-07-30
From what I understand from an extensive search, it's not the actual parking that is the issue: It's the fact that ubuntu seems to not allow the drive to be in sleep for more than a few seconds?

I've read several posts describing how the drive goes into sleep mode and immediately comes out of it, only moments later. 

Now back in 2007, people suggested this could be due to ext3 updating some uptime variables every 5 seconds or perhaps other services that could wake the drive. 

Considering how, during idle, Ubuntu seems to wake the drive alomst instantly and how windows seems to leave it in peace for longer periods of time: I'm wondering how this is progressing? Is ubuntu sticking to their "manufacturer knows best" idiology? Are manufacturers setting these apm settings based on the assumption that the native OS will not pull the drive back up from sleep status almost instantly?

Not to be offensive, but I've dug back quite a bit and the one working sollution seems to be to disable APM alltogether. Given the fact that other operating systems seem fully capable of using apm while not crushing though load cycles like if they where diet pills, I doubt this is the last word on this.

Merely looking for information, I truely like Ubuntu and have been using *nix systems for years. Which, I guess, is why I am so concerned.

*edit*

> hey i have a new M1530. I am seeing some wierd results.

When I have the computer on battery my LCC increases slowly. when i plug it in it increases like crazy. opposite of what it should be doing.

I have the exact same thing happening on my HP 6720s

---

### Post by muadnu on 2008-07-31
> **muadnu said:**
> Ok, thanks, I'll try it and post back. But now I found out that the fix is not working at all, and I think the problem is that powersave mode is set to true even when I'm on AC power. Indeed, if I manually set it to false the hdparm value goes to the desired 254 instead of 128. I don't know if I'm missing something...

I tried putting the script in sleep.d, and as it seems it is setting the hdparm value after resume, though it sets it to 128 regardless of being on AC, which is what's happening too when I power on the laptop, so I'm not sure about it. This is what's bothering me most now (see previous post). Any ideas?

---

### Post by BandD on 2008-07-31
> **ThaRabbit said:**
> From what I understand from an extensive search, it's not the actual parking that is the issue: It's the fact that ubuntu seems to not allow the drive to be in sleep for more than a few seconds?

I've read several posts describing how the drive goes into sleep mode and immediately comes out of it, only moments later. 

Now back in 2007, people suggested this could be due to ext3 updating some uptime variables every 5 seconds or perhaps other services that could wake the drive. 

Considering how, during idle, Ubuntu seems to wake the drive alomst instantly and how windows seems to leave it in peace for longer periods of time: I'm wondering how this is progressing? Is ubuntu sticking to their "manufacturer knows best" idiology? Are manufacturers setting these apm settings based on the assumption that the native OS will not pull the drive back up from sleep status almost instantly?

Not to be offensive, but I've dug back quite a bit and the one working sollution seems to be to disable APM alltogether. Given the fact that other operating systems seem fully capable of using apm while not crushing though load cycles like if they where diet pills, I doubt this is the last word on this.

Merely looking for information, I truely like Ubuntu and have been using *nix systems for years. Which, I guess, is why I am so concerned.

*edit*



I have the exact same thing happening on my HP 6720s



There are confirmed cases of this same problem in Windows and Mac as well.  The Mac fix is very similar to the OpenSuse fix, or so I've heard.  

Some have speculated that a "normal" windows installation doesn't actually let the heads park all that often due to constant disk access.  Though I'm not entirely convinced.  

The problem it seems is that dirve manufactures aren't really communicating with the OS manufacturers.  And it seems that the firmware the drive manufacturers write is buggy in many cases.  

There are many factors at play, more than just Ubuntu or other *nix distributions.  Though I've read at some point in this thread (or it's older, now dead, brother) that communication was beginning to happen between Ubuntu devs and the drive companies.  So hopefully a less ugly fix will come about in the near future.

---

### Post by Helical on 2008-08-03
Okay, so I'm definately suffering from this problem but I noticed an interesting thing: my load cycles increase very slowly (like I imagine they might on a desktop or something) when I'm listening to music through my laptop! It seems like a simple fix might be to just have a program running in the background that behaved the same way that an MP3 does. Also I haven't noticed any temperature increase when using this method as opposed to the one offered in this thread.

All the warnings on the first post about the fix make it seem pretty shady. Why can't someone post how to undo the 'fix' just like they posted how to do it? I only say that because it says that you should only do it if you know how to undo it; to me it seems like you could just tell us unless it's incredibly complicated or something. 

I'm not fixing it yet because of that but mine probably goes up >100 per hour. For now I'll stick with my 'fix' of listening to music (where it probably only goes up 10 per hour).

---

### Post by Arthur Archnix on 2008-08-03
Helical.. the workarounds listed by ubuntudemon involve creating a few new files. If you want to undo the changes, then delete those files.
```
sudo rm file
```

---

### Post by ThaRabbit on 2008-08-04
> **Helical said:**
> Okay, so I'm definately suffering from this problem but I noticed an interesting thing: my load cycles increase very slowly (like I imagine they might on a desktop or something) when I'm listening to music through my laptop! It seems like a simple fix might be to just have a program running in the background that behaved the same way that an MP3 does. Also I haven't noticed any temperature increase when using this method as opposed to the one offered in this thread.

All the warnings on the first post about the fix make it seem pretty shady. Why can't someone post how to undo the 'fix' just like they posted how to do it? I only say that because it says that you should only do it if you know how to undo it; to me it seems like you could just tell us unless it's incredibly complicated or something. 

I'm not fixing it yet because of that but mine probably goes up >100 per hour. For now I'll stick with my 'fix' of listening to music (where it probably only goes up 10 per hour).

Shutting down APM can cause drive overheating on _some_ hard drives in high load situation, hence the listing of the undo. I don't think that's an indication of the fix quality, however ugly it may be.

---

### Post by silkstone on 2008-08-04
I've not read through all of this, but it looks like the problem is caused (in some cases) by Ubuntu waking up the drive every few seconds.

Do the laptops affected have card readers? If so, check /var/log/kern.log

I had a problem with an internal card reader on a desktop machine, where the OS was detecting a voltage change every second (probably something in the card detection circuit) and writing this change to kern.log. Then, the updated kern.log was written to the HD every five seconds or so.

Apologies if this is not relevant, but I though it was worth mentioning.

---

### Post by muadnu on 2008-08-04
I still haven't been able to figure this out... Anyone?

> **muadnu said:**
> ... But now I found out that the fix is not working at all, and I think the problem is that powersave mode is set to true even when I'm on AC power. Indeed, if I manually set it to false the hdparm value goes to the desired 254 instead of 128. I don't know if I'm missing something...

---

### Post by Nergar on 2008-08-05
I am reading [https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695) but i really don't get it. 

Whats up with the "Temporary Workaround:" ([https://wiki.ubuntu.com/PowerManagement](https://wiki.ubuntu.com/PowerManagement))

Lets analyze:

> To correct disk-idleing in Ubuntu 8.04 you need to adjust the following:

[LIST]
[*]Enable CONTROL_HD_POWERMGMT=1 in /etc/laptop-mode/laptop-mode.conf
[INDENT][Bug]244832 missing hdparm -B setting during boot[/INDENT]

[*]Even though you may not ENABLE_LAPTOP_MODE_ON_BATTERY or _ON_AC in laptop-mode.conf, you still need to ENABLE_LAPTOP_MODE=true in /etc/default/acpi-support (another package's conffile).
[INDENT][Bug]244838 laptop-mode needs to be activated in two places[/INDENT]

[*]Comment the four $HDPARM blocks in /etc/acpi/power.sh and change the two $LAPTOP_MODE start/stop lines to "$LAPTOP_MODE auto"
[INDENT][Bug]244836 /etc/acpi/power.sh overrides user settings
[Bug]244831 /etc/acpi/power.sh overrides user scripts
[Bug]244844 Adapt laptop-mode-tools invocation to ubuntu's acpi-support / pm-tools packages[/INDENT]

[*]Create a bogus /etc/pm/power.d/laptop-tools script to override /usr/lib/pm-utils/power.d/laptop-tools.
[INDENT][Bug]239419 pm-utils has laptop-tools script which conflicts with laptop-mode-tools
[/INDENT]

[*]Still no hdparm setting after resume.
[INDENT][Bug]244833 missing hdparm -B setting during resume
[Bug]244839 /etc/acpi/start.d and resume.d scripts are not run.
[Bug]244844 Adapt laptop-mode-tools invocation to ubuntu's acpi-support / pm-tools packages also:
[Bug]238555 pm-utils doesn't reload hdparm.conf after a suspend[/INDENT]
[/LIST]


[LIST]
[*]Enable CONTROL_HD_POWERMGMT=1 in /etc/laptop-mode/laptop-mode.conf
Ok. Yes I can do that. And why isn't this the default?


[*]Even though you may not ENABLE_LAPTOP_MODE_ON_BATTERY or _ON_AC in laptop-mode.conf, you still need to ENABLE_LAPTOP_MODE=true in /etc/default/acpi-support (another package's conffile).
Yes, done. Again, why isn't this the default?


[*]Comment the four $HDPARM blocks in /etc/acpi/power.sh and change the two $LAPTOP_MODE start/stop lines to "$LAPTOP_MODE auto"
What is a block? Do you mean comment out every line starting with $HDPARM? Really? Why isn't this the default?!


[*]Create a bogus /etc/pm/power.d/laptop-tools script to override /usr/lib/pm-utils/power.d/laptop-tools.
Bogus? Are you serious? whats that? what do I put in there?
And whats up with all those bug links? Am I expected to read for 4 hours before I can fix this?


[*]Still no hdparm setting after resume.
???
[/LIST]

If I do this will it solve my problem?
Is it possible for someone to post a step by step guide for normal users?
Why is it so difficult to solve this? I even tried explaining to Wester Digital Support and they told me the HDD was not getting enough power from the USB port! 

I hope anyone can help and clarify all this and make it easy for normal users to fix this.

---

### Post by frodon on 2008-08-06
The answer is already in the thread.

Both fixes work (laptop_mode or pm-utils) but we tend to advice the pm-utils one as laptop_mode as few chance to get a real future in ubuntu.

Description in post #3 :
[http://ubuntuforums.org/showpost.php?p=5031047&postcount=3](http://ubuntuforums.org/showpost.php?p=5031047&postcount=3)

---

### Post by Nergar on 2008-08-07
> **frodon said:**
> The answer is already in the thread.

Both fixes work (laptop_mode or pm-utils) but we tend to advice the pm-utils one as laptop_mode as few chance to get a real future in ubuntu.

Description in post #3 :
[http://ubuntuforums.org/showpost.php?p=5031047&postcount=3](http://ubuntuforums.org/showpost.php?p=5031047&postcount=3)

Thanks a lot, and btw:

I really don't think post #3 is the best place to put this, and I certainly don't have the time to read 17 pages looking for "a new answer" or updates. This is very important and it should be easily accessible for everyone.

---

### Post by muadnu on 2008-08-07
> **Arthur Archnix said:**
> If there were a reliable way to do this I'm sure demon would have updated his original post. Have you tried copying the disk script you created in the Suse workaround from the power.d directory, to the sleep.d directory?

I tried putting it in the sleep.d directory but it doesn't work. Moreover, suspending stopped working, somehow having the script there made the suspend sequence stall.

---

### Post by Belerophon on 2008-08-07
I agree with Nergar.

Just to say that, in a matter like this, in which our hard drives can get harmed, these kind of topics should be placed elsewhere...I don't really have a solution and I'm not saying that what demon wrote isn't a really good job, but maybe it's time to move what is known about this "bug" and any upcoming updates to another place...

..it's just an opinion, don't know if anyone else agrees...

Thanks.

---

### Post by sergiom99 on 2008-08-07
> **Nergar said:**
> Thanks a lot, and btw:

I really don't think post #3 is the best place to put this, and I certainly don't have the time to read 17 pages looking for "a new answer" or updates. This is very important and it should be easily accessible for everyone.

Yes.
You can subscribe to this thread and get the updates.
And/or you can create a page in the ubuntu wiki.

---

### Post by OlaNordmann on 2008-08-07
I'm thinking that my laptop (Dell XPS M1530) might be affected, the temperature seems to be increasing alot.. But smarttools won't give me any output on it.

```
laptop:/home/user# smartctl -a /dev/sda | grep Load_Cycle_Count
laptop:/home/user# 

```
While "grep temperature" does.
```
laptop:/home/user# smartctl -a /dev/sda | grep Temperature
194 Temperature_Celsius     0x0022   100   085   000    Old_age   Always       -       46 (Lifetime Min/Max 15/51)
laptop:/home/user# 

```
As you can see, there's no "load cycle count" at all:
> SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   100   051    Pre-fail  Always       -       175
  3 Spin_Up_Time            0x0007   252   252   025    Pre-fail  Always       -       2750
  4 Start_Stop_Count        0x0032   059   059   000    Old_age   Always       -       422506
  5 Reallocated_Sector_Ct   0x0033   252   252   010    Pre-fail  Always       -       0
  9 Power_On_Hours          0x0032   093   093   000    Old_age   Always       -       3893
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       186
191 G-Sense_Error_Rate      0x0032   092   092   000    Old_age   Always       -       80955
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       115
194 Temperature_Celsius     0x0022   100   085   000    Old_age   Always       -       46 (Lifetime Min/Max 15/51)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       88240
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       1150
198 Offline_Uncorrectable   0x0030   100   100   000    Old_age   Offline      -       1307
199 UDMA_CRC_Error_Count    0x0036   252   252   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x000a   252   252   000    Old_age   Always       -       0

SMART Error Log Version: 1
No Errors Logged


I should mention that I'm running pure debian-strength with smartctl version 5.38 installed from the official repositories.

Please, do help. :confused:

---

### Post by Nergar on 2008-08-08
> **OlaNordmann said:**
> I'm thinking that my laptop (Dell XPS M1530) might be affected, the temperature seems to be increasing alot.. But smarttools won't give me any output on it.

```
laptop:/home/user# smartctl -a /dev/sda | grep Load_Cycle_Count
laptop:/home/user# 

```
While "grep temperature" does.
```
laptop:/home/user# smartctl -a /dev/sda | grep Temperature
194 Temperature_Celsius     0x0022   100   085   000    Old_age   Always       -       46 (Lifetime Min/Max 15/51)
laptop:/home/user# 

```
As you can see, there's no "load cycle count" at all:


I should mention that I'm running pure debian-strength with smartctl version 5.38 installed from the official repositories.

Please, do help. :confused:

Try pasting all the output of smartctl and also try "sudo fdisk -l"

I don't think 46 is that high. check your cpu temp instead
Mine says 0-60° is normal operation. [http://www.wdc.com/en/products/products.asp?driveid=377#jump77](http://www.wdc.com/en/products/products.asp?driveid=377#jump77)

---

### Post by OlaNordmann on 2008-08-08
Thanks alot for the reply, Nergar.
Your help is really appreciated :)

Anyway; here's the fdisk output.
> laptop:/home/user# fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000161bd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30071   241545276   83  Linux
/dev/sda2           30072       30401     2650725    5  Extended
/dev/sda5           30072       30401     2650693+  82  Linux swap / Solaris
And here is the complete smartctl output:
> laptop:/home/user# smartctl -a /dev/sda
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF INFORMATION SECTION ===
Device Model:     SAMSUNG HM250JI
Serial Number:    S133JD0Q124141
Firmware Version: HS100-11
User Capacity:    250*059*350*016 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  ATA/ATAPI-7 T13 1532D revision 0
Local Time is:    Fri Aug  8 16:08:18 2008 CEST

==> WARNING: May need -F samsung or -F samsung2 enabled; see manual for details.

SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00)	Offline data collection activity
					was never started.
					Auto Offline Data Collection: Disabled.
Self-test execution status:      (  32)	The self-test routine was interrupted
					by the host with a hard or soft reset.
Total time to complete Offline 
data collection: 		 ( 103) seconds.
Offline data collection
capabilities: 			 (0x5b) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Suspend Offline collection upon new
					command.
					Offline surface scan supported.
					Self-test supported.
					No Conveyance Self-test supported.
					Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					General Purpose Logging supported.
Short self-test routine 
recommended polling time: 	 (   2) minutes.
Extended self-test routine
recommended polling time: 	 ( 103) minutes.
SCT capabilities: 	       (0x003f)	SCT Status supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   100   051    Pre-fail  Always       -       175
  3 Spin_Up_Time            0x0007   252   252   025    Pre-fail  Always       -       2750
  4 Start_Stop_Count        0x0032   058   058   000    Old_age   Always       -       429022
  5 Reallocated_Sector_Ct   0x0033   252   252   010    Pre-fail  Always       -       0
  9 Power_On_Hours          0x0032   093   093   000    Old_age   Always       -       3908
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       186
191 G-Sense_Error_Rate      0x0032   092   092   000    Old_age   Always       -       81140
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       115
194 Temperature_Celsius     0x0022   106   085   000    Old_age   Always       -       44 (Lifetime Min/Max 15/51)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       88986
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       1151
198 Offline_Uncorrectable   0x0030   100   100   000    Old_age   Offline      -       1307
199 UDMA_CRC_Error_Count    0x0036   252   252   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x000a   252   252   000    Old_age   Always       -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%        11         -
# 2  Short offline       Completed without error       00%        10         -
# 3  Short offline       Aborted by host               150%        10         -
# 4  Short offline       Completed without error       00%         0         -
# 5  Short offline       Aborted by host               150%         0         -

SMART Selective Self-Test Log Data Structure Revision Number (0) should be 1
SMART Selective self-test log data structure revision number 0
Warning: ATA Specification requires selective self-test log data structure revision number = 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Interrupted [00% left] (0-65535)
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.

In case you're wondering. running -F samsung/samsung2 returns the exact same thing.

The main cause of high temperatures is my graphics card (running at 60-70C). But nevertheless, it would be smart to check if I'm affected. Especially since this wiki says i am.

[http://wiki.debian.org/InstallingDebianOn/Dell/XPSm1530](http://wiki.debian.org/InstallingDebianOn/Dell/XPSm1530)

---

### Post by Nergar on 2008-08-09
> **OlaNordmann said:**
> Thanks alot for the reply, Nergar.
Your help is really appreciated :)

Anyway; here's the fdisk output.
And here is the complete smartctl output:
In case you're wondering. running -F samsung/samsung2 returns the exact same thing.

The main cause of high temperatures is my graphics card (running at 60-70C). But nevertheless, it would be smart to check if I'm affected. Especially since this wiki says i am.

[http://wiki.debian.org/InstallingDebianOn/Dell/XPSm1530](http://wiki.debian.org/InstallingDebianOn/Dell/XPSm1530)

Wierd, look at this: [http://ubuntuforums.org/showpost.php?p=4263078&postcount=696](http://ubuntuforums.org/showpost.php?p=4263078&postcount=696)

And I also found your drive listed here: [https://wiki.ubuntu.com/DanielHahler/Bug59695](https://wiki.ubuntu.com/DanielHahler/Bug59695)

I would apply the fix, but I hope someone can help you more on that

---

### Post by AbtZ on 2008-08-11
> **muadnu said:**
> I'm running Hardy on a Dell Vostro 1400. I used the Hardy (OpenSUSE) fix, but still haven't got it to work after resuming from suspend/hibernate. I know this has been asked several times already, but after reading many threads I'm still not sure as to whether there is a fix for this or not. Anyone knows?

[Here's how I solved it]("http://ubuntuforums.org/showthread.php?p=5564900").

However, this was after solving the load-cycle problem through the use of laptop-mode as [described in the Ubuntu wiki]("https://wiki.ubuntu.com/PowerManagement"). I don't know if it's the optimal solution, but everything works fine for me right now, so I have no complaints.

---

### Post by carlosbertholdi on 2008-08-14
I have an Asus G1S with a Hitachi hdd by the model HTS542516K9SA00, and I'm using Ubuntu 7.10, I never update it.

I'm using this command:

*sudo smartctl -a /dev/sda | egrep '(Load_Cycle_Count|Temperature)'*

to monitor the load cycle and the result is ALWAYS like this:

[I]193 Load_Cycle_Count        0x0012   098   098   000    Old_age   Always       -       **20698**
194 Temperature_Celsius     0x0002   127   127   000    Old_age   Always       -       43 (Lifetime Min/Max 14/53)[/I]

The temperature changes sometime from 43 to 46.

Is it ok to have the same load cycle count( 20698 ) after hours?

---

### Post by ThaRabbit on 2008-08-15
> **carlosbertholdi said:**
> I have an Asus G1S with a Hitachi hdd by the model HTS542516K9SA00, and I'm using Ubuntu 7.10, I never update it.

I'm using this command:

*sudo smartctl -a /dev/sda | egrep '(Load_Cycle_Count|Temperature)'*

to monitor the load cycle and the result is ALWAYS like this:

[I]193 Load_Cycle_Count        0x0012   098   098   000    Old_age   Always       -       **20698**
194 Temperature_Celsius     0x0002   127   127   000    Old_age   Always       -       43 (Lifetime Min/Max 14/53)[/I]

The temperature changes sometime from 43 to 46.

Is it ok to have the same load cycle count( 20698 ) after hours?

It simply means your drive never spins down, did you apply the patch mentioned in this thread or not? (it effectively prevents down spinning when on AC)

CHeck on your hard drive manufacturer's website what the operating temperature range of your hard drive is to determine if this is ok.

Result of NEVER spinning down:
1. Possible overheat (check operating temperature specifications)
2. Higher risk at damage when moving the laptop around when in operation
3. Higher power consumption.
4. When used carefully (laptop always sat stable / temperature is ok) possible longer lifetime

Is your laptop always on AC?

---

### Post by prince_niceguy on 2008-08-15
I too had this problem and fixed with the scripts given.

Model of laptop & hard disk if known. - Toshiba M500 Protege (Hard drive not known)
1 hour cycle count before fix & after - count increased by 4 in just 1 minute so applied the fix.
Temperature before fix & after fix - disk temprature before fix 45. after fix 41.

---

### Post by carlosbertholdi on 2008-08-16
Thanks for the answer ThaRabbit. No, I didn't applied the fix, about the temperature, I downloaded a datasheet, but the only thing it says about temperature is "Ambient Temperature" 5 to 55 degrees Celsius. I think temperature is ok. 
It's almost all the times on AC power, I never use it on battery more than 5 minutes or so.
I'm monitoring the load cycle and I notice that when I turn on the laptop I got 2 more counts, probably 1 count when turn it off and another when I turn it on again, when it's on, like the whole day on AC power I got the same count at the end of the day.
The counting now is at **20717**

---

### Post by muadnu on 2008-08-20
> **AbtZ said:**
> [Here's how I solved it]("http://ubuntuforums.org/showthread.php?p=5564900").

However, this was after solving the load-cycle problem through the use of laptop-mode as [described in the Ubuntu wiki]("https://wiki.ubuntu.com/PowerManagement"). I don't know if it's the optimal solution, but everything works fine for me right now, so I have no complaints.

Thank you AbtZ. I finally got around to do this, and it worked!

Just a little question. I'm not sure I understood how the laptop-mode fix works. But it turns out than when I go to battery the hdparm value goes to 1 instead of 128 as I wanted. Do you know how I should set this up?

---

### Post by AbtZ on 2008-08-20
Glad to hear it works :)

To change your hd power management values do
```
sudo gedit /etc/laptop-mode/laptop-mode.conf
```
Scroll down until you find the power managment for HD part and then change to ```
BATT_HD_POWERMGMT=150
``` or whichever hdparm -B value you prefer.

---

### Post by Polygon on 2008-08-26
does anyone know the stats of this problem in intrepid? Like, is it fixed, or will be fixed?

---

### Post by frodon on 2008-08-26
You should better look at the kernel development news as this problem is more related to the linux kernel itself than to a specific distribution.
If they did not deal with the power saving matters yet intrepid is more likely to have the problem too.

---

### Post by carlosbertholdi on 2008-08-28
I don't think this problem is a Linux bug, I think it's a problem with the hard drive itself, because I'm running ubuntu 7.10 on my Asus G1S and it doesn't seem to have this problem. I've read an article about load cycle problem 2 weeks ago and from what I can recall, it said that people with high load cycle counts on ubuntu have high load cycle counts on windows as well, just that on ubuntu the count was a little bit higher than on windows.

---

### Post by Polygon on 2008-08-28
i decided to install ubuntu and try this again, but still, im following the opensuse guide to the letter, but when i test the script, and i disable powersave, it still shows a star next to the output which means its still enabled. Can anyone help?

EDIT: after some tests, it seems that the workaround DOES work, but the star is still there, and according to the opensuse guide, that means its not working, when really it is. Should i edit it?

and also, i heard that this work around does not work when you come out of suspend/hibernate, does anyone know how to fix that?

---

### Post by Linux-World on 2008-08-30
> **carlosbertholdi said:**
> I don't think this problem is a Linux bug, I think it's a problem with the hard drive itself, because I'm running ubuntu 7.10 on my Asus G1S and it doesn't seem to have this problem. I've read an article about load cycle problem 2 weeks ago and from what I can recall, it said that people with high load cycle counts on ubuntu have high load cycle counts on windows as well, just that on ubuntu the count was a little bit higher than on windows.
when i had windows, the count rised up more than in ubuntu...:S

---

### Post by linux5uper on 2008-09-01
> **Polygon said:**
> 
and also, i heard that this work around does not work when you come out of suspend/hibernate, does anyone know how to fix that?

I use the Gutsy fix in Hardy, and everything is working fine. Otherwise I think the Opensuse solution should work after suspend/resume as well. But I'll let someone who's using it confirm this.

---

### Post by ThaRabbit on 2008-09-01
> **carlosbertholdi said:**
> Thanks for the answer ThaRabbit. No, I didn't applied the fix, about the temperature, I downloaded a datasheet, but the only thing it says about temperature is "Ambient Temperature" 5 to 55 degrees Celsius. I think temperature is ok. 
It's almost all the times on AC power, I never use it on battery more than 5 minutes or so.
I'm monitoring the load cycle and I notice that when I turn on the laptop I got 2 more counts, probably 1 count when turn it off and another when I turn it on again, when it's on, like the whole day on AC power I got the same count at the end of the day.
The counting now is at **20717**

Sorry for the late reply this time, holiday and such ;)

Based on what you tell me, I see no reason for you to be worried at all. 

You might try to use it on battery mode for an hour and log the load cycle increase.

---

### Post by Neovos on 2008-09-11
Not sure where the official thread for this is anymore, but here is my laptop info regarding this bug:

Asus M51Sn Laptop running 8.04 x86-64 on 2.6.24-19.

Before fix:```
brian@Apollo:/etc/init.d$ date; sudo smartctl -a /dev/sda | egrep '(Load_Cycle_Count|Temperature)'
Fri Aug 29 00:54:08 PDT 2008
193 Load_Cycle_Count        0x0032   199   199   000    Old_age   Always       -       5062
194 Temperature_Celsius     0x0022   108   104   000    Old_age   Always       -       39
brian@Apollo:/etc/init.d$ date; sudo smartctl -a /dev/sda | egrep '(Load_Cycle_Count|Temperature)'
Fri Aug 29 01:11:08 PDT 2008
193 Load_Cycle_Count        0x0032   199   199   000    Old_age   Always       -       5089
194 Temperature_Celsius     0x0022   109   104   000    Old_age   Always       -       38
brian@Apollo:/etc/init.d$ date; sudo smartctl -a /dev/sda | egrep '(Load_Cycle_Count|Temperature)'
Fri Aug 29 01:22:08 PDT 2008
193 Load_Cycle_Count        0x0032   199   199   000    Old_age   Always       -       5105
194 Temperature_Celsius     0x0022   110   104   000    Old_age   Always       -       37
brian@Apollo:/etc/init.d$
```

Testing out different values:```
brian@Apollo:/etc/acpi/resume.d$ date; sudo smartctl -a /dev/sda | egrep '(Load_Cycle_Count|Temperature)'
Fri Aug 29 01:33:31 PDT 2008
193 Load_Cycle_Count        0x0032   199   199   000    Old_age   Always       -       5118
194 Temperature_Celsius     0x0022   109   104   000    Old_age   Always       -       38
brian@Apollo:/etc/acpi/resume.d$ date; sudo smartctl -a /dev/sda | egrep '(Load_Cycle_Count|Temperature)'
Fri Aug 29 01:35:14 PDT 2008
193 Load_Cycle_Count        0x0032   199   199   000    Old_age   Always       -       5122
194 Temperature_Celsius     0x0022   109   104   000    Old_age   Always       -       38
brian@Apollo:/etc/acpi/resume.d$ sudo hdparm -B 200 /dev/sda

/dev/sda:
 setting Advanced Power Management level to 0xc8 (200)
brian@Apollo:/etc/acpi/resume.d$ date; sudo smartctl -a /dev/sda | egrep '(Load_Cycle_Count|Temperature)'
Fri Aug 29 01:35:51 PDT 2008
193 Load_Cycle_Count        0x0032   199   199   000    Old_age   Always       -       5125
194 Temperature_Celsius     0x0022   109   104   000    Old_age   Always       -       38
brian@Apollo:/etc/acpi/resume.d$ sudo hdparm -B 250 /dev/sda

/dev/sda:
 setting Advanced Power Management level to 0xfa (250)
brian@Apollo:/etc/acpi/resume.d$ sudo hdparm -B 250 /dev/sda

/dev/sda:
 setting Advanced Power Management level to 0xfa (250)
brian@Apollo:/etc/acpi/resume.d$ date; sudo smartctl -a /dev/sda | egrep '(Load_Cycle_Count|Temperature)'
Fri Aug 29 01:37:30 PDT 2008
193 Load_Cycle_Count        0x0032   199   199   000    Old_age   Always       -       5127
194 Temperature_Celsius     0x0022   110   104   000    Old_age   Always       -       37
brian@Apollo:/etc/acpi/resume.d$ date; sudo smartctl -a /dev/sda | egrep '(Load_Cycle_Count|Temperature)'
Fri Aug 29 01:55:18 PDT 2008
193 Load_Cycle_Count        0x0032   199   199   000    Old_age   Always       -       5154
194 Temperature_Celsius     0x0022   109   104   000    Old_age   Always       -       38
```

For some reason, different values did nothing to the frequency for me. It seemed like it's either on or off.

And for me, the 254 setting and 255 effectively both disabled it.
```
brian@Apollo:/etc/acpi/resume.d$ date; sudo smartctl -a /dev/sda | egrep '(Load_Cycle_Count|Temperature)'
Fri Aug 29 01:56:20 PDT 2008
193 Load_Cycle_Count        0x0032   199   199   000    Old_age   Always       -       5155
194 Temperature_Celsius     0x0022   109   104   000    Old_age   Always       -       38
brian@Apollo:/etc/acpi/resume.d$ date; sudo smartctl -a /dev/sda | egrep '(Load_Cycle_Count|Temperature)'
Fri Aug 29 02:06:04 PDT 2008
193 Load_Cycle_Count        0x0032   199   199   000    Old_age   Always       -       5155
194 Temperature_Celsius     0x0022   106   104   000    Old_age   Always       -       41
brian@Apollo:/etc/acpi/resume.d$ date; sudo smartctl -a /dev/sda | egrep '(Load_Cycle_Count|Temperature)'
Fri Aug 29 02:11:15 PDT 2008
193 Load_Cycle_Count        0x0032   199   199   000    Old_age   Always       -       5155
194 Temperature_Celsius     0x0022   105   104   000    Old_age   Always       -       42
brian@Apollo:/etc/acpi/resume.d$ date; sudo smartctl -a /dev/sda | egrep '(Load_Cycle_Count|Temperature)'
Fri Aug 29 02:25:11 PDT 2008
193 Load_Cycle_Count        0x0032   199   199   000    Old_age   Always       -       5155
194 Temperature_Celsius     0x0022   104   104   000    Old_age   Always       -       43
brian@Apollo:/etc/acpi/resume.d$ date; sudo smartctl -a /dev/sda | egrep '(Load_Cycle_Count|Temperature)'
Fri Aug 29 03:11:32 PDT 2008
193 Load_Cycle_Count        0x0032   199   199   000    Old_age   Always       -       5155
194 Temperature_Celsius     0x0022   103   103   000    Old_age   Always       -       44
brian@Apollo:/etc/acpi/resume.d$ date; sudo smartctl -a /dev/sda | egrep '(Load_Cycle_Count|Temperature)'
Fri Aug 29 03:11:47 PDT 2008
193 Load_Cycle_Count        0x0032   199   199   000    Old_age   Always       -       5155
194 Temperature_Celsius     0x0022   103   103   000    Old_age   Always       -       44
```

I also want to point out that for hardy, in terms of resuming from suspend and having this script run, it won't work in /etc/acpi/resume.d because of pm utilities. The script needs to be put in /etc/pm/sleep.d for it to work. I was setting this manually for a couple months on resume before I found this out and now it's fixed. That change needs to be more obvious in the instructions if it's in there at all.

I found this out here: [https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/205005](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/205005)

---

### Post by linux5uper on 2008-09-11
Thanks for pointing this out, I hadn't noticed it before.

Does this apply to the script suggested for OpenSuse too?

---

### Post by david_e on 2008-09-13
I have this issue on an old laptop (used as a mail client by my mother) and **the hdparm workaround is not working for it**: I was experiencing 2 clicks per minute even with hdparm -B254 -S0.

Finally I came out with a really ugly workaround: it stops the clicks and it does not rely on hdparm, **but I don't know if this is really a good idea to implement**. Basically I am forcing the drive to stay alive by making periodic writes to a small file in the background. I made a stupid script like this:

```

#!/bin/bash

outfile=$(mktemp)

while [ true ]; do
    dd if=/dev/zero of=$outfile bs=1K count=10 &> /dev/null
    sleep 15
    echo > $outfile
    sleep 5
done

```

saved it in /usr/local/bin as ugly_fix.sh, chmodded +x it and made it start at boot from /etc/rc.local by adding:

```

nice -n 19 /usr/local/bin/ugly_fix.sh &

```

before the return. This works very well for me and does not interfere with my activities even while doing heavy disk usage as its very low priority. Off course I don't suggest this if the hdparm solution works for you as keeping the disk alive all the time is not a really good thing to do to keep it healthy and can have nasty consequences in case of shocks. But I think that this is better then having the disk clicking all the time and the resulting behavior is no different from the one of the OS for which that laptop was designed for as it was always doing IO swapping activities on that (P-III mobile + 300 Mb di RAM and Windows XP...).

Just wanted to share and hear any opinion on this "desperate workaround".

PS: I am using Debian Lenny on that as even Xubuntu is too heavy for that :D
PPS: **Commit time settings for the filesystems may be relevant for this workaround to work: I am using the default 5sec on ext3, and laptop_mode is disabled**.

---

### Post by Halbarad on 2008-09-16
I'm using Jakon's fix:
[http://ubuntuforums.org/showpost.php?p=4897802&postcount=842]("http://ubuntuforums.org/showpost.php?p=4897802&postcount=842")
The issue with this fix is that it disables head parking both on AC and on battery but I think this is okay for me, because my laptop is normally off when I travel with it. Or perhaps head parking is advisable even before carrying a powered off laptop?
 
The Load_Cycle_Count has frozen at 48370, but the HD temperature is higher than usual.
It used to be around 30 Celsius -- it now reaches 39, then the fan goes up and keeps it around 38.
My question is: smartctl gives me 0/16 as a Lifetime Min/Max.

```
 194 Temperature_Celsius     0x0022   039   048   000    Old_age   Always       -       39 (Lifetime Min/Max 0/16)

```
What do these Min/Max figures mean? I think they do **not** mean I ought to keep my HD in a fridge...

---

### Post by Halbarad on 2008-09-16
Sorry --- already found. I got my hd name with smartctl /dev/sda -i, then I found the specs on Google: 5-60 Celsius. However, I'd be grateful if you could answer the question about possible dangers in carrying a laptop with unparked heads...

---

### Post by Halbarad on 2008-09-17
Uh oh -- found out this one too. Every time I power on the laptop, the Load_Cycle_Count increases by one, and I guess this means that the heads are in fact parked on suhtdown.

---

### Post by david_e on 2008-09-17
> **Halbarad said:**
> Uh oh -- found out this one too. Every time I power on the laptop, the Load_Cycle_Count increases by one, and I guess this means that the heads are in fact parked on suhtdown.
It's ok that heads are parked at shutdown: otherwise the drive could be damaged when moving the laptop. You should not worry about it as a standard laptop hard drive can do 200'000 to 600'000 parking in its life: 200'000 power cycles are by far more than any hard disk can substain: if you start and stop your computer 5 times a day it will take 109 years to break the drive. Obviously it will fail for some other reason well before that time! :D

---

### Post by Halbarad on 2008-09-17
Thank you! But I just meant I have found out the reply to my previous question...
I wonder what exactly happens once head parking is disabled. Does the hard disk go on spinning all the time? I mean, what is the reason for the increase in temperature? And in this case, would this not be another aging factor for the HD?

---

### Post by david_e on 2008-09-17
The "ugly fix" (not the one from me) and the Jakon's one **will set the HD Advanced Power Management to "highest I/O performance" and, as a side effect, this will also prevent the drive from parking**, but IMHO it will have other effects on the drive that could lead to a temperature increase, even unrelated with the parking: it's reasonable that this happens as this fixes are pushing the drive to its maximum I/O capabilities. (see the hdparm man page).

You can try to adjust the apm settings to something lower than 254: for example 200 stops the parking for me (not on the laptop of my post above) and it seems that I have a lower temperature than with 254. You have to experiment with different settings to see what is the minimal value for which you have no parking or a reasonable number of "clicks" (less than one every ten minute is ok as this will break your drive in 3 years of non-stop usage, more than the expected life time of a notebook drive), with a lower APM setting the drive **should** be less stressed but this really depends on the HD: I think that the drive will just check if the apm setting is in a certain range, but the actual value will not matter so for example 254 and 230 could be the same on certain drives...

*** edit ***
Sorry I did some confusion with spinning/parking.

---

### Post by Halbarad on 2008-09-17
Thank you. I've read man hdparm and tried something. 254 down to 192 entirely suppresses the clicking on my laptop; as soon as I get below 192 (that is to say, as soon as bit 7 is zeroed), the clicking starts again, more or less at the same rate I was used to before. On the other hand, the temperature is significantly lower at hdparm 192 than it was at hdparm 254: 31 C vs. 39-40. Thus, it looks as if I've found the optimal settings for my hd! I have modified the patch to /etc/hdparm.conf accordingly. Time to relax and watch a good movie! :popcorn:

---

### Post by -Tauren- on 2008-09-20
the only thing putting me off using ubuntu is this problem. even if i had a load cycle similar to vista i'd be happy.


will this be fixed in the next release of ibex?

---

### Post by linux5uper on 2008-09-20
> **-Tauren- said:**
> the only thing putting me off using ubuntu is this problem. even if i had a load cycle similar to vista i'd be happy.


will this be fixed in the next release of ibex?

I guess the source of the problem is different for different people, but for my machine, it's the hard drive's manufacturer settings. What that means is that I have the problem in Ubuntu, Vista and XP. The only difference is that in Windows I could not enable the s.m.a.r.t. capabilities of my drive (and I tried about 10 different tools), while in Ubuntu I applied the so-called 'ugly-fix' and I fixed it. 

So I think you should not be quick to point at Ubuntu as the problem, it might be the only way to actually be in control of these settings and to fix the problem.

---

### Post by luismanson on 2008-09-22
so, Hi all, im not shute if im afected by this, im using my laptop almos allways on AC, i have this one for a week and i already have 2225 load cycle count, i use it like 14 hours/day....

how do you measure this in an eficent way? maybe i dont get something....
i made a script which does something like:

smartctl -a /dev/sda | grep Load_Cycle_Count
hdparm -B 1
sleep 2m
smartctl -a /dev/sda | grep Load_Cycle_Count
sleep 5m
smartctl -a /dev/sda | grep Load_Cycle_Count
sleep 10m


and so on, with diffent values for -S, because a dont see any patter with the 1-255 values, some makes the count increase by 3/10 min and some others by 8/10 min....
im also measung this from a gnome-terminal with the sistem being idle, on AC....

sholdnt -B have a pattern??????

the funny part is that i need a stethoscope to heard the drive spin up/down... :|

---

### Post by Halbarad on 2008-09-23
Hi Luis, I think 2000 clicks per week is really not bad -- as far as head parking is concerned, you can expect at least some 6 years lifetime for your HD (600,000 hours is the minimum expected value, and it would mean 300 weeks for you). I had 2000 **per day**.
I think you really ought to experiment with different values with 
```
sudo hdparm -B <value>
```
Reading man hdparm about the option -B was very useful to me. The clicking ought to be completely suppressed by such values as 255 or 254; just begin with the 255 and gradually lower it until you find an acceptable clicking rate. If neither 255 nor 254 work, I don't really know what to say -- let's wait a reply from anyone who knows better than me.
But I insist that a count of 2225 for one week, say, 6 days, 14 hours a day, is not bad at all, because you have more or less 2225/(14*6)=26.5 clicks per hour, less than 0.5 clicks per minute, which is really fine.

---

### Post by gianluca.pettinello on 2008-09-23
My first reply in an ubuntu forum !


You can easily set the hdparm in pm-utils, which will be the supported tool to tune power management in ubuntu next releases.

You copy laptop-tools from /usr/lib/pm-utils/power.d/into /etc/pm-utils/power.d/

and then you write
hdparm -q -B $APM_VAL /dev/sda 2 > /dev/null 

and in the if section you set APM_VAL=254 when on ac power and =1 when on battery

---

### Post by luismanson on 2008-09-23
> **gianluca.pettinello said:**
> My first reply in an ubuntu forum !

You can easily set the hdparm in pm-utils, which will be the supported tool to tune power management in ubuntu next releases.


pm-utils is the next?!!!
i tought it was the older...apm related

---

### Post by luismanson on 2008-09-23
Wird, i overwrited all files to the originals and did:
> 
hdparm -I /dev/sda|grep ower
        Advanced power management level: disabled
           *    Power Management feature set
                Advanced Power Management feature set
                Device-initiated interface power management



and the drive spins down after a few seconds...
i think im gona have to give som heavy use the weekend and see the count...

---

### Post by luismanson on 2008-09-24
I got this from Fujitsu support:
[http://www.scribd.com/doc/6209343/Fujitsu-APM](http://www.scribd.com/doc/6209343/Fujitsu-APM)
They also toldme:
> We don't support the program, nor do we use it

We only support 3 APM settings on our drives
We have no idea what he will get if he uses any of the 127
values with this program.

Attached are the details of our 3 settings
beyond this I suggest he find out who wrote HDPARM and
ask them what the program is actually doing any ideas?

i did not make any tests yet, but converting hex to dec i got:

FR = 05h : Enable APM = **5?**
[INDENT]
SC = C0h - FEh : Mode-0 Active Idle Low Power Idle =**SC =  192- 254**
SC = 80h - BFh : Mode-1 Active Idle Low Power Idle (Default) = **SC = 128 - 191**
SC = 01h - 7Fh : Mode-2 Active Idle Low Power Idle Standby =** SC = 1 - 127**
[/INDENT]
FR = 85h : Disable APM (Set Mode-0) =** 133**

---

### Post by Digz on 2008-09-26
Is this a Hardware problem or a Software problem caused by linux ?

---

### Post by david_e on 2008-09-26
AFAIK this is an hardware issue (a problem in the drive firmware) exposed by Linux.

---

### Post by Digz on 2008-09-26
Is there a Windows fix for those that dual boot ?

---

### Post by david_e on 2008-09-26
Some manufacturers makes some utilities to tune the firmware settings (for example Hitachi does), using bootable dos-based cds or, maybe, windows based applications. You can try checking your hard disk maker web page for these tools (read carefully the documentation before doing anything to avoid damaging your drive), but the hdparm Linux solution is recommended as this won't make any permanent modification to your drive firmware. I think that there is something similar to hdparm under windows too.

---

### Post by Digz on 2008-09-26
Thanks

---

### Post by TigPT on 2008-09-30
I hade the same problem in my ASUS F3KA and sloved it with [this]("http://ubuntuforums.org/showthread.php?t=795327") tutorial.

Good luck to everyone with a ASUS F3KA.

---

### Post by -Tauren- on 2008-10-01
i like the head parking settings in vista (parks are set just right), is there anyway to mimic these in ubuntu? how can i do that? cheers

---

### Post by gin_ger_ale on 2008-10-02
Below is the Load_Cycle_count output. 
193 Load_Cycle_Count        0x001a   001   001   000    Old_age   Always       -       295079

The load cycle count after an hr is as below.

193 Load_Cycle_Count        0x001a   001   001   000    Old_age   Always       -       295177

It seems to increase by about a 100. My laptop is 8 month old. I have been using it more or less for about 10-12 hrs a day. Do I have to implement the fix? If I do will it increase the temperature? Please suggest.

---

### Post by frodon on 2008-10-03
Yes implement the fix in hurry, about the temperature most drive are guaranteed till 60C° so the temperature will surely increase but it will be several degrees and you should be still far from the 60C° limit.

---

### Post by gin_ger_ale on 2008-10-04
Thanks Frodon and Ubuntu_Demon. I implemented the ugly fix for Hardy. The temperature increased to 51C. I already use a cooling pad for my laptop. Also, I read in a thread that for Seagate harddrives the operating temperature is much higher.

The load cycle count is now constant(on ac).
 sudo smartctl -a /dev/sda | grep Load_Cycle_Count
193 Load_Cycle_Count        0x001a   001   001   000    Old_age   Always       -       295530

I have not checked on battery. Should I experiment and change the values in the ugly fix or they would work fine? Please suggest if a someone not using Ubuntu rarely but having dual boot should also implement this fix.

---

### Post by frodon on 2008-10-04
For the setting on battery you can try a less drastic setting. In most documentations i have read on the topic a 30 head parking per hour ratio is considered as something common for a laptop on battery.

For example i have been unable to set less drastic setting on battery on my laptop, my heads almost never park and i live perfectly fine with it. My drive has never gone over 54C° even after several hours of gaming.

In your case, considering the high load cycle count you already have, i would advice you to keep a drastic setting even on battery, you are near a 300000 head parking count so better now to not increase your head parking count too much.

---

### Post by darkstaar on 2008-10-05
> **frodon said:**
> In your case, considering the high load cycle count you already have... you are near a 300000 head parking count so better now to not increase your head parking count too much.

Hmmm...I don't think I'd be too concerned about a 300000 count.

Here's what mine looks like:

> 
193 Load_Cycle_Count  0x0032  040  040  000  Old_age  Always   -   608016


...and all is well. BTW, it seems to have been incrementing accurately (one cycle per parking).

The drive is barely 11 months old and has only had Linux on it. This is also the third drive in this laptop. Apparently I'll be ready for a fourth soon as this one seems to be running on borrowed time.

--Leisa

---

### Post by frodon on 2008-10-06
It depends, some laptop drives are guaranteed for a 300000 maximum head parking count only which don't mean of course than you can't go further.

Anyway some hdd firmware default config are definitely not sane, i truely hope this message will be heard by drive makers but this is not sure because the problem has been reported for long now.

---

### Post by darkstaar on 2008-10-06
> **frodon said:**
> i truely hope this message will be heard by drive makers but this is not sure because the problem has been reported for long now.

Probably won't happen before flash drive technology becomes inexpensive enough to replace these things.

---

### Post by shrndegruv on 2008-10-07
is there a way to increase the interval at which ext3 journals?  instead of every five seconds maybe once every 120 seconds?

i installed my system with an encrypted lvm.  the fstab looks like

```

# /dev/mapper/group1-root
UUID=a0101307-9332-4aed-a74c-27a1a5144b0f /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda1
UUID=42c36bbf-aa35-4eed-b2d5-1a10a32ef367 /boot           ext3    relatime        0       2
# /dev/mapper/group1-home
UUID=c4386ab9-e13f-4743-9786-8ec85fdaf74e /home           ext3    relatime        0       2


```

I am trying to decrease the rate at which LCC increases without messing with hdparm....thanx

---

### Post by david_e on 2008-10-08
I think that you can do it by mounting with the option "commit=120" (add it to your fstab).

---

### Post by shrndegruv on 2008-10-08
are you sure?  I dont want to make a huge mistake and have to reinstall --- i cant find the damn config options for ext3 anywhere; man fstab isn't too informative.

---

### Post by david_e on 2008-10-08
You can see all the ext3 mount options in "man mount". I am sure that commit=120 will set the right option, but I don't know if this can have some bad side-effects, apart from the obvious problem that you will lose much more data in case of a power failure.

---

### Post by gin_ger_ale on 2008-10-08
> **frodon said:**
> It depends, some laptop drives are guaranteed for a 300000 maximum head parking count only which don't mean of course than you can't go further.

Anyway some hdd firmware default config are definitely not sane, i truely hope this message will be heard by drive makers but this is not sure because the problem has been reported for long now.

My laptop's harddrive is a Seagate Momentus 5400.3 (ST9160821AS). According to the specs the maximum count is >600000. I applied the fix but the count jumps by 50 when the laptop is resumed from the suspend mode. When I disabled advanced power management using hdparm the count seemed to remain constant. In the ugly fix I set the value to 255. Earlier it was set to 254. So I presume it will be alrite. 
PS: The count is now at 296772.

---

### Post by subash_patel on 2008-10-09
Hello, 

thank you for helping fix my laptop load_cycle issue. Now I see the following:
$hdparam -B 200 /dev/sda
$ date; sudo smartctl -a /dev/sda | grep -i -E '(load_cycle|temp)'Thu Oct  9 11:10:21 EDT 2008
sudo: unable to resolve host SRP-Laptop
193 Load_Cycle_Count        0x0032   099   099   000    Old_age   Always       -       17293
194 Temperature_Celsius     0x0022   100   100   000    Old_age   Always       -       54 (Lifetime Min/Max 21/55)

Although the Load_Cycle hasnt increased for sometime now, Is it SAFE to run the hard drives at such high temperatures? Is it going to affect the hard drive hardware in any ways?

Thanks,
Subash

---

### Post by Gausian on 2008-10-14
So is this bug fixed in Interpid?  According to this link it will be...

[http://ubuntuforums.org/showthread.php?p=5930536]("http://ubuntuforums.org/showthread.php?p=5930536")

---

### Post by shrndegruv on 2008-10-15
i think i have the issue under control by setting the ext3 time to commit every 30 seconds.  I also mount my ext3 partitions with the noatime option; I don't know if this is helping the count issue but my machine sure boots faster.  

Ive gone from about 10 increases a minute to less than 1 a minute with the machine plugged in.  havent tested it unplugged yet.

---

### Post by ngine13 on 2008-10-23
Guys i have a problem...

i own an acer 5920G laptop. 

When i boot i disable apm for my /dev/sda using :

hdparm -B 255 /dev/sda

With this commant Load_Cycle_Count stops increasing!

When i suspent it and then resume my Load_Cycle_Count is increasing..

My system is ubuntu 8.10 beta upgraded from 8.04.. and is running on ac!

In my /etc/acpi directories (suspent, resume...) there is the following script

90-hdparm.sh :

#! /bin/sh
#
# This script adjusts hard drive APM settings using hdparm. The hardware
# defaults (usually hdparm -B 128) cause excessive head load/unload cycles
# on many modern hard drives. We therefore set hdparm -B 254 while on AC
# power. On battery we set hdparm -B 128, because the head parking is
# very useful for shock protection.
#

. /usr/share/acpi-support/power-funcs

DO_HDPARM=y
if [ -e /usr/sbin/laptop_mode ] ; then 
  LMT_CONTROL_HD_POWERMGMT=$(. /etc/laptop-mode/laptop-mode.conf && echo "$CONTROL_HD_POWERMGMT")
  if [ "$LMT_CONTROL_HD_POWERMGMT" != 0 ] ; then
    # Laptop mode controls hdparm -B settings, we don't.
    DO_HDPARM=n
  fi
fi

if [ $DO_HDPARM = y ] ; then
  # Get the power state into STATE
  getState;
  
  for dev in /dev/sd? /dev/hd? ; do
    if [ -b $dev ] ; then
      # Check for APM support; discard errors since not all drives
      # support HDIO_GET_IDENTITY (-i).    
      if hdparm -i $dev 2> /dev/null | grep -q 'AdvancedPM=yes' ; then
	if [ $STATE = "BATTERY" ] ; then
	  hdparm -B 128 $dev
	else
	  hdparm -B 254 $dev
	fi
      fi
    fi
  done
fi


If anyone knows something.. please help me. :)

---

### Post by frodon on 2008-10-24
> **gin_ger_ale said:**
> My laptop's harddrive is a Seagate Momentus 5400.3 (ST9160821AS). According to the specs the maximum count is >600000. I applied the fix but the count jumps by 50 when the laptop is resumed from the suspend mode. When I disabled advanced power management using hdparm the count seemed to remain constant. In the ugly fix I set the value to 255. Earlier it was set to 254. So I presume it will be alrite. 
PS: The count is now at 296772.There's one more script to add to ensure ugly fix is run after resume, it is known to not always work properly after a resume.

> Disk Power Management
From openSUSE

Disk Power Management Configuration

Create a configuration file to management disk power management:

/etc/pm/config.d/disk

    # Configure disk power management settings to ensure both
    # long disk life and good power management.
    #
    # Space delimited list of disk devices this affects.
    #
    DEVICES_DISK_PM_NAMES="/dev/sda"
    #
    #
    # Power management modes
    #
    # Powersave mode off
    #  Disable APM and spin-down
    #
    DEVICES_DISK_PM_POWERSAVE_OFF="hdparm -q -B 255 -q -S 0"
    #
    # Powersave mode on
    # Enable APM to conservative 200 and set spin-down for 21 minutes
    #
    DEVICES_DISK_PM_POWERSAVE_ON="hdparm -q -B 200 -q -S 252"

Note: Your laptop drive can get hot with no power management if you leave your laptop plugged in all the time. You may want to set DEVICES_DISK_PM_POWERSAVE_OFF to a large value, but not disabled completely. If you were going to do this, you might use something like: hdparm -q -B 254 -q -S 242

This means set the least power management, but not off, and spin down the disk after an hour.

Disk Power Management Script

Then create the power management script:

/etc/pm/power.d/disk

    #!/bin/bash
    . /usr/lib/pm-utils/functions
    . /etc/pm/config.d/disk

    if test -z "${DEVICES_DISK_PM_NAMES}"; then
            exit 1
    fi

    case "$1" in
            true)
                    echo "**enabled pm for harddisk"
                    for DISK_NAME in `echo ${DEVICES_DISK_PM_NAMES}`; do
                            ${DEVICES_DISK_PM_POWERSAVE_ON} ${DISK_NAME}
                    done ;;
            false)
                    echo "**disabled pm for harddisk"
                    for DISK_NAME in `echo ${DEVICES_DISK_PM_NAMES}`; do
                            ${DEVICES_DISK_PM_POWERSAVE_OFF} ${DISK_NAME}
                    done ;;
    esac

Make the script executable.

chmod +x /etc/pm/power.d/disk

Test the script

You can then test the set up by using the following commands:

pm-powersave true
hdparm -I /dev/sda | grep 'Advanced Power'

An asterisk next to 'Advanced Power Management feature set' means its enabled. Now try this:

pm-powersave false
hdparm -I /dev/sda | grep 'Advanced Power'

No asterisk means it's disabled.

These settings are immediately accessible to kpowersave or gnome-power-manager and are used by default when plugging in your power adapter or removing it on a laptop.
If you want the script to be resume proof :
Suspend/Resume handling Script adopted based on Redhat Bugzilla Link:

disksr --> the script is created with a slight modification to adapt the one like suse script for handling suspend/resume and named disksr (sr stands for suspend resume), to be copied into /etc/pm/sleep.d/

create a file called disksr with the following contents

    #!/bin/bash
    . /usr/lib/pm-utils/functions
    . /etc/pm/config.d/disk


    if test -z ${DEVICES_DISK_PM_NAMES}; then
            exit 1
    fi

    case "$1" in
            hibernate|suspend)
                    echo "**enabled pm for harddisk"
                    for DISK_NAME in `echo ${DEVICES_DISK_PM_NAMES}`; do
                            ${DEVICES_DISK_PM_POWERSAVE_ON} ${DISK_NAME}
                    done ;;
            thaw|resume)
                    echo "**disabled pm for harddisk"
                    for DISK_NAME in `echo ${DEVICES_DISK_PM_NAMES}`; do
                            ${DEVICES_DISK_PM_POWERSAVE_OFF} ${DISK_NAME}
                    done ;;
    esac

give the file executable permission, chmod +x disksr from the folder where the script is saved. Copy the script to /etc/pm/sleep.d/ using the following command


sudo cp disksr /etc/pm/sleep.d/
sudo chmod +x /etc/pm/sleep.d/disksr

The second part is about creating a script to relaunch the ugly fix automatically after resume.

---

### Post by www.rzr.online.fr on 2008-10-29
Just wanted to tell that I was afected by this issue on this hardisk (using debian)  :
IC25N020ATCS04 

-- 
[http://rzr.online.fr/q/hitachi](http://rzr.online.fr/q/hitachi)

---

### Post by erythrocyte on 2008-11-02
i'm promoting an idea on ubuntu's brainstorm related to this issue. would appreciate all your votes! thanks!

[[IMG]http://brainstorm.ubuntu.com/idea/15153/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/15153/)

---

### Post by shrndegruv on 2008-11-03
after updating to intrepid this issue is back for me.  all i originally did was change my ext3 commit times to 30 seconds.  On AC i had minimal increases.  with intrepid i get about 10/minute.  is there going to be a new guide for this issue for intrepid?

---

### Post by KuBala on 2008-11-03
With these hdparm related tricks you guys threat the symptoms only: like when you use painkiller the reason of the pain still persists. The real problem is something(s) always polls the HDD so that it "wakes up".
Is there a topic dealing with efforts to stop these unnecessary disk accesses?
(ThaRabbit also mentioned this earlier)

(now l am trying without swap partition, but it does not help)

When I use -B 254 there are no clicks.
When I use -B 128 (this is the default l guess) there are clicks, about 5/min.
I tried to use -B 12 there are also spindowns, and spinups immediately.

I think if we want lower power consumption, thus lesser heat and longer battery life we need also spindown. If we got only parking of the heads (clicks), that would not spare a lot of energy (the disk is still spinning, and l assume that consumes the most energy), however it certainly does against the effects of the "bumps".

Toshiba A300 equipped with sata 2 1/2" WDC WD2500BEVS-26UST0.
Ubuntu 8.10

Best regards.

---

### Post by bigbrovar on 2008-11-04
I was during a research to see if my laptop a dell xps m1330 (which came preinstalled with Ubuntu) was affected by the laptop harddrive Load_Cycle_Count issue i ran 2 test in 15 minute following the guide here [http://ubuntuforums.org/showthread.php?t=795327](http://ubuntuforums.org/showthread.php?t=795327) and the result was really disturbing .

when i ran the first test i got this result

190 Temperature_Celsius 0x0022 062 054 045 Old_age Always - 639303718
193 Load_Cycle_Count 0x0032 090 090 000 Old_age Always - 20939
194 Temperature_Celsius 0x0022 038 046 000 Old_age Always - 38 (Lifetime Min/Max 0/23)


15 minute later when i ran the same test

190 Temperature_Celsius 0x0022 062 054 045 Old_age Always - 639303718
193 Load_Cycle_Count 0x0032 090 090 000 Old_age Always - 20967
194 Temperature_Celsius 0x0022 038 046 000 Old_age Always - 38 (Lifetime Min/Max 0/23)


from this result my load cycle count number listed in this commands output changed by 28 meaning my load cycle count increases by 28 every fifteen minute. from the look of things its really scary and i want to ask if anyone has the same problem should i apply the patch

my hard disk is 320gb in size and made by samsung the speed is 7200 RPM and it comes with freefall sensor. point is i am afraid and i dont know if i should apply thge patch becasue i dont want to do anything that would hurt the the harddrive does anyone have the same problem?

---

### Post by nokatus on 2008-11-05
Thanks, everyone, for an informative read! Just quickly chiming in here (first post, yay, although signed in a long while ago).

> **ubuntu_demon said:**
> Even if the laptop is used on battery everyday for four hours the Load_Cycle_Count would have to increase with 137 per hour to be able to reach 600.000 within three years of usage. Most people don't see their Load_Cycle_Count increase that fast (although some might)

I installed Intrepid on an oldie-but-goodie IBM Thinkpad T40, and the issue seems more prominent than ever. After a while of inactivity, even on AC power, the HD (Hitachi HTS541060G9AT00) goes into a non-stop sequence of successive loads/unloads which doesn't seem to stop even after resuming work.

I'm not seeing 100-150 per hour; it's hitting that neighbourhood in mere minutes. It literally loads and unloads all the time, every three-four seconds. Checking it on smartctl verifies this, the count rises before my eyes at a steady rate. For sure, this can be a nasty surprise for someone who has just installed a new OS and doesn't know about the issue.

At the moment I have to get some work done and I don't have time to troubleshoot this any more than I absolutely have to :( ... Dual booting into Windows XP, the HD functions as expected, and in Linux the *hdparm -B 254* fix works. That will have to do for now (thanks!)

---

### Post by shrndegruv on 2008-11-05
someone clearly need to reopen this issue.  The bug is not fixed.

---

### Post by frodon on 2008-11-05
This is the purpose of the ugly fix to fix this :)

---

### Post by shrndegruv on 2008-11-05
will the hardy instructions work for intrepid?

---

### Post by erythrocyte on 2008-11-06
> **shrndegruv said:**
> someone clearly need to reopen this issue.  The bug is not fixed.

then vote for:-

[[IMG]http://brainstorm.ubuntu.com/idea/15153/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/15153/)

and thanks!

---

### Post by erythrocyte on 2008-11-06
Mark Shuttleworth responded to a question from somebody who obviously was aware of this problem and brainstorm idea 15153 on the #ubuntu-classroom IRC channel on Freenode today. [jcastro aka Jorge Castro was moderator. sabdfl is aka Shuttleworth]

[[IMG]http://brainstorm.ubuntu.com/idea/15153/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/15153/)

Pasting the transcript here for commentators:

-- 
15:39 jcastro QUESTION: Does Canonical ever make "Official Policy Announcements" on contentious issues? Two recent controversies were the hard drive wear issue and the issue with the Intel network cards being bricked. Are there official guidelines on what should be done when Ubuntu can possibly damage hardware?
15:40 sabdfl yes, we have a process for handling emergencies and screwups
15:40 sabdfl including making sure that we communicate clearly about what the situation is
15:40 sabdfl unfortunately we have that because there have been emergencies, and we have in the past occasionally screwed up
15:40 sabdfl but i think the policies are good
15:41 sabdfl i don't think such an issue is contentious - if we make a mistake, we need to sort it out, and keep people briefed
-- 

I think we should be pretty optimistic about hearing an official statement soon! wuhoo! :)



PS: couple of other hardware compatibility questions were relevant too such as:

-- 
16:25 jcastro QUESTION: The hardware database mentioned earlier seems limited to certifying whole machines. It seems like it would be more useful for most of us if we had a listing of individual hardware products that were known to work (or not work), particularly video and wireless cards...
16:25 jcastro QUESTION: .. Yet few wireless vendors would see the point in submitting their hardware for certification unless there were already a database to be added to. Is there a plan to get that sort of certification?
16:25 sabdfl i think jcastro pointed to the hardware database earlier
16:26 sabdfl we try to aggregate the information folks send us about their hardware
16:26 sabdfl it's difficult to do component-level certification
16:26 sabdfl because often, something breaks at the system level
16:26 sabdfl we do work with component manufacturers, though, if there is a machine that needs to be enabled
-- 

I had missed the earlier questions, so asked this crucial question just in case:

-- 
6:55 jcastro QUESTION: how robust is the laptop certification process between Canonical and its partners? should customers expect 0% system breakage (in terms of hardware or software)?
16:56 sabdfl they should expect it, and we strive to deliver it
16:56 sabdfl see above for how we handle emergencies and screwups :-)
-- 

cheers everybody! #ubuntu-classroom is a great place to hang out! :D

---

### Post by Alfred_McGee on 2008-11-07
No, this bug definitely has not been fixed in Ibex. On my Acer, the load cycle count actually seems to increase more quickly than it did under Hardy. The fix at the beginning of this thread works in Ibex, but stops working after a suspend, just as it did in Hardy. Then I have to switch my laptop from battery to AC or vice-versa to get the load cycle count to stop skyrocketing. BTW, I set hdparm to 255 for both battery and AC because I handle my machine carefully and don't like to worry about whether or not it's plugged in.

---

### Post by minisori on 2008-11-07
> **Alfred_McGee said:**
> No, this bug definitely has not been fixed in Ibex. On my Acer, the load cycle count actually seems to increase more quickly than it did under Hardy. The fix at the beginning of this thread works in Ibex, but stops working after a suspend, just as it did in Hardy. Then I have to switch my laptop from battery to AC or vice-versa to get the load cycle count to stop skyrocketing. BTW, I set hdparm to 255 for both battery and AC because I handle my machine carefully and don't like to worry about whether or not it's plugged in.

Yes, i supposse a western digital hd like mine where all values from, 2 to 253, to park the drive give the same result, (crappy hd firmwares...).

Just enable laptop mode and change the value 128 to 254 or sudo hdparm -B 254 /dev/sda, but your drive will never park. Also i have noticed, that a value of 1 combined with laptop mode works good since most of the time there is no need to read from hd, so it's parked most of the time.

---

### Post by futuroimperfetto on 2008-11-09
Hello,

I have a Dell XPS m1330 with Hardy Heron which is a little less than 3 months old and has already a staggering 92897 as a Load_Cycle_Count (notice: I bought it with Gutsy preinstalled).

I had another laptop before and the hard drive failed due to this issue (I was using Ubuntu 6.10, 7.04 and 7.10 on that one). When I bought this new laptop and put Hardy on it, a friend of mine pointed me to the the third post of ubuntu_demon

[http://ubuntuforums.org/showpost.php?p=5031047&postcount=3]("http://ubuntuforums.org/showpost.php?p=5031047&postcount=3")

and the ugly fix for Hardy at this link

[http://en.opensuse.org/Disk_Power_Management]("http://en.opensuse.org/Disk_Power_Management")

What happened is that yesterday I checked the Load_Cycle_Count and it was extremely high. I got very scared, as I have already lost one hard drive similarly.

I am a newbie and maybe I did not do something correctly: I created the two files suggested in the second link. Each time I turn my computer on I'm on PM_POWERSAVE_ON and my hard drive parks its heads 144 times per hour...

I decided to go on POWERSAVE_OFF and remove the fix, but I'm not sure this makes any sense. I am 99% of the times on AC power and don't know what to do. Right now the heads are not parking at all (at least I'm not raising the count).

Can anyone help me as to what I should do (to make them park a reasonable amount of time on battery and maybe never on AC power)? I obviously did something wrong, but don't know how to navigate in the sea of posts on the topic.

Also, does anyone know how "old" my hard drive is now?

Thanks

---

### Post by AndrewZorn on 2008-11-10
This is still not fixed in Intrepid.  This is ******* ridiculous.

---

### Post by Hated On Mostly on 2008-11-12
The best fix was posted by jakon in the old thread.

[http://ubuntuforums.org/showpost.php?p=4897802&postcount=842](http://ubuntuforums.org/showpost.php?p=4897802&postcount=842)

It works in v8.04 (Hardy Heron) and v8.10 (Intrepid Ibex).

It is easy to do and easy to remove.

It should be added to the first post as one of the solutions (non-ugly).

The ugly solution is a big mess compared to the one jakon posted.

--------
> 
AbtZ, the guide of ubuntu_demon doesn't work anymore on Hardy.

The "normal" way to set your hd power management setting is through /etc/hdparm.conf. Unfortunately, because of [https://bugs.launchpad.net/ubuntu/+source/hdparm/+bug/199094](https://bugs.launchpad.net/ubuntu/+source/hdparm/+bug/199094) , these settings will be lost upon suspend/resume. But, i have posted a patch there that should fix this issue.

You could test the patch, stop the klicking, help fix bug 199094 by:

1.

```
sudo gedit /etc/hdparm.conf
```

Add

```

/dev/sda {
apm = 254
}
```

to the end of the file.

2. Save [http://launchpadlibrarian.net/14195287/30hdparm](http://launchpadlibrarian.net/14195287/30hdparm) to /tmp/30hdparm . Then,


```
sudo install /tmp/30hdparm /etc/pm/sleep.d/
```

(Note: /usr/lib/pm-utils/sleep.d/ also works, but /etc/ is the cleaner solution)

3. Suspend/Resume or reboot to make it take effect.

4. Report back here.

That's it. You can undo it by deleting /usr/lib/pm-utils/sleep.d/30hdparm . Don't forget that this makes your hd more vulnerable to bumps.

---

### Post by maxiemillion on 2008-11-12
I've been watching this for a long time. I concur Intrepid didn't fix it.
Had I left my HD as is I would be approaching my disks published limits.
I now just run [COLOR=#000000][FONT=DejaVu Sans]sudo hdparm -B 249 /dev/sda after a reboot/login. If I remember. The clicks quickly remind me anyway.
I hope this is an acceptable fix. I tried all the fixes here but they broke somehow.
[/FONT][/COLOR]
HP DV9000 (dv9000tx)


 I installed ubuntu immediately on reciept of this notebook.
As you can see, after just two weeks or so my HDD was at almost 86,000 clicks.

stats: from 2-3 weeks old.
(From my Knotes:)
*date, time, [COLOR=Red]**click count**[/COLOR], HD temp, Ambient temp, [COLOR=DarkGreen]**clicks since last check**[/COLOR].*
_***First entry:***_
nov29 2007        8:17pm [COLOR=Red]**    85996**[/COLOR]         50deg                         1.5hrs batt. hib overnight.

Added Ugly fix.

nov30         9:15pm        **[COLOR=Red]86080[/COLOR]**        47deg [COLOR=DarkGreen]**                84**[/COLOR]
dec2        1:13pm     **[COLOR=Red]86135[/COLOR]**        48deg [COLOR=DarkGreen]**                55**[/COLOR]
dec3        2:12pm        **[COLOR=Red]86144[/COLOR]**        49deg [COLOR=DarkGreen]**               09**[/COLOR]
dec5        6:46pm        **[COLOR=Red]86206[/COLOR]**        50deg [COLOR=DarkGreen]**               52**[/COLOR]
dec9        3:18pm        **[COLOR=Red]86309[/COLOR]**        56deg  (34amb)    103         up:2d5h47m
dec16        12:53pm [COLOR=Red]**   86389**[/COLOR]        49deg [COLOR=DarkGreen]**               80**[/COLOR]

2008

jan1        6:49pm [COLOR=Red]**       86962**[/COLOR]        44deg [COLOR=DarkGreen]**               572**[/COLOR]
mar 7        12.12am [COLOR=Red]**   88412**[/COLOR]        67deg [COLOR=DarkGreen]**               1550**[/COLOR]
june 7         8:17pm [COLOR=Red]**       92175**[/COLOR]          42deg    16 [COLOR=DarkGreen]**           3747**[/COLOR]
aug 15        1am [COLOR=Red]**       97981**[/COLOR]        44deg [COLOR=DarkGreen]**               5806**[/COLOR]
sep 2        9pm [COLOR=Red]**       123221**[/COLOR]        39deg    14 [COLOR=DarkGreen]**           5240    **[/COLOR]

Fix not working anymore!
Added fix to ac.d battery.d. Removed from suspend.d
sudo smartctl -a /dev/sda | grep Load_Cycle_Count

sep2        9:20 **[COLOR=Red]       123259[/COLOR]**        45deg[COLOR=DarkOliveGreen] **               38**[/COLOR]
sep27        12pm [COLOR=Red]**       160018**[/COLOR]        50deg [COLOR=DarkGreen]**               37241**[/COLOR]
oct3        1:21pm [COLOR=Red]**       167752**[/COLOR]        50deg    amb35 [COLOR=DarkGreen]**       7734**[/COLOR]


[COLOR=RoyalBlue][I]NEW 8.1 INSTALL INTREPID
[/I][/COLOR]
oct27    2:30 [COLOR=Red]**       180749**[/COLOR]        40[COLOR=DarkGreen] **                   12997**[/COLOR]
nov3    21:38 [COLOR=Red]**       193294**[/COLOR]        46[COLOR=DarkGreen]**                   13653**[/COLOR]

Now Doing manual  sudo hdparm -B 249 /dev/sda after each reboot. If remembered.

nov12    11:23 **[COLOR=Red]       199116[/COLOR]**        55    23deg [B][COLOR=DarkGreen]            5822
[/COLOR][/B]  [COLOR=#000000][FONT=DejaVu Sans]nov13 12:04pm    **[COLOR=Red]199116[/COLOR]**        55    28deg            [COLOR=DarkGreen]**0**[/COLOR][/FONT][/COLOR]

---

### Post by frodon on 2008-11-13
> **maxiemillion said:**
> Now Doing manual  sudo hdparm -B 249 /dev/sda after each reboot. If remembered.What about adding it to hdparm.conf for good so that you don't have to bother with it anymore ?

---

### Post by mjones41 on 2008-11-15
I am using a Fujitsu Esprimo U9200 running Ubuntu Intrepid 8.10.  The laptop is less than 6 months old and I have 203143 cycles already.  I was pretty surprised.  

Did the manual fix, it worked, then did the permanent ugly fix, very glad I did, the cycles have come way way down, and the temperature is not too high, under 40 degrees most of the time.

I did the fix from here;
[http://ubuntudemon.wordpress.com/2007/10/26/laptop-hardrive-killer-bug/#comment-31234](http://ubuntudemon.wordpress.com/2007/10/26/laptop-hardrive-killer-bug/#comment-31234)

Used their values and am now happy, and can relax.  I really want to vote for Ubuntu fixing this issue without people having to go to the command line.  I realise it is not a Ubuntu problem, but Ubuntu needs to help out. Just not sure where to vote?

---

### Post by DublinDude on 2008-11-20
I have a Lenovo 3000 n200 laptop, which recently suffered a hard disk failure after only 11 months and required a replacement disk. 
Upon hearing about this issue for the first time last week, I downloaded smartmontools in Xubuntu and checked my new disk's load_cycle_count SMART attribute, which had reached 22500 after six weeks, or 535 increments per day on average. At that rate the disk will likely fail in just under three years time if the manufacturers MTBF statistics are accurate. Does this seem rather high? 


I reluctantly took Xubuntu off my laptop and put XP back on it, as none of the fixes, ugly or otherwise, would work. I could still hear the click sound every 20-30 seconds or so during normal operation, and I had written a Bash script to keep polling the load_cycle_count attribute every minute, and I could see it increasing by between 1-3 after each iteration. Under XP I never really hear the pop, but am wondering if I am overreacting and can put Xubuntu back on my laptop :)

---

### Post by frodon on 2008-11-20
Your polling script is increasing your load cycle count even faster as it will unpark head each time if they are parked.

Just implement the ugly fix and your load cycle count will be under control in ubuntu.

---

### Post by quanumphaze on 2008-11-21
About the suspend/resume fix.

> **frodon said:**
> If you want the script to be resume proof :
Suspend/Resume handling Script adopted based on Redhat Bugzilla Link:

disksr --> the script is created with a slight modification to adapt the one like suse script for handling suspend/resume and named disksr (sr stands for suspend resume), to be copied into /etc/pm/sleep.d/

create a file called disksr with the following contents

```
#!/bin/bash
. /usr/lib/pm-utils/functions
. /etc/pm/config.d/disk


if test -z ${DEVICES_DISK_PM_NAMES}; then
exit 1
fi

case "$1" in
hibernate|suspend)
echo "**enabled pm for harddisk"
for DISK_NAME in `echo ${DEVICES_DISK_PM_NAMES}`; do
${DEVICES_DISK_PM_POWERSAVE_ON} ${DISK_NAME}
done ;;
thaw|resume)
echo "**disabled pm for harddisk"
for DISK_NAME in `echo ${DEVICES_DISK_PM_NAMES}`; do
${DEVICES_DISK_PM_POWERSAVE_OFF} ${DISK_NAME}
done ;;
esac
```

give the file executable permission, chmod +x disksr from the folder where the script is saved. Copy the script to /etc/pm/sleep.d/ using the following command


sudo cp disksr /etc/pm/sleep.d/
sudo chmod +x /etc/pm/sleep.d/disksr 

I'm no scripting expert but the missing left '(' is a little disturbing. I just want to make sure that is correct before I make this executable.

---

### Post by erythrocyte on 2008-11-21
I just noticed that as of 21 November 2008 1239 UTC, the status of this bug is no longer "Fixed Released" and it has been changed to "In Progress" on its tracker at Launchpad.

---

### Post by norreman on 2008-11-23
I have also a Fujitsu Siemens Esprimo U9200 with the same problem. I noticed that it's ticking when it's idle. I applied the ugly fix and played a little with the numbers. It turned out that "hdparm -S xxx" had no effect on the spin down time at all. So I just use now "hdparm -B 254".

My machine is 1 week old with 2964 cycles.

---

### Post by quanumphaze on 2008-11-23
I took the dive and chmoded the suspend/resume fix and it seems to work fine.

I would also like to point out that this problem seems to also effect external USB hard drives of the 'pocket' variety. Unfortunately hdparm can't talk to the drive though USB.

---

### Post by Crow550 on 2008-11-24
On an HP DV5000 when the laptop is idling the hard drive light stays on. I don't know what it's doing. In XP it doesn't do this and will go off when idle. In Ubuntu 8.10 when a program is loaded it will go off for a little but then when idle it will stay on. Even if Ubuntu just starts up and not even logged in, it will do it.

Is this something to worry about or what? Battery seems to last about the same as it usually does. Two hours.

---

### Post by Crow550 on 2008-11-24
Problem fixed.... Laptop mode wasn't enabled. I just opened the terminal and typed sudo /etc/default/acpi-support then went to search and laptop and found ENABLE_LAPTOP_MODE and set it from false to true. I figured this out after doing some research and decided to check if it was on.

I don't know why Ubuntu didn't figure out it was a laptop in the first place. I also heard when installing Ubuntu to go into other options and select laptop mode? Why can't it detect a laptop or ask you if your installing it on a desktop or laptop?

---

### Post by Zetheroo on 2008-11-24
> **Crow550 said:**
> Problem fixed.... Laptop mode wasn't enabled. I just opened the terminal and typed sudo /etc/default/acpi-support then went to search and laptop and found ENABLE_LAPTOP_MODE and set it from false to true. I figured this out after doing some research and decided to check if it was on.

I don't know why Ubuntu didn't figure out it was a laptop in the first place. I also heard when installing Ubuntu to go into other options and select laptop mode? Why can't it detect a laptop or ask you if your installing it on a desktop or laptop?

Is that really safe to do? This is what is says above that option:

```
# Switch to laptop-mode on battery power - off by default as it causes odd
# hangs on some machines.  (Note: This is reported to cause breakage in
# Debian - see deb bug #425800.  Leaving enabled for Ubuntu for now
# since presumably it's still valid here.)
```

Please let us know if enabling this option causes any strange things to happen on your machine.
Thanks

---

### Post by frodon on 2008-11-24
The laptop_mode fix is a known one with known drawbacks, a forum search should tell you all on the topic.

---

### Post by edingc on 2008-11-24
I have an Acer 5570z laptop running Hardy that had a new hard drive installed this past January. After finally getting around to checking my Load_Cycle_Count this past weekend, it has amassed 216,000 cycles in less than 11 months! 

I applied the ugly fix and it has only added about 20 cycles in the last 5 days. When I was checking before the fix, it was doing about 20 cycles every 5 minutes.

---

### Post by Crow550 on 2008-11-24
Well I threw Ubuntu on my friends laptop and in a few days he wants to pick it up, since i'm pretty much done with it. I noticed the hard drive light was staying on when idle. I figured it might be this hard drive problem and don't want his laptops drive to burn out. So I kept hearing about a laptop mode and figured it might be off. So I turned it on and so far everything seems to be working just fine. The hard drive light isn't staying on when idle and everything still works and loads fine while plugged in. I Plan to do another battery test and see how mucher longer it lasts, compared to the two hours before. This is using Ubuntu 8.10 on a HP DV5000 laptop. With the AMD cpu. The only other issues are the Ati Compiz one with flickering of like Google Earth and screen savers while visuals are turned on normal or high and Yahoo games doesn't seem to work in Firefox but fine in Opera. So two kinks that need to be worked out. I'll update with the battery life later.

---

### Post by Zetheroo on 2008-11-24
> **frodon said:**
> The laptop_mode fix is a known one with known drawbacks, a forum search should tell you all on the topic.

Do you know of any good documentation on that?

---

### Post by Crow550 on 2008-11-24
Battery seemed to last around 2 hours and 30 minutes.

---

### Post by ngine13 on 2008-11-25
Guys i think i solved it..

What i did ?

first :

cd /usr/lib/pm-utils/sleep.d/

then :

sudo nano 30hdparm

#!/bin/bash

hdparm -B 255 /dev/sda

i wrote the above and saved the file

then i made the file executable :

sudo chmod +x 30hdparm

and then i tested it and it works for both suspend and hibernate!

:)

---

### Post by frodon on 2008-11-25
Congrats your head never park ;)

Real risk to damage your disk including when laptop powered off. Change your 255 setting to 254 it's way saffer.

Please everyone just stand with the ugly fix given by ubuntu_demon on post #3, don't try to reinvent the wheel putting in place even more dangerous settings for your hard drive.

The pm-util fix should work just as expected for everyone with drive who support hdparm -B commands.

---

### Post by Zetheroo on 2008-11-25
[http://pastebin.com/m128b002d]("http://pastebin.com/m128b002d")

Could someone have a look at the above? It is the output of **sudo smartctl -a /dev/sda | more** on my laptop and towards the end there are quite a few stated errors. Any idea what they mean? 

BTW, I have been having system freezes and crashes since upgrading to Intrepid. Very frustrating ... :confused:

---

### Post by Zetheroo on 2008-11-25
I found this ([http://brainstorm.ubuntu.com/idea/288]("http://brainstorm.ubuntu.com/idea/288")) but I can definitely vouch that it is not fixed in Intrepid!

Is there a fix for Intrepid? My cycle count is crazy ...

---

### Post by frodon on 2008-11-26
PM-util fix still works, check that laptop_mode is disabled though.

---

### Post by Zetheroo on 2008-11-26
which is the pm-utils fix?

I have it installed .... is that all I need to do?

---

### Post by frodon on 2008-11-26
> **Zetheroo said:**
> which is the pm-utils fix?

I have it installed .... is that all I need to do?Don't you think one should always read the first posts of a thread before posting in it ?

See post #3

Search feature of the forum here, it never hurts using it :
[http://ubuntuforums.org/search.php](http://ubuntuforums.org/search.php)

---

### Post by cutterjohn on 2008-11-26
I took a look in my laptop-mode.conf and discovered that power management was set to 1 on battery power:
BATT_HD_POWERMGMT=1

The drive was parking and unparking every few seconds on battery, raised my cycle load count by about 30 in the time that it took me to find it before I sudo hdparmed it to 249.

Changed the above to:
BATT_HD_POWERMGMT=249
but have yet to reboot and see if it does the job.

Also haven't tried suspend/resume yet, but the way it was was just unacceptable.  I've had the notebook since friday and have already hit 3230 on the load count, since I'd forgotten about this until yesterday, but was on AC all day which was working well after modding acpi conf and rebooting.

[EDIT]
OK suspend still seemed to work fine, now just to reboot and see if the laptop-mode.conf setting is honored and then to actually read the thread since Intrepid release (or the whole thing plus prior thread) to find the best tradeoff value for the hard drive.

Mine is a WDC WD3200BEVT-22ZCT0, the 5400 RPM SATA II 2.5" drive.
[/EDIT]

[EDIT2]
May have spoken too soon as my cycle load count is still growing noticeably since suspend resume, I'll let it run for a while before reboot and see whats going on here...
[/EDIT2]

---

### Post by Zetheroo on 2008-11-26
> **frodon said:**
> Don't you think one should always read the first posts of a thread before posting in it ?

See post #3

Search feature of the forum here, it never hurts using it :
[http://ubuntuforums.org/search.php](http://ubuntuforums.org/search.php)

Of course I went through the initial posts ... I had read them ages ago as well ... but it seems there is no clear-cut mention of "Here is the pm-utils fix" or anything like it. I don't want to just "try" this or "try" that ... I want to just apply the said fix.

Thanks

---

### Post by juamez. on 2008-12-04
> **frodon said:**
> Congrats your head never park ;)

Real risk to damage your disk including when laptop powered off. Change your 255 setting to 254 it's way saffer.


Back with Hardy my hard disk kept on clicking like crazy, make the load_cycle_count go boom in only a couple of days, even with the setting at 254. So I used it at 255. But now with Intrepid it seems that 254 is just fine, no clicking when doing some casual surfing. This is on a laptop by the way.

---

### Post by Nabanna on 2008-12-05
$ sudo smartctl -H /dev/sda

smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

what does it mean?
Am i affected with this bug (and do i need to apply the fix)??

[Edit : I am using Ubuntu on Seagate 320 GB HDD(ST3320620A)]

---

### Post by psychok9 on 2008-12-05
Acer 5920G 250Gb WD HDD.
Hello, I've tried with laptop-mode, and work. But i don't know if work with AC unplugged (it's always plugged).
The [Daemonubuntu]("http://ubuntudemon.wordpress.com/2007/10/26/laptop-hardrive-killer-bug/#comment-31234") tip/fix, it's better of then [laptop-mode fix]("http://vale.homelinux.net/wordpress/2007/10/24/potential-risk-for-your-nx6325s-harddrive/")?

Please help me,
thank you.

p.s. 254 it's the min value before disable (255), I can use intermediate values, for calculate a correct parking? (30mins for example).
I can't understand how 254 value and this > LM_AC_HD_IDLE_TIMEOUT_SECONDS=600 LM_BATT_HD_IDLE_TIMEOUT_SECONDS=20 NOLM_HD_IDLE_TIMEOUT_SECONDS=600 works together...

Thank you again for your patience and help.

---

### Post by psychok9 on 2008-12-06
This values don't work, it's ignored!:
```
LM_AC_HD_IDLE_TIMEOUT_SECONDS=600 LM_BATT_HD_IDLE_TIMEOUT_SECONDS=20 NOLM_HD_IDLE_TIMEOUT_SECONDS=600 
```

For enable laptop-mode I must set 255 power management?

---

### Post by Nico-dk on 2008-12-16
Interesting read, even if I did get information overload halfway through this thread.

Yes, I'm definitely suffering from LCC issue as well.
HDD: **WD1600BJKT**. A look at the western digital site didn't yield any FW upgrades (one could always hope).

I've been manually monitoring my LCC for the past 2 hours:
```
Time  - Count
20:37 - 1299
21:11 - 1331
21:40 - 1382
22:04 - 1417
22:38 - 1476
```
That's 177 click in 2 hours (or just about 88 an hour).

```
sudo smartctl -a /dev/sda:

9 Power_On_Hours - 23
Load_Cycle_Count - 1527

```
This equals ca. 66

The actual count is probably somewhere in between, so I definitely need to apply the Hardy fix.

Since I'm a newbie, I'd like to confirm this "recipe".

1) Experiment with values
```
sudo hdparm -B 128 /dev/sda
```

2)Apply findings to [this guide](http://en.opensuse.org/Disk_Power_Management)

3) Continously watch LCC and HDD temp (w/o using hddtemp)
Maybe creating a shellscript from this
```
while (true); do date;sudo smartctl -a /dev/sda |grep Load;sleep 600; done
```
Good one Kokopelli

Did I miss anything??

---

### Post by gocin on 2008-12-23
Hi! Itried several workarounds but without success. 

Hers's what worked for me on two systems:

I created a file gedit /etc/init.d/sethdparm.sh

filled the file with the code:

#! /bin/bash
#

hdparm -B 254 /dev/sda

made it executable:

chmod -x sethdparm.sh
chmod 755 sethdparm.sh


Then I edited the file /rc.local:

gedit /etc/rc.local

I added the following line above the line with the exit 0:

/etc/init.d/sethdparm.sh


And it just works :-)

---

### Post by kamiokande on 2009-01-18
A relevant article on Slashdot:

[http://it.slashdot.org/article.pl?sid=09/01/17/2127254](http://it.slashdot.org/article.pl?sid=09/01/17/2127254)

---

### Post by varaonaid on 2009-01-22
Please bear with me.  I'm trying to understand if I have a problem with my HDD.  Either I don't understand what I'm reading from the output or it's really bad... 

 $ sudo smartctl -a /dev/sda | grep Load_Cycle_Count
225 Load_Cycle_Count        0x0012   001   001   000    Old_age   Always       -       1391707
 $ sudo smartctl -a /dev/sda | more
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF INFORMATION SECTION ===
Device Model:     SAMSUNG HM120JI
Serial Number:    S09GJ10LC64312
Firmware Version: YF100-15
User Capacity:    120,034,123,776 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  ATA/ATAPI-7 T13 1532D revision 0
Local Time is:    Thu Jan 22 11:30:15 2009 EST

==> WARNING: May need -F samsung or -F samsung2 enabled; see manual for details.

SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00)	Offline data collection activity
					was never started.
					Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		 (4631) seconds.
Offline data collection
capabilities: 			 (0x5b) SMART execute Offline immediate.
					Auto Offline data collection on/off supp
ort.
					Suspend Offline collection upon new
					command.
					Offline surface scan supported.
					Self-test supported.
					No Conveyance Self-test supported.
					Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					General Purpose Logging supported.
Short self-test routine 
recommended polling time: 	 (   2) minutes.
Extended self-test routine
recommended polling time: 	 (  77) minutes.
SCT capabilities: 	       (0x003f)	SCT Status supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_
FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   100   051    Pre-fail  Always       -
       0
  3 Spin_Up_Time            0x0007   100   100   025    Pre-fail  Always       -
       2816
  4 Start_Stop_Count        0x0032   098   098   000    Old_age   Always       -
       2262
  5 Reallocated_Sector_Ct   0x0033   253   253   010    Pre-fail  Always       -
       0
  7 Seek_Error_Rate         0x000e   253   253   000    Old_age   Always       -
       0
  8 Seek_Time_Performance   0x0024   253   253   000    Old_age   Offline      -
       0
  9 Power_On_Hours          0x0032   099   099   000    Old_age   Always       -
       784168
 10 Spin_Retry_Count        0x0032   253   253   000    Old_age   Always       -
       0
 12 Power_Cycle_Count       0x0032   099   099   000    Old_age   Always       -
       1382
191 G-Sense_Error_Rate      0x0012   097   097   000    Old_age   Always       -
       36827
192 Power-Off_Retract_Count 0x0012   253   253   000    Old_age   Always       -
       0
194 Temperature_Celsius     0x0022   112   085   000    Old_age   Always       -
       42
195 Hardware_ECC_Recovered  0x001a   100   100   000    Old_age   Always       -
       420941
196 Reallocated_Event_Count 0x0032   253   253   000    Old_age   Always       -
       0
197 Current_Pending_Sector  0x0012   253   253   000    Old_age   Always       -
       0
198 Offline_Uncorrectable   0x0030   253   253   000    Old_age   Offline      -
       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -
       0
200 Multi_Zone_Error_Rate   0x000a   100   100   000    Old_age   Always       -
       0
201 Soft_Read_Error_Rate    0x0012   253   253   000    Old_age   Always       -
       0
223 Load_Retry_Count        0x0012   100   100   000    Old_age   Always       -
       12
225 Load_Cycle_Count        0x0012   001   001   000    Old_age   Always       -
       1391707
255 Unknown_Attribute       0x000a   253   100   000    Old_age   Always       -
       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA
_of_first_error
# 1  Extended offline    Completed without error       00%         3         -
# 2  Short offline       Completed without error       00%         2         -
# 3  Short offline       Completed without error       00%         2         -
# 4  Short offline       Completed without error       00%         1         -
# 5  Short offline       Completed without error       00%         0         -

SMART Selective Self-Test Log Data Structure Revision Number (0) should be 1
SMART Selective self-test log data structure revision number 0
Warning: ATA Specification requires selective self-test log data structure revis
ion number = 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.

Any thoughts?  Am I in trouble?  Should I be looking at replacing my HDD?  Any advice would be really appreciated.

Thanks so much.
Rae

---

### Post by BandD on 2009-01-22
It seems that your smart values are a little strange.  Unless my calculations are wrong smart is reporting that your hard drive been powered on for the equivilent of 89 years.  If your hard drive isn't making any abnormal noises and you haven't noticed sliggish writes, I'd say you are ok.  

Keep an eye on it and see how much it goes up each day.  Also ifyou hear the heads park check the Load Cycle Count.  Wait for the heads to park again and immediately check the vlue.  It may be goping up by more than one vlaue per head park.

It's always good practice to have your data backed-up, regardless if your drive seems healthy or not...none of them last forever.

---

### Post by varaonaid on 2009-01-22
> **BandD said:**
> It seems that your smart values are a little strange.  Unless my calculations are wrong smart is reporting that your hard drive been powered on for the equivilent of 89 years.  If your hard drive isn't making any abnormal noises and you haven't noticed sliggish writes, I'd say you are ok.  

Keep an eye on it and see how much it goes up each day.  Also ifyou hear the heads park check the Load Cycle Count.  Wait for the heads to park again and immediately check the vlue.  It may be goping up by more than one vlaue per head park.

It's always good practice to have your data backed-up, regardless if your drive seems healthy or not...none of them last forever.

Thanks for the reply.  I appreciate it!

From what I've read in the man pages, it seems that my particular brand of hard drive reports power on time in minutes rather than the usual hours.  At least that's what I think it said.  That would make at least a little more sense than the 89 years! ;)

I don't actually hear the drive parking...it's very quiet.  But I am starting to follow the load cycles and also am on the lookout for a good deal on a new drive.  The fact that my load cycle count is well over 2x the 600,000 mark makes me want to be a bit cautious.  At least I've recently backed everything up!

Again, thanks for the reply!

---

### Post by joe74 on 2009-01-23
I have a ThinkPad X40 (Dec 2004 model). I have been checking some SMART scans of similar disks (HITACHI_DK13FA-40B) and I noticed that I am very lucky for mine is still alive.

I tried all options here about this issue and none could make any difference. My disk kept making those clicks every 15-25 minutes when idle. I tried finally one of these fixes (the one that works after suspend/resume), and something seems to get a bit better. The clicks keep on coming, but now is less often (45secs to 2 min). I don't know if this is supposed to be like that. Here are my counts

```
Fri Jan 23 01:11:37 CST 2009
193 Load_Cycle_Count        0x0032   066   066   000  Old_age Always    -  3510951424434
194 Temperature_Celsius     0x0022   100   074   000  Old_age Always    -  37 (Lifetime Min/Max 17/53)

Fri Jan 23 01:27:27 CST 2009
193 Load_Cycle_Count        0x0032   066   066   000  Old_age Always    -  3511186305472
194 Temperature_Celsius     0x0022   100   074   000  Old_age Always    -  36 (Lifetime Min/Max 17/53)

Fri Jan 23 01:34:49 CST 2009
193 Load_Cycle_Count        0x0032   066   066   000  Old_age Always    -  3511236637123
194 Temperature_Celsius     0x0022   100   074   000  Old_age Always    -  35 (Lifetime Min/Max 17/53)

Fri Jan 23 01:38:43 CST 2009
193 Load_Cycle_Count        0x0032   066   066   000  Old_age Always    -  3511337300425
194 Temperature_Celsius     0x0022   100   074   000  Old_age Always    -  36 (Lifetime Min/Max 17/53)
```

As I have read here and in my searchs in google, my disk shoud be dead, but this laptop spent about two years turned-off with winXP, and that was what probably accelerated its dead in first, and inactivity kept it alive then.

These counts in code format are after applying the scripts and codes to fix these issue. As I can calculate, my disk has some months to one year if this fix didn't work.

Hope we find a cure to these irresponsible act of manufacturers.

---

### Post by GrouchoMarx on 2009-01-31
The latest acpi-support update did not fix the Load_Cycle problem when on battery power because "hdparm -B 128" is not a sane default on my system (Thinkpad x200, Seagate ST980817AS, Intrepid). With "hdparm -B 128" the Load_Cycle count was incrementing every 5 seconds. I had to enable laptop-mode in /etc/default/acpi-support, and then change "BATT_HD_POWERMGMT=1" to "BATT_HD_POWERMGMT=220".

Is this the preferred way to change the hdparm power management level?

---

### Post by Hated On Mostly on 2009-02-03
8.04.2 release notes say the currently available fix is incomplete.

[https://wiki.ubuntu.com/HardyReleaseNotes/ChangeSummary/8.04.2](https://wiki.ubuntu.com/HardyReleaseNotes/ChangeSummary/8.04.2)

"set hdparm power management to 254 for all hard drives while on AC, and 128 while on battery (note that suspend/resume still breaks this, and a more complete fix will be forthcoming for Ubuntu 8.04.3"

---

### Post by sergiom99 on 2009-02-03
> **Hated On Mostly said:**
>  and a more complete fix will be forthcoming for Ubuntu 8.04.3"

wooohoooooo!! :popcorn:

---

### Post by GrouchoMarx on 2009-02-03
> **Hated On Mostly said:**
> 8.04.2 release notes say the currently available fix is incomplete.

[https://wiki.ubuntu.com/HardyReleaseNotes/ChangeSummary/8.04.2](https://wiki.ubuntu.com/HardyReleaseNotes/ChangeSummary/8.04.2)

"set hdparm power management to 254 for all hard drives while on AC, and 128 while on battery (note that suspend/resume still breaks this, and a more complete fix will be forthcoming for Ubuntu 8.04.3"


:) I'm on Intrepid (Forgot to change my profile). The problem for me is that setting hdparm power management to 128 on battery power is not a sane default on my system. I think I managed to solve the problem by changing 128 to 200 in the following files (after turning off laptop-mode in /etc/default/acpi-support):

/etc/acpi/start.d/90-hdparms.sh
/etc/acpi/resume.d/90-hdparms.sh
/etc/acpi/battery.d/90-hdparms.sh
/etc/acpi/ac.d/90-hdparms.sh

---

### Post by WannabeFantasma on 2009-02-03
this load cycle thing? is that really really bad? or?
will your laptop still work properly with alot of load cycles?

193 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       421 
p:~$ sudo smartctl -a /dev/sda | grep Load_Cycle_Count 
193 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       456 
:~$ sudo smartctl -a /dev/sda | grep Load_Cycle_Count 
193 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       502 

1HOUR
_______________________________________________________

:~$ sudo smartctl -a /dev/sda | grep Load_Cycle_Count 
193 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       530 
:~$ sudo smartctl -a /dev/sda | grep Load_Cycle_Count 
193 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       569 
:~$ sudo smartctl -a /dev/sda | grep Load_Cycle_Count 
193 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       596 
-laptop:~$ sudo smartctl -a /dev/sda | grep Load_Cycle_Count 
193 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       611 

100 MINUTES


yesterday i had like 310 (on AC)

all this happened with just battery (so i'll never use battery again?)

---

### Post by forcecore on 2009-02-03
i want to know too is that bad, i use my laptop mostly with power adapter but is there easy way to make sure does that affects me ubuntu 8.10???

---

### Post by GrouchoMarx on 2009-02-03
Basically a hard drive is only designed to do a certain number of Load_Cycles in its life-time. For most devices it's 600,000. For some newer drives it's 1,200,000. You need to check the manufacturers specifications for your particular device. Then it's a simple matter of making sure that you get the average number of Load_Cycles per day to such a level that the drive will last four or five years. However you don't necessarily want to completely prevent load cycles while on battery power because they are a useful power saving feature and help reduce the chance of damage to your hard drive when the laptop is in motion.

---

### Post by WannabeFantasma on 2009-02-04
but what if there are more load cycles?
what'll happen than? 
than the harddrive goes slower?

---

### Post by forcecore on 2009-02-04
GrouchoMarx, you say that ubuntu is only affected if using battery and if using power adapter then problem is gone? my laptop running mostly on power adapter.

---

### Post by GrouchoMarx on 2009-02-04
> **WannabeFantasma said:**
> but what if there are more load cycles?
what'll happen than? 
than the harddrive goes slower?

If your Load_Cycle count grows past the hard drive's design spec it doesn't neccesarily mean that your hard drive will break (think mileage for cars; a car may be designed to run 600,000 miles, but that doesn't mean it will break down exactly on the 600,000th mile). For instance the hard drive in my old laptop is well past 600,000 Load_Cycles and it still works (knock on wood). It just means that the hard drive has performed more Load_Cycles than in was "designed" to do. At that point you might consider disabling load cycles completely. Of course hard drives fail for any number of reasons, not just because of excessive Load_Cycles. So eliminating Load_Cycles will not keep a hard drive working forever.

One thing to note is that not all hard drive brands report Load_Cycles the same way. For some strange reason, certain hard drive brands increment the load cycles count by multiples. So although you may see 800,000 load cycles, you might in reality only have had 80,000. You need to monitor your load cycle count and see by what multiple it increments.

> GrouchoMarx, you say that ubuntu is only affected if using battery and if using power adapter then problem is gone? my laptop running mostly on power adapter.

If you have all the latest updates and keep your laptop on AC, then you will incur almost no Load_Cycles. In fact, the latest updates should have solved the problem for most people even on battery power. It just so happens that for my specific hard drive I still get too many Load_Cycles (one every 5 seconds), even at the new settings.

---

### Post by Repgahroll on 2009-02-17
Excuse me, and sorry my english, but i have an Acer Aspire One, 160GB HDD version, and i couldn't get rid of the load Cycles problem.

First of all, i was really decided to use the Linpus Linux which came with the netbook, but i checked the load cycles, and i saw it was increasing every 10 seconds or so.

Then i saw a [great tutorial (the one linked in the 3rd post)]("http://en.opensuse.org/Disk_Power_Management") teaching how to fix the problem, but for some reason, didn't work.

So i tried to install Fedora, because i thought it was probably easier to have it fully working, because Linpus is a custom Fedora 8. But when i tried to fix the load cycles, it wasn't working also, i tried both the 'ugly fix for Gutsy' (for ubuntu < 8.04) and the 'ugly fix for Hardy and later'.

Then i thought it was a distro related issue, so i installed opensuse, and the same thing... then i gave up on non-debian-like distros and installed Ubuntu, which was working very well almost out-of-the-box, the only "special" thing i had to do was installing manually the newest alsa, because mic wasn't working. But the Load Cycles problem still happening, i tried again the two ugly fixes, and the thing still clicking every 10 seconds and increasing one cycle.

If i run manually the command (hdparm -B 254 /dev/sda) it works, but when i put it into a script in acpi or pm folders, it didn't work, of course i could put the command in rc.local, but the problem is that i need to sleep the netbook a lot of times a day, and every time i resume it the Load Cycles began to increase.

The strange thing is that there's no difference between 253~128, every number in this range will cause the hd to increase a load cycle every 10 seconds or so.

I hope someone can understand my english and help me.

Thanks.

---

### Post by quanumphaze on 2009-02-17
I'm assuming that you are using the latest Fedora and that Fedora uses pm-utils. So use the Hardy ugly fix.

Firstly, **did you remember to make the scripts executable?** It doesn't hurt to check.

Check to see if the scripts are actually working by running:```
sudo hdparm -I /dev/sda | grep 'Advanced power'
```The wiki from OpenSUSE uses a capital 'P' in 'Advanced Power' which doesn't give us that number (like 254).
Unplug your laptop and run this again. It should change according to the /etc/pm/config.d/disk script.

With the problem of it not working after suspending the laptop there is a third script you can make. I have it quoted in one of my [earlier posts]("http://ubuntuforums.org/showpost.php?p=6222987&postcount=246"). (Ignore the comment about the missing "(", it's the way that bash scripts use 'case')

---

### Post by Repgahroll on 2009-02-17
> **quanumphaze said:**
> I'm assuming that you are using the latest Fedora and that Fedora uses pm-utils. So use the Hardy ugly fix.

Firstly, **did you remember to make the scripts executable?** It doesn't hurt to check.

Check to see if the scripts are actually working by running:```
sudo hdparm -I /dev/sda | grep 'Advanced power'
```The wiki from OpenSUSE uses a capital 'P' in 'Advanced Power' which doesn't give us that number (like 254).
Unplug your laptop and run this again. It should change according to the /etc/pm/config.d/disk script.

With the problem of it not working after suspending the laptop there is a third script you can make. I have it quoted in one of my [earlier posts]("http://ubuntuforums.org/showpost.php?p=6222987&postcount=246"). (Ignore the comment about the missing "(", it's the way that bash scripts use 'case')

I think you didn't understood my english :) sorry... i'm using intrepid right now, i couldnt get my cam working on Fedora (tried the gnome and xfce versions).

Thanks for the capital "P" tip.

I actually just reinstalled the whole system (intrepid), and just applied the Ugly Fix for Gutsy (acpi) and the thing is working partially, i mean, when i plug/unplug the ac cable, it works, when i boot on ac or battery it works also, but when i resume or wake up, the power manager goes back to 128 (very deadly :)).

I'll undo the ugly fix for gutsy and apply the ugly fix for hardy.

Thank you very much man!! Sorry my english!


OFF:
The only bad thing about intrepid in this system is the boot time... man, it tooks almost one minute after grub, Linpus was 15 sec (after bios screen) i installed readahead and disabled some services, but didn't make any visible diference, bootchart says it's 2 seconds :(.

---

### Post by Repgahroll on 2009-02-17
No way man! :(

I tried the opensuse fix, but it doesn't work after wakeup/resume.

I found a better way to apply the ugly fix for gutsy, in acpi/*.d theres a script "90-hdparm.sh", you just need to find the lines:

	if [ "$STATE" = "BATTERY" ] ; then
	  hdparm -B 200 $dev
	else
	  hdparm -B 254 $dev

And modify it as you wish.
It works for me.

But i cant see a way to set the power management after resume or wake up... there should be a way... or will i need to make a idiot icon which runs the command "hdparm -B 254 /dev/sda" and name it "click here after wakeup or resume"?

Thanks for your patience.

---

### Post by Xhip on 2009-02-19
Hello friends!

Sorry putting this here, but this thread is very long and complicated to understand... I already opened a thread about what I'm going to ask, but no one was able to tell me what I wanted. I just want your fast opinion on my Load_Cycle_Count.

I'm running Xubuntu here on my laptop and I regularly have a check on the SMART attributes of my hard disk. I do this since my Windows times, and I always noticed that the parameter 'Load_Cycle_Count' decreased by 1 in an average time of 3 or 4 weeks.

I have changed to Linux, but obviously I continued to check the parameters and their evolution, and I think that now the same parameter is decreasing more fast than before, and I'm getting quite scared about it...

By the way, my SMART overall-health self-assessment test always passes ok, and all my short and extended self-tests were completed without errors. This was the evolution of the parameter in 1 week time:

1 week ago
==========
ID#: 193
ATTRIBUTE_NAME: Load_Cycle_Count
FLAG: 0x0032
VALUE: 042
WORST: 042
THRESH: 000
TYPE: Old_age
UPDATED: Always
WHEN_FAILED: -
RAW_VALUE: 581792

Today
=====
ID#: 193
ATTRIBUTE_NAME: Load_Cycle_Count
FLAG: 0x0032
VALUE: 041
WORST: 041
THRESH: 000
TYPE: Old_age
UPDATED: Always
WHEN_FAILED: -
RAW_VALUE: 592090

Can you give a fast opinion on this? Should I be worried? Thank you! :) 
By the way, my hard drive is 4 and a half years old...

---

### Post by GrouchoMarx on 2009-02-19
> I do this since my Windows times, and I always noticed that the parameter 'Load_Cycle_Count' decreased by 1 in an average time of 3 or 4 weeks.
I think you're looking at the wrong number. The Load_Cycle count is given by "RAW_VALUE". 592090 is about what you'd expect for a 4 1/2 year old hard drive. At this point you might consider turning Load_Cycles off. However old hard drives will inevitably die no matter what precautions you take. The most important to do is to regularly back up your data.

---

### Post by Xhip on 2009-02-20
Well, I usually look at that value "VALUE" (41) and compare it to the threshold value (0), and judging by their difference, I thought my hard drive still had a couple of time left... Problem is that the value has been decreasing more fast in Linux, than when I used Windows. Why is that?

And also, what are the consequences of turning off that feature? Isn't there a way of just slowing down the decrease?

Backup stuff is something usual over here :)

---

### Post by psychok9 on 2009-02-20
With a modify of laptop mode file, you can disable it. Set 254 the power management of your firmware when your laptop is in AC mode. Is a problem of too aggressive firmware for save very little energy...
You have less cycle counts than Windows, because it stresses very often your hdd, blocking the power management.

---

### Post by DevAdv on 2009-02-21
is this problem still there in 8.10?

just wondering before i go ruining my harddrive.

ty in advance.

---

### Post by BandD on 2009-02-22
> **DevAdv said:**
> is this problem still there in 8.10?

just wondering before i go ruining my harddrive.

ty in advance.


First off, it's not a Ubuntu or Linux "problem" (as in something inherent in the OS itself--other than extreme efficiency).  The consensus seems to be that it is faulty firmware from the drive manufacturers.  So it is not consistent across all hard drives. Some drives are unaffected (presumably they have better firmware) others are affected but changing the hdparm value to a less aggressive number will fix the "problem", while other drives have the "problem" and will not accept any hdparm values, and therefore there is no way to apply some sort of fix (other than asking the drive manufacturer for firmware that works correctly).

As far as I know, this "problem" exists in Intrepid.  The catch-22 that the Ubuntu devs have is that some people ***want*** very aggressive head parking for their laptop drives, to help ensure the least amount of possible data loss due to a head strike.  And because there is no way to conceivably know which drive models will be affected and which drives will not be affected, it is better to leave the parameters at default, than change them to something extreme.

It has also been discussed at length that this "problem" doesn't kill hard drives--even if left rampant. There should be nothing for anyone to fear.  High operating temperatures will kill a drive much faster than even 800,000-900,000 load cycle counts will.

---

### Post by DevAdv on 2009-02-22
the reason i ask is this. i ran a dual boot some time ago with ubuntu 6.04. i primarily used ubuntu for about 3 months. even now my load cycle count is less then 8k. 

is it safe to say my hard drive is unaffected? or was this not a problem back in the dapper days?

i guess the only real way to find out is to load up intrepid and test it, but would still like to know.

---

### Post by Xhip on 2009-02-27
Ok, so let me redraw the questions:

1) This is not a Linux problem, correct? It's HDD model dependent?
2) So, if my HDD is one of those models (with problems), it's normal that my Load_Cycle_Count increases more fast in Linux, correct?
3) Ok, you said I should not fear this parameter, but the normalized value (41) is decreasing towards the threshold value (0) faster than before, any fear on this?
4) Should I change something on my configuration or not?
5) I will probably buy a new hard drive, so I will be interested in fixing this problem on the new one, so that it does not suffer from the same problem...

---

### Post by xieu90 on 2009-02-27
I'd like to add some question too

how can i know if my hdd is one of those loser ?
aren't there any list ?


HITACHI HTS543225L9SA00: 36°C

sudo smartctl -a /dev/sda | egrep '(Load_Cycle_Count|Temperature)'
193 Load_Cycle_Count        0x0012   099   099   000    Old_age   Always       -       **11127**
194 Temperature_Celsius     0x0002   152   152   000    Old_age   Always       -       36 (Lifetime Min/Max 8/45)

that is my hdd, it is quite new, i get my laptop on 09-01-2009
so it is around 50 days old. if I count right then i lost around 222 cycle per day. does it mean I am infected ?

what about those ugly fix ? which one should I use ? 
I just see feisty, hardy, gutsy versions. but I am using linux mint 6 = Intrepid.

thought it is not ubuntu fault, but are there any fix for this bug from heaven for intrepid ?
what about next version of ubuntu in april ? Can Ubuntu- the leader of Linux do something to stop this huge bug ?

besides are there any symptoms for this bug? 
i just found out that I am infected, because my temperature in mint was higher in xp.
the highest part of my laptop is somewhere between cpu and HDD
and i noticed that my laptop is cool under linux, but when i mount the hdd to listen to music then my temperature will go up and stay there. even i unmount and let my laptop idle. in xp it would go down and be cool like the beginning.

so could it be because of that bug ? I am not so sure. unfortunately i am not a pro yet. so can anyone give me some explain ?

---

### Post by DevAdv on 2009-02-28
xieu i would say your affected by this.

my hard drive is 4-5 years old, a hitachi, and only has a load cycle count of 7561.

---

### Post by xieu90 on 2009-02-28
wow, impressive ! 5 years and only 8000
mine is 50 days and already 12000 
:lolflag:

so can you give me any hint ? what should i do to cure the poor organ of my laptop ?
it is dying. my poor little child is dying.

---

### Post by BandD on 2009-03-02
xieu90:

try running this command in a terminal:
```
sudo hdparm -B 254 /dev/sda
```
A setting of 254 should set your hard drive to the least aggressive power managemnet setting.  You can try different values for the 254 in the code above.  You can then check the smartctl values for the Load_Cycle_Count and see if it helps.

---

### Post by MegaJim on 2009-03-11
Discovered that on some laptops the ugly fix script is given the wrong/unknown power status on resume from standby resulting in the laptop quietly sitting there ticking away after its supposed to be fixed.

I solved it by adding a cronjob to run the script at five minute intervals

```
sudo crontab -e
```
Choose your preferred editor if prompted then copy in the line below, using a valid path to ubuntu-demon's ugly fix script
```

# m h  dom mon dow   command
*/5  *   *   *   *    /etc/acpi/resume.d/99-hdd-ugly-fix.sh

```

Depending on your config you may need to add sudo in front of the hdparm lines of the original script under Intrepid

---

### Post by Rossi9x87 on 2009-03-15
OK i need a little help on this issue.

I just bought a XPS 1530 and have been configureing it like crazy.  Everything seems to work rather well, but it has a pretty bad load-cycle count. It increases about 20 every 10 minutes (i.e. 120/hour).

I have tried the ugly fix with -B set to 254 and it does not do anything. I'm unsure of what to do next.  


Any help would be much appreciated. Thank you.

---

### Post by Hated On Mostly on 2009-03-15
> **Rossi9x87 said:**
> OK i need a little help on this issue.

I just bought a XPS 1530 and have been configureing it like crazy.  Everything seems to work rather well, but it has a pretty bad load-cycle count. It increases about 20 every 10 minutes (i.e. 120/hour).

I have tried the ugly fix with -B set to 254 and it does not do anything. I'm unsure of what to do next.  


Any help would be much appreciated. Thank you.

Try this:

[http://ubuntuforums.org/showthread.php?p=6157860#post6157860](http://ubuntuforums.org/showthread.php?p=6157860#post6157860)

Much easier to do than the ugly fix. Works perfectly for me in v8.04 (Hardy Heron) and v8.10 (Intrepid Ibex).

---

### Post by AbtZ on 2009-03-17
Indeed, the ugly fix is a big mess, and unnecessarily complicated to boot.

It would be nice if the first post was updated with one of the less ugly fixes. 

Last time I had to do something about this, I basically just set "ENABLE_LAPTOP_MODE=true" in /etc/default/laptop-mode and told laptop mode to control power saving settings also when on AC. Worked perfectly on that computer.

Here's a complete guide:
[http://vale.homelinux.net/wordpress/2007/10/24/potential-risk-for-your-nx6325s-harddrive/](http://vale.homelinux.net/wordpress/2007/10/24/potential-risk-for-your-nx6325s-harddrive/)

---

### Post by yesint on 2009-05-01
Anybody knows if this annoyance with load cycle count is finally fixed in 9.04? I'm thinking about upgrading my laptop from 8.10 but I'm getting sick of applying the fixes again, to struggle with suspend/resume, etc.
Btw, is there a single universal fix for this now? The threads about this issue are huge and the number of solutions is 10+, so anybody is going to be lost immediately.

---

### Post by BandD on 2009-05-01
@ yesint

For me things worked as I would expect.  While on AC power the hard drive does not park the heads.  When running on battery power, the heads park and unpark.  I'm not sure what the devs are using in 9.04 to control this behavior, but it works as I would expect it to.

---

### Post by yesint on 2009-05-04
> **BandD said:**
> @ yesint

For me things worked as I would expect.  While on AC power the hard drive does not park the heads.  When running on battery power, the heads park and unpark.  I'm not sure what the devs are using in 9.04 to control this behavior, but it works as I would expect it to.

I suspect that this depends on the hard drive model heavily. It seems that the only way to find out is to try.

---

### Post by victorgreen on 2009-05-04
Hey Hated on Mostly, Im trying your suggestion, Im running Jaunty 64 on a Thinkpad X61 with 320gb WD 5400rpm drive; everytime i upgrade OS version I have to go through this mess of dealing with spindwon [this isnt the drive that came wiht the laptop, that one blew out in  1.5years]

i hope it works, but this drive seems to like totally disabling PM on HDD (255) than 254

---

### Post by BandD on 2009-05-05
> **yesint said:**
> I suspect that this depends on the hard drive model heavily. It seems that the only way to find out is to try.

I suffered badly in Gutsy and Hardy with this problem on this drive.  So Jaunty is a blessing!

---

### Post by xieu90 on 2009-05-08
> **BandD said:**
> I suffered badly in Gutsy and Hardy with this problem on this drive.  So Jaunty is a blessing!

hi bandd,
why is jaunty a blessing ?
did the problem disappear ? can you tell me which filesystem did you choose ?
ext3 or ext4 ? did you have to use ugly fix ?

---

### Post by victorgreen on 2009-05-08
Im very interested as well. My problems with Jaunty may be from the fact that I upgraded and didnt fresh install, not not using an ext filesystem.

---

### Post by kung fu buntu on 2009-05-09
On my desktop system I have 4 HDD and running
```
smartctl -a /dev/sdX | grep Load_Cycle_Count
```
only shows results for 1 of them.

How can I get the load cycle values for the other HDD?

I have run smartctl tests on the disks and they look fine but you can never be too sure (I've read that only 60% of the disks that failed have given warning signs through SMART).


BTW, this issue seems to still be present with newer hard disks (and it doesn't seem to be ubuntu related per se, but instead with the hard disk and kernel):
[http://forum.excito.net/viewtopic.php?t=1554](http://forum.excito.net/viewtopic.php?t=1554)
Be wary of WD Green Power disks.

---

### Post by kung fu buntu on 2009-05-18
Any comments on this?
Any way to see the load cycle values for the other HDD?

---

### Post by Alfred_McGee on 2009-05-24
The Load_Cycle_Count issue has been a problem for me since the Gutsy days. I kinda thought that it would be fixed in Jaunty, but oh well, the fix at the beginning of this thread, though "ugly," is still effective, except when resuming from suspend. In that case, switching from AC to battery power, or vice versa, always works to bring my load cycle count back under control.

EDIT: New in Jaunty: resume from suspend no longer disables the fix posted at the start of this thread- at least not when you've got AC power on.

---

### Post by BandD on 2009-05-24
> **xieu90 said:**
> hi bandd,
why is jaunty a blessing ?
did the problem disappear ? can you tell me which filesystem did you choose ?
ext3 or ext4 ? did you have to use ugly fix ?

For me, in Jaunty, while on AC power my drive heads don't park ever.  When on battery power, they do park--relatively often.  This is what I expect and it was a pleasant surprise for me to find this behavior out of the box in Jaunty--no ugly fix required!

I chose to stick with the tried and true ext3.

---

### Post by BandD on 2009-05-24
> **kung fu buntu said:**
> On my desktop system I have 4 HDD and running
```
smartctl -a /dev/sdX | grep Load_Cycle_Count
```
only shows results for 1 of them.

How can I get the load cycle values for the other HDD?

I have run smartctl tests on the disks and they look fine but you can never be too sure (I've read that only 60% of the disks that failed have given warning signs through SMART).


BTW, this issue seems to still be present with newer hard disks (and it doesn't seem to be ubuntu related per se, but instead with the hard disk and kernel):
[http://forum.excito.net/viewtopic.php?t=1554](http://forum.excito.net/viewtopic.php?t=1554)
Be wary of WD Green Power disks.


I would imagine that you would have to run the smartctl -a command for each drive individually (i.e. if you have drives sda, sdb, sdc, and sdd, then you'd have to run sudo smartctl -a /dev/sda, and then run sudo smartctl -a /dev/sdb, then run sudo smartctl -a /dev/sdc, then run sudo smartctl -a /dev/sdd).  

It's possible that these drives don't support SMART values (I'm assuming this is a desktop).  In general desktop drives don't ship with any power saving features because there is really no need for them (you don't have to worry about draining a battery!).  In which case there is load_cycle_count because head parking isn't something the drives are even capable of.

---

### Post by xieu90 on 2009-05-26
hi , i typed installed and run codes like this
ace@ace-laptop ~ $ sudo apt-get install hdparm
Reading package lists... Done
Building dependency tree       
Reading state information... Done
hdparm is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 66 not upgraded.
ace@ace-laptop ~ $ sudo hdparm -B 254 /dev/sda

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
ace@ace-laptop ~ $ sudo hdparm -B 254 /dev/sda

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
ace@ace-laptop ~ $ sudo hdparm -B 254 /dev/sda3

/dev/sda3:
 setting Advanced Power Management level to 0xfe (254)
ace@ace-laptop ~ $ sudo smartctl -a /dev/sda | egrep '(Load_Cycle_Count|Temperature)'
193 Load_Cycle_Count        0x0012   098   098   000    Old_age   Always       -       22620
194 Temperature_Celsius     0x0002   144   144   000    Old_age   Always       -       38 (Lifetime Min/Max 8/45)
ace@ace-laptop ~ $ 





so will it be ok from now on ?
what does 192 infront of Load cycle count mean ?
and is my hdd set to 254 ?

---

### Post by Hated On Mostly on 2009-07-16
Recently did a clean install of Ubuntu v9.04 (Jaunty Jackalope) and the problem has been fixed in this version. No need for me to do any of the fixes.

---

### Post by sefs on 2009-09-01
Hi, I just want to confirm that I no longer need to do this with 9.04.

Thanks, and how can I check.

---

### Post by paulchinnz on 2009-09-06
In terminal:

sudo apt-get install smartmontools

date; sudo smartctl -a /dev/sda | egrep '(Load_Cycle_Count|Temperature)'

Run the second one every so often (15 minutely if you're bored, otherwise something like daily )

---

### Post by rg_stephens on 2009-09-30
Since I've installed 9.04 I've noticed that the hard drive would cycle on and off very frequently. Neither the -B 254 or -B 255 had any affect. I tried the -S 0 and I think this fixed it. 


Robert 
HP tc4200 tablet

---

### Post by Bjalf on 2009-11-07
A clean CLI only install from an alternate 9.10 CD still has the old **Load_Cycle_Count **problem. Solution: install acpi-support
```
sudo aptitude install --without-recommends acpi-support smartmontools
```smartmontools is probably not part of the solution, just needed to check the **Load_Cycle_Count**.

---

### Post by James Keating on 2009-11-08
After upgrading to Karmic 9.10, I noticed that my hard drive was starting and stopping a couple of times a minute. Issuing a smartctl command didn't make a difference, and neither did unchecking "Spin down hard disks when possible" in System > Preferences > Power Management. 

I tried removing the packages laptop-detect and laptop-mode-tools and rebooting. This seems to work. It also seems too simple and too easy. Where is the Linux joy in tinkering with arcane scripts I don't understand? Still, it seems to work. Something in the scripts must have interfered with my laptop's default tendency to keep the hard drive spinning. 

This could possibly be a problem under battery power, if changing the Power Management settings for battery power has no effect. But I never unplug my laptop anyway.

---

### Post by nonperson on 2009-12-15
> **James Keating said:**
> 
I tried removing the packages laptop-detect and laptop-mode-tools and rebooting. 

This works for me on my NC10 using Xubuntu (Karmic.) Having thought I had found a solution I tried a fresh install of Linux Mint 8 hoping that it work there too. It doesn't. I am going to return to Xubuntu. Though I am only a light user and it would be years until I hit my drive's maximum duty cycle I find the noise (and knowledge of what is happening to small parts under great load) disturbing. I see a copy of Windows 7 in my not to distant future............

EDIT: I am correct in thinking Debian has *fixed* the problem? Or I am getting confused with all the messing about?

---

### Post by Rubunter on 2009-12-21
I hear the clicking of the HD on my HP mini 5101 running UNR 9.10 when on battery. 2 days of use and a load cycle count of 978 (scary, isn't it?). The only fix that has worked for me is setting the apm to 254 after every boot.

---

### Post by BandD on 2009-12-26
> **Rubunter said:**
> I hear the clicking of the HD on my HP mini 5101 running UNR 9.10 when on battery. 2 days of use and a load cycle count of 978 (scary, isn't it?). The only fix that has worked for me is setting the apm to 254 after every boot.

That's the default and expected behavior.  The head parking was designed to save energy and to protect the disk in case of a strong jolt.

Have you tried to going to Power Preferences and uncheck the box that says "Spin Down Hard Disks When Possible"?

---

### Post by Rubunter on 2009-12-26
> **BandD said:**
> That's the default and expected behavior.  The head parking was designed to save energy and to protect the disk in case of a strong jolt.

Have you tried to going to Power Preferences and uncheck the box that says "Spin Down Hard Disks When Possible"?

That did not work! thank u anyway

---

### Post by 9tails on 2010-02-19
Any advice for USB HDDs? I own a WD3200BEVT-60ZCT0 that is on Nicedude's list at [http://ubuntuforums.org/showthread.php?t=795327](http://ubuntuforums.org/showthread.php?t=795327)

hdparm doesn't work with USB drives, is there another way to disable apm or do I have to buy a new hard drive? #-o

(if only the link above had been made a sticky topic I would have never bought a Western Digital drive!)

---

### Post by dementic on 2010-05-15
Where are start.d suspend.d and resume.d on 10.04. Because it doesn't work for me.

---

### Post by nandayo on 2010-08-15
Hi all,

Does this Load_Cycle_Count problem still be unsolved ? My laptop have 250k cycles in 3 goddam years, and is increasing by one each 5 seconds, whereas under windows it increases from one each minute !

Damn this problem is really starting to sux a lot now, can you believe this thread started in 2007 and that it is still unfixed ?!!

---

### Post by nhocjok on 2011-01-28
It's 2 years already and this issue still hasn't been solve officially :(

---

### Post by Sir_Yaro on 2011-02-12
Problem still exist on kubuntu 10.10 :/
Setting Advanced Power Management level to disabled seems to solve the problem :/ (hdparm -B 255 /dev/sda)

---

