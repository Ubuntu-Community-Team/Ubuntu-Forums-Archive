---
title: "Thinkpad T420, Ubuntu 11.04  Fan running all the Time"
date: 2011-05-04
forum: Hardware
---

### Post by robin.nightingale on 2011-05-04
Hi,

I got my Thinkpad T420 with Nvidia Optimus T420 4180W1H and without an OS a few days ago. In the BIOS I selected the integrated graphics adapter and then I installed Ubuntu 11.04. It looks like almost every driver got installed automatically. However, I have the problem that the fan runs all the time. Is that always the case? 

I updated the BIOS from 1.16 to 1.23 but no change.
I found thinkfan, which seems to be a program to control the fan of Thinkpad Laptops, but iam not able to controle the Fanspeed with it.

Can anyone help ?
Thanks

---

### Post by unagimiyagi on 2011-05-04
Same problem here for an x220 running 11.04 ubuntu natty

---

### Post by antskip on 2011-05-04
I have a switchable gpu - in the bios I choose to use only the dedicated gpu...My fan ran constantly until I installed the ATI gpu drivers. Then silence.

---

### Post by robin.nightingale on 2011-05-06
What do you mean with > until I installed the ATI gpu drivers
Waht did you installed and what do you use now ?
cause i would love to get my machine silent.

---

### Post by robin.nightingale on 2011-05-06
I found out that **thinkfan **is not working, because the Packet **/proc/acpi/ibm/thermal** isnt existing anymore for newer thinkpad models. So we need to wait for an update for this (but its not shure if there will be one)

