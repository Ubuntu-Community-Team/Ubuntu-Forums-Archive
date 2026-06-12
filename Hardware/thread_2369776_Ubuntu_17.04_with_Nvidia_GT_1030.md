---
title: "Ubuntu 17.04 with Nvidia GT 1030"
date: 2017-08-26
forum: Hardware
---

### Post by brian696 on 2017-08-26
Hi all,

I'm having some trouble getting graphics drivers to run and be stable. I've exhausted my limited troubleshooting knowledge and haven't been able to find any forum posts with my specific problem.

The problem:
[LIST=1]
[*]Fresh installation of Ubuntu 17.04, stock, nothing special 
[*]Install nvidia binary drivers (I have tried both 384.69 and 384.47). During the installation process, I receive a warning message that the pre-installation script has failed. I continue anyway and the driver installation proceeds without errors. 
[*]Cue reboot, wonderful full HD resolution on my monitor, everything seems OK. No issues crop up after a few reboots (note: reboots, not full shutdown). 
[*]Full shutdown, unplug the monitor HDMI cable from the 1030 graphics card, restart......** and I'm stuck in a login loop**. I enter my password, the screen blinks, and I'm back to the login screen 
[*]Re-installing the Nvidia drivers fixes the login loop 
[/LIST]

I've been able to reproduce this problem twice using the steps above, but I am not able to consistently reproduce it.

I'm not sure where to go from here. I imagine there are some logs or configuration files that would help with troubleshooting, but I'm not sure what or where I should be looking.

Has anyone gotten 17.04 working with the GT 10 series?

Thanks in advance for any troubleshooting suggestions.

---

### Post by Autodave on 2017-08-27
Where did you get the driver from?

---

### Post by Perfect Storm on 2017-08-27
Have you tried this, open the terminal and type:
```
sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt update
```

Now search for 'Software and Updates' in the Dash/Menu. Open it.
Go to Additional Drivers and pick the latest driver for your 1030 card.Click apply changes.
When it's done reboot.

---

### Post by brian696 on 2017-08-27
Autodave, 

I got my currently-installed drivers from the Nvidia website: [https://www.geforce.com/drivers](https://www.geforce.com/drivers)

Art,

After following your instructions, I see the following on my Additional Drivers page. The open source drivers option is disabled. What must I do to get it back?

Thanks again.


[IMG]http://i.imgur.com/PIEDs5j.jpg[/IMG]

---

### Post by Bashing-om on 2017-08-27
brian696; Uh Uh ....

Installing from OEM is the means of last resort . even nvidia "
> 
Note that many Linux distributions provide their own packages of the NVIDIA Linux Graphics Driver in the distribution's native package management format. This may interact better with the rest of your distribution's framework, and you may want to use this rather than NVIDIA's official package.


See:
[http://www.nvidia.com/download/driverResults.aspx/123103/en-us](http://www.nvidia.com/download/driverResults.aspx/123103/en-us)

I suggest we remove the OEM driver and do as nvidia recommends and install the 384 version driver from our trusted PPA.
```

sudo find / -name "NVIDIA-Linux-*"

```
 you have to run the .run file again with --uninstall:
```

./Nvidiawhatever.run --uninstall ##(must be cd'd to the directory/location)
sudo apt purge nvidia

```
 Now install from PPA:
```

sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt update
sudo ubuntu-drivers autoinstall
sudo apt full-upgrade
sudo reboot

```
Where I expect autoinstall to choose 384 to install .

see what we look like on this other side of the boot up.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by puffomon on 2017-09-03
Yeah i have the same card, (see my thread)
I can not get this card stable, i use ppa drivers, and ive tried everone from 381.xx and to the newest. 

Random freezes, random reboot (on a fresh install of 16.04)

To bad. Let me know if you have any luck.

---

### Post by Autodave on 2017-09-03
Well, we haven't heard back from Brian696 yet, so I am gonna assume he fixed his with the instructions given by Bashing-om.  Have you tried that yet?

---

