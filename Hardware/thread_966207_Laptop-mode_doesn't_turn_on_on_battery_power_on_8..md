---
title: "Laptop-mode doesn't turn on on battery power on 8.10"
date: 2008-11-01
forum: Hardware
---

### Post by Valde_91 on 2008-11-01
Hi!

I upgraded to Intrepid yesterday. I solved a lot of littles problems caused by the upgrade, but at the end my HP compaq Nx7000 works quite well. 

But I still have a problem with laptop-mode:

I set the  /etc/laptop-mode/laptop-mode.conf and the /etc/default/acpi-support files (see attachments) to turn on laptop mode when to computer runs on battery. But when I unplug the cable laptop-mode doesn't turn on!

If I code on the terminal after having unplugged the cable ```
 cat /proc/sys/vm/laptop_mode 
``` I obtain 0, that's means that laptop_mode is turned off.

If I started manually laptop_mode in the terminal with the command 
```
 sudo laptop_mode start
``` and then ```
 cat /proc/sys/vm/laptop_mode 
``` I obtain 2, that's mean that laptop_mode is turned on.

can someone help me to solve this please? because without the laptop_mode on when the battery is critical my computer doesn't hibernate.

thanks to all

Valde_91

---

### Post by Valde_91 on 2008-11-01
Hi! I have another related issue:

I waited until my battery dies with laptop-mode turned on, and now (without touching anything in laptop-mode.conf and in acpi-support that I posted before) hibernating doesn't work. It's work only if, after that the power-manger says that the battery is very critical (3%), I relaunch laptop_mode in the terminal. It's very strange because laptop-mode.conf it's set to hibernate at 6%, but even if laptop_mode was on nothing happens until I relaunched it manually.

After I replugged my laptop, turn it on. Laptop_mode was still on even if I put the AC cable, so I turned off manually. The terminal says that it's off, but my HD still spin up, so I think that the laptop_mode is not really disabled. 

Anyone having similar issues with laptop_mode?

thanks Valde_91**[B][B]**[/B][/B]

---

### Post by phatjonny on 2008-11-02
I am running the same machine and just changed to Ibex also.  I am having similar problems...  

The battery is not really charging, and when I pull the power cable it does not switch to battery...

John

---

### Post by Valde_91 on 2008-11-02
> **phatjonny said:**
> I am running the same machine and just changed to Ibex also.  I am having similar problems...  

The battery is not really charging, and when I pull the power cable it does not switch to battery...

John

Hi phatjonny!

Do you have upgraded to Ibex from Hardy or do you have done a fresh install? 

I ask you that because I don't know if a fresh install will resolve this problems.

Thanks 

Valde_91

---

### Post by Valde_91 on 2008-11-02
I find a solution that worked for me:

1. Open your Synaptic Pack Manager and Mark for reinstallation the following packages: acpi, acpid, acpi-support, laptop-mode-tools, laptop-mode-detect

2. then in terminal type
```
sudo gedit /etc/default/acpi-support
```

