---
title: "nVidia resolution super low after update"
date: 2016-11-18
forum: Hardware
---

### Post by PenguinLust on 2016-11-18
I did a (dist-)upgrade which lower my resolution. So following advice, I then did
> sudo apt-get install --reinstall nvidia-367 nvidia-opencl-icd-367
That's made everything worse, and now my resolution is capped at 640x480. Unfortunately, this resolution also makes it difficult to research anything. What should I do?

I have Ubuntu 16.04 64-bit running a GeForce GTX 750 Ti. Whether I'm running nVidia's 367.57, 340.98 or the open source driver (through "Additional Drivers") their all just as bad. If I run NIVIDIA X Server Settings, it confirms that the maximum resolution is 640.

---

### Post by PenguinLust on 2016-11-20
If I could do it w/> sudo dpkg-reconfigure xserver-xorgI would, but doing that didn't do any good.

---

### Post by Bashing-om on 2016-11-20
PenguinLust; Hello;

Did you purge old drivers prior to installing nvidia-367 ?
Let's look at what is installed presently:
```

sudo lshw -C display
dpkg -l | grep -i nvidia

```
as there can be only one driver installed - 

[INDENT][INDENT]else:
[INDENT][INDENT][INDENT]there be a conflict of interest
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by PenguinLust on 2016-11-20
I dunno, I've really pooched it now! I followed some directions to start in runlevel 3, but it failed so now when I start my system, the res is even lower, and every time I login, it boots me out again to the login screen. So now I need to know how to reset whatever that is.

---

### Post by Bashing-om on 2016-11-20
PenguinLust; Well ..

process of learning :)

How far can you get into logging into the system ?
Can you get to the login screen, and key combo ctl+alt+F1 to gain a console interface ?

Login at the console with your credentials - username and password . there will be no response to the screen when pass word is entered. Just type your password blindly and hit the enter key .

If you can get the console active we continue from there.
Else we get a terminal in some other way.

