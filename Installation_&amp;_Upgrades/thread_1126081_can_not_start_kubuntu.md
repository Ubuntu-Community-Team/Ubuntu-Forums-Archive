---
title: "can not start kubuntu"
date: 2009-04-15
forum: Installation &amp; Upgrades
---

### Post by aknight_sa on 2009-04-15
i have tried to upgrade my kubuntu 8.04 to 9.04 yesterday, and during the process it told me that the display driver i am using for my ATI card is not available on 9.04 and asked if want to cancel which i did..

but after a while i shut down my laptop (Dell Vostro 1000) and when i start it up later on KDE stopped working..
i get to the login screen and after providing my password i get the message:

> 
The following installation problem was detected
while trying to start KDE
      No Write Access to $HOME directory (/home/abdullah)

KDE is unable to start


and after pressing OK
i get the message

> 
Could not start ksmserver, check your installation.


---

### Post by aknight_sa on 2009-04-15
ok.. i got it solved by loggin in to konsol mode and using the command

chown -R abdullah /home/abdullah

thanks

---

