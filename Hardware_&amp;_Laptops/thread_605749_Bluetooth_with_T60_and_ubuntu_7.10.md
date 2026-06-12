---
title: "Bluetooth with T60 and ubuntu 7.10"
date: 2007-11-07
forum: Hardware &amp; Laptops
---

### Post by chineseollie on 2007-11-07
Hi everyone,

I am a new user of Ubuntu.

My laptop is Thinkpad T60 and my OS is Ubuntu 7.10. I have a problem while trying to set up a bluetooth connection with my laptop and my Nokia 6300 mobile phone.

Following the [BluetoothSetup]("https://help.ubuntu.com/community/BluetoothSetup"), I installed the gnome-bluetooth and launched it, then there is an icon in the system tray saying "ready for bluetooth transfer". However, I can't find my laptop while using my phone to search bluetooth devices.

I also tried to [COLOR="DimGray"]sudo hcitool dev[/COLOR], and the result contains nothing
[COLOR="DimGray"]zhanwu@xibot:/etc/init.d$ sudo hcitool dev
Devices:
zhanwu@xibot:/etc/init.d$ 
[/COLOR]

Well, as the "hcitool dev" command is to list the local devices, the result indicates that I have no bluetooth device in my laptop, am I right? How could it happens? The bluetooth works well under WindowsXP.

Then I tried [COLOR="DimGray"]hcitool scan[/COLOR], I got this:
[COLOR="DimGray"]zhanwu@xibot:/etc/init.d$ hcitool scan
Device is not available: No such device
zhanwu@xibot:/etc/init.d$ [/COLOR]

I am really confused, anyone could help me? Thank you in advance.

---

### Post by MeanderingCode on 2007-12-27
I wish i had a permanent and sleek solution to give you, but alas, i am searching as well.

I did find something, and posted it [here]("http://ubuntuforums.org/showpost.php?p=4026061&postcount=8"), though.

---

