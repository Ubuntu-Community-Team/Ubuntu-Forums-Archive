---
title: "Satellite Pro L300 overheating"
date: 2012-07-31
forum: Hardware
---

### Post by Sijmen on 2012-07-31
There are two Toshiba Satellite Pro L300's on my desk. One with an Intel Core 2 Duo T6400 and one with an Intel Core 2 Duo T8100. The one with the T8100 runs beautifully, the other one on the other hand is a real smart ***.  It really, really, really likes heat! It likes heat so much it just shuts the fan off completely and then goes into a stupor and slowly starts enjoying the tingly feeling of getting closer and closer to the boiling point. I don mind this machine has a mind of its own. It just that he doesn't realize the consequences. Luckily, Ubuntu has been designed as a smart system and after about an hour Ubuntu sees the temp going over a 104 degrees Celcius and shuts down the system.

I've been searching the internet for some kind digital Super Nanny program to teach this L300 a lesson in temperature control. The problem is.... there isn't a Super Nanny program. I've found some files to change the thermal trip points, but even as root I'm not allowed to change the values. 

Is there any way to change the values in these files? Or does a Super Nanny tool exist?

Sincerely.

Sijmen

---

### Post by Sijmen on 2012-07-31
Right....... just when you think you've found all the info there is......:

[http://ubuntuforums.org/showthread.php?t=309407&highlight=change+thermal+trip+points](http://ubuntuforums.org/showthread.php?t=309407&highlight=change+thermal+trip+points)

sijmen@Blofeld:~$ acpi -t
The program 'acpi' is currently not installed.  You can install it by typing:
sudo apt-get install acpi

Here goes after install and reboot:

sijmen@Blofeld:~$ acpi -t
Thermal 0: ok, 39.0 degrees C

And now we wait.......

---

### Post by houseworkshy on 2012-07-31
There are several tools in the repositories if you search for "temperature". some of those may be an easy way in.  In a termanal you could try "man pwmconfig" and "man fancontrol".  That will display the manual pages of command lines you might want to  use.  Read up first and be cautious if you decide to use them, as you know this is in a hardware frying via keyboard entry area.
I'd also recomend giving the machine a good clean, especially the heat sink.  With luck it could be that is all you need to do.

---

### Post by houseworkshy on 2012-07-31
Just did a quick search on youtube for "cleaning a Toshiba Satellite Pro L300" and there are a lot of videos on it, at least one is specific to the fan.  As you have two machines you could have have the vid running on one, with liberal use of the pause and rewind buttons, whilst cleaning the other.  I find seeing it done easier than reading about it for the mechano side of things.

---

### Post by Sijmen on 2012-07-31
Took the machine apart and it looked brand new. I applied new thermal grease just to be sure. 

I tried the pwmconfig command:

```

root@Blofeld:/home/sijmen# pwmconfig
# pwmconfig revision 5857 (2010-08-22)
This program will search your sensors for pulse width modulation (pwm)
controls, and test each one to see if it controls a fan on
your motherboard. Note that many motherboards do not have pwm
circuitry installed, even if your sensor chip supports pwm.

We will attempt to briefly stop each fan using the pwm controls.
The program will attempt to restore each fan to full speed
after testing. However, it is ** very important ** that you
physically verify that the fans have been to full speed
after the program has completed.

/usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed

``````

root@Blofeld:/sys/devices/virtual/thermal/thermal_zone0# cat trip_point_0_type
critical
root@Blofeld:/sys/devices/virtual/thermal/thermal_zone0# cat trip_point_0_temp
104000
root@Blofeld:/sys/devices/virtual/thermal/thermal_zone0# cat trip_point_1_type
passive
root@Blofeld:/sys/devices/virtual/thermal/thermal_zone0# cat trip_point_1_temp 
104000
root@Blofeld:/sys/devices/virtual/thermal/thermal_zone0# cat trip_point_2_type 
active
root@Blofeld:/sys/devices/virtual/thermal/thermal_zone0# cat trip_point_2_temp 
70000

```

So that means it switches on at 70, but is passive at 104 and at 104 it goes critical...... makes absolute sense.

Dug a bit further:

```

root@Blofeld:/sys/devices/virtual/thermal/thermal_zone0/cdev2# cat type
Fan
root@Blofeld:/sys/devices/virtual/thermal/thermal_zone0/cdev2# cat cur_state
1
root@Blofeld:/sys/devices/virtual/thermal/thermal_zone0/cdev2# cat max_state
1

```

cdev2 is the fan and according to this it can go any faster than its current state...... which is basically no state at all.

---

### Post by houseworkshy on 2012-07-31
I'm out of my depth here, so this one is as much a bump as anything.  Reading through fancontrol's manual, it seems to depend on lm_sensors so put that in if it's not already there, it may help with the lack of pwm-capable modules mentioned by pwmconfig.  Or may not, but it won't hurt. So out of my depth you can see the bubbles.
 
If the box is clean it *could* be that some program is causing the problem, flash video often goes wrong in a very heavy hot sort of way for example.  As it causes a shut down the clue to the cluprit, if there is one, may be found in the system logs.  Looking at the system prosesses may also be helpful, top, htop or via system monitor.  You may need to use these diagnotic programs with sudo if you want to see everything.

A short term "it's not really fixed yet" solution would be to change the gui to something lighter.  Lxde, among others, is available in the repositories.  You wouldn't loose what you have as if installed you just choose to use it at logon, the old GUI will still be there as a choice in cooler times.  About a win98 ish interphase, but very light on system resources, which many use to save battery power when on the move anyway.
Darn't give anymore advise on something this critical so hope someone who knows more turns up soon good luck 
and ... bump.

---

### Post by ahallubuntu on 2012-07-31
It's hard to imagine it's really getting to 104C (water boils at 100C).  Could you mean 104F?  Where are you getting this temperature reading?

I'm exactly sure what you mean by what you describe.  If the fan shuts off before it shuts down, that's probably why it's overheating; the fan must be running to keep the CPU cool.  Maybe the fan needs to be replaced.  Is it plugged in securely to the motherboard?

I've not had good luck with Linux tools detecting temperature sensors especially on laptops.  Sadly, I'd probably recommend going back to Windows at least briefly until you can debug this issue.  There are some decent tools that let you monitor fan speed and sensor temperature for Windows.  There are legit versions of say Windows 7 you can download and install without a product key (for 30 days until it stops working) to allow you to test it out, perhaps if you have a spare hard drive or something.  If you are dealing with a heating issue, it's important to have accurate temperature readings.

You might also look for a BIOS update from Toshiba's website.  Are the BIOS versions the same on both of the laptops?  Another reason Windows would be helpful briefly: to install any BIOS update you might have.

---

### Post by Sijmen on 2012-08-01
The fan turns on immediately when the power button is pressed. As soon as xubuntu has started it slows down to a crawl. Toshiba doesn't provide temperature settings in the BIOS, so the fan is controlled by the OS, which isn't controlling the fan.

More problems arise with this system. The brightness controls aren't working anymore. I'm making a backup now. The data is transfered from the machine via USB to an external disk.  This goes somewhat smoothly. If I try a transfer from the disk to the  machine, XFCE hangs after about ten seconds.  I hope a reinstall of xubuntu will help.

---

### Post by ahallubuntu on 2012-08-01
If you have two identical laptops, where one works well and one doesn't, try swapping hard drives.  If the one that is bad now is still bad when you swap in the other hard drive, it's probably a hardware problem.  As I said, I'd also check the BIOS version and update the BIOS to latest available from Toshiba if that's an option.

---

### Post by Sijmen on 2012-08-20
Did a clean install of xubuntu 12.04. That didn't do much good.  There was a BIOS update which I applied and that made things better. It's running in the high 40's.
That shows something about the firmware of Toshiba. It doesn't show any temperature settings but underneath it does regulate the fan.

---

