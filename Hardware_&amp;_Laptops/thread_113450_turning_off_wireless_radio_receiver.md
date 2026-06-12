---
title: "turning off wireless radio receiver"
date: 2006-01-06
forum: Hardware &amp; Laptops
---

### Post by krait on 2006-01-06
hi,

i hav a IBM R51 runnin Breezy. I am not using my wireless fr internet and wud like to know how to turn off the receiver. In windows there used to be a option after which the receiver *LED* on my laptop wud turn off. I am a newbie and wud gr8ly appreciate any help offered.

Thanks in advance.

Cheers

---

### Post by Titus A Duxass on 2006-01-06
Your wireles is probably not even running.  Most people have a problem getting wireless to damn well work in the first place.  You are the first I've seen wanting to turn it off LoL.

Are you sure it is switched on?

---

### Post by krait on 2006-01-06
yes, it is switched on even tho i aint usin it. the led's alight.

cheers

---

### Post by Titus A Duxass on 2006-01-06
Are talking about power to reciever or turning the receiver function off.

Are there two light? (power and transmit/link)

If it is the power have you tried disabling it through BIOS?

---

### Post by Lambert on 2006-01-06
The r51 looks like it comes with a wireless minipc either based on atheros or intel's 2200bg. NOt sure about atheros but if it's the 2200bg then here are some instructions.

> To disable the radio (and further reduce power consumption) when the card is not in used, issue:


```
echo 1 > /sys/bus/pci/drivers/ipw2200/*/rf_kill
```
To enable the radio, issue:


```
echo 0 > /sys/bus/pci/drivers/ipw2200/*/rf_kill
```
To make the radio off by default after boot, add 

options ipw2200 disable=1

You will probably need root privledges for above commands.

to find out what chipset it uses run this command.

```
lspci -v | grep Eth
```

---

### Post by krait on 2006-01-06
i think tht did the trick. the led is not lit after i used the disable cmd and turns on again wen i use the enable one. jus one doubt, where must i add the line to turn off radio on boot?
i wonder why there isnt a option on ubuntu network manager or somethin fr this.
well tht aside, thanks a lot.

cheers

---

### Post by auto78900 on 2008-05-01
> **Titus A Duxass said:**
> Your wireles is probably not even running.  Most people have a problem getting wireless to damn well work in the first place.  You are the first I've seen wanting to turn it off LoL.

Are you sure it is switched on?

-------------------
well buddy , if u do a google search u will find there are hundreds 
 of laptop owners with this problem.
Mine started when I was testing to see how many wireless routers were in my street.

---

