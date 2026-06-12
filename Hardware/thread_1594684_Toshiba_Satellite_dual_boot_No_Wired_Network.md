---
title: "Toshiba Satellite dual boot No Wired Network?"
date: 2010-10-12
forum: Hardware
---

### Post by Megaman255 on 2010-10-12
Hello!
I bought a Toshiba Satellite L650d - 13U Laptop today.
Windows 7 was already installed so I tried to dual boot with ubuntu 10.04.
Firstly I was having issues installing but i read a thread on how to fix (which worked),
I had to edit etc/default/grub so that it read GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=off"

Everything worked like a dream but I can't get connected to the internet through a wired connection...

I've tried googling and searching but cant find anything relevant.

I've tried loading in packages my friend suggest through usb but it just says dependencies not fulfiled of something :confused::confused:

Any help would be great

(again)

Many thanks

Will

---

### Post by proseliet on 2010-11-28
> **Megaman255 said:**
> Hello!
I bought a Toshiba Satellite L650d - 13U Laptop today.
Windows 7 was already installed so I tried to dual boot with ubuntu 10.04.
Firstly I was having issues installing but i read a thread on how to fix (which worked),
I had to edit etc/default/grub so that it read GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=off"

Everything worked like a dream but I can't get connected to the internet through a wired connection...

I've tried googling and searching but cant find anything relevant.

I've tried loading in packages my friend suggest through usb but it just says dependencies not fulfiled of something :confused::confused:

Any help would be great

(again)

Many thanks

Will

@Will:
You're in need of the correct driver (I think).
My laptop contains a:
Realtek Semiconductor Co., Ltd. Device 8172 (rev 10) for wired internet
(found that out via typing 'lspci' in a terminal).
Goto
[http://ftp.nluug.nl/pub/os/Linux/system/kernel/people/mcgrof/ethernet/](http://ftp.nluug.nl/pub/os/Linux/system/kernel/people/mcgrof/ethernet/)
Download AR81Family-linux-v1.0.1.6.tar.gz
Unpack
Open a terminal
cd to the directory you unpacked the downloaded file in.
Become root
and type:
make <enter>
make install <enter>
cd src <enter>
insmod atl1e.ko <enter>
You should now have a working nic (standard auto eth0 is dhcp). 

NOW:
I have similar problems with my toshiba L650D-10J
(AMD Athlon II P320 dual core processor, 4 GB ram, ATI Mobility Radeon HD4200).
I upgraded the bios with win1.40.exe under windows 7 to version 1.4 (was 1.3). This is the latest version from toshiba.
The laptop is set up as a dual-boot with Ubuntu 10.04 LTS.
Booting only works with acpi=off option.
Only one cpu is recognized, FN + function-keys do not work, hibernation is no good, when plugging in an external mike it does not work. Wired networking does not work out of the box (easy to fix though and wireless does work instantly). And there is no battery-indication.
There 's no directory /proc/acpi/All-kinds-of-files
However...
When using a live-dvd with ubuntu 9.04 LTS there's no wireless nor wired internet.
(easy to fix).
FN+functionkeys work, I have no idea about the hibernation or the external mike. Both cpu's are seen by the system monitor.
And yes there's an /proc/acpi directory with content.
I've read  numerous threads calling it a bios problem, something about a dsdt file etc
But IF this is a bios problem, why then, does 9.04 boot normally, recognizing battery and FN keys working, seeing two cpu's?

Help? Anybody??

TIA
Paul

---

### Post by tosh755 on 2011-06-16
Have you tried the solution given in "Networking & Wireless/Atheros AR8151 ethernet on Asus P8H67-V"?

---

### Post by mathiaho on 2012-03-23
Hi, I know this is an old tread, but if any of you still use ubuntu with the satellite L650D machines, please come over to a thread I've started:

[http://ubuntuforums.org/showthread.php?t=1942992](http://ubuntuforums.org/showthread.php?t=1942992)

A fix will come more likely if many people have the same problems!

Thanks!

---

