---
title: "Acer 7715z - 2 initial problems"
date: 2012-01-10
forum: Hardware
---

### Post by st0ne2thedge on 2012-01-10
Hi everyone

Yesterday i tried to install Ubuntu on a friends' Laptop. (model 7715z, Acer) As i booted into the live cd i noticed the screen going black as it would normaly show the Ubuntu loading screen, after a few tries, i managed to get the screen working through entering the keys which manage her laptops brightness in a random manner (this might also work with other keys haven't tried it). As i did this, the terminal as usual showed the keycharacters as a response, after whitch it succesfully showed the live system.

The above would be the first problem i'd like some help with.
secondly

While in this Live Ubuntu system her mousepad did not work @ all i followed a few standard procedures on the ubuntu guides which told me to assume this is a kernel compatability issue.

Is there a way to determine a Distribution or a version that can work on this laptop?



Best of regards

Vincent

---

### Post by FrugalNl on 2012-06-25
Hey,

I also have an Acer 7715z, im not using a debian based distro right now so
location of files may vary, solution however works on every disto i tried so far.
Im using Linux with right resolution for my card/screen.

00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller 

nano /etc/rc.d/rc.local

Add this line

setpci -s 00:02.0 F4.B=00

then do

nano /boot/grub/menu.lst

add

acpi_osi=Linux

If still doesnt work edit mobprobe.d/blacklist.conf

add viafb to blacklist

For booting in live mode choose to add line to kernel
in grub then add: nomodeset 
( works also with installed system just press "e" at grubscreen

Resolution wont be set right but u can use live cd like that
( i dont recommend this for everyday use as at least on my 
screen looks well.; ugly :-) )

Touchpad:

Can't tell if its the case with Ubuntu but with many distro's
it will work out off the box but just isn't enabled by default.
Check in settings if it's enabled.

xf86-input-synaptics needs to be installed

for tap-to-click

Click Start and then Control Panel.
Select Classic View from the left side of the window.
Double-click the Mouse icon and, then, select the Device settings tab.
Click the Settings button and, then, Tapping .
Select the Enable tapping check box and click OK .

Dont know if this stil works in new gnome, it used to be

Alt+F2

enter gconf-editor

goto /Desktop/gnome/peripherals/Touchpad

Enable tap-to-click ( restarting Gnome might be needed )


Hope it helps somehow :D

FrugalNL

---

