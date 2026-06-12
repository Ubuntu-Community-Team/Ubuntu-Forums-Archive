---
title: "Ubuntu(hardy heron) wont turn off completly"
date: 2008-08-24
forum: General Help
---

### Post by chec69 on 2008-08-24
Hello, this is my first post, and im also new to ubuntu, please be easy on me because it is still kinda of confusing all this.

Well the thing is that i was having problems booting up since i have a dual boot, and every time i wanted to go on ubuntu i had to edit the grub menu (i had to put ....[/dev/sda1 ro acpi=off noapic] because the problem was the APCI), but this wasnt permanet and i wanted it to be. I Search here on the forums and found this [http://ubuntuforums.org/showthread.php?t=335347]("http://ubuntuforums.org/showthread.php?t=335347")g 
I followed the instructions as the dude said, but now im having problems when i have to turn off the pc because after everything is unmounted at the it says 
[ 2... sum numbers] system now will halt or something like that.
unless this is normal, i would love to have a solution for this.

thanks

Chec69

---

### Post by GenesisV2.0 on 2008-08-24
are you shutting down from a command line or custom command something like this 

Sudo shutdown now 

if so you need to put the -P flag after so it powers off after the system has halted

Sudo shutdown now -P

this is the only thing i could think of but you probably though of that already

---

### Post by chec69 on 2008-08-24
well i though but i didnt try.
after i did it keeps happening
i have a screen shot of it
[http://i373.photobucket.com/albums/oo172/chec69/DSC01332.jpg]("http://i373.photobucket.com/albums/oo172/chec69/DSC01332.jpg")
i can try to put back the menu.lst back how it was but again i would have to edit it every time i boot up 
any sugestions..

---

### Post by YouSmeg118 on 2008-08-24
Terminal > sudo shutdown -h now

---

### Post by chec69 on 2008-08-24
still, 
this is part of the menu.lst file that i had to mod for the boot
turning the apci off
-------------------------------------------------------------------------------------

## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=50433958-8145-43b9-9d44-3ae0f112d76c ro acpi=off noapic
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=50433958-8145-43b9-9d44-3ae0f112d76c ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
-------------------------------------------------------------------------------------

---

### Post by Uchiha_madara on 2008-08-25
1 - Click The Right Click >>> click on Add Launcher>>

2 - change it from Application to Application in terminal

3 - in the Command text box Type :
> sudo halt now


4 - change the icons if you need and Type the name of the Launcher

Note : this order sometimes need a password

---

### Post by chec69 on 2008-08-25
thanks, but the problem persist 
now is like 
[865.######] system halted
ill put back the menu.lst as it was since it wasnt giving me that prob.

o i forgot

im using a sony vaio vgn-n365e it might have issues since the hardware on this laptop is kinda of weard, the original drivers are for win vista and even on xp it have some problems.

---

### Post by -Zeus- on 2008-08-25
the reason it's not working is because ubuntu is unable to pass the power off command to the computer because ACPI is off.  once it says halted, it is safe to pull the plug/hold down power button.  I would recommend reenabling ACPI

---

### Post by chec69 on 2008-08-25
thanks
i some how was thinking of that but i wasnt feeling shure about it
another issue if with the battery before this ubuntu was able to tell me when the battery was discharging or when was on ac.. but now it doesnt. i know its probably because the acpi is off.

well if i put the menu.lst back how it was it  would not boot up and it will stop before booting up.
how can i reenable the acpi when the OP is up and running?

---

### Post by chec69 on 2008-08-25
ok
i restored menu.lst just how it was 
the system halt thing is not happening anymore, now the screen just turns off, but the green light its still on
i think the acpi is on  because the batery icon is back, and the problem booting up symply dissapeared
idk, i woul love sum explanation, but as im new to ubuntu and to linux i guess ill find it on the way

---

