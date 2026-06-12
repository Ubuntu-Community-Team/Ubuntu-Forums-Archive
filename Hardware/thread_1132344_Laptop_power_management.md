---
title: "Laptop power management?"
date: 2009-04-21
forum: Hardware
---

### Post by Noise... on 2009-04-21
After installing Ubuntu and using it for a couple weeks now, my only real issue is the power consumption.

My notebook is constantly running VERY hot, and there's no way I can switch to a "power saver" mode to fix that. 

Normally in Windows I would switch to 15-25% CPU power, lower screen brightness, and various other power tweaks to conserve power (I live off-grid, so the less power usage the better), and to keep the laptop cooler when I'm just web browsing.

In Ubuntu, this isn't really possible. The other day I was in town all day, and due to this heavy power usage, I only got about an hour and a half battery time, compared to the 5.5 hours I would get with a custom "power saver" plan in Windows.

What are my options for power management? I installed Kpowersave, but it's disappointing, as it lacks power plan customization, and it's power saver plan is still very power-intense, only cutting the CPU to 50%.

Any suggestions?

---

### Post by lisati on 2009-04-21
I'm assuming you're using the Gnome desktop that comes as "standard" with regular Ubuntu:
Have a look at the System->Preferences->Power management menu

---

### Post by Noise... on 2009-04-21
> **lisati said:**
> I'm assuming you're using the Gnome desktop that comes as "standard" with regular Ubuntu:
Have a look at the System->Preferences->Power management menu

I've checked it. I have everything set to the minimum, and my battery life was still horrendous.

---

### Post by tidris on 2009-04-21
Have you tried using the CPU Frequency Scaling Monitor applet under GNOME? It allows you to select among several CPU frequency management profiles. On my computer it shows Conservative, Ondemand, Performance, and Powersave.

---

### Post by Noise... on 2009-04-21
> **tidris said:**
> Have you tried using the CPU Frequency Scaling Monitor applet under GNOME? It allows you to select among several CPU frequency management profiles. On my computer it shows Conservative, Ondemand, Performance, and Powersave.

I just added those, and I'm not getting a menu to change the setting?

Does that mean that the kernel I'm using doesn't support it? It just says it's "ondemand" and is going between 50 and 100%.

Could Kpowermanager be interfering? It's not running at the moment, but I'm not sure if it alters power settings by being installed?

---

### Post by tidris on 2009-04-21
Well when I click on the applet's icon I do get a menu that allows me to choose a profile. It also shows me the 5 different CPU frequencies my laptop supports and I can choose one of them instead of a profile. The profiles do automatic frequency adjustments based on workload and such. I am running intrepid 8.10, maybe that makes a difference.

---

### Post by eldragon on 2009-04-22
check this thread, even if its for some dell notebook, its quite useful.

[http://ubuntuforums.org/showthread.php?t=847773](http://ubuntuforums.org/showthread.php?t=847773)

---

