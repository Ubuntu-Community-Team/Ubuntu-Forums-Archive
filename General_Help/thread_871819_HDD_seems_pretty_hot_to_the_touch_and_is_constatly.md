---
title: "HDD seems pretty hot to the touch and is constatly on..."
date: 2008-07-27
forum: General Help
---

### Post by PsychedelicWonders on 2008-07-27
Alright right now my computer has its screen saver on... the HDD seems to be running full speed and is quite warm... is thish normal?

And any time this machine is actually on... all of the fans on the case, the power supply, video card and processor will always be running right?

None of them ever shut off or sleep while the machine is on do they?

---

### Post by PsychedelicWonders on 2008-07-27
bump

---

### Post by mcduck on 2008-07-28
Yes, that's normal.

The fans are supposed to run all the time. This is not even controlled by the operating system, uusually they simply are connected to constant 12V from the power source and run as long time as the computer is on. In some cases you might have a setting in BIOS that allows the machine to adjust the fan speeds based on system temperatures, but even this only works if the fans are compatibele, and connected to the mothernard instead of directly to the PSU.

HDD's run at constant speed all the time they are powered on  (slower speed is not an option, for example a 7200rpm drive either runs at 7200rpm or not at all). It's possible to configure them to power off after some time with no disk activity, although this shouldn't make much difference on a desktop machine. They are designeed to run all the time, anyway. If the disk is hot you should make sure there's enough airflow around the disk to cool it.

---

### Post by cariboo on 2008-07-28
You can setup sensors to monitor your hardware, I monitor both cpu cores, fan speed and hard drive temps, I've got 4 hardrives installed.

There is a good howto located here:

[http://www.techthrob.com/tech/linuxsensors.php](http://www.techthrob.com/tech/linuxsensors.php)

Jim

---

### Post by PsychedelicWonders on 2008-07-28
Is there any benefit by powering down the HDD after a certain period of time with no disk activity?

Does it help keep the HDD cooler thereby keeping your files safer from burning itself up in some freak accident?

Does it cut back on any worth while electricity, in like an "energy saver" option?



Cari - is that an option that needs a separate piece of hardware to show you the temp... or is that a software mod?

I have an Origen AE VFD unit that may perhaps read all of that information for me... I'm not sure yet as I havent installed that part.

---

### Post by silkstone on 2008-07-28
It's a good idea to have a front-mounted fan blowing air over the drives - many cases are designed to accept either an 80mm or a 120mm fan. This should blow air into the case. Then have the normal exhaust fan on the back.

The drives should not get too warm when they are spinning but idle - they heat up when accessed. Also the power consumption is quite low, so there's little to be gained by using power management to turn them off on a desktop machine.

---

### Post by PsychedelicWonders on 2008-07-28
all 3 of my HDD are mounted in a cage that sits on a fan that blows directly on them... so i guess I'm good.

Hmm, I dont think they are beign accessed when I feel them... all I'm running right now is Ubuntu, no other programs or files are even on the comp, but they still seem pretty warm to the touch.

---

