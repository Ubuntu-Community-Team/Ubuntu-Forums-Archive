---
title: "nividia geforce 970 drivers for ubuntu 14.04"
date: 2016-01-06
forum: Hardware
---

### Post by jerry50 on 2016-01-06
I'm building a new computer and have installed a dedicated graphics card, EVGA GeForce 970.  It is Nividia.  Can someone explain step by step where to find the drivers and how to install them?  The disc that came with the graphics card is not useful and most sites I've visited just give downloads for windows systems and I have only Ubuntu 14.04.  Are there commands I need to put into the terminal?  What??  Stumped.

---

### Post by yetimon_64 on 2016-01-06
First type "Additional Drivers" in Dash to bring up the utility to add proprietary drivers. There may be a proprietary driver available there for an nvidia card. If there is click it and choose to install/apply changes etc. 

If no drivers are available in the "Additional Drivers" utility for the nvidia card you may need to go to the xorg-edgers ppa to get support for a newer card. Not sure about the 970 you mention but I had to use the ppa with this hybrid graphics nvidia set up, some newer cards also need the ppa to get support for drivers if none are available in the additional drivers utility.

---

### Post by Bucky Ball on 2016-01-06
*Thread moved to **Hardware**.*

Right there on the Nvidia site, and if you do an update and check 'Additional Drivers' you may find the correct one right there, too. :)
[URL="http://www.geforce.com/drivers"]
Look here[/URL], choose the 900 series and then the GTX 970, then the Linux .deb driver. Download that, double click it, Software Centre should open and install it. Reboot.

On the verge of buying this card myself, have done some research for how it might go and what I'd need to do to get it working, so interested to know how you go.

---

### Post by blm-ubunet on 2016-01-06
The GTX970 works just fine in 14.04 mate desktop.

There is an appropriate ppa closer to home..
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa?field.series_filter=trusty](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa?field.series_filter=trusty)

xorg-edgers is not recommended as it touches so many core files/packages.
Direct download from nVidia is not recommended for novices.
The nVidia driver readme file (& the info tab on their webpages) lists the supported models..

---

### Post by Bucky Ball on 2016-01-06
> **blm-ubunet said:**
> The GTX970 works just fine in 14.04 mate desktop.

Out of the box? Good to hear either way.

> **blm-ubunet said:**
> There is an appropriate ppa closer to home..
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa?field.series_filter=trusty](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa?field.series_filter=trusty)

Is this the PPA you are using as I can find no mention of the GTX 970 on that page anywhere. 

> **blm-ubunet said:**
> Direct download from nVidia is not recommended for novices.

Unsure why.

> **blm-ubunet said:**
> The nVidia driver readme file (& the info tab on their webpages) lists the supported models..

The read me file of the driver in the PPA you have linked to? :)

---

### Post by jerry50 on 2016-01-07
> **yetimon_64 said:**
> First type "Additional Drivers" in Dash to bring up the utility to add proprietary drivers. There may be a proprietary driver available there for an nvidia card. If there is click it and choose to install/apply changes etc. 

If no drivers are available in the "Additional Drivers" utility for the nvidia card you may need to go to the xorg-edgers ppa to get support for a newer card. Not sure about the 970 you mention but I had to use the ppa with this hybrid graphics nvidia set up, some newer cards also need the ppa to get support for drivers if none are available in the additional drivers utility.

I have the additional drivers in dash opened and it has three choices and the last one is selected which is "Using X.Org X Server-Nouveau display driver, etc.  But the first choice is "Using Nvidia binary driver-versioin 352.63 from nvidia-352 (proprietary, tested).

My follow up question is, what is "xorg-edgers ppa"?  I'm trying the first choice now and will tell you how it goes.  Changes are being applied but very very slowly.  Ok.  Finished.  Now what?  How do I know if this worked?

---

### Post by Bucky Ball on 2016-01-07
Reboot. Open a terminal and check the driver with:

```
sudo lshw -C video
```

---

### Post by jerry50 on 2016-01-07
> **Bucky Ball said:**
> Reboot. Open a terminal and check the driver with:

```
sudo lshw -C video
```

Ok, here is what came up in the terminal:    [SIZE=5]Did it work??????
[/SIZE]
jerry@jerry-Z97X-UD3H:~$ sudo lshw -C video
[sudo] password for jerry: 
  *-display               
       description: VGA compatible controller
       product: NVIDIA Corporation
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:34 memory:f6000000-f6ffffff memory:e0000000-efffffff memory:f0000000-f1ffffff ioport:e000(size=128) memory:f7000000-f707ffff
  *-display
       description: VGA compatible controller
       product: Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:31 memory:f7400000-f77fffff memory:d0000000-dfffffff ioport:f000(size=64)

