---
title: "Ubuntu drivers arghhh"
date: 2009-08-21
forum: Installation &amp; Upgrades
---

### Post by schoft on 2009-08-21
Why is so many hardware not supported by ubuntu ? I never had a perfect install of ubuntu on a computer, there is always almost no support for that video or soundcard im using. Also, if i search for problem/driver solutions on google and i try solutions , it doesnst help, wich is very frustrating. I have a p5w dh deluxe motherboard with onboard realtek alc882 and a nvidia 9600 GT. I have all the drivers, none of them work. Either trough an error in the manual installition or it just doesnt work. I have tried envyNG in recoverymode, no luck. Still errors. 
 
Are there any driver solutions for nvidia 9600 ? The official once dont work, they first say i have to disable xserver, and after that it says i dont have the correct kernels (?). My resolution doesnt go further then 1300 by something and i want 1650x1080. I think it is weird you cant just type in your resolution. 
 
How come everyone runs ubuntu fine with their graphicscard and soundcards ? It never works for me, i always end up editing configuration files and not finding a solution, and giving up. Ubuntu Drivers are hell, and always have been. I am ready to move on to w7
 
atm using ubuntu 9.04 x64

---

### Post by pawhtiobo on 2009-08-21
[COLOR=Black]Hi :)

I had exactly the same problem as you, i couldn't manage to install the correct driver for my card, but with some research i managed to do it.

I Used the **Nvidia proprietary driver**, that can be downloaded [here]("http://www.nvidia.com/object/linux_display_amd64_185.18.31.html"), then you need your **Linux Kernel Headers** instaled:

[B][COLOR=#996633][COLOR=#996633][COLOR=Black]$sudo apt-get update

[/COLOR][/COLOR][/COLOR][/B][COLOR=#996633][COLOR=#996633][COLOR=Black]and then,[/COLOR][/COLOR][/COLOR][B][COLOR=#996633][COLOR=#996633] 

[/COLOR][/COLOR][/B]**$sudo apt-get install linux-headers-$(uname -r)**

or you can find them in synaptic... :)

Next press **ctrl alt F1**, to exit X, do the **login** and then:

**$sudo killall gdm** or [/COLOR] **[COLOR=Black]$sudo /etc/init.d/gdm sto[/COLOR]p **(if you are using gnome, for KDE just change **gdm** to **kdm**) next,[B]

$cd Desktop[/B] (location of the downloaded driver)

next,

[COLOR=Black]**$sudo sh NVIDIA-Linux-x86_64-185.18.31-pkg2.run **and follow the instructions, after it finish the install, do
[/COLOR][B]
sudo reboot now [/B](let the system restart)

if everiting went well X will start correctly :) and you will see the Nvidia Logo appear.

You may need to update the xorg.conf, if the X fails to start:

**$sudo gedit /etc/X11/xorg.conf**

and change in the section **device**:

[B]Driver "nvidia"

[/B]to remove the Nvidia Logo, just add to section device:[B]

Option        "NoLogo"[/B]

I hope that can help you, i think i didn't miss any step :P...if you have any trouble, we are here to help.

---

### Post by schoft on 2009-08-21
Thanks loads, i will try this when i get back from work ! :D

---

### Post by schoft on 2009-08-21
Forgot to mention i already installed the nvidia driver. This is how my xorg file looks like:

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
    Disable    "dri2"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Driver    "nvidia"
EndSection


Kind of empty. I can also load the **Nvidia xserver settings**. But i cant set the resolution higher, only the panning.

---

### Post by schoft on 2009-08-21
So, followed your steps again and i got a 'precompiled kernel not found,download from nvidia? ' error in the installation. When i say yes, it fails to download and continues the installation. After a while it gives the 'usr/lib/nvidia/libglx.xserver-xorg-core could not be executed for reading' or something like that.

I reboot, and it says 'failed to load .ini nvidia kernel'
*ABORTING*
'screen (s) found but none have a useable configuration'
i choose 'use low-resolution mode for this session only'
-warning
there already appears to be an xserver on display (0)
should another display be tried? I choose yes because no doesnt do anything: 'The specified display nr. was busy, so this server was started on display: 1'

