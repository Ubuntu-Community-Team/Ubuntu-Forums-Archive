---
title: "Unable to detect nvidia GTX 970M with hybrid gpu MSI GE72 2QF Apache Pro"
date: 2016-02-05
forum: Hardware
---

### Post by resaypi on 2016-02-05
Hi everyone,

I'm kind of a newbie to ubuntu. I've got 15.10 installed in my MSI, which has GTX970M and an intel integrated graphics. When I type lspci, the relevant lines I get are:

00:02.0 VGA compatible controller: Intel Corporation Broadwell-U Integrated Graphics (rev 0a)
01:00.0 3D controller: NVIDIA Corporation GM204M [GeForce GTX 970M] (rev a1)

When I type nvidia-detector I get none as output.

I've looked at older threads, most of them suggest I use bumblebee. When I run optirun nvidia-detector I still get none. And I need to be very careful with installing optirun, as it sometimes gives me error. I need to make sure I use the right version and get it from ppa.

I've just clean installed my system again, and I'm aiming to play games on steam for linux. Any suggestions to get my nvidia gpu working again?

Thanks,

---

### Post by Bashing-om on 2016-02-05
resaypi; Hello .

Should be no big deal .
Make sure that the Nvidia card is enabled in bios ; And
Nvidia recommends the 352 version driver for that Nvidia card; Per:
[http://www.nvidia.com/download/driverResults.aspx/97645/en-us](http://www.nvidia.com/download/driverResults.aspx/97645/en-us)

Now me I am a CLI type of guy and:
CLI method to install drivers:->
this command will give information about your card + all drivers available including the open source driver.
```

sudo ubuntu-drivers devices

```
To see all the devices that need drivers (list the proprietary video drivers available for your graphic card).
```

sudo ubuntu-drivers list

```
to see all available drivers. These commands take a while to run.
```

sudo ubuntu-drivers autoinstall

```
to install the standard available proprietary video driver; This will install the latest proprietary video driver. If the proprietary video driver is already installed then this command will only read the package lists and rebuild the dependency tree. If that happens then you know you have the proprietary driver installed.
See: [http://askubuntu.com/questions/449693/how-to-change-graphic-card-driver-using-ubuntu-drivers](http://askubuntu.com/questions/449693/how-to-change-graphic-card-driver-using-ubuntu-drivers)
When the Nvidia driver is installed the tool nvivia-prime will also be installed - BumbleBee is depreciated now in favor of nvidia-prime.
see:
```

apt-cache show nvidia-prime

```
for a better description .

[INDENT][INDENT]kernel has to have a way to talk to the hardware
[/INDENT][/INDENT]

---

### Post by resaypi on 2016-02-05
Hi Bashing-om,

Thanks for your input. I've followed every step, and now I can access NVIDIA X Server Settings by simply typing nvidia on dash. There I select the GPU I would like to use. I can choose between NVIDIA and Intel. I choose NVIDIA and reboot, but still when I type lspci, my VGA is 
00:02.0 VGA compatible controller: Intel Corporation Broadwell-U Integrated Graphics (rev 0a)

Am I missing something here?

Thanks

---

### Post by efflandt on 2016-02-07
lspci will always show VGA as the Intel and 3D as Nvidia. That does not tell you which is active at any given time. Doesn't your power LED change color to indicate which graphics is active? The power LED on my MSI GE60-2OE is cool **[COLOR=#0000cd]blue[/COLOR]** when Intel graphics is active and hotter **[COLOR=#ff6600]amber[/COLOR]** when Nvidia is active (in my case GTX 765M).

---

### Post by resaypi on 2016-02-08
I don't have an indicator for which GPU I'm using in GE72, or even if there is I haven't figured out or obvious to me yet. Is there a way to check which GPU I'm using through the system? 

I've also noticed when I run the benchmark glmark2-es2, the score when the NVIDIA card is selected 427, whereas Intel gives me 2235. I reboot every time I change the prime profile, before running the benchmark. Somethings looks wrong here.

---

### Post by Bashing-om on 2016-02-08
resaypi; Yeah ...

Agreed that " Somethings looks wrong here. " I too would expect the Nvidia chip set to have the greater performance .

You can verify which chip set is current with terminal command:
```

sudo lshw -C display

```
Will take a bit of time for the command to complete; patience.
in the output is the graphics set AND the driver in use.

At this time I do suggest we look at what Nvidia drivers are installed:
```

dpkg -l | grep -i nvidia

```
let's verify that the correct driver for the Nvidia chip set is installed and that there are no conflicts.

I do have a thought in mind, make sure 1st
[INDENT][INDENT][INDENT]we have a firm foundation
[/INDENT][/INDENT][/INDENT]

---

