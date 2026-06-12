---
title: "Problem with GTX 980 Ti?"
date: 2016-06-17
forum: Hardware
---

### Post by Josease on 2016-06-17
Hi, long time ago I'm trying to install ubutnu (or other linux distro) on my PC, for some reason when installing with the 980 ti connected not start black screen is both the outputs of the graph and outputs integrated . I installed ubuntu without the 980ti and works perfectly, but I need to install with the graphic. Does this happen to anyone else? What could it be? Thank you. (Sorry for my english)

---

### Post by Bashing-om on 2016-06-17
Josease; Hello; Welcome to the forum.

That card takes the 367 version driver. Unfortunately, that driver is only available for release 16.04 and to be 16.10.
What release are you running ? .. if 14.04 .. we might get the 364 version driver to work, but even that requires accessing our trusted PPA ( Personal Package Archive ) .

The procedure is to boot to a terminal and in this terminal activate the PPA and then once the system is fully updated, install the desired driver. You must have the 980 ti card installed.

How far in the boot process do you get when attempting to boot ? We may have to employ a boot parameter to get you started, if you can not get to the login screen.
Once at the login screen key combo ctl+alt+F1 will yield a console interface. We can work from this interface to get a driver installed.


we can do this
[INDENT][INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT][/INDENT]

---

### Post by Josease on 2016-06-17
> **Bashing-om said:**
> Josease; Hello; Welcome to the forum.

That card takes the 367 version driver. Unfortunately, that driver is only available for release 16.04 and to be 16.10.
What release are you running ? .. if 14.04 .. we might get the 364 version driver to work, but even that requires accessing our trusted PPA ( Personal Package Archive ) .

The procedure is to boot to a terminal and in this terminal activate the PPA and then once the system is fully updated, install the desired driver. You must have the 980 ti card installed.

How far in the boot process do you get when attempting to boot ? We may have to employ a boot parameter to get you started, if you can not get to the login screen.
Once at the login screen key combo ctl+alt+F1 will yield a console interface. We can work from this interface to get a driver installed.


we can do this[INDENT][INDENT][INDENT]where there is a will there is a way
[/INDENT]
[/INDENT]
[/INDENT]

I do not remember the version, but I think in any linux distro and any version of ubuntu all I could see was the screen to install and test. With version 16.04 and 16.10 I can install it without problems?

---

### Post by Bashing-om on 2016-06-17
Josease; Well ..

Release 16.04 has the better avenue for support. We still have to activate the driver PPA, and install the 367 version driver from the PPA.

That is not to say that in 14.04 the 364 driver would not also work .

The point here is what ever you decide for an Operating System, we can install a driver . It is not that demanding or difficult.

[INDENT][INDENT]there is a way
[/INDENT][/INDENT]

---

### Post by Josease on 2016-06-17
> **Bashing-om said:**
> Josease; Well ..

Release 16.04 has the better avenue for support. We still have to activate the driver PPA, and install the 367 version driver from the PPA.

That is not to say that in 14.04 the 364 driver would not also work .

The point here is what ever you decide for an Operating System, we can install a driver . It is not that demanding or difficult.
[INDENT][INDENT]there is a way
[/INDENT]
[/INDENT]


And i can do from that screen? Thank you.

---

### Post by Bashing-om on 2016-06-17
Josease; Welp;

There are several ways we can do this ( install a driver ) .
If you can get to the login screen and activate the console interface is by far the least problem .
There are other ways to get that driver installed .

