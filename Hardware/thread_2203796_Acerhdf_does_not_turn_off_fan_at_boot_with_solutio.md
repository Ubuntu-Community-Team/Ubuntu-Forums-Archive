---
title: "Acerhdf does not turn off fan at boot with solution"
date: 2014-02-05
forum: Hardware
---

### Post by Huib123 on 2014-02-05
Using Ubuntu 12.04 LTS on Acer A0A 110 and parameters set to overide BIOS controle by acerhdf it switches off the fan only after exceeding fanon temperature and subsequently dropping below fanoff temperature.
Attemps to manage this by using parameters failed.
Finally I got the fan  switched off at boot by changing the file acerhdf.c  (to be found on [http://www.piie.net/?section=acerhdf](http://www.piie.net/?section=acerhdf)) the line
static unsigned int fanstate = ACERHDF_FAN_AUTO; into
static unsigned int fanstate = ACERHDF_FAN_OFF;
Compile by going to the directory where you have stored the file acerhdf.c and in termal do

make
sudo make install

and reboot

For safety reasons check if the fan switches on above fanon temperatures e.g. by executing dmesg | grep acerhdf in terminal.

---

### Post by joao-ildefonso on 2014-08-14
Hello [COLOR=#000000]Huib123

I'm having the same problem with my d150 with 14.04 Trusty

I've installed the **acerhdf **without any problem, and it works on activating the fan.
But as soon as the temperature drops bellow the fanoff point, it does not silences.

I try'ed to recompile as you sugested (for kernel 3.13), but gives me a lot of errors:

[/COLOR]acerhdf.c:364:2: error: too few arguments to function ‘thermal_zone_bind_cooling_device’

Did you experience the same thing?

Thanks in advance for your previous post.

Regards,

Joao

---

