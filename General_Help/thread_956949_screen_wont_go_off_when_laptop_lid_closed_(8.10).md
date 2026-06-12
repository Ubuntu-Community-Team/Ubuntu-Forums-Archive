---
title: "screen wont go off when laptop lid closed (8.10)"
date: 2008-10-23
forum: General Help
---

### Post by wolf-n-beast on 2008-10-23
i have a Compaq nc6000 running Ubuntu 8.10 and when i close the lid the screen will not go off. i have already tried the  power management settings.

EDIT: it is not my computer because closing the lid in my windows partition does turn off the screen so its something to do with the software configuration in Ubuntu 8.10

---

### Post by shawnrgr on 2008-10-23
Check your /etc/X11/xorg.conf, make sure you have the DPMS option for you monitor. X allows DPMS (Energy Star) features to be used with capable monitors.

Add the following to your "Monitor" section:
```
Option       "DPMS"
```

Restart X and try again. If not, after testing again, check "dmesg" output for anything relavent to your monitor, X or power.

---

### Post by wolf-n-beast on 2008-10-23
i tried that it still doesn't  work and the dmesg gave me a whole bunch of stuff that i have know idea what it means and it is long

---

### Post by gsedej on 2009-02-18
Hello!

I too have problem with my NC6000 HP laptop.
I tried to do "DMPS", but I didnt noticed any change.

BUT
Sometimes lid button works, I do not know exactly when. I may guess that if I run laptop without battery and then turn off, put battery in and then boot again, it works (no picrure at all on screen (windows just turn off the back light, picture is still there), if I play music in stops for a secound and then resumes)... But when I boot again, button doesnt work.
AND
Button works in BIOS, GRUB, even half time of ubuntu boot, but than just doesent work. I think when some drivers loads (video?).

I have P4 M1.6, 1GB ram , ATI9600M, intel wireless on Ubuntu 8.10.
I haven't tested on other distibutons yet and I didn't try restricted video drivers too.

EDIT: I tried some old Sabayon live CD and lid button works fine

---

### Post by Guus1982 on 2009-03-01
same problem here hp nc4400

---

### Post by Rallg on 2009-03-01
I have a different computer. In my case, the original BIOS did not support all power management features, but a more recent BIOS does. So, consider going to the manufacturer's site and see if there is a BIOS update. If there is, and if you don't have Windows also, then maybe you can do the update with a DOS version of the BIOS updater. It's tricky but it can be done (search forum for advice).

---

### Post by Guus1982 on 2009-03-02
In windows hibernation worked just fine, do i really need to mess with my bios? id rather not

---

### Post by djwohls on 2009-03-12
Same issue here. Dell D430.  Works fine under Windows.

---

### Post by raido357 on 2009-04-16
Same problem here with HP NC6000, actually it began from 8.04 version already, currently using 9.04.

Lid switch doesn't to nothing, even it's state doesn't change, although it will start working after i have hibernated my laptop and resumed it. It would be really nice to found a fix or something.

watch -n 0.5 cat /proc/acpi/button/lid/C138/state -> no change while pressing lid switch.

#dmesg | grep Lid
[    3.601609] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input2
[    3.601782] ACPI: Lid Switch [C138]

Any help ?

---

### Post by Ebrithil on 2009-05-01
Guys I'm having the same problem, and I have a Inspiron 5160. But it works in Windows. I am using the 9.04 Jaunty. Can someone please help with this issue, it's a serious problem.

---

### Post by Ebrithil on 2009-05-03
BUMP this is also in launch pad, but it's for older versions of Ubuntu.

---

### Post by Random5 on 2009-05-05
This is happening to me with an Inspiron 6400 as well - screen turns black when I close the lid but the backlight is still on, so it's definitely detected I've closed the lid. I've just noticed it IS actually off right now with the lid closed, so it seems to start working after the laptop has been suspended/hibernated? Or it was possibly having the AC adaptor unplugged and replugged in.

---

### Post by Ebrithil on 2009-05-06
Looks like no one knows.

---

### Post by meteornp on 2010-02-16
hello all,
at my hp530 laptop, the same problem...
and i solved it by adding " & " to the end of this line:
xset dpms force off &
... of this file:
/usr/share/acpi-support/screenblank
... maybe someone will find this usefull.

---

### Post by gsedej on 2010-09-09
Hi,

I see my theme is still active.
I have problems again on my HP nc6000 in Lucid. It worked ok in 9.04 and 9.10 but in 10.04 it isn't working again.

meteornp: I tried your method but didn't work. 
But I find out that screen goes off if I go to terminal and write:
```
xset dpms force off
```

I presume that scipt "/usr/share/acpi-support/screenblank" isn't called the right way.

But I still didn't find out how to get input from screen lid button.

---

