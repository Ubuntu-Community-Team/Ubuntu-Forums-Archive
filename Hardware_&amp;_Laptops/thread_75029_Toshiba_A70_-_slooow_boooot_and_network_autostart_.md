---
title: "Toshiba A70 - slooow boooot and network autostart stops working"
date: 2005-10-13
forum: Hardware &amp; Laptops
---

### Post by holiday on 2005-10-13
I installed Breezy about six weeks ago on this Toshiba A70 which is not the first but is absolutely the last Toshiba I will ever buy (but never mind that - different subject).

At first install the boot was quick and clean and my atheros wireless came up very nicely but then about two weeks ago, things started to choke up. The boot process is  very slow and apparently for other reasons than the fact that networking does not start. The lines used to fleet by, now they plop out one by one.

And I have to manually start networking.

Booting to the previous kernel makes no difference except that the messages change: instead of the 8139too suggestion I get messages about the fan device not being found (seems to be working though)

here's my /etc/network/interfaces file. It looks ok to me, but maybe things have changed. Anywhere else i can look. 

Thanks
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0

# The primary network interface



iface ath0 inet static
wireless-essid sroom
wireless-key <secret>
address 192.168.0.101
netmask 255.255.255.0
gateway 192.168.0.1

auto ath0

iface eth0 inet static
address 192.168.0.101
netmask 255.255.255.0
gateway 192.168.0.1


```

---

### Post by simms on 2005-10-13
it sounds like the initial failure of your networking startup during boot is causing other boot-time items to stall and fail.  

for example, i notice that the default breezy install tries to synchronize the system clock with ntp.ubuntulinux.org (or something like that) at boot time, and this will obviously stall for a minute if networking functions failed to come up for whatever reason.  a similar stall will occur if your mail transport agent (MTA), for example **exim4**, tries to start up with no networking available.  the quick-n-dirty solution for these (during boot-up) is to simply hit **Ctrl+C** once for each stalled item in the boot-up list.  

the real solutions?  either fix your wireless support so that it comes up correctly at boot-time, or disable the automatic startup of network-dependent items that cause such stalls by editing your system startup scripts (in **/etc/rc***) -- there's a nice GUI for this called **Boot-Up Manager** or **bum** (in the *universe* repository).

---

### Post by leezer3 on 2005-10-13
Yup, its the NTP. Have a look around the forums, I can't lay my hands on the precise thread at this time :rolleyes: , but what you can do is chmod the ntp module to be non-executable, and thus disable it at boot. Others have reported that uninstalling works as well, but it didn't with me.

Alternatively, press CTRL+C to skip the NTP synchro.

Cheers

-Leezer-

---

### Post by holiday on 2005-10-13
Thanks for the replies. I'll disable my network-dependent boot items if necessary, but I prefer to fix the wireless.

Any ideas why it's suddenly gone wrong? It used to work great. It connected faster than under XP. 

Other than the /etc/network/interfaces file, what could be screwing things up. I suppose that the hardware could suddenly have gone flakey, but XP works as before. And I've reset my router.

---

### Post by leezer3 on 2005-10-13
I would kinda assume that if it was working under Hoary fine on boot etc, then a driver update might be in order, especially if the kernel you are using has changed, but the driver hasn't been recompiled.
Is this a Ubuntu provided driver- If so, then you may be better off finding the official version; Ubuntu tends to ship slightly out of date drivers for this sort of thing.

Oh, and I sympathise entirely with your thoughts on the lappy- My Tecra S1 had (Seems to be over it now) new motherboard syndrome, having had three in three months. Why? - Inadequate cooling :rolleyes: and this is on pretty light gfx/ office work.

Cheers

-Leezer-

---

### Post by holiday on 2005-10-14
Using the same driver as originally installed by Breezy about a month-6 weeks ago. Stopped working about two weeks ago. Seems about the same time as the kernel upgrade but booting into the previous kernel does not fix the problem.

I've tried interpreting Device Manager to find the driver, but couldn't find what looked to be the file. How do I map between the Device Manager driver setting and the actual file? Or perhaps it's been deleted??? If so, how do I ask apt-get for it. 

Also - if I get into recompiling drivers, how do I make sure that Ubuntu uses them? The apt-get has been working very well (Well... maybe not after all there is this problem)...

---

### Post by SwordAngel on 2005-10-16
holiday, how did you get Breezy to install in the first place? I have an A70, too; but I can't install Ubuntu at all (4.10, 5.04, and 5.10). Whenever I boot from the installation CD, after the bootloader unpacks and loads some stuff, I get a black screen and the computer seems to stop there. Is there some special setting that I need to set (for instance, in the BIOS)?

---

### Post by knappen on 2005-10-17
Maybe you got a corrupt CD?

---

### Post by Xiata on 2005-10-17
SwordAngel: 
Boot install cd with command:
linux debian-installer/framebuffer=false


... The slash might be the other direction. Anyhow its inside one of the menus (hit the F* keys).

Sounds like you have an ATI card in that laptop.

Holiday:
Since the normal way to handle wireless in linux sort of sucks, I installed NetworkManager (network-manager) from the apt repositories, disabled autostarting of all network interfaces using the old way, and then used networkmanager to handle it all (through the applet nm-applet). Syncing the normal way takes forever, but syncing through NetworkManager is faster for me. The only problem is: NetworkManager makes any boot-time network activities (like syncing the clock to ntp.ubuntu.com or something like that) impossible. Maybe this will work for you.

---

### Post by holiday on 2005-10-18
Yes i used the  debian-installer/framebuffer=false
and it went in like a charm.

Beautiful. And then, gradually, as the daily updates came down, the system has been slowing down and  falling apart. Got so I'd say, Ok what's going to break this time.

---

### Post by SwordAngel on 2005-10-18
Yes, you are absolutely right. The Toshiba Satellite A70 comes with an ATi Mobility Radeon 9000.

Let me try again tonight, using the command option you suggest.
[quote=Xiata]SwordAngel: 
Sounds like you have an ATI card in that laptop.
[/quote]

---

### Post by SwordAngel on 2005-12-25
Somebody else has also suggested using the option "vga=771". How is that different from "debian-installer/framebuffer=false"? Do you know?

---