[INDENT][INDENT]'buntu
[INDENT][INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by PenguinLust on 2016-11-20
Oh, I can get into the console alright. But I had to start my laptop to tell you all about it.

---

### Post by Bashing-om on 2016-11-20
PenguinLust; K

as you are at the console, you do not have the amenities of a terminal emulator to copy paste the output of commands.
How about we install a tool that will transfer files ?
```

sudo apt update
sudo apt upgrade
sudo apt install pastebinit

```

now we can do the transfers:
```

pastebinit /var/log/Xorg.0.log
pastebinit <( apt list nvidia* | grep installed )
sudo lshw -C display | pastebinit

```
The results of the pastebinit commands will be URLs back in the terminal, pass these links back here and we can then access the files.

We then have an idea of what is going on in the GUI and what the graphic's situation is like .

[INDENT][INDENT]we can do that
[/INDENT][/INDENT]

---

### Post by PenguinLust on 2016-11-21
Ok, so we got:
[http://paste.ubuntu.com/23510225](http://paste.ubuntu.com/23510225)
[http://paste.ubuntu.com/23510226](http://paste.ubuntu.com/23510226)
[http://paste.ubuntu.com/23510231](http://paste.ubuntu.com/23510231)

---

### Post by Bashing-om on 2016-11-21
PenguinLust; Well, well ...


Is there a reason that you boot up with the "text' boot parameter ? Not that it is of great import, just as added info for troubleshooting .

As we have :
Log file says :
> 
43.350] (II) NVIDIA GLX Module  375.20  Tue Nov 15 16:38:52 PST 2016

But system do say:
> 
nvidia-367


Let's try and purge all and install the 375 version driver. per:
[http://www.nvidia.com/download/driverResults.aspx/111596/en-us](http://www.nvidia.com/download/driverResults.aspx/111596/en-us)


Are you working from this PPA for drivers ?
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)

[INDENT][INDENT]get the system on the same page
[/INDENT][/INDENT]

---

### Post by PenguinLust on 2016-11-21
> **Bashing-om said:**
> PenguinLust; Well, well ...


Is there a reason that you boot up with the "text' boot parameter ? Not that it is of great import, just as added info for troubleshooting .
I did mention that I was trying to start at runlevel 3. This was supposed to be part of that.

> 
As we have :
Log file says :

But system do say:

What I didn't say it that I was trying to install nVidia's then-2-day-old driver. Since it expressly failed, I assumed it had no effect.

> 
Let's try and purge all and install the 375 version driver. per:
[http://www.nvidia.com/download/driverResults.aspx/111596/en-us](http://www.nvidia.com/download/driverResults.aspx/111596/en-us)

Ok, what's the reliable way of doing it, since the failed installation rollback didn't work?

> 
Are you working from this PPA for drivers ?
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)


I'm pretty sure I am. I was just going w/the "Additional Drivers" applet. I think that's PPA. How can I tell?

---

### Post by Yellow Pasque on 2016-11-21
If you tried to install Nvidia's driver from the downloaded .run file, the uninstall procedure is:
```
sudo ./Nvidiablahblah.run --uninstall
```
Of course, now that you've installed/uninstalled other Nvidia packages, there's no telling how well that will work.

> I'm pretty sure I am. I was just going w/the "Additional Drivers" applet. I think that's PPA. How can I tell? 
It's not the same thing. The "drivers" app just scans your hardware and suggests packages in the default repositories. The PPA adds newer versions of available packages.

Can you show output of:
```
cat /etc/modprobe.d/* | grep nouv
ls /etc/modprobe.d/
```

---

### Post by Yellow Pasque on 2016-11-21
Until you get your driver situation straightened out, you may want to make an /etc/X11/xorg.conf like this:
```
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "vesa"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection
```

The "vesa" driver should allow 1280x1024, whereas the current driver X is falling back to (fbdev) defaults to 640x480.

---

### Post by Bashing-om on 2016-11-21
PenguinLust; Hey ;

In addition to Temüjin's most worthy input, I would also like to see if our trusted PPA source is on your system;
what returns:
```

tail -v -n +1 /etc/apt/sources.list.d/*
sudo find / -name "NVIDIA-Linux-*"

```

We get your system cleaned up .. and then decide on what you want to do .

FYI, I too run a new generation nVidia card . As there is no open source driver available in 14.04 for this card, I too run with the vesa driver. It performs wonderfully for my use case . Far superior to my old card and driver.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by PenguinLust on 2016-11-21
Ok, so now that I uninstalled the nVidia script-installed driver, my resolution is back to its old unacceptably low, but functional resolution. Now I can log in again.
Here's that tail of the sources you wanted:
> ==> /etc/apt/sources.list.d/dropbox.list <==
# deb [arch=i386,amd64] [http://linux.dropbox.com/ubuntu](http://linux.dropbox.com/ubuntu) xenial main # disabled on upgrade to xenial

==> /etc/apt/sources.list.d/dropbox.list.distUpgrade <==
deb [arch=i386,amd64] [http://linux.dropbox.com/ubuntu](http://linux.dropbox.com/ubuntu) trusty main

==> /etc/apt/sources.list.d/dropbox.list.save <==
deb [arch=i386,amd64] [http://linux.dropbox.com/ubuntu](http://linux.dropbox.com/ubuntu) trusty main

==> /etc/apt/sources.list.d/inameiname-stable-trusty.list <==
# deb [http://ppa.launchpad.net/inameiname/stable/ubuntu](http://ppa.launchpad.net/inameiname/stable/ubuntu) xenial main # disabled on upgrade to xenial
# deb-src [http://ppa.launchpad.net/inameiname/stable/ubuntu](http://ppa.launchpad.net/inameiname/stable/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/inameiname/stable/ubuntu](http://ppa.launchpad.net/inameiname/stable/ubuntu) trusty main

==> /etc/apt/sources.list.d/inameiname-stable-trusty.list.distUpgrade <==
deb [http://ppa.launchpad.net/inameiname/stable/ubuntu](http://ppa.launchpad.net/inameiname/stable/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/inameiname/stable/ubuntu](http://ppa.launchpad.net/inameiname/stable/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/inameiname/stable/ubuntu](http://ppa.launchpad.net/inameiname/stable/ubuntu) trusty main

==> /etc/apt/sources.list.d/inameiname-stable-trusty.list.save <==
deb [http://ppa.launchpad.net/inameiname/stable/ubuntu](http://ppa.launchpad.net/inameiname/stable/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/inameiname/stable/ubuntu](http://ppa.launchpad.net/inameiname/stable/ubuntu) trusty main

==> /etc/apt/sources.list.d/mc3man-gstffmpeg-keep-trusty.list <==
# deb [http://ppa.launchpad.net/mc3man/gstffmpeg-keep/ubuntu](http://ppa.launchpad.net/mc3man/gstffmpeg-keep/ubuntu) xenial main # disabled on upgrade to xenial
# deb-src [http://ppa.launchpad.net/mc3man/gstffmpeg-keep/ubuntu](http://ppa.launchpad.net/mc3man/gstffmpeg-keep/ubuntu) trusty main

==> /etc/apt/sources.list.d/mc3man-gstffmpeg-keep-trusty.list.distUpgrade <==
deb [http://ppa.launchpad.net/mc3man/gstffmpeg-keep/ubuntu](http://ppa.launchpad.net/mc3man/gstffmpeg-keep/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/mc3man/gstffmpeg-keep/ubuntu](http://ppa.launchpad.net/mc3man/gstffmpeg-keep/ubuntu) trusty main

==> /etc/apt/sources.list.d/mc3man-gstffmpeg-keep-trusty.list.save <==
deb [http://ppa.launchpad.net/mc3man/gstffmpeg-keep/ubuntu](http://ppa.launchpad.net/mc3man/gstffmpeg-keep/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/mc3man/gstffmpeg-keep/ubuntu](http://ppa.launchpad.net/mc3man/gstffmpeg-keep/ubuntu) trusty main

==> /etc/apt/sources.list.d/steam.list <==
# deb [arch=amd64,i386] [http://repo.steampowered.com/steam/](http://repo.steampowered.com/steam/) precise steam # disabled on upgrade to xenial
# deb-src [arch=amd64,i386] [http://repo.steampowered.com/steam/](http://repo.steampowered.com/steam/) precise steam # disabled on upgrade to xenial

==> /etc/apt/sources.list.d/steam.list.distUpgrade <==
deb [arch=amd64,i386] [http://repo.steampowered.com/steam/](http://repo.steampowered.com/steam/) precise steam
deb-src [arch=amd64,i386] [http://repo.steampowered.com/steam/](http://repo.steampowered.com/steam/) precise steam

==> /etc/apt/sources.list.d/steam.list.save <==
deb [arch=amd64,i386] [http://repo.steampowered.com/steam/](http://repo.steampowered.com/steam/) precise steam
deb-src [arch=amd64,i386] [http://repo.steampowered.com/steam/](http://repo.steampowered.com/steam/) precise steam

==> /etc/apt/sources.list.d/team-xbmc-ppa-trusty.list <==
# deb [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) xenial main # disabled on upgrade to xenial
# deb-src [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) trusty main

==> /etc/apt/sources.list.d/team-xbmc-ppa-trusty.list.distUpgrade <==
deb [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) trusty main

==> /etc/apt/sources.list.d/team-xbmc-ppa-trusty.list.save <==
deb [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) trusty main

==> /etc/apt/sources.list.d/ubuntu-wine-ppa-trusty.list <==
# deb [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) xenial main # disabled on upgrade to xenial
# deb-src [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) trusty main

==> /etc/apt/sources.list.d/ubuntu-wine-ppa-trusty.list.distUpgrade <==
deb [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) trusty main

==> /etc/apt/sources.list.d/ubuntu-wine-ppa-trusty.list.save <==
deb [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) trusty main

==> /etc/apt/sources.list.d/xenial-partner.list <==
# channel for the xenial (16.04) partner channel
# 
#:description:This channel contains the partner software for xenial
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner
and I don't have any nVidia driver install scripts, except the one I used already.

And, to answer your question from yesterday:
> ~$ sudo lshw -C display
  *-display               
       description: VGA compatible controller
       product: GM107 [GeForce GTX 750 Ti]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:34 memory:fd000000-fdffffff memory:d0000000-dfffffff memory:ce000000-cfffffff ioport:dc00(size=128) memory:fe980000-fe9fffff

and
> ~$ dpkg -l | grep -i nvidia
ii  bbswitch-dkms                                        0.8-3ubuntu1                                  amd64        Interface for toggling the power on NVIDIA Optimus video cards
rc  libcuda1-331-updates                                 331.113-0ubuntu0.0.4                          amd64        NVIDIA CUDA runtime library
ii  libcuda1-367                                         367.57-0ubuntu0.16.04.1                       amd64        NVIDIA CUDA runtime library
rc  nvidia-331                                           340.96-0ubuntu0.14.04.1                       amd64        Transitional package for nvidia-331
rc  nvidia-331-updates                                   331.113-0ubuntu0.0.4                          amd64        NVIDIA binary driver - version 331.113
rc  nvidia-340                                           340.98-0ubuntu0.16.04.1                       amd64        NVIDIA binary driver - version 340.98
rc  nvidia-361                                           367.57-0ubuntu0.16.04.1                       amd64        Transitional package for nvidia-367
ii  nvidia-367                                           367.57-0ubuntu0.16.04.1                       amd64        NVIDIA binary driver - version 367.57
rc  nvidia-libopencl1-331-updates                        331.113-0ubuntu0.0.4                          amd64        NVIDIA OpenCL Driver and ICD Loader library
rc  nvidia-opencl-icd-340                                340.98-0ubuntu0.16.04.1                       amd64        NVIDIA OpenCL ICD
rc  nvidia-opencl-icd-340-updates                        340.96-0ubuntu3                               amd64        Transitional package for nvidia-opencl-icd-340
rc  nvidia-opencl-icd-361                                367.57-0ubuntu0.16.04.1                       amd64        Transitional package for nvidia-opencl-icd-367
ii  nvidia-opencl-icd-367                                367.57-0ubuntu0.16.04.1                       amd64        NVIDIA OpenCL ICD
ii  nvidia-prime                                         0.8.2                                         amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings                                      361.42-0ubuntu1                               amd64        Tool for configuring the NVIDIA graphics driver
and
> ~$ sudo cat /etc/modprobe.d/* | grep nouv
blacklist nouveau
blacklist lbm-nouveau
alias nouveau off
alias lbm-nouveau off# This file was installed by nvidia-361
blacklist nouveau
blacklist lbm-nouveau
alias nouveau off
alias lbm-nouveau off# This file was installed by nvidia-367
blacklist nouveau
blacklist lbm-nouveau
alias nouveau off
alias lbm-nouveau off
and
> ~$ ls /etc/modprobe.d/
alsa-base.conf                  blacklist.conf              blacklist-oss.conf           fbdev-blacklist.conf    nvidia-361_hybrid.conf
amd64-microcode-blacklist.conf  blacklist-firewire.conf     blacklist-rare-network.conf  iwlwifi.conf            nvidia-graphics-drivers.conf
ath9k.conf                      blacklist-framebuffer.conf  blacklist-watchdog.conf      mlx4.conf               vmwgfx-fbdev.conf
blacklist-ath_pci.conf          blacklist-modem.conf        dkms.conf                    nvidia-331_hybrid.conf

You think my generation of vid card is "new"? I was going for something a little out-of-date. In any case, I do want to do a little bit of gaming, so I don't know if the driver you're talking about would cut it.

---

### Post by Bashing-om on 2016-11-21
PenguinLust; K;

Gaming calls for the proprietary driver.
So what I do suggest is to purge the present nVidia files .. and
install our trusted PPA source ( here these drivers are tested prior to being released to the general public ) and obtain/install the 375 driver.

So run in terminal:
```

sudo find / -name "NVIDIA-Linux-*"

```
If that comes back null we can proceed.

Clean up the old debris:
```

sudo rm /etc/X11/xorg.conf
sudo apt purge nvidia*

```

Add our PPA source and install the 375 version driver:
```

sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt update
sudo apt install nvidia-375
sudo apt upgrade

```

And reboot to see the effect:
```

sudo reboot

```

Bear in mind with the boot parameter "text" I am not sure what to expect other than the pretty colors will not be displayed in booting up .. Maybe in systemd this will boot you to terminal rather than to the GUI login . I have not tested so not real sure .

[INDENT][INDENT]what ya look like now
[INDENT][INDENT][INDENT]on the other side
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by PenguinLust on 2016-11-22
Doesn't appear to have made a difference :(

> **Bashing-om said:**
> 
So run in terminal:
```

sudo find / -name "NVIDIA-Linux-*"

```
If that comes back null we can proceed.

It didn't, but all it found was the install file in my home directory, which is inactive at this time.

> 
Clean up the old debris:
```

sudo rm /etc/X11/xorg.conf

```

It's a bit strange, but this file doesn't exist.
> 
sudo find / -iname xorg.conf

didn't find anything either.
> 
```

sudo apt purge nvidia*

```

Done.

> Add our PPA source and install the 375 version driver:
```

sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt update
sudo apt install nvidia-375
sudo apt upgrade

```

And reboot to see the effect:
```

sudo reboot

```

Done

> Bear in mind with the boot parameter "text" I am not sure what to expect other than the pretty colors will not be displayed in booting up .. Maybe in systemd this will boot you to terminal rather than to the GUI login . I have not tested so not real sure .
I put it back to the splash screen.

I noticed that all of my addition drivers are open source except one, so I tried it w/340. It also didn't make a difference.

Here are some of the other listings again:
> 
~$ sudo cat /etc/modprobe.d/* | grep nouv
blacklist nouveau
blacklist lbm-nouveau
alias nouveau off
alias lbm-nouveau off# This file was installed by nvidia-340
blacklist nouveau
blacklist lbm-nouveau
alias nouveau off
alias lbm-nouveau offoptions vmwgfx enable_fbdev=1

> ~$ ls /etc/modprobe.d/
alsa-base.conf                  blacklist-rare-network.conf
amd64-microcode-blacklist.conf  blacklist-watchdog.conf
ath9k.conf                      dkms.conf
blacklist-ath_pci.conf          fbdev-blacklist.conf
blacklist.conf                  iwlwifi.conf
blacklist-firewire.conf         mlx4.conf
blacklist-framebuffer.conf      nvidia-340_hybrid.conf
blacklist-modem.conf            nvidia-graphics-drivers.conf
blacklist-oss.conf              vmwgfx-fbdev.conf

> ~$ dpkg -l | grep -i nvidia
ii  bbswitch-dkms                                        0.8-3ubuntu1                                  amd64        Interface for toggling the power on NVIDIA Optimus video cards
rc  libcuda1-331-updates                                 331.113-0ubuntu0.0.4                          amd64        NVIDIA CUDA runtime library
ii  libcuda1-340                                         340.98-0ubuntu0.16.04.1                       amd64        NVIDIA CUDA runtime library
ii  nvidia-340                                           340.98-0ubuntu0.16.04.1                       amd64        NVIDIA binary driver - version 340.98
rc  nvidia-375                                           375.20-0ubuntu0~gpu16.04.1                    amd64        NVIDIA binary driver - version 375.20
ii  nvidia-opencl-icd-340                                340.98-0ubuntu0.16.04.1                       amd64        NVIDIA OpenCL ICD
rc  nvidia-opencl-icd-375                                375.20-0ubuntu0~gpu16.04.1                    amd64        NVIDIA OpenCL ICD
ii  nvidia-prime                                         0.8.2                                         amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings                                      375.20-0ubuntu0~gpu16.04.1                    amd64        Tool for configuring the NVIDIA graphics driver

---

### Post by Bashing-om on 2016-11-22
PenguinLust; Yuk ..

Sorry, but this is now above my skill level . You have already tried all I know to do.

[INDENT][INDENT]when I do not know
[INDENT][INDENT][INDENT]I do not know
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Yellow Pasque on 2016-11-22
It still looks like you have a mix of nvidia-340 and 375 packages installed. I think Synaptic can help you here (search for 'nvidia' to see the installed packages) to get rid of the 340 packages. Mark the 375 packages for reinstall, and when you're done, run:
```
sudo nvidia-xconfig
```
Reboot and give us the new Xorg log

> I noticed that all of my addition drivers are open source except one, so I tried it w/340. It also didn't make a difference.
Now that you added the PPA, I would recommend not using the drivers GUI to switch video drivers.

---

### Post by PenguinLust on 2016-11-23
I'm starting to think it was a flakey monitor connection. I borrowed another one from work, which managed to display at a whopping 1920x1080. When I plugged my own monitor back in, it ran at 1680x1050 again. Now that I think of it, this isn't the first time that connector has given me grief. Thanks for taking the time.<br><br>BTW, since I began the process for setting up in runlevel 3, can you give me a tip on reversing that? All I remember is that it was supposed to be relevant to systemd.

---

