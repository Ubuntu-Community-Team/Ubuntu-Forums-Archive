---
title: "ls_switch turning ambient light detector off"
date: 2010-01-29
forum: Hardware
---

### Post by jungle_steamtrunk on 2010-01-29
Just started into ubuntu, and must say so far it has been a very rewarding experience.

I'm running 9.10 (karmic) 2.6.31.-17generic, Gnome 2.28.1 on an Asus X56V.

I was having problems with my screen constantly going dim, tried changing settings in the power manager but to no avail. Looked up many things via google and these forums and stumbled across ls_switch.

Located in /sys/devices/platform/asus-laptop/ I used *more* to look at it then used gedit as sudo to change from 1 to 0. This did disable the ambient light detector however gedit would display the following errors

*Could not create a backup file while saving /sys/devices/platform/asus_laptop/ls_switch7* 

then

[I]Could not save the file /sys/devices/platform/asus_laptop/ls_switch.
(Unexpected error: Invalid argument)[/I]

in the terminal the following,

[I]** (gedit:5921): WARNING **: Hit unhandled case 13 (Invalid argument) in parse_error.

[/I]However the change from 1 to 0 or vice versa is made.

My question what is the correct method for changing the contents of this file?

Many thanks in advance.

---

