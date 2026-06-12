---
title: "ACPI - what can we do with it ?"
date: 2004-11-10
forum: Hardware &amp; Laptops
---

### Post by wasteed on 2004-11-10
I installed warty on my toshiba satellite yesterday, and so far I am quite impressed - a very nice distro.

One thing that concerns me is that it has defaulted to ACPI
for power management, but I am not sure what I can actually do with ACPI.

Before warty, my laptop ran Mandrake and used APM for power management. Using this, suspend actually worked. I could also use the toshset utility to control the lcd brightness and the cpu speed.

Under warty with ACPI, I have added toshiba_acpi and speedstep-ich to /etc/modules, so they get loaded at boottime. So far the only way I can see to control the lcd brightness is to

echo "brightness:4" > /proc/acpi/toshiba/lcd.

Hardly user friendly! 

Also, I do not seem to have control over the cpu speed.
While powernowd is running and the cpu seems to be  at 1.2 or 1.7 GHz, sometimes I would like to set it at the lowest setting and just leave it (e.g. on long flights) to maximise my battery life. Is this possible?

There does not seem to be any suspend capability under ACPI. Also, I am not sure if the laptop_mode.sh script gets run when the laptop is running on it's battery. Should I be doing this by hand ?

Does anyone have any ACPI power management tips ?

---

### Post by wasteed on 2004-11-18
I am still having issues with power management on this
laptop.  To summarise, it is a Toshiba Satellite 2410 with a nVidia GeForce4 420 Go graphics controller. 

Prior to running ubuntu I had Mandrake 9.1 on it, and apm suspend worked absolutely fine from  X (with the binary nvidia driver installed). Now under ubuntu  neither acpi or apm return from a suspend correctly (just a blank screen) and   I have to hit the power button to reboot. 

Like under mandrake, I have the binary nvidia drivers installed,  and I noticed in the included nVidia README that it says beta support is available for ACPI, but you have to use the nvidia_agp  kernel module, rather than the agpgart module.

Now no matter what I do, I cannot get it to boot up loading the nvidia_agp module. I have specifiied the correct settings in the XF86Config file, tried loading it from /etc/modules,
but it always comes up with the agpgart modules loaded!

I think the reason for this is the framebuffer module vesafb is inserted sometime during the bootup sequence, and it must load in agpgart. This even happens after configuring grub to bootup non-graphically. Does anyone know what causes vesafb to get loaded at bootup? Is it gdm ?

I have also tried forcing acpi suspend (to memory, S3) after quitting X and unloading the nvidia kernel module. That is :

sudo /etc/init.d/gdm stop
sudo rmmod nvidia
sudo sh -c "echo 3 > /pric/acpi/sleep"

At this point, the laptop suspends nicely. Now if I shut the lid, wait for a few seconds, and open the lid again, the laptop
resumes from suspend to the console. But then, after a few more seconds, a message flashes up which says the power button has been pressed and the system starts to shutdown!
A similar thing happens if, after I have suspended it, I don't shut the lid but resume it by pressing the power button.
It resumes OK, but says the power button has been pressed and starts to shut down again! 

Anyone have any hints or tips how to solve this?

On the plus side, the powernowd and cpufreq CPU speed control works really well. I discovered the correct cpufreq module for this laptop is the p4_clockmod one, and it gives great speed control from 100% down to 12% CPU speed.

---

### Post by Roland77 on 2004-11-18
I had the same issue on my thinkpad t21.
It wouldnt go out of stanby anymore, even if I opened the lid again.
It would go into stanby pressing Fn + F4,  tried pressing that again, that worked.
If u would press the power button, it would shutdown, just press ur stanby-button again to wake it up again.

Still sometimes X got all weird... 
i want apm back ....
;)

greetz Ro*

---

### Post by andy_sp1ke on 2004-11-18
Your all one step ahead of me!!! I really want to get control over the power settings of my laptop so that I can have it near silent at night so I can download and not be kept awake!! I need to control the fan speed and also the CPU speed so i can turn the fan down/off and not fry my cpu!!

Andy

---

