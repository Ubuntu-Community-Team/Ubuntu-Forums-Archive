---
title: "Laptop battery issue"
date: 2005-11-23
forum: General Help
---

### Post by thelaughingman on 2005-11-23
Hi all, I've got Kubuntu 5.10 installed on my Averatec 3200 laptop and it works pretty well, but I keep getting one unexplained problem that I can't seem to solve.  It seems that there may be a problem with my power adapter or how KDE's battery monitor reads from my battery.  When I am running off the battery alone everything is fine, but sometimes when I am plugged into the wall the battery monitor messes up and my computer will just shut off, no shutdown sequence... just *poof* off.  Before this happens I have noticed that my monitor will  show the image of the power cord but an empty battery, which 1 second before was completely full.

The only way I have found to solve this, while keeping it plugged in, if I want to keep it on over night is to ctrl-alt-f1 to the console and then turn off the monitor.  This is really bugging me and I want to get it fixed asap if anyone has a solution for me.  I don't think its the power adapter b/c the power works fine over night in the console, but only messes up in KDE when the battery monitor is on, but I could be wrong.  Thanks for any help you can provide.

---

### Post by mlomker on 2005-11-23
Are you saying that you shut down KDE or you used a **kill** command to stop something?  That wasn't clear.

My only thought was that the power management daemons aren't communicating properly with the BIOS in your machine.  KDE doesn't have its own agents afaik, they just communicate with modules that are already loaded.  If you've already checked that your system BIOS is current then this is a head scratcher.

```

mlomker@mlomkernote:~$ lsmod | grep i2c
i2c_acpi_ec             5568  0
i2c_sis96x              5316  0
i2c_core               21328  2 i2c_acpi_ec,i2c_sis96

```

**dmesg | grep ACPI** will also give you some output.

---

### Post by thelaughingman on 2005-11-24
I didn't shutdown KDE or kill anything, the laptop will just shut off.  It shows that the battery is out of power(despite being plugged in) and after a second or two it just shuts off (no shut down sequence, the computer just shuts off).

When I run lsmod, I get similar output to yours, but I dont know what I should be looking for.
```
brian@anubis:~$ lsmod |grep i2c
i2c_acpi_ec             5760  0
i2c_viapro              7696  0
i2c_core               19728  2 i2c_acpi_ec,i2c_viapro

```

---

### Post by mlomker on 2005-11-24
[QUOTE=thelaughingman]I didn't shutdown KDE or kill anything, the laptop will just shut off.  It shows that the battery is out of power(despite being plugged in) and after a second or two it just shuts off (no shut down sequence, the computer just shuts off).
[/QUOTE]

That shows that power management drivers are loading.  If I run this shortly after bootup then it confirms that it recognized my battery:

```

mlomker@mlomkernote:/$ dmesg | grep battery
[4294729.219000] ACPI: Battery Slot [BAT0] (battery present)

```

My question about what you are killing was when you said that it would run fine overnight from a terminal prompt.  Are you ending your KDE session?  Using Ctrl-Alt-F1 to get to a terminal prompt does not shut down KDE.

If you have the latest BIOS on your laptop then you'll probably want to search/file a bug report at the Bugzilla link at the top of the page.

---

### Post by thelaughingman on 2005-11-24
It recognizes my battery just fine
```
brian@anubis:~$ dmesg | grep battery
[4294705.960000] ACPI: Battery Slot [BAT0] (battery present)

```

I don't actually kill anything to get to the terminal, I just ctrl-alt-f1, which I realize doesn't kill KDE.  I'll check for a new BIOS and file a bugzilla report if I don't find anything.  Thanks for your help.

---

