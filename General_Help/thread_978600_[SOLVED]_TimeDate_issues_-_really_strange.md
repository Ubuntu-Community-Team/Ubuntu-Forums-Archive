---
title: "[SOLVED] Time/Date issues - really strange"
date: 2008-11-11
forum: General Help
---

### Post by Neural oD on 2008-11-11
Hi All, I hope someone out there can help me. Maybe I'm overlooking something, but it has been really frustrating me. The issue is this: if I'm on the command line and call the date function, it shows that the time is 7 hours behind that shown in the panel. If I change the date in either it effects the other - they do not seem to be synced. How can I get my time on the command line and the applet to be the same.

Thanks in advance

---

### Post by 4-Ever-Euphemistic on 2008-11-11
Your saying that,if you alter the date then it changes the time to somthing different that you have set and vice-versa?

If so have you tried setting it to something totally different and then retry it of your own location!

---

### Post by Neural oD on 2008-11-11
Basically, if I change the time using the clock applet on the top panel on the desktop, then the time in a terminal shows differently. The time in the terminal is 7 hours behind. Now if I wanted the time to display correctly in the terminal, and I set it there, then the time in the applet would be incorrect.

---

### Post by Portmanteaufu on 2008-11-11
Are you in the time zone 7 hours behind UTC (Greenwich Meantime)? If so, are your system's settings aware of that?

---

### Post by Neural oD on 2008-11-11
Hi Portmanteaufu - no this is actually quite strange as in fact my time zone is actually UTC +2 hours. So I'm really stumped as to what is going on here.

---

### Post by bapoumba on 2008-11-11
Please post the output of:
```
bapoumba@SonyBlue:~$ grep UTC /etc/default/rcS
UTC=no
bapoumba@SonyBlue:~$ 
```
Do you have another OS? Does it show the correct time?

[https://help.ubuntu.com/community/UbuntuTime](https://help.ubuntu.com/community/UbuntuTime)

---

### Post by Neural oD on 2008-11-11
Hi bapoumba  - my result with the grep command came out as UTC=yes

I was thinking that this issue may involve differences in the hwclock and the system clock. Could this be the case?

---

### Post by Neural oD on 2008-11-11
> **bapoumba said:**
> 

Do you have another OS? Does it show the correct time?


Sorry - never mentioned - no I don't run another os on this machine - got rid of Vista fast :)

---

### Post by bapoumba on 2008-11-11
> **Neural oD said:**
> Hi bapoumba  - my result with the grep command came out as UTC=yes

I was thinking that this issue may involve differences in the hwclock and the system clock. Could this be the case?
Probably. There are useful infos in the link above. You can set it to "no" and reconfigure tzdata. Should work (TM) :)

If you use another OS (instructions in the link are for Windows, I think it is different for MacOS), you may have to perform more adjustments.

---

### Post by Neural oD on 2008-11-11
Thanks - let me go tinker with the tzdata. One thing though -skimming through the links you gave, it seemed to indicate that Linux should work well with UTC. As mine is already set to UTC, could this be a bug, and should I then report it?

---

### Post by bapoumba on 2008-11-11
> **Neural oD said:**
> Thanks - let me go tinker with the tzdata. One thing though -skimming through the links you gave, it seemed to indicate that Linux should work well with UTC. As mine is already set to UTC, could this be a bug, and should I then report it?
Well, I do not know. I've seen bugs around against the debian installer (that ubuntu uses) but they were old. Do you use a ntp server to synch time and date? (I do not, and the time got set up right when we went to winter time a couple weeks ago).

Edit:
> Ubuntu comes with ntpdate as standard, and will run it once at boot time to set up your time according to Ubuntu's NTP server
Looks like ntpdate is set up and runs at boot time even if you do not ask for it specifically. I had problems looooooooong time ago with either Warty or Hoary, that is why I have played around with tzdata & Cie a little :)

---

### Post by Neural oD on 2008-11-11
I did use the manual selection of time - no ntp, but then I tried ntp - still giving me the same hassles. BTW - I now put a string in my .profile "TZ='Africa/Johannesburg'; export TZ" and this seems to have set my hwclock and sysclock on to the same time. So if I put in date this is what I get: Tue Nov 11 16:22:50 EST 2008, and if I type in hwclock, I get this:Tue 11 Nov 2008 04:23:11 PM EST  -0.450726 seconds.  
The strange thing is that the clock applet is still displaying 23h23 - which is in fact the correct time for me.

---

### Post by Neural oD on 2008-11-17
Solved the issue - was really silly from my side. Posted this incase anyone else could find this helpful. 
Basically I had zsh installed and in the config file for it - it has a TZ setting. I was initially unaware of this. When I changed that, then I could configure the date and hwclock functions without any problems. IOW - all things then worked as expected.

---

