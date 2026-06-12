---
title: "[SOLVED] New ubuntu user, help?"
date: 2008-10-19
forum: General Help
---

### Post by Tictoon on 2008-10-19
Hey, while trying to remove ubuntu, something went horribly wrong and I'm stuck with it. Ironic, isn't it?

so now 
I need to get some things working: my HP Color LaserJet CP1215 printer, my Dymo Label Printer, and my microsoft Lifecam

how can I do this??

---

### Post by CloudFX on 2008-10-19
Hi,

Is your intention still to remove Ubuntu, and replace it with another operating system, or have you decided now to continue using Ubuntu?

---

### Post by hansdown on 2008-10-19
Hi Tictoon.

As far as the printer goes, click on system> administration> snaptic package manager.

Enter your password, search for hplip, and xane.

Install these, turn on the printer, and you should be good to go.

---

### Post by Tictoon on 2008-10-20
well yea, I've decided to use Ubuntu for now.

I can't find a xane package, the search brings up now results, and theres tons of ones for hplip, but the one thats only hplip already has the green square.

EDIT: I found the problem, its using the wrong driver. It thinks the printer is a CP3505, now what?

---

### Post by Tictoon on 2008-10-20
Bump

---

### Post by Tictoon on 2008-10-21
Can anyone help me?

kinda before this thread denies its existence!

---

### Post by hansdown on 2008-10-21
Hi tictoon. My appologies. That should have read xsane.

I checked this site [https://answers.launchpad.net/hplip/+question/45898](https://answers.launchpad.net/hplip/+question/45898)

And it doesn't look promising for this printer.

If you start a new thread, someone here may be able to help recover your microsoft install. I'm not too skilled with that stuff.

---

### Post by Tictoon on 2008-10-21
*dies inside*

---

### Post by MasterNetra on 2008-10-21
Try just using the HP Laserjet driver. The basic one with no model number after it. Maybe HP Laserjet 2 or 3.

---

### Post by Tictoon on 2008-10-21
Ok I just tried that, it doesn't work, please people help me out!! otherwise I'm going to have to switch back to vista

---

### Post by CloudFX on 2008-10-22
You will probably get better help from a section relating more specifically to printing, such as the hardware one. 

[http://ubuntuforums.org/forumdisplay.php?f=332](http://ubuntuforums.org/forumdisplay.php?f=332)

---

### Post by sparvik on 2008-10-22
Did you botch your recovery drive on your Vista install?

If it comes down to it with the printer you might try searching for a driver wrapper. I know they have them for Wifi cards but I think there is also one for printer drivers as well.
Maybe, not sure but this link might help
[http://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html]("http://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html")

Sorry that link was probaly of no help but after I google'd your printer and linux drivers I found a page that looks more promising. 
[http://foo2hp.rkkda.com/]("http://foo2hp.rkkda.com/")
This one claims to have a working driver.

---

### Post by steveydoteu on 2008-10-22
> **hansdown said:**
> **[COLOR="RoyalBlue"]If you start a new thread, someone here may be able to help recover your microsoft install.[/COLOR]**

What exactly happened when you tried to remove Ubuntu?

In fact *how* did you try and do so.

> **hansdown said:**
> Hi Tictoon.

search for hplip, and xane.



hplip and xsane are both installed by default, way to go.

---

### Post by hyper_ch on 2008-10-22
It is adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;) 

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse brackets around (each) output. That makes it also easier to read.

---

### Post by hansdown on 2008-10-22
> **steveydoteu said:**
> What exactly happened when you tried to remove Ubuntu?

In fact *how* did you try and do so.



hplip and xsane are both installed by default, way to go.



Could you please provide documentation for your last statement?

I'd like to be the first forum member to thank you.

---

### Post by Crossyboi on 2008-10-22
Does this website help in anyway? 
It says something about supporting your printer

[http://foo2hp.rkkda.com/]("http://foo2hp.rkkda.com/")

---

### Post by hansdown on 2008-10-22
Thanks for doing what this forum is intended for Crossyboi.

---

### Post by Tictoon on 2008-10-23
Ok,I'll rename this thread to printer problems, and if that site doesn't work I'll start a new thread in the hardware forums3

EDIT: I can't do that so I'll keep that in mind for next time, thanks everyone for looking in this thread!

DOUBLE EDIT< THANK YOU< I FIXED MY PRINTER!!! I love you!!! (like a brother)

---

### Post by steveydoteu on 2008-10-23
> **hansdown said:**
> Thanks for doing what this forum is intended for Crossyboi.


I may not have posted a link but you may note I was asking the original poster how they got into the situation in the first place prior to pointing out about xsane and hplip. Hostility is not exactly going to help is it. I suggest winding your neck in a little. 

Take a quick look on your graphics menu and you will find xsane, and head into synaptic and search for hplip, it is there, installed also.

---

### Post by steveydoteu on 2008-10-23
> **Tictoon said:**
> Ok,I'll rename this thread to printer problems, and if that site doesn't work I'll start a new thread in the hardware forums3

EDIT: I can't do that so I'll keep that in mind for next time, thanks everyone for looking in this thread!

DOUBLE EDIT< THANK YOU< I FIXED MY PRINTER!!! I love you!!! (like a brother)

On your thread tools menu, mark this as solved once you are certain everything is a-ok :)

---

### Post by Tictoon on 2008-10-23
Thanks for your help everyone, I'm gonna start new threads for my problems

---

### Post by Crossyboi on 2008-10-23
> **hansdown said:**
> Thanks for doing what this forum is intended for Crossyboi.

No Problem :-) 

Thats what im here for

---