---

### Post by Yellow Pasque on 2016-01-07
Did it work? It probably did since "driver=nvidia" appears in the output. A better test would be looking at glxinfo:
```
sudo apt-get install mesa-utils #this may already be installed, but I can't remember if it's installed by default on Trusty
glxinfo | grep string
```

You should see something like:
```
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce GTX 970/PCIe/SSE2
OpenGL core profile version string: 4.5.0 NVIDIA 352.63
OpenGL core profile shading language version string: 4.50 NVIDIA
OpenGL version string: 4.5.0 NVIDIA 352.63
OpenGL shading language version string: 4.50 NVIDIA
```

---

### Post by Yellow Pasque on 2016-01-07
> **Bucky Ball said:**
> Unsure why (direct download is not recommended).

If you run the Nvidia driver directly, it can be difficult to uninstall/upgrade it. It is not Debian compliant (installs files to places it's not supposed to and may overwrite files) and does not use the alternatives system to coexist with other drivers like a proper .deb package does. It is not recommended for any Debian/Ubuntu system, regardless of the experience level of the user, though novices are especially vulnerable because if they don't have dkms installed, the system will break (or at least not load the GUI) on the next kernel upgrade.

---

### Post by jerry50 on 2016-01-07
> **Temüjin said:**
> Did it work? It probably did since "driver=nvidia" appears in the output. A better test would be looking at glxinfo:
```
sudo apt-get install mesa-utils #this may already be installed, but I can't remember if it's installed by default on Trusty
glxinfo | grep string
```

You should see something like:
```
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce GTX 970/PCIe/SSE2
OpenGL core profile version string: 4.5.0 NVIDIA 352.63
OpenGL core profile shading language version string: 4.50 NVIDIA
OpenGL version string: 4.5.0 NVIDIA 352.63
OpenGL shading language version string: 4.50 NVIDIA
```

Ok. Did it and this came up:  [B]I don't know what this means:  E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
[/B]

jerry@jerry-Z97X-UD3H:~$ sudo apt-get install mesa-utils #this may already be installed, but I can't remember if it's installed by default on Trusty
[sudo] password for jerry: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  liblouis-data liblouis2 python3-brlapi python3-louis python3-pyatspi
  python3-speechd
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  mesa-utils
0 upgraded, 1 newly installed, 0 to remove and 6 not upgraded.
Need to get 34.4 kB of archives.
After this operation, 133 kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty/universe mesa-utils amd64 8.1.0-2 [34.4 kB]
Fetched 34.4 kB in 0s (117 kB/s)    
Selecting previously unselected package mesa-utils.
(Reading database ... 196849 files and directories currently installed.)
Preparing to unpack .../mesa-utils_8.1.0-2_amd64.deb ...
Unpacking mesa-utils (8.1.0-2) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Setting up mesa-utils (8.1.0-2) ...
jerry@jerry-Z97X-UD3H:~$ apt-get autoremove
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
jerry@jerry-Z97X-UD3H:~$

---

### Post by yetimon_64 on 2016-01-07
> **jerry50 said:**
> I have the additional drivers in dash opened and it has three choices and the last one is selected which is "Using X.Org X Server-Nouveau display driver, etc.  But the first choice is "Using Nvidia binary driver-versioin 352.63 from nvidia-352 (proprietary, tested).

My follow up question is, what is "xorg-edgers ppa"?  I'm trying the first choice now and will tell you how it goes.  Changes are being applied but very very slowly.  Ok.  Finished.  Now what?  How do I know if this worked?

Don't worry about the ppa as you have a proprietary driver available in the 352 driver; the ppa suggestion is for other circumstances where hardware doesn't have a driver offered.

Edit:> E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
jerry@jerry-Z97X-UD3H:~$                 You need to use sudo before the command to get root privileges there.

---

### Post by Yellow Pasque on 2016-01-07
The mesa-utils package installed. Run the glxinfo command I gave you in my last post. You can use the 'sudo apt-get autoremove' command as apt instructs, but that's irrelevant to this thread..

---

### Post by Yellow Pasque on 2016-01-07
> **yetimon_64 said:**
> Don't worry about the ppa as you have a proprietary driver available in the 352 driver; the ppa suggestion is for other circumstances where hardware doesn't have a driver offered.

If the OP is interested in playing modern games, a newer driver version may help. This 352.xx bug is also annoying and it inspired me to install a newer Nvidia version on my Debian system: [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-352/+bug/1500113](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-352/+bug/1500113)

---

### Post by jerry50 on 2016-01-07
> **yetimon_64 said:**
> Don't worry about the ppa as you have a proprietary driver available in the 352 driver; the ppa suggestion is for other circumstances where hardware doesn't have a driver offered.

Edit:You need to use sudo before the command to get root privileges there.

OK.  Did it.  Below is what happened.  [B]Do I need to put in "sudo apt-get install mesa-utils #this may already be installed, but I can't remember if it's installed by default on Trusty" again?
[/B]

jerry@jerry-Z97X-UD3H:~$ sudo apt-get autoremove
[sudo] password for jerry: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  liblouis-data liblouis2 python3-brlapi python3-louis python3-pyatspi
  python3-speechd
0 upgraded, 0 newly installed, 6 to remove and 6 not upgraded.
After this operation, 6,890 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 196859 files and directories currently installed.)
Removing python3-louis (2.5.3-2ubuntu1) ...
Removing liblouis2:amd64 (2.5.3-2ubuntu1) ...
Removing liblouis-data (2.5.3-2ubuntu1) ...
Removing python3-brlapi (5.0-2ubuntu2) ...
Removing python3-pyatspi (2.10.0+dfsg-1) ...
Removing python3-speechd (0.8-5ubuntu1) ...
Processing triggers for libc-bin (2.19-0ubuntu6.6) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
jerry@jerry-Z97X-UD3H:~$

