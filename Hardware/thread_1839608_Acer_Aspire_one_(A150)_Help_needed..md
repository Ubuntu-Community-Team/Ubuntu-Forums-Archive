---
title: "Acer Aspire one (A150) Help needed."
date: 2011-09-05
forum: Hardware
---

### Post by draco2011 on 2011-09-05
I'm new to Linux, I need some help before installing Ubuntu 11.04 into my Acer aspire one (A150)

[B]1st question -

[/B]In the aspire one documentation there is something like this,


***"Add this to your /etc/rc.local to enable Acer Aspire One Fan driver fan control: ***
***echo -n "enabled" > /sys/class/thermal/thermal_zone0/mode"***

what does this mean "[B][I] enable Acer Aspire One Fan driver fan control" 
[/I][/B]and how can I add this (Please be kind enough to post step by step instructions)[B][I]

2nd question -

[/I][/B]Is swap space compulsory, and is it possible to create the swap space after the installation 

:)

---

### Post by draco2011 on 2011-09-05
Is it compasury to add this **"echo -n "enabled" > /sys/class/thermal/thermal_zone0/mod"  **

---

### Post by draco2011 on 2011-09-06
Help needed! :)

---

### Post by draco2011 on 2011-09-06
Please help! :)

---

### Post by nothingspecial on 2011-09-06
One bump every twenty four hours is the recommended amount.

Swap space is not compulsory.

Yes it can be added after installation.

Can you link to the documentation you are reading? the chances are that the fan instruction is old and no longer necessary.

---

### Post by draco2011 on 2011-09-06
Acer aspire one AOA 105

[https://help.ubuntu.com/community/AspireOne/AOA150](https://help.ubuntu.com/community/AspireOne/AOA150)

:)

---

### Post by 3rdalbum on 2011-09-06
Posted to the other thread as well.

> **draco2011 said:**
> I'm using an acer aspire one (A150)

How can I do this 

***"Add this to your /etc/rc.local to enable Acer Aspire One Fan driver fan control: ***
***echo -n "enabled" > /sys/class/thermal/thermal_zone0/mode"***

Please mention step by step instructions :)

[SIZE="3"]**READ ALL THIS.**[/SIZE]

Install Ubuntu 11.04 and see if the fan is controlled to your satisfaction. This is a netbook with an older Atom CPU, so don't expect it to be totally silent. If the fan is working okay, then you don't need to mess with anything.

If you're sure you need this thing done, then I'd suggest a trial run. Go into the terminal and run this command:

```
sudo echo -n "enabled" > /sys/class/thermal/thermal_zone0/mode
```

This will apply that setting **until you reboot** so you can check that it works safely. If your computer crashes, **DO NOT CONTINUE THE INSTRUCTIONS**.

If you find that there's an improvement and you want to be using this setting all the time, you need to open up the file /etc/rc.local as root (administrator): 

```
gksudo gedit /etc/rc.local
```

(in the terminal)

and then paste in the line "echo -n "enabled" > /sys/class/thermal/thermal_zone0/mode" (without the quote marks) on a line of its own, before the "exit 0" line. Save your changes. When you reboot, the setting will be applied at the end of the boot sequence.

---

