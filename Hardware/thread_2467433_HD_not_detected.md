---
title: "HD not detected"
date: 2021-09-26
forum: Hardware
---

### Post by tjerram on 2021-09-26
This is very strange a few weeks ago my odroid server stopped seeing the attached HD.  I thought it was a drive problem so I tried the drive in another odriod server and it worked fine.  I then thought it was a hardware problem with the first odroid so I used another sd card with a new version of ubuntu it works and saw the HD.  I then tried a different HD in the 1st odroid using the original HD (that stopped working) and it also worked.  So my conclusion is that there is a problem with the original boot sd ubuntu installation.  My question is there any way to figure out and fix the original installation without starting all over with a new installation. I now see teh wisdom in a backup system sd card but its too late.  I don't want to try to recreated the original system.

Any help would be appreciated.

---

### Post by tea for one on 2021-09-26
> **tjerram said:**
>  I then tried a [COLOR="#0000FF"]different HD[/COLOR] in the 1st odroid using the [COLOR="#0000FF"]original HD[/COLOR] (that stopped working) and it also worked.

You lost me here..........? Different HD using original HD?

Should it be Different SD Card using Original HD?

Anyway, perhaps the SD card is faulty but the OS may be healthy.

Have you cleaned the contact strips?

Also, sometimes SD Cards can be recognised in a USB attached card reader.

Do Odroid devices boot from USB card readers?

---

### Post by tjerram on 2021-09-27
sorry it is confusing.

on the odroid (odroid1) box the original HD (call it HD1) suddenly stopped working.  I tried a different HD (call it HD2) in the odroid and it worked (same OS1 on an SD1 card)

I then tried HD1 in a different odroid (odroid2) and it worked with a different OS2  (OS2 is an old image of OS1)

HD1 works in odroid1 using OS2

I have a related (I think) problem with OS1  as when I try to update of upgrade I keep getting errors about dependency issues with samba-common it wants 2:4.116+dfsg-0ubuntu1.9 but it finds 2:4.116+dfsg-0ubuntu1.10

I have no idea how to fix this I have tried to uninstall samba and get the same dependency error
I tried to reinstall samba (with a force) same error

Ay thoughts?

---

