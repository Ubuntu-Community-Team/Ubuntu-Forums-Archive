---
title: "automatically turn off bluetooth at start up"
date: 2010-09-30
forum: Hardware
---

### Post by Axx83 on 2010-09-30
hi guys, the question is simple, I have a thinkpad x60s with incorporated bluetooth.

The thing works PERFECTLY with ubuntu lucid 10.04 but it is automatically turned on at boot, even if it was off before shutdown. I click on gnome-bluetooth icon to turn it off and everything's alright, but I don't want to do this every time I turn on my notebook!

How do i keep it off at startup ? I only need it a few times but i don't want to disable it completely.

Thank you

UPDATE !!!!!!!!!!!!!!!!

the solution was much much easier than expected, the command is:

```
sudo rfkill block bluetooth
```
which turns completely off bluetooth and can be turned back on easily with
```
sudo rfkill unblock bluetooth
```
so if someone puts this code in /etc/rc.local the command is run at every startup flawlessly

---

### Post by Axx83 on 2010-09-30
if I issue
```
sudo hciconfig hci0 down
```
the icon goes grey, but the bluetooth is still sucking power and in fact is still turned on, it still gives me the option to turn it off. Also when I check on
```
lsusb
```
and
```
sudo powertop
```
bluetooth is definitely on. What commands are issued by gnome-bluetooth when you click on the turn off icon ???

---

### Post by Axx83 on 2010-09-30
```
sudo /etc/init.d/bluetooth stop
```
does the same thing, icon greys out but bluetooth is still on and still attached to usb, only clicking on gnome-bluetooth icon and on turn off actually turns off the device

---

### Post by Jeroensum on 2010-09-30
You might try:
sudo /etc/init.d/bluetooth stop
then
sudo rmmod bluetooth, if it cries it has dependencies, disable them first (one at a time)
sudo rmmod sco
sudo rmmod 
and so on


If that doesn't get you what you need you might be getting what you want from tools like dbus-monitor of strace.

dbus-monitor will tell you what commands are floating accross the message bus and you will be able to write your own script/program to set the same triggers.

strace should be run against the indicator applet found in /usr/lib/indicator-applet/indicator-applet , with strace you can see there what low-level calls are being made to the system.

---

### Post by IcarusR on 2010-09-30
Install Boot-Up Manager (BUM) it is the repositories. You can then control what runs at boot-up, including switch off Bluetooth.

---

### Post by Axx83 on 2010-09-30
> **Jeroensum said:**
> You might try:
sudo /etc/init.d/bluetooth stop
then
sudo rmmod bluetooth, if it cries it has dependencies, disable them first (one at a time)
sudo rmmod sco
sudo rmmod 
and so on
if I remove the modules I won't be able to start bluetooth when I click the button, i think, but I may have to try this first

> 
If that doesn't get you what you need you might be getting what you want from tools like dbus-monitor of strace.

dbus-monitor will tell you what commands are floating accross the message bus and you will be able to write your own script/program to set the same triggers.

strace should be run against the indicator applet found in /usr/lib/indicator-applet/indicator-applet , with strace you can see there what low-level calls are being made to the system.
I tried dbus-monitor and I didn't find what commands it was issuing.

About strace, how exactly do I do what you suggested ?

---

### Post by SlugSlug on 2010-09-30
I disable stuff by

sudo update-rc.d -f bluetooth remove

---

### Post by Axx83 on 2010-09-30
> **SlugSlug said:**
> I disable stuff by

sudo update-rc.d -f bluetooth remove
I tried this one too. First time you run it this is the output:

root@achille-laptop:/home/achille# update-rc.d -f bluetooth remove
 Removing any system startup links for /etc/init.d/bluetooth ...
   /etc/rc0.d/K74bluetooth
   /etc/rc1.d/K74bluetooth
   /etc/rc2.d/S25bluetooth
   /etc/rc3.d/S25bluetooth
   /etc/rc4.d/S25bluetooth
   /etc/rc5.d/S25bluetooth
   /etc/rc6.d/K74bluetooth

the icon goes gray but bluetooth power surge is not effectively off.

---

### Post by SlugSlug on 2010-09-30
after that 
apt-get remove bluetooth  ?

---

### Post by Axx83 on 2010-09-30
> **SlugSlug said:**
> after that 
apt-get remove bluetooth  ?

:confused: I want to turn off bluetooth at startup without disabling it permanently so that I can press the button on top screen and activate it when I need it...not uninstall it.

---

### Post by Axx83 on 2010-09-30
> **SlugSlug said:**
> I disable stuff by

sudo update-rc.d -f bluetooth remove

It seems I permanently removed some link files from rc*.d folders with this command, where they useful ?

---

### Post by SlugSlug on 2010-09-30
nah there just startup links

  pretty sure u can restore them with 

update-rc.d -f bluetooth defaults

---

### Post by IcarusR on 2010-09-30
Axx83

Did you try my suggestion ? No fiddling with files involved & can easily reverse it with a couple of mouse clicks !!


> Install Boot-Up Manager (BUM) it is the repositories. You can then control what runs at boot-up, including switch off Bluetooth. 

---

### Post by Axx83 on 2010-09-30
if I turn off bluetooth services at startup with bum then I won't be able to turn them on with a click on the icon and, by the way, bluetooth modules are still loaded and the bluetooth is still using power from my battery

at least that's what happened in 9.04

---

### Post by Axx83 on 2010-09-30
> **SlugSlug said:**
> nah there just startup links

  pretty sure u can restore them with 

update-rc.d -f bluetooth defaults

I reinstalled bluez and they're back to normal, no problem

---

### Post by msakms on 2010-09-30
Boot-up manager does the magic. Just disable Bluetooth services at startup

---

### Post by Axx83 on 2010-10-01
> **msakms said:**
> Boot-up manager does the magic. Just disable Bluetooth services at startup

I tried, but negative, not only is the bluetooth still physically on (checking with lsusb) but the whole bluetooth services are still on, icon on top and all, like I never used BUM at all.

---

### Post by IcarusR on 2010-10-02
> the whole bluetooth services are still on

Yes you are correct but if in a terminal you do

```
hcitool scan
``` 

you should get the same result as me...

```
hcitool scan
Device is not available: No such device
```

Indicating that the device is not being used & therefore using minimal power.

> bluetooth still physically on (checking with lsusb)

The only way to switch bluetooth device completely off will be either with hardware switch (FN key ?), in bios or with software which is probably not available.

If you are concerned about the bluetooth modules still being loaded you could write a simple script that unloads/reloads them.

I suspect using bum is as near as you will get as an easy to reverse solution.

---

### Post by Axx83 on 2010-10-05
the solution was much much easier than expected, the command is:

```
sudo rfkill block bluetooth
```
which turns completely off bluetooth and can be turned back on easily with
```
sudo rfkill unblock bluetooth
```

---

### Post by philcarao88 on 2010-10-14
Hi there! may i ask help too?
my problem is the reverse one,
i can't Enable my Bluetooth (Fn+F12) and Camera (Fn+F10) on my laptop.
those are already attached inside my computer.

these works fine when i used ubuntu 9.04, help please....

---

### Post by Axx83 on 2010-10-14
sorry man that's another issue related to the keyboard combination and your specific notebook, you better search for a bug on launchpad or post a new message

---

### Post by klausner on 2011-04-12
> **Axx83 said:**
> 
the solution was much much easier than expected, the command is:

```
sudo rfkill block bluetooth
```
which turns completely off bluetooth and can be turned back on easily with
```
sudo rfkill unblock bluetooth
```

Why use *sudo*? Command seems to run fine with user privileges.

---

