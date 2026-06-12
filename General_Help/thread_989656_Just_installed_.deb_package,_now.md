---
title: "Just installed .deb package, now?"
date: 2008-11-21
forum: General Help
---

### Post by gvanto on 2008-11-21
I'm having some trouble getting VirtualBox to work on Hardy. AFter installing it (using sudo aptitude install virtualbox), I got the error (on launching the virtual machine):
> 
VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


So after following someone in a forums' advice, I went to install the .deb package from the virtualbox.org site, with success:

> 

pacific@mainbox:~$ ls
Desktop    Music     Public     Videos
Documents  Pictures  Templates  virtualbox-2.0_2.0.4-38406_Ubuntu_hardy_i386.deb
pacific@mainbox:~$ sudo dpkg -i virtualbox-2.0_2.0.4-38406_Ubuntu_hardy_i386.deb
[sudo] password for pacific:
Selecting previously deselected package virtualbox-2.0.
(Reading database ... 104310 files and directories currently installed.)
Unpacking virtualbox-2.0 (from virtualbox-2.0_2.0.4-38406_Ubuntu_hardy_i386.deb) ...
Setting up virtualbox-2.0 (2.0.4-38406_Ubuntu_hardy) ...
Installing new version of config file /etc/init.d/vboxdrv ...
Found old version of /etc/vbox/vbox.cfg, removing.
addgroup: The group `vboxusers' already exists as a system group. Exiting.
 * Starting VirtualBox kernel module                                                          *  done.
 * Starting VirtualBox host networking                                                        *  done.

pacific@mainbox:~$



Only now, when I type 'virtualbox', it doesn't recognize it. HOw do I start the application (and how to make it so I can type 'virtualbox' to launch the app?)

So yeah, I'm at a bit of a loss getting virtualbox to work, help would be much appreciated!

Gerry
.deb package newbie

---

### Post by Therion on 2008-11-21
Here's the tutorial I used to get Virtual Box going under Hardy.  It's always worked well for me:

[http://n00buntu.blogspot.com/2007/11/howto-ubuntu-compiz-virtualbox-part-1.html](http://n00buntu.blogspot.com/2007/11/howto-ubuntu-compiz-virtualbox-part-1.html)

---

### Post by drs305 on 2008-11-21
Unlike many linux apps, VirtualBox uses mixed case letters: **VirtualBox** is the start command.

---

### Post by gvanto on 2008-11-22
Thanks guys,

OK i've created a virtual machine, of fixed 50GB size for the Windows virtual box (with 2GB base memory).

Only, now when I start the virtual machine, it goes to the windows setup (the blue screen), I give it the entire 50GB partition (with 8MB spare partition) to format and install windows on - BUT it never gets passed the formatting stage. Quick format gets to 20% and normal format to 0% and just stays there. in both cases, it simply aborts after a while, and the virtual machine is in the aborted state.

Advice would be really appreciated if anyone knows about this obscure problem ?

I've installed this ages ago on Hardy and it worked fine (using the same windows disks), no idea why its playing up now!)

Gerry
frustrated virtualboxer

---

### Post by gvanto on 2008-11-22
When I click on settings, I get the following message pop up, not sure if it has anything to do with the fact that the windows setup formatting is crashing?

> 

Could not load the Host USB Proxy Service (VERR_FILE_NOT_FOUND). The service might be not installed on the host computer.


Result Code: 
NS_ERROR_FAILURE (0x00004005)
Component: 
Host
Interface: 
IHost {489fb370-c227-4d43-9761-ceb28484fd9f}
Callee: 
IMachine {1e509de4-d96c-4f44-8b94-860194f710ac}



---

