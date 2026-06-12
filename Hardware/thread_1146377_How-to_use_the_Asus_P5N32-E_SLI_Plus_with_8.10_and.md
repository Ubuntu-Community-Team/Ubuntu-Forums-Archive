---
title: "How-to use the Asus P5N32-E SLI Plus with 8.10 and 9.04"
date: 2009-05-02
forum: Hardware
---

### Post by Caedis on 2009-05-02
If you don&#8217;t have my exact setup some of these hacks/tweaks may help if implemented properly.

**My Specs:**
[LIST]
[*]OS: Ubuntu 8.10 &#8220;Intrepid&#8221; or Ubuntu 9.04 "Jaunty"
[*]Motherboard: Asus P5N32-E SLI Plus
[*]GPU: Nvidia GTX 250 / Nvidia 9800GTX+
[*]CPU: Intel E6600 LGA775
[*]RAM: 2 GB Gskill DRR2 800
[/LIST]

I realize this isn&#8217;t a top end gaming rig, but after I chose to sell my old gaming rig a few years ago to pay for my wife&#8217;s engagement ring I was left with nothing to work with. I needed a place to start and get my foot back in the door to high performance OCing and gaming, only this time I&#8217;m determined to go totally Open Source with Ubuntu Linux as my weapon of choice. I procured this setup for about 200$ from some long time friends. Many more parts were thrown in but they are not pertinent to the scope of this how to.

[LIST]
[*][COLOR="DarkRed"]**Problem**[/COLOR]: When installing with the standard desktop edition I was unable to boot into the graphical environment on the live cd.
[*][COLOR="Blue"]**Solution**[/COLOR]: I fixed this by downloading the alternate install disk which installs from the command line.
[/LIST]

[LIST]
[*][COLOR="DarkRed"]**Problem**[/COLOR]: GDM (Gnome Desktop Manager, AKA graphical environment) would not start. The monitor flickered sporadically and nothing happened.
[*][COLOR="Blue"]**Solution**[/COLOR]: Compile the latest drivers from Nvidia for maximum performance
[/LIST]
Press [Ctrl] +[Alt] + F6 through F8 (whichever gets you to a login prompt on the command line)

Login to the command line with your regular credentials.

On a separate computer with Internet access go to the Nvidia website and download the appropriate drivers for your Linux build.

Drop them on a flash drive.

Mount the flash drive on your command line only box:

```
sudo mkdir /media/usb
sudo mount /dev/sdb /media/usb  (sometimes it's labeled sdb1, so if sdb doesn't seem to work use sdb1)
cd /media/usb
sudo killall gdm (this kills X and GDM so the nvidia drivers can be compiled and installed without conflicts)
sudo sh NVIDIA-Linux-x86_64-180.44-pkg2.run
```

Follow the prompts and your done.

Reboot

```
sudo shutdown -r now
```

[LIST]
[*][COLOR="DarkRed"]**Problem**[/COLOR]: Networking is not working
[*][COLOR="Blue"]**Solution**[/COLOR]: Force the networking stack into compliance with the nVidia MCP55
[/LIST]

Open a terminal

```
sudo su
rmmod forcedeth
modprobe forcedeth msi=0 msix=0
/etc/init.d/networking restart
```

Now we want to make these changes permanent as this hack resets when the computer reboots.

```
sudo su
cd /etc/modprobe.d/
nano options
```

Add the following to the end of the file
```

#nVIDIA Corporation MCP55 Ethernet
options forcedeth msi=0 msix=0
```

Save the change to the options file

Now the boot image must be rebuilt

```
update-initramfs -u
```

After all that you should be running perfectly with no performance hang ups.

This setup has proven to be the most problematic I have ever dealt with. Most of the computers I&#8217;ve built with Ubuntu work out of the box with no hacking or tweaking, I just happened to get the least compliant of every version. Oh well, nothing a little command line wizardry can&#8217;t fix. I expect to be playing Left 4 Dead, Oblivion, Spore and even Crysis shortly.

[CENTER][SIZE="4"][This guide was from my blog at Caedis.net]("http://caedis.net/2009/04/17/linux-gaming-rig-first-aid/")[/SIZE][/CENTER]

---

### Post by Gravity on 2009-08-18
Thank you, the networking guide was just what I needed! :D

---