### Post by wasteed on 2004-11-19
[QUOTE=andy_sp1ke]Your all one step ahead of me!!! I really want to get control over the power settings of my laptop so that I can have it near silent at night so I can download and not be kept awake!! I need to control the fan speed and also the CPU speed so i can turn the fan down/off and not fry my cpu!!

Andy[/QUOTE]
 what make is it? if it is a toshiba I might be able to help ?

---

### Post by DriftSK on 2004-11-25
[QUOTE=Roland77]
i want apm back ....
;)

greetz Ro*[/QUOTE]

I have LOTS of issues on an A21m Thinkpad, due to lousy ACPI support in bios. Updating to the latest bios release doesn't help: the 3com miniPCI NIC hangs up completely if ACPI is running.

However I solved this by reverting to APM. Here's how I did it:
- installed Ubuntu with acpi=off as boot kernel parameter, by starting the installation process with *linux acpi=off* at the very beginning;
- after the installation ACPI was disabled by default in /etc/grub/menu.lst, so I just enabled APM by loading its module, adding *apm* in tail of /etc/modules.

And that's it, you're running with APM now. ;-)

---

### Post by Thaddeus Morgan on 2004-12-16
[QUOTE=DriftSK]
- after the installation ACPI was disabled by default in /etc/grub/menu.lst, so I just enabled APM by loading its module, adding *apm* in tail of /etc/modules.
[/QUOTE]

I think you mean /boot/grub/menu.lst.  Thanks for the information, I'll try it out on my T42p, which also doesn't seem to like ACPI.

---

### Post by andy_sp1ke on 2004-12-16
[QUOTE=wasteed]what make is it? if it is a toshiba I might be able to help ?[/QUOTE]

It is a Toshiba!! a satelitte sa40, all the power gizmos work in XP. ACPI loads, i see the module getting an ok at start up. Also when running on battery the LCD brightness does drop slightly. how can i take control of it?

Andy

ps. sorry for the delay in posting!

---

### Post by jdong on 2004-12-16
[QUOTE=Thaddeus Morgan]I think you mean /boot/grub/menu.lst.  Thanks for the information, I'll try it out on my T42p, which also doesn't seem to like ACPI.[/QUOTE]

No, he doesn't. /etc/modules is a list of modules to auto-insert at boot. You need to insert this module before using APM... for obvious reasons!

---

### Post by markus on 2004-12-16
Hey! I have a toshiba satellite A50 and.. I must say i'm a little fed up with the power management. I've tried to make speedstep work but it has been impossible, how did you do it?? I just want my laptop to keep cool!
And I also wanted to know how you load the toshiba modules, as I'm new to linux I think i'm not doing it correctly.

Please help me! XD

Thanks

---

### Post by Thaddeus Morgan on 2005-02-10
[QUOTE=jdong]No, he doesn't. /etc/modules is a list of modules to auto-insert at boot. You need to insert this module before using APM... for obvious reasons![/QUOTE]

Yes, but I was referring to /etc/grub/menu.lst, which doesn't exist.  Rather, I think he meant /boot/grub/menu.lst, which is where you would pass boot-time kernel parameters, such as turning ACPI off.  Of course, you still have to add apm to /etc/modules as you said.

---

### Post by lerrup on 2005-02-11
I am running a Samsung X15 plus and I can't get ACPI to function at all.  KDE tells me that its not installed correctly and I need to rebuld my kernel.

Do I have to?  Is ACPI already there?  Should I install hoary? 

I am sorry, its really, really frustrating me.

---

### Post by jerome bettis on 2005-02-11
you toshiba people might want to recompile your kernels with toshiba laptop support and the toshiba laptop extras configured in. it might already be in there, but it doesn't sound like it so it's worth a look at least.

---

### Post by Jspired on 2005-02-11
[QUOTE=jerome bettis]you toshiba people might want to recompile your kernels with toshiba laptop support and the toshiba laptop extras configured in. it might already be in there, but it doesn't sound like it so it's worth a look at least.[/QUOTE]

..but first, make sure you have a native Toshiba BIOS and not a Phoenix BIOS.  (Found this one out the hard way.)

---

