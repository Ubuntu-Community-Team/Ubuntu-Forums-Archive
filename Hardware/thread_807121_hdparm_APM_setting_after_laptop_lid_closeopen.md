---
title: "hdparm APM setting after laptop lid close/open"
date: 2008-05-25
forum: Hardware
---

### Post by csete on 2008-05-25
I'm trying to avoid the load cycles issue on my hard drive.  I have a Dell E1505 with an aggressive APM BIOS that I want to set the hdparm APM setting much higher than the default value of 128.  I cannot seem to get that to happen when closing and opening the lid of the laptop.  It does not matter what the value is for the APM setting when closing the lid, it is always set to 128 when I open it again.  I've hacked every location I can find in the /etc/* tree that refers to hdparm and set the value to 200 or greater.  Unfortunately, I still can't find a change that will work for setting that value.

Can anyone help me out?  Is there any way that I can hook the hdparm command so that I can see the caller of that command?  Does anyone know the correct commands to hook?

Thanks for any help,
Craig

---

