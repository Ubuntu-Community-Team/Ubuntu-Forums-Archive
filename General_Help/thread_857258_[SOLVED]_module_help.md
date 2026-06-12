---
title: "[SOLVED] module help"
date: 2008-07-12
forum: General Help
---

### Post by tad1073 on 2008-07-12
When I: 
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

I get this error:
```
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080712091251
FATAL: Error inserting battery (/lib/modules/2.6.24-19-generic/kernel/drivers/acpi/battery.ko): No such device

```

---

### Post by boblemur on 2008-07-12
have you tried manualy backing up the file its looking for and then deleting it??

and then running the config...

ie..

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
# make sure the first copy worked... and then
sudo rm /etc/X11/xorg.conf
# then try configure again
sudo dpkg-reconfigure -phigh xserver-xorg


```

give that a go, but im not really sure what it means about the battery :S

---

### Post by tad1073 on 2008-07-12
I have tried that already.

---

### Post by boblemur on 2008-07-12
i think it could be a grub thing, are you running a desktop or a laptop??

ie, do u actualy have a battery?

---

### Post by tad1073 on 2008-07-12
> **boblemur said:**
> i think it could be a grub thing, are you running a desktop or a laptop??

ie, do u actualy have a battery?

I have a desktop, no battery.

---

### Post by PmDematagoda on 2008-07-12
Try unloading that module with:-
```
sudo modprobe -r battery
```
and then try doing the reconfiguration again.

---

### Post by boblemur on 2008-07-12
try booting with this:

```
noapic acpi=off noapm
```

on the end of your grub entry the one with this in it: ( the long one)

ro quiet splash

---

### Post by tad1073 on 2008-07-12
> **PmDematagoda said:**
> Try unloading that module with:-
```
sudo modprobe -r battery
```
and then try doing the reconfiguration again.

Just tried it then did reconfig again and got the same error.

---

### Post by PmDematagoda on 2008-07-12
> **tad1073 said:**
> Just tried it then did reconfig again and got the same error.

Try doing the suggestion by boblemur, but if that doesn't work, then boot Ubuntu in Recovery Mode and select xfix, after that is finished see if everything(meaning the PS/2 mouse) works now.

---

### Post by tad1073 on 2008-07-12
nothing is working, and when I do xfix or sudo dpkg-reconfigure -phigh xserver-xorg dkms gets removed and I have to reinstall the nvida driver

---

### Post by tad1073 on 2008-07-12
bump

---

### Post by PmDematagoda on 2008-07-13
Then try:-
```
sudo dpkg-reconfigure xserver-xorg
```
and see if it works any better.

---

### Post by tad1073 on 2008-07-13
> **PmDematagoda said:**
> Then try:-
```
sudo dpkg-reconfigure xserver-xorg
```and see if it works any better.

that didn't work either

---

### Post by PmDematagoda on 2008-07-13
> **tad1073 said:**
> that didn't work either

Was it with the same error as before?

---

### Post by tad1073 on 2008-07-14
> **PmDematagoda said:**
> Was it with the same error as before?

yep.

---

### Post by PmDematagoda on 2008-07-14
> **tad1073 said:**
> yep.

Then try moving the module in question with:-
```
sudo mv /lib/modules/2.6.24-19-generic/kernel/drivers/acpi/battery.ko ~/
```
and then try executing the command again.

---

### Post by tincho09 on 2008-08-10
same problem

[[IMG]http://img110.imageshack.us/img110/4296/screenshotfp2.th.png[/IMG]](http://img110.imageshack.us/my.php?image=screenshotfp2.png)
:lolflag:

---

### Post by tad1073 on 2008-08-16
> **tincho09 said:**
> same problem

[[IMG]http://img110.imageshack.us/img110/4296/screenshotfp2.th.png[/IMG]](http://img110.imageshack.us/my.php?image=screenshotfp2.png)
:lolflag:

I guess we need a Linux guru to help us with our problem.

I still havn't solved the problem.

---

