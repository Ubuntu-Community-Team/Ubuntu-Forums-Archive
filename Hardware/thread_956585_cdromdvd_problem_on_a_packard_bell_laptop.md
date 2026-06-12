---
title: "cdrom/dvd problem on a packard bell laptop"
date: 2008-10-23
forum: Hardware
---

### Post by ludovic889 on 2008-10-23
hi,

I have un little problem. I installed a kunbuntu distribution on my Packard Bell EasyNote laptop (SW51-101 AMD Turion 64x2) a year ago.

But, this morning, I realized that my NEC DVD-RW ND-6750A drive ([http://support.necam.com/Optical/nd6750A.asp]("http://support.necam.com/Optical/nd6750A.asp")) encounters some issue: when I introduce a blank cd/musical blank/commercial dvd, nothing happens. The drive seems work, but none icon appears in my desktop. I believe that one can say "the cdrom is unmount". 

I exposed my problem on a french thread ([http://forum.ubuntu-fr.org/viewtopic.php?pid=2146357#p2146357]("http://forum.ubuntu-fr.org/viewtopic.php?pid=2146357#p2146357")), but no solution was found. I notice in the bios that my drive still works (not dead). My version of kubuntu is Ubuntu 8.04.1 and my kernel is 2.6.24-21-generic.

Can you help me ?

thanks,
Ludovic

---

### Post by teaker1s on 2008-10-25
sounds like hardware failure. If you have a live boot cd can you boot that. does the drive light seem to run a long time?

---

### Post by H_a_D_3_z on 2008-10-25
I seem to have the same problem.  I upgraded to Intrepid via sudo apt-get upgrade from Hardy, it worked before the upgrade.  The drive is an  Optiarc  DVD RW AD-7563A.  I can even burn an ISO file using blank disc, what have you.  It will run normal, and eject.  When i put the disc back in WOW nothing is on disc.  Speak up people if you have the same prob.

---

### Post by ludovic889 on 2008-10-26
hi,

thank you for your replies.

**teaker1s**
i haven't a live cd, but a simple installation cd. the cdrom can boot on the ubuntu cd.

**H_a_D_3_z**
so, my problem may not be specific to my settings ? i can try to search for similar issues on this forum...

any other idea ?

thank a lot
ludovic

---

### Post by teaker1s on 2008-10-26
in this instance it sounds like ubuntu issue, rather than hardware failure.

There also appears to be some bug reports for recent kernels not detecting drives:-haven't found a definitive solution yet.

In this instance if it was a desktop I would suggest looking to see if there is a drive firmware update.

what does your bios call the drive-ie make/model
have you checked your logs

---

### Post by ludovic889 on 2008-10-26
hi,
I forgot to precise that I'm not a hardware wizard ....
;)


Where can I find the log files ?

Ludovic

---

### Post by teaker1s on 2008-10-26
both the links are worth a look, they explain how logs work and how to find them:-more often than not they give clues to help solve a problem.


[http://www.cyberciti.biz/faq/ubuntu-linux-gnome-system-log-viewer/]("http://www.cyberciti.biz/faq/ubuntu-linux-gnome-system-log-viewer/")


[https://help.ubuntu.com/community/LinuxLogFiles]("https://help.ubuntu.com/community/LinuxLogFiles")

---

### Post by ludovic889 on 2008-10-26
thank for this explanation.
but I don't know what I'm looking for ........

I suppose I have to inspect /var/log/kern.log to see if something is wrong. right ? for instance, I have ACPI errors.

i'm right ?

---

### Post by teaker1s on 2008-10-26
Acpi errors could point to your problem, for instance if you have acpi errors in effect your hardware will disappear from ubuntu. I always find that googling the errors will help pinpoint them and a solution:popcorn: process of elimination.

---

### Post by ludovic889 on 2008-10-26
hi,

i found a first error
**ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.**
-> [http://ubuntuforums.org/showthread.php?t=629707]("http://ubuntuforums.org/showthread.php?t=629707"): it's a battery bug, but seems to work properly. I follow the advice and reboot. The error disappears.

thank google !

after the reboot, it remains some bug (a port usb doesn't work)
[B]Oct 26 13:24:56 mycomputer kernel: [    0.000000] usb 1-4: device descriptor read/64, error -62
Oct 26 13:24:56 mycomputer kernel: [    0.000000] usb 1-4: device descriptor read/64, error -62
Oct 26 13:24:56 mycomputer kernel: [    0.000000] usb 1-4: device descriptor read/64, error -62
Oct 26 13:24:56 mycomputer kernel: [    0.000000] usb 1-4: device descriptor read/64, error -62
Oct 26 13:24:56 mycomputer kernel: [    0.000000] usb 1-4: device not accepting address 5, error -62
Oct 26 13:24:56 mycomputer kernel: [    0.000000] usb 1-4: device not accepting address 6, error -62
Oct 26 13:24:56 mycomputer kernel: [    0.000000] phy0 -> rt2500usb_init_eeprom: Error - Invalid RT chipset detected.
Oct 26 13:24:56 mycomputer kernel: [    0.000000] phy0 -> rt2x00lib_probe_dev: Error - Failed to allocate device.[/B]

some idea ?

---

### Post by teaker1s on 2008-10-26
[http://ubuntuforums.org/showpost.php?p=5540650&postcount=6]("http://ubuntuforums.org/showpost.php?p=5540650&postcount=6")
explains how to disable modules should you wish,they are wifi
Now I don't know the solution from what I can see so far, but I've had an Idea. have you tried boot options.
[https://help.ubuntu.com/community/BootOptions]("https://help.ubuntu.com/community/BootOptions")


some we have tried also listed in this wiki page-trial and error
[https://wiki.ubuntu.com/HP_dv6000_Series#Introduction]("https://wiki.ubuntu.com/HP_dv6000_Series#Introduction")

---

