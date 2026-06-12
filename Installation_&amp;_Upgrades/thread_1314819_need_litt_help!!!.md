---
title: "need litt help!!!"
date: 2009-11-04
forum: Installation &amp; Upgrades
---

### Post by shahxaibhaq on 2009-11-04
[B]hi,
i am totally new to ubuntu *to be honest*
the prob is__yesterday i installed kubuntu 9.10 through wubi
the installation was fine like hell but after reboot,dont know what exactly happened nd my comp stuck at some thing like "initramfs"

i took some screen shots which are attached
[/B]**pls help me**

---

### Post by jjcv on 2009-11-04
If you leave the Ubuntu CD in the DVD drive when you boot up (but boot from the hard disk) does it then start?

It seems to be looking for you CD, so I am guessing the install never finished properly.

---

### Post by muscularsage on 2009-11-05
am not sure but i guess one of frinds got it when h did not copy the cd properly..are u sure the cd writing process was fine?

---

### Post by shahxaibhaq on 2009-11-05
> am not sure but i guess one of frinds got it when h did not copy the cd properly..are u sure the cd writing process was fine?

yes i am sure the writing process was fine_(flawless) _i did process at the least speed too....
what exactly can goes wrong
for the safe side!!!!before the burn cd,i chked the md5__it wasn't corrupt at all

i tried to install wubi through cd and through hard disk also (i found this suggestion in this forum to run it successfully)
but it doesn't worked for me

what should i do with initramfs???

---

### Post by shahxaibhaq on 2009-11-05
can any one assist me????

---

### Post by shahxaibhaq on 2009-11-05
> **jjcv said:**
> If you leave the Ubuntu CD in the DVD drive when you boot up (but boot from the hard disk) does it then start?

It seems to be looking for you CD, so I am guessing the install never finished properly.

yah tried to boot from the hard disk....
it directly took me to xp
strange!!!

any suggestion???

---

### Post by shahxaibhaq on 2009-11-07
Bingo!!!!!!!!!!

pls help me out

---

### Post by xtremesupremacy3 on 2009-11-07
As pointed out above, it is looking for your ISO.
My guess here is that either there was a problem with installing, or that it wasn't 100% finished.

My advice would be to log in to windows, go to the control center, add/remove (Programs in Vista), and uninstall Ubuntu, and then use wubi to start again, this time making 100% sure its finished.

---

### Post by shahxaibhaq on 2009-11-07
> **xtremesupremacy3 said:**
> As pointed out above, it is looking for your ISO.
My guess here is that either there was a problem with installing, or that it wasn't 100% finished.

My advice would be to log in to windows, go to the control center, add/remove (Programs in Vista), and uninstall Ubuntu, and then use wubi to start again, this time making 100% sure its finished.

yah i did it as you said,i uninstalled ubuntu nd reinstall it 
again,at the end one pop up came up....
reboot now 
or reboot manually

i chose reboot!!!
the same weird problem occurred :mad:

*frustrating*!!!!!!!

---

### Post by shahxaibhaq on 2009-11-11
Bump!!!!!!

---

### Post by Swagman on 2009-11-11
That sounds like windows has suffered a dirty shutdown

ie: a crash or power down.

Just so you know... When windows is in use it sets a flag on the hard drive that it's "In USE". When windows is shutdown correctly the flag is "Unset".

What this means is... If a dirty shutdown has occured the flag will still be set to on... Meaning nothing else can access it until windows reboots and fix disk is run.

My advice to you would be to uninstall kubuntu... run disk check.. reboot.. and then try to reinstall. oh.. if you can then it's better to install to a different partition than c:\

---

