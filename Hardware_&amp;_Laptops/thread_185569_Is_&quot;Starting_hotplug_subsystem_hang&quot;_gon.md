---
title: "Is &quot;Starting hotplug subsystem hang&quot; gone in Dapper?"
date: 2006-05-31
forum: Hardware &amp; Laptops
---

### Post by 1002285 on 2006-05-31
Hi,

I've had problems with system hanging during the boot at the point of "starting hotplug subsystem. I searched threads about that a couple of weeks ago and found that it is a common problem with laptops and that there were no good solutions.

I'm considering upgrading to Dapper, but this is an important question. Will I have it there also?

The computer is Dell Latitude CPi with 133 Mhz P II and 128 Mb Ram, so it's not powerful at all, either.

And, last time I upgraded to Dapper - network upgrade - I lost my  ethernet connection. My wifi wouldn't work anyway. This was about a couple of weeks ago, too. Was it a bug?

How can I upgrade leaving the Breezy install just in case? I have some free space, but how much free space do I need?

---

### Post by K.Mandla on 2006-05-31
I've been using Dapper for at least a couple of months on several different laptops (including a CPx) and haven't had any hotplug hangs. Of course, that isn't any guarantee.

If you partition out your free space and leave about 2GB for a Dapper installation, you could dual-boot Breezy and Dapper. Would that work for you?

---

### Post by 1002285 on 2006-05-31
[QUOTE=K.Mandla]I've been using Dapper for at least a couple of months on several different laptops (including a CPx) and haven't had any hotplug hangs. Of course, that isn't any guarantee.

If you partition out your free space and leave about 2GB for a Dapper installation, you could dual-boot Breezy and Dapper. Would that work for you?[/QUOTE]

Thanks for the answer.
Yes, I certainly have 2 Gb's, I thought I needed a lot more.
I have 3 main partitions - NTFS for windows, FAT32 for docs, and a linux partition, but I guess there is a lot of free room on both Windows and Breezy partition.
But if I want to install dapper from internet, how can I get it to another partition? I don't have a DVD-rom here.
I think I'll try it then at some point, althouth it might not solve all my problems at all.

I'll try and post a new thread describing my wifi card problem that has not been solved, and I suspect it has to do with the hotplug subsystem - ethernet in the PCMCIA slot works fine, but usb wifi ...
Anyway, I'll have to write a proper post about it with all the info I have managed to get, but I don't have a lot of time for that right now.

---

### Post by K.Mandla on 2006-05-31
Well, be sure to back everything up before you do any drastic repartitioning. :)

GParted is what I usually use to modify partitions, and if you have to resize your system partition, there's a GParted Live CD that works like a champ. 

You shouldn't need a DVD to install Dapper; there are CD ISOs. Or perhaps I misunderstand you. ;)

---

### Post by Yamfu on 2006-06-02
I've got the same problem with "starting hotplug subsystem". Until now I think this problem does appear more often when the powercord/AC-adapter is connected during  a boot.

I'm using a Dell Latitude CPi with 366 Mhz P II - 128 Mb Ram.

Anyone has a solution for this starting problem?  I'm not convinced that Dapper Drake resolves this problem

---

### Post by 1002285 on 2006-06-02
i can only tell that Dapper doesn't work at all for me. I made a network upgrade from a separate install of 5.10, and got to see what Dapper looks like. But not more. I don't know what to do, cause I'm a newbie. PCMCIA doesn't work. In 5.10 it works and I have ethernet LAN card there. In dapper boot I get the message "PCMCIA services - failed" or sth.
And I guess this has to do with the same old problem.

---

### Post by wbmj on 2006-06-03
Hotplug is replaced by Udev in Dapper.

---

### Post by ddumanis on 2006-06-04
I used to hate this problem in Breezy. It's totally gone for me in Dapper. In fact, it's the REASON I upgraded to Dapper. Everything else is just gravy.

---

