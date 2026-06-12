---
title: "Acer Timeline 5810TG"
date: 2010-06-16
forum: Hardware
---

### Post by Robin Upton on 2010-06-16
I'm starting a thread specific to the Acer Aspire 5810TG (Ignore the misleading 5810T sticker on the screen). With a 15" screen and the HD4330 Radeon graphics, it's battery life is probably the shortest of any of the timelines. I got about 3 hours on a fresh install of 10.04. See [http://robinupton.com/computer/ubuntu/10.04/Increased%20Laptop%20Battery%20Life%20under%20Linux%20for%20Acer%20Aspire%205810TG.html]("http://robinupton.com/computer/ubuntu/10.04/Increased%20Laptop%20Battery%20Life%20under%20Linux%20for%20Acer%20Aspire%205810TG.html") for how I doubled battery life from 3 to 6 hours, including a script for toggling power settings.
 
How have other 5810TG users been faring? My power life is usually above 10W now that I've installed a bunch of stuff on it. Does the bigger screen draw noticeably more power, I wonder?

The main issue now is suspend. I haven't got hibernate working, and suspend works but the laptop uses unaccountably more power when it resumes. Re enabling the lenovo_acpi with 'sudo rmmod lenovo_acpi' and 'sudo modprobe lenovo_acpi' module helps, but power consumption is still about 3W higher than just after a reboot.

I run the laptop on mains most of the time at the moment, so the battery is almost always fully charged. This is convenient, but not best for battery lifetime. However, Li-Ion batteries don't decay that much at room temperature. So when the laptop was only drawing 10W, this was fair enough. When the laptop is more like 13W, one part of the battery gets warm to the touch, which means it'll be losing capacity and the whole battery will fail that much sooner as a result.

---

### Post by Robin Upton on 2010-07-25
I just got suspend sorted by installing the "pm-utils" package which gives a hook to do just this:
[FONT=Courier New]
sudo apt-get install pm-utils
echo SUSPEND_MODULES=\"lenovo_acpi\" | sudo tee -a /etc/pm/config.d/modules > /dev/null[/FONT]

I also found a script to horizontal 2-finger scrolling on the touchpad:
[FONT=Courier New]
#!/bin/sh
# Set up the touch pad of Acer Aspire 5810TG Under Linux
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Two-Finger Scrolling" 8 1
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Scrolling" 8 1 1
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Pressure" 32 10
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Width" 32 8
[/FONT]

---

### Post by westmerch on 2010-07-30
Hi Robin,

Thank you for posting on your findings on the timeline 5810tg. Im using one as well, and just Im just astonished by ubuntu 10.04. 

Im looking for information for the power management as well, looks like you were able to get a 6.5 hrs battery. 

Im not good at all with linux, ubuntu, nor coding (pasting stuff...), but willing to learn. :D

I really need that 6.5 hrs battery, if you can help.

 From what I understood from this file: 

[http://robinupton.com/computer/ubuntu/10.04/Acer-Timeline-5810TG-powersave-ubuntu-lucid.bash](http://robinupton.com/computer/ubuntu/10.04/Acer-Timeline-5810TG-powersave-ubuntu-lucid.bash)

I need to paste it somewhere? .bash_profile...? I cant locate this file... 

can you give a hint?

I will be following you posting for anything you find on the Acer timeline 5810tg with ubuntu 10.04

Thanks for your help.

West,

---

### Post by Robin Upton on 2010-08-24
The file ([http://robinupton.com/computer/ubuntu/10.04/Acer-Timeline-5810TG-powersave-ubuntu-lucid.bash](http://robinupton.com/computer/ubuntu/10.04/Acer-Timeline-5810TG-powersave-ubuntu-lucid.bash)) is a script which instructs the computer to switch a load of things to low power mode. To run it, you need to save it to a file somewhere handy. I have a folder from my home directory for such scripts. You can make one with the following:
```

mkdir ~/scripts
```It doesn't much matter what you call it, so let's call it "powersave.bash":

```
gedit ~/scripts/powersave.bash
```Cut and paste that script into the editor and save it. Then you can try to run it by typing:

```
~/scripts/powersave.bash
```If you do this straight away, you'll likely get a "Permission denied" error, because you need to instruct the computer that this is an executable script. To do that:

```
chmod u+x ~/scripts/powersave.bash
```This may give a warning or two, if your system is differently set up than mine, but that's no big deal. You should hear a click as it activates audio powersaving. The main thing is to test whether it makes a difference to the power consumption (check by running "sudo powertop"). If it does, you can get max battery life by running it as follows:

```
~/scripts/powersave.bash -battery
```I mainly use it without an argument, to get  maximum battery life if it's on battery, maximum performance if its on mains power.

```
~/scripts/powersave.bash
```

---

### Post by rds37 on 2012-07-02
Hi Robin,

Thanks for the information! I have an Acer Timeline 5810TG too, but I'm running ubuntu 12.04 and unfortunately the power saving scripts don't seem to work for me. I was wondering if you've since upgraded to 12.04 and managed to get any power saving to work?

Thanks,

Rajen

---

