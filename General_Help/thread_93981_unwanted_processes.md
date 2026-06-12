---
title: "unwanted processes"
date: 2005-11-23
forum: General Help
---

### Post by scarabaeus on 2005-11-23
I let my breezy running for 11 days. unlike windows, it didn't crash. but nevertherless the system seemed to slow down a bit. so i compared the running processes to before and after a reboot and found this:

1) clicking on the clock-applet, evolution processes start. i dont use evolution so they take up memory for nothing:

evolution-alarm-notify
evolution-data-server-1.4
evolution-exchange-storage

each 30 to 55 mb ram

2) 9(!) gnome-pty-helper were running (2.2 mb each)

(this seems to be an unsolved problem:
[http://www.ubuntuforums.org/showthread.php?t=86212&highlight=gnome-pty-helper](http://www.ubuntuforums.org/showthread.php?t=86212&highlight=gnome-pty-helper)
[http://www.ubuntuforums.org/showthread.php?t=80266&highlight=gnome-pty-helper](http://www.ubuntuforums.org/showthread.php?t=80266&highlight=gnome-pty-helper))

3) nautilus was using 180 mb of ram, although not acitve

i didn't find anything in the forum. help much appreciated.

cheers

PS: i'm having a 1.8 intel with 256mb of ram

---

### Post by pato101 on 2005-11-23
1) do not believe those amounts of RAM. See the "Resident size", which may be about 12Mb each one. I don't think it is the real memory usage either since there are 9Mb shared among other processes for each one of them... Have you tried to uninstall evolution? since you are not using it...

2) I don't have such that problem. Perhaps because I use the login shell option at gnome-terminals.

3) same than point 1) about memory usage. You may do:
killall nautilus
at each moment to force kill (it spawns again with a new fresh process)

---

### Post by Wolki on 2005-11-23
> **scarabaeus]
1) clicking on the clock-applet, evolution processes start. i dont use evolution so they take up memory for nothing:

evolution-alarm-notify
evolution-data-server-1.4
evolution-exchange-storage

each 30 to 55 mb ram [/quote]

volution-data-server is not really a part of evolution said:**
> 2) 9(!) gnome-pty-helper were running (2.2 mb each)

I only have 2, and they take 540 kb of real ram with 540 shared, I wouldn't worry too much.

> 3) nautilus was using 180 mb of ram, although not acitve

This seems like too much, it only takes ~42 virtual and 19 rss here, with the desktop and three windows open.

---

### Post by scarabaeus on 2005-11-23
thx for the replies.

> 2) I don't have such that problem. Perhaps because I use the login shell option at gnome-terminals.

i try that now. see what happens.


> Keep in mind, though, that the ram displayed with the system monitor is not the real RAM that these programs use - To get better numbers, enable "show more info" in the system monitor, the take the "RSS" line and subtract the "shared" line from that - RSS ist how much real RAM these processes (and their libraries) take, Shared is how much of that memory is shared between many processes (libraries, for example)
> 1) do not believe those amounts of RAM. See the "Resident size", which may be about 12Mb each one. I don't think it is the real memory usage either since there are 9Mb shared among other processes for each one of them...

true. :-\"  so it's not as dramatic as it seems after all.
new calculation: evolution-data-server: 1,5mb, that's ok...


> Have you tried to uninstall evolution? since you are not using it...

> evolution-data-server is not really a part of evolution; It's a part of Gnome and can't be easily removed. The calendar applet and some other stuff depend on it. Not sure about evolution-exchange-storage, sounds like it's not a core component but I don't know for sure.

if i try unistalling evolution it wants to remove "ubuntu-desktop" and i don't feel too comfortable with this... (i had the same problem before, cuz it would be nice to get rid of some ubuntu-application that are there by default, but not used)

strange thing is, i can kill all the evolution-apps except the data-server, which relunches instantly. but it's not there at startup. 


but again, misinterpreting the ram use was the problem. i was just concerned having just 256mb of ram. i guess i can live with some small processes running although not needed.

> killall nautilus

sounds good.


thanks again!

---

### Post by Wolki on 2005-11-23
[QUOTE=scarabaeus]
if i try unistalling evolution it wants to remove "ubuntu-desktop" and i don't feel too comfortable with this... (i had the same problem before, cuz it would be nice to get rid of some ubuntu-application that are there by default, but not used)
[/quote]

Removing ubuntu-desktop is not a problem (unless you remove core packages at the same time), it's a metapackage that makes sure you have everything installedf that ubuntu installs by default. Just be sure that you reinstall it before getting a new version of Ubuntu, or you won't get all the new goodies. :)

They're working on fixing this, so that you can remove some of the default apps without removing ubuntu-desktop, but it's not yet sure whether a solution is found and implemented in time for dapper.

> but again, misinterpreting the ram use was the problem. i was just concerned having just 256mb of ram. i guess i can live with some small processes running although not needed.


Don't worry, a lot of people are confused regarding that, and it's a bit counter-intuitive to say the least :) Though there are probably good reasons.

---

### Post by scarabaeus on 2005-11-23
> Removing ubuntu-desktop is not a problem (unless you remove core packages at the same time), it's a metapackage that makes sure you have everything installedf that ubuntu installs by default. Just be sure that you reinstall it before getting a new version of Ubuntu, or you won't get all the new goodies.


synaptic says:
It is safe to remove this package if some of the desktop system
packages are not desired.  However, it is recommended that you keep
it installed, because it is used to carry out certain upgrade
transitions (such as adding new packages to the system).

so i can get all the updates etc even without ubuntu-desktop. just when i want to move to dapper, i have to reinstall it before? is that what "certain upgrade transitions" means?

cheers

---

### Post by Wolki on 2005-11-23
[QUOTE=scarabaeus]so i can get all the updates etc even without ubuntu-desktop. just when i want to move to dapper, i have to reinstall it before? is that what "certain upgrade transitions" means?[/QUOTE]

Yes. Basically, Ubuntu provides only security fixes for a distro once it's released. If you remove ubuntu-desktop, they will still come in, since they're new versions of the same packages. Now, let's say you upgrade from Hoary to Breezy. There are some new programs by default, like Serpentine for burning audio cds. Ubuntu-desktop depends on it, so if you upgrade ubuntu-desktop (as part of the normal upgrade process) Serpentine will automatically be installed. If you don't have ubuntu-desktop anymore, apt can't know (yet) that you want those packages. So you can just install it, which will get the new packages, then delete the unwanted stuff again.

---

