---
title: "Wake up with keyboard from hibernation mode"
date: 2013-01-08
forum: Hardware
---

### Post by mabox on 2013-01-08
Hello,
I would like to turn on my computer from the hipernation mode using the keyboard. In Windows that is on the same computer installed, it works simply press any key and the computer will boot. On my Ubuntu   the keyboard then only wild starts to flicker, but the computer will not boot. I am using a logitech G15 keyboard.
Have anyone an idea?

Greetings
mabox

---

### Post by tgalati4 on 2013-01-08
Perhaps there is a BIOS setting either "Legacy USB Devices" or "Allow USB to Wake"?

---

### Post by mabox on 2013-01-09
But with Windows on the same machine it is working.
Therefore i think the BIOS settings should be correct

---

### Post by tgalati4 on 2013-01-09
Did you check the BIOS settings?  Linux interacts with the hardware in a very different fashion than Windows.

---

### Post by mabox on 2013-01-09
Now I did check the BIOS settings. There is a setting "Legacy USB Device" activated. 
Otherwise I can not find any settings for "wake up" and "USB".....

Any other idea?

---

### Post by tgalati4 on 2013-01-09
What is the model of the computer?  Does suspend-to-RAM work?  In otherwords, can you put the machine to sleep (but not hiberation--that writes to disk) and then wake it by hitting the power-on button?

Open a terminal and install acpitool:

```
sudo apt-get install acpitool
acpitool -e
```

Post the output of that into this thread.

---

### Post by mabox on 2013-01-09
Hi,
here is the output:
```
acpitool -e
  Kernel version : 3.5.0-21-generi   -    ACPI version : 20120320
  -----------------------------------------------------------
  Battery status : <not available>

  AC adapter     : <info not available or off-line> 
  Fan            : <not available>

  CPU type               : Intel(R) Core(TM) i7 CPU         920  @ 2.67GHz 
  Min/Max frequency      : 1600/2668 MHz
  Current frequency      : 2668 MHz
  Frequency governor     : performance 
  Freq. scaling driver   : acpi-cpufreq 
  Cache size             : 2668.000 KB
  Bogomips               : 5345.77 
  Bogomips               : 5345.77 
  Bogomips               : 5345.77 
  Bogomips               : 5345.77 
  Bogomips               : 5345.77 
  Bogomips               : 5345.77 
  Bogomips               : 5345.77 
  Bogomips               : 5345.77 
  Function Show_CPU_Info : could not read directory /proc/acpi/processor/
  Make sure your kernel has ACPI processor support enabled.

  Thermal info   : <not available>

   Device	S-state	  Status   Sysfs node
  ---------------------------------------
  1. NPE2	  S4	*disabled  
  2. NPE4	  S4	*disabled  
  3. NPE5	  S4	*disabled  
  4. NPE6	  S4	*disabled  
  5. NPE8	  S4	*disabled  
  6. NPE9	  S4	*disabled  
  7. NPEA	  S4	*disabled  
  8. P0P1	  S4	*disabled  pci:0000:00:1e.0
  9. USB0	  S4	*enabled   pci:0000:00:1d.0
  10. USB1	  S4	*enabled   pci:0000:00:1d.1
  11. USB2	  S4	*enabled   pci:0000:00:1d.2
  12. USB5	  S4	*disabled  
  13. EUSB	  S4	*enabled   pci:0000:00:1d.7
  14. USB3	  S4	*enabled   pci:0000:00:1a.0
  15. USB4	  S4	*enabled   pci:0000:00:1a.1
  16. USB6	  S4	*enabled   pci:0000:00:1a.2
  17. USBE	  S4	*enabled   pci:0000:00:1a.7
  18. P0P4	  S4	*disabled  pci:0000:00:1c.0
  19. P0P5	  S4	*disabled  
  20. P0P6	  S4	*disabled  pci:0000:00:1c.2
  21. P0P7	  S4	*disabled  
  22. P0P8	  S4	*disabled  
  23. P0P9	  S4	*disabled  pci:0000:00:1c.5
  24. NPE1	  S4	*disabled  pci:0000:00:01.0
  25. NPE3	  S4	*disabled  pci:0000:00:03.0
  26. NPE7	  S4	*disabled  pci:0000:00:07.0
  27. GBE	  S4	*disabled  

```

