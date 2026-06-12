---
title: "ATI Graphics Fan Speed"
date: 2007-10-30
forum: Hardware &amp; Laptops
---

### Post by nightmare03 on 2007-10-30
Hey,

So recently i decided install Ubuntu 7.10, i installed the latest ATI drivers and they seemed to work without any problems but, my graphics fan speed is always at max!

Even when its just idling at the desktop the fan is at max, any ideas on how to fix this? 

Thanks for any advice!

---

### Post by nightmare03 on 2007-10-31
*bump*

---

### Post by roli100 on 2007-11-03
I have the same problem with my Radeon x800GTO. When I install graphic driers from ATI, fan speed goes to max. But this problem in on all linux systems. 

I send email to ATI support and they just replied that this is not their problem and that I shoud send email to someone.... That was about half a year ago.

---

### Post by nightmare03 on 2007-11-03
Damn thats ashame!

Thanks alot for the reply though :)

---

### Post by Somnus07 on 2007-11-06
yup same problem with me - havent come across a fix yet though sorry :(

---

### Post by nightmare03 on 2007-11-06
Hopefully we get a fix soon, or some sort of idea of why its doing it!

:-k

---

### Post by cow_racer on 2007-11-06
> **nightmare03 said:**
> Hey,

So recently i decided install Ubuntu 7.10, i installed the latest ATI drivers and they seemed to work without any problems but, my graphics fan speed is always at max!

Even when its just idling at the desktop the fan is at max, any ideas on how to fix this? 

Thanks for any advice!

Taken from aticonfig man page:

POWERplay Options:
  Following options will not change the config file. 
  These options will be effective immediately. Other options on 
  the same command line will be ignored.
  --lsp, --list-powerstates
        Print information about power states and exit.
  --set-powerstate=NUMBER
        Set a power state listed by --list-powerstates.

I actually have not tried, but I would think by setting to a loser powerstate would reduce the power consumption and heat which means no fan is turned on.

---

### Post by techboy31 on 2007-11-18
Hi there,

I'm running 7.10 with an ATI X800 and i have exactly the same issue, the graphics card fan is full blast all the time.

Did anyone find a fix for this?

---

### Post by nightmare03 on 2007-11-20
Please, someone make a fix :)

I REALLY wanna start using ubuntu again but this bug is stopping me :(

---

### Post by techboy31 on 2007-12-08
I managed to fix this.....

By putting my spare Nvidia 6800gt in my ubuntu box and hey presto it works perfect!

So it must be the ATI driver that sucks tbh

---

### Post by L0cky on 2008-01-13
I'm having the same problem.

You can view the available powerstates with:> aticonfig --list-powerstates
And then set a lower power state with > aticonfig --set-powerstate=x
Where x corresponds to the desired powerstate.  This might help some poeple.

However, when I list powerstates, there is only 1 (overdrive, default state).  There must be something better, as this hot noisy card is a dealbreaker for me.

---

### Post by Genome82 on 2008-02-02
So, there is basically no solution to this? I've finally gotten everything to work just the way I want it, but the fan is driving me nuts. But since I dualboot on this PC for gaming in Windows, I really don't want to slide in my passive 7600GS instead of my X1950Pro. :(

I can't do anything with powerstates either, it seems.

---

### Post by nikio on 2008-06-18
This may be a "work around" if you have a dual boot:
I have an ATI radeon X1550, with no dedicated drivers for linux.
I've installed Ubuntu to recover data from my dead Windows partition (now they're both working) where the fan speed was (quite) well handled...
the only way I found to speed down the fan was to 
first boot Windows (and the fan becomes silent enough)
reboot the system with ubuntu (without switching off th PC)
at this point the unhandled speed remains the same that was set in Windows

I can imagine the horrified reaction of many linux users... still maybe someone may find this "thing" useful!

---

