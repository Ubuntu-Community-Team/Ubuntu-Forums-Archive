---
title: "Hangs at shutdown, Ubuntu 11.10 64 bits"
date: 2012-03-01
forum: Hardware
---

### Post by CardexDave on 2012-03-01
Hello!

I have a problem with my Asus U36SG, the system won't shutdown nor reboot. It is not properly a clean install but it is a recent install, not even a week old.
I removed 'splash' from the grub command line to be able to see more things at shutdown, and the system actually seem to shutdown correctly, but the device itself does not power off.
The system says things like "Terminating all processes" and so on, which appears to work smoothly, as there always is [OK] at the right of the screen, then it displays "Will now halt", and then it displays "[xxx] Power down" with xxx being some time in seconds, the same pattern as when booting I can see "[aaa] Loading some driver" etc..
Then I can hear the fans and drive stop, but the screen does not go blank, and the power led still lights. 
The Alt+SysRq+REISUO does nothing. One time I got the system hanging at "Will now halt" instead of "[xxx] Power down", then I tried REISUO and all the commands worked except for the O one, which resulted in the same state as before, it did not power off the system, only the fans and drive stopped, with the screen and led still going on...

I already tried acpi=force, acpi=off, acpi_osi=Linux...
I already blacklisted the rt2800pci driver some people says they have shutdown problem related to it...
I already tried killing network manager before shutdown, I already removed modemmanager, as I saw people were also having problem with it...

I'm out of clue and desperate, can someone please help me?

Thanks in advance,

David

PS: English is not my native language, I apologize for the potential errors I made...

---

### Post by CardexDave on 2012-03-01
Strangely, reboot and hibernate works flawlessly, only pure shutdown fails to actually power off the computer...

---

### Post by CardexDave on 2012-03-03
Up please!

---

### Post by siepo on 2012-03-04
shutdown -h now

used to work for me, but after a processor upgrade even that command failed to shut down the computer.

As long as local file systems have been unmounted, it should be safe to just flip the power switch.

Anyhow, that is what I have been doing without apparent ill effects.

---

### Post by CardexDave on 2012-03-04
Thanks for your answer!

Unfortunately, this command gave the same result as usual... ;-)
I know I could always power off my computer using the power button as long as the drives are unmounted, but it's definitely not a very elegant way of shutting down one's computer, I'd rather fix it to work in the normal way...
The thing I am wondering is how can it power off when asking to hibernate and not when asking for a normal shutdown?

---

### Post by CardexDave on 2012-03-08
Up please... ;-)

---

### Post by CardexDave on 2012-03-16
Nobody has any idea?

---

### Post by saltydog on 2012-03-21
I have the same issue.
My system reaches "System Halted", but the power is not switched off.

I have tried all acpi combinations in grub, with no success.

---

### Post by CardexDave on 2012-03-21
Did you experience the same issue with earlier versions of Ubuntu on the same machine?
My installation is a new os on a new computer so I can't tell if the hardware is not perfectly supported in general or if it's a regression of newer version of ubuntu...

---

### Post by saltydog on 2012-03-22
No, my machine has always performed great with Ubuntu. This issue is present since no more than a couple of months.

---

### Post by jchaffeejr on 2012-03-26
I have Ubuntu 11.10 32 bits but my machine started doing the same after I installed the Catalyst video drivers and got my dual screens to work properly. 

I found in the Dash home more apps area two buttons, one for shutdown and one for restart. These buttons work properly and the system shuts down or restarts when I use them. The shutdown item in the menu in the upper right corner does not work. The system hangs at the Ubuntu screen with the five buttons. You can also set the computer turn on button to shut down when you press it. This is the button you use to turn on the computer.

I hope this is helpful!!

---

### Post by CardexDave on 2012-04-10
Hi guys, I found the cause of my problem!
It was a script I used for power saving.
I actually have two devices I CANNOT set to power save otherwise my computer won't shutdown.

The script used to echo "auto" to all the devices, I had to try every of them to find the ones which I couldn't let it set to auto.
Here are they:
```
/sys/bus/pci/devices/0000:00:1a.0/power/control
/sys/bus/pci/devices/0000:00:1d.0/power/control
```

I have a ASUS U36SG, and I used a script that did this:
```
for foo in /sys/bus/pci/devices/*/power/control;
do echo on > $foo;
done
```
If you encounter the same problem, manually write each echo to the devices and try powering the computer off, allowing you to find the ones that cause problems.

According to powertop the two devices causing troubles on the U36SG are Runtime PM for PCI Device Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 and 2.
Does anyone know what they actually are and why do they prevent my computer to shutdown if I set them to powersave?

---

