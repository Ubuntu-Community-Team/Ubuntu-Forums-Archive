---
title: "Acer Aspire 5732ZG overheating"
date: 2013-05-23
forum: Hardware
---

### Post by Nightshadow931 on 2013-05-23
Hello everyone.

Few days ago I've installed Ubuntu 13.04 on my Acer Aspire 5732ZG.
Right after I finished installation and booted, my laptop turned off.It was due to high temp(105c)
I've never had such problems on windows 7, it's normal temp on 7 is 60-70c with firefox and winamp being used.

I've already tried to look for a solution, googled the problem and found out that I'm not the only one with it.
But there is no specific solution.I've tried to install TLP and configured it to save as much power as I can, but it didn't help.

So, what should I do ?
I think it's because of the wrong graphichs driver, can that be the problem ? I didn't install/uninstall any driver since I installed ubuntu though.

Thanks in advance,
Darko.

---

### Post by Mark Phelps on 2013-05-24
You can check in Additional Drivers to see if any are being offered, but if they aren't, there aren't any drivers you can install.

Overheating is a common problem in laptops because the recent Linux kernel versions do not provide the idling support that is already there in the MS Windows kernels; thus, the CPU runs faster in general, and gets hotter.

You can try using Jupiter to see if that helps:  [http://www.ubuntubuzz.com/2012/04/fix-laptop-overheating-problem-in.html]("http://www.ubuntubuzz.com/2012/04/fix-laptop-overheating-problem-in.html")

---

### Post by Nightshadow931 on 2013-05-25
There isn't anything in Additional Drivers.
Jupiter does not work on Ubuntu 13.04, it's discontinued project afaik, I've tried TLP as I said, but seems like it isn't helping at all.

---

### Post by 2F4U on 2013-05-25
Do you know which hardware component caused the high temperature? If not, lm-sensors might help to find it out:

[https://help.ubuntu.com/community/SensorInstallHowto](https://help.ubuntu.com/community/SensorInstallHowto)

Am I right in assuming that you already took the usual measures like checking that nothing blocks the fan, cleaning from dust inside the laptop?

---

### Post by Nightshadow931 on 2013-05-25
No, I don't exactly know that.
This is the output of the 'sensors' command.

> nightshadow@nightshadow-Aspire-5732Z:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +75.0°C  (crit = +110.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +72.0°C  (high = +105.0°C, crit = +105.0°C)
Core 1:       +75.0°C  (high = +105.0°C, crit = +105.0°C)

The temp is not high atm, as I turned my laptop on 20 mins ago.

---

### Post by 2F4U on 2013-05-25
From the output it seems as if sensors doesn't detect a sensor on the graphics card or that there is no seperate sensor on the graphics card. Are the fans working? You should be able to hear them if they do work. Do you have the latest BIOS installed?

---

### Post by Nightshadow931 on 2013-05-25
Yea, they are working I think.
I didn't clean them, but they are working completely fine with windows 7, so it should work on ubuntu too.
About BIOS, I've never updated it, I have the one that came with my computer, and I bought it around 3 years ago.
I've tried to search for newer version yesterday, but couldn't find abythng though.

[EDIT]
Actually, now when I've reached 92c, I think that fans are not working as they should.They should be a lot more loud than they are atm.

---

### Post by 2F4U on 2013-05-25
Unfortunately, this seems to be famous with quite a lot of Acer models. The problem seems to be that the fans are only properly controlled if Windows is installed. I've found a promising post here on the forum about how the problem might be solved:

[http://ubuntuforums.org/showthread.php?t=2141864](http://ubuntuforums.org/showthread.php?t=2141864)
[http://ubuntuforums.org/showthread.php?t=2010883](http://ubuntuforums.org/showthread.php?t=2010883)

---

### Post by Nightshadow931 on 2013-05-26
Seems like it's not compatible with my acer 5732zg.
Yesterday I found new BIOS for my laptop, and flashed it, but it didn't fix my problem at all.

---

### Post by 2F4U on 2013-05-26
Ubuntu with Unity is know to place quite some burden on the graphics card, which may be the reason for the overheating issue. Since the fans are at least working, it might be an option to use a different, more lightweight desktop environment such as those from Xubuntu or Lubuntu. These are, however, quite different from Unity.

---

### Post by Nightshadow931 on 2013-05-26
I don't think that is the problem.
I think that something is not working properly here.Ubuntu can't be that much power-hungry in idle state.Windows 7 must use more resources than Ubuntu.And on windows 7 I don't have this problem.
So, I'll keep searching for a solution, and if I don't find anything at the end, I will try kubuntu, although, I thought that KDE needs more power than GNOME.

Thanks for trying to help by the way!

---

### Post by mörgæs on 2013-05-27
> **Nightshadow931 said:**
> I don't think that is the problem.


It's better to test than assume. A good test is to install the Lubuntu desktop with the command 

```
sudo apt-get install lubuntu-desktop
```

which will give you the choice between Lubuntu and Ubuntu. 

Also cleaning the cooling unit is worth trying, even though it is not overheating in Windows.

---

### Post by Nightshadow931 on 2013-05-27
I've used KDE before with mandriva linux, now I wanted to try GNOME, and I've chosen ubuntu.
Alright, I will try Kubuntu then.But I'm limited with bandwidth on my laptop, so I can't download it from here.I will be home on my desktop computer on friday, so I will download the whole kubuntu system.Can't try it before moday though.

Thanks!

---

### Post by LU95 on 2013-05-31
Hi,  
 
I just wanted to confirm this since I have the exact same laptop model (Aspire 5732ZG). Kubuntu, Lubuntu and other variants didn't work for me either. I also tried various Debian distros to no avail; Every install ends in an overheating shutdown of the laptop.  The odd thing is, I can install and use Fedora & OpenSuse. 

And no, it's not dust in the cooling fans; I vacuum them regularly, so I know that's not an issue.
 
Going to try some different Bios next: V3.10 & V3.08 overheat.

---

### Post by LU95 on 2013-05-31
Bios V.3.04 overheats as well and shuts down.

---

### Post by LU95 on 2013-05-31
Bios V. 3.06 same thing. Any help would be appreciated; disabed the slideshow(Ubuntu) and did a text based install (Debian) both fail.

---

### Post by Yellow Pasque on 2013-06-01
> I think it's because of the wrong graphichs driver, can that be the problem?
Maybe you should at least tell us what GPU you have..
```
lspci | grep VGA
```

---

### Post by LU95 on 2013-06-02
The card is an ATI Mobility Radeon HD 4570.

---

### Post by Yellow Pasque on 2013-06-02
The open-source radeon driver is not good with power management on laptops. Try setting the power profile to low and see if it helps: [http://www.x.org/wiki/RadeonFeature#KMS_Power_Management_Options](http://www.x.org/wiki/RadeonFeature#KMS_Power_Management_Options)
Example:
```
echo "low" | sudo tee /sys/class/drm/card0/device/graphics/fb0/device/power_profile
```

Your other option is to use Ubuntu 12.04.1 and run the Catalyst Legacy driver.

---

### Post by LU95 on 2013-06-04
Thanks, I'll give it a shot next weekend.

---

### Post by Nightshadow931 on 2013-06-05
Kubuntu seems to be a bit better, if I'm using only ffox, cpu temp is 70-80c.
The command you provided, is it just an example, or should I use exactly the same command ?

Thanks for the help though!

---

### Post by LU95 on 2013-06-10
Couldn't get it to work reliably (under load) and being a laptop I use for work daily, I cant risk frying the gpu. ( Also, I couldn't find 12.04.01 only the later 12.04.02)

---

### Post by Yellow Pasque on 2013-06-10
[http://old-releases.ubuntu.com/releases/precise/](http://old-releases.ubuntu.com/releases/precise/)

---

