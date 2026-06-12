---
title: "Acer TM 8104 Powermanagement"
date: 2006-08-29
forum: Hardware &amp; Laptops
---

### Post by martin_d on 2006-08-29
I recently installed Kubuntu on my Acer Travelmate 8104. What is the best way to increase the battery lifetime? I am using powersaved with kpowersave, but I am not sure if it is the best way.

---

### Post by hizaguchi on 2006-08-29
Dim the screen, reduce the processor speed, avoid using hardware 3D acceleration, avoid reading from and writing to the hard drive, disable the wireless and bluetooth when not in use, and if you have a dual core processor use a non-SMP kernel when you need to conserve battery life.

---

### Post by danielfm123 on 2006-11-24
battery least only 1:40 on windows it least a least 3:00
the fan is always on and cpu temperature never less than 49º
i tried everithing

list of what i did
configure ati powerplay with aticonfig (using fglrx)
configure acpi tables with the DDST
configure cpu thrtling for powersaving
turned of wifi and bluetoot (buttons working)

oyher probles is that gnome batery level shows only wrong data i have to use acpi -t

now im using windows xp.... i really miss my loved amarok and gnome please help

i just cant find help on web about his
i need mi long live battery

---

### Post by martin_d on 2006-11-25
> **danielfm123 said:**
> battery least only 1:40 on windows it least a least 3:00
the fan is always on and cpu temperature never less than 49º
i tried everithing

list of what i did
configure ati powerplay with aticonfig (using fglrx)
configure acpi tables with the DDST
configure cpu thrtling for powersaving
turned of wifi and bluetoot (buttons working)

oyher probles is that gnome batery level shows only wrong data i have to use acpi -t

now im using windows xp.... i really miss my loved amarok and gnome please help

i just cant find help on web about his
i need mi long live battery

Did you patch the right DSDT into the DSDT? There are several versions for the TM 8104!!!

Check the config files in /etc/powersave, perhaps something is wrong there (set cpu thorttling to 50%!) ?

Are you using Dapper or Edgy?

---

### Post by danielfm123 on 2006-11-25
i´m using edgy
cpu was @ 800 mhz (max speed 2000mhz)
and i trued all the DSDT, the S3F05 is my bios ver
with S3F05, even the suspend worked
i dont remember testing temperature with other DSDT

---

### Post by danielfm123 on 2008-04-22
suposed to be fixed here
[http://www.ubuntu-forum.com/showthread.php?t=539365](http://www.ubuntu-forum.com/showthread.php?t=539365)

---

