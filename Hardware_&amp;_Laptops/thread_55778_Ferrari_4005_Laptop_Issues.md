---
title: "Ferrari 4005 Laptop Issues"
date: 2005-08-10
forum: Hardware &amp; Laptops
---

### Post by Cosmic_Crusader on 2005-08-10
Bought this laptop recently and have been trying to get it working well with Hoary 64bit release. I have also installed the x86 32bit version and get pretty much the same results as here.
I fell in love with Ubuntu at Linux.conf.au, have been using Linux since 1993, and run Gentoo and Debian on my home servers. I'd rather my laptop "just work", which is why I chose Ubuntu (also your laptop support is rockin).
Things aren't all working smoothly on the hardware front, but it is working enough for me to use it for development, just not enough to reach its full potential.

On inital bootup after install X windows displayed a blank screen. This is due to the ATI X700 not being supported by the ATI driver from the default install. It doesn't crash the machine as switching to a text terminal (with Ctrl+Alt+F1) provides a working system. From there it is as simple as changing to the vesa driver in xorg.conf and X is usable. However it won't go above 1024x768, nowhere near the native LCD res of 1680x1050.

Then it is noticed that the touchpad does not work. Fixinging this is as simple as running "rmmod psmouse && modprobe psmouse". I don't know of a better way of fixing it at this stage.
The system log shows the following on running the modprobe part of the above command:> Aug 10 19:15:16 localhost input.agent[11539]: evdev: already loaded
Aug 10 19:15:16 localhost input.agent[11539]: evbug: blacklisted
Aug 10 19:15:16 localhost input.agent[11575]: evdev: already loaded
Aug 10 19:15:16 localhost input.agent[11575]: evbug: blacklisted
Aug 10 19:15:16 localhost input.agent[11613]: evdev: already loaded
Aug 10 19:15:16 localhost input.agent[11613]: evbug: blacklisted
Aug 10 19:15:16 localhost kernel: Synaptics Touchpad, model: 1, fw: 5.9, id: 0x126eb1, caps: 0xa04713/0x4000
Aug 10 19:15:16 localhost kernel: input: SynPS/2 Synaptics TouchPad on isa0060/serio4
Aug 10 19:15:16 localhost input.agent[11647]: joydev: loaded successfully
Aug 10 19:15:16 localhost input.agent[11647]: evdev: already loaded
Aug 10 19:15:16 localhost input.agent[11647]: evbug: blacklisted
Aug 10 19:15:16 localhost input.agent[11647]: mousedev: already loaded
Aug 10 19:15:16 localhost input.agent[11647]: tsdev: already loaded

Another problem on initial bootup is the time goes twice as fast as it should, resulting in a few issues, including the CPU always appearing to be 50% in use. To fix this is as simple as upgrading to the 2.6.12 kernel and appending "no_timer_check" to the kernel boot options. Things run very nicely then.
The exact kernel I'm running is from the Breezy repository, where "uname -a" displays:
> Linux comet 2.6.12-6-amd64-k8 #1 Fri Aug 5 20:51:28 BST 2005 x86_64 GNU/Linux and the startup logs show it as > Linux version 2.6.12-amd64-k8 (root@ubuntu) (gcc version 3.4.4 20050209 (prerelease) (Debian 3.4.3-9ubuntu4)) #1 Wed Jul 27 19:10:58 IDT 2005

To get full graphics support, the latest release from ATI does appear to support it, however it only supports up to kernel 2.6.11, and that kernel doesn't work well due to the aforementioned timer issue. Apparently ATI are releasing a new driver in September. If only they supported Linux as well as nVidia! However this is my first ATI card, so perhaps I am not fully versed in things yet.

It is also noted that on starting xorg the CPU scaling applet complains that CPU scaling is not supported, and attempting to "modprobe acpi-cpufreq" gives the following error:> FATAL: Error inserting acpi_cpufreq (/lib/modules/2.6.12-6-amd64-k8/kernel/arch/x86_64/kernel/cpufreq/acpi-cpufreq.ko): Operation not permitted

