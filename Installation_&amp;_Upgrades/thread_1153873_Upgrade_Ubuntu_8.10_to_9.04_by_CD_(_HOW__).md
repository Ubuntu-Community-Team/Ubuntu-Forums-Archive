---
title: "Upgrade Ubuntu 8.10 to 9.04 by CD ( HOW ? )"
date: 2009-05-09
forum: Installation &amp; Upgrades
---

### Post by Gabtevez on 2009-05-09
[B]Hi 

I want to upgrade my Ubuntu (Ubuntu 8.10) to new Ubuntu version 9.04. 

But I don't want to do it by internet, I want to upgrade it by the CD of ubuntu 9.04.

I do this method but isn't work : [/B]

> **Upgrading Using the Alternate CD/DVD**

  
 Use this method if the system being upgraded is not connected to the Internet. 
 
[LIST=1]
[*] Download the **alternate** installation CD
[*] [Burn the ISO to a CD]("https://help.ubuntu.com/community/BurningIsoHowto#InUbuntu") and insert it into the CD-ROM drive of the computer to be upgraded.
[LIST]
[*] If the ISO file is on the computer to be upgraded, you could avoid wasting a CD by [mounting the ISO as a drive]("https://help.ubuntu.com/community/ManageDiscImages#MountISOFiles") with a command like: 
 sudo mount -o loop ~/Desktop/ubuntu-9.04-alternate-i386.iso /media/cdrom0
[/LIST]
 
[*]A dialog will be displayed offering you the opportunity to upgrade using that CD.
[*]Follow the on-screen instructions.
[/LIST]
 If the upgrade dialog is not displayed for any reason, you may also run the following command using Alt+F2: 
 gksu "sh /cdrom/cdromupgrade" 
 Or in Kubuntu run the following command using Alt+F2: 
 kdesudo "sh /cdrom/cdromupgrade"**Anybody can help me please !! **

---

### Post by hw-tph on 2009-05-09
So what's the problem? Do you get any error messages? If so, please post them. You don't give us much indication of what you've actually done or what problems you have encountered so it's really not very easy to help you.

---

### Post by Gabtevez on 2009-05-09
> **hw-tph said:**
> So what's the problem? Do you get any error messages? If so, please post them. You don't give us much indication of what you've actually done or what problems you have encountered so it's really not very easy to help you.

Hi, Thanks for your reply

When I mount the CD I have this message : 

> This medium contains software intended to be automatically started. Would you like to run it? 

When I click on run, This message apear : 

> Error autorunning software
Cannot find the autorun program

Then I try 

> sh /cdrom/cdromupgrade

but nothing happen !!

---

### Post by drs305 on 2009-05-09
If you think it may be a CD burning problem, this is a good guide from the ubuntu documentation:
[https://help.ubuntu.com/community/BurningIsoHowto]("https://help.ubuntu.com/community/BurningIsoHowto")

If the alternate CD has an option to check the disk for integrity, did you try running that process?

---

### Post by DLG102282 on 2009-05-09
> **drs305 said:**
> If you think it may be a CD burning problem, this is a good guide from the ubuntu documentation:
[https://help.ubuntu.com/community/BurningIsoHowto]("https://help.ubuntu.com/community/BurningIsoHowto")

If the alternate CD has an option to check the disk for integrity, did you try running that process?
Sounds like you have a bad bur did you burn at the slowest speed?

---

### Post by ethan brand on 2009-05-09
Um... I think Gab is simply mounting the iso so it's not a burning problem.

Ok,

After you mount the iso, check that it's mounted properly. Go into your /cdrom/ directory and verify the iso file is splayed out in there.

sh /cdrom/cdromupgrade --- this should do it after that.

What messages exactly do you get when you type the above?

---

### Post by Gabtevez on 2009-05-09
> **ethan brand said:**
> Um... I think Gab is simply mounting the iso so it's not a burning problem.
 
Ok,
 
After you mount the iso, check that it's mounted properly. Go into your /cdrom/ directory and verify the iso file is splayed out in there.
 
sh /cdrom/cdromupgrade --- this should do it after that.
 
What messages exactly do you get when you type the above?
 
Hi 
 
after I do this "sh /cdrom/cdromupgrade"
 
nothing happen and no message apear !!
 
I think I will install Ubuntu 9.10 on the old without upgrade ....

---

