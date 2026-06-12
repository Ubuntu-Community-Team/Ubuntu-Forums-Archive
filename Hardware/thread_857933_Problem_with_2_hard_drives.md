---
title: "Problem with 2 hard drives"
date: 2008-07-13
forum: Hardware
---

### Post by recombinantevil on 2008-07-13
I'm not really sure WHERE in the forum to look for this, and I've only been using ubuntu or linux or anything outside of windows for about 3 days now.  I had ubuntu installed on a hard drive before then I downloaded some pretty big files to that hard drive and at one point was trying to get my video card to work right because it was messed up.  Anyway I screwed up ubuntu and couldnt even get to the log in screen.  So i installed it on another hard drive and tried to hook the other one up as a slave.  My bios recognizes it and everything but I cant get to it in ubuntu.  Any suggestions?  And thanks for taking the time to read this!

---

### Post by matt$2 on 2008-07-13
Easy as pie.
Bring up a console.  Enter 
sudo ls /dev/sd*
and also
sudo ls /dev/hd*

post the result and we'll take it from there.  You'll be very close.

---

### Post by coffeecat on 2008-07-13
Hopefully, it might even be easier than that, but as you (if I read you correctly) fitted the slave drive after you installed Ubuntu, I can't be sure. It's worth a go anyway.

Go to Places > Computer and click on that. A browser window (Nautilus) opens. If your Ubuntu is working properly it *should* show all drives and partitions, but not necessarily mounted. The design of the icon for each partition is different for mounted and unmounted ones. See if you can work out which one is the root partition for the previous Ubuntu installation on the slave drive and double-click on that. If the partition wasn't labelled it will probably show the size in the name.

---

### Post by goldnikevip on 2008-07-13
[www.goldnikevip.com](www.goldnikevip.com)
Do you want to have a comfort shoes to fit your foot?If your answer iscertainly,that please land on our website choose you feel satisfaction's product. Comehere, everyone!Don't scruple ! Our product are popular allover the world with High Quality, Competitive Price, Best Service and Safe Delivery. They are exported to US, UK , Canada , France , Italy ,Germany and many other countries.Sport shoes such as Nike Air Jordan I to XXI and Jordan Dub Zero, NikeShox (R4, R5, OZ, NZ , Turbo, TL1, TL2, TL3 ,TL4, BMW , Classic ,Monster , DE ,VC ),Nike Air max( airmax 90, 95, 97, 2003, 2004, 2005, 2006,TN , TN6),Air Force one, Dunk, James, Kobe ,Adidas , Bape , GUCCI ,ICE CREAM , Timberland , Lacoste shoes and so on.
site:[www.goldnikevip.com](www.goldnikevip.com)
msn : [email]goldnike007@hotmail.com[/email]                
yahoo: [email]goldnike@yahoo.cn[/email]

---

### Post by recombinantevil on 2008-07-13
sudo ls /dev/sd* gives me this
/dev/sda  /dev/sda1  /dev/sda2	/dev/sda5

And the hd* one says cannot access no such file or directory.  It doesnt show up in the places/computer window either

---

### Post by recombinantevil on 2008-07-13
Ahhh sorry and never mind guys.  It was my mistake, when I first hooked it up I put the jumper in the cable select possition accidentally and there was some weird error, so when I changed the jumper position the IDE cable wasnt on all the way.  Thanks for help anyway, much appreciated!

---

### Post by matt$2 on 2008-07-13
If you can, edit your initial thread an add 

[Resolved]

---

