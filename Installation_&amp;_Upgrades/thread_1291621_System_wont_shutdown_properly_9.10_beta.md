---
title: "System wont shutdown properly 9.10 beta"
date: 2009-10-14
forum: Installation &amp; Upgrades
---

### Post by Lancelotet on 2009-10-14
so im dual booting windows vista/ubuntu 9.04. Im very new to the ubuntu side of the tracks and since the install i have been overly impressed and just down right excited about everything ubuntu is and stands for! well any way i thought maybe i had a handle on most stuff so like anyone else i saw the new update 9.10beta and got excited and upgraded to it. Works fine as 9.04 did but when i go to restart of shutdown it gets to the "de-boot screen" and says asking to kill all processes yada yada yada then says deactivating swap and then says something about loop i/o then a series of numbers. anybody else had this problem. ran a chkdsk on windows and everything was fine saw an error of similar magnitude in a post but it was referring to ubuntu 7.xx something or other. any answers would be wonderful!!

---

### Post by kumar8O on 2009-10-16
I have been getting same error.It has to do with Ext3. if you figure it out please let me know thank you

---

### Post by knitin777 on 2009-10-16
I am also sailing same boat. I guess this is beta bug, may they will come up with patch soon.

---

### Post by kalyogi on 2009-10-16
I had the same issue. I forced to shut down and restarted it. it all fine now.

---

### Post by KitsuneDragon on 2009-10-18
It seems I have the same problem and it is quite annoying since at one point I forced it shut-down and when I booted next time my Desktop icons were corrupt....
Does anyone know if there's a fix/patch or if there is a bug report filed about this
if a bug report has not been filed how would I file one at Launchpad?
Thanks for any help because I think that there are more people suffering from this problem than us...

---

### Post by AliTabuger7 on 2009-10-18
I thought it had something to do with being a wubi install, so made an actual swap partition and changed the fstab. Didn't fix it.

I think it might have something to do with having a "failing" hard disk. The new version of ubuntu warned me that SMART says the hard disk is pre-fail in the number of re-allocated sectors.

---

### Post by Lancelotet on 2009-10-20
well first of all it sucks but im glad to see that im not the only one with that problem! i really think its gotta be a bug that just hasnt been hashed out yet. that doesnt bother me! but to have it working perfectly with 9.04 then have this problem kinda pisses me off! but i have faith in the ubuntu cru so ill just wait it out and force shut down! thanks again!

---

### Post by Terrycymru on 2009-11-09
Why is this bug marked as solved when there are several threads all reporting the same problem with 9.10 final?

---

### Post by skyiscrying on 2009-11-09
It shuts down ok when you install the final version. Get that from Ubuntu's main web page. Karmic would not shut down the computer when I was using the beta version. I had upgraded from Jaunty and things did go screwy for a while until I did a clean install.

---

