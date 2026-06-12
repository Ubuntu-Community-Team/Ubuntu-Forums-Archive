---
title: "Lenovo ThinkPad T410s does not boot after installing proprietary NVIDIA driver."
date: 2010-10-05
forum: Hardware
---

### Post by PhantamaroK on 2010-10-05
I have a new ThinkPad T410s with the NVIDIA graphics card.  I tried with Lucid, and after I installed the proprietary NVIDIA driver, it would boot to a blank screen with a blinking cursor.

I tried with the Maverick release candidate, and it boots to a command line.

Can anyone please help me figure out why installing this driver prevents the machine from booting?

---

### Post by P4man on 2010-10-06
This is one of those laptops with switchable graphics (it has both integrated video and an nvidia card), right?. I fear support for this under linux is not great yet.  But try this:
[http://www.ramoonus.nl/2010/08/linux-kernel-2-6-35-installation-guide-for-ubuntu-linux/](http://www.ramoonus.nl/2010/08/linux-kernel-2-6-35-installation-guide-for-ubuntu-linux/)

It installs a newer kernel which apparently has support for "VGA switcheroo".

---

### Post by PhantamaroK on 2010-10-12
Thanks for the tip P4man.  I do have a switchable graphics card.  I believe, though, that Maverick comes with the latest kernel (or at least now it does).

For what it's worth for the archives: it appears that I have 3D acceleration enabled without the NVIDIA proprietary driver.  I enabled the desktop effects, and although it says I need the NVIDIA driver, it goes through and the windows are wobbling.

It doesn't seem perfect, though (there's some lag).  I don't want to mess with the proprietary driver anymore, for fear of borking my system again.

---

### Post by phuxed on 2010-10-12
I have a newer Toshiba Satellite, and the same thing happened to me, after installing the NVIDIA proprietary driver, it just boots to the command line.

---

### Post by PhantamaroK on 2010-10-25
I know it's been a while, but I found something useful so I thought I'd post.

For the T410s, the switchable graphics can be configured in the BIOS.  I switched the setting to "Discrete Graphics", then installed the driver, and it rebooted and worked as expected.

I'm playing Yo Frankie! right now.

---

### Post by thehero on 2010-11-03
I just posted this in another thread ([http://ubuntuforums.org/showthread.php?t=1586292&highlight=t410s](http://ubuntuforums.org/showthread.php?t=1586292&highlight=t410s)) but I'll say it again for Lenovo Thinkpad T410s owners with Optimus technology that are having problems. 

If you have Nvidia Optimus and have installed the nvidia driver you don't need to reinstall to fix X.

If you want to use the Nvidia propretary driver go into your bios with supervisor/administrator level access. From here you can choose Optimus/Integrated/Discrete graphics. Choose discrete graphics to use the Nvidia card.

If you want to use the Intel integrated card to save batter life choose integrated.

Note: that if you installed the Nvidia proprietary driver the Intel driver will not load correctly and your screen will freeze before login.

To fix this boot into recovery mode from grub and start failsafe-X. Once X is started go to additional drivers under system > administration and uninstall the nvidia binary driver. You may have to remove the xorg.conf file as well. Move the file by typing "sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old". This will not delete the file but instead move it in case you want it later.

Now reboot and the Intel driver should be working again.

---

### Post by fhsm on 2010-11-22
> **thehero said:**
> I just posted this in another thread ([http://ubuntuforums.org/showthread.php?t=1586292&highlight=t410s](http://ubuntuforums.org/showthread.php?t=1586292&highlight=t410s)) but I'll say it again for Lenovo Thinkpad T410s owners with Optimus technology that are having problems. 

If you have Nvidia Optimus and have installed the nvidia driver you don't need to reinstall to fix X.

If you want to use the Nvidia propretary driver go into your bios with supervisor/administrator level access. From here you can choose Optimus/Integrated/Discrete graphics. Choose discrete graphics to use the Nvidia card.

If you want to use the Intel integrated card to save batter life choose integrated.

Note: that if you installed the Nvidia proprietary driver the Intel driver will not load correctly and your screen will freeze before login.

To fix this boot into recovery mode from grub and start failsafe-X. Once X is started go to additional drivers under system > administration and uninstall the nvidia binary driver. You may have to remove the xorg.conf file as well. Move the file by typing "sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old". This will not delete the file but instead move it in case you want it later.

Now reboot and the Intel driver should be working again.

@thehero
Thanks for this fix. I've just [started a thread]("http://ubuntuforums.org/showthread.php?p=10149968") reviewing the info I've been able to find on the T410s/Nvidia topic and asking a few questions about streamlining the switch from one GPU to the other. If you have anything to add I'd appreciate it.

---

### Post by FunnyLookinHat on 2011-01-24
This method didn't work for me...

I went in and set the graphics to "Discrete" and also Disabled the detection.  When I try to use the driver, however, it keeps complaining of "No screens found".

Ideas?

---

### Post by lekksi on 2011-05-11
> **FunnyLookinHat said:**
> This method didn't work for me...

I went in and set the graphics to "Discrete" and also Disabled the detection.  When I try to use the driver, however, it keeps complaining of "No screens found".

Ideas?

I had the same situation after changing the bios settings as you described.

I found the following in /var/log/Xorg.0.log
```

[    18.940] (EE) NVIDIA(0): The NVIDIA GPU at PCI:1:0:0 is not supported by the 173.14.30
[    18.940] (EE) NVIDIA(0):     NVIDIA driver.
[    18.940] (EE) NVIDIA(0): Failed to initialize the NVIDIA graphics device!
---
[    18.940] (EE) Screen(s) found, but none have a usable configuration.
[    18.940] 
Fatal server error:
[    18.940] no screens found
[    18.940] 
```Then, I removed all nvidia-173 packages (which I had installed for trying out older drivers) and reinstalled nvidia-current, ran nvidia-xconfig, rebooted and now everything works as it should.
My current nvidia driver version is 270.41.06.

---