Suspend and hibernation works, e.g. with the terminal:
```
sudo pm-suspend
```
or
```
sudo pm-hibernate
```

With both it is possible to wake up the machine over the power-on button.

---

### Post by tgalati4 on 2013-01-09
USB5 is disabled, which means it loses power when your computer goes to sleep.  Is it possible that your keyboard is connected to USB5?

acpitool -w

man acpitool

enable USB5 using acpitool and see if keyboard will wake the computer.

sudo acpitool -w 5 (or use whatever number shows up as USB5 when running with -w switch.)

Then verify with:

acpitool -w

---

### Post by mabox on 2013-01-10
Hi,
I try to change the status from USB5, but it doesn't work.

```
sudo su -
acpitool -W 12
```

Result:
```
acpitool -W 12
  Changed status for wakeup device #12 (USB5)
```

```
acpitool -w
   Device	S-state	  Status   Sysfs node
  ---------------------------------------
  1. NPE2	  S4	*disabled  
  2. NPE4	  S4	*disabled  
  3. NPE5	  S4	*disabled  
  4. NPE6	  S4	*disabled  
  5. NPE8	  S4	*disabled  
  6. NPE9	  S4	*disabled  
  7. NPEA	  S4	*disabled  
  8. P0P1	  S4	*disabled  pci:0000:00:1e.0
  9. USB0	  S4	*enabled   pci:0000:00:1d.0
  10. USB1	  S4	*enabled   pci:0000:00:1d.1
  11. USB2	  S4	*enabled   pci:0000:00:1d.2
  12. USB5	  S4	*disabled  
  13. EUSB	  S4	*enabled   pci:0000:00:1d.7
  14. USB3	  S4	*enabled   pci:0000:00:1a.0
  15. USB4	  S4	*enabled   pci:0000:00:1a.1
  16. USB6	  S4	*enabled   pci:0000:00:1a.2
  17. USBE	  S4	*enabled   pci:0000:00:1a.7
  18. P0P4	  S4	*disabled  pci:0000:00:1c.0
  19. P0P5	  S4	*disabled  
  20. P0P6	  S4	*disabled  pci:0000:00:1c.2
  21. P0P7	  S4	*disabled  
  22. P0P8	  S4	*disabled  
  23. P0P9	  S4	*disabled  pci:0000:00:1c.5
  24. NPE1	  S4	*disabled  pci:0000:00:01.0
  25. NPE3	  S4	*disabled  pci:0000:00:03.0
  26. NPE7	  S4	*disabled  pci:0000:00:07.0
  27. GBE	  S4	*disabled  

```

:cry:

No changes in the status.

---

### Post by tgalati4 on 2013-01-10
I noticed that USB5 is still off.  So perhaps it is a special USB connection or it is under control of BIOS.  Does your keyboard have a sleep button (half-moon symbol).  If so, will it wake the machine if you press it?  If that works then you can remap the sleep key to any key that you want.  On one machine with a keyboard that did not have a sleep key, I remapped it to the "p" key.  So to wake the machine, I would hit "p" and it would wake up.

As a work-around, use the power button.

Send an email to the manufacturer of the computer detailing your problem.

---

### Post by mabox on 2013-01-11
No there is not a sleep button on the keyboard :(
I will use the work-around with the power button.

Thank you very much for your help. Have a good weekend.

mabox

---

### Post by mabox on 2013-01-12
Hi tgalati4,
What a great think.
I changed the USB Port behind the PC between keyboard and mouse and now it works with the space button... whatever... :D

Greetings ):P
mabox

---

### Post by tgalati4 on 2013-01-12
Everything is fixable in linux--you just need to find the patience to find the fix!

---

### Post by mabox on 2013-01-12
> **tgalati4 said:**
> Everything is fixable in linux--you just need to find the patience to find the fix!

With your agree I will use it for my signature :p

---

### Post by tgalati4 on 2013-01-14
I need to translate it to Latin, but yes, go ahead and use it.

Here you go:

Unumquodque potest reparantur. Patientia sit virtus.

---

