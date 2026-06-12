---
title: "the battery don't last"
date: 2007-11-15
forum: Hardware &amp; Laptops
---

### Post by nobody850 on 2007-11-15
I don't know whey but the battery with UBUNTU don't last more than 45 minuets, but with XP it gets me up to 2 hours. 
the battery icon is correct, after 45 minuets the laptop shuts down
i am using ubuntu 7,10

---

### Post by handaxe on 2007-11-15
edit the last line of /etc/default/acpi-support to read 

ENABLE_LAPTOP_MODE=true

See if that helps. This is disabled by default as some lappies do not behave.

Also, remember that Ubuntu does not ( or at least on mine, does not) automatically dim the screen on battery - power hungry etc

HA

---

### Post by deez on 2007-11-15
I'm having the same problem except I can't compare my battery life to Windows XP.  I get just over half an hour and I have already edited '/etc/default/acpi-support'.  But I still get a value of 0 when I do 'cat/proc/sys/vm/laptop-mode.  Any other ideas?

Peace

---

### Post by nobody850 on 2007-11-16
sorry guys, I am a newbie on ubuntu
how do I edit /etc/default/acpi-support ? I tride the terminal but it told me permission denied ( and I am the admin )

---

### Post by nobody850 on 2007-11-16
i went to the file but cud not change it! it tels me the i don't have permission.

---

### Post by handaxe on 2007-11-16
```
sudo gedit /etc/default/acpi-support
```

As for other issues: wireless cards can drain if they are constantly polling and not connecting. Some don't switch off easily under Linux. Also, if you have had to use acpi=off or some such switch in the boot loader to get the laptop to boot successfully, you are not using power saving measures by default.

Also check that laptop_mode is working. At the command line type:

```
 sudo laptop_mode 
``` whilst plugged in and then on battery. Output should show that it is enabled inactive and enabled active respectively.

Check cpu scaling. On demand scaling with intensive use will still drain batteries.

```
sudo chmod +s  /usr/bin/cpufreq-selector
``` will enable selection of cpu frequency.  Use the panel applet (right click on panel, "Add to Panel") to easily make selection for power save.

HA

---

### Post by deez on 2007-11-16
sudo laptop_mode gets me command not found

when i tried to put the applet on the panel, it tells me :

You will not be able to modify the frequency of your machine.  Your machine may be misconfigured or not have hardware support for CPU frequency scaling.

I've got a hp 4010 pentium M 1.7Ghz.  

Any ideas?

cheers

---

### Post by deez on 2007-11-16
and my fan is running all the time.  i get the feeling it could be more efficient, a lot more efficient.

---

### Post by handaxe on 2007-11-16
I believe that processor should scale - but I am not certain.

Is "laptop-mode-tools" installed? Check in Synaptic.  That's the script set with laptop_mode.

On the fan issue - this sounds as if ACPI is disabled? What's is the GRUB boot line?

HA

---

### Post by deez on 2007-11-16
I'm not sure how to get the information you're asking for from the GRUB line.  

I just installed laptop mode tools and now it says that my computer is in laptop mode, it's enabled and active.  Thanks

---

### Post by handaxe on 2007-11-16
Not installed then...?  Well, that was not helpful and I assume that the install either failed in some way or did not detect a laptop.

So, check that "powernowd" is also installed, as well as "acpid".

If they are, check with System Monitor if acpid is loaded.

```
lsmod | grep acpi
``` and ```
lsmod | grep power
``` will also give some info re cpu scaling etc.

The GRUB boot can be read in /boot/grub/menu.lst.  Look for something like this, prolly towards the end of the file:

> title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=4acf3744-e5ec-4e79-8302-087a5745bda7 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet
If acpi=off or noacpi appears in the kernel line then it is disabled at boot.  Beware that if you remove this, the laptop may not boot. You will however be able to type the noacpi bit in at the grub menu in order to boot and set the file back. make sure you can do this before you delete anything.

Not too, that 7.10 appears to be misbehaving on HP laptops for some. Search for the thread..

HA

---

### Post by deez on 2007-11-16
This is what I found in boot:

itle		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=65ad7fb2-64d0-4dd9-8641-88a47511f332 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

lsmod | grep power:

cpufreq_powersave       2688  0 

lsmod | grep acpi:

nothing

Those other packages are installed.  

Cheers

---

### Post by handaxe on 2007-11-16
So, acpid is running... well that brings easy solutions to an end. Does having laptop_mode enabled and active on DC improve the battery time at all?

A near constantly running fan is a clear problem and all I can suggest is that you search the forums on that specific issue...

Good luck - 0.5 an hour is not acceptable unless the battery is going belly up. That's why dual boots with windows can be useful if the same happens...

HA

---

### Post by bthoward on 2007-11-16
Install powertop and run it as root.  

"sudo powertop" at a terminal

It will help you to see what is causing your battery life to be shortened and will also give you some pointers on what you may do to help improve life.

---

### Post by deez on 2007-11-16
Thanks for that, I'm going to try a new thread to see if I can get this sorted out.  How can I know if it is the battery going belly up?

---

### Post by silent1643 on 2007-11-16
> **bthoward said:**
> Install powertop and run it as root.  

"sudo powertop" at a terminal

It will help you to see what is causing your battery life to be shortened and will also give you some pointers on what you may do to help improve life.

exactly
[http://www.littleubuntu.com/blog/?p=99](http://www.littleubuntu.com/blog/?p=99)

---

### Post by handaxe on 2007-11-17
> **deez said:**
> Thanks for that, I'm going to try a new thread to see if I can get this sorted out.  How can I know if it is the battery going belly up?

One indication is to left mouse click on the Power Manager tray icon (enable it to show at all times if on AC) and then select the battery. A popup will give some info **IF** the battery is capable of doing so. In my case, this shows that whilst 100% charged, my battery capacity is at 78%. This has been declining over time, as it will, given that batteries (like us :)) age. So my current charge is 34.7 Wh, whilst the design charge is 44.4 Wh.

If your lappie is old and has been through numerous charge / discharge cycles, your battery may be going. I am sure a dealer could test it for you as you lack Windoze as a comparison.

@ silent1643 and bthoward: thnx for the heads up on powertop.

HA

---

### Post by nobody850 on 2007-11-20
sudo chmod +s  /usr/bin/cpufreq-selector

dose not work??

---

### Post by handaxe on 2007-11-20
> **nobody850 said:**
> sudo chmod +s  /usr/bin/cpufreq-selector

dose not work??

Meaning you get an error when you enter the above at the command line, or it is accepted but the cpu will not scale using the "CPU frequency scaling monitor" on the panel to make the change?

The above is for gnome, I must add (and should have added in the post). KDE has kpowersave.  Whether that needs to be set for executable first, I know not as I have never used KDE, but guess not....

CPU scaling is a kernel affair and the cpufreq progs / ACPI in simply interact via with the kernel to achieve the effect. On a laptop it should be happening automatically via ACPI. The cpufreq-selector is simply a manual override.

HA

---

