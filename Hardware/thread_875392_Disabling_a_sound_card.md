---
title: "Disabling a sound card"
date: 2008-07-30
forum: Hardware
---

### Post by xd397 on 2008-07-30
I need to disable my internal sound card I have a vai8237 sound card built in and i want to use my sound blaster live instead I tried to disable the built in with the Bios but ubuntu still detected it and is running the via instead and i need to know how to disable or move default off the via

---

### Post by markbuntu on 2008-07-31
Are you shure you turned it off in the bios?
You should check.

---

### Post by prshah on 2008-07-31
> **xd397 said:**
> I need to disable my internal sound card I have a vai8237 sound card built in and i want to use my sound blaster live instead I tried to disable the built in with the Bios but ubuntu still detected it and is running the via instead and i need to know how to disable or move default off the via

You can either

1) Click on System-Preferences-Sound and change the default devices to your soundblaster live

== OR ==

2) blacklist the relevant via module in your "/etc/modprobe.d/blacklist" file to prevent the via module from loading.

---

### Post by xd397 on 2008-08-01
> **prshah said:**
> You can either

1) Click on System-Preferences-Sound and change the default devices to your soundblaster live

== OR ==

2) blacklist the relevant via module in your "/etc/modprobe.d/blacklist" file to prevent the via module from loading.

How can i do the second one

---

### Post by prshah on 2008-08-01
> **xd397 said:**
> How can i do the second one

OK, I'm giving the instructions, but they're not absolute, you need to think a bit before running any commands.

I'd really, really suggest that you check the BIOS settings as the previous poster has mentioned, and/or use method 1.

==  method 2

Open a terminal (Applications-Accessories-Terminal)

1) locate the correct module name for your via sound card by studying the output of: Either```
lsmod | grep -i snd
``` or ```
lsmod | grep -i via
```

2) edit the blacklist file: ```
sudo gedit /etc/modprobe.d/blacklist
```

3) Add the below phrase to the end of the file (last line) ```
blacklist via8237
``` replace via8237 with the actual module name as found from the first two commands.

4) Save, and close the file.

5) You need to reboot for changes to take effect.

Post back with relevant outputs if you run into any trouble.

---

