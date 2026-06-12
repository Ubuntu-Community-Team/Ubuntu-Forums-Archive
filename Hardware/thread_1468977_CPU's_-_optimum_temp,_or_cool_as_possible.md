---
title: "CPU's - optimum temp, or cool as possible?"
date: 2010-05-01
forum: Hardware
---

### Post by Moozillaaa on 2010-05-01
Is there an optimum temperature for processing? Or is as cool as possible the best?

And is there a way to link BIOS operating parameters ---> desktop applet? Fanspeed, temps?

---

### Post by Yellow Pasque on 2010-05-01
There's no optimum temperature, but you do want to stay below 60C, and hopefully, your system shuts off automatically at 70C or so.

On a laptop, your BIOS should control the fan through ACPI. On a desktop, you can probably use the pwmconfig script if you have BIOS fan control disabled and lm-sensors package installed.
```
sudo pwmconfig
```

---

### Post by Moozillaaa on 2010-05-01
Thanks again there! (near Pittsburgh? formerly of Greentree/Parkway West area)

I ask since I have a spare case fan, and a spare hard disk fan, and am wonderin' if either is necessary. 

I don't 'game', but do watch and will be transcoding lots of vids.

What's max 'safe' continuous temperatures? What should be warning / shutdown temps?

---

### Post by arsenic23 on 2010-05-01
> **Moozillaaa said:**
> What's max 'safe' continuous temperatures? What should be warning / shutdown temps?

It varies by processor.  Intel and AMD both have lists with this kind of data available on their websites.

---

### Post by cascade9 on 2010-05-02
> **Temüjin said:**
> There's no optimum temperature, but you do want to stay below 60C

+1. Thats what I aim for, max 60C when @ full load for any length of time. 

> **Moozillaaa said:**
> Thanks again there! (near Pittsburgh? formerly of Greentree/Parkway West area)

I ask since I have a spare case fan, and a spare hard disk fan, and am wonderin' if either is necessary. 

I don't 'game', but do watch and will be transcoding lots of vids.

What's max 'safe' continuous temperatures? What should be warning / shutdown temps?

I'd do what arsenic23 suggested, check the specification for your CPU. Then, if 'max temp is (for example) 75C, set 'shutodwn slightly under that (maybe 73C) and awrning at a tiny bit uder that (say 71C). That way you will never burn your CPU out. 

As for the case fans.....well, IMO, teh easiest way to see if you need them it to run several encoding jobs back to back, and check the temps several times durign the process. If our CPU stays under 60C, you can probably get rid of one, or both of them. Or you cccould get a fan controller and utrn them down. In some cases, fans can run at 5volts, not 12v (a lot of fans have trouble 'spinning up' at 5v, in which case you cant really use 5v). If they run at 5v, its a good idea o keep them IMO...most fans are very quite at 5v, and a bit of extra airflow wont hurt. 

There is also ways to run fans at 7v, but that is more tricky, and a (tiny) element of risk. 

BTW, dotn forget that its not quite the northern summer yet. Increase the ambient temp (like you get in summer) will increase CPU, and every other temp in the case.

---

