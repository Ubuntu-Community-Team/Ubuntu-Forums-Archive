---
title: "Toshiba Satellite L305d CPU Overheating - 9.04 - Tried Everything"
date: 2010-03-15
forum: Hardware
---

### Post by lazypeterson on 2010-03-15
My CPU temperatures are constantly between 70-95 degrees, and my computer overheats and shuts down all the time. I'm dual booting with Vista, and the fan works just fine in Vista, I've never had any problems. But since upgrading from 8.10 to 9.04, I've had this problem. 

I've tried adding ```
sudo gedit /boot/grub/menu.lst
``` to my grub file, but that didn't work. I've tried mostly everything in this post: [http://ubuntuforums.org/showthread.php?t=1042500&highlight=l305+overheat]("http://ubuntuforums.org/showthread.php?t=1042500&highlight=l305+overheat"), with no luck there either.

And I've searched all throughout this forum for a solution, with no luck. Any help would be immensely appreciated!

---

### Post by lazypeterson on 2010-03-15
Bump

---

### Post by lazypeterson on 2010-03-16
slump

---

### Post by lazypeterson on 2010-03-28
bump

---

### Post by lazypeterson on 2010-04-01
bumpity

---

### Post by lazypeterson on 2010-06-10
Still having this problem. Can anyone help?

---

### Post by yossell on 2010-06-11
Not really an expert but...

In my installation, one thing that gnome often does on boot up is run cpu in performance mode so it's always running as fast as possible. That makes a big difference to the heat and battery life. If you add the cpu frequency scaling monitor to the gnome panel, this will allow you to set the cpus settings - running 'ondemand' or `powersave' should keep the chip running slow, without much noticable degradation of performance.

A utility I especially like is powertop, from [http://www.lesswatts.org/projects/powertop/](http://www.lesswatts.org/projects/powertop/)

though it's getting a little out of date perhaps. This analyses your system and makes suggestions - following these suggestions may also help you cool the computer down.

---

### Post by lazypeterson on 2010-07-14
> **yossell said:**
> Not really an expert but...

In my installation, one thing that gnome often does on boot up is run cpu in performance mode so it's always running as fast as possible. That makes a big difference to the heat and battery life. If you add the cpu frequency scaling monitor to the gnome panel, this will allow you to set the cpus settings - running 'ondemand' or `powersave' should keep the chip running slow, without much noticable degradation of performance.

A utility I especially like is powertop, from [http://www.lesswatts.org/projects/powertop/](http://www.lesswatts.org/projects/powertop/)

though it's getting a little out of date perhaps. This analyses your system and makes suggestions - following these suggestions may also help you cool the computer down.

Thanks for your response, I added the CPU performance to the panel and it set it at performance, but I'm still experiencing the overheating problem.

---

### Post by lazypeterson on 2010-10-19
Bump... the only solution I've found for this is physically blowing in my laptop vent. 

Anyone?

---

### Post by jweby on 2010-11-07
I have a Toshiba L305D-5928 and am having the same problem. The cpu gets to 90 plus degrees Celsius in Ubuntu under load. Been doing it since the Version 9's and still doing it thru version 10.10. When in Vista the cpu fan normally spins on low and spins faster when ever the temps rise, over 60C in vista I can hear it up-spin and it gets faster if cpu temps continue to rise. But when in ubuntu the cpu fan does not up-spin as temps rise, causing overheating of the CPU. In vista cpu temps cap out at 70~72 C with the fan spinning at what appears to be high. In ubuntu the temps have reached the 90's C

I really do not know, but I think there is an ACPI incompatibly with ubuntu and this series of laptops. Also none of the on keyboard acpi functions work either, dim/brighten display etc.

My short solution is, the cpu fan in ubuntu will stay at what ever speed it is when ubuntu boots. When it gets hot in ubuntu I reboot and I wait in Grub for the fan to spin up then hit enter to boot ubuntu. Then the fan will stay on  a higher speed and keep the cpu cool, not great for battery life. If ubuntu is booted when the fan is spinning slow, the cpu over heats.

I realize this is not a solution, wish I new more . . . on how to fix it.

Also I have tried all the things I have found in the forums and elsewhere on the net. Including acpi_osi="Linux". Does not seem to change behavior. Nor does it appear to be a faulty laptop as its fine in windows.

---

### Post by jweby on 2010-11-07
> **lazypeterson said:**
> Bump... the only solution I've found for this is physically blowing in my laptop vent. 

Anyone?

Yep I have done that too to keep my toshiba cool. Back in the day with Commodore 64 1541 floppy drives, blowing a fan into the vents is how we kept the drive spindle from becoming unseated due to heat when playing Bards Tale. We have come so far yet so little distance in 25 years.

---

### Post by azitizz on 2010-11-22
I also have a Toshiba satellite. Mines a 350D. Like you said, mine stays at a steady fan speed, a low one, and overheats in Ubuntu, but works fine in Windows.

Ill try the log-in fan speed trick. at least its a temporary solution. 

Isnt there some kind of program that would be able to manually control the fan speed? Or at least command it to increase at a given temp?

Would this be something to submit as a bug to the developers?

---

### Post by snagi12 on 2011-04-08
i am running 10.10 with kernel 2.6.35-28-generic-pae.  i had the same issue but i think that i might have solved my systems over heat problem: Toshiba L305D-S5930 with an Athlon dual core

i used several grub boot codes most did not work but this combination i think solved my problem: add acpi=force acpi=copy_dstd to /etc/default/grub

sudo gedit /etc/default/grub

my system use to overheat when using devede during the converting stage but ran fine after adding those codes to the grub.  For people that are new to linux the Method for installation was as follows:

add lm-sensors
sudo apt-get install lm-sensors

then run
sudo sensors-detect

restart

edit grub
sudo gedit /etc/default/grub

add acpi=force acpi=copy_dstd to the line
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

should look like this
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=force acpi=copy_dstd"

update grub
sudo update-grub

restart

my max temp when converting was 77* C and immediately went down after convert prossess to around 54* C

worked for me so you might try that it may help

---

### Post by wari on 2011-09-14
In my Satellite Pro L300D-SP5804 I did the following (just some commands changed):

Enter superuser environment:
```
sudo -i
```
Setup lm-sensors and configure:
```
apt-get install lm-sensors
sensors-detect 
reboot
```

After reboot, I edited grub to add the lines(as sudo):
```
vim /etc/default/grub 
update-grub 
cp /boot/grub/grub.cfg /boot/grub/grub.cfg.bak
grub-mkconfig >/boot/grub/grub.cfg
```

But still my fan keeps running. My temperature reported are all in the range 15-29°C

Any ideas? I'm on a 11.04 amd64 system

---

### Post by jinchuricki on 2011-12-05
Hi, I have the same problem with my Toshiba M505. I have tried anything   but I've got nothing. Then I find the trick to solve this problem.
You can try this trick **[Solution How to Fix Toshiba Laptop Fan Error (Overheat) on Linux (Ubuntu, etc)]("http://jinchuricki.blogspot.com/2011/11/solution-how-to-fix-toshiba-laptop-fan.html")**

---

