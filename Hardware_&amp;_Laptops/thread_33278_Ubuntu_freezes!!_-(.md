---
title: "Ubuntu freezes!! :-("
date: 2005-05-10
forum: Hardware &amp; Laptops
---

### Post by supermarchino on 2005-05-10
XP2600 on a KM266 mobo from HP (I wonder mobo's brand...) OS randomly freezes!! :-( It seemed connected to using network (actually I have some smbfs mount points and smb printers), I also tried to disable onboard lan chip, using a pci ethernet card, but no way! I'm using also athcool 0.3.10, but disabling it does not solve issue. What else to try? :-( :-(
PS: winxp runs fine on this machine, and fedora 3 did too...

---

### Post by supermarchino on 2005-05-11
it seems it has to do with smb shares....  :roll:

---

### Post by nocturn on 2005-05-11
[QUOTE=supermarchino]it seems it has to do with smb shares....  :roll:[/QUOTE]

If you have an Nvidia card, make sure you do not have the XID errors (in the Xorg log file).

They cause a lot of system freezes.

---

### Post by supermarchino on 2005-05-11
[QUOTE=nocturn]If you have an Nvidia card, make sure you do not have the XID errors (in the Xorg log file).

They cause a lot of system freezes.[/QUOTE]

I got ATI RADEON VE (7000)

---

### Post by Sniffer on 2005-05-11
Warty has freeze on mine because of a buggy Squid package (Original released on warty).....

This is the problem on Lin...we never know from where it come....

---

### Post by supermarchino on 2005-05-11
[QUOTE=Sniffer]Warty has freeze on mine because of a buggy Squid package (Original released on warty).....

This is the problem on Lin...we never know from where it come....[/QUOTE]


what's squid?

anyway I think it's a default chartset problem, since it happens mainly when I open smbfs folders, with file names with à è é ì ò ù, where is said 'invalid encoding'...

how can I set ISO 8859-15 as default character set?

---

