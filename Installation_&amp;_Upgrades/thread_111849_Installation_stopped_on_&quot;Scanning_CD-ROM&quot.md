---
title: "Installation stopped on &quot;Scanning CD-ROM&quot;"
date: 2006-01-03
forum: Installation &amp; Upgrades
---

### Post by marvaneke on 2006-01-03
When I try to install the 5.10, the installation stopped on the "Scanning CD-ROM" for loading packages.  There are no error messages, and I don't know the procedure to view the debugging messages (if there are ?).

Can someone help me ?

Regards.

---

### Post by dcstar on 2006-01-03
[QUOTE=marvaneke]When I try to install the 5.10, the installation stopped on the "Scanning CD-ROM" for loading packages.  There are no error messages, and I don't know the procedure to view the debugging messages (if there are ?).

Can someone help me ?

Regards.[/QUOTE]
If the CD-ROM is set to be a "Slave" on a channel without a Master IDE device, try changing it to Master (and enable it in your BIOS, if necessary).

---

### Post by x-ph on 2006-01-03
I have the same problem, but when i typed 'noapic acpi=off' it worked. you'd better give more info about your computer i think... hupe you solve the problem. i can't install ubuntu too, ihave problems with the X server...

---

### Post by djlilyazi on 2006-01-04
[QUOTE=marvaneke]When I try to install the 5.10, the installation stopped on the "Scanning CD-ROM" for loading packages.  There are no error messages, and I don't know the procedure to view the debugging messages (if there are ?).

Can someone help me ?

Regards.[/QUOTE]


mine stopes at the same step too...what can i do ?

---

### Post by vasudevank on 2006-01-04
does any other bootable cd, or linux distro cd work?

---

### Post by djlilyazi on 2006-01-04
[QUOTE=vasudevank]does any other bootable cd, or linux distro cd work?[/QUOTE]

i tried Knoppix it gave me disabling IRQ#10 that was the end of it...so it did not work for me

---

### Post by marvaneke on 2006-01-05
I think I have know isolate the problem, since I have change the CD/DVD writer to a basic CD reader.  The problem is the same.

I think that the problem come from the SATA disk, and the (bad) use of the IRQ 18.  This problem is reported on [http://www.us.debian.org/releases/stable/debian-installer/](http://www.us.debian.org/releases/stable/debian-installer/), "SATA driver can block access to CD drive in installations from CD".  I have tried to disable all of the modules except these mentionned, with no success.  

I have tried to boot with different parameter like "noacpi", disabling the usb, and so on.  It seems (with dmesg) that the acpi and the usb is still loaded.  

I am desesperate.  So, I address this message to Mark Shuttleworth, please help us.

Can someone from the debian team, or some expert answer us ?

Can someone tell me where I must post these thread somewhere else to contact some experts.

Regards

06-jan-2006 11:23 : This thread is still active.  Can someone hep me ?

---

### Post by djlilyazi on 2006-01-08
[QUOTE=marvaneke]When I try to install the 5.10, the installation stopped on the "Scanning CD-ROM" for loading packages.  There are no error messages, and I don't know the procedure to view the debugging messages (if there are ?).

Can someone help me ?

Regards.[/QUOTE]

this is how i fixed my exact problem i changed BIOS Settings to Native-Mode...

thats it...

---

