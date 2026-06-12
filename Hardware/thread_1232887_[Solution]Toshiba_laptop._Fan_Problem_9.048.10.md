---
title: "[Solution]Toshiba laptop. Fan Problem 9.04/8.10"
date: 2009-08-06
forum: Hardware
---

### Post by fatigue on 2009-08-06
Most of recent toshiba laptop have a problem with 9.04 and 8.10
Fan runs all the time and they never turn fan them off even though cpu temerature is less 30C

Here is a solution

open /boot/grub/menu.lst with a text editor 

For instance, if you use emacs
```
sudo emacs /boot/grub/menu.lst
```Scroll down and find your ubuntu

"
## ## End Default Options ##

title Ubuntu 9.04, kernel 2.6.28-11-generic
uuid 55b3c634-36c5-4a06-b8ec-8d51a8cb97d4
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=55b3c634-36c5-4a06-b8ec-8d51a8cb97d4 ro quiet splash
initrd /boot/initrd.img-2.6.28-11-generic

Add acpi_osi="Linux" after
"kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=55b3c634-36c5-4a06-b8ec-8d51a8cb97d4 ro quiet splash "

Fixed line should be 

kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=55b3c634-36c5-4a06-b8ec-8d51a8cb97d4 ro quiet splash acpi_osi="Linux"

and then save and restart
This should fix fan problem in toshiba laptops

---

### Post by Juno Eclipse on 2009-11-01
Unfortunately, this workaround did not fix anything for my Toshiba L505-10P laptop...once the fan is at its full speed, it never run more slowly even with a core temperature of 30°C

---

### Post by Sader on 2009-11-01
Ok man, had the same issue today with my new work Sattelite L500. After getting on high speed, fan simply wount come back to low speed after certain time...
Actually described above solution will work, only after you will recheck if you have acpid daemon running. Had no luck after adding acpi_osi=Linux to kernel boot line...
However after I started acpid service and rebooted -everything working fine...
pls check & let me knwow in case this helps

---

### Post by infinities on 2009-11-02
My toshiba doesn't have a /menu directory? :/

---

### Post by jenaniston on 2010-01-31
> **fatigue said:**
> 
Add acpi_osi="Linux" after
"kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=55b3c634-36c5-4a06-b8ec-8d51a8cb97d4 ro quiet splash "

Fixed line should be 

kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=55b3c634-36c5-4a06-b8ec-8d51a8cb97d4 ro quiet splash **acpi_osi="Linux"**

and then save and restart
This should fix fan problem in toshiba laptops

I will definitely look more into something like this . . .

I am trying to stop or slow down a constant running fan with Ubuntu 9.04 OS full install USB
 running on a Sharp AL27 laptop, with hddtemp showing in the low 30 C. degrees.

---

### Post by borabosna on 2010-03-22
> **infinities said:**
> My toshiba doesn't have a /menu directory? :/
What about /boot/grub/grub.cfg ? I don't have a menu.lst file either.

---

### Post by Sader on 2010-04-20
Update on fan issue with Toshiba.....
Apparently it has some connections with Ati drivers & Powerplay function.
Fan started to work nice after installation of the Ati Fglrx drivers via Ubuntu Utility......this is on Ubuntu 9.10(presume earlier versions would be the same)
Did not add anything to kernel line.
acpid is started upon boot

Thanks
sader

---

### Post by Gotit on 2010-05-16
> **borabosna said:**
> What about /boot/grub/grub.cfg ? I don't have a menu.lst file either.

No you don't want to edit that file.

Depending on what version you are running you may need to edit /etc/default/grub as I did with LL 10.04.

First make a back up copy of the default grub file:
```
cd /etc/default
sudo cp grub grub.bk
``` 

Then open grub for editing:
```
sudo gedit grub
```

Then change this line:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

To read:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash  acpi_osi="force""
```

Then to get "acpi_osi=force" automatically added to /boot/grub/grub.cfg and new kernels when they are installed:
```
sudo update-grub
```
Reboot

Note: I tried "acpi_osi="Linux" but that didn't seem to do anything for my A205 Toshiba.  Using "force" the fan runs slower at/after boot and speeds up around 56C and slows down again around 54 C.  At no time have I had the fan stop or run so slow I could not hear it.

---

