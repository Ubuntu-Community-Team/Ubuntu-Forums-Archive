---
title: "Sending alerts when power supply unplugged from laptop"
date: 2011-07-24
forum: Hardware
---

### Post by CTPAYC on 2011-07-24
Hello,

a situation that is I have an IBM ThinkPad laptop at my coffee shop, and lately having some power outages that can result in losing frozen products.

How can I set up Ubuntu to send me an email when it has its power supply unplugged?

Thank you.

---

### Post by SteveDee on 2011-07-25
> **CTPAYC said:**
> ...How can I set up Ubuntu to send me an email when it has its power supply unplugged?


This is an interesting question.

Exploring /proc/acpi on my laptop, I see a text file /proc/acpi/battery/BAT0/state
which looks like this when running on mains power:-

```

present:                 yes
capacity state:          ok
charging state:          charging
present rate:            unknown
remaining capacity:      19660 mWh
present voltage:         11381 mV

```
...and like this when running on battery power:-
```

present:                 yes
capacity state:          ok
charging state:          discharging
present rate:            19088 mW
remaining capacity:      19840 mWh
present voltage:         12043 mV

```


Sending email via the command line could be achieved with something like this:-
```

mail -s “Power has failed” ctpayc@coffee-shop.com

```

So you could check battery state in a script or program, and if it was "charging" but is now "discharging" the program could send you an email.

This question may attract more interest in the Programming forum, unless you are looking for an existing application that can do this for you.

---

