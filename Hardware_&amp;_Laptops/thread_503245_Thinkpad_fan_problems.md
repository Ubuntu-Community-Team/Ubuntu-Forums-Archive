---
title: "Thinkpad fan problems"
date: 2007-07-17
forum: Hardware &amp; Laptops
---

### Post by ScarletPimpernell on 2007-07-17
Hi guys.

I realise there are already a couple of threads regards this issue, but none have sufficed as a satisfactory fix for this particular problem.

I have a refurbished thinkpad T42 which I have just bought exclusively for use with Ubuntu and I like it very much.

Unfortunately though the fan is always running, and the noise created is annoying to put it mildly.

Can anyone shed light on why the fan would always be running? I would have thought that the fan should only kick in to keep temperatures in check when necessary, but I'm no expert by any means.

Perhaps the fan can be set to kick in to keep temperatures below, oh I don't know... 65?

An 'acpi -t' displays that the temp is currently; Thermal 1: ok, 43.0 degrees C

Does anyone know if this is a bios issue or an OS issue?

If anyone has experience with fixing this problem within Ubuntu, I'm sure there's lots of other thinkpad users besides myself who would find that information beneficial both now and for future reference.

Thanks in advance

---

### Post by ScarletPimpernell on 2007-07-17
[http://thinkwiki.org/wiki/ACPI_fan_control_script#Variable_speed_control_scripts](http://thinkwiki.org/wiki/ACPI_fan_control_script#Variable_speed_control_scripts)


For future readers of this thread;

Download the tp-fancontrol script from the above link, save it somewhere.

cd to where you saved it and 'sudo ./tp fancontrol'

Seems to be working so far for me. :)

---

### Post by vegetable on 2007-08-31
i've been trying to use this script but am getting syntax errors


fan.sh: line 201: syntax error near unexpected token `<'
fan.sh: line 201: `    read X Y1 Y2 Y3 Y4 Y5 Y6 Y7 Y8 Z1 Z2 Z3 JNK < <(echo "$THERMAL") '

anyone know what could be causing this?

---

### Post by vegetable on 2007-09-04
anyone?

---

### Post by softtower on 2007-09-05
A few questions:
- Do you have an embedded or dedicated video card?
- What is the actual speed of the fan?

To answer the 2nd question you can run
```
$ cat /proc/acpi/ibm/fan 
```

Also, check if your CPU frequency scaling works. [Read about that here]("http://www.fredrikbergstrand.se/?cat=8").

The thing is that all ThinkPads with dedicated video cards will run fan most of the time (depends on ambient temperature). Mine switches from 2,800rpm (almost silent) to about 3,600rpm (tolerable) all the time.

---

### Post by vegetable on 2007-09-05
i have the ati m300 dedicated card
and my cpu temp, during normal usage is around 52-56 C
my GPU is around 54C and my fan is running at 4100RPMS

---

### Post by bomanizer on 2007-10-30
> **softtower said:**
> 
The thing is that all ThinkPads with dedicated video cards will run fan most of the time (depends on ambient temperature). Mine switches from 2,800rpm (almost silent) to about 3,600rpm (tolerable) all the time.

This is true. My R50 is using "sensible" trip-points with this script, but it doesn't step down once it's started. On Windows (yes, again... :)) the fan stops after cooling from heavier usage. On Ubuntu, a constant hummmmm.....

-Regards

UPDATE:

Hehe, after posting this my fan stopped.. :D Seems that the tp-fancontrol-script is a winner here. I thought that the behavior would be the same as with previously on Feisty, but it seems that Gutsy brought something new to this subject, cool.

---

