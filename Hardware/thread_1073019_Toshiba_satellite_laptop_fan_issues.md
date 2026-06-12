---
title: "Toshiba satellite laptop fan issues"
date: 2009-02-17
forum: Hardware
---

### Post by harman0 on 2009-02-17
I have a Toshiba Satellite A305-S6872 Linux 2.6.28.4 running the newest Ubuntu. 
The fan seems to kick on at high once it hits a certain temperature and not go down no matter what I do, aside from hibernating the system or rebooting. I cannot get thermal readouts.I do not know how the fan may be kicking on without showing me what temp and everything it's at unless it's being operated by the BIOS. the BIOS seems to be the insydeH2O BIOS. 

I seem to have had issues from day one with the fan on this laptop, unfortunately I think it's too late for an exchange.

Please let me know if you have a related issue or advice

---

### Post by jerrynewt on 2009-02-19
Try "acpi -t" in terminal (without the quotes) for temp readout.

---

### Post by harman0 on 2009-02-19
```
acpi -t
     Battery 0: Full, 100%
     Thermal 0: ok, 0.0 degrees C
```

I think the issue may actually be that acpi is looking at the wrong temp readout.. because sensors returns this: 
```
sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +0.0°C  (crit = +92.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +51.0°C  (high = +85.0°C, crit = +85.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +55.0°C  (high = +85.0°C, crit = +85.0°C)
```

The latter two of which appear to be correct temperatures.. I don't know what the deal is with that acpitz-virtual-0

---

### Post by mnd on 2009-02-20
Try this [**link**.]("http://ubuntuforums.org/showthread.php?t=1042500&highlight=toshiba+fan") I had the same problem and setting the acpi_osi="Linux" boot option worked for me.

---

### Post by amkr on 2009-02-20
Hey dude, I just put a Ubuntu 7.10 on my Toshiba L300, and now I dont how to get the Fn buttons working. Help please!

---

### Post by harman0 on 2009-02-26
Mnd: Your fix did not seem to work for me, however, I have sort of noted that the fan *seems* to switch on at 69C or 70C? (which is absurdly hot and I don't see how I could ever get that hot doing what I was doing at the time.. using abiword..). This is all well, I don't want my laptop to melt, but the fan does not turn off after it has turned on.. I'm thinking I may be able to edit some trip points somewhere? These messages may help a bit.. from /proc/acpi/thermal_zone/THRM:

```
harman@:/proc/acpi/thermal_zone/THRM$ ls
cooling_mode  polling_frequency  state  temperature  trip_points
harman@:/proc/acpi/thermal_zone/THRM$ cat trip_points 
critical (S5):           92 C
passive:                 106 C: tc1=2 tc2=5 tsp=300 devices=CPU0 CPU1 
active[0]:               70 C: devices= FAN 
harman@:/proc/acpi/thermal_zone/THRM$ cat cooling_mode 
0 - Active; 1 - Passive
harman@:/proc/acpi/thermal_zone/THRM$ cat polling_frequency 
polling frequency:       2 seconds
harman@:/proc/acpi/thermal_zone/THRM$ cat state 
state:                   ok
harman@:/proc/acpi/thermal_zone/THRM$ cat temperature 
temperature:             0 C

```
Thanks a lot for the help so far =)

---

### Post by amitbk on 2009-03-10
Hi,
I use a Toshiba Satellite A305-S6898, and share your problem.
I get a similar output from `acpi -t` and from `sensors`.

I posted on two similar threads:
[http://ubuntuforums.org/showthread.php?t=1047640]("http://ubuntuforums.org/showthread.php?t=1047640")
[http://ubuntuforums.org/showthread.php?t=1042500]("http://ubuntuforums.org/showthread.php?t=1042500")

Did you find a solution to this problem?
Is there a bug open for this issue?

Thanks :)

---

### Post by harman0 on 2009-03-10
Hi. Well all I have found really is *most* of the time the fan will work correctly when I boot from cold. When I hibernate, which I had been doing for awhile, the fan does not come on when you unhibernate and never does come on until I get to 79C, and at that point it stays on and cannot be turned off.
When I boot up, the fan will usually turn on at the lowest setting and keep it under 52C, if it goes about 52C it will go on at a medium speed, and it will turn off if it cools down again.
I had been using hibernate all of the time, and never really noticed whether I had changed something that caused it to start working from a cold boot or not, but I'm not sure I changed anything, I just was experimenting with hibernate trying to get it to work correctly all of the time (which I eventually did, aside from the fan issue, which I haven't yet bothered with) so I never noticed the fan working correctly...
It may have started working from the solution posted by others with the acpi_osi="Linux" : [http://ubuntuforums.org/showpost.php?p=6843011&postcount=17]("http://ubuntuforums.org/showpost.php?p=6843011&postcount=17")
Right now, frankly, I've not bothered to figure out how to fix this problem with hibernate and the fan. Let me know if you figure anything out.
Also, no I have not opened a bug because, as you can see, and from reading around, it doesn't seem we know exactly what is causing this issue.. Honestly it seems to me that the newer toshiba satellites just do not yet have full driver support in the linux kernel.

---

### Post by amitbk on 2009-03-22
Just to understand your situation, harman0, do you currently have the 
```
acpi_osi="Linux"
``` line added to you kernel params?

Also, when you run "sensors" do you get the same output as I get?

```
$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +0.0°C  (crit = +92.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +42.0°C  (high = +85.0°C, crit = +85.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +45.0°C  (high = +85.0°C, crit = +85.0°C)
```

Another final question, did you figure out what is the meaning of the 'acpitz-virtual-0' adapter? If it is the CPU heat then how come it isn't some kind of calculation over the Core # temperatures?

---

### Post by harman0 on 2009-03-23
Yes I have acpi_osi="Linux" in my kernel params.

and yes, I get the exact same sensors output.

As for the acpitz-virtual-0 I have no idea.. I remember googling it a bit and found nothing in particular.
I'm going to try to figure out the difference between modules loaded at boot and modules loaded after unhibernating.. see if I can find anything.

---

### Post by amitbk on 2009-03-24
I get this "sensors" output without adding acpi_osi="Linux" to my kernel params, so I guess it has no effect on your system too.

Why should there be a difference between the loaded modules after boot and after returning from "hibernate"?

---

### Post by harman0 on 2009-03-24
Yeah, probably not.. because this only happens to me after having hibernated, and I'd guess it'd be some sort of module

---

### Post by raztus on 2009-04-09
I have this same model (A305-S6872) and fussed with this issue for about a month.  Eventually, I gave up because it was consuming too much time, and I moved grudgingly back to Windows.  The most helpful information I found on this issue was found here: [http://memebeam.org/toys/ToshibaAcpiDriver]("http://memebeam.org/toys/ToshibaAcpiDriver")

I actually contacted both Toshiba and InsydeH2O (the maker of my bios), and both responded simply that Linux is not supported.  From the link listed above:

[INDENT]This driver does not work on all Toshiba laptops, particularly those models which seem to have a BIOS or other firmware which was not developed by Toshiba itself. New reverse engineering work will have to be done on these machines, or Toshiba will have to disclose the necessary details. (For support of machines with Phoenx BIOS, try the [Omnibook driver].) The error you will see in this case is:[/INDENT]

[INDENT][INDENT]    $ modprobe toshiba_acpi
    FATAL: Error inserting toshiba_acpi
    (.../kernel/drivers/acpi/toshiba_acpi.ko): No such device[/INDENT][/INDENT]

This is the exact error I was getting when trying to install the Toshiba driver found on the page above.  Hopefully someday I can return to the world of Ubuntu.

---

