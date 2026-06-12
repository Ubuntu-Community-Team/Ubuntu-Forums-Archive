---
title: "Dapper &amp; ACPI &amp; CPU Fan (never stops)"
date: 2006-06-01
forum: Hardware &amp; Laptops
---

### Post by mihai.ile on 2006-06-01
I know there are some threads about this in here but nothing to solve my problem...
I have an Acer Aspire 1694wlmi, and using daily updated dapper.
What happens is that my cpu fan almost never stops.
My cpu temperature goes from 43º until 52º on normal usage.
The fan comes up after cpu goes something like 59º or more and goes down if cpu has less than 41º
How can i make it go down before reaching 41º? something like 49º is good for me as i don't have to hear the fan all the time...

some additional info:
/proc/acpi/thermal_zone has:
thermal_zone/
thermal_zone/THRM
thermal_zone/THRM/polling_frequency
thermal_zone/THRM/cooling_mode
thermal_zone/THRM/trip_points
thermal_zone/THRM/temperature
thermal_zone/THRM/state

/proc/acpi/fan/ is empty

mihai007@acer:/proc/acpi$ cat /proc/acpi/thermal_zone/THRM/cooling_mode
<setting not supported>
cooling mode:   passive

mihai007@acer:/proc/acpi$ cat /proc/acpi/thermal_zone/THRM/polling_frequency
<polling disabled>

mihai007@acer:/proc/acpi$ cat /proc/acpi/thermal_zone/THRM/state
state:                   ok

mihai007@acer:/proc/acpi$ cat /proc/acpi/thermal_zone/THRM/trip_points
critical (S5):           93 C
passive:                 92 C: tc1=2 tc2=3 tsp=40 devices=0xdf971d40

mihai007@acer:/proc/acpi$ cat /proc/acpi/thermal_zone/THRM/temperature
temperature:             46 C


I hope someone could help me, as my laptop dryes my battery fast with the fan always on and even on acpower it makes me crazy with all this noise...
I should also say that in windows the fan is on many times but stops from time to time and when in battery mode is almost always stopped.
Any help is much appreciated...

---

### Post by torben81 on 2006-06-02
Hi, 
first of all, it might be that you can't set the temperature using acpi, because many laptop manufacturers have the BIOS control cooling. (I had to flash mine to get better values for starting/stopping the fan.) Check with your vendor's website. If acpi has control, you could try to alter the trip points as described here:
[http://acpi.sourceforge.net/documentation/thermal.html](http://acpi.sourceforge.net/documentation/thermal.html) 
However, the actions which can be defined there also depend on the settings of the manufacturer.  You can alter those as well by writing a new dsdt but this is assembly-language hacking.
greets Torben

---

### Post by mihai.ile on 2006-06-04
no luck :(
i tryed 
echo -n "110:0:90:60:0" > trip_points

have no ideea how to write and complile dsdt's :S

---

### Post by mihai.ile on 2006-06-16
still no luck, if someone can make it work please tell me what to do...

---

### Post by N6546R on 2006-06-16
[QUOTE=mihai007]still no luck, if someone can make it work please tell me what to do...[/QUOTE]

On my laptop (T42), it's the video card fan that runs continuously (ATI with the 8.25 driver), not the CPU/system fan. Might be on yous, too.

Perry

---

### Post by ozorba on 2006-06-16
The problem is with gnome-cpu-icon process. You can change the powernowd  deamon configuration. 

If you do man powernowd you will see the necessary settings. And if you use -m 2 option the fan wil stop working all the time.

Alternatively, you can install Kubuntu...

OZ

---

### Post by ozorba on 2006-06-16
Ooops!

It is not gnome-cpu-icon. It is gnome-cups-icon...

If you type top in the terminal windows you will see which process is the one that is consuming the cpu poewer.

---

### Post by rabidphage on 2006-06-18
acer 1652 Wlmi with the same annoying problem.. fan works perfectly in windows.. because of its eagerness my battery dies in 2 hrs max at idling.
totaly lost and frustrated....

---

### Post by mrmarco on 2006-06-18
Same hardware (Acer 1692), same problem here. The laptop is hot, the fan keeps running almost constantly, the cpu is on high load but there is corresponding process eating the cpu. It could be something related to interrupts, but I am not knowledgeable enough in that kind of debugging to be able to go really further. 
Is there a gentle hacker here eager to point us on a documentation on how to be able to describe the issue further ? 
(Note : I have just seen that irq0 get 200 interrupts per second ; ksysgard is able to measure it for kubuntu folks)

Note added later : when using the ati xorg driver instead of fglrx, the cpu overload desappears, but the interruptions issue stays, and perhaps makes even worse the interactivity of the system. 
Those who want to try by themselves should add the Option         "MonitorLayout" "LVDS" 
line to their xorg.conf not to face the black screen bug.

---

### Post by David Jaša on 2006-06-19
The same behaviour on Acer Aspire 1652LMi. Fan stopped only once after laptop was 10 minutes idle...

---

### Post by David Jaša on 2006-06-19
[QUOTE=N6546R]On my laptop (T42), it's the video card fan that runs continuously (ATI with the 8.25 driver), not the CPU/system fan. Might be on yous, too.

Perry[/QUOTE]


That's it, thanx a lot!

If you use fglrx, then run this command and fan will stop immediately:
```
aticonfig --set-powerstate=1
```
If you want to know, what happens, run:
```
aticonfig --lsp
```

I'm gonna to find out, how to change it automatically...

---

### Post by mihai.ile on 2006-06-20
[QUOTE=David Jaša]That's it, thanx a lot!

If you use fglrx, then run this command and fan will stop immediately:
```
aticonfig --set-powerstate=1
```
If you want to know, what happens, run:
```
aticonfig --lsp
```

I'm gonna to find out, how to change it automatically...[/QUOTE]


This is a good one ;)

---

### Post by zchshao on 2006-06-26
I got the same problem on Dell Latitude D800. It is a nVidia GeForce FX5200. So the fix for ATI will not apply to my problem. 

I didn't got this fan non-stopping problem on 5.10. It only happened after I udgrade to 6.06. I tried the ACPI-howto to set trip-point but when I read the file back, nothing gets changed. So I guess this is not supported my laptop. So any clue about this? :confused:

---

### Post by johanvandermeer on 2006-09-14
I have the same problem on my Acer 1692: 
I tried both 
#powernowd -m 2 
#aticonfig --set-powerstate=1
....but to no avail.

My fan is still hitting it off like a slavering Zebransky.

Incidentally, exactly the (fan) same problem applies when I try to install Ubuntu on a dualcore powermac G5. The fans are so loud that it sounds like the G5 is about to rocket into the air.

So now my thoughts go to either recompiling the kernel (something which i never done before), or making a dsdt (also never done before). With Ubunto 5.10 there never was a fan problem. It turned on when the CPU was busy, and it turned off when the CPU was lazy...

So what's different in 6.06 and how do I fix it?

---

