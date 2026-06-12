---
title: "Lenovo over heat with 8.04"
date: 2008-07-20
forum: Hardware
---

### Post by XProgrammer on 2008-07-20
My Lenovo T60 laptop is getting over heated after 8.04 upgrade.
I'm running Ubuntu on my lenovo laptop for over a 1.5 years from 6.06 to 7.10. No issue with fan or heat. 

After my upgrade to 8.04 on May 1st of 2008, I ran into battery issue and eventually got replaced. Laptop system temperature goes beyond 90 degree now. 

Please help me to fix the issue. I'm thinking of downgrade to 7.10. 
I'm posting this from Windows Xp. I dont see this problem in Windows.

---

### Post by 71CH on 2008-07-20
I also would like to know this.

---

### Post by XProgrammer on 2008-07-20
Hi 71Ch,

do you also see this issue with your R61 laptop?.

---

### Post by 71CH on 2008-07-20
Yes indeed.  My laptop is at around 102 degrees fahreheit right now.

---

### Post by XProgrammer on 2008-07-20
[https://bugs.launchpad.net/ubuntu/+bug/250289](https://bugs.launchpad.net/ubuntu/+bug/250289)

I've raised a bug for this. 

Actually, i got into battery failure. Last week, I got a message that " Your battery capacity is 42%(poor) and you may need to repair or change your battery". I was able to get only 40min battery backup. I went ahead and changed my battery. 

I had been running 7.l0 about 6 months. I didnt see such a problem.

Because of 8.04, I got my battery fault. :(

I hope, ubuntu team would address it asap.

---

### Post by 71CH on 2008-07-20
Do you think that if I went back to 7.10 my heat issues would go away?  I don't have any desire for any battery failure myself.  Also, would 7.10 be compatible with my R61.  I thought I heard somewhere that these two had issues with each other.  Thanks.

---

### Post by 71CH on 2008-07-21
BTW when you say laptop temperature what part are you talking about?  HDD?  CPU?

---

### Post by PHATSPEED7x on 2008-07-21
Not to threadjack, but is there a program that will show you your laptop temps that you can add to linux?

---

### Post by DanubeRS on 2008-07-21
I know of some desktop widgets that display the load of the cpu, adn various other parts of hardware, but I don't know wether they have CPU reading temperature 'out of the box'

Try searching for a widget application (I think there is one on the Compiz Fusion site) and have a look wether it has a CPU temp plugin.

Im sorry I cant be more specific, i havent exactly looked into software CPU temp monitoring.

---

### Post by 71CH on 2008-07-21
i think you can sudo apt-get install computertemp and add the applet to your panel

---

### Post by PHATSPEED7x on 2008-07-21
> **71CH said:**
> i think you can sudo apt-get install computertemp and add the applet to your panel

Didn't come up with anything.

---

### Post by XProgrammer on 2008-07-21
"acpi -V" command would give you temperature info. 

xp@lenovo-laptop:$ acpi -V
     Battery 1: charging, 41%, 01:34:22 until charged
     Thermal 1: ok, 76.0 degrees C
     Thermal 2: ok, 78.0 degrees C
  AC Adapter 1: on-line
xp@lenovo-laptop:$ 
xp@lenovo-laptop:$ acpi -V
     Battery 1: charging, 41%, 01:32:59 until charged
     Thermal 1: ok, 76.0 degrees C
     Thermal 2: ok, 83.0 degrees C
  AC Adapter 1: on-line
xp@lenovo-laptop:$ uptime 
 18:36:53 up 19 min,  2 users,  load average: 0.45, 0.87, 1.01

within 19 min, my laptop gone into 83 degrees. 

Please i need a some workaround or fix.

---

### Post by 71CH on 2008-07-21
wow yours is super hot
I actually found out that my temp is in the normal range
I wish I could help you out but I'm still pretty much a noob...

---

### Post by XProgrammer on 2008-07-21
this is irritating problem.
the bug seems to be reported already 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/213818](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/213818)

no significant improvement. I'm losing the faith in ubuntu after using it for last 3.5 years. 

i took the risk of challenging everyone at office and installed the laptop with ubuntu without taking IT dept help. Now, I understanding why Windows is important. I'm not afford to lose any single data. I'm having a laptop which i cant keep it in laps just because of 8.04 is over heating . :(

---

### Post by samskpun on 2008-07-28
[http://ubuntuforums.org/showpost.php?p=5035858&postcount=7](http://ubuntuforums.org/showpost.php?p=5035858&postcount=7)

i did that and temp drop a lot...

---

### Post by gunashekar on 2008-07-28
Heating problem on my HP compaq disappeared after I updated the BIOS. I do not know about your T60 but updating the BIOS fixes many other issues. Take a look at [http://www-307.ibm.com/pc/support/site.wss/MIGR-63024.html](http://www-307.ibm.com/pc/support/site.wss/MIGR-63024.html) for T60

---

### Post by MaindotC on 2009-02-02
Nothing on there about fixing any overheating.

---

