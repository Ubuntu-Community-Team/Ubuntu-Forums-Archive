---
title: "[HELP!] nVidia 8500GS + Ubuntu 8.04"
date: 2008-07-20
forum: Hardware
---

### Post by ksaul on 2008-07-20
I have a nvidia 8500gs graphics card in my laptop which I am running Ubuntu 8.04, but for the hell of me I cannot get the driver to install correctly.

If i install the driver within the Ubuntu GUI, and I reboot, the screen goes all white.

I can fix the problem by opening the kernel and editing xorg.conf file changing "nvidia" to "nv", but that doesn't fix the problem of not having a video driver.

What do I have to do to get the driver working properly??:confused:

---

### Post by Skripka on 2008-07-20
> **ksaul said:**
> I have a nvidia 8500gs graphics card in my laptop which I am running Ubuntu 8.04, but for the hell of me I cannot get the driver to install correctly.

If i install the driver within the Ubuntu GUI, and I reboot, the screen goes all white.

I can fix the problem by opening the kernel and editing xorg.conf file changing "nvidia" to "nv", but that doesn't fix the problem of not having a video driver.

What do I have to do to get the driver working properly??:confused:

Slow down, how did you get (download) the driver?



With Synaptic/Adept you can get the drivers off the repos, and activate the driver through a hardware manager..  I'm running an 8500GT right now, that was that quick and that easy (with the "New" Nvidia driver).

---

### Post by ksaul on 2008-07-21
> **Skripka said:**
> Slow down, how did you get (download) the driver?



With Synaptic/Adept you can get the drivers off the repos, and activate the driver through a hardware manager..  I'm running an 8500GT right now, that was that quick and that easy (with the "New" Nvidia driver).

When I go to effects for ubuntu, it asked for me to install the nvidia accelerated graphics driver, so i click yes and it installs the driver, then i reboot and the white screen appears.

---

### Post by ksaul on 2008-07-21
anyone..??

---

### Post by Trueno22 on 2008-07-21
ok first which are you installing nvidia-glx or nvidia-glx-new?

You would need nvidia-glx-new.  If you have the GLX alone version do this:

> sudo apt-get purge nvidia-glx

then do this

> sudo apt-get install nvidia-glx-new

sudo nvidia-xconfig

after that just restart x.

---

### Post by ksaul on 2008-07-23
> **Trueno22 said:**
> ok first which are you installing nvidia-glx or nvidia-glx-new?

You would need nvidia-glx-new.  If you have the GLX alone version do this:



then do this



after that just restart x.

> 
ksaul@ksaul-laptopubuntu:~$ sudo apt-get purge nvidia-glx
[sudo] password for ksaul: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package nvidia-glx is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libxvidcore4 mplayer-skins libsvga1 libmono-cairo2.0-cil libx264-57 libenca0
  libggi2 libgii1 libgii1-target-x liblame0 libfaac0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ksaul@ksaul-laptopubuntu:~$ sudo apt-get install nvidia-glx-new
Reading package lists... Done
Building dependency tree       
Reading state information... Done
nvidia-glx-new is already the newest version.
The following packages were automatically installed and are no longer required:
  libxvidcore4 mplayer-skins libsvga1 libmono-cairo2.0-cil libx264-57 libenca0
  libggi2 libgii1 libgii1-target-x liblame0 libfaac0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ksaul@ksaul-laptopubuntu:~$ sudo nvidia-xconfig

Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Configured Video Device" must have a Driver
                  line.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'


is this what is supposed to happen..?

---

### Post by ksaul on 2008-07-23
I rebooted, and the same problem, a white screen...

I did "sudo dpkg-reconfigure -phigh xserver-xorg" and reboot and i was able to see again..

whats the problem here?///

---

### Post by ksaul on 2008-07-28
still having a problem with this, I cant figure this out :confused:

---

### Post by falcon61102 on 2008-07-28
Ooops... didn't read the entire post...

Try installing nvidia-settings

```
sudo apt-get install nvidia-settings
```

Then run it:
```
 sudo nvidia-settings
```

When it runs, select the settings  you want and then make sure you save X config file, you'll see the button on one of the tabs.

---

### Post by hotweiss on 2008-07-28
> **ksaul said:**
> still having a problem with this, I cant figure this out :confused:

1. sudo apt-get remove nvidia* (will also remove any other restricted modules (e.g.-madwifi), so watch out)
2. sudo apt-get install envyng-gtk
3. enable the proposed repositories
4. sudo apt-get update
5. sudo envyng -g
6. Select Nvidia on the left side, now click on Install the Nvidia driver (Manual Selection of the Driver), select 173, and finally click Apply.
7. Once the installation is completed, reboot and you will once again have a crisp screen.

---

### Post by ksaul on 2008-08-03
> **hotweiss said:**
> 1. sudo apt-get remove nvidia* (will also remove any other restricted modules (e.g.-madwifi), so watch out)
2. sudo apt-get install envyng-gtk
3. enable the proposed repositories
4. sudo apt-get update
5. sudo envyng -g
6. Select Nvidia on the left side, now click on Install the Nvidia driver (Manual Selection of the Driver), select 173, and finally click Apply.
7. Once the installation is completed, reboot and you will once again have a crisp screen.

im new to ubuntu, what are repositories?

also i dont have an option for 173, only
 - 169.12
 - 96.43.05
 - 71.86.04

---

### Post by Xan63 on 2008-08-17
>  Originally Posted by ksaul  View Post
I have a nvidia 8500gs graphics card in my laptop which I am running Ubuntu 8.04, but for the hell of me I cannot get the driver to install correctly.

If i install the driver within the Ubuntu GUI, and I reboot, the screen goes all white.

Hi,

I got the same white screen problem with my Geforce 8600GT, and I managed to solve this issue with removing compiz fusion and its associated packages. I am now running with Nvidia drivers installed with Envy (173.14.12 version)

I don't have yet tried to reinstall compiz, so I can't tell if it will work with Compiz-fusion; and I have  still another issue: i can't access to nvidia-settings.

Hope it can help,

Xan

---

