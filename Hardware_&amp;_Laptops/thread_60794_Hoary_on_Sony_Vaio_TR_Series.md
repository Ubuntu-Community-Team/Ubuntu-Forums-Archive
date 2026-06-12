---
title: "Hoary on Sony Vaio TR Series"
date: 2005-08-29
forum: Hardware &amp; Laptops
---

### Post by mahalram on 2005-08-29
Just installed Hoary on Vaio TR2
I had Warty previously - very happy with that - except that sleep did not work

With hoary everything works - EXCEPT SOUND

Anyone else with this laptop?


Anyway, for those of you fumbling around I'll share what I've learned so far
1. Sonypi module has been replaced with sony_acpi

2. Cannot use spicctrl for adjusting screen brighness. (spicctrl uses the older sonypi)
I dont know if there is a newer version of spicctrl for sony_acpi . But this is what you do

just do
echo "x" > /proc/acpi/sony/brt 

with x ranging from 0 to 8. 0 the lowest brightness level and 8 the highest

For activating sleep .... well I just realized that I dont remeber offhand. I'll post a follow up message very soon

The crux of it is editing an /etc/acpi file to enable sleep when the lid button is activated. Works very well. And as I said I'll post the details very soon.


Now my questions.

1. I havent tried hibernate yet. My laptop has 1GB RAM and I have a swap of 1.5GB. Can anyone let me know the procedure to activate this?

2. Sound. In Warty all I had to do was to run gnome-alsamixer and select external-amplifier down.
I somehow cannot get to do that in Hoary. The whole sound thing seems a lot more complicated in Hoary.
Can anyone direct me?

---

### Post by mahalram on 2005-08-29
Follow up: I missed a few things

I have seen people mention that Hoary automatically recognizes 1280x768

Well it does. My xorg.conf had only 1028x768 - but I still got only 1024 x 768 :( 

As with Warty I had to use 1280patch to get widescreen

For some reason this 855resolution has  never worked for me

---

### Post by mahalram on 2005-08-29
The follow-up I promised
edit /etc/acpi/events/lidbtn 

"change action=" line to

action=/etc/acpi/sleep.sh

---

### Post by mahalram on 2005-08-30
Well I managed to figure out how to use alsamixer to set external amplifier down.

Well also had a problem with realplayer. But there is already a post somewhere here which deals with that


So everything works! Ofcourse the attached camera does not. Dont know of any effort in progress either for that

Probably with the new kernel 2.6.13 - (the release notes indicates why we may be able to see some hidden 
PCI devices) there may be some hope.


And how many of you have tried ROX-FILER?

I absolutely love it!

---

### Post by netsyd on 2005-08-31
I have some of my notes from my old TR running Debian... May not help, but it has some info for the 1280 resolution junk. 

[http://www.netsyd.com/content.php?content.3](http://www.netsyd.com/content.php?content.3)

---

### Post by mahalram on 2005-08-31
[QUOTE=netsyd]I have some of my notes from my old TR running Debian... May not help, but it has some info for the 1280 resolution junk. 

[http://www.netsyd.com/content.php?content.3](http://www.netsyd.com/content.php?content.3)[/QUOTE]


The problem with the 1280-patch is that I dont know how to "undo" the patch - for instance when I need to connect to a projector I need to reboot again (and this time without involking the patch) so that I can use 1024x768 mode (projectors dont work with 1280x768)

Any of you know how to undo the patch without rebooting?

Anyway, I still havent figured out how to connect to an external monitor / projector even with the 1024x768 mode - I guess we need to use hooks in  sonypi module (now sony_acpi module) for that as the function keys are not tied to the bios.

Anyone knows how? 

By the way. When I logout the option "hibernate" is present. But does not do a good job. When I reboot it shows a messed up screen and finally I have to do a hard reboot. But as I said earlier sleep works very well. I can live with that!

---

