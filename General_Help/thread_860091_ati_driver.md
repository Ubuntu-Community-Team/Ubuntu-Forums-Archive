---
title: "ati driver"
date: 2008-07-15
forum: General Help
---

### Post by whalogreg on 2008-07-15
running 8.04 on a fresh install...

I'm trying to install the radeon driver from ati. When I try to run the installer (ati-driver-installer-8-6-x86.x86_64.run) that I've downloaded from ati's website, in terminal, i get the error...
"bash: ati-driver-installer-8-6-x86.x86_64.run: command not found"
I know i'm in the right directory in terminal, because when I type "dir" it lists "ati-driver-installer-8-6-x86.x86_64.run"... what am i doing wrong here?


These are the instructions from ati's site...

1. Launch the Terminal Application/Window and navigate to the ATI Proprietary Linux driver download.
2. Enter the command ati-driver-installer-8-6-x86.x86_64.run to launch the ATI Proprietary Linux driver installer. The ATI Proprietary Linux Driver Setup dialog box is displayed.

again, when I do so, I get the "bash" error...

---

### Post by coderpp on 2008-07-15
sudo sh ati-driver-installer-8-6-x86.x86_64.run

or

chmod +x ati-driver-installer-8-6-x86.x86_64.run
./ati-driver-installer-8-6-x86.x86_64.run

---

### Post by whalogreg on 2008-07-15
> **coderpp said:**
> sudo sh ati-driver-installer-8-6-x86.x86_64.run

or

chmod +x ati-driver-installer-8-6-x86.x86_64.run
./ati-driver-installer-8-6-x86.x86_64.run

So I sucessfully installed with the first code you offered me, but when I rebooted and logged in, instead of seeing my desktop I only see a white screen with my mouse pointer.. I tried booting in recovery where I ran both "repair packages" and "xfix" to no avail.. I have no visible desktop now...

---

### Post by Bablefish on 2008-07-15
I hate to tell you this I know what happened, dispite what some say here that is a 64 bit CPU driver only and my guess is that you have a 32 bit CPU. I discovered that myself when the 32 bit commands to open that driver did not work for me, and a good friend who repairs computers for a living advised me not to use the 64 bit commands.

---

### Post by whalogreg on 2008-07-15
> **Bablefish said:**
> I hate to tell you this I know what happened, dispite what some say here that is a 64 bit CPU driver only and my guess is that you have a 32 bit CPU. I discovered that myself when the 32 bit commands to open that driver did not work for me, and a good friend who repairs computers for a living advised me not to use the 64 bit commands.

I think you're right.. I noticed that the download for 32 and 64 bit driver was exactly the same.. any suggestions on where to find a 32 bit driver for an ati radoen x1600 that will work in 8.04?

---

### Post by jocko on 2008-07-15
> **Bablefish said:**
> I hate to tell you this I know what happened, dispite what some say here that is a 64 bit CPU driver only and my guess is that you have a 32 bit CPU. I discovered that myself when the 32 bit commands to open that driver did not work for me, and a good friend who repairs computers for a living advised me not to use the 64 bit commands.

> **whalogreg said:**
> I think you're right.. I noticed that the download for 32 and 64 bit driver was exactly the same.. any suggestions on where to find a 32 bit driver for an ati radoen x1600 that will work in 8.04?

That's wrong. AMD/ATI provides both the [COLOR=Blue]32 bit[/COLOR] driver and the [COLOR=Red]64 bit[/COLOR] driver in the same file (ati-driver-installer-8-6-[COLOR=Blue]x86[/COLOR].[COLOR=Red]x86_64[/COLOR].run). That's why it's file name contain both "[COLOR=Blue]x86[/COLOR]" and "[COLOR=Red]x86_64[/COLOR]". 
But to install the driver there are a few options, and just running the installer from amd/ati is not a good way to do it on ubuntu (it will just mess things up).

The first (and easiest+supported by ubuntu) option is to use the restricted driver manager (Administration --> Hardware Drivers). It will install the driver from the ubuntu repos (not the latest version, though).

The second option (also quite easy) is to install the program envyng-gtk (from the repos) and use it to set up ati's drivers (slightly newer than the standard repo version, but still not the latest).

The third option is to follow [this guide]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_2:_Manual_Method_.28installing_Catalyst_8.6.29") (quite advanced and I don't recommend it to a beginner, unless there is a good reason for needing the latest driver) for installing the latest version of the driver using amd/ati's installer to build proper debian packages. This guide also contains a few extra steps that are absolutely necessary to get things working without conflicting with the repo version, as well as some troubleshooting.

---

