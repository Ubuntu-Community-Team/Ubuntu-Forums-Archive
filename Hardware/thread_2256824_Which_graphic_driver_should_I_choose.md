---
title: "Which graphic driver should I choose?"
date: 2014-12-15
forum: Hardware
---

### Post by 95kreaninw95 on 2014-12-15
Recently, AMD updated their website to provide GPU drivers for specific Ubuntu versions instead of just Linux X86 and Linux X86_64. They currently support LTS version (12.04 and 14.04).

[http://support.amd.com/en-us/download/desktop?os=Ubuntu%20x86%2064](http://support.amd.com/en-us/download/desktop?os=Ubuntu%20x86%2064)

But there are many drivers to choose from, including...

[LIST]
[*]A normal one, [COLOR=#000000][FONT=Calibri]Video Driver for Graphics Accelerators
[/FONT][/COLOR]
[*][COLOR=#000000][FONT=Calibri][/FONT][/COLOR][COLOR=#000000][FONT=Calibri]Minimal Video Driver for Graphics Accelerators (Non-X Support)[/FONT][/COLOR][COLOR=#000000][FONT=Calibri]
[/FONT][/COLOR]
[*][COLOR=#000000][FONT=Calibri][/FONT][/COLOR][COLOR=#000000][FONT=Calibri]Video Driver for Graphics Accelerators Devel Files (OGL, OCL)
[/FONT][/COLOR]
[*][COLOR=#000000][FONT=Calibri][/FONT][/COLOR][COLOR=#000000][FONT=Calibri]Catalyst Control Center[/FONT][/COLOR]
[/LIST]
[COLOR=#000000][FONT=Calibri]&#8203;
I don't know which driver I should install... And there's a bug here [/FONT][/COLOR]Bug 831 - segfault at Xorg starting from 13.4 ( [http://ati.cchtml.com/show_bug.cgi?id=831](http://ati.cchtml.com/show_bug.cgi?id=831) )[COLOR=#000000][FONT=Calibri]
[/FONT][/COLOR] which is an ongoing issue.

---

### Post by deadflowr on 2014-12-15
Is there a question?

Basically as far as Drivers for AMD cards go you have 3 options.
1)Use the open-source drivers, if your card runs them well enough. For a large chunk of users this is all they really need.

2)Use the drivers you can install through Ubuntu Additional Drivers program. They're older closed source, but are stable and get updated when the need arises.

3)Install the drivers from the AMD site. Usually really new, which can mean either better support or worse support, depending.

I think your post says it all, the AMD site has 3 options as well. A normal driver, a barebone driver, and a development(developer?) driver.
If installing from the AMD sites drivers, go with normal.

It's hard to know though since you didn't post anything about your card...

---

### Post by /ADM on 2014-12-15
If you have an older card, stick with the open source driver.  AMD are not known for supporting their older cards very well.  If it is a new card then check out the 'normal' proprietary driver.

---

### Post by Mark Phelps on 2014-12-15
To see what video chipset you have, open a terminal, enter "lspci" (without the quotes) and look for the line containing "VGA". Post that information back here.

Don't just download and force the installation of the Catalyst drivers.  That could corrupt your display and render fixing it quite difficult.

---

### Post by MartyBuntu on 2014-12-15
> **deadflowr said:**
> 

2)Use the drivers you can install through Ubuntu Additional Drivers program. They're older closed source, but are stable and get updated when the need arises.



Absolutely agreed.

Unless there's a *specific* need for the driver package from AMD themselves, I'd stick with the software center.

---

