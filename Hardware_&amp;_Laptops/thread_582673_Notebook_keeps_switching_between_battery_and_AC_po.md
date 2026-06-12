---
title: "Notebook keeps switching between battery and AC power"
date: 2007-10-20
forum: Hardware &amp; Laptops
---

### Post by kanabiis on 2007-10-20
I have recently installed Gutsy on an MSI MS-1719 Notebook [http://www.msicomputer.com/NB/product_spec.asp?model=MS-1719](http://www.msicomputer.com/NB/product_spec.asp?model=MS-1719)

Based on the Intel PM965 + ICH-8M chipset. 

What is happening is, periodically the system will switch from  AC power to battery power
then back to AC power. 

I cant seem to find out why this is happening (this is my first Ubuntu install) and limited 
Linux experience, so I'm having difficulties troubleshooting. 

So far the only fix seems to be removing the battery while on AC power. 

Can anyone help me out?

---

### Post by kanabiis on 2007-10-20
I still have not found a solution to this, I have even tried a different power management package.

---

### Post by tweekville on 2007-10-24
Hey,

I'm having the same issue.  I've just upgraded from feisty to gusty.  I've gone through some of the different options and i'm not sure what to do.  I have win xp dual booted and i don't have the issue there and it never happened in feisty, so I'm pretty sure it's something with Gusty.

If anyone knows anything please do tell.

Tweekville

---

### Post by Dmtalon on 2007-10-24
search around guys... while there isn't a solution, be aware that it's happening to a few of us.  I have an MSI based laptop also and am having the same problems.  Since there's at least three here posting about it I'm fairly confident it's not a hardware problem on any one of our laptops.

My thread from yesterday:
[http://ubuntuforums.org/showthread.php?t=588790](http://ubuntuforums.org/showthread.php?t=588790)

---

### Post by RurouniJ on 2007-11-06
Same issue, MSI G-series Laptop with Intel CPU. 

Anyone had any luck? Don't want to go back to Feisty since I like the install on encryped drives that Gutsy offers.

---

### Post by ravenon on 2007-11-06
This may be an Intel thing. I have an MSI 1029 with ATI chipset and graphics card and experience none of this.

---

### Post by Dmtalon on 2007-11-06
My laptop still switches between battery/AC on the battery icon, however setting up the "on AC" to the brightness I want, and the "On Battery" to no dim the display has at least stopped the annoying switching of the brightness, and  I no longer get the little onscreen display of the display change.

Makes this "issue" a lot less annoying

---

### Post by RurouniJ on 2007-11-06
I am getting the random switching even when not plugged in, the icon on the power manager shows the battery at about 75% but if I hover the mouse the expanded tooltip says I am at 0%.

Methinks something s is totally buggered here.

---

### Post by RurouniJ on 2007-11-07
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/160726](https://bugs.launchpad.net/ubuntu/+bug/160726) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Official bug raised at: [https://bugs.launchpad.net/ubuntu/+bug/160726](https://bugs.launchpad.net/ubuntu/+bug/160726)

I encourage anyone else with this issue to add their laptops to the (K)Ubuntu device database and add their submission ID and symptoms to that bug.

---

### Post by cymetrx on 2007-12-08
I don't think this is an OS issue at all, because it happens right at the begining of the boot, in the bios phase.  And it also happens in windows xp.

---