Alternate you can try to install (patch) **Thinkpad Fan Control** on your system.
[http://thinkpad-wiki.org/Thinkpad_Fan_Control]("http://thinkpad-wiki.org/Thinkpad_Fan_Control")

I didnt managed to do so sucesfully but iam stil working on it.
Tell me if you guys gonna make it.

---

### Post by jonathanysp on 2011-05-07
im planning to get a T420 soon, is the fan really noisy when its on all the time?

Also, just wondering, does everything else work nicely out of the box with natty?

---

### Post by antskip on 2011-05-07
> **robin.nightingale said:**
> What do you mean with 
Waht did you installed and what do you use now ?
cause i would love to get my machine silent.
I just installed the proprietary ATI FGLRX graphics driver through "additional drivers" in system settings/control centre.

Everything (except my Epson scanner - need to look into that) worked just great right out of the box. But adding "additional drivers" in ubuntu software centre provides a heap of basic software that most people will want.

---

### Post by kenden on 2011-05-22
> **antskip said:**
> I just installed the proprietary ATI FGLRX graphics driver through "additional drivers" in system settings/control centre.



This does not apply to the Thinkpad T420, there is no ATI card in it.
There can be a Nvidia Optimus NVS 4200M.

---

### Post by mejo on 2011-05-26
i got thinkfan working on my t420:

1. install thinkfan package
2. add kernel module 'coretemp' to /etc/modules
3. load kernel module 'coretemp'
4. add the following three sensor entries to /etc/thinkfan.conf just before the temperature levels:

sensor /sys/devices/platform/coretemp.0/temp1_input
sensor /sys/devices/platform/coretemp.2/temp1_input
sensor /sys/devices/virtual/hwmon/hwmon0/temp1_input

5. add the following to /etc/modprobe.d/thinkfan.conf:

options thinkpad_acpi fan_control=1

6. reload kernel module 'thinkpad_acpi'
7. set START="yes" in /etc/default/thinkfan
8. start thinkfan: /etc/init.d/thinkfan start

9. check whether it works: cat /proc/acpi/ibm/fan

if level has a value between 0 and 7, and changes by times, your thinkfan daemon works.

I found the solution in the thinkpad wiki (only german) at [http://thinkpad-wiki.org/Thinkfan#Ke..._Kernel_2.6.38]("http://thinkpad-wiki.org/Thinkfan#Keine_Funktion_auf_X220.2C_T420.2C_L420_mit_Ubuntu_11.04_.2F_Kernel_2.6.38")

greetings,
 jonas

---

### Post by fraktalek on 2011-06-06
Thanks for the report, @mejo, worked for me like a charm.

---

### Post by monkeyking009 on 2011-07-11
> **mejo said:**
> i got thinkfan working on my t420:

1. install thinkfan package
2. add kernel module 'coretemp' to /etc/modules
3. load kernel module 'coretemp'
4. add the following three sensor entries to /etc/thinkfan.conf just before the temperature levels:

sensor /sys/devices/platform/coretemp.0/temp1_input
sensor /sys/devices/platform/coretemp.2/temp1_input
sensor /sys/devices/virtual/hwmon/hwmon0/temp1_input

5. add the following to /etc/modprobe.d/thinkfan.conf:

options thinkpad_acpi fan_control=1

6. reload kernel module 'thinkpad_acpi'
7. set START="yes" in /etc/default/thinkfan
8. start thinkfan: /etc/init.d/thinkfan start

9. check whether it works: cat /proc/acpi/ibm/fan

if level has a value between 0 and 7, and changes by times, your thinkfan daemon works.

I found the solution in the thinkpad wiki (only german) at [http://thinkpad-wiki.org/Thinkfan#Ke..._Kernel_2.6.38]("http://thinkpad-wiki.org/Thinkfan#Keine_Funktion_auf_X220.2C_T420.2C_L420_mit_Ubuntu_11.04_.2F_Kernel_2.6.38")

greetings,
 jonas

Would you mind explaining how to do step 2: Adding 'coretemp' to /etc/modules?

Cheers,
M

---

### Post by mejo on 2011-07-12
> **monkeyking009 said:**
> Would you mind explaining how to do step 2: Adding 'coretemp' to /etc/modules?
M

Sure. It's very easy. Just add a line with the content 'coretemp' to the textfile /etc/modules. You can do so by using your favourite texteditor, or by executing the following commandline:

```
# echo "coretemp" >> /etc/modules
```

---

### Post by dilettantic on 2011-07-18
@mejo, works nicely!

on T400, coretemp.1 may be needed instead of coretemp.2

---

### Post by raphifix on 2011-08-14
I'm looking at laptops to install Ubuntu on and the t420 seems like a good bet. Besides needing a workaround for the fan and HDAPS, is the t420 a good machine to use Ubuntu (and/or Mint) on?

---

### Post by mejo on 2011-08-14
> **raphifix said:**
> I'm looking at laptops to install Ubuntu on and the t420 seems like a good bet. Besides needing a workaround for the fan and HDAPS, is the t420 a good machine to use Ubuntu (and/or Mint) on?

take a look at [http://ubuntuforums.org/showthread.php?t=1816071](http://ubuntuforums.org/showthread.php?t=1816071) for a first overview of issues with ubuntu on t420 and links to workarounds and fixes.

---

### Post by chonald on 2011-09-23
> **mejo said:**
> i got thinkfan working on my t420:

1. install thinkfan package
2. add kernel module 'coretemp' to /etc/modules
3. load kernel module 'coretemp'
4. add the following three sensor entries to /etc/thinkfan.conf just before the temperature levels:

sensor /sys/devices/platform/coretemp.0/temp1_input
sensor /sys/devices/platform/coretemp.2/temp1_input
sensor /sys/devices/virtual/hwmon/hwmon0/temp1_input

5. add the following to /etc/modprobe.d/thinkfan.conf:

options thinkpad_acpi fan_control=1

6. reload kernel module 'thinkpad_acpi'
7. set START="yes" in /etc/default/thinkfan
8. start thinkfan: /etc/init.d/thinkfan start

9. check whether it works: cat /proc/acpi/ibm/fan

if level has a value between 0 and 7, and changes by times, your thinkfan daemon works.

I found the solution in the thinkpad wiki (only german) at [http://thinkpad-wiki.org/Thinkfan#Ke..._Kernel_2.6.38]("http://thinkpad-wiki.org/Thinkfan#Keine_Funktion_auf_X220.2C_T420.2C_L420_mit_Ubuntu_11.04_.2F_Kernel_2.6.38")

greetings,
 jonas

I was trying to go through this, but I'm thinking I don't have enough expertise.  How would you recommend installing the thinkfan package?  I ran 'sudo apt-get install thinkfan'.  Is this what you meant?

Also, when loading kernel modules (step 3), how do you do this?  I restarted my computer to load this module.

I stopped at number 5 because I didn't have a thinkfan.conf file in /etc/modprobe.d/.

How should I go about this?

The fan does seem to be going all the time.  But I can't be sure, because most of the time it is really quiet, or it gets drowned out by other audio.

Thanks.

---

### Post by mejo on 2011-09-23
> **chonald said:**
> I was trying to go through this, but I'm thinking I don't have enough expertise.  How would you recommend installing the thinkfan package?  I ran 'sudo apt-get install thinkfan'.  Is this what you meant?

Also, when loading kernel modules (step 3), how do you do this?  I restarted my computer to load this module.

I stopped at number 5 because I didn't have a thinkfan.conf file in /etc/modprobe.d/.

How should I go about this?

The fan does seem to be going all the time.  But I can't be sure, because most of the time it is really quiet, or it gets drowned out by other audio.

Thanks.

You need to create the file /etc/modprobe.d/thinkfan.conf.

I'll describe the steps in detail:

1. install thinkfan package:

$ sudo apt-get install thinkfan

2. add kernel module 'coretemp' to /etc/modules

$ sudo sh -c 'echo coretemp >> /etc/modules'

3. load kernel module 'coretemp'

$ sudo modprobe coretemp

4. add the following three sensor entries to /etc/thinkfan.conf just before the temperature levels:

sensor /sys/devices/platform/coretemp.0/temp1_input
sensor /sys/devices/platform/coretemp.2/temp1_input
sensor /sys/devices/virtual/hwmon/hwmon0/temp1_input

[ edit the file /etc/thinkfan.conf with your favourite editor, e.g. 'sudo gedit /etc/thinkfan.conf' ]

5. add the following to /etc/modprobe.d/thinkfan.conf: 'options thinkpad_acpi fan_control=1'

$ sudo sh -c 'echo "options thinkpad_acpi fan_control=1" >> /etc/modprobe.d/thinkfan.conf'

6. reload kernel module 'thinkpad_acpi'

$ sudo modprobe -r thinkpad_acpi
$ sudo modprobe thinkpad_acpi

7. set START="yes" in /etc/default/thinkfan

[ edit the file /etc/default/thinkfan with your favourite editor, e.g. 'sudo gedit /etc/default/thinkfan' ]

8. start thinkfan:

$ sudo /etc/init.d/thinkfan start

9. check whether it works

$ sudo cat /proc/acpi/ibm/fan

if level has a value between 0 and 7, and changes by times, your thinkfan daemon works.

---

### Post by rewyllys on 2011-09-23
@mejo:
Chonald commented: "I stopped at number 5 because I didn't have a thinkfan.conf file in /etc/modprobe.d/."

I encountered the same problem, but I assumed that the reference to subdirectory "modprobe.d" was an error and made the number 5 change to the "thinkfan.conf" file in directory "/etc".  

This seems to have worked for me.

---

### Post by chonald on 2011-09-23
Mejo, thank you very much.  I appreciate it.

One thing before I follow these steps.  Right now the fan isn't running constantly.  I did install the thinkfan package earlier when I first tried this, but I just didn't get through all of the steps.  Is there still need for me to go through the rest of the steps, or has the package somehow set itself up to work?

---

### Post by mejo on 2011-09-23
> **rewyllys said:**
> @mejo:
Chonald commented: "I stopped at number 5 because I didn't have a thinkfan.conf file in /etc/modprobe.d/."

I encountered the same problem, but I assumed that the reference to  subdirectory "modprobe.d" was an error and made the number 5 change to  the "thinkfan.conf" file in directory "/etc".  

This seems to have worked for me.

I wonder why this has worked for you. The file referenced in step five configures the options for the thinkpad_acpi kernel module. This is _not_ the same file as /etc/thinkfan.conf, which configures the options for the thinkfan daemon. The former is kernel level, the latter is userland level.

> **chonald said:**
> Mejo, thank you very much.  I appreciate it.

One thing before I follow these steps.  Right now the fan isn't running constantly.  I did install the thinkfan package earlier when I first tried this, but I just didn't get through all of the steps.  Is there still need for me to go through the rest of the steps, or has the package somehow set itself up to work?

Which version of thinkfan do you have installed? Did you try step 9 to check whether thinkfan works as expected? Monitor the content of /proc/acpi/ibm/fan in different load situations, and see whether it changes. You can check this by executing 'sudo cat  /proc/acpi/ibm/fan' on the console. In case that the value (it's the fan speed level), then your thinkfan already works as expected.

---

### Post by chonald on 2011-09-23
I just opened a bunch of youtube videos, gimp, eclipse, random programs, a movie editor, etc...  And the fan speed did not change from 0.  I'm going to assume this means things aren't setup properly.  So I will go through your steps.

Also, my thinkfan version is 0.7.1.

---

### Post by chonald on 2011-09-23
I went through the instructions and the fan is now running.  I've seen it go from level 3 to level 1.  So it seems to be working.

Anything else?

Thank you for your help.

---

### Post by mejo on 2011-09-24
> **chonald said:**
> I went through the instructions and the fan is now running.  I've seen it go from level 3 to level 1.  So it seems to be working.

Anything else?

Thank you for your help.

You're welcome. Thinkfan is working on your system now. I'm curious though, why your fan wasn't working at all before that. Because level 0 is 'no fan'. But whatever the reason was, now it's working as expected.

---

### Post by coolleonard on 2011-09-24
when i tried the following command....i get the following error. Can any body help me regarding this?

```
# sudo modprobe thinkpad_acpi
FATAL: Error inserting thinkpad_acpi (/lib/modules/2.6.38-11-generic/kernel/drivers/platform/x86/thinkpad_acpi.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```

---

### Post by mejo on 2011-09-24
> **coolleonard said:**
> when i tried the following command....i get the following error. Can any body help me regarding this?

```
# sudo modprobe thinkpad_acpi
FATAL: Error inserting thinkpad_acpi (/lib/modules/2.6.38-11-generic/kernel/drivers/platform/x86/thinkpad_acpi.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```

What's the output in /var/log/dmesg? I guess that you pass a wrong parameter to the module. Please post the output of 'grep -r thinkpad_acpi /etc/modprobe.d/'.

---

### Post by Jeff9 on 2011-09-24
I'm trying to install this on a T61p. Would that make a difference? After I enter sudo echo "coretemp" >> /etc/modules I get back...bash: /etc/modules: Permission denied

Admittedly I am new at this, but any help would be appreciated.

---

### Post by coolleonard on 2011-09-24
> **mejo said:**
> What's the output in /var/log/dmesg? I guess that you pass a wrong parameter to the module. Please post the output of 'grep -r thinkpad_acpi /etc/modprobe.d/'.



The output is
```
$ grep -r thinkpad_acpi /etc/modprobe.d/
/etc/modprobe.d/thinkfan.conf:options thinkpad_acpi fan_control = 1
```

---

### Post by coolleonard on 2011-09-24
Also  while installing the thinkfan I got the following out put:
# apt-get install thinkfan
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  thinkfan
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/33.7 kB of archives.
After this operation, 164 kB of additional disk space will be used.
Selecting previously deselected package thinkfan.
(Reading database ... 161516 files and directories currently installed.)
Unpacking thinkfan (from .../thinkfan_0.7.1-2_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Setting up thinkfan (0.7.1-2) ...
/proc/acpi/ibm/fan: No such file or directory


I guess the file in /proc/acpi/ibm/fan is not created while install.  i don't know why...

---

### Post by Aide9aic on 2011-09-24
Thanks for the tutorial. Working very well on my T410 also.

---

### Post by mejo on 2011-09-24
> **Jeff9 said:**
> I'm trying to install this on a T61p. Would that make a difference? After I enter sudo echo "coretemp" >> /etc/modules I get back...bash: /etc/modules: Permission denied

Admittedly I am new at this, but any help would be appreciated.

Sorry, indeed the command was wrong. 'sudo' gives you root privileges for the command. So the command 'echo 'coretemp'' is executed with root privileges. but the redirection of output to /etc/modules doesn't work as this is done as normal user again. The following should work:

$ sudo sh -c 'echo coretemp >> /etc/modules'

---

### Post by mejo on 2011-09-24
> **coolleonard said:**
> The output is
 ```
$ grep -r thinkpad_acpi /etc/modprobe.d/
 /etc/modprobe.d/thinkfan.conf:options thinkpad_acpi fan_control = 1
```
 
I'm not sure whether this is a problem at all, but I don't have spaces between variable, = and value. In other words, try to change 'fan_control = 1' to 'fan_control=1', and see whether modprobe succeeds afterwards.

> **coolleonard said:**
> Also  while installing the thinkfan I got the following out put:
# apt-get install thinkfan
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  thinkfan
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/33.7 kB of archives.
After this operation, 164 kB of additional disk space will be used.
Selecting previously deselected package thinkfan.
(Reading database ... 161516 files and directories currently installed.)
Unpacking thinkfan (from .../thinkfan_0.7.1-2_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Setting up thinkfan (0.7.1-2) ...
/proc/acpi/ibm/fan: No such file or directory


I guess the file in /proc/acpi/ibm/fan is not created while install.  i don't know why...

/proc/acpi/ibm/fan is created by the kernel module thinkpad_acpi. Thus it's no suprise that you don't have that file. I guess all your problems are related to the fact that loading the kernel module fails.

---

### Post by coolleonard on 2011-09-24
> **mejo said:**
> I'm not sure whether this is a problem at all, but I don't have spaces between variable, = and value. In other words, try to change 'fan_control = 1' to 'fan_control=1', and see whether modprobe succeeds afterwards.



/proc/acpi/ibm/fan is created by the kernel module thinkpad_acpi. Thus it's no suprise that you don't have that file. I guess all your problems are related to the fact that loading the kernel module fails.

After removing spaces I'm still getting the same error on 
# sudo modprobe thinkpad_acpi

---

### Post by mejo on 2011-09-24
> **coolleonard said:**
> After removing spaces I'm still getting the same error on 
# sudo modprobe thinkpad_acpi

ok, so there is another problem. which hardware do you have, btw? is it a t420 or another thinkpad? please do the following:

1. open a console and start the following command to monitor log files:

$ tail -n0 -f /var/log/syslog /var/log/dmesg /var/log/kern.log

2. open a second console and run modprobe in verbose mode:

$  sudo modprobe -v thinkpad_acpi

3. post the output of modprobe both the the console and to the log files here

---

### Post by coolleonard on 2011-09-24
> **mejo said:**
> ok, so there is another problem. which hardware do you have, btw? is it a t420 or another thinkpad? please do the following:

1. open a console and start the following command to monitor log files:

$ tail -n0 -f /var/log/syslog /var/log/dmesg /var/log/kern.log

2. open a second console and run modprobe in verbose mode:

$  sudo modprobe -v thinkpad_acpi

3. post the output of modprobe both the the console and to the log files here

I have T420 with NV4000 graphics

here is the output :
```
 # tail -n0 -f /var/log/syslog /var/log/dmesg /var/log/kern.log
==> /var/log/syslog <==

==> /var/log/dmesg <==

==> /var/log/kern.log <==

==> /var/log/syslog <==
Sep 24 16:15:52 Freeloader kernel: [ 4431.577741] thinkpad_acpi: Unknown parameter `='

==> /var/log/kern.log <==
Sep 24 16:15:52 Freeloader kernel: [ 4431.577741] thinkpad_acpi: Unknown parameter `='

```another output:
```
# sudo modprobe -v thinkpad_acpi
insmod /lib/modules/2.6.38-11-generic/kernel/drivers/platform/x86/thinkpad_acpi.ko fan_control = 1 fan_control=1
FATAL: Error inserting thinkpad_acpi (/lib/modules/2.6.38-11-generic/kernel/drivers/platform/x86/thinkpad_acpi.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```

---

### Post by mejo on 2011-09-24
> **coolleonard said:**
> I have T420 with NV4000 graphics

here is the output :
```
==> /var/log/syslog <==
Sep 24 16:15:52 Freeloader kernel: [ 4431.577741] thinkpad_acpi: Unknown parameter `='

```

another output:
```
# sudo modprobe -v thinkpad_acpi
insmod /lib/modules/2.6.38-11-generic/kernel/drivers/platform/x86/thinkpad_acpi.ko fan_control = 1 fan_control=1
FATAL: Error inserting thinkpad_acpi (/lib/modules/2.6.38-11-generic/kernel/drivers/platform/x86/thinkpad_acpi.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```

Ok, if you take a look at the output of modprobe, then you see, that the fan_control argument is given twice to insmod. once with spaces ('fan_control = 1'), and once without ('fan_control=1').

Now if you take a look at the error log to syslog, it writes: 'Unknown parameter `=''. So I was right, that the parameter with spaces between variable, = and value is wrong. For some reason it is still given to the module as argument. please again post the output of 'grep -r thinkpad_acpi /etc/modprobe.d/'.

---

### Post by coolleonard on 2011-09-24
> **mejo said:**
> Ok, if you take a look at the output of modprobe, then you see, that the fan_control argument is given twice to insmod. once with spaces ('fan_control = 1'), and once without ('fan_control=1').

Now if you take a look at the error log to syslog, it writes: 'Unknown parameter `=''. So I was right, that the parameter with spaces between variable, = and value is wrong. For some reason it is still given to the module as argument. please again post the output of 'grep -r thinkpad_acpi /etc/modprobe.d/'.

Yes it clearly shows the control argument is given twice. Here is the output
```
# grep -r thinkpad_acpi /etc/modprobe.d/
/etc/modprobe.d/thinkfan.conf:options thinkpad_acpi fan_control = 1
/etc/modprobe.d/thinkfan.conf:options thinkpad_acpi fan_control=1

```Could you please tell me how to delete the argument with spaces?

---

### Post by mejo on 2011-09-24
> **coolleonard said:**
> Yes it clearly shows the control argument is given twice. Here is the output
```
# grep -r thinkpad_acpi /etc/modprobe.d/
/etc/modprobe.d/thinkfan.conf:options thinkpad_acpi fan_control = 1
/etc/modprobe.d/thinkfan.conf:options thinkpad_acpi fan_control=1

```Could you please tell me how to delete the argument with spaces?

The easiest and most convenient way is to edit the file /etc/modprobe.d/thinkfan.conf with your favourite editor. In case you don't have a favourite editor yet, I suggest you use gedit, which is installed by default: 'sudo gedit /etc/modprobe.d/thinkfan.conf'. Simply remove the first line (that contains the argument with spaces), save the file and try whether modprobe succeeds now.

---

### Post by coolleonard on 2011-09-24
> **coolleonard said:**
> Yes it clearly shows the control argument is given twice. Here is the output
```
# grep -r thinkpad_acpi /etc/modprobe.d/
/etc/modprobe.d/thinkfan.conf:options thinkpad_acpi fan_control = 1
/etc/modprobe.d/thinkfan.conf:options thinkpad_acpi fan_control=1

```Could you please tell me how to delete the argument with spaces?


I deleted the argument with spaces. Now the command sudo modprobe thinkpad_acpi is working. 
I'll perform the other commands and let you know in case I get stuck.
Thanks for your prompt solutions!

---

### Post by coolleonard on 2011-09-24
The file shows status as disabled. I can't see any changing values for speed with time. 
I already started the thinkfan daemon using the command sudo  /etc/init.d/thinkfan start

```

# sudo cat /proc/acpi/ibm/fan
status:        disabled
speed:        0
level:        0
commands:    level <level> (<level> is 0-7, auto, disengaged, full-speed)
commands:    enable, disable
commands:    watchdog <timeout> (<timeout> is 0 (off), 1-120 (seconds))

```

---

### Post by mejo on 2011-09-24
> **mejo said:**
> The easiest and most convenient way is to edit the file /etc/modprobe.d/thinkfan.conf with your favourite editor. In case you don't have a favourite editor yet, I suggest you use gedit, which is installed by default: 'sudo gedit /etc/modprobe.d/thinkfan.conf'. Simply remove the first line (that contains the argument with spaces), save the file and try whether modprobe succeeds now.

> **coolleonard said:**
> I deleted the argument with spaces. Now the command sudo modprobe thinkpad_acpi is working. 
I'll perform the other commands and let you know in case I get stuck.
Thanks for your prompt solutions!

> **coolleonard said:**
> The file shows status as disabled. I can't see any changing values for speed with time. 
I already started the thinkfan daemon using the command sudo  /etc/init.d/thinkfan start

```

# sudo cat /proc/acpi/ibm/fan
status:        disabled
speed:        0
level:        0
commands:    level <level> (<level> is 0-7, auto, disengaged, full-speed)
commands:    enable, disable
commands:    watchdog <timeout> (<timeout> is 0 (off), 1-120 (seconds))

```

Try to enable thinkfan with the following command:

$ sudo sh -c 'echo enable > /proc/acpi/ibm/fan'

Again: which hardware do you use? Is this a T420 or another thinkpad?

---

### Post by mejo on 2011-09-24
> **coolleonard said:**
> The file shows status as disabled. I can't see any changing values for speed with time. 
I already started the thinkfan daemon using the command sudo  /etc/init.d/thinkfan start

```

# sudo cat /proc/acpi/ibm/fan
status:        disabled
speed:        0
level:        0
commands:    level <level> (<level> is 0-7, auto, disengaged, full-speed)
commands:    enable, disable
commands:    watchdog <timeout> (<timeout> is 0 (off), 1-120 (seconds))

```

Do you have thinkfan enabled in /etc/default/thinkfan?

---

### Post by coolleonard on 2011-09-24
> **mejo said:**
> Do you have thinkfan enabled in /etc/default/thinkfan?

here is the content of /etc/default/thinkfan
```

# Should thinkfan be started automatically on boot?
# Only say "yes" when you know what you are doing, have configured
# thinkfan correctly for *YOUR* machine and loaded thinkpad_acpi
# with fan_control=1 (if you have a ThinkPad).
START="yes"

# Additional startup parameters
DAEMON_ARGS="-q"

```after running the command  : # sudo sh -c 'echo enable>/proc/acpi/ibm/fan'
I run the following command each with some time intervals
# sudo cat /proc/acpi/ibm/fan
status:        enabled
speed:        3568
level:        auto
commands:    level <level> (<level> is 0-7, auto, disengaged, full-speed)
commands:    enable, disable
commands:    watchdog <timeout> (<timeout> is 0 (off), 1-120 (seconds))

# sudo cat /proc/acpi/ibm/fan
status:        disabled
speed:        1784
level:        0
commands:    level <level> (<level> is 0-7, auto, disengaged, full-speed)
commands:    enable, disable
commands:    watchdog <timeout> (<timeout> is 0 (off), 1-120 (seconds))

# sudo cat /proc/acpi/ibm/fan
status:        disabled
speed:        0
level:        0
commands:    level <level> (<level> is 0-7, auto, disengaged, full-speed)
commands:    enable, disable
commands:    watchdog <timeout> (<timeout> is 0 (off), 1-120 (seconds))

# sudo cat /proc/acpi/ibm/fan
status:        disabled
speed:        0
level:        0
commands:    level <level> (<level> is 0-7, auto, disengaged, full-speed)
commands:    enable, disable
commands:    watchdog <timeout> (<timeout> is 0 (off), 1-120 (seconds))

# sudo cat /proc/acpi/ibm/fan
status:        disabled
speed:        0
level:        0
commands:    level <level> (<level> is 0-7, auto, disengaged, full-speed)
commands:    enable, disable
commands:    watchdog <timeout> (<timeout> is 0 (off), 1-120 (seconds)

# sudo cat /proc/acpi/ibm/fan
status:        enabled
speed:        1978
level:        1
commands:    level <level> (<level> is 0-7, auto, disengaged, full-speed)
commands:    enable, disable
commands:    watchdog <timeout> (<timeout> is 0 (off), 1-120 (seconds))

# sudo cat /proc/acpi/ibm/fan
status:        enabled
speed:        1975
level:        1
commands:    level <level> (<level> is 0-7, auto, disengaged, full-speed)
commands:    enable, disable
commands:    watchdog <timeout> (<timeout> is 0 (off), 1-120 (seconds))

I guess its working now. what's the  significance of commands? are they come like this only or with some values?
```

commands:    level <level> (<level> is 0-7, auto, disengaged, full-speed)
commands:    enable, disable
commands:    watchdog <timeout> (<timeout> is 0 (off), 1-120 (seconds))

```

---

### Post by mejo on 2011-09-25
> **coolleonard said:**
> here is the content of /etc/default/thinkfan
```

# Should thinkfan be started automatically on boot?
# Only say "yes" when you know what you are doing, have configured
# thinkfan correctly for *YOUR* machine and loaded thinkpad_acpi
# with fan_control=1 (if you have a ThinkPad).
START="yes"

```

You can also check whether thinkfan is running by checking the list of processes: 'ps -ef | grep thinkfan'. If there is a process with /usr/sbin/thinkfan as command, it is running.

> **coolleonard said:**
> 
after running the command  : # sudo sh -c 'echo enable>/proc/acpi/ibm/fan'
I run the following command each with some time intervals
# sudo cat /proc/acpi/ibm/fan
status:        enabled
speed:        3568
level:        auto
commands:    level <level> (<level> is 0-7, auto, disengaged, full-speed)
commands:    enable, disable
commands:    watchdog <timeout> (<timeout> is 0 (off), 1-120 (seconds))

# sudo cat /proc/acpi/ibm/fan
status:        disabled
speed:        1784
level:        0
commands:    level <level> (<level> is 0-7, auto, disengaged, full-speed)
commands:    enable, disable
commands:    watchdog <timeout> (<timeout> is 0 (off), 1-120 (seconds))

# sudo cat /proc/acpi/ibm/fan
status:        disabled
speed:        0
level:        0
commands:    level <level> (<level> is 0-7, auto, disengaged, full-speed)
commands:    enable, disable
commands:    watchdog <timeout> (<timeout> is 0 (off), 1-120 (seconds))

# sudo cat /proc/acpi/ibm/fan
status:        disabled
speed:        0
level:        0
commands:    level <level> (<level> is 0-7, auto, disengaged, full-speed)
commands:    enable, disable
commands:    watchdog <timeout> (<timeout> is 0 (off), 1-120 (seconds))

# sudo cat /proc/acpi/ibm/fan
status:        disabled
speed:        0
level:        0
commands:    level <level> (<level> is 0-7, auto, disengaged, full-speed)
commands:    enable, disable
commands:    watchdog <timeout> (<timeout> is 0 (off), 1-120 (seconds)

# sudo cat /proc/acpi/ibm/fan
status:        enabled
speed:        1978
level:        1
commands:    level <level> (<level> is 0-7, auto, disengaged, full-speed)
commands:    enable, disable
commands:    watchdog <timeout> (<timeout> is 0 (off), 1-120 (seconds))

# sudo cat /proc/acpi/ibm/fan
status:        enabled
speed:        1975
level:        1
commands:    level <level> (<level> is 0-7, auto, disengaged, full-speed)
commands:    enable, disable
commands:    watchdog <timeout> (<timeout> is 0 (off), 1-120 (seconds))

I guess its working now. what's the  significance of commands? are they come like this only or with some values?
```

commands:    level <level> (<level> is 0-7, auto, disengaged, full-speed)
commands:    enable, disable
commands:    watchdog <timeout> (<timeout> is 0 (off), 1-120 (seconds))

```

Indeed, it is working. 'disabled' indicates that the fan is not running at all at the moment. thinkfan will enable it once temperature rises.

You're  correct, the syntax to control the fan directly is written above. Just echo the command (syntax above) to /proc/acpi/ibm/fan. But this is not required at all, as thinkfan takes care of the fan control.

To summarize: thinkfan is now working as expected on your system.

---

### Post by 1keith1 on 2011-10-07
Hi, new user here, and very new user of linux. Maybe I should have created a new thread for this but support here seemed relevant enough.

I am actually running [Elementary OS]("elementaryos.org") but it is based on Ubuntu 10.10 so things should be pretty similar.

Well I've installed thinkfan, and attempted to follow instructions, but I seem to be missing the file thinkfan.conf within /etc/modprobe.d/ so I cannot complete step 5. Attempting to do so gives:

$ sudo echo 'options thinkpad_acpi fan_control=1' >> /etc/modprobe.d/thinkfan.conf
bash: /etc/modprobe.d/thinkfan.conf: Permission denied

My computer is a Thinkpad T420, and I am again new to linux, so my understanding is very little. So far this is my only gripe, everything else has been great. 

Thanks in advance.

---

### Post by mejo on 2011-10-07
> **1keith1 said:**
> Hi, new user here, and very new user of linux. Maybe I should have created a new thread for this but support here seemed relevant enough.

I am actually running [Elementary OS]("http://elementaryos.org") but it is based on Ubuntu 10.10 so things should be pretty similar.

Well I've installed thinkfan, and attempted to follow instructions, but I seem to be missing the file thinkfan.conf within /etc/modprobe.d/ so I cannot complete step 5. Attempting to do so gives:

$ sudo echo 'options thinkpad_acpi fan_control=1' >> /etc/modprobe.d/thinkfan.conf
bash: /etc/modprobe.d/thinkfan.conf: Permission denied

My computer is a Thinkpad T420, and I am again new to linux, so my understanding is very little. So far this is my only gripe, everything else has been great. 

Thanks in advance.

Yes, the command was wrong. Sudo executes a command with superuser privileges. The command above executed 'echo' with superuser privileges, but the redirection (>>) to file /etc/modprobe.d/thinkfan.conf is still done as normal user, who doesn't have required privileges.

The following command is correct:

```
$ sudo sh -c 'echo "options thinkpad_acpi fan_control=1" >> /etc/modprobe.d/thinkfan.conf'
```

I also fixed this in the step-by-step tutorial earlier in the thread. Thanks for the hint.

---

### Post by 1keith1 on 2011-10-07
Thanks for the quick reply, I redid the steps from 5 and above just now, and when I get to step 8 this is what happens:


```
$ sudo /etc/init.d/thinkfan start

/etc/thinkfan.conf:55:options thinkpad_acpi fan_control=1

Syntax error.
```

---

### Post by mejo on 2011-10-08
> **1keith1 said:**
> Thanks for the quick reply, I redid the steps from 5 and above just now, and when I get to step 8 this is what happens:


```
$ sudo /etc/init.d/thinkfan start

/etc/thinkfan.conf:55:options thinkpad_acpi fan_control=1

Syntax error.
```

It seems like you added the line 'options thinkpad_acpi fan_control=1' to /etc/thinkfan.conf instead of /etc/modprobe.d/thinkfan.conf. Both files have different meanings. /etc/thinkfan.conf is the configuration file for the thinkfan userspace daemon. /etc/modprobe.d/thinkfan.conf is a configuration file for linux kernel modules. it contains the information, that the kernel module 'thinkpad_acpi' should be loaded with the parameter 'fan_control=1'.

I suggest that you open both files with an editor (e.g. gedit) and modify them manually. You need to open both files with superuser privileges: '$ sudo gedit /etc/thinkfan.conf' and '$ sudo gedit /etc/modprobe.d/thinkfan.conf'.

Remove the the line 'options thinkpad_acpi fan_control=1' from /etc/thinkfan.conf, and make sure that it exists in /etc/modprobe.d/thinkfan.conf.

---

### Post by 1keith1 on 2011-10-08
Okay, it seems to be working, the fan still seems pretty loud though, even though level always says 0.

```
$ sudo cat /proc//acpi/ibm/fan
[sudo] password for keith: 
status:		disabled
speed:		2348
level:		0
commands:	level <level> (<level> is 0-7, auto, disengaged, full-speed)
commands:	enable, disable
commands:	watchdog <timeout> (<timeout> is 0 (off), 1-120 (seconds))

```

Heres how the bottom of my thinkfan.conf in /etc/ looks, did I set it up right?
```
# I use this on my T61p:
#sensor /proc/acpi/ibm/thermal (0, 10, 15, 2, 10, 5, 0, 3, 0, 3)

sensor /sys/devices/platform/coretemp.0/temp1_input
sensor /sys/devices/platform/coretemp.2/temp1_input
sensor /sys/devices/virtual/hwmon/hwmon0/temp1_input

(0,	0,	55)
(1,	48,	60)
(2,	50,	61)
(3,	52,	63)
(4,	56,	65)
(5,	59,	66)
(7,	63,	32767)[CODE]
```[/CODE]

---

### Post by mejo on 2011-10-08
> **1keith1 said:**
> Okay, it seems to be working, the fan still seems pretty loud though, even though level always says 0.

level 0 means that the fan is not running at all. are you sure that it's the fan that makes the noise?

> **1keith1 said:**
>  Heres how the bottom of my thinkfan.conf in /etc/ looks, did I set it up right?

Yes, that's correct. It's exactly the same as in my /etc/thinkfan.conf. Which Thinkpad do you use? Is it a T420?

---

### Post by 1keith1 on 2011-10-08
Yes it is a T420, and thinking more it really may be the Hard drive I hear. I was running an SSD in it, but it just died so I had to swap it out for a hard drive, maybe I'm not used to it. I just thought the fan was running because it says something like 2348 by speed which seems high, but as long as its working I am happy.

---

### Post by mejo on 2011-10-08
> **1keith1 said:**
> Yes it is a T420, and thinking more it really may be the Hard drive I hear. I was running an SSD in it, but it just died so I had to swap it out for a hard drive, maybe I'm not used to it. I just thought the fan was running because it says something like 2348 by speed which seems high, but as long as its working I am happy.

yes speed of 2348 is not level 0. I guess that it was still spinning and level was just decreased. you should keep an eye on the level and speed of the fan. in case it changes frequently, and you see a coherency between level and speed changes, then it should work.

---

### Post by JurB on 2011-10-22
I'm trying to get thinkfan to work on my T420 running 11.10.
I've worked my way trough every step, but when i try to start thinkfan i get: ```
/sys/devices/platform/coretemp.2/temp1_input: No such file or directory

```
sudo cat /proc/acpi/ibm/fan gives me:
```
status:		enabled
speed:		3221
level:		auto
commands:	level <level> (<level> is 0-7, auto, disengaged, full-speed)
commands:	enable, disable
commands:	watchdog <timeout> (<timeout> is 0 (off), 1-120 (seconds))

```

a little help please

---

### Post by mejo on 2011-10-22
> **JurB said:**
> I'm trying to get thinkfan to work on my T420 running 11.10.
I've worked my way trough every step, but when i try to start thinkfan i get: ```
/sys/devices/platform/coretemp.2/temp1_input: No such file or directory

```

The path to temperature sensors changed with new Oneiric (11.10) kernel. See [this post]("http://ubuntuforums.org/showthread.php?p=11353524#post11353524"), especially the following subitem:

> **mejo said:**
> 

[LIST]
[*]While the auto modus for the fan seems to work much better in  Oneiric, thinkfan didn't run after the upgrade. This is due to changed  paths to temperature sensors. For me the coretemp paths changed from  /sys/devices/platform/coretemp.X/temp1_input to  /sys/devices/platform/coretemp.0/tempX_input, X being ascending diggits.
[/LIST]

 
In other words, I needed to change the sensors in /etc/thinkfan.conf to the following:

```
sensor /sys/devices/platform/coretemp.0/temp1_input
sensor /sys/devices/platform/coretemp.0/temp2_input
sensor /sys/devices/platform/coretemp.0/temp3_input
sensor /sys/devices/virtual/hwmon/hwmon0/temp1_input

```

---

### Post by JurB on 2011-10-23
Thank you, that did the trick!

---

### Post by Astronaut356 on 2011-11-13
> **mejo said:**
> i got thinkfan working on my t420:

1. install thinkfan package
2. add kernel module 'coretemp' to /etc/modules
3. load kernel module 'coretemp'
4. add the following three sensor entries to /etc/thinkfan.conf just before the temperature levels:

sensor /sys/devices/platform/coretemp.0/temp1_input
sensor /sys/devices/platform/coretemp.2/temp1_input
sensor /sys/devices/virtual/hwmon/hwmon0/temp1_input

5. add the following to /etc/modprobe.d/thinkfan.conf:

options thinkpad_acpi fan_control=1

6. reload kernel module 'thinkpad_acpi'
7. set START="yes" in /etc/default/thinkfan
8. start thinkfan: /etc/init.d/thinkfan start

9. check whether it works: cat /proc/acpi/ibm/fan

if level has a value between 0 and 7, and changes by times, your thinkfan daemon works.

I found the solution in the thinkpad wiki (only german) at [http://thinkpad-wiki.org/Thinkfan#Ke..._Kernel_2.6.38]("http://thinkpad-wiki.org/Thinkfan#Keine_Funktion_auf_X220.2C_T420.2C_L420_mit_Ubuntu_11.04_.2F_Kernel_2.6.38")

greetings,
 jonas


Where do you get the thinkfan package? I have a T420s coming and I want to install 11.10 64 bit. Can you post a step by step for a newbie?

---

### Post by mejo on 2011-11-13
> **Astronaut356 said:**
> Where do you get the thinkfan package? I have a T420s coming and I want to install 11.10 64 bit. Can you post a step by step for a newbie?

See the following post for a step-by-step tutorial:
[http://ubuntuforums.org/showpost.php?p=11277718&postcount=17](http://ubuntuforums.org/showpost.php?p=11277718&postcount=17)

all lines starting with $ are commands to be executed in a terminal. you mustn't type the $, it's just there to indicate it's a commandline.

---

### Post by Astronaut356 on 2011-11-13
Thanks! I'll give it a try as soon as Lenovo delvers the laptop.

---

### Post by HankB on 2011-11-20
mejo,
Many thanks for your help with this. For reasons I do not understand, my fan started making a lot of noise as if it was running away. (RPMs reported about 3000.) I went through the process and it seems to be working fine now.

I also had to use coretemp.1 instead of coretemp.2 in /etc/thinkfan.conf.

---

### Post by keithpeter on 2011-12-04
Hello All

Just to say the howto here works with T60 as well, but the thinkfan.conf file ended up looking like this...

```
sensor /sys/devices/platform/coretemp.0/temp2_input
sensor /sys/devices/platform/coretemp.0/temp3_input
sensor /sys/devices/virtual/hwmon/hwmon0/temp1_input
sensor /sys/devices/virtual/hwmon/hwmon0/temp2_input
(0,	0,	55)
(1,	48,	60)
(2,	50,	61)
(3,	52,	63)
(4,	56,	65)
(5,	59,	66)
(7,	63,	32767)
```

The T60 hasn't melted yet and is running a lot quieter. Any T60 owners who have a more considered thinkfan.conf please let me know!

---

### Post by elindiano on 2012-01-09
Hi guys and girls,

I've followed the instructions here and everything and still my fan is going crazy running 11.04 on my t420. However the fan does drop to the wished values and runs softer until I reboot eventhough I've set it to start with the "YES" value. Anybody got any additional inputs?

I really like my t420 and ubuntu. Don't want to go back to windows.

Cheers,

elindiano

---

### Post by yaronf on 2012-01-22
Hi Mejo,

before I permanently enable thinkfan on my T420: the conf file is very adamant that you need to specify a bias value so that the fan starts way before the hard drive reaches 55C. But I'm not sure which of the 4 sensors  is the HD, and what is the syntax for the bias (I only see one value when reading each sensor, not 3). Thanks!

---

### Post by donniezazen on 2012-04-13
Thinkfan 0.8 Alpha2 has been released with a new complex configuration. Has anyone set it up yet?

---

### Post by jensoko on 2012-05-02
I have a T60p running 11.10 kubuntu. Mejo, many thanks for the step-by-step tutorial--worked like a charm, once I made keithpeter's adjustment for my T60. Keithpeter, thank you so much for this adjustment. My fan is running at level 5. Although my temps still look a little high on the monitor plasmoid because I'm too timid to change them, at least I know my fan is working and can be tweaked.

> **keithpeter said:**
> Hello All

Just to say the howto here works with T60 as well, but the thinkfan.conf file ended up looking like this...

```
sensor /sys/devices/platform/coretemp.0/temp2_input
sensor /sys/devices/platform/coretemp.0/temp3_input
sensor /sys/devices/virtual/hwmon/hwmon0/temp1_input
sensor /sys/devices/virtual/hwmon/hwmon0/temp2_input
(0,	0,	55)
(1,	48,	60)
(2,	50,	61)
(3,	52,	63)
(4,	56,	65)
(5,	59,	66)
(7,	63,	32767)
```

The T60 hasn't melted yet and is running a lot quieter. Any T60 owners who have a more considered thinkfan.conf please let me know!

---

### Post by donniezazen on 2012-05-02
> **jensoko said:**
> I have a T60p running 11.10 kubuntu. Mejo, many thanks for the step-by-step tutorial--worked like a charm, once I made keithpeter's adjustment for my T60. Keithpeter, thank you so much for this adjustment. My fan is running at level 5. Although my temps still look a little high on the monitor plasmoid because I'm too timid to change them, at least I know my fan is working and can be tweaked.

Have you used [Ubuntu Kernel Power Saving Tweaks]("https://wiki.ubuntu.com/Kernel/PowerManagement/PowerSavingTweaks") and if you have Nvidia Optimus you will get better battery life and low power comsumption with [Bumblebee]("https://wiki.ubuntu.com/Bumblebee")? This will help you lower your temperature and consequently fan speed.

---

### Post by cenaar on 2012-05-02
Thanks to mejo for the great guide! Now the fan speed on my T420 at least varies over time. However... it peaks like crazy. I have tried different settings, these are the ones I am using right now:


```

sensor /sys/devices/platform/coretemp.0/temp1_input
sensor /sys/devices/platform/coretemp.0/temp2_input
sensor /sys/devices/platform/coretemp.0/temp3_input
sensor /sys/devices/virtual/hwmon/hwmon0/temp1_input


(0,    0,    30)
(1,    50,    80)
(2,    75,    87)
(3,    78,    89)
(4,    80,    91)
(5,    82,    93)
(7,    70,    32767)

```I added these little different temperatures because I wanted the fan to run for a while on level 1 before jumping up to level 7. But it does not work - the fan still jumps from 0 to 7 and then back to 0 again. I have a feeling that the problem lies in the sensors that we all now use. Is anyone actually certain that all of them should be in that list? Or that the numbers used as temperatures are actually temperatures in celsius? When I look in sys/devices/platform/coretemp.0 there is a list of files: 

```

driver    subsystem         temp1_max         temp2_max         temp3_max
hwmon     temp1_crit        temp2_crit        temp3_crit        uevent
modalias  temp1_crit_alarm  temp2_crit_alarm  temp3_crit_alarm
name      temp1_input       temp2_input       temp3_input
power     temp1_label       temp2_label       temp3_label

```and if I check what's in the critical temperatures 

```
$ cat temp*_crit
100000
100000
100000

```Are we using the right formats for the temperatures?

I have no idea what I am doing.

---

### Post by donniezazen on 2012-05-02
@Cennar

The problem is with simple configuration. An alpha version of Thinkfan, that is 0.8, uses complex configuration which checks individual temperature for each sensor. For example hard drive will blow up at 50. But it does not take account for it at the moment. And even if temp jumps up to 80 and then back to 45, the fan will follow it instead of gradual up and down. I have noticed that Windows take it easy between 50-60C unlike Linux.

Here is an example of complex configuration.

```
######################################################################
# thinkfan 0.8 example config file
# ================================
#
# ATTENTION: There is only very basic sanity checking on the configuration.
# That means you can set your temperature limits as insane as you like. You
# can do anything stupid, e.g. turn off your fan when your CPU reaches 70°C.
#
# That's why this program is called thinkfan: You gotta THINK about your FAN!
#
######################################################################
#
# This file shows how to use sensor-specific temperature limits.
# First of all, you need to specify temperature inputs. On a Thinkpad, you can
# just use:
#
sensor /proc/acpi/ibm/thermal  # provides us with 16 temperature inputs

#
# On other systems, you have to specify a file in /sys/class/hwmon for each
# sensor you want to use. They are numbered in their order of appearance.
# For example:
# sensor /sys/class/hwmon5/temp2_input           #1
# sensor /sys/class/hwmon0/device/temp3_input    #2
# ...
#

#
# Next we specify the fan we want to use. On a Thinkpad, this is:
#
fan /proc/acpi/ibm/fan

#
# On anything other than a Thinkpad you'll probably use some PWM control file
# in /sys/class/hwmon. Remember that fan levels range from 0 to 255 and that
# they're just a number, not including the word "level" as seen below.
#

#
# Then you need to specify the temperature limits for each of the sensors.
# A dot means that the corresponding sensor should be ignored. The length of the
# UPPER and LOWER limits must be the same as the number of temperatures. In this
# example, /proc/acpi/ibm/thermal contains 16 sensors (on older thinkpads,
# there may be only 8), some of which are unused (hence the dots).
# A sysfs temperature input always contains only one sensor, so if you specify
# 5 sysfs files above, the length of your limits must be 5, too.
#
# I've come up with these preliminary settings for my Thinkpad T61p. They probably
# don't make sense for anything else, so you most definitely have to work
# something out for yourself.
#
# Sensor count:
#    1  2  3  4  5  6  7  8  9  10 11 12 13 14 15 16
######################################################
{ "level 0"                                               # the fan level
    (0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0)      # LOWER limit
    (54 42 42 54 42 .  42 .  42 46 54 .  .  .  .  .)      # UPPER limit
}

{ "level 1"
    (46 39 39 48 39 .  39 .  41 44 46 .  .  .  .  .)
    (58 45 45 60 45 .  45 .  45 47 56 .  .  .  .  .)
}

{ "level 3"
    (52 43 43 57 43 .  43 .  43 45 51 .  .  .  .  .)
    (62 48 48 67 48 .  48 .  48 48 57 .  .  .  .  .)
}

{ "level 5"
    (56 46 46 65 46 .  46 .  46 46 52 .  .  .  .  .)
    (66 49 49 69 49 .  49 .  49 49 58 .  .  .  .  .)
}

{ "level 7"
    (63 47 47 67 47 .  47 .  47 47 50 .  .  .  .  .)
    (73 55 55 83 60 .  60 .  60 60 64 .  .  .  .  .)
}

{ "level disengaged" # nice idea: "level auto" can also be used.
    (69 50 50 75 55 .  55 .  55 55 55 .  .  .  .  .)
    (99 99 99 99 99 .  99 .  99 99 99 .  .  .  .  .)
}

```

---

### Post by cenaar on 2012-05-03
> **donniezazen said:**
> @Cennar

The problem is with simple configuration. An alpha version of Thinkfan, that is 0.8, uses complex configuration which checks individual temperature for each sensor. For example hard drive will blow up at 50. But it does not take account for it at the moment. And even if temp jumps up to 80 and then back to 45, the fan will follow it instead of gradual up and down. I have noticed that Windows take it easy between 50-60C unlike Linux.

Here is an example of complex configuration.


I thought I would give the 0.8 version a try. **All I did was the first step in the Thinkfan 0.8 README**, like so:
```

..
# make CFLAGS="-O3"
..
```And then I just wanted to check the fan, so I ran ```
sudo cat /proc/acpi/ibm/fan
``` which produced ```
status:        enabled
speed:        3238
level:        auto
commands:    level <level> (<level> is 0-7, auto, disengaged, full-speed)
commands:    enable, disable
commands:    watchdog <timeout> (<timeout> is 0 (off), 1-120 (seconds))
```...and now the fan seems much more stable in fan speed, i.e. it doesn't jump back and forth between levels 0 and 7. I did not edit [FONT=Courier New]/etc/thinkfan.conf[/FONT].
Funny.

---

### Post by donniezazen on 2012-05-03
> **cenaar said:**
> I thought I would give the 0.8 version a try. **All I did was the first step in the Thinkfan 0.8 README**, like so:
```

..
# make CFLAGS="-O3"
..
```And then I just wanted to check the fan, so I ran ```
sudo cat /proc/acpi/ibm/fan
``` which produced ```
status:        enabled
speed:        3238
level:        auto
commands:    level <level> (<level> is 0-7, auto, disengaged, full-speed)
commands:    enable, disable
commands:    watchdog <timeout> (<timeout> is 0 (off), 1-120 (seconds))
```...and now the fan seems much more stable in fan speed, i.e. it doesn't jump back and forth between levels 0 and 7. I did not edit [FONT=Courier New]/etc/thinkfan.conf[/FONT].
Funny.

level - auto means it's constantly running at 3500RPM irrespective of temperature. No configuration file is included in 0.8 version as far as I know.

---

### Post by cenaar on 2012-05-03
> **donniezazen said:**
> level - auto means it's constantly running at 3500RPM irrespective of temperature. No configuration file is included in 0.8 version as far as I know.

Hm... not sure. Right now it is running at 3557, but then I have had it on for a while. When I wrote my previous post I saw the fan at ~1900 as well... Argh, so I have to go back to monitoring the fan speed. Oh well. Thanks for pointing it out, though!

---

### Post by donniezazen on 2012-05-03
> **cenaar said:**
> Hm... not sure. Right now it is running at 3557, but then I have had it on for a while. When I wrote my previous post I saw the fan at ~1900 as well... Argh, so I have to go back to monitoring the fan speed. Oh well. Thanks for pointing it out, though!

Try this.
```

sudo thinkfan stop

sudo thinkfan -n

```
The second command will give you both temp and fan speed.

---

### Post by cenaar on 2012-05-07
> **donniezazen said:**
> Try this.
```

sudo thinkfan stop

sudo thinkfan -n

```The second command will give you both temp and fan speed.


OK, this is what I got:

```
$ sudo thinkfan stop

LOWER limit doesn't overlap with previous UPPER limit.
/etc/thinkfan.conf:50:(1,    50,    80)

LOWER limit doesn't overlap with previous UPPER limit.
Refusing to run without usable config file. Please read AND UNDERSTAND the documentation!


$ sudo thinkfan -n

LOWER limit doesn't overlap with previous UPPER limit.
/etc/thinkfan.conf:50:(1,    50,    80)

LOWER limit doesn't overlap with previous UPPER limit.
Refusing to run without usable config file. Please read AND UNDERSTAND the documentation!


```"Please read AND UNDERSTAND the documentation!" -- I guess I deserved that :-D

Any ideas on what to do next? I feel a bit sick of this so I might keep going with the "auto" config, unless you think it is a bad idea...

Edit: I purged the thinkfan installation, because I was worried it might be the cause of recent system freezes (nothing works, not even mouse, and I have had to hard restart). Now I am worried that I've been configuring this the wrong way all along. Apparently the T420 can overheat and the "auto" setting is not sufficient from stopping it to overheat (it does not run at the fan's maximum possible speed: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/751689](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/751689)). This is my work PC so I have to make some time in the future to set up thinkfan properly. Until then, I will monitor this thread.

---

### Post by donniezazen on 2012-05-07
Find your sensors using the command.

```
find /sys/devices -type f -name "temp*_input"
```

Add sensor in front of them like

```
sensor /sys/devices/platform/coretemp.0/temp1_input
sensor /sys/devices/platform/coretemp.2/temp1_input
sensor /sys/devices/virtual/hwmon/hwmon0/temp1_input
```

This is the default configuration.

```
######################################################################
# thinkfan 0.7 example config file
# ================================
#
# ATTENTION: There is only very basic sanity checking on the configuration.
# That means you can set your temperature limits as insane as you like. You
# can do anything stupid, e.g. turn off your fan when your CPU reaches 70°C.
#
# That's why this program is called THINKfan: You gotta think for yourself.
#
######################################################################
#
# IBM/Lenovo Thinkpads (thinkpad_acpi, /proc/acpi/ibm)
# ====================================================
#
# IMPORTANT:
#
# To keep your HD from overheating, you have to specify a correction value for
# the sensor that has the HD's temperature. You need to do this because
# thinkfan uses only the highest temperature it can find in the system, and
# that'll most likely never be your HD, as most HDs are already out of spec
# when they reach 55 °C.
# Correction values are applied from left to right in the same order as the
# temperatures are read from the file.
#
# For example:
# sensor /proc/acpi/ibm/thermal (0, 0, 10)
# will add a fixed value of 10 °C the 3rd value read from that file. Check out
# http://www.thinkwiki.org/wiki/Thermal_Sensors to find out how much you may
# want to add to certain temperatures.

#  Syntax:
#  (LEVEL, LOW, HIGH)
#  LEVEL is the fan level to use (0-7 with thinkpad_acpi)
#  LOW is the temperature at which to step down to the previous level
#  HIGH is the temperature at which to step up to the next level
#  All numbers are integers.
#

# I use this on my T61p:
#sensor /proc/acpi/ibm/thermal (0, 10, 15, 2, 10, 5, 0, 3, 0, 3)

**ADD YOUR SENSORS HERE**

(0,	0,	55)
(1,	48,	60)
(2,	50,	61)
(3,	52,	63)
(4,	56,	65)
(5,	59,	66)
(7,	63,	32767)


```

---

### Post by AllWires on 2012-05-08
Deleted message

---

### Post by Sicadastra on 2012-08-22
> **mejo said:**
> level 0 means that the fan is not running at all. are you sure that it's the fan that makes the noise?



Yes, that's correct. It's exactly the same as in my /etc/thinkfan.conf. Which Thinkpad do you use? Is it a T420?

Hello @mejo, I hope it's all right to ask in this thread despite it nearly being a year old. I have a ThinkPad R61i running on 12.04 64-bit. I carefully followed your steps without any error AFAIK that popped on the terminal, but I have to ask if what I added on ```
/etc/thinkfan.conf
``` is correct?

```
# I use this on my T61p:
#sensor /proc/acpi/ibm/thermal (0, 10, 15, 2, 10, 5, 0, 3, 0, 3)

sensor /sys/devices/platform/coretemp.0/temp1_input
sensor /sys/devices/platform/coretemp.2/temp1_input
sensor /sys/devices/virtual/hwmon/hwmon0/temp1_input

(0,    0,    55)
(1,    48,    60)
(2,    50,    61)
(3,    52,    63)
(4,    56,    65)
(5,    59,    66)
(7,    63,    32767)
```I added the same 3 sensor lines even if I'm using an R61i and not T420. Is that correct? Because if I enter the command ```
sudo find /sys/devices -type f -name "temp*_input"
``` I find more than 3 sensors:

```
sensor /sys/devices/platform/coretemp.0/temp2_input
sensor /sys/devices/platform/coretemp.0/temp3_input
sensor /sys/devices/platform/thinkpad_hwmon/temp9_input
sensor /sys/devices/platform/thinkpad_hwmon/temp10_input
sensor /sys/devices/platform/thinkpad_hwmon/temp11_input
sensor /sys/devices/platform/thinkpad_hwmon/temp12_input
sensor /sys/devices/platform/thinkpad_hwmon/temp13_input
sensor /sys/devices/platform/thinkpad_hwmon/temp14_input
sensor /sys/devices/platform/thinkpad_hwmon/temp15_input
sensor /sys/devices/platform/thinkpad_hwmon/temp16_input
sensor /sys/devices/platform/thinkpad_hwmon/temp1_input
sensor /sys/devices/platform/thinkpad_hwmon/temp2_input
sensor /sys/devices/platform/thinkpad_hwmon/temp3_input
sensor /sys/devices/platform/thinkpad_hwmon/temp4_input
sensor /sys/devices/platform/thinkpad_hwmon/temp5_input
sensor /sys/devices/platform/thinkpad_hwmon/temp6_input
sensor /sys/devices/platform/thinkpad_hwmon/temp7_input
sensor /sys/devices/platform/thinkpad_hwmon/temp8_input
sensor /sys/devices/virtual/hwmon/hwmon0/temp1_input
sensor /sys/devices/virtual/hwmon/hwmon0/temp2_input
```I manually inserted 'sensors' before the /sys/...

Also, I noticed that my fan speed increased to more than 3000 RPM (max is around 3100). Before I installed thinkfan my fan speed was only around 2500 to 2800 RPM despite having temperature ranging from 60 to 80 Celsius. I monitor my temperature via Psensor and Hardware Sensors Indicator.

When I entered ```
sudo cat /proc/acpi/ibm/fan 
``` at an interval of around 3 to 5 minutes, this was the result. 

```
juno@Oogushi:~$ sudo cat /proc/acpi/ibm/fan
status:        enabled
speed:        3031
level:        auto
commands:    level <level> (<level> is 0-7, auto, disengaged, full-speed)
commands:    enable, disable
commands:    watchdog <timeout> (<timeout> is 0 (off), 1-120 (seconds))
juno@Oogushi:~$ sudo cat /proc/acpi/ibm/fan
status:        enabled
speed:        3052
level:        auto
commands:    level <level> (<level> is 0-7, auto, disengaged, full-speed)
commands:    enable, disable
commands:    watchdog <timeout> (<timeout> is 0 (off), 1-120 (seconds))
juno@Oogushi:~$ 
```I rebooted and did the command again but the level is always stuck to 'auto' and never became a number like 1 or 3. Did I do something wrong in installing the thinkfan?

I hope you can help me. Thank you very much.

---

### Post by VRathor on 2013-02-12
Using Thinkpad W500, ubuntu 12.04. I came to this thread to find solution for my interesting problem.
Problem:
My laptop, while watching movie or playing games, shuts down all of sudden. With syslog having this message:
```
Feb 11 15:02:49 vipin-ThinkPad-W500 kernel: [17020.922112] Critical temperature reached (128 C), shutting down.
```
Upon investigating, found out that it's the GPU temp which is shooting up till 128C. 
Started monitoring temp & fan speed since last two days... Generally the GPU sensor (i.e. temp4) remains at around 100C-118C which is abnormal IMO. The fan remains in auto mode doing ~3500 rpm "all the times". This explains temperature soaring so much.
Read about thinkfan here, gave it a shot. But not helping either. Followed the instructions by mejo (thanks!). And the fan still shows auto and doesn't change speed with temperature change.
```

vipin@vipin-ThinkPad-W500:~/Downloads$ sudo cat /proc/acpi/ibm/fan
[sudo] password for vipin: 
status:        enabled
speed:        3386
level:        auto
commands:    level <level> (<level> is 0-7, auto, disengaged, full-speed)
commands:    enable, disable
commands:    watchdog <timeout> (<timeout> is 0 (off), 1-120 (seconds))

vipin@vipin-ThinkPad-W500:~/Downloads$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +58.0°C  (crit = +127.0°C)
temp2:        +56.0°C  (crit = +100.0°C)

thinkpad-isa-0000
Adapter: ISA adapter
fan1:        3375 RPM
temp1:        +58.0°C  
temp2:        +62.0°C  
temp3:        +42.0°C  
temp4:       +120.0°C  
temp5:        +43.0°C  
temp6:            N/A  
temp7:        +36.0°C  
temp8:            N/A  
temp9:        +43.0°C  
temp10:       +62.0°C  
temp11:       +60.0°C  
temp12:           N/A  
temp13:           N/A  
temp14:           N/A  
temp15:           N/A  
temp16:           N/A  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +56.0°C  (high = +105.0°C, crit = +105.0°C)
Core 1:       +55.0°C  (high = +105.0°C, crit = +105.0°C)
```

Any thoughts?

---

### Post by linrunner on 2013-02-12
Hi,

looking for a software solution is pointless imho. 

Check your hardware: remove dust from air vents, heat exchanger and fan. I would even remove the fan unit and change the thermal grease and pads -> [Hardware Maintenance Manual]("http://support.lenovo.com/de_DE/detail.page?LegacyDocID=MIGR-70068").

---