Lastly (at least from what so far I have attempting to get working), the battery status is not working (most likely due to an incorrect DSTC for the ACPI). This is most easily diagnosed from the following system log entries that occur every 30s: > Aug 10 19:15:22 localhost kernel: ACPI-0352: *** Error: Looking up [Z00I] in namespace, AE_NOT_FOUND
Aug 10 19:15:22 localhost kernel: search_node ffff810002f3bf80 start_node ffff810002f3bf80 return_node 0000000000000000
Aug 10 19:15:22 localhost kernel: ACPI-1138: *** Error: Method execution failed [\_SB_.BAT1._BST] (Node ffff810002f34e40), AE_NOT_FOUND

To round out my current findings, here is a listing from lspci (note how many unknown devices there are!!!):> 0000:00:00.0 Host bridge: ATI Technologies Inc: Unknown device 5951 (rev 01)
0000:00:02.0 PCI bridge: ATI Technologies Inc: Unknown device 5a34
0000:00:06.0 PCI bridge: ATI Technologies Inc: Unknown device 5a38
0000:00:13.0 USB Controller: ATI Technologies Inc: Unknown device 4374
0000:00:13.1 USB Controller: ATI Technologies Inc: Unknown device 4375
0000:00:13.2 USB Controller: ATI Technologies Inc: Unknown device 4373
0000:00:14.0 SMBus: ATI Technologies Inc: Unknown device 4372 (rev 11)
0000:00:14.1 IDE interface: ATI Technologies Inc: Unknown device 4376
0000:00:14.3 ISA bridge: ATI Technologies Inc: Unknown device 4377
0000:00:14.4 PCI bridge: ATI Technologies Inc: Unknown device 4371
0000:00:14.5 Multimedia audio controller: ATI Technologies Inc: Unknown device 4370 (rev 02)
0000:00:14.6 Modem: ATI Technologies Inc: Unknown device 4378 (rev 02)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 5653
0000:05:00.0 Ethernet controller: Broadcom Corporation: Unknown device 169d (rev 11)
0000:06:02.0 Network controller: Broadcom Corporation: Unknown device 4318 (rev 02)
0000:06:09.0 CardBus bridge: Texas Instruments: Unknown device 8031
0000:06:09.2 FireWire (IEEE 1394): Texas Instruments: Unknown device 8032
0000:06:09.3 Unknown mass storage controller: Texas Instruments: Unknown device 8033

I have compiled my own kernel, but got nothing more than the stock kernel provided (although I read somewhere that a preempt kernel makes ACPI work better??).

VERY looking forward to Breezy, and am most willing to help in ensuring this hardware is fully supported. If any devs want more info please ask!

If anyone can provide some insight into making things smoother then please post!

---

### Post by lakin on 2005-08-12
I have spent the past few days getting Ubuntu working as well as I can with my Ferrari 4005 laptop. 
Here are my notes:

