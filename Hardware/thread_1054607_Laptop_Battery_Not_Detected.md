---
title: "Laptop Battery Not Detected?"
date: 2009-01-29
forum: Hardware
---

### Post by matthew.ball on 2009-01-29
Hi, using 8.10, the laptop tells me "no battery detected, using AC power", regardless if the laptop is actually plugged in or not (though it still runs on battery) - I'm fairly sure 8.04 detected the battery, but it didn't get the sound, wireless or video, so I'm happier with 8.10.

I have really only used this laptop plugged in, so it hasn't been a big worry, but I will be going into school next month, and I would much rather take this laptop in, then use the school computers, it would be quite annoying if I can't tell the battery power...

The laptop is an ASUS PRO50GL-AP211C, [http://www.asus.com.au/products.aspx?l1=5&l2=24&l3=477&l4=0&model=2575&modelmenu=2](http://www.asus.com.au/products.aspx?l1=5&l2=24&l3=477&l4=0&model=2575&modelmenu=2).

Edit: If it is of any use running acpi -b produces no output.
The battery is detected (it runs on battery), but I have no way of seeing it...

---

### Post by matthew.ball on 2009-02-17
Bump, just wondering if anyone knows anything about this (or perhaps a fix in 9.04?).

---

### Post by matthew.ball on 2009-04-19
Well, there's no fix in 9.04... yet :(

Any help?

---

### Post by marklar2u on 2009-07-23
Same problem, Dell Inspiron 3500.

used Alternate Installer as only 256 MB RAM.

no Battery icon at top of screen, no battery options under power management, only "On AC Power".

The laptop did charge the battery under windows.  The laptop is running on battery now w/ Ubuntu, don't know if it will charge it if I run it down.

BTW: wiped Windows off completely to install Ubuntu.  Can't go back w/o buying another copy of Win - this is a friend's son's deserted laptop trying to make usable for her.

thanks


----

hmmm, just closed the lid, and the screen went off but it sounds like the machine is still running / not sleeping, so in my case, perhaps a better way to describe the problem is Ubuntu didn't recognize that it was being installed onto a laptop at all??  Maybe I should start a different thread?

---

### Post by marklar2u on 2009-07-23
re-reading Matt's post, I tried typing 

$ acpi -b

and got the result:  acpi is currently not installed. 

After more research, found this
[http://ubuntuforums.org/showthread.php?p=2595626](http://ubuntuforums.org/showthread.php?p=2595626)

which explains the BIOS prior to 2000 issue that prevented the acpi from being installed: so investigating...

---

### Post by marklar2u on 2009-07-27
well, updated BIOS (by reinstalling Windows...ugggh, stupid dell non-floppy based installers that require windows...wtf??) then, reinstalled 9.04...same message, even though the BIOS is dated 8/15/2000, the Alternate Installer still fails to recognize it and install ACPI.

As this computer has no internet connectivity, I am stuck ( unless I can move it there on a floppy or cd?? ) without the use of a battery monitor, or power profiles that recognize that this is a laptop installation.

I wonder if I downloaded a full installation cd (vs the alternate install that was used) could the ACPI package be applied somehow to the install on the HD?

Thanks in advance for any help / suggestion how to try this.

---

### Post by Pianoman72 on 2009-09-15
You can't use ACPI with the Inspiron 3500 (or other old machines).  Enable APM instead.

This is the post I used to get mine working:

[http://ubuntuforums.org/showpost.php?p=4012983&postcount=18]("http://ubuntuforums.org/showpost.php?p=4012983&postcount=18")

---

