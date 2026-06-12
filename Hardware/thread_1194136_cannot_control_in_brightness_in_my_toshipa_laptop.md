---
title: "cannot control in brightness in my toshipa laptop"
date: 2009-06-22
forum: Hardware
---

### Post by da7oom on 2009-06-22
hey guys

i have problem with brightness control !

FN button doesn't work in 9.04

so some of guys told me to add to panel [COLOR="DarkRed"]"brightness applet "[/COLOR]

so i did

but still nothing changed !

brightness still high .. really it's heart my eyes !

my laptop is TOSHIBA A105-S4004

thank u guys ..

---

### Post by da7oom on 2009-06-22
up

---

### Post by the jaq on 2009-06-22
Open a terminal and type

```

modprobe toshiba_acpi

```If toshiba_acpi is not installed go here: r[http://memebeam.org/toys/ToshibaAcpiDriver](http://memebeam.org/toys/ToshibaAcpiDriver)

try this

```

 cat /proc/acpi/toshiba/lcd
 
```Should report brightness setting

To change it try
```

  echo "brightness:7" > /proc/acpi/toshiba/lcd
  
```This is what the gnome applet does I think...

There is also this brightness setting, but I am not sure what it does I set mine to 100

```

   cat /proc/acpi/video/VGA/LCD/brightness

```These funny settings can be weird. I had no problem through several ubuntu versions since they included toshiba_acpi years ago, but have been having trouble since about Ibex.

---

### Post by da7oom on 2009-06-22
first of all thank u for ur replay

n second of all

i don't have toshiba_acpi

so i went to that page u give me ,, n actually i got confused 

is there another page explain it easily ?

thank u

---

### Post by da7oom on 2009-06-23
up

---

### Post by poisoneggs on 2009-07-16
bump
I have the same problem, and I'm desperate to solve it

---

### Post by niztrator on 2009-07-26
> **da7oom said:**
> first of all thank u for ur replay

n second of all

i don't have toshiba_acpi

so i went to that page u give me ,, n actually i got confused 

is there another page explain it easily ?

thank u

I'd have to agree with the fellow, the link regarding the acpi driver and having get it work or even just getting started is a bit difficult for me to understand. Perhaps it can be simplified for newbies such as myself? So first, how does one install  toshiba_acpi? 

This website is a bit hard to follow:
> **the jaq said:**
> 
If toshiba_acpi is not installed go here: r[http://memebeam.org/toys/ToshibaAcpiDriver](http://memebeam.org/toys/ToshibaAcpiDriver)


---

