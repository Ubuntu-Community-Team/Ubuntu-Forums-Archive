---
title: "Bad sectors reported at the end of installing Ubuntu 10.04.2"
date: 2011-07-02
forum: Hardware
---

### Post by bombicri on 2011-07-02
I have a laptop Amilo Pro 2035.
Till now there was installed WindosXP and it was running without any problem.
I decided to install Ubuntu 10.04.2 LTS.
After finishing installation, before restart, appeared a long list of bad sectors.
To see what is happening I run Disk Utility and it showed a healthy disk, without bad sectors, but trying to install OpenERP 6.0 I had a lot of problems like loosing connection between server and client. Also printing on a network printer is impossible because of some bad sectors.
How can I get rid of this situation? I think that "bad sectors" is completely untrue.

---

### Post by in-dust-rial on 2011-07-02
hey there,

on establishing bad-blocks:
when i had bad-blocks I added them to the bad-block list
something like:
[HTML]e2fsck -c DEVICE[/HTML]
I think that problems that remain should not be due to bad-blocks...
also
I remember I was validating my bad-blocks by the HD-streaming speed. (I cannot remember what command revealed the reading speed ... 'lsof' maybe?)
but very slow reading speeds can result in time-outs. try to increase the time-out threshold maybe?

maybe try to put a live-cd on a USB stick and to scan from another linux-distribution version to reinforce ubuntus findings.

also SOME older laptops hat a special disc-geometry, which would only work with preinstalled windows. 
maybe you should search on the web for known disc-geometry issues with your model.
(had such problems with a acer travelmate, ... and acer laptops were partly produced by the same manufacturer as medion laptops.)


good luck!

---

### Post by bombicri on 2011-07-03
Thank you for advice.
I applied "Darik's Boot and Nuke" in automatic mode.
After 3 passes there where no errors and the installation of Ubuntu 10.04.2 was without any problem, all the bad sectors disappeared.
Printing is now without any problem.
Now I finished also the installation of OpenERP and all is going well.
This "Darik's Boot and Nuke" is a miracle for me.
It was a good idea not to listen to all the advises saying that the HDD is dying and must be replaced. In fact the HDD is in good shape and the alarms about a lot of bad sectors where false.
Thanks to all.

---

### Post by psusi on 2011-07-03
Open the disk utility and check the SMART status of the drive.  It is possible that you did have a number of bad sectors that have now been reallocated from the spare pool.  If that is the case, it is not a good sign for the drive.  It might be ok for now, but often once bad sectors start developing, they keep getting worse.  Depending on how many are there, you may want to replace the drive, especially if it is still under warranty.

---

### Post by bombicri on 2011-07-04
Psusi,
Just run self-test and the result in "Disk is healthy". Looking to the "Reallocated Sector count" the results are:
- normalized: 100
- worst: 100
- threshold: 24
- value: 0 sectors

I think that I have not to worry about disk failing.
Do you think that is something wrong?

---

### Post by psusi on 2011-07-04
That looks good.  It should be fine then.

---

### Post by bombicri on 2011-07-04
Psusi,
So, if you agree that it is fine, my conclusion is that Ubuntu 10.04 is frightening people with the resolution "bad sectors". Moreover I googled for what can be the solving for such a strange situation when my computer was very healthy with Windows and, instantly, after installing Ubuntu I found out that my HDD is dying ... and all sites and forums are saying the same ... "back-up your data and run for buying another HDD". But for me, a newbi in Ubuntu world, the facts where not logically connected and this is why I asked help and other opinions and learned about testing HDD in Ubuntu and tried to do everything possible before buying another HDD which, without understanding what is happening, could became, in short time, again full with bad sectors asking to be replaced.
I have to thank again to you and to all.
This forum is a forum of friends.

---

### Post by bombicri on 2011-07-04
By the way, my Amilo Pro V2045 was bought 9 years ago :-)

---

