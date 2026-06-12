---
title: "CPU fan running at max speed"
date: 2016-03-28
forum: Hardware
---

### Post by gen4 on 2016-03-28
Hey, guys, I have  a problem - CPU fan is running max speed all the time(which it shouldn't..), and, accordingly, after a few hours, it really starts making a lot of noise. I've browsed enough internet to find its a common problem enough, yet so far I've found no valid answers to my case. Consider the following scenario: 

Running sensors-detect i get written to /etc/modules: w83627hf, but continuing with pwmnonfig I get -  found the following devices: hwmon0/device is w83697hf, and no fans(ok, I only have 1) have speed changes detected. Pwmconfig only generates config file with empty values.. Sensors just return a pile of parameters empty values and fancontrol doesnt even have its config file. Previously, when the same machine was running win, I had no such problems, and the cpu's workload now shouldnt be a problem. 

System specs: 
[COLOR=#393939][FONT=arial]os: Ubuntu Linux 14.04.4[/FONT][/COLOR] (no GUI)
[COLOR=#393939][FONT=arial]kernel:Linux 4.2.0-34-generic on x86_64 [/FONT][/COLOR]
[COLOR=#393939][FONT=arial]cpu:Intel(R) Celeron(R) CPU 2.53GHz, 1 cores
motherboard: asrock 775vm800

[/FONT][/COLOR]Ps: I do apologize if this turns out to be a trivial question that -has- already been answered billion times. But after 3 months of searching and failing and not having enough linux knowledge(all the home services are running perfectly, for unknown reasons..) I'm growing desperate.. ](*,)

---

### Post by Yellow Pasque on 2016-03-29
Looking through the manual ( [http://download.asrock.com/manual/775VM800.pdf](http://download.asrock.com/manual/775VM800.pdf) ), I don't see an option to disable BIOS fan control so that you can manually control the fan with a utility like pwmconfig or Speedfan in Windows.

I have two suggestions. First, since fan control works with Windows, I would try booting with 'acpi_osi=Windows' or 'acpi_osi=Linux'
[http://askubuntu.com/questions/28848/what-does-the-kernel-boot-parameter-set-acpi-osi-linux-do](http://askubuntu.com/questions/28848/what-does-the-kernel-boot-parameter-set-acpi-osi-linux-do)

Second, you could try plugging the fan into the chassis fan header and hoping it supports PWM control. Given the age and chipset this mobo uses, my money would be on the chassis fan header not supporting PWM because the mobo manufcaturer didn't want to spend the extra $.50 to wire it in.

---

