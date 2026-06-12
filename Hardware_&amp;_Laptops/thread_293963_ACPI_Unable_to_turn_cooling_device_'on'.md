---
title: "ACPI: Unable to turn cooling device 'on'"
date: 2006-11-05
forum: Hardware &amp; Laptops
---

### Post by renjoy on 2006-11-05
I am getting the message :
ACPI: Unable to turn cooling device [c15ebdec] 'on'

Its printing frequently on my system if I check dmesg.
I was wondering how I can fix this.

This has something to do with the kernel, since I am dual booting Ubuntu and Fc6, and I found that I am getting this on both the OS.

If I turn off ACPI, of course, it stops.
I hope this makes sense. 
I am not able to figure out what is failing here.
I am attaching my DMESG info. I am having an AMD Athlon system, with Nvidia Geforce MX 4000. I have installed the beta driver for nvidia, but this is happening even if I do a fresh installation with just vega driver.

---

### Post by ArtechnikA on 2006-11-17
Just a bit of a bump for you, since I'm getting (approximately) this message too.  (The specific hardware address is different.)
It's getting logged to all 3 of syslog, messages, and kernlog - every 5 seconds.

I've opened the box and verified that all the fans are spinning and the BIOS tells me the CPU temp is in its happy range so I'm not panicked other than I don't like the performance hit of 3 files getting filled with superfluous stuff...

(6.10)

---

### Post by Papou on 2006-11-19
Same issue with AMD Athlon XP in HP pavilion ( tower, not labtop ), after upgrade dapper to edgy.

dmesg : 
[17179575.104000] ACPI: Fan [FAN] (on)
[17179575.112000] ACPI: Unable to turn cooling device [dffdfdec] 'on'
[17179575.112000] ACPI: Thermal Zone [THRM] (43 C)

And then ACPI: Unable to turn cooling device [dffdfdec] 'on' is added every 6 sec in the log files .... boring !

Seems that ACPI got wrong information from the hardware/sensors because fan are spinning normally and CPU isn't overheating ( checked by the BIOS ).

if y stop ACPI using sudo /etc/init.d/acpid stop , the message still appears every 6 sec...

---

### Post by bobosity on 2006-11-28
I just noticed this too. My computer isn't overheating and I can hear the fan running.

I want the message to go away. Does anyone know where it's coming from?

---

### Post by noland on 2008-04-25
well it does the same to me, i actually had a fatal crash although fan is running and temperature is fine... actually the computer was running really hot when i first installed gutsy, but i installed the application  gkrellm and that seems to keep the temperature low enough (usually 45 degrees celcius)...and i am now using all new 8.04LTS... laptop is a toshiba satellite A100

---

### Post by DragonHawk on 2008-04-28
This appears to be an issue with certain hardware.  Details are unclear.

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/63550](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/63550)

If you prefer, rather than disabling ACPI completely, you can blacklist the "thermal" and/or "fan" kernel modules .  That will prevent the kernel from trying to control the fan.  To do so, edit the file "/etc/modprobe.d/blacklist" (using sudo), and add a line "blacklist thermal" or "blacklist fan", as appropriate.

Note that if your system actually *needs* the kernel to be able to control the fan (to prevent system overheat), blacklisting the modules may cause system instability or hardware damage.  In my case, the fans were working, despite the log messages saying the kernel could not turn them on.

---