[http://pages.cpsc.ucalgary.ca/~weckerl/ferrari_ubuntu_64.html](http://pages.cpsc.ucalgary.ca/~weckerl/ferrari_ubuntu_64.html)

I would appreciate feedback on this if there are typos or unclear sections.  please continue to use these forums for problems, rather than using my email.

---

### Post by Cosmic_Crusader on 2005-08-21
Nice page!  Very helpful for fixing the ACPI as I hadn't got around to figuring that one out.

Have you had any progress on getting CPU scaling support?

The applet always pops up a dialog saying it isn't supported when I log in and then stays at 2GHz.

---

### Post by matthew on 2005-08-21
[QUOTE=lakin][http://pages.cpsc.ucalgary.ca/~weckerl/ferrari_ubuntu_64.html](http://pages.cpsc.ucalgary.ca/~weckerl/ferrari_ubuntu_64.html)

I would appreciate feedback on this if there are typos or unclear sections.  please continue to use these forums for problems, rather than using my email.[/QUOTE]
That is a **fabulous** page. Please consider putting the info on the Wiki as well. It's made by Acer, right? So maybe on this page:

[http://wiki.ubuntu.com/HardwareSupportMachinesLaptopsAcer](http://wiki.ubuntu.com/HardwareSupportMachinesLaptopsAcer)

I see another Acer Ferrari laptop there, but not your model. It would be a welcome addition!

---

### Post by jvh on 2005-09-02
Lakin : 

When i try to access : [http://pages.cpsc.ucalgary.ca/~weckerl/ferrari_ubuntu_64.html](http://pages.cpsc.ucalgary.ca/~weckerl/ferrari_ubuntu_64.html) 

i get a :
Forbidden
You don't have permission to access /~weckerl/ferrari_ubuntu_64.html on this server.
Additionally, a 403 Forbidden error was encountered while trying to use an ErrorDocument to handle the request.
Apache/2.0.53 (Unix) mod_ssl/2.0.53 OpenSSL/0.9.7a PHP/4.4.0 Server at pages.cpsc.ucalgary.ca Port 80

I've just bought a Ferrari 4005, and it's giving me a very hard time. I could really benefit from your page, is the URL moved or something? 
Could i access it somehow - it would be a great help i've been fighting with this damm thing for 1 month now.

---

### Post by matthew on 2005-09-02
[QUOTE=jvh]Lakin : 

When i try to access : [http://pages.cpsc.ucalgary.ca/~weckerl/ferrari_ubuntu_64.html](http://pages.cpsc.ucalgary.ca/~weckerl/ferrari_ubuntu_64.html) 

i get a :
Forbidden
You don't have permission to access /~weckerl/ferrari_ubuntu_64.html on this server.
Additionally, a 403 Forbidden error was encountered while trying to use an ErrorDocument to handle the request.
Apache/2.0.53 (Unix) mod_ssl/2.0.53 OpenSSL/0.9.7a PHP/4.4.0 Server at pages.cpsc.ucalgary.ca Port 80[/QUOTE]
I just tried the pages and they work fine for me. I suggest trying again, maybe form a different location. Maybe your ISP is being banned or maybe is was just a weird web hiccup??

---

### Post by jvh on 2005-09-02
Hi Matthew, thank you for the quick reply. 

This i really wierd. . .  I tried the URL from work earlier today and then again several hours later when i got home many times - same stupid error. 

Now it works. . ! It's great  :grin: 

The web works in mysteries ways.

Thanks anyway friend.

---

### Post by lakin on 2005-09-20
[QUOTE=jvh]Hi Matthew, thank you for the quick reply. 

This i really wierd. . .  I tried the URL from work earlier today and then again several hours later when i got home many times - same stupid error. 

Now it works. . ! It's great  :grin: 

The web works in mysteries ways.

Thanks anyway friend.[/QUOTE]


My school went through a number of server issues. During that portion of time many of the file permissions got screwed up.  Glad you were able to reach it eventually. :)

---

### Post by lakin on 2005-09-20
[QUOTE=Cosmic_Crusader]Nice page!  Very helpful for fixing the ACPI as I hadn't got around to figuring that one out.

Have you had any progress on getting CPU scaling support?

The applet always pops up a dialog saying it isn't supported when I log in and then stays at 2GHz.[/QUOTE]


You just need to insert the appropriate module at boot time:
powernow-k8

---

### Post by jvh on 2005-09-23
[QUOTE=lakin]My school went through a number of server issues. During that portion of time many of the file permissions got screwed up.  Glad you were able to reach it eventually. :)[/QUOTE]

Hi Lakin, great work getting the Ferrari issues solved. Really helped me alot - thank you very much.

What about Breezy ? Have you heard news from the development team, are they listening to you ? Is all the Ferrari-errors being corrected by the time Breezy hits the shelves ? 

Thank again for helping the Ferrari users :-) 

- Joachim

---

### Post by lakin on 2005-09-23
[QUOTE=jvh]Hi Lakin, great work getting the Ferrari issues solved. Really helped me alot - thank you very much.

What about Breezy ? Have you heard news from the development team, are they listening to you ? Is all the Ferrari-errors being corrected by the time Breezy hits the shelves ? 

Thank again for helping the Ferrari users :-) 

- Joachim[/QUOTE]


Unfortunately I haven't had much time to work directly with the developers.  Some of the issues were solved in the colony 4 release, but not all of them.  I really hope that I get the time to make sure that dapper drake works well.    In the meantime, what I can say is that I will update my instructions once breezy is officially released.

---

### Post by jvh on 2005-09-24
[QUOTE=lakin]Unfortunately I haven't had much time to work directly with the developers.  Some of the issues were solved in the colony 4 release, but not all of them.  I really hope that I get the time to make sure that dapper drake works well.    In the meantime, what I can say is that I will update my instructions once breezy is officially released.[/QUOTE]

Damn i had a small hope that everything would work right out of the box, by the time Breezy was realeased. I have an expensive machine just standing on the shelf doing nothing. 

So Dapper Drake is the goal, and the battle for Breezy is somewhat lost ? :-(

I'm realy looking foreward to reading your notes about getting Breezy to play nice with the Ferrari.

---

### Post by lakin on 2005-09-24
[QUOTE=jvh]Damn i had a small hope that everything would work right out of the box, by the time Breezy was realeased. I have an expensive machine just standing on the shelf doing nothing. 

So Dapper Drake is the goal, and the battle for Breezy is somewhat lost ? :-(

I'm realy looking foreward to reading your notes about getting Breezy to play nice with the Ferrari.[/QUOTE]

Well, breezy is almost ready for release, I doubt they will include any new features.  Besides, many of the things which aren't working, are not Ubuntu's fault.  

I just upgraded directly from hoary today, and so far I've gotten the same things working again, with very little trouble.  In a few days I'll try getting the suspend to ram working again.

I was also able to get the secondary monitor out to work fairly well with the latest ATI drivers,  Once I figure out exactly what's needed I'll add a section.

---

### Post by jvh on 2005-09-27
[QUOTE=lakin]Well, breezy is almost ready for release, I doubt they will include any new features.  Besides, many of the things which aren't working, are not Ubuntu's fault.  

I just upgraded directly from hoary today, and so far I've gotten the same things working again, with very little trouble.  In a few days I'll try getting the suspend to ram working again.

I was also able to get the secondary monitor out to work fairly well with the latest ATI drivers,  Once I figure out exactly what's needed I'll add a section.[/QUOTE]

Yeah, guess your right - who's fault is it then ? ;) 
I really like Ubuntu (or debian system in the first place), but i really wished i could find a distro wich could support my Ferrari fully out of the box. Wireless network for example, and the bluetooth mouse.

---

### Post by lakin on 2005-09-27
[QUOTE=jvh]Yeah, guess your right - who's fault is it then ? ;) 
I really like Ubuntu (or debian system in the first place), but i really wished i could find a distro wich could support my Ferrari fully out of the box. Wireless network for example, and the bluetooth mouse.[/QUOTE]

Well, unless the manufacturers of the wireless card release their specifications or open source versions of their drivers, the probability that it will support the wireless card out of the box is pretty slim.    

Things are definitely way better with breezy.  For instance: all the function keys are setup properly out of the box in breezy.  Keep up hope.  It won't be too long before everything is fully functioning.  (Except for hardware who's manufacturer's refuse to cooperate with free software developers.)  Classes will be done in December, and I'll be working hard with Ubuntu to get the best possible support for this laptop.

---

### Post by jvh on 2005-09-28
[QUOTE=lakin]Well, unless the manufacturers of the wireless card release their specifications or open source versions of their drivers, the probability that it will support the wireless card out of the box is pretty slim.    

Things are definitely way better with breezy.  For instance: all the function keys are setup properly out of the box in breezy.  Keep up hope.  It won't be too long before everything is fully functioning.  (Except for hardware who's manufacturer's refuse to cooperate with free software developers.)  Classes will be done in December, and I'll be working hard with Ubuntu to get the best possible support for this laptop.[/QUOTE]

That sounds great Lakin, i really hope you get it all working. I would be happy to help you if you need a hand testing something or anything - just let me know. 
Please send me a link by the time Breezy is out and you've written the guide :-)

---

### Post by mark52230 on 2005-09-28
Hi everyone,

I've just installed Breezy Colony 5 and I've encountered a problem that I did not expect, my wired networking isn't working.. Has anyone else had this problem? In Lakin's guide it says it should work automatically..

Thanks..

EDIT: When trying to visit 192.168.0.1 in firefox it says the connection was refused..

---

### Post by lakin on 2005-09-28
[QUOTE=mark52230]Hi everyone,
I've just installed Breezy Colony 5 and I've encountered a problem that I did not expect, my wired networking isn't working.. Has anyone else had this problem? In Lakin's guide it says it should work automatically..
Thanks..
EDIT: When trying to visit 192.168.0.1 in firefox it says the connection was refused..[/QUOTE]

I've had no problem with this.   I guess I should first make sure that you've gone into System->Administration->Networking and ensured that your network card shows up there, and that you've properly set it up for DHCP and/or the static IP for your network?

The kernel module that you want to use is tg3.  You may want to make sure that it's being loaded properly.  

You can try inserting it manually through: 

sudo insmod tg3

You can also look through your boot logs: /var/log/messages
and see if it's being loaded automatically.  I know that it's been working fine for me in breezy.

---

### Post by mark52230 on 2005-09-29
That module is already loaded :???: 

I've noticed that when I do a clean install and it boots ubuntu for the first time it says [ok] when it synchronizes the clock (so its connecting to something) but then after its configured the packages and I've rebooted it's messed up again (saying [failed] to synchronizing the clock etc).. I don't know if thats coincidence or not..

---

### Post by mark52230 on 2005-09-30
Does anyone know anything I could try? I'd really like to have Ubuntu on this laptop..

EDIT: Theres an icon in the system tray that says Network Connection when I hover over it.. When I click on it, I recieve the following error:

Please contact your system administrator to resolve the following problem:
SIOCGIFFLAGS error: No such device.

---

### Post by lakin on 2005-10-02
[QUOTE=mark52230]Does anyone know anything I could try? I'd really like to have Ubuntu on this laptop..
EDIT: Theres an icon in the system tray that says Network Connection when I hover over it.. When I click on it, I recieve the following error:
Please contact your system administrator to resolve the following problem:
SIOCGIFFLAGS error: No such device.[/QUOTE]

Hrmm, I've had that error as well, but not lately.  One thing that might help you is signing on to IRC, using the freenode servers, and joining #ubuntu, as it might get you some real-time help. 

Also, post your output of the following commands:
ifconfig eth0
ps ax | grep dhclient3
lsmod | grep tg3

Also, if you have web space to upload files, you can upload a copy of:
/var/log/messages
/etc/network/interfaces

---

### Post by mark52230 on 2005-10-03
Ok now networking has suddenly started working and I have no idea why.. But I still get the error on startup :???:

I've just tried getting the graphics drivers to work but I get a module load error :???: 

I guess some things aren't meant to be :(

---

### Post by lakin on 2005-10-08
[QUOTE=mark52230]Ok now networking has suddenly started working and I have no idea why.. But I still get the error on startup :???:

I've just tried getting the graphics drivers to work but I get a module load error :???: 

I guess some things aren't meant to be :([/QUOTE]

The error from the applet is usually because the applet is trying to monitor the wrong device, you can try changing it.

What was the error with the graphics drivers?  Remember that you need to install the linux restricted modules for the kernel that you using.  (You can figure out which kernel you are running through: uname -r).  You also need to install the xorg-fglrx modules.

---

