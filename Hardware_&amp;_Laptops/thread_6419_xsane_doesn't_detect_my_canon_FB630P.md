---
title: "xsane doesn't detect my canon FB630P"
date: 2004-11-28
forum: Hardware &amp; Laptops
---

### Post by plebeien on 2004-11-28
hi everybody

after several months trying to find a good GNU/linux distro, I've found Ubuntu and I might say that he rocks. big thanks to the developpers.

one problem I got with it (all the distros I've tried) is that my Canon FB630P isn't recognized at all by xsane, I've tried under the user and root account but can't get it to work. there's nothing but xsane program and libraries.

doing a dmesg | grep lp0 I've got this line : 
[INDENT]lp0: using parport0 (interrupt-driven).[/INDENT] 
doing a  dmesg | grep parport0 I've got these lines : 
[INDENT]parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
lp0: using parport0 (interrupt-driven).[/INDENT]

at this point is there anything wrong ?

I've got the scanner in SPP mode under bios for compatibity issues under Windows. (seems canon and chipset VIA don't like each other) and I've put force nibble without the # in  /etc/sane.d/canon_pp.conf

/dev/lp0 doesn't exist but /proc/sys/dev/parport/parport0 does

at the end, does someone have an idea to make it work ?

respectfully

---

### Post by plebeien on 2004-11-28
just something that seems strange, I've made a dmesg | grep 1284 and nothing about ieee1284 neither when I do a lsmod.
there's nothing talking about it, is there a problem ? should it appear in some way ?

---

### Post by Soulman on 2004-12-12
I have a Canon FB620P which is also a parallel port scanner.  In order for me to get it to work I had to uncomment canon_pp in /etc/sane.d/dll.conf.  Once that was done.  I ended up having to run xsane as root.  Sometimes I'll have to power down and plug the scanner back in.  On the whole though it works fine.  Hope this helps.  I do though want to know how to allow a regular user to use the scanner instead of being in root.  Hope this helps! :)

---

### Post by plebeien on 2004-12-23
thanks Soulman I've tried it but it doesn't work... I'll go on trying some things to see what happen.

thanks a lot the same. :)

---

### Post by plebeien on 2004-12-23
In fact it works, I just have to uncomment Force Nibble in canon_pp.conf to get it to work but I got the same problem with the root rights... it works, it's something, it rocks really. post something if I get it to work as a normal user.

:)

---

### Post by ecadre on 2005-07-07
I'm having similar problems.

I've got this scanner (FB630P) working on this computer using Suse Linux.  All I did was to remove the # before canon_pp in "/etc/sane.d/dll.conf" and it worked.

In Kubuntu this does not work and my scanner is not detected.  Opening xsane as root does not help.

/de/lp0 exists, as does /proc/sys/dev/parport/parport0

############
dmesg | grep lp0

gives

lp0: using parport0 (interrupt-driven).

and

dmesg | grep parport0

gives

parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
lp0: using parport0 (interrupt-driven).
############

I could really do with getting this all working (as it did under Suse), but I'm not sure what to do next.

---

### Post by ecadre on 2005-07-07
OK then.............

I've now got my scanner running, but not correctly.

I went to my computer's bios settings and changed the parallel port setting to EPP.  Now I can get xsane to recognise the scanner and do a scan, but only if I run xsane as root   :(

Like the previous poster I'm going to investigate how to access the scanner with proper permissions.

---

### Post by DavidBowman on 2006-06-29
Thanks guys! The tip about setting the BIOS to EPP has saved me. :KS Let me return the favour...

The reason why you need root is because by default the /dev/parport device is not permissioned for general user access. In /etc/udev/rules.d there is a file called 40-permissions.rules. Edit the file

$ sudo vi /etc/udev/rules.d/40-permissions.rules

find the line:
[INDENT]SUBSYSTEM=="ppdev",                     GROUP="lp"[/INDENT]
and change it to
[INDENT]SUBSYSTEM=="ppdev",                     GROUP="lp",MODE="0666"[/INDENT]

(In Vim, arrow down to the line, press [End], type in 'a, MODE="0666"', press [ESC], type ":wq" and press [Enter].)

Then reboot and XSane is ready to place nicely!

---

### Post by samuelkarush on 2007-02-25
Killer info. The scanner fired up on the first try. I may have a hardware problem. though. I got  previews and scans showing mostly a black page. I played with some scanner settings and now it gets halfway through a scan and locks up, and it takes some playing around to get it going again.

 Anyone experience this?
sam

---

### Post by petform on 2007-06-14
I've tried all the suggestions posted (and many of those provided on the different web sites) but I still don't have my scanner working. Xsane (and other programmes) keep telling me that there is "no device available") :(

I'm relatively new in Linux and use Ubuntu 6.10, Edgy Eft, and don't always understand what I'm requested to do. Could someone guide me through to check whether I installed all that seems to be necessary correctly?

---

### Post by blazini on 2007-07-30
> **DavidBowman said:**
> Thanks guys! The tip about setting the BIOS to EPP has saved me. :KS Let me return the favour...

The reason why you need root is because by default the /dev/parport device is not permissioned for general user access. In /etc/udev/rules.d there is a file called 40-permissions.rules. Edit the file

$ sudo vi /etc/udev/rules.d/40-permissions.rules

find the line:
[INDENT]SUBSYSTEM=="ppdev",                     GROUP="lp"[/INDENT]
and change it to
[INDENT]SUBSYSTEM=="ppdev",                     GROUP="lp",MODE="0666"[/INDENT]

(In Vim, arrow down to the line, press [End], type in 'a, MODE="0666"', press [ESC], type ":wq" and press [Enter].)

Then reboot and XSane is ready to place nicely!I've tried this and I stann can't get the scanner to be found unless I run it as root in the terminal. Any ideas?

---

