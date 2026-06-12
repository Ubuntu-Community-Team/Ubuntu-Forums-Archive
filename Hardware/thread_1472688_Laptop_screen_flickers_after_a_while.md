---
title: "Laptop screen flickers after a while"
date: 2010-05-04
forum: Hardware
---

### Post by Fibonacci on 2010-05-04
Hello.

I've upgraded my laptop (HP nc6400, video card ATI Technologies Inc M52 [Mobility Radeon X1300] [1002:714a]) to Lucid a couple of days ago.
Since then, after a while of the laptop being on, the screen begins to flicker incessantly, which makes it impossible to work. The screen won't stop flickering no matter what I do, unless I completely reboot the computer.

What can I do?

Thank you for your help.

---

### Post by kevinatkins on 2010-05-04
This could be a hardware issue, but to rule out Ubuntu, it might be worth trying a live CD (preferably a different Linux distro) and, if you have a windows partition on the machine, try windows too.

---

### Post by tgalati4 on 2010-05-04
Put some temperature sensors on your taskbar.  ATI's get toasty.  Anything above 70C is asking for trouble.

You can set dynamic clocks (do a forum search) to modulate the graphic card with load so it will run a little cooler.  You can also modulate the fan speed (check the BIOS) and acpitool to also keep the temps under control.

If it's under warranty, it's time to experience HP's stellar customer service.

---

### Post by Fibonacci on 2010-05-04
> **kevinatkins said:**
> This could be a hardware issue, but to rule out Ubuntu, it might be worth trying a live CD (preferably a different Linux distro) and, if you have a windows partition on the machine, try windows too.

Windows works fine, and so did Karmic. I'm sure the problem is with Lucid, but just to be sure, I'll try an old Knoppix version.

> **tgalati4 said:**
> Put some temperature sensors on your taskbar.  ATI's get toasty.  Anything above 70C is asking for trouble.

How do I do that?

> **tgalati4 said:**
> If it's under warranty, it's time to experience HP's stellar customer service.

That is, if it's a hardware problem - which most likely it is not.

---

### Post by tgalati4 on 2010-05-04
sudo apt-get install lm-sensors

(answer yes all the questions)

Reboot may be required.

sensors

Right-click on the taskbar, "Add-to-panel", temperature monitor, choose GPU.

---

### Post by Fibonacci on 2010-05-04
> **tgalati4 said:**
> Right-click on the taskbar, "Add-to-panel", temperature monitor, choose GPU.

That option doesn't appear.

---

### Post by tgalati4 on 2010-05-04
Open a terminal.  What is the output of:

sensors

It should look something like:

tgalati4@tpad-Gloria7 ~ $ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +52.0°C  (crit = +99.0°C)                  

thinkpad-isa-0000
Adapter: ISA adapter
fan1:       4660 RPM
temp1:       +52.0°C                                    
temp2:       +47.0°C                                    
temp3:       +36.0°C                                    
temp4:       +61.0°C                                    
temp5:       +34.0°C                                    
ERROR: Can't get value of subfeature temp6_input: Can't read
temp6:        +0.0°C                                    
temp7:       +27.0°C                                    
ERROR: Can't get value of subfeature temp8_input: Can't read
temp8:        +0.0°C                                    
temp9:       +47.0°C                                    
temp10:      +52.0°C                                    
temp11:      +47.0°C                                    
ERROR: Can't get value of subfeature temp12_input: Can't read
temp12:       +0.0°C                                    
ERROR: Can't get value of subfeature temp13_input: Can't read
temp13:       +0.0°C                                    
ERROR: Can't get value of subfeature temp14_input: Can't read
temp14:       +0.0°C                                    
ERROR: Can't get value of subfeature temp15_input: Can't read
temp15:       +0.0°C                                    
ERROR: Can't get value of subfeature temp16_input: Can't read

You might have to add a gnome-applet:

apt-cache search gnome applet

sudo apt-get install gnome-applets

Now right-click on the task bar.

---

### Post by Fibonacci on 2010-05-05
$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +45.0°C  (crit = +256.0°C)                  
temp2:       +47.0°C  (crit = +105.0°C)                  
temp3:       +43.0°C  (crit = +115.0°C)                  
temp4:       +36.0°C  (crit = +80.0°C)                  
temp5:       +20.6°C  (crit = +105.0°C)                  
temp6:        +0.0°C  (crit = +110.0°C) 

After installing sensors-applet, I can add a temperature monitor to the panel. Problem is, it comes with about 15 temperature monitors, and none of them is labelled "GPU".

---

### Post by Fibonacci on 2010-05-05
My screen is flickering right now, and this is the output of sensors:

$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +55.0°C  (crit = +256.0°C)                  
temp2:       +46.0°C  (crit = +105.0°C)                  
temp3:       +45.0°C  (crit = +115.0°C)                  
temp4:       +40.0°C  (crit = +80.0°C)                  
temp5:       +33.2°C  (crit = +105.0°C)                  
temp6:       +50.0°C  (crit = +110.0°C)                  

So nothing over 60 degrees, even. It's not temperature then.

---

### Post by tgalati4 on 2010-05-06
sudo apt-get install cpuburn

burnP5

(Let it run for a few minutes.)

sensors

The hot chip would be your CPU.

glxgears

(Let it run for a few minutes.)

The hot chip would be your GPU.

You can relabel the temps in the monitors.  The other sensors are battery, power circuit, I/O chip, etc.  You can do a google search and find a reference for the location of the sensors on your particular machine.

sudo apt-get install htop
htop

Monitor the processes that are running when flickering occurs.  It could be some system process (like indexing) that is causing interrupts.

