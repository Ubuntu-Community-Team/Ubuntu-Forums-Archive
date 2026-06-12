---
title: "Issues with Ubuntu 14.04 LTS and Nvidia GTS 450"
date: 2014-11-30
forum: Hardware
---

### Post by McGoo84 on 2014-11-30
Hi, 

I instal Ubuntu 14.04 and have problem with drivers for my NVIDIA GeForce GTS 450, I can setup 1360 x 768 resolution only. Best resolution for my monitor is 1920x1080. I try step by step use this [http://www.howopensource.com/2012/10/install-nvidia-geforce-driver-in-ubuntu-12-10-12-04-using-ppa/](http://www.howopensource.com/2012/10/install-nvidia-geforce-driver-in-ubuntu-12-10-12-04-using-ppa/) but no effect. I alsow try that [http://ubuntuforums.org/showthread.php?t=2173223](http://ubuntuforums.org/showthread.php?t=2173223) but no efect to. :(

Any suggestions?

---

### Post by oldfred on 2014-11-30
There are 3 ways to install nVidia drivers. From Ubuntu repository, from PPA & directly from nVidia.
I always suggest just using the repository unless you have one of the very new cards/chips that needs a newer version of driver than is in repository. Occasionally there are fixes for older cards in the newest driver, but most are fixes for recent cards and the version in the repository is pretty new, just not the very latest. Also if using the nVidia directly download you have to reconfigure on every kernel update.

And if you attempt to change from one install process to another you have to absolutely purge all traces of nVidia drivers and settings in xorg before changing to avoid conflicts.

       #To see video:
sudo lshw -c display
sudo lshw | grep -A 11 display
lspci | grep VGA
#Resolution:
xwininfo -root
What is installed
dkms status

 lsmod | grep -E 'nvidia|nouveau'

This shows versions in repository:

 ubuntu-drivers devices

---

### Post by McGoo84 on 2014-11-30
Ok, but I'm new on ubuntu (linux), and it does not tell me anything


 :(

I try and, it show: 

**sudo lshw -c display**

*-display               
       description: VGA compatible controller
       product: GF116 [GeForce GTS 450 Rev. 2]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:f8000000-f9ffffff memory:d0000000-d7ffffff memory:d8000000-dbffffff ioport:e000(size=128) memory:fa000000-fa07ffff


**sudo lshw | grep -A 11 display**

*-display
                description: VGA compatible controller
                product: GF116 [GeForce GTS 450 Rev. 2]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:16 memory:f8000000-f9ffffff memory:d0000000-d7ffffff memory:d8000000-dbffffff ioport:e000(size=128) memory:fa000000-fa07ffff
[B]
lspci | grep VGA[/B]

01:00.0 VGA compatible controller: NVIDIA Corporation GF116 [GeForce GTS 450 Rev. 2] (rev a1)

**xwininfo -root**

 Absolute upper-left X:  0
  Absolute upper-left Y:  0
  Relative upper-left X:  0
  Relative upper-left Y:  0
  Width: 1152
  Height: 864
  Depth: 24
  Visual: 0x21
  Visual Class: TrueColor
  Border width: 0
  Class: InputOutput
  Colormap: 0x20 (installed)
  Bit Gravity State: ForgetGravity
  Window Gravity State: NorthWestGravity
  Backing Store State: NotUseful
  Save Under State: no
  Map State: IsViewable
  Override Redirect State: no
  Corners:  +0+0  -0+0  -0-0  +0-0
  -geometry 1152x864+0+0


**dkms status**
bbswitch, 0.7, 3.13.0-40-generic, i686: installed
ndiswrapper, 1.59, 3.13.0-32-generic, i686: installed
ndiswrapper, 1.59, 3.13.0-32-generic, x86_64: installed
ndiswrapper, 1.59, 3.13.0-40-generic, i686: installed
nvidia-304, 304.123, 3.13.0-40-generic, i686: installed

**lsmod | grep -E 'nvidia|nouveau'**
nvidia              10329701  40 


**ubuntu-drivers devices **
== /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0 ==
vendor   : NVIDIA Corporation
model    : GF116 [GeForce GTS 450 Rev. 2]
modalias : pci:v000010DEd00001245sv00000000sd00000000bc03sc00i00
driver   : nvidia-331-updates - distro non-free
driver   : nvidia-304 - third-party free
driver   : xserver-xorg-video-nouveau - distro free builtin
driver   : nvidia-304-updates - distro non-free
driver   : nvidia-331 - third-party free
driver   : nvidia-340 - third-party free recommended

---

### Post by oldfred on 2014-11-30
Are you running 32 bit or 64 bit?
       uname -a
i386 or i686 = 32-bit

Repository suggests this:
driver   : nvidia-340 - third-party free recommended 

But it looks like you have the 32 bit version installed?
nvidia-304, 304.123, 3.13.0-40-generic, i686: installed

---

### Post by McGoo84 on 2014-11-30
**uname -a**
Linux mcgoo 3.13.0-40-generic #69-Ubuntu SMP Thu Nov 13 17:56:26 UTC 2014 i686 i686 i686 GNU/Linux

So what I should do now? :|

---

### Post by oldfred on 2014-11-30
You are running the 32 bit version. Is this an old computer? Or less than 2GB of RAM?

I would totally purge current nVidia and install from repository.
You may have to go back to nouveau and may need nomodeset to boot from grub menu when nVidia is uninstalled. But should be able to reinstall after total purge?

       Shows any file with nvidia in name, lots of files.
sudo find / -name "nvidia*"
Shows versions in repository:
sudo apt-cache search nvidia-sett*
Lists installed version, in/with your kernel:
dkms status
# Houseclean out all old versions to avoid issues
sudo apt-get remove --purge < nvidiadriverpackagename>
# [ using the correct names] for each driver, before running:
sudo apt-get purge nvidia*
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

    
       sudo apt-get update
sudo apt-get upgrade

You are showing 340, not sure if that is from Ubuntu repository or not. My system only shows -331 and I would then install the -331-updates.

 sudo apt-get install nvidia-331-updates

 sudo nvidia-xconfig
sudo reboot

[http://www.dedoimedo.com/computers/ubuntu-ringtail-nvidia.html](http://www.dedoimedo.com/computers/ubuntu-ringtail-nvidia.html)
[http://choorucode.com/2013/02/07/how-to-fix-nvidia-driver-failure-on-ubuntu/](http://choorucode.com/2013/02/07/how-to-fix-nvidia-driver-failure-on-ubuntu/)

---

### Post by McGoo84 on 2014-12-01
No my computer : Intel® Core&#8482; i5-2320 CPU @ 3.00GHz × 4 , 3,9 GiB

I try all step by step and after :

**sudo nvidia-xconfig**

Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as
'/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

Now I have resolution 640x480 :( 

What should I do?

---

### Post by oldfred on 2014-12-01
How are you connecting to monitor, not old vga, but DVI? and is it a newer monitor or very old.

Is nVidia seeing as the correct model number? That is from the EDID that monitor tells systems are valid settings.

---

### Post by McGoo84 on 2014-12-01
I'm conected by D-sub cable - but monitor is not so old (Its LG Flatron E2340S). 

How to check is nVidia seeing correctly model number?

---

### Post by oldfred on 2014-12-01
I do not have nVidia installed yet on this system. But it think it was the next line down in this:

---

### Post by McGoo84 on 2014-12-01
What that's means?

My is:
[http://s30.postimg.org/8xq7enq35/Zrzut_ekranu_z_2014_12_01_22_29_22.png](http://s30.postimg.org/8xq7enq35/Zrzut_ekranu_z_2014_12_01_22_29_22.png)

---

### Post by oldfred on 2014-12-01
go down several lines, not sure which anymore.
It should show monitor and allowed settings.

---

