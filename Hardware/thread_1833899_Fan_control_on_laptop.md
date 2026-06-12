---
title: "Fan control on laptop"
date: 2011-08-26
forum: Hardware
---

### Post by buntu_hugenewbie11 on 2011-08-26
I am on Dell E6510 running Lucid 64 bit.
I have the updated Bios A09.
When running ubuntu, my computer tends to overheat and locks up and shuts down.
It seems that the fan does not work.
Using the sensors command is useless as I guess fan control is supposedly run by the bios alone.
But my computer does not overheat in windows and the fan definitely runs more in windows.
Is there a way I can get control of the fan settings???
pwmconfig will not work on my machine either.
Please help if you have a solution.

---

### Post by s1hr on 2011-08-26
> **buntu_hugenewbie11 said:**
> I am on Dell E6510 running Lucid 64 bit.
I have the updated Bios A09.
When running ubuntu, my computer tends to overheat and locks up and shuts down.
It seems that the fan does not work.
Using the sensors command is useless as I guess fan control is supposedly run by the bios alone.
But my computer does not overheat in windows and the fan definitely runs more in windows.
Is there a way I can get control of the fan settings???
pwmconfig will not work on my machine either.
Please help if you have a solution.

so u have dual boot? and bios setting is same.
probably source of heat is graphic driver which if give u more perfomance in one hand,perfomance in other hand produce heat.
there is plenty different open source and closed source driver,which driver u use? some open source driver produce perfomance and heat..so try ..different graphic driver..

---

### Post by buntu_hugenewbie11 on 2011-08-26
Yes I have dualboot.
But the machine never overheats in Windows.
Is there a way to get manual control over the fan.
i8kmon should work but it gives me nothing here.
As for video drivers 
lspci gives the following:
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
01:00.0 VGA compatible controller: nVidia Corporation NVS 3100M (rev a2)
01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)

---

### Post by s1hr on 2011-08-26
> **buntu_hugenewbie11 said:**
> Yes I have dualboot.
But the machine never overheats in Windows.
Is there a way to get manual control over the fan.
i8kmon should work but it gives me nothing here.
As for video drivers 
lspci gives the following:
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
01:00.0 VGA compatible controller: nVidia Corporation NVS 3100M (rev a2)
01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)

That is not name of driver ,that is hardware.
try system->administration->additional hardwere drivers(if u have that),or type in terminal sudo apt-get install jokey-kde (for kde desktop,but can work on gnome too) that program is more simplier then jokey for gnome,maybe you can find it in ubuntu center of software too, and then start that program,and ACTIVATE closed source driver,...will be downloaded and after that just restart laptop,and lets see if that was main thing.

---

### Post by buntu_hugenewbie11 on 2011-08-27
I am using the correct nvidia driver for Lucid.
Is there a way to control the laptop fan in Lucid?
Any Dell users have this problem?

---

### Post by s1hr on 2012-03-27
so ,first there is open source and closed source drivers for same thing, and in many cases, from any kind, or to say group of kind, of particular driver,there is many times ,many different drivers which all works.
Some graphic card driver from open source works better in 2D ,some works better in 3D, some when give outstanding performance ,comparing to closed source driver, then those performance produce heat,what is logical,and that is not problem when we use those particular driver in desktop with good cooling, but in laptop ,with prolonged use can make it heat faster.

So again ,you can choose some other driver, for example if u use closed source ,u can try open source which are generally better in 2D applications,what i supose and think that is more better for use in laptop ,as for gaming we use usually desktops.
Its your free choice.

Again to mention,as that is well know thing, driver which give u more perfomance ,will make that ur component produce more heat.

and then will be wise to monitor and control and even adjust speed of the fan(s)...
that is usually even possible from bios, but also with some hardwere like potenciometers, regerdless of operating system.

---

### Post by s1hr on 2012-03-27
ok, as ur using laptop, so if u dont want to control fan from bios,or u dont have that option, and cos ur on laptop ur limited to install some hardwere like potenciometer(s) then you can use this program in Ubuntu.(one of plenty)

lm-sensors, basically its for monitoring but can be used for control too.

more about ,you can find here in ubuntu manuals:lolflag:


[http://manpages.ubuntu.com/manpages/hardy/man8/fancontrol.8.html]("http://manpages.ubuntu.com/manpages/hardy/man8/fancontrol.8.html")

):P

---

### Post by Dodeca on 2012-03-27
my laptop overheated till I slowed down the cpu.

I found and installed an app that displays and sets the cpu speed ... got it years back.

Clicked on  the "about" ... 

CPU Frequency Scaling Monitor 2.30.0 - 2004 Carlos Garcia Campos.

...

Now my laptop is more under my control.

good luck !

---

