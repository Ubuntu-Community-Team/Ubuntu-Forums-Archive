---
title: "please help! new to linux"
date: 2006-08-03
forum: Hardware &amp; Laptops
---

### Post by newlinuxusr on 2006-08-03
I'm new to ubuntu and the whole linux thing. I've been using ubuntu for about a week now and decided to try to install aiglx. I am using a 945gm intel express graphics card on my dell inspiron e1405 laptop. I figured out that i needed to use a i810 driver for the graphics card instead of the vesa driver. I can not figure out how to change the driver from vesa to i810. I have the i810 installed as a package in the synaptics package mananger. please help me with this issue.

thanks

---

### Post by E-werd on 2006-08-03
Open a terminal (Applications->Accessories->Terminal) and type in:

sudo gedit /etc/X11/xorg.conf

Scroll down to the "Device" section.  Where you see "Driver" in that section, change "vesa" to "i810"


That should work for you.  Here is some definition of that for you.

The command "sudo" allows you to run a program as a superuser, with all privelages possible.

"gedit" is the default text editor under GNOME desktop.

And... /etc/X11/xorg.conf is your X.Org configuration file.



Happy Ubuntu-ing. :p

---

### Post by newlinuxusr on 2006-08-03
i should have mentioned this in my original post but i did tryed that and it didnt work. if i do that and start up x it just comes up with a blue screen that says something like x is not configured properly and it cant find a screen or something and i end up using the command prompt to change it back to vesa.

---

### Post by newlinuxusr on 2006-08-03
bump

---

### Post by Buffalo Soldier on 2006-08-03
[list=1]
[*] Not my intention to demoralize, or discourage you from trying AIGLX, XGL or any other eye candy, or to be an elitist. But, I think as a beginner to GNU/Linux you should be getting comfortable with the more fundamentals skills first. Understanding the file system, knowing the essential command in terminal.

[*] But hey, it's a free and liberal OS :) So, let's see what we can do to help you with your problem here. Have you tried using the **i910** driver? I think the i810 driver is for the lowly integrated Intel graphic such as my 855GM. For those 9XX graphic cards such as 945, I think you need to use the i910 driver.

[*] Try not to bump your thread too frequently and too often. It *may* be perceived as something rude. Sometimes even when people know the solution to the problem, they will avoid answering just because of that.

[*] Lastly, welcome to Ubuntu :)
[/list]

---

### Post by Buffalo Soldier on 2006-08-03
[list=1]
[*] Not my intention to demoralize, or discourage you from trying AIGLX, XGL or any other eye candy, or to be an elitist. But, I think as a beginner to GNU/Linux you should be getting comfortable with the more fundamentals skills first. Understanding the file system, knowing the essential command in terminal.

[*] But hey, it's a free and liberal OS :) So, let's see what we can do to help you with your problem here. Have you tried using the **i910** driver? I think the i810 driver is for the lowly integrated Intel graphic such as my 855GM. For those 9XX graphic cards such as 945, I think you need to use the i910 driver.

[/list]

---

### Post by wylfing on 2006-08-03
> **Buffalo Soldier said:**
> Not my intention to demoralize, or discourage you from trying AIGLX, XGL or any other eye candy, or to be an elitist. But, I think as a beginner to GNU/Linux you should be getting comfortable with the more fundamentals skills first. Understanding the file system, knowing the essential command in terminal.


Urgh, sorry to follow you on multiple threads, Buffalo Soldier! You're spot on here. **newlinuxusr**, please get used to everything else about Linux first and let graphics-accelerated desktops happen on their own time. Eventually this kind of hypercool desktop experience will merge into the mainstream and it will just appear for you. Don't try to force it early unless you are an elite poweruser.

---

### Post by newlinuxusr on 2006-08-03
> **Buffalo Soldier said:**
> [list=1]
[*] Not my intention to demoralize, or discourage you from trying AIGLX, XGL or any other eye candy, or to be an elitist. But, I think as a beginner to GNU/Linux you should be getting comfortable with the more fundamentals skills first. Understanding the file system, knowing the essential command in terminal.

[*] But hey, it's a free and liberal OS :) So, let's see what we can do to help you with your problem here. Have you tried using the **i910** driver? I think the i810 driver is for the lowly integrated Intel graphic such as my 855GM. For those 9XX graphic cards such as 945, I think you need to use the i910 driver.

[*] Try not to bump your thread too frequently and too often. It *may* be perceived as something rude. Sometimes even when people know the solution to the problem, they will avoid answering just because of that.

[*] Lastly, welcome to Ubuntu :)
[/list]

i tried the i910 driver, it gives me an error on startup about x that says driver not found. i also tried putting in i915 as a driver and the same thing happend. I have 915resolution installed. i am pretty sure that in the descreption of the i810 driver that it works for i945 series intel chips. when i put in i810 in as a driver instead of linux it wont start and i just get a X error. please help this is very frustrating.

thanks

---

### Post by bensexson on 2006-08-03
Take a look at your /var/log/Xorg.0.log file.  This should hopefully give an indication of the trouble.

---

### Post by newlinuxusr on 2006-08-03
> **bensexson said:**
> Take a look at your /var/log/Xorg.0.log file.  This should hopefully give an indication of the trouble.

the Xorg.0.log file tells me this but i dont know what to make of it:

(EE) I810(0): No Video BIOS modes for chosen depth.
(II) UnloadModule: "i810"
(II) UnloadModule: "ddc"
(II) UnloadModule: "int10"
(II) UnloadModule: "int10"
(II) UnloadModule: "vgahw"
(II) Unloading /usr/lib/xorg/modules/libvgahw.so
(II) UnloadModule: "vbe"
(II) UnloadModule: "int10"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

thanks for all the help!

---

### Post by bensexson on 2006-08-04
It looks like the xorg config only has video modes that are not supported by the adapter.  You may want to search on the forum and Wiki and Google for other people who have your setup and what they are using for modlines.

---

