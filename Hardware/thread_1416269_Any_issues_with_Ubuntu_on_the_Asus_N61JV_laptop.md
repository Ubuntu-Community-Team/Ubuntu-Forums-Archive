---
title: "Any issues with Ubuntu on the Asus N61JV laptop?"
date: 2010-02-25
forum: Hardware
---

### Post by bgilbert on 2010-02-25
Hi,

I would really like to get the Asus N61JV laptop. Does anyone know of any issues running ubuntu on this laptop, or can spot any incompatible hardware pieces? 

Thanks in advance!
-Bryan


You can find it on amazon here:

[http://www.amazon.com/N61JV-X2-16-Inch-Versatile-Entertainment-Laptop/dp/B00352LQYO/ref=sr_1_1?ie=UTF8&m=ATVPDKIKX0DER&s=pc&qid=1267150586&sr=1-1]("http://www.amazon.com/N61JV-X2-16-Inch-Versatile-Entertainment-Laptop/dp/B00352LQYO/ref=sr_1_1?ie=UTF8&m=ATVPDKIKX0DER&s=pc&qid=1267150586&sr=1-1")

The specs are: 
* 2.53GHz Intel Core i5-430M Processor
* 4GB of DDR3 1066MHz SDRAM, 2 slots, 8GB Max
* 500GB Hard Drive (7200 RPM); Super Multi Optical Disk Drive; Wi-Fi 802.11 bgn
* 16-Inch HD LED LCD Display; 2.0MP Webcam; HDMI Port; NVidia GT325M Graphics Engine with 1GB DDR3 Dedicated VRAM

---

### Post by avilella on 2010-02-27
Has anyone tried the Nvidia optimus compatibility with Linux?

---

### Post by phidia on 2010-03-08
I think, as of yet, this technology is too new. Unless something has happened recently there are no linux drivers from nvidia. See [this]("http://www.phoronix.com/scan.php?page=news_item&px=Nzk3Mg") - the laptop in question could be a nice one only time will tell if nvidia releases linux drivers for the gpu.

---

### Post by avilella on 2010-03-17
Good news. It seems things have started moving in the Linux front:
[http://airlied.livejournal.com/71734.html](http://airlied.livejournal.com/71734.html)

> **phidia said:**
> I think, as of yet, this technology is too new. Unless something has happened recently there are no linux drivers from nvidia. See [this]("http://www.phoronix.com/scan.php?page=news_item&px=Nzk3Mg") - the laptop in question could be a nice one only time will tell if nvidia releases linux drivers for the gpu.

---

### Post by gap1981 on 2010-04-27
i have a n61jv and i have tried the ubuntu 10.4 release candidate live cd. it seems to work ok, on intel graphics with compiz efects, wifi, etc. The system ofered me to install the nvidia porpietary driver but i didnt do it. I think is an error because there isnt a nvidia driver for optimus.

---

### Post by palmira on 2010-05-27
Hi everyone,

I'm currently also considering to purchase an ASUS N61 laptop. It's my preselection as the hardware makes the first impression of being somewhat Linux-friendly (NVidia graphics, Intel wireless, ... although I'm absolutely not an expert). My intention is clear: the preinstalled windows would not even experience a first start-up.

What's the current status? Do most things work out of the box?

What about the NVidia card? Does Ubuntu automatically suggest the right proprietary driver and does it survive kernel updates? Or does Ubuntu ignore the card and uses the Intel graphics instead?

Does USB 3.0 cause some weird problems?

I'd love to hear which experience you've had.

Thank you very much in advance,
palmira

---

### Post by avilella on 2010-05-28
Hi palmira,

even if you haven't bought the laptop, feel free to subscribe to the asus-n-series group and ask any questions you may have to the mailing list:

[http://lists.launchpad.net/asus-n61-series](http://lists.launchpad.net/asus-n61-series)

> **palmira said:**
> Hi everyone,

I'm currently also considering to purchase an ASUS N61 laptop. It's my preselection as the hardware makes the first impression of being somewhat Linux-friendly (NVidia graphics, Intel wireless, ... although I'm absolutely not an expert). My intention is clear: the preinstalled windows would not even experience a first start-up.

What's the current status? Do most things work out of the box?

What about the NVidia card? Does Ubuntu automatically suggest the right proprietary driver and does it survive kernel updates? Or does Ubuntu ignore the card and uses the Intel graphics instead?

Does USB 3.0 cause some weird problems?

I'd love to hear which experience you've had.

Thank you very much in advance,
palmira

---

### Post by palmira on 2010-05-28
Thank you very much, avilella, both for the tip and for initiating such a mailing list. I have just subscribed to the list and will ask there soon.

I think, however, that it would be very useful for all those who do some quick search through the web if this thread could provide at least some very basic answers. Most importantly: What can be expected to work out of the box, and where can small / big problems occur?

palmira

---

### Post by palmira on 2010-05-31
Okay, little update:

I have decided not to buy the ASUS N61 laptop as it seems that there are very serious problems with the graphics. The rest is said to work fine, except the USB 3.0 (an issue that has a relatively easy solution somewhere described in this forum).

Although our experience has taught us that NVIDIA cards work fine, one has to be extremely careful when it comes to new laptops. The ASUS N61, e.g., uses the Optimus technology which is supposed to automatically switch between an NVIDIA and an Intel chip (as far as I understood). Not only is there no Linux support for this switching; it even seems that it's impossible to use the NVIDIA card. One would be restricted to the Intel graphics. And, worst of all: a search through the web indicates that no solution is close.

palmira

---

### Post by Welly Wu on 2010-08-28
I am replying to see if there has been any progress made with regard to the ASUS N61JV-X2 and Ubuntu GNU/Linux 10.04 LTS. I bought my notebook PC about two weeks ago and I am contemplating whether or not to install Ubuntu on my laptop.

It seems that NVIDIA released a Linux x64 bit package version 256.44 certified on 08/02/2010. Here is the link:

[http://www.nvidia.com/object/linux-display-amd64-256.44-driver.html](http://www.nvidia.com/object/linux-display-amd64-256.44-driver.html)

What else seems to be working out of the box with this notebook PC and Ubuntu GNU/Linux?

I would appreciate replies from others on this matter. Thank you.

---

### Post by ericinthebay on 2010-09-01
I am on the N61JV right now with Ubuntu 10.04 LTS.  Everything is fine until trying to activate Nvidia drivers.  

Ubuntu suggests to activate the Nvidia drivers (System -> Administration -> Hardware Drivers), which goes fine until you reboot whereby I always get a blank screen.  

From the forums it is suggested to hit ctrl-alt-F1 or ctrl-alt-shift-F1 to bypass X and get a command line or boot into recovery mode to fix it, however ctrl-alt-F1 just freezes up the X display.  Recovery mode doesn't seem useful.

I also tried to install the Linux 64 bit drivers dated 8-31-2010 from the Nvidia site -- however it tells me I need to exit the X server to install the drivers.  Due to above issues I cannot find anyway to get out of X and onto a plain command line.

However I am getting all the Desktop effects, running Google Earth, etc without activating Nvidia drivers, so the system is seeing something, but perhaps it is the Intel video.  There is no xorg.conf file created so it's hard to know what is providing the video.

---

### Post by Welly Wu on 2010-09-02
Thank you for the informative post. I think that I will wait until NVIDIA publishes an updated package that will enable the Optimus technology to work seamlessly as it does in Microsoft Windows 7.

---

### Post by Welly Wu on 2010-09-04
I just installed Ubuntu GNU/Linux 10.04 LTS on my ASUS N61JV-X2. Almost everything works out of the box except for the NVIDIA 325 M GPU. I downloaded the latest NVIDIA drivers version 256.53 Certified and opened up the README file too.

You have to boot into the command line by changing your run level. Then, you have to disable NOVEAU to install the proprietary driver which I mentioned.

Steps to solve this problem:

[http://ubuntuforums.org/showthread.php?t=990978&highlight=nvidia-common](http://ubuntuforums.org/showthread.php?t=990978&highlight=nvidia-common)

This is my first attempt to install the proprietary NVIDIA 325 M driver package on Ubuntu GNU/Linux 10.04 LTS. If I am successful, then I will let the community know the outcome.

Thank you.

---

### Post by ericinthebay on 2010-09-16
> You have to boot into the command line by changing your run level. 

Therein lies the problem, I can't find a way to boot to runlevel 1 and get a prompt -- the screen is always just blank.  

And yes it has the 325M GPU with Optimus.

I would really like to get it going, but without being able to get a rescue prompt it seems risky.  I have to constantly make backups whenever I install anything -- in case I break something and have to restore it all from scratch, ugh.

---

### Post by dugh on 2010-09-19
That driver from nvidia also mentions support for xorg 1.9, which is the version that Ubuntu Maverick uses.

[http://www.nvidia.com/object/linux-display-amd64-256.53-driver.html](http://www.nvidia.com/object/linux-display-amd64-256.53-driver.html)

So you might try upgrading to Ubuntu Maverick and then see if you can install the nvidia drivers.

Also the 2.6.35 kernel Maverick uses apparently supports VGA switcheroo for hybrid graphics (2 cards like we have).  [https://launchpad.net/~hybrid-graphics-linux](https://launchpad.net/~hybrid-graphics-linux)

[http://asusm51ta-with-linux.blogspot.com/](http://asusm51ta-with-linux.blogspot.com/)

I'll give it a shot sometime, but I can't today.

---

### Post by dugh on 2010-09-19
No, still doesn't work in Ubuntu 10.10.

Tried both the 256.53 and beta 260.19.06 nvidia drivers.

If anyone tries this stuff out and it hangs on boot, learn about the keyboard shortcuts (beyond control-alt-f1), such as:

alt-sysrq-e - to try to quit (sigterm) the current processes nicely (then you can control-alt-f1 to get to a login prompt)

alt-sysrq-k - kill all not nicely

alt-sysrq-b - reboot - sometimes I had to reboot and then hit alt-sysrq-e before it hung up to get a login prompt

alt-sysrq-r - raw keyboard (try to get keyboard control back)

Before you try the nvidia installer run 'sudo service gdm stop'

To uninstall the nvidia driver, run the installer again, tacking on: --uninstall

and then delete /etc/X11/xorg.conf and delete /etc/init.d/nvidia-installer-disable-nouveau.conf if you want to disable nvidia and go back to where it was (the intel card, which works).

---

### Post by ericinthebay on 2010-09-21
Thanks -- alt-sysrq-e followed by ctrl-alt-F1 got me to a prompt.  

I wasn't aware of the alt-sysrq commands. On other systems I just select recovery mode and it all works.

- Eric

---

### Post by ericinthebay on 2010-09-21
In any case, it doesn't look worthwhile to install these drivers.  The laptop is not 100% Linux and the available graphics are fine for my Linux needs.

---

### Post by Welly Wu on 2011-03-17
Unfortunately, nVIDIA Optimus is not going to be supported for GNU/Linux. Do not install the proprietary nVIDIA graphics drivers or you will reboot into BASH.

---

