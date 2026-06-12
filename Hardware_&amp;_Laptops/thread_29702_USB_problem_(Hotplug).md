---
title: "USB problem (Hotplug?)"
date: 2005-04-25
forum: Hardware &amp; Laptops
---

### Post by rlcoach on 2005-04-25
I am hoping some kind soul can help me fix my problem with installing and configuring Ubuntu. I am doing my best to switch from Windows XP after all the positive things I have heard about Linux however I am having massive teething issues that I cannot fix (tried all weekend) and if I cannot get past them it will mean I will have to return to Microsoft &#9785;

I have installed Ubuntu on my PC but am having major problems getting my USB devices to work. First of all I couldn’t install at all when I had my USB keyboard and mouse plugged in. I tried swapping their ps/2 equivalents and then the install went smoothly. However…………then when I plugged any usb devices in nothing would work. I tried changing from ACPI to ACM but this made no difference. Curiously though if I restart hotplug (sudo /etc/init.d/hotplug restart) once booted everything kicks into life and my usb devices are detected and work fine. Sadly this is not a long term solution as I cannot boot with my usb keyboard/mouse plugged in.

One more clue is that when hotplug starts in boot up it pauses for quite a long time.

Here are my system specs.

Medion Athlon XP 3200+ with 512mb RAM
nVidia GeForce FX5200
Pioneer DVD RW DVR-106D
Sony DVD Rom DDU1612
Seagate Barracuda ST3160021A (Ultra ATA/100)
Medion TV Tuner
Microsoft USB Digital Media Pro Keyboard
Logitech Wireless MX Laser mouse
Creatix Modem
Nevo F-419 19" TFT Monitor
Via Rhine II Fast Ethernet
Internal card reader

Any help would be greatly appreciated, I have run out of ideas.

Andrew

p.s. And my sound doesn’t work either, but I figured that could wait until I fix the usb problem (if I can)

---

### Post by hobnob on 2005-04-25
Hi!

Can you post the output of 'dmesg' and 'lsusb' so we could have a bit more info to work with. Also perhaps if you can paste the logs after unplugging and plugging in the mouse/keyboard to see if there's any life.

---

### Post by rlcoach on 2005-04-25
[QUOTE=hobnob]Hi!

Can you post the output of 'dmesg' and 'lsusb' so we could have a bit more info to work with. Also perhaps if you can paste the logs after unplugging and plugging in the mouse/keyboard to see if there's any life.[/QUOTE]

At what stage do you want to to get the output, at the moment I am booting with ps/2 keyboard and mouse, then restarting hotplug and then plugging in my usb keyboard and mouse (which then both work fine).

---

### Post by hobnob on 2005-04-25
Let's start with 

a) As you are now, all functioning properly
b) Booting with PS/2, then plugging in USB mouse/keyboard (but not restarting hotplug - I appreciate it is tricky typing the commands when your keyboard isn't working, but you could try putting them in a shell script with "sleep 10" at the beginning).

Maybe I missed it above, but where does the boot actually fail when you have USB k/m connected? Is it during a particular service startup? You mentioned hotplug takes a while, but only when PS/2 is connect.

---

### Post by rlcoach on 2005-04-26
Hooray it is fixed.

I flashed my bios and suddenly all the USB problems have disapeared.

---

