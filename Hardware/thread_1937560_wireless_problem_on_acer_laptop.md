---
title: "wireless problem on acer laptop"
date: 2012-03-08
forum: Hardware
---

### Post by ajaykumar.b on 2012-03-08
HI

I have acer core i3 laptop.I am running kubuntu 11.10 on it .I connect to internet through router.It was working fine .But suddenly dont know wat happened the wifi LED doesnt glow.
I am using windows on the same machine .It is working fine in windows.
I tried to find the solution .I couldnt 
when I checked sudo lshw , it is showing that the drivers are installed.
the result of rfkill list shows something like this

acer wireless:wirelesslan 
soft blocked:yes
hard blocked:no

phy0 wireless:wireless 
soft blocked :no
hard blocked :yes

I guess wireless is switched off.Can anyone help me how to switch it on .
if you need any info please post .

Thanks in advance

Ajay

---

### Post by cespinal on 2012-03-08
Please try to browse and use the connection. 

There is known bug that is causing the LED to switch off, although wireless keeps working properly.

---

### Post by TBABill on 2012-03-08
In case you need to remove the soft block, ```
sudo rfkill unblock all
```

---

### Post by ajaykumar.b on 2012-03-09
no luck :(

I tried the above ,still not working .

---

### Post by ts3 on 2012-03-09
> **ajaykumar.b said:**
> no luck :(

I tried the above ,still not working .

Is there a hardware switch, a button, for the wireless (I think it's F12 on my laptop)? Try to toggle it and run "sudo rfkill unblock all" for each position.  I am not sure whether this is a good explanation, sorry.  What I mean is run "sudo rfkill unblock all" then if "rfkill list all" still shows a hardware block press the switch and run "sudo rfkill unblock all" again.  Works on my laptop when the hardware switch freezes so it might help.

---