[INDENT][INDENT]more than one path
[INDENT][INDENT][INDENT]to an end[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Josease on 2016-06-17
> **Bashing-om said:**
> Josease; Welp;

There are several ways we can do this ( install a driver ) .
If you can get to the login screen and activate the console interface is by far the least problem .
There are other ways to get that driver installed .
[INDENT][INDENT]more than one path[INDENT][INDENT][INDENT]to an end[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


But only i can see the screen to test or install, no more. I can also install it on another computer and start ubuntu ¿boot?...

---

### Post by Bashing-om on 2016-06-18
Josease; Hey ;

If you are in the installer, and want to "test" .
Reboot the liveDVD(USB) with the Nvidia GTX 980 Ti card as active.
At the purple splash screen (stick figure keyboard emblems at bottom of screen) -> hit any key ->
Language screen -> escape key to accept the default ->
Booting options screen -> F6 key (other options) -> arrow down to the preset option(s) space or enter to accept and then the escape key to exit; 
choose the  "nomodeset" option at this time;
Enter key to continue the boot process to the GUI desk top; Degraded graphics is OK at this point.

When you complete the install, we do something similar IF required in order to install the graphics driver.

I do highly suggest and recommend that you install the 16.04 release.

[INDENT][INDENT]we can do this
[/INDENT][/INDENT]

---

### Post by Josease on 2016-06-18
> **Bashing-om said:**
> Josease; Hey ;

If you are in the installer, and want to "test" .
Reboot the liveDVD(USB) with the Nvidia GTX 980 Ti card as active.
At the purple splash screen (stick figure keyboard emblems at bottom of screen) -> hit any key ->
Language screen -> escape key to accept the default ->
Booting options screen -> F6 key (other options) -> arrow down to the preset option(s) space or enter to accept and then the escape key to exit; 
choose the  "nomodeset" option at this time;
Enter key to continue the boot process to the GUI desk top; Degraded graphics is OK at this point.

When you complete the install, we do something similar IF required in order to install the graphics driver.

I do highly suggest and recommend that you install the 16.04 release.
[INDENT][INDENT]we can do this
[/INDENT]
[/INDENT]


Ok, I'll try to do this now and say you, thx :)

---

### Post by Bashing-om on 2016-06-18
Josease; Great,

I am done for this session .. I will pick this back up later in my morrow.
If you continue this time, and have difficulties, there are others here to pick up my slack and help you through this.

[INDENT][INDENT]it is not a big deal
[/INDENT][/INDENT]

---

### Post by Josease on 2016-06-18
> **Bashing-om said:**
> Josease; Great,

I am done for this session .. I will pick this back up later in my morrow.
If you continue this time, and have difficulties, there are others here to pick up my slack and help you through this.
[INDENT][INDENT]it is not a big deal
[/INDENT]
[/INDENT]


Ok, thx

---

### Post by Bashing-om on 2016-06-18
Josease; HeY ...

I am back on. What progress have you made ? And what release have you decided to install ?

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by Josease on 2016-06-18
> **Bashing-om said:**
> Josease; HeY ...

I am back on. What progress have you made ? And what release have you decided to install ?
[INDENT][INDENT]all in the process
[/INDENT]
[/INDENT]


Hi! Yesterday I did was in the Ubuntu installation menu press a tab (or advanced options?) And once there put the "live nomodeset" command as nomodeset did nothing. Once I put that led to the ubuntu desktop, where I install nvidia drivers (I think) and I imagine that once installed could already  to install ubuntu. Yesterday I needed to sleep and find my other hdd, I found it recently and now I will try to do the same to install.

---

### Post by Bashing-om on 2016-06-18
Josease; K;

Continued progress .
Once installed with the 'nomodeset" boot parameter, we then install the graphics driver.

What release have you installed that we will work on ? The release version will make a difference on which driver version we can install.

[INDENT][INDENT]small steps
[INDENT][INDENT][INDENT]small steps
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Josease on 2016-06-18
> **Bashing-om said:**
> Josease; K;

Continued progress .
Once installed with the 'nomodeset" boot parameter, we then install the graphics driver.

What release have you installed that we will work on ? The release version will make a difference on which driver version we can install.
[INDENT][INDENT]small steps[INDENT][INDENT][INDENT]small steps
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


Ubuntu 16.04, i installed drivers with "[COLOR=#444444]sudo apt-get install nvidia-current"? or what is the right way?[/COLOR]

---

### Post by Bashing-om on 2016-06-18
Josease; Hey !

If you have no problems then " nvidia-current" is just fine .

Let's verify what version is installed/
```

sudo lshw -C display
dpkg -l | grep -i nvidia
lsmod | grep nvidia

```
will take a bit of time for the system to return the lshw output .. give it the time to complete.

[INDENT][INDENT]see,
[INDENT][INDENT][INDENT]no step for a stepper
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Josease on 2016-06-18
> **Bashing-om said:**
> Josease; Hey !

If you have no problems then " nvidia-current" is just fine .

Let's verify what version is installed/
```

sudo lshw -C display
dpkg -l | grep -i nvidia
lsmod | grep nvidia

```
will take a bit of time for the system to return the lshw output .. give it the time to complete.
[INDENT][INDENT]see,[INDENT][INDENT][INDENT]no step for a stepper
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


It worked!! I installed ubuntu, rebooted and everything perfect, thank you very much . Would you give me any advice to start using ubuntu? But wait... Now i have a problem

---

### Post by Bashing-om on 2016-06-18
Josease; Outstanding ..

I am interested in what version driver is installed,

As to getting started in ubuntu; I found these of great help:
[http://ubuntu-manual.org/downloads](http://ubuntu-manual.org/downloads)
[http://ubuntuguide.org/wiki/Ubuntu_Trusty](http://ubuntuguide.org/wiki/Ubuntu_Trusty) <-The ubuntu_guide
[http://www.ubuntupocketguide.com/download_main.html](http://www.ubuntupocketguide.com/download_main.html)

Be aware that the guides for 16.04 have not been released to this time, so far as I am aware.
16.04 uses systemd rather than upstart for the initiate and services control. There will be differences in the documentation as pertains to 16.04. You will soon learn to discern what applies .

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by Josease on 2016-06-18
> **Bashing-om said:**
> Josease; Outstanding ..

I am interested in what version driver is installed,

As to getting started in ubuntu; I found these of great help:
[http://ubuntu-manual.org/downloads](http://ubuntu-manual.org/downloads)
[http://ubuntuguide.org/wiki/Ubuntu_Trusty](http://ubuntuguide.org/wiki/Ubuntu_Trusty) <-The ubuntu_guide
[http://www.ubuntupocketguide.com/download_main.html](http://www.ubuntupocketguide.com/download_main.html)

Be aware that the guides for 16.04 have not been released to this time, so far as I am aware.
16.04 uses systemd rather than upstart for the initiate and services control. There will be differences in the documentation as pertains to 16.04. You will soon learn to discern what applies .
[INDENT][INDENT]hope this helps
[/INDENT]
[/INDENT]


Now I get error when you start ubuntu, I can not log in, proves to reinstall With this (sudo add-apt-repository ppa: graphics-drivers / ppa sudo apt-get update sudo apt-get install nvidia-358 nvidia-settings )

---

### Post by Bashing-om on 2016-06-18
Josease; Ouch .

If you do not purge the older installed driver prior to installing another driver, one gets a conflict in drivers.
Drives the system nuts, and will not start the GUI .

Still, not known what driver was installed .

[INDENT][INDENT]there can be only one
[/INDENT][/INDENT]

---

### Post by Josease on 2016-06-18
> **Bashing-om said:**
> Josease; Ouch .

If you do not purge the older installed driver prior to installing another driver, one gets a conflict in drivers.
Drives the system nuts, and will not start the GUI .

Still, not known what driver was installed .
[INDENT][INDENT]there can be only one
[/INDENT]
[/INDENT]


But now, in the installation have one problem for install "dev/sda"... I try to install other version or distro?

---

### Post by Bashing-om on 2016-06-18
Josease; Yuk;

We are having a communications issue between us.
I am not looking over your shoulder and can not see your terminal.
If you do not answer my questions I am at a loss.
If you do not explain an issue I can not follow your thought process.
Are you now attempting another install .. over a graphics driver issue ?

This is 'buntu .. always fixable .. the RE-install is a nuclear solution .

If it is that you want to install another distro as dual booting, keeping ubuntu 16.04 .. I would expect in the new installer to have some option similar to ubuntu install option of " install along side" .

All I am currently familiar with is ubuntu . It has been years since I even looked at any other distribution for fault isolation.

[INDENT][INDENT]which way did he go George
[/INDENT][/INDENT]

---

### Post by Josease on 2016-06-18
> **Bashing-om said:**
> Josease; Yuk;

We are having a communications issue between us.
I am not looking over your shoulder and can not see your terminal.
If you do not answer my questions I am at a loss.
If you do not explain an issue I can not follow your thought process.
Are you now attempting another install .. over a graphics driver issue ?

This is 'buntu .. always fixable .. the RE-install is a nuclear solution .

If it is that you want to install another distro as dual booting, keeping ubuntu 16.04 .. I would expect in the new installer to have some option similar to ubuntu install option of " install along side" .

All I am currently familiar with is ubuntu . It has been years since I even looked at any other distribution for fault isolation.
[INDENT][INDENT]which way did he go George
[/INDENT]
[/INDENT]


Yeah, sorry my english no is good, When installing the first time all went well, but booted the PC and re-enter ubuntu he left a message (I can not remember) and once past that message could not log in, to put the password looked out a graphical error and was returning to the login screen. When attempting to install it again halfway installation the error "dev/sda" or similar.

I will try to install it again, or another version, and if I can not nothing happens...

---

### Post by Bashing-om on 2016-06-18
Josease; OK !

We are fixing the current install .

Can be either a change in authority to access the desktop ..
OR
a graphic's driver either not installed ..or broken.

Again, in small steps to arrive at the fault.
1st step:
can you activate a console interface ?
at the login screen one should be able to activate this console with key combo ctl+alt+F1 .

From this console we have access to the system, and can then make queries of what is taking place.

So, what results when at the login screen you execute key combination ctl+alt+F1 ?

[INDENT][INDENT]we find the fault
[/INDENT][/INDENT]

---

### Post by Josease on 2016-06-18
> **Bashing-om said:**
> Josease; OK !

We are fixing the current install .

Can be either a change in authority to access the desktop ..
OR
a graphic's driver either not installed ..or broken.

Again, in small steps to arrive at the fault.
1st step:
can you activate a console interface ?
at the login screen one should be able to activate this console with key combo ctl+alt+F1 .

From this console we have access to the system, and can then make queries of what is taking place.

So, what results when at the login screen you execute key combination ctl+alt+F1 ?
[INDENT][INDENT]we find the fault
[/INDENT]
[/INDENT]


I have not not tried to install ubuntu but I was wrong, so the first instalacción has been corrupted. I will format the hdd and redo the installation. (Thx for patience xD)


This error (No is my image but is same error) [http://i.stack.imgur.com/65dgI.png](http://i.stack.imgur.com/65dgI.png)

---

### Post by Bashing-om on 2016-06-18
Josease; A bit late:

But installing the bootloader to the correct place ..is no big deal either.
IF that were all that is wrong about this present install.

However. a re-install can be a good thing.
[INDENT][INDENT]practice makes perfect
[/INDENT][/INDENT]

---

