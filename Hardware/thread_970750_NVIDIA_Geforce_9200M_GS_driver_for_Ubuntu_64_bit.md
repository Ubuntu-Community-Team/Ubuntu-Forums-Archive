---
title: "NVIDIA Geforce 9200M GS driver for Ubuntu 64 bit"
date: 2008-11-04
forum: Hardware
---

### Post by shobhitg on 2008-11-04
Hi All,

I recently purchased an HP dv4 with 64 bit Vista pre-installed.

This laptop has NVIDIA Geforce 9200M GS (which works extremely well on Vista). 

I then installed Kubuntu 64 bit as a Virtual Box machine.
Unfortunately I am not able to find out any supported linux driver for my graphics card. And now I am getting a 800x600 resolution. Which is very uncool...

So i am desperately trying the drivers provided by NVIDIA at:
[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

I am not even able to find [[COLOR="Blue"]my graphics card[/COLOR]]("http://www.nvidia.com/object/geforce_9200m_gs.html") listed there!! 

I have seen quite some related incomplete help threads on Googling... And now I thought I will ask for help in the forum from the ubuntu community.

Has anyone ever been able to install a driver in ubuntu for this graphics card ([http://www.nvidia.com/object/geforce_9200m_gs.html]](http://www.nvidia.com/object/geforce_9200m_gs.html])) ?

Is there any tested trick which I can apply to fool it to use some other (but related) NVIDIA driver ?

Is there a way by which I can get more resolution (even if my graphics card doesn't get configured to its full potential) ?

Thanks for all the help.
Shobhit

---

### Post by methodmarvel on 2008-11-24
> **shobhitg said:**
> Hi All,

I recently purchased an HP dv4 with 64 bit Vista pre-installed.

This laptop has NVIDIA Geforce 9200M GS (which works extremely well on Vista). 

I then installed Kubuntu 64 bit as a Virtual Box machine.
Unfortunately I am not able to find out any supported linux driver for my graphics card. And now I am getting a 800x600 resolution. Which is very uncool...

So i am desperately trying the drivers provided by NVIDIA at:
[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

I am not even able to find [[COLOR="Blue"]my graphics card[/COLOR]]("http://www.nvidia.com/object/geforce_9200m_gs.html") listed there!! 

I have seen quite some related incomplete help threads on Googling... And now I thought I will ask for help in the forum from the ubuntu community.

Has anyone ever been able to install a driver in ubuntu for this graphics card ([http://www.nvidia.com/object/geforce_9200m_gs.html]](http://www.nvidia.com/object/geforce_9200m_gs.html])) ?

Is there any tested trick which I can apply to fool it to use some other (but related) NVIDIA driver ?

Is there a way by which I can get more resolution (even if my graphics card doesn't get configured to its full potential) ?

Thanks for all the help.
Shobhit

I might be wrong but in virtualbox you aren't able to install graphics drivers because it emulates the hardware and then translates this to your actual graphics card to display it to you - which means no 3D in virtualbox virtual machines.

Other than that I don't know - I think it's likely the repos would have a restricted driver if you were to install it to a separate partition but whether they'd have a 64bit driver or whether 32v64 matters when it comes to video drivers is beyond me.

Also - I noticed your post on [http://www.nvnews.net/vbulletin/showthread.php?t=122473](http://www.nvnews.net/vbulletin/showthread.php?t=122473) (I'm researching the samsung q310) and looked at appendix A - GeForce 9200M GS 	0x06E8   is absolutely listed so as "AaronP" says on that forum - your card is supported.

---

### Post by sjbaugh on 2008-11-24
> whether they'd have a 64bit driver or whether 32v64 matters when it comes to video drivers is beyond me.

I am running 8.10 64 bit (NOT in a virtual box), and I am using the 177.80 restricted video driver with no issues (yet!) on my nVidia 8400 GS card. It says it should work with later nVidia cards.

In virtualbox you will be using a driver for its "virtual" video card, not your own real card and, as methodmarvel says, I have not found a way to get 3D effects from it.

---

### Post by avilella on 2009-04-05
Since you have access to a laptop with hybrid graphics and have tried to run Linux, please take a moment to provide the DSDT information for the laptop in this link:

[https://bugs.launchpad.net/bugs/312756](https://bugs.launchpad.net/bugs/312756)

DSDT is an acronym for Differentiated System Description Table. This table contains the Differentiated Definition Block, which supplies the information and configuration information about the base system. It is always inserted into the ACPI Namespace by the OS at boot time.

If you've got a laptop with a IGP and a hybrid Nvidia or ATi card, and you have tried to use Linux on it, you may have noticed that there are issues with the hybrid graphics setup. To help improve the Linux hybrid graphics support for this laptop, please attach your DSDT information to this Launchpad bug report specifying your laptop model:

[https://bugs.launchpad.net/bugs/312756](https://bugs.launchpad.net/bugs/312756)

To compile your DSDT information, install if you haven't already the acpidump and iasl tools:
sudo apt-get install acpidump iasl           # on Debian-based systems

Then run the following commands:

sudo acpidump > acpidump.txt
sudo acpixtract acpidump.txt
iasl -d DSDT.dat

This will create a DSDT.dsl file that you can attach to the bug report. This information will allow the developers to fully implement the hybrid graphics features for Linux.

---

