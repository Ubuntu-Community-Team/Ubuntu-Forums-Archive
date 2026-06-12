---
title: "Acer Aspire One"
date: 2014-06-26
forum: Hardware
---

### Post by WanderingAlbatross on 2014-06-26
Dear friends,

Just installed on the following machine, which had Windows 8:
Acer Aspire One
Model: Q1V2C  (also says CM-5 but I don't know if this is important)

One issue I faced was disabling Secure Boot in UEFI.  Strange to me was that you actually have to put a Supervisor Password in the BIOS (I know that's not the new name) for the ability to boot from a CD-ROM, as per [this]("http://acer--uk.custhelp.com/app/answers/detail/a_id/6814/~/enabling-the-boot-device-menu")

Also, this device has what is known as a clickpad.  Interesting device, but leads to a small headache.  It does not by default have it's right click working.  To get it to work I had to create this script as .clickpad in the home directory: (note that there are many ways to skin a cat)
```
#!/bin/bash
synclient Clickpad=1
i=0
while read label min delim max; do
 if [ $i -eq 0 ]; then
  minx=$min
  maxx=$max
 elif [ $i -eq 1 ]; then
  miny=$min
  maxy=$max
  break
 fi

 (( i++ ))
done < <(xinput list "12" | grep Range)
#the 12 above is the my device number.

left=`echo \($maxx - $minx\) / 2 + $minx | bc -l`
right=$maxx
top=`echo \($maxy - $miny\) \* 0.8 + $miny | bc -l`
bottom=$maxy

echo "$left"
echo "$right"
echo "$top"
echo "$bottom"

xinput set-prop "ETPS/2 Elantech Touchpad" "Synaptics Soft Button Areas" $left $right $top $bottom 0 0 0 0
```

This was from these sources: (A big thanks to them.)
[http://ubuntuforums.org/showthread.php?t=2048226](http://ubuntuforums.org/showthread.php?t=2048226)
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/944961](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/944961)

The part I had to add was the first line
```
synclient Clickpad=1
```
because I found that it would not open the necessary parameters unless you told GNU/Linux that it was indeed a clickpad.
Also note that I had to change the ```
xinput list "12"
``` because that was my device number, as stated with the command:```
xinput --list
```

Then one final step, once you have tried the script and confirmed that it works, is to put it somewhere and let it run at startup.  I put it in my home directory, then went to Settings > Session and Startup > Application Autostart and added it as a startup program.  This works on single user systems, but someone else would have to give advice on multi-user logins.

Hope this helps someone else in their quest.

---

### Post by mörgæs on 2014-06-26
Thanks, please post a brief summary in [http://ubuntuforums.org/showthread.php?t=1543006](http://ubuntuforums.org/showthread.php?t=1543006) , in which you can link to the thread here.

---

### Post by WanderingAlbatross on 2014-06-27
Done

---

### Post by WanderingAlbatross on 2014-07-09
Additionally, this also works on a Chromebook with Chrubuntu installed.

---

