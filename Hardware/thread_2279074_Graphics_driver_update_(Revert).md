---
title: "Graphics driver update (Revert)?"
date: 2015-05-20
forum: Hardware
---

### Post by ironhoof on 2015-05-20
Version 14.04.2
First an explanation: I normally install my AMD/ATI   with the static driver from 'proprietary drivers'. that doesn't get  updated. The driver I was using worked with all the software I was using  including Second Life. I accidently clicked ATI/Updates this time and it gave me a graphics driver update.

This  provided very undesireable results. In Second Life including making  EVERYONE invisible if they are mesh due to a change with the new AMD/ATI  driver I was given. (this is a well known on the windows version of  these later drivers as well.)

The only solution to this is to  roll back the driver:  (The package I had I dug through the entire night  was able to get some details.)

This is the tail end of the package update: (Thankfully i found it.)

My card:
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] BeaverCreek [Radeon HD 6530D]

The update I got May 19, 2015:
Start-Date: 2015-05-19  09:51:19
Commandline: aptdaemon role='role-commit-packages' sender=':1.74'
Install: fglrx-updates-core:amd64 (15.200-0ubuntu0.3)
Upgrade:  fglrx-updates:amd64 (13.350.1-0ubuntu2, 15.200-0ubuntu0.3),  thunderbird-locale-en-us:amd64 (31.6.0+build1-0ubuntu0.14.04.1,  31.7.0+build1-0ubuntu0.14.04.1), thunderbird:amd64  (31.6.0+build1-0ubuntu0.14.04.1, 31.7.0+build1-0ubuntu0.14.04.1),  fglrx-amdcccle-updates:amd64 (13.350.1-0ubuntu2, 15.200-0ubuntu0.3),  thunderbird-locale-en:amd64 (31.6.0+build1-0ubuntu0.14.04.1,  31.7.0+build1-0ubuntu0.14.04.1)

The new driver I was updated to (15.200-0ubuntu0.3 -im geussing this is related to the new one.- ):
Driver 3.35.1005-140312a-169199E
@D Driver: 15.20.2
Catalyst 2.21
RandR 1.3

Previous driver desired is unkown I would have wrritten it down but im assuming from (13.350.1-0ubuntu2)
Driver: ????
ect
ect.

Anyway  this breaks a lot and I was hoping to get the older driver back trying  to purge and reinstall just installs the new one again with the  problem...

Is there anyway to get the old driver back?

---

### Post by dino99 on 2015-05-21
you can download, and then install with 'sudo dpkg -i packagename', the working driver you was using. Better to purge to wrong one first (sudo apt-get purge fglrx*)
[https://launchpad.net/ubuntu/+source/fglrx-installer](https://launchpad.net/ubuntu/+source/fglrx-installer)

---

### Post by ironhoof on 2015-05-21
Wow, that was only two packages that wasn't even hard... I feel a bit silly now. Thanks a million it all works again.

I filled in the driver version incase anyone else needs it (never know).
Driver:15.20.1013-150227a-180955E-ATI
2D 13.35.5
Catalyst: 2.20
RandR 1.3

---

### Post by Bashing-om on 2015-05-21
ironhoof; Outstanding !

You do good work, and a good service to provide the solution.
> 
wasn't even hard... I feel a bit silly now. 


When we do not know - we do not know. I am the one ( from your IRC request ) that now feels the silliest.
Thanks dino99 ; That void is now filled.

[INDENT][INDENT]all a process of learning
[/INDENT][/INDENT]

---

### Post by ironhoof on 2015-05-21
Bashing-om: Well you did give it your best shot! I still appreciate you taking the time you did! Now we both know for future reference*

---

