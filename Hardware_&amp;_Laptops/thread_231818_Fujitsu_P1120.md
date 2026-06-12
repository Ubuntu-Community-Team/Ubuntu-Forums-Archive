---
title: "Fujitsu P1120"
date: 2006-08-07
forum: Hardware &amp; Laptops
---

### Post by FinePix on 2006-08-07
Can any help me to install ubuntu 6 on my Fujitsu Laptop P1120. 

Currently theres No Operatin System, Floppy, CD-rom. Bios showing only 3 bootin options (From Hard Disk, USB Floppy, USB CD-ROM)

Is there any way i can install ubuntu without spending money on USB CD-ROM or Floppy.

---

### Post by Ziox on 2006-08-07
> **FinePix said:**
> Can any help me to install ubuntu 6 on my Fujitsu Laptop P1120. 

Currently theres No Operatin System, Floppy, CD-rom. Bios showing only 3 bootin options (From Hard Disk, USB Floppy, USB CD-ROM)

Is there any way i can install ubuntu without spending money on USB CD-ROM or Floppy.

if you have a good bandwidth, then I suppose you can install from a Network Boot Server...I'll see if I can find my trusty guide book...[-o<

---

### Post by FinePix on 2006-08-07
i cannot boot from network, as i mentioned b4 thers only 3 booting options

---

### Post by FinePix on 2006-08-20
i bought a usb-floppy drive and a reffrence book by Keir Thomas "Beginning Ubuntu Linux from Novice to Professional". But the book did not expalin how to install ubuntu over a Network Boot....

Any help

---

### Post by Longwing on 2006-08-29
You're in luck. Several very smart people decided to install Linux on 1120 systems, leaving us normal folk with a slew of resources for installing and maintaining them.

To install without a drive, the easiest way is to use the PXE environment in your laptop bios. Hit F2 while the Fujitsu logo is on display, and you should be able to enable it from there.

For a PXE install to work, you need another working computer to send the files from. Here again, smarter people than I have worked out the details:

[A guide for installing Ubuntu using another Linux computer.]("https://help.ubuntu.com/community/Installation/Netboot?action=show&redirect=PXEInstall")

[URL="https://help.ubuntu.com/community/Installation/WindowsServerNetboot"]A guide for installing Ubuntu using a windows computer.
[/URL]
The default Ubuntu install should enable your keyboard "eraser mouse", your sound, and even your network, modem, and wireless. You will have trouble with the touchscreen and the resolution. I found solutions to those issues here:

[Advice on the Resolution]("http://www.interstice.com/journals/Simon/20030911.html")

[Touchscreen program.]("http://www.interstice.com/journals/Simon/20060413.html")

You'll need to set up the touchscreen program to run whenever the computer runs, and you'll need to to use the keyboard shortcut for re-enabling the keyboard mouse after suspend, but otherwise, this will do the job.

Hope this helps.

---

### Post by FinePix on 2006-11-02
thanks. it works really well

---

### Post by tlie on 2007-10-12
hi, i have fujitsu p1120 without cdrom or floppy.

I have tried many times & fail to install ubuntu feisty 7.04 by following many sources from the net, my lifebook did boot for a moment (by installing from the internal windows xp, after following instructions from where i forgot) and then now displaying "ERROR LOADING OPERATING SYSTEM"

finepix, could u give me some tips what you did different to make it work?

hope the following info helps:
1) I have a working ubuntu-desktop on my PC (so i can install from linux)
2) My network is connected with Linksys Router via Cable modem (the router has DHCP so i'm not sure whether i should disable it so the network boot can work, etc)
3) I cannot access dos or windows from my fujitsu p1120 now
4) I have a bootable ubuntu-desktop CD from Canonical
5) really love ubuntu and would like to get it working in my laptop since win XP is too slow to load for the not-so-fast processor

longwing, thanks for your resources, i will try first "install from linux" but i'm quite confused with some of the procedure.

---

### Post by tlie on 2007-10-13
I have managed to install in my ubuntu PC:
- dnsmasq
- tftp server
as required

however, in my target PC, it now says
"PXE-E51: No DHCP or proxyDHCP offers were received"
PXE-M0F: Exiting PXE ROM.
Error loading operating system

any ideas? thanks

---

### Post by Longwing on 2007-10-15
The PXE environment requests an IP from its server. If your router has DHCP enabled, it will get the address from your router, and not from your PXE install server (your linux PC).

You'll need to assign a static IP to your PC, and disable DHCP in your router until after the install is complete.

---

### Post by tlie on 2007-10-22
done.

by disabling the DHCP server in my router, it can pick up. I just followed the instructions in the following link.
(particularly following the quicknetbook link inside the page)

[A guide for installing Ubuntu using another Linux computer]("https://help.ubuntu.com/community/Installation/Netboot?action=show&redirect=PXEInstall")

After finishing installation, i only come up with ubuntu command line, then later i found out I can just
do apt-get install ubuntu-desktop

then, finally ubuntu in my lifebook!
later on, i switched to xubuntu because ubuntu is too slow for the old lifebook.

installed  xubuntu with no problem with
1) apt-get install xubuntu-desktop
2) then i remove all ubuntu-desktop and related packages by following aysiu's suggestion (i get from the net but i forget where)

the touchscreen is enabled by joytouch from simon
[http://sifter.org/~simon/journal/20030911.html](http://sifter.org/~simon/journal/20030911.html)

the wireless is made easier by having this package
linux-wlan-ng

other than those two, the rest works nice.

i'm quite happy so far.
thanks everyone for the help.

---

### Post by Longwing on 2007-10-23
I'm glad to hear that it worked.

Did you notice any speed gains for dropping the Ubuntu packages? I run Xubuntu myself, but I never bothered to remove the Ubuntu packages from the system.

---

### Post by tlie on 2007-10-30
longwing, sorry for late reply. i did check back this post a few times and just noticed you have reply on page 2. i thought it was only single page...

after dropping the packages not needed by xubuntu, the speed i can notice is when it starts login first time graphically after i type user & password.

but loading from the text (where there's list of OKs), it still takes time...

so far ok now, still slow compared to my 2.4Ghz PC :)
but i'm happy to use ubuntu than winxp now.

currently i'm doing upgrade to gutsy 7.10

---

