---
title: "Lenovo U460 screen brightness"
date: 2010-11-20
forum: Hardware
---

### Post by chairmanK on 2010-11-20
I have a Lenovo U460 laptop running Ubuntu 10.10. During normal use, the brightness of the screen will suddenly start fluctuating rapidly up and down for up to 30 seconds at a time. This occurs once every few minutes, and it happens in a wide range of ambient light levels. During this time, the screen brightness indicator will appear in the upper right corner of the screen and the indicator bar will flicker back and forth as the brightness changes. While this is happening, the Fn- hotkeys that control brightness have no effect as if they are being interrupted/ignored. When this spontaneous brightness fluctuation is not happening, however, I can control the brightness with the hotkeys as expected. 

I can also use gnome-power-preferences (Preferences > Power Management) to change brightness. Strangely, gnome-power-preferences seems to set the screen brightness but does not get the current value. When started, it shows a value for "Set display brightness to:" that does not match the actual screen brightness, and when the screen brightness changes (either due to this spontaneous flickering bug or when I press the hotkeys), the value shown is not updated. Setting the screen brightness using gnome-power-preferences does not stop the screen brightness from fluctuating later.

I want to stop the spontaneous fluctuation of screen brightness. I suspect that it might have something to do with the ambient light sensor, but I can't find where the ambient light sensor is located on the laptop; if I did, I would try shining a flashlight on it or blocking it to see if this changes the screen brightness. I also don't know if the ambient light sensor is enabled at a software level in Ubuntu Linux, and if so, where I could disable it completely.

```

$ uname -a
Linux alice 2.6.35-23-generic #40-Ubuntu SMP Wed Nov 17 22:14:33 UTC 2010 x86_64 GNU/Linux

```

---

### Post by Wise Shtashi on 2010-12-01
Hey, I have the same problem (with the same laptop and OS version) I was wondering if you have found a solution at all?

---

### Post by chairmanK on 2010-12-04
I haven't found a solution. Disabling ACPI (boot with acpi=off) eliminates the problem but has obvious downsides (overheating, short battery life) and also cripples wireless networking. Honestly I would happy with just knowing where the ambient light sensor is located so that I can open the computer and rewire it so that it does nothing.

---

### Post by Wise Shtashi on 2010-12-07
Externally - it is on the touch sensitive strip second little hole from the left. I have put an Ubutnu sticker over it for the moment and it seems better.

Page 2 [http://consumersupport.lenovo.com/us/en/UserGuide/Guide_show_1274506572472.html](http://consumersupport.lenovo.com/us/en/UserGuide/Guide_show_1274506572472.html)

Internally - I have no idea sorry.

---

### Post by chairmanK on 2011-01-09
Thanks for the tip. For my computer, covering the light sensor does not solve the problem, but at least I know where it is so that I can test.

> **Wise Shtashi said:**
> Externally - it is on the touch sensitive strip second little hole from the left. I have put an Ubutnu sticker over it for the moment and it seems better.

Page 2 [http://consumersupport.lenovo.com/us/en/UserGuide/Guide_show_1274506572472.html](http://consumersupport.lenovo.com/us/en/UserGuide/Guide_show_1274506572472.html)

Internally - I have no idea sorry.

---

### Post by fgmart on 2011-02-19
From the instruction manual, the light sensor is #8 here:

[http://yfrog.com/h345608825p](http://yfrog.com/h345608825p)

It's pretty easy to solve just by putting a sticker over the sensor.  Then the laptop thinks it's in the dark.  When you first put the sticker on, the brightness will come way down, but you can just manually jog it up, and then it will stay there.

[http://yfrog.com/gzzc3dbj](http://yfrog.com/gzzc3dbj)

Sometimes a hardware solution is better :)  (PS I am looking for a new sticker....)

---

### Post by kneekahliss on 2011-02-25
I have the lenovo u460 with ubuntu 10.10 (updated completely)

I experience this rarely. Although today 3 times, only 1 time before. It last only 5-10 seconds. It only happens while plugged into AC and unplugging replugging fixes it immediately.

on a side note this laptop has intel/nvidia gfx cards
Id assume im using nvidia bcz lsmod lists that...
Is there a way to determine which im actually using? 
Also have you guys got the HDMI port to work?

> Linux silvertop 2.6.35-25-generic-pae #44-Ubuntu SMP Fri Jan 21 19:01:46 UTC 2011 i686 GNU/Linux


> update: it happens all the time now, click the power top right sometimes stops it. dammit.

---

### Post by artemyk on 2011-06-19
I was able to fix this by booting into Windows and using the Lenovo power management settings to disable the ambient light sensor (directions at [http://forums.lenovo.com/t5/IdeaPad-Y-and-U-series-Laptops/Y560-Disable-Auto-Adjust-Screen-Brightness-ambient-light-sensor/ta-p/270494](http://forums.lenovo.com/t5/IdeaPad-Y-and-U-series-Laptops/Y560-Disable-Auto-Adjust-Screen-Brightness-ambient-light-sensor/ta-p/270494) ).  

Not sure how to do this in Ubuntu.

---

