---
title: "Suspend to Ram waked up by Multimedia Keys"
date: 2008-05-01
forum: Hardware
---

### Post by LordFarquaad on 2008-05-01
Hi,

Since Hardy suspend to ram seems to work really better on my laptop. However I have always add the problem that the multimedia keys wake up my laptop when it is suspended. This is really annoying because those keys are situated on the front of my laptop, and are thus randomly pressed when I put it in my bag…

I have a Zepto Znote 6615WD laptop with nVidia Geforce Go 7600. Notice that I have never tried other operating systems on it (I bought it with a clean HDD) so I don't know if this problem is hardware or software (or even BIOS?) related…

Any suggestions on what I could try*? If someone could confirm that it is an hardware problem I would contact the alter-sales service…

---

### Post by LordFarquaad on 2008-05-04
*Bump**!

This issue is very annoying so I would really appreciate any help…

As a temporary fix/workaround, perhaps is it possible to set up suspend to ram so that it does not wake up when the lid is closed? Or at least so that it goes back suspending in such a case. What would be the best way to do that?

---

### Post by Zorael on 2008-05-04
I believe the BIOS decides this; check if there are any such settings in your system setup.

---

### Post by LordFarquaad on 2008-05-05
There is no such setting in my bios, it is very restricted: I can't even set a password&#8230;

---

### Post by highfructose327 on 2008-05-05
LordFarquaad, 
here is a post that I used to wake with the keyboard or mouse.
I did not try to set it to a specific key so not sure if this is exactly what you are looking for but I can strike any key and it will wake. 


[http://ubuntuforums.org/showthread.php?t=711747]("http://ubuntuforums.org/showthread.php?t=711747")

good luck

---

### Post by highfructose327 on 2008-05-05
I used this

[HTML]
cat /proc/acpi/wakeup[/HTML] 

to see my usb locations and then tried each using 
[HTML]
echo "USB*" > /proc/acpi/wakeup[/HTML] 
mine keyboard was at  "USB0" no the most elegant way to determine it but it 
worked for me

I used a script

[HTML]#!/bin/bash
 echo "USB0" > /proc/acpi/wakeup[/HTML]

I named it wake.sh and placed it in /etc/init.d/
then followed this post [http://ubuntu.wordpress.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/]("http://ubuntu.wordpress.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/")

so then I ran
[HTML]sudo update-rc.d wake.sh defaults[/HTML]

and then

[HTML]
 cd  /etc/init.d/[/HTML]

and finally

[HTML]sudo chmod +x wake.sh[/HTML]

that was it for me.

---

