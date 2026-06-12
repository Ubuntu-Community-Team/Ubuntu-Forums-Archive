---
title: "ACPI, smart battery and missing random keystrokes"
date: 2006-06-03
forum: Hardware &amp; Laptops
---

### Post by kousik on 2006-06-03
After dist-upgrade from Breezy to Dapper, the smart battery in my Acer Travelmate 4002NLCi started working :) and it shows both percentage and time remaining.

Unfortunately, the ACPI caused a severe side effect. X misses random keystrokes, sometimes gets repeated ones. Even mouse clicks are missed too. Only if I boot with acpi=off, keyboard behaves sane; but that turns all ACPI features off.

I did some search in net and tried booting with ec_burst=1 as boot parameter, but that does not help too. Can it be the cause that the kernel shipped with Dapper has the sbs- (smart battery) patch but not ec- (embedded controller) patch? 

As a side issue, I fixed my broken DSDT as per [http://forums.gentoo.org/viewtopic.php?t=122145](http://forums.gentoo.org/viewtopic.php?t=122145) and as per [http://gaugusch.at/kernel.shtml](http://gaugusch.at/kernel.shtml) Ubuntu kernels should already have acpi-initrd-dsdt patch incorporated, but if I append the magic signature and DSDT.aml to the initrd, the kernel panics at boot.

Any idea what should I do to avoid missing random events? It really gets in the way.

I tried booting the Breezy's kernel 2.6.12-10 but somehow that fails to initialize my WLAN (insmod ipw2200 fails).

](*,)  Kousik

---

### Post by Jaif on 2006-06-03
Missing keystrokes also here on an Acer Travelmate 4502wlmi with Dapper.

---

### Post by Murphy666 on 2006-06-03
I have the same problem. There is a lot of people how have this problem and  there is no real solution for now. You can see other people comments from 
this bug report :

[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/39315]("https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/39315")

On my side, I know this is related to KDE that start something at boot but I'm unable to find which program is causing this misbehavior. All I know is that it's related to power management/monitoring software.

---

### Post by Murphy666 on 2006-06-03
Just to let you know that I have a temporary fix for my problem :

killing the "kaccess" process. This is a little daemon that monitor the keyboard.

This workaround is just for people using KDE (Kubuntu)

---

### Post by kousik on 2006-06-04
[QUOTE=kousik]After dist-upgrade from Breezy to Dapper, the smart battery in my Acer Travelmate 4002NLCi started working :) and it shows both percentage and time remaining.

Unfortunately, the ACPI caused a severe side effect. X misses random keystrokes, sometimes gets repeated ones. Even mouse clicks are missed too. 
...

](*,)  Kousik[/QUOTE]

I guess I found the workaround. The smart battery module is the culprit. Removing it disables the battery status, but the laptop is usable.

```
sudo rmmod acpi_sbs
```

Voila! :D

---

### Post by fsf@rula on 2006-07-18
adding the ec_burst=0 option to my kernel boot parameters helped a bit...not a lot, but a bit...it is more usable.

---

### Post by Fullofit on 2006-07-28
I recently upgraded my Acer Travelmate 4502LCi from Breezy to Dapper LTS. This provided support for my smart battery that I had not had before but has shown no side effects yet. I use Gnome desktop. A first attempt to do a clean instal from CD did not work. When upgrading over the internet, I had to insert the CD though (despite having downloaded ~500MB).

---

### Post by Kashirigi on 2006-08-03
I've got an Acer TravelMate 4002 WLmi and I have the same problems, although they are not particularly severe using Xubuntu with all the battery monitoring turned off. Removing acpi_sps has "solved" the problem. I don't use the battery much anyway. I would, ideally, like to be able to use the battery and know how much power it has left, though.

---

### Post by tiger015 on 2006-09-24
Hi. I have Acer travelmate 4502 WLmi. I see battery status fine but my keyboard also misses keystrokes at random. Any help ?

---

### Post by Eragon on 2006-10-19
Yea i'm having this problem too... i tried disabling the kaccess and it does help a lot, but even typing this response i'm getting duplicated and missed characters. I travel all the time so i really need my battery status to work, i cant just turn it off. I'm a system admin so i type fast and dont have time to constantly check what i typed, especially when entering shell passwords that dont display anything.

I'm going to have to spend some serious time tearing this shit apart to get to the answer, i dropped FC4 because it wouldnt recognize the battery in my acer (it seems to only happen to acers, probably because of the SBS and not standard ACPI calls).

Ill let you all know if i find anything, but in the meantime anything anyone post would help, any additional information.

Thanks,
Dave

---

