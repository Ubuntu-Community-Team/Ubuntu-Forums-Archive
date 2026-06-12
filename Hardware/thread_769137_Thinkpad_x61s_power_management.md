---
title: "Thinkpad x61s power management"
date: 2008-04-26
forum: Hardware
---

### Post by csadowski on 2008-04-26
Hi all,

I just istalled hardy on my Thinkpad x61s, and have a few problems i can't seem to resolve:

1.  When i run my laptop on battery, the gnome power manager tells me i have about 3 hours and 5 minutes of battery life left, while acpi tells me i have 4 hours and 33 minutes left.  Is there any reason for this discrepancy, and how can i fix it?

2.  My fan never seems to stop spinning.  Is there a fix for this?

3. My right palm rest gets really warm, I think it may be due to the wireless card getting hot, but I'm ot sure.

Any help would be greatly appreciated.  Thanks!

---

### Post by gudmund84 on 2008-05-02
I got the same problem on my Thinkpad T60. The fan does not stop spinning and it gets really hot. Powersaving is not working!

The acpi reports 2:48 @ 56%, but gnome power manager says 1:40 on 56%. The sad thing is that gnome power manager is calculating the right time, but when i used Windows XP the acpi time would be right for 56%.. this is annoying!.. not only the time but also that it gets so hot and noisy.. have any1 tried KDE powersaver?

---

### Post by Axx83 on 2008-06-13
OH MY GOD and you're even complaining ?

I've been messing with these stuff for the past 2 weeks on my Thinkpad X60s and THE BEST I can get is 1.9 hours

3 hours would be paradise, please give me your configurations

---

### Post by Axx83 on 2008-06-13
by the way for the fan problem try this:
[http://www.gambitchess.org/mediawiki/index.php/ThinkPad_Fan_Control](http://www.gambitchess.org/mediawiki/index.php/ThinkPad_Fan_Control)

it works great

---

### Post by drorata on 2009-08-19
I am looking for solutions to the heating problem and the battery consumption as well. 

My right hand palm is getting over heated (not always). I lift the laptop a bit and it helps. I Installed the Fan-Control but i don't know what should be the values, and how to handle them... I have:
Sensor 0: 46
Sensor 1: 49
Sensor 2: 49
Sensor 3: 42
Sensor 4: 36
<No Sensor 5,7>
Sensor 6: 34
Sensor 8: 45
Sensor 9: 42

I think that the fan never idle for me as well.

As for the battery, I am using [*powertop*]("http://www.lesswatts.org/projects/powertop/") and it helps the battery last for about 2.2 hours. Problem is, that resuming from suspension after the changes *powertop* applies takes much longer (about 30-40 seconds). But still, I feel that the power management of Ubuntu could be better, and I am looking for further solutions to the battery issue (I have a 6-cell).

Any other ideas?

---

### Post by Axx83 on 2009-08-20
I have a x60s, heat is above normal but in windows as well. I get least wattage consumption using laptop-mode tools. Here's my guide:

[http://ubuntuforums.org/showpost.php?p=7271995&postcount=7]("http://ubuntuforums.org/showpost.php?p=7271995&postcount=7")

check if that works better

---