---

### Post by Yellow Pasque on 2016-01-07
No, you already installed mesa-utils. Run:
```
glxinfo | grep string
```

---

### Post by jerry50 on 2016-01-07
Finally got this:    So....are my drivers finally installed properly??

server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce GTX 970/PCIe/SSE2
OpenGL core profile version string: 4.3.0 NVIDIA 352.63
OpenGL core profile shading language version string: 4.30 NVIDIA via Cg compiler
OpenGL version string: 4.5.0 NVIDIA 352.63
OpenGL shading language version string: 4.50 NVIDIA
jerry@jerry-Z97X-UD3H:~$

---

### Post by Yellow Pasque on 2016-01-07
It looks good. *Thumbs up*

---

### Post by jerry50 on 2016-01-07
YEAH!!  Thanks for your help..._***truly***_.  I just blindly trust y'all to know what you are doing and you have never disappointed.  I think most dedicated  Linux users would do almost anything to avoid turning to Windows.  Well, I'm in  that camp.  So, once again...many thanks to all those that got me here.

Next step: gaming on Linux.  That should be fun!!

---

### Post by Yellow Pasque on 2016-01-07
You're welcome. Please mark the thread solved (Thread Tools menu at the top).

---

### Post by jerry50 on 2016-01-10
I would mark this as "solved" but these actions created an unusable operating system! I couldn't even get into the BIOS.  I had to take the battery out to reset the CMOS and BIOS.  Then I booted with the Linux disk and this is what happened:  ***Errors found while checking the disk drive.  Press F to attempt to fix.***  The screen quickly went to *** !The system is running in low graphics mode.  (Your screen, graphics card, and input device settings could not be detected correctly.  You will need to configure these yourself.) *** I hit "OK" and it asked  ***What would you like to do?  ***I was given 4 choices:  ***Run in low graphics mode for just one session.  Reconfigure graphics.  Troubleshoot error.  Exit to console login.  ***I tried all 4.  Options 1 and 4 both got me to a text log in screen that looked similar to the terminal screen.  After putting in my login name and password there is just a blinking dash waiting for the next command and I have no idea what to put in.  Option 3, to troubleshoot the error, gives 3 more options and only one, ***Review the xserver log file, ***provides any information, a laundry list of information, very long, most of which I can't understand.  What was repeated was ***"couldn't open module nvidia"*** and ***"unloading module nouveau".  ***Towards the end of this list was ***"Fatal Server error"***.  That wasn't a happy thing to see!!

I'm to the point of erasing the hard drive and reinstalling Ubuntu.  I think I will try Parted Magic but wanted to get your ideas before I began.  Barring that, I'm off to buy a new ssd and begin again.  This is one way of learning...not the most enjoyable, but definitely a learning experience.

---

### Post by jerry50 on 2016-01-15
I ended up taking it to a tech to reinstall linux.  I'm really disappointed that someone didn't respond to my last post.  Oh well.  onward and upward

---