Speaking of interrupts.  Post the output of /proc/interrupts

cat /proc/interrupts

---

### Post by Fibonacci on 2010-05-06
> **tgalati4 said:**
> sudo apt-get install cpuburn

burnP5

(Let it run for a few minutes.)

sensors

The hot chip would be your CPU.

glxgears

(Let it run for a few minutes.)

The hot chip would be your GPU.

Found and labelled. The GPU never gets hotter than 53°C - and when the screen was flickering it was at 45°C, so it's definitely not temperature.

> **tgalati4 said:**
> You can relabel the temps in the monitors.  The other sensors are battery, power circuit, I/O chip, etc.  You can do a google search and find a reference for the location of the sensors on your particular machine.

Couldn't find them anywhere.

> **tgalati4 said:**
> sudo apt-get install htop
htop

Monitor the processes that are running when flickering occurs.  It could be some system process (like indexing) that is causing interrupts.

The screen's flickering right now, yet I see nothing odd on htop.

> **tgalati4 said:**
> Speaking of interrupts.  Post the output of /proc/interrupts

cat /proc/interrupts

$ cat /proc/interrupts
           CPU0       CPU1       
  0:     884661          0   IO-APIC-edge      timer
  1:          9        846   IO-APIC-edge      i8042
  7:          2          0   IO-APIC-edge      parport0
  8:          1          0   IO-APIC-edge      rtc0
  9:       2156          0   IO-APIC-fasteoi   acpi
 12:      97980          0   IO-APIC-edge      i8042
 14:      37830          0   IO-APIC-edge      ata_piix
 15:          0          0   IO-APIC-edge      ata_piix
 16:        567          0   IO-APIC-fasteoi   HDA Intel
 17:         60      34062   IO-APIC-fasteoi   eth2
 18:          1          0   IO-APIC-fasteoi   uhci_hcd:usb4, yenta, tifm_7xx1
 19:          0          0   IO-APIC-fasteoi   uhci_hcd:usb5
 20:        146          0   IO-APIC-fasteoi   ehci_hcd:usb1, uhci_hcd:usb2
 22:       1624       1930   IO-APIC-fasteoi   uhci_hcd:usb3, mmc0
 28:       7599      18651   PCI-MSI-edge      ahci
 29:     794267          0   PCI-MSI-edge      radeon
 30:          2          0   PCI-MSI-edge      eth0
NMI:          0          0   Non-maskable interrupts
LOC:     223254     437739   Local timer interrupts
SPU:          0          0   Spurious interrupts
PMI:          0          0   Performance monitoring interrupts
PND:          0          0   Performance pending work
RES:       4279      33147   Rescheduling interrupts
CAL:         37         72   Function call interrupts
TLB:       2442       1304   TLB shootdowns
TRM:          0          0   Thermal event interrupts
THR:          0          0   Threshold APIC interrupts
MCE:          0          0   Machine check exceptions
MCP:         11         11   Machine check polls
ERR:          0
MIS:          0

---

### Post by Fibonacci on 2010-05-06
Also, I've just tried Windows. The screen did not flicker.
Back to Ubuntu, and even after disabling Compiz the screen still flickers.
So it's not hardware for sure.

---

### Post by tgalati4 on 2010-05-06
Your msi radeon interrupts and rescheduling interrupts are high.  I saw a post for a boot code pci=nomsi.   Search for boot pci msi and try those tweaks.

---

### Post by janneman37 on 2010-05-06
Same problem with ATI x1400 only in ubuntu 10.04...

---

### Post by Fibonacci on 2010-05-06
> **tgalati4 said:**
> Your msi radeon interrupts and rescheduling interrupts are high.  I saw a post for a boot code pci=nomsi.   Search for boot pci msi and try those tweaks.

Couldn't find anything on that - that is, except for this thread.

---

### Post by tgalati4 on 2010-05-06
At the bottom of this post.  It solved a SATA problem which could actually be an interrupt problem:

[http://ubuntuforums.org/showthread.php?t=1472578&highlight=nomsi&page=2](http://ubuntuforums.org/showthread.php?t=1472578&highlight=nomsi&page=2)

---

### Post by jjgibster on 2010-05-07
I'm seeing the same problem on an HP NC6400 Notebook with an ati x1300 video card -- worked fine in 9.10 -- problem started with 10.04 -- In addition, out of nowhere multiple displays when connected to a dock stopped working.

---

### Post by Fibonacci on 2010-05-07
> **tgalati4 said:**
> At the bottom of this post.  It solved a SATA problem which could actually be an interrupt problem:

[http://ubuntuforums.org/showthread.php?t=1472578&highlight=nomsi&page=2](http://ubuntuforums.org/showthread.php?t=1472578&highlight=nomsi&page=2)

Didn't work, the screen is still flickering.

---

### Post by tgalati4 on 2010-05-07
Look for errors in .xsession-errors and Xorg.0.log:

cd
cat .xsession-errors
cat /var/log/Xorg.0.log

---

### Post by Fibonacci on 2010-05-07
> **tgalati4 said:**
> Look for errors in .xsession-errors and Xorg.0.log:

cd
cat .xsession-errors
cat /var/log/Xorg.0.log

Nothing is written to those files when the flickering happens.

---

### Post by janneman37 on 2010-05-08
This problem was solved here when i boot with option "nomodeset"

---

### Post by Fibonacci on 2010-05-09
> **janneman37 said:**
> This problem was solved here when i boot with option "nomodeset"

So far, nomodeset appears to have solved the flickering problem. Thank you!

---

