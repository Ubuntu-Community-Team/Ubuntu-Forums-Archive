---
title: "Monitoring fan speed on a NUC"
date: 2017-07-02
forum: Hardware
---

### Post by CatKiller on 2017-07-02
I've got a NUC, the NUC7i5BNK, in my living room, tucked behind the TV. It has no keyboard or mouse attached.

Sometimes the fans don't spin up for some reason, which is annoying because then the NUC overheats and shuts down.

I could OCD keep checking to see if I can hear the fans, but that's annoying because there's a NAS, a PS3 and a Sky box in the same part of the room, so I'd have to get really close to be sure that it was the right fan that I was hearing. And it's tucked behind the TV, so not really super accessible. I could plug in a keyboard and change the BIOS settings so that I could definitely hear the fan from across the room, but that would be annoying because I'd be able to hear the fan from across the room. I could disassemble the thing to see if there's something rubbing against the fan that stops it spinning up, but it's fiddly as anything in there and the unit is tucked behind the TV, so I'd rather not disturb it.

What would be significantly nicer would be if I could SSH into the NUC, run sensors, and see that the fans are spinning quietly. Perhaps even give them a nudge with fancontrol if they haven't started up.

I've done it before with my desktop: my Conky shows my fan speeds and temps, and fancontrol follows the settings that I've given it to keep my computer mostly silent and running cool. I even had to sort out my own w83627ehf module back when I was setting it up since support from that hadn't made it into the release yet. I know roughly what I'm doing, basically.

According to Intel, > 
1.12.1 Hardware Monitoring 

The hardware monitoring and fan control subsystem is based on a[FONT=sans-serif]n ITE Tech. IT8987E[/FONT][FONT=sans-serif]-VG [/FONT][FONT=sans-serif]embedded controller[/FONT][FONT=sans-serif], which supports the following:
[/FONT][FONT=sans-serif]Processor and system ambient temperature monitoring[/FONT]
[FONT=sans-serif]Chassis fan speed monitoring 
[/FONT][FONT=sans-serif]Voltage [/FONT][FONT=sans-serif]monitoring of [/FONT][FONT=sans-serif]CPU IO Vcc ([/FONT][FONT=sans-serif]+Vccio)[/FONT][FONT=sans-serif], Memory Vcc (V_SM), [/FONT][FONT=sans-serif]CPU IN Vcc ([/FONT][FONT=sans-serif]+Vccp[/FONT][FONT=sans-serif]) [/FONT][FONT=sans-serif][/FONT]
[FONT=sans-serif]SMBus interface[/FONT]

[FONT=sans-serif]1.12.2 [/FONT][FONT=sans-serif]Fan [/FONT][FONT=sans-serif]Monitoring
[/FONT]
[FONT=sans-serif]Fan monitoring can be implemented using third[/FONT][FONT=sans-serif]-party software.  [/FONT][FONT=sans-serif]
[/FONT]which isn't super helpful.

coretemp gives temperatures, which is fine, but it's the fan that I'm interested in. The [FONT=sans-serif]IT8987E[/FONT][FONT=sans-serif]-VG is discovered by sensors-detect as ```
Trying family `National Semiconductor/ITE'...               Yes
Found unknown chip with ID 0x8987
```[/FONT]

Similar chips are handled by the it87 kernel module, which seems to be blacklisted and seems to be tied into something called a watchdog daemon. That's where I get hazy.

So, given that the NUC line has been out for a few years now, and I suspect that the non-Intel chips for the newer models are probably broadly similar to the non-Intel chips in the older models;

Am I on the right track trying to look at it87?
Is it87 likely to have support, or get support, for this chip?
Is setting up watchdog a necessary step to getting monitoring and control of the fan speed through this chip?
Has anyone successfully managed to monitor the fan speed of their NUC previously?

Thank you for making it to the end of this post.

---

### Post by gsahli on 2017-07-03
Have you reviewed this?
[https://help.ubuntu.com/community/SensorInstallHowto](https://help.ubuntu.com/community/SensorInstallHowto)

---

### Post by CatKiller on 2017-07-03
> **gsahli said:**
> Have you reviewed this?
[https://help.ubuntu.com/community/SensorInstallHowto](https://help.ubuntu.com/community/SensorInstallHowto)

Yes.

---

### Post by CatKiller on 2017-07-03
Apparently it can't be done.

[https://github.com/groeck/it87/issues/30](https://github.com/groeck/it87/issues/30)

---

