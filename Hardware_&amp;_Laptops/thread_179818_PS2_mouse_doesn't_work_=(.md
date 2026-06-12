---
title: "PS/2 mouse doesn't work =("
date: 2006-05-20
forum: Hardware &amp; Laptops
---

### Post by SiGen on 2006-05-20
Hi.

I just installed Ubuntu 5.04 on my Compaq Presario 725LA laptop. How do I get the PS2 mouse to work? I just connected my 3 button optical and wired mouse to the PS2 port, but is not recognized and doesnt work =(
Touchpad works perfectly.

Help please.

Thanks

---

### Post by Hugo Bio on 2006-05-21
I need some help there too... I got a new ATX Form Card (2 Usb + PS/2 + IR) for my Mobo, and the USB ports works great (i get my printer listed when i lsusb). The problem is that my PS/2 Optical mouse isn't working! I tryied everything... 
cat /proc/bus/input/device do not show my mouse... The red lights are up, and i tested it within my m$ machinhe, and it works flawlessly....

It's a simple 3 buttons mouse! What should i put in xorg.conf? I tryied Intellimouse, PS/2, ExplorerPS/2, Auto... nothing seems to work! Help woudl be appreciated!](*,)

---

### Post by gesho on 2006-05-23
the same problem on dell inspiron
mdetect says 9 logitec ttyS0 mouse detected, but only touchpad works.
in Mandriva/KDE there was a little check, for PS2 mouse, here can't find it. touchpad works, external mouse doesn't.
do I need some package or config?
what is gpm?

---

### Post by SiGen on 2006-05-23
I found the solution:

*open the terminal

*Then write: sudo gedit /etc/modules

*find the line that has plain ole psmouse and change to

psmouse proto=imps

*save and reboot

Touchpad and mouse both work :D

---

### Post by gesho on 2006-05-23
> psmouse proto=imps
i tried both proto=imps and proto=bare, still, touchapad works, external ps2 mouse doesn't.

---

### Post by dannyboy79 on 2006-05-28
i just read in another thread about fedora core 3 that they were having the same problem and it is solved by adding psmouse.proto=imps as a boot parameter. You can add it as an option to grub.conf and a lot of people confirmed that that made a external ps2 mouse work. Also, look in your bios and see if you can disable the touchpad and others have said that that made the ps2 mouse work as well. I haven't tried it yet but I was going to later today cause I gotta go to a wedding. Hope you guys get it working!

---

### Post by Micke.Breath on 2006-06-04
I found that after I upgraded to Dapper (6.06) my ps/2 mouse that had been working using the workaround above stopped working again - but thanks to others I found the solution.

open a terminal

sudo gedit /etc/rc.local

then type in

modprobe -r psmouse
modprobe psmouse proto=imps

I placed this before the exit 0 line

save and restart - should have your ps/2 mouse back - again

---

### Post by Carandol on 2006-06-05
I've tried the original workaround on my IBM Thinkpad T21, and your workaround, and I'm still having no joy with my PS2 mouse.

---

### Post by giefferre on 2006-06-06
[QUOTE=Micke.Breath]I found that after I upgraded to Dapper (6.06) my ps/2 mouse that had been working using the workaround above stopped working again - but thanks to others I found the solution.

open a terminal

sudo gedit /etc/rc.local

then type in

modprobe -r psmouse
modprobe psmouse proto=imps

I placed this before the exit 0 line

save and restart - should have your ps/2 mouse back - again[/QUOTE]


OH, FINALLY!
It works fine :)
Thank you!

---

### Post by alvenegas on 2006-06-07
I've  got another problem regarding the mouse.  Although I do not have 
problems with the external mouse, I do have a weird behavior of the mouse.
And that  is randomly getting stuck for a few seconds and sometimes 
running around the screen pretty fast.  This is happening on Dapper (thought
upgrading would get rid of it) and it is independently of a PS/2 mouse is 
connected or not.  Any of you having the same problem?

---

### Post by ulugeyik on 2006-11-06
yes, I have the same problem, on XUbuntu. I was thinking of upgrading to edgy to avoid it.

it is a dell inspiron 8100. first i disabled the pointer-stick and touchpad works but it has these short freezes the previous poster mentioned, if I attach a ps/2 mouse. everything hangs. grr.

---