3. Check the line 
```
ENABLE_LAPTOP_MODE=
```
Mine was set on 1, but I find on the laptop-mode site ([http://samwel.tk/laptop_mode/packages/ubuntu](http://samwel.tk/laptop_mode/packages/ubuntu)) that this line must be set on true. 

4. save and exit.

5. After that I restarted my computer and plug-in in the cable disable laptop-mode and plug-off the cable enable laptop-mode. You can check this on the terminal by typing:

```
cat /proc/sys/vm/laptop_mode
```

This procedure solved also my spin-up problem. But I still don't know if hibernating will working on critical battery, because I must wait that my battery dies. 
Probably my problem was caused by the fact that during the upgrade I keep my old laptop-mode.conf.

I hope that this thread will by useful to you

bye bye Valde

---

### Post by phatjonny on 2008-11-02
I upgraded from Hardy.  

My laptop mode was set at false, so I changed it to true.

Battery is still only 4% charged so will pull cable later when it is fully charged.

I have never managed to get the wireless working on this machine.  I know we are off topic, but if you can direct me to a driver for my wireless card or give any advice on how to set it up that would be great!

Thanks

---

### Post by Valde_91 on 2008-11-02
Hi phatjohnny!

I run Ubuntu since 6.10 and I never had problems for the Wireless card. It worked always out of the box!
What card do you have? I have a Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter. I checked on the restricted driver and my computer doesn't use a proprietary driver for the wireless adapter. 

You can see your model by typing in terminal ```
lspci
``` 

btw I think that hibernating still doesn't work on my machine

bye bye 
Valde

---

### Post by Valde_91 on 2008-11-02
Hi! Phatjohnny,

Try with this wiki. [http://www.linuxextremist.com/2006/06/21/ubuntu-dapper-drake-606-on-hp-compaq-nx7000-laptop/](http://www.linuxextremist.com/2006/06/21/ubuntu-dapper-drake-606-on-hp-compaq-nx7000-laptop/) . It's quite old (it's for dapper) but I think that I can solve the problem with your wireless card.


Bye

---

### Post by phatjonny on 2008-11-03
I have the same card as yours and will try the tutorial next weekend when I have more time.  

My battery is still not really charging, about 1% in 24hours I think, and when I pull the power cord it shuts off.  Not a huge issue as I rarely remove it from the desktop, but the backup supply of the battery would be nice to have...  

Also when I leave the laptop plugged in over night the charge light is off in morning, but returns when I pull the cord and put it back in again.

Any ideas?

---

### Post by Valde_91 on 2008-11-03
Hi phatjonny,

I think that your problem with the battery is more an hardware problem then an OS problem. Probably your battery has no more capacity or the alternator on your machine is broken. Did you always leave your computer with the power cord plugged-in? If yes, that can kill the capacity of your battery.

But anyway try to calibrate yours battery:

1. Turn on  your computer with a finger ready on the F10 Button

2. When the HP splash screen appears push F10, you will enter the Bios

3. Select the TOOLS and then Battery calibration and follow the instruction

Good luck

bye bye Valde

---

### Post by phatjonny on 2008-11-14
Dear Valde_91

Got my wireless working, thanks very much.

The issue with the battery is, I think connected with the OS upgrade as it was working fine with Heron.

My battery is charging VERY slowly and when I remove the power cord it shuts down violently, ie it doesn't switch to battery power.  Ironic really that now that I wireless up and running the battery will keep me stationary.

Any ideas on resolution?

---

### Post by Valde_91 on 2008-11-14
Hi phatjonny!

But your battery chrages slowly also when you charge your machine when it's shut down?

bye bye vade_91

---

### Post by phatjonny on 2008-11-14
Yes it charges when the computer is turned off, but not very long.  For example if I leave the computer plugged in but off overnight then in the morning the charge led on the computer is off, and I assume it has stopped charging.  When you pull the power cord out and stick it back in it lights up again.  The computer will not start without AC...

Again, thanks with the wireless!

---

### Post by Valde_91 on 2008-11-15
Hi phatjonny!

I'm happy that you solved your wireless problem! But I still don't have an idea how to solve your battery charging problem...have you looked on launchpad  if anybody have some similar problem ([https://launchpad.net/ubuntu](https://launchpad.net/ubuntu))

And have you tried to calibrate the battery as I suggest you in post #10?

bye bye Valde_91

---

### Post by Valde_91 on 2008-11-15
Hi phatjonny!

I searched a bit on internet: It seems that quite a lot of Hp/compaq machines have this problem, mostly running Windows XP or Vista. They solve the problem doing a PowerDrain:

1. Turn Off your machine
2. Detach your machine from the AC cable AND unmount the battery
3. Hold down the power button for 1-2 minute, to drain any remaining charges on the circuit board.
4. then put back the battery on your machine
5. plug-in the AC cable, Allow the laptop to charge for a couple of hours, and then turn it on.


Others people simply turn on without the battery. Then they runs the computer only with the AC cable for 5 minutes and then, WITH THE COMPUTER ON, they put back in place the battery. If you try that be very carfull not to unplug the AC cable when you move the computer to put in the battery...

bye bye Valde_91

---

### Post by phatjonny on 2008-11-15
Wireless running perfectly and battery back to original functionality.  

danke vielmals

John

---

### Post by Valde_91 on 2008-11-15
Hi phatjonny! Only for information which method do you used? the calibration or the powerdrain?

I'm glad that I helped you! 

bye bye valde_91

---

### Post by phatjonny on 2008-11-15
I tried the calibration method in the BIOS when you first suggested it and nothing really happened.  It only told me my battery was at 13% charge.

Earlier tonight I pulled the battery and held the power button, as you suggested, and left it charging for 90mins.  Hey presto battery working 100%, I can pull the power cord and start from battery too.  A real success.  Thanks again.  Now I am working on Skype...

---

### Post by Ryan2009 on 2008-11-25
> **Valde_91 said:**
> I find a solution that worked for me:

1. Open your Synaptic Pack Manager and Mark for reinstallation the following packages: acpi, acpid, acpi-support, laptop-mode-tools, laptop-mode-detect

2. then in terminal type
```
sudo gedit /etc/default/acpi-support
```

3. Check the line 
```
ENABLE_LAPTOP_MODE=
```
Mine was set on 1, but I find on the laptop-mode site ([http://samwel.tk/laptop_mode/packages/ubuntu](http://samwel.tk/laptop_mode/packages/ubuntu)) that this line must be set on true. 

4. save and exit.

5. After that I restarted my computer and plug-in in the cable disable laptop-mode and plug-off the cable enable laptop-mode. You can check this on the terminal by typing:

```
cat /proc/sys/vm/laptop_mode
```

This procedure solved also my spin-up problem. But I still don't know if hibernating will working on critical battery, because I must wait that my battery dies. 
Probably my problem was caused by the fact that during the upgrade I keep my old laptop-mode.conf.

I hope that this thread will by useful to you

bye bye Valde

This fixed my laptop_mode, thanks

---

### Post by krlhc8 on 2008-12-22
Thank you Ryan 2009!!!  It fixed my girlfriend's laptop.  I was worried in the package manager that laptop-mode had to be removed when reinstalling and installing packages, but it appears to be working fine.

---

