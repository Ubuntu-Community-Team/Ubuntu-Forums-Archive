---
title: "Sony laptop acpi problem."
date: 2006-09-13
forum: Hardware &amp; Laptops
---

### Post by svizi on 2006-09-13
Hi, 

I installed ubuntu 6.06 on a Sony vaio vgn-fs315s. Unfortunately the acpi doesn't work at all. When i unplug the dc converter the laptop works but when  i plug it back in it shuts down like you gave it from the terminal halt. I don't know what to do. It used to work fine with the previous ubuntu version. Should i go back or should i install a newer package ? I don't know if this is a gnome problem.

---

### Post by coffeecat on 2006-09-13
I know this is not particularly helpful but acpi is working fine in Ubuntu Dapper (Gnome) on my Sony Vaio VGN-FS215B laptop. I don't know what the hardware differences are between the two models.

---

### Post by anchois on 2006-09-13
Hi,

I have a VGN-FS315e (I think that the only difference is video card).
ACPI works almost beautifuly with it.
There is just a small problem with gnome-power-manager that doesn't
report accurately the battery remaining capacity/time.
By default gnome-power dapper profile is to hibernate the computer
if it reachs 5% or so of the battery (on battery power).
I just deactivate this action in 
Menu -> System -> Preferences -> energy settings (sorry I have this item
in french and don't know the correct translation)
then on the tab "on battery" when "critical level of the battery" 
(last item at the bottom of the windows) choose : "Do nothing"

Hope it helps

Cheers,
F.

---

### Post by anchois on 2006-09-13
Forgot one thing,
if it doesn't resolve your problem and
want to go deeper:

all the acpi scripts that deal with battery/ac power or other stuff
are in /etc/acpi

I think that the one responsible for doing something on plugging
or unplugging the dc adapter is /etc/acpi/power.sh.
The quick and dirty way will be to rename this script (root or sudo) 
to something else, so that it can't be run by acpi events...

---

### Post by svizi on 2006-09-13
I found out that the system is shutting down only when battery is fully charged. I'll see what happens when battery is fully charged implementing your solution.

---

### Post by anchois on 2006-09-13
Please, add the last lines before the shutdown of the computer of
/var/log/acpid
to see what the acpi daemon is doing to turn the computer off.

---

### Post by mainmojo on 2006-09-13
This is a know issue with gnome-power-manager and yes, it mostly occurs when your battery is fully charged and no, sony laptops aren't the only ones affected. Please go to launchpad.net (search for bug #33072) to see extensive dialogue over this issue. I have a sony laptop VGN-FS790 and there are a couple of comments I made - look at the comment log for Dennis and the suggestions I received. I hope this helps. Also, you might want to subscribe to the bug to receive regular updates.

---

### Post by svizi on 2006-09-13
It seems that anchois solution to revert to "do nothing" when battery is critical works. Thanks mainmojo for your suggestions.

---

### Post by jko21 on 2006-09-13
Hi,

I have a vaio-fe21m. I also faced some problems with the acpi, after the first installation of ubuntu. When i unpluged the a/c, immediately there was a message that the battery was empty and the pc shuted down. I did again another install (i had more problems, mostly with the programs i installed) and then i didn't have so many problems. 
The complete solution to all that came after a kernel compile i did (a friend helped me with the entire process, i am newbie:)).I never had acpi problems again. So i believe that you should also trie it. 
Good luck:)

---