And now i am on 1024x768 :-({|=

Edit: [http://http.download.nvidia.com/XFree86/Linux-x86/1.0-9629/README/chapter-02-section-03.html](http://http.download.nvidia.com/XFree86/Linux-x86/1.0-9629/README/chapter-02-section-03.html)

Will that help me ?

Here i tried to restartx server:
```
usr@deadreceiver:~$ sudo sh /home/usr/restartx 
[sudo] password for usr : 

X: warning; process set to priority -1 instead of requested priority 0

X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-15-server x86_64 Ubuntu
Current Operating System: Linux deadreceiver 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 19:25:34 UTC 2009 x86_64
Build Date: 09 April 2009  02:11:54AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@crested.buildd) 
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Aug 21 23:40:39 2009
(==) Using config file: "/etc/X11/xorg.conf"
Error: API mismatch: the NVIDIA kernel module has version 180.44,
but this NVIDIA driver component has version 185.18.31.  Please make
sure that the kernel module and all NVIDIA driver components
have the same version.
(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module. Please see the
(EE) NVIDIA(0):     system's kernel log for additional error messages and
(EE) NVIDIA(0):     consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log
giving up.
xinit:  No such file or directory (errno 2):  unable to connect to X server
xinit:  No such process (errno 3):  Server error.
/home/usr/restartx: 4: ~$: not found
```

---

### Post by jimmyhacker on 2009-08-21
:))) i have Ati Radeon 9200SE,Via sound card,and all drivers are installed and working fine from installation to this day.cheap *** or very weird hardware,and choosing 8.04 is not going well.

Also,aprox. all drives are in repository.:lolflag:

---

### Post by schoft on 2009-08-22
Anyone?!

---

### Post by PmDematagoda on 2009-08-22
Can you try downloading and installing the latest Nvidia driver from [here]("http://www.nvidia.com/object/linux_display_ia32_185.18.36.html") and seeing if the installation manages to succeed?

By rights you shouldn't have to be doing this since the drivers are available on the repositories and would have probably only necessitated going to Administration->Hardware Drivers and then enabling the Nvidia driver, though I have no idea what on earth that log is talking about.

Can you post what you did in trying to get the Nvidia driver working?

---

### Post by schoft on 2009-08-22
I already had that installition, and it did not succeed. Also, i wouldn't have manual installed if the repositorys drivers worked

---

### Post by PmDematagoda on 2009-08-23
Could you remove the nvidia-glx package with:-
```
sudo apt-get remove nvidia-glx-180
```
reinstall the Nvidia driver manually again and see if that works?

---

### Post by pawhtiobo on 2009-08-24
Hi :)

Strange, the setup of the Nvidia proprietary driver should ask you if you want to remove the previous version of the installed driver, after reboot, if you retry the setup as i explained in the first post, it would ask if you want to download the kernel, from Nvidia, then it should says no Kernel available or something like that, so it will compile the Nvidia Kernel according to your system...well something not right...

I advise you to remove any Nvidia related driver stuff... maybe something is in conflict, in the console do the following:

**sudo apt-get remove nvidia-kernel-common**

and,

**sudo apt-get remove --purge nvidia***

and,

**sudo apt-get remove linux-restricted-modules***

and,

[B]sudo rm  /lib/restricted-modules/.nvidia*

[/B]still in your Desktop, if you want, you can install a small aplication called **Ubuntu-Tweak**, that you can download [here]("http://ubuntu-tweak.com/downloads"). The application has an option called package cleaner, where you can remove broken dependencies, package cache, old config files and old Kernels, if tou want you can do a cleaning, just to garantee that all Nvidia stuff is really gone :)

Next, exit **X**,and[B],

sudo /etc/init.d/gdm stop[/B]

Reinstall the driver as i descrived in the first post...an let us know how it went..if it was good, then do,

**sudo modprobe -r nvidia**

**sudo depmod -a**

**sudo /etc/init.d/gdm start**

if X don't start, you may need to,

**sudo dpkg-*reconfigure* -phigh *xserver*-xorg**

Let us know how it went :)

See ya....

---

### Post by aponhcet on 2009-08-26
omg, after so many time to search, it's work perfectly.

so, my last nvidia driver was 180.* from ubuntu library.

this is maybe the cause of the conflict. uninstall all like pawhtiobo said and reinstall driver. and it ll be ok.

thx you for this post :)

during the installation i got few message : unable to create folder, or , empty folder... i thought this ll generate an error but no. look nice.

---

### Post by pawhtiobo on 2009-08-26
Nice :)... another happy costumer :D...loll

---

