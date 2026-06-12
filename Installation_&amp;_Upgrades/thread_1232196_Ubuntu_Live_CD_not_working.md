---
title: "Ubuntu Live CD not working"
date: 2009-08-05
forum: Installation &amp; Upgrades
---

### Post by gdoc on 2009-08-05
Hi,
I'm trying to install Ubuntu 9.04 on a friends laptop. She has two hadrives in her laptop and the plan is to install ubuntu on one. The problem is this, when I boot from the cd I get to the screen where I have the option to 


[LIST]
[*]install Ubuntu
[*]try Ubuntu without installing
[*]check cd for defects
[*]etc..
[/LIST]
The problem is that when I select one of these the screen goes black & nothing happens. I am using the 9.04 cd. I searched online & saw someone recommend the alternative text based install cd. I tried that too but the same happened.

I also tried the 8.04 version. In this one when I picked one the above options the ubuntu loading screen appeared but nothing happened, i.e. the loading bar didn't change. I left it for more than an hour and it remained unchanged.

I don't think its the cd as I used the same 9.04 cd to install it on my laptop with absolutely no problems.
Her laptop is a LG Electronics, E500-J.AP51B

Does anybody have any advice? I've searched online but I've been unable to find a solution and would greatly appreciate any advice you all could give.

Thanks,

G

---

### Post by tripolitan on 2009-08-05
This is common among burnt CDs. Try burning the Ubuntu CD at a lower speed.
or it could be this bug:

lg notebook E500-J.AP51B can't be booted unless C-state is disabled or the boot option of "nolapic_timer" is added.

so you might want to add that option to the boot parameters

---

### Post by gdoc on 2009-08-05
Thanks for the advice tripolitan, I'm burning the CD at the slowest speed possible on my laptop (x10). If that doesn't work I'll look at the bug.
Thanks
G

---

### Post by presence1960 on 2009-08-05
[MD5SUM ]("https://help.ubuntu.com/community/HowToMD5SUM")the iso you downloaded.
If that checks out check CD for defects on boot.
Maybe try a new CD and burn at 4x - no faster.
[Boot Options]("https://help.ubuntu.com/community/BootOptions") - try safe graphic mode.

---

### Post by gdoc on 2009-08-06
I checked the iso  I downloaded using md5sun and the hashes matched. I'm going to burn a new disk with a slower speed. The slowest my laptop can burn is x10 so I'll use someone else's and try to burn at x4.


*lg notebook E500-J.AP51B can't be booted unless C-state is disabled or the boot option of "nolapic_timer" is added.*

How would one go about disabling c-state? When the laptop was booting I pressed F2 and got to the setup screen but I could not see any option for disabling C-state or adding 'nolapic timer'.

Thanks for all your help,
G

---

### Post by om26er on 2009-08-06
u may want to try to install from a usb using unetbootin. that would perhaps work for u

---

### Post by tripolitan on 2009-08-09
look for boot options, if the option is not in the list, type it.

---

### Post by gdoc on 2009-08-12
Thanks tripolitan,
It worked straight away! I inserted the live cd, pressed F6, typed nolapic_timer & then booted as normal. Worked a treat. Ubuntu is installed and everything is working great.

Thanks everybody for the advice & assistance,

G

---

### Post by tripolitan on 2009-08-12
Great! now all you have to do is remember this for the next time you install any linux version on your laptop. Thanks for the feedback.

---

