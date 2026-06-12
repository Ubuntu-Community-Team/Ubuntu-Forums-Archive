---
title: "HP Compaq 6720s and Ubuntu 8.04 Hardy Heron - a (hopefully) complete guide..."
date: 2008-05-04
forum: Hardware
---

### Post by slayer^_^ on 2008-05-04
This is the Hardy sequel to the gutsy one, that, i must admit, had a great success !!

In Hardy Heron everything seems to work (I am always ready to update this guide), except the wireless device, the infamous hard disk reduced life and a video memory allocation problem, that is a bit problematic... so, let's see...

**_1) UBUNTU EATS YOUR HARD DISK_**
_**2) MAKING WIRELESS WORK**_
_**3) CORRECT ALLOCATION OF VIDEO MEMORY**_ _(should have been fixed with the last updates)_
_**4) CLOSING THE LID MAKES YOUR SYSTEM FREEZE**_
**_5) CONFIGURING YOUR MICROPHONE_**


_**UBUNTU EATS YOUR HARD DISK**_

Just copying and pasting from the ubuntu howto

# Enable CONTROL_HD_POWERMGMT=1 in /etc/laptop-mode/laptop-mode.conf

    *

      (Bug 244832 missing hdparm -B setting during boot (fixed in intrepid 250935)) 

# ENABLE_LAPTOP_MODE=true in /etc/default/acpi-support (another package's conffile), even if you do not ENABLE_LAPTOP_MODE_ON_BATTERY or _ON_AC in laptop-mode.conf. So that laptop-mode-tools can control the harddisk power management settings.

    *

      (244838 laptop-mode needs to be activated in two places) 

# Delete or #comment the four $HDPARM blocks (for...done) in /etc/acpi/power.sh and change the two $LAPTOP_MODE start/stop lines to "$LAPTOP_MODE auto"

    *

      (244836 /etc/acpi/power.sh overrides user settings (fixed in intrepid 250938))
      (244831 /etc/acpi/power.sh overrides user scripts (fixed in intrepid 250938))
      (244844 Adapt laptop-mode-tools invocation to ubuntu's acpi-support / pm-utils packages (fixed in intrepid 250935)) 

# Create a bogus /etc/pm/power.d/laptop-tools script to override /usr/lib/pm-utils/power.d/laptop-tools.

    *

      (239419 pm-utils has laptop-tools script which conflicts with laptop-mode-tools (not so in intrepid)) 
_**MAKING THE WIRELESS DEVICE ( BROADCOM BCM4312 rev 02 ) WORK**_

**_Before trying any method below, try to unlock the "proposed" repository and do a full update of Hardy. Then install the package b43-fwcutter. It has been reported that working drivers have been put there. Just if this doesn't work go forward._**

If you haven't managed to get your wireless card working...

**_METHOD 0)_** -- _Ndiswrapper zero - This one works for sure_

Tested a minute ago.. works on all the laptos I tried onto...

Check you've got a BCM4312 (rev 02) before proceeding

```
lspci | grep Broadcom\ Corporation
```

Just copy and paste - line by line - in the terminal
(I've been very busy lately, when I'll have enough time I'll explain the commands as usual...)

```
mkdir ~/bcm43xx; cd ~/bcm43xx
wget ftp://ftp.compaq.com/pub/softpaq/sp34001-34500/sp34152.exe
sudo apt-get install cabextract
cabextract sp34152.exe
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
echo 'blacklist wl' | sudo tee -a /etc/modprobe.d/blacklist
sudo apt-get install ndiswrapper-utils-1.9
sudo ndiswrapper -i bcmwl5.inf
ndiswrapper -l
sudo depmod -a
sudo modprobe ndiswrapper
sudo cp /etc/network/interfaces /etc/network/interfaces.orig
echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces
sudo ndiswrapper -m
echo 'ndiswrapper' | sudo tee -a /etc/modules
echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant
sudo aptitude remove b43-fwcutter
```

Turn gedit into Kate, of Xfce, or your favourite text editor in the next line
```
sudo gedit /etc/init.d/wirelessfix.sh
```

Paste into the created (and opened) text file the following lines:

      ```
#!/bin/bash
      modprobe -r b44
      modprobe -r b43
      modprobe -r b43legacy
      modprobe -r ssb
      modprobe -r ndiswrapper
      modprobe ndiswrapper
      modprobe b44
```

Save the text file and exit; now paste into the terminal the following lines:

      ```
cd /etc/init.d/ && sudo chmod 755 wirelessfix.sh
      sudo update-rc.d wirelessfix.sh defaults
```

Reboot... I can assure this works..


Well, if you're unlucky enough and it shouldn't work you can use these old deprecated methods...




**_METHOD 1)_** -- _Patching your kernel_

Hardy Heron Kernel 2.6.24 allows the use of **(rev 01)** hardware, but not **(rev 02)**. If you apply a patch to the kernel you may use (rev 02) hardware but no more (rev 01). So Be careful!

To understand if you got (rev 01) or (rev 02) hardware, type in terminal

```
sudo lspci
```

You got to compile a patched kernel and then install it.

_Before you follow this method please take a backup of your data, the result could be a damage of your ubuntu installation..._

Let's compile a patched kernel from the linux-source  package:

```
sudo apt-get install linux-source
mkdir ~/src
cd ~/src
tar xjvf /usr/src/linux-source-2.6.24.tar.bz2
cd linux-source-2.6.24
```

Now let's configure it. We will re-use the configuration of the already running kernel:

```
sudo cp -vi /boot/config-`uname -r` .config
```

We'll need some packages now for the next step

```
sudo apt-get install libncurses5 libncurses5-dev
```

Now let's run:

```
sudo make menuconfig
```

Here you can choose your modules. You won't need this, but i suggest you to unselect "Kernel Debugging" (under "Kernel Hacking) for a lighter kernel.

Before compiling our kernel, we need to patch it!

Be sure yo ugot the necessary packages:

```
sudo apt-get install linux-source-2.6.24 kernel-package build-essential
```

Download the patch:

[http://linuxwireless.org/download/b43/patch_2.6.24_for_4311_2](http://linuxwireless.org/download/b43/patch_2.6.24_for_4311_2)

Drag and drop the patch file in the directory /yourusername/src/linux-headers-2.6.24-18-generic (well the name of the folder may be a bit different...however there should be only one!)

Now, in terminal:

```
sudo patch -p1 --dry-run < patch_2.6.24_for_4311_2
```

If all looks good, re-run the patch command and remove the --dry-run to do it for real. 

Now we got to compile our patched kernel!

If you got a dual core or quad processor, you'll be happy to use it! Give this info to the terminal _only_ 

If you got a Dual Core:

```
export CONCURRENCY_LEVEL=3
```

If you got a Quad Core:

```
export CONCURRENCY_LEVEL=5
```

because the number in the end means 1 + "the number of your processors".

Now, finally, let's compile our patched kernel (copy and paste as it is written):

```
sudo fakeroot make-kpkg --initrd --append-to-version=-some-string-here kernel-image kernel-headers
```

Let it compile...

When it has finished, you got your patched kernel in the folder /home/yourusername/src/ directory. 

It is a *deb archive (there should be two packages, one for the image, one for the headers). 

Install it and enjoy...  :)

p.s. perhaps I've forgotten one or two packages needed to perform all the operations i posted. In this case the terminal should help you ;)

Now let's install the broadcom driver cutter package:

```
sudo apt-get install b43-fwcutter
```

It should work by now... if it doesn't, let's try the ndiswrapper way:

**_METHOD 2)_** -- The return of ndiswrapper!

Again, let's blacklist the native bcm43xx driver (that should be blacklisted by default in Hardy Heron):

```
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
```

Let's install ndiswrapper (here I explain the text-terminal way, you can install these packages with synaptic package manager too, where there's also the graphical interface for ndiswrapper : ndisgtk - you can try that too)

```
sudo apt-get install ndiswrapper-utils-1.9
```

let's create a driver folder:

```
mkdir ~/bcm43xx; cd ~/bcm43xx
```

Now let's download the drivers:

First, let's download cabextract to extract them:

```
sudo apt-get install cabextract
```

Now, let's download the drivers:

```
wget ftp://ftp.compaq.com/pub/softpaq/sp34001-34500/sp34152.exe
```

And let's extract the drivers:

```
cabextract sp34152.exe
```

Now let's configure ndiswrapper:

```
sudo ndiswrapper -i bcmwl5.inf
```

Let's see if everything it's ok

```
ndiswrapper -l
```

The result should be driver installed, hardware present.

Now let's go forward:

```
sudo depmod -a
```

Then:

```
sudo modprobe ndiswrapper
```

Then:

```
sudo cp /etc/network/interfaces /etc/network/interfaces.orig
```

Then:

```
echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces

```

Then:

```
sudo ndiswrapper -m
```

Then:

```
echo 'ndiswrapper' | sudo tee -a /etc/modules
```

Then:

```
echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant
```

Now it's important to remove he firmware extraction tool if you have installed it. The Kernel of Hardy Heron needs a patch to work with your bcm4312 (rev 02) device, that breaks the compatibility with (rev 01 hardware). Therefore b43 won't work.

```
sudo aptitude remove b43-fwcutter
```

Now we got to apply a trick to make the module "ssb" not to load before "ndiswrapper" (preventing it from working:
```

sudo gedit /etc/init.d/wirelessfix.sh
```

Paste the followings in the opened text file (wirelessfix.sh)

> #!/bin/bash
modprobe -r b44
modprobe -r b43
modprobe -r b43legacy
modprobe -r ssb
modprobe -r ndiswrapper
modprobe ndiswrapper
modprobe b44
Then in the terminal:

```
cd /etc/init.d/ && sudo chmod 755 wirelessfix.sh
```

Finally:

```
sudo update-rc.d wirelessfix.sh defaults
```


Reboot, your wireless should work! If you had no luck still, we can try recompiling ndiswrapper from source:

Let's remove Stock ndiswrapper (paste every code that follows in the terminal, as usual...)

```
sudo modprobe -r ndiswrapper
```

```
sudo ndiswrapper -r bcmwl5
```

```
sudo apt-get remove ndiswrapper-utils
```

```
sudo rm -r /etc/ndiswrapper/
```

```
sudo rm -r /etc/modprobe.d/ndiswrapper
```

Now, REBOOT.

Compile and Install New ndiswrapper

```
sudo apt-get update
```

```
sudo apt-get install build-essential
```

```
sudo apt-get install linux-headers-`uname -r`
```

```
sudo ln -s /usr/src/linux-`uname -r` /lib/modules/`uname -r`/build
```

```
mkdir -p ~/bcm43xx/ndiswrapper; cd ~/bcm43xx/ndiswrapper
```

```
sudo wget http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.52.tar.gz -Ondiswrapper.tar.gz
```

```
tar xvzf ndiswrapper.tar.gz
```

```
cd ndiswrapper*
```

```
make distclean
```

```
make
```

```
sudo make install
```

Redo Some Steps That Were Undone by ndiswrapper Compilation/Installation

```
cd ~/bcm43xx
```

```
sudo ndiswrapper -i bcmwl5.inf
```

```
ndiswrapper -l
```

```
sudo modprobe ndiswrapper
```

```
sudo ndiswrapper -m
```

Now, reboot... everything should work!!

Disclaimer : i took some info from these two guides, who deserve my thanx:

[https://help.ubuntu.com/community/Wi...358e4b611353c0](https://help.ubuntu.com/community/Wi...358e4b611353c0)

[http://ubuntuforums.org/showthread.p...hlight=BCM4312](http://ubuntuforums.org/showthread.p...hlight=BCM4312)

_**CORRECT ALLOCATION OF VIDEO MEMORY**_

_It should have been fixed with the last updates. Do the changes below only if you experience troubles._

The "intel" driver is not able to do a correct allocation of the video memory. But we can solve manually the problem:

In terminal:

> sudo gedit /etc/X11/xorg.conf 

Then add the underlined options in the text file

```
[...]

Section "Device" 
          Identifier "Videocard0" 
          Driver "intel" 
          _Option "LinearAlloc" "6144"_
          _Option "CacheLines" "agoodnumberyoudecide"_
          _Option "AperTexSize" "agoodnumberyoudecide" _
[...]
```

From the intel website:

_Option "CacheLines" "integer"_ Decreasing this amount leaves more for 3D textures. Increasing it can improve 2D performance at the expense of 3D performance. The default used for a specific configuration can be found by exam- ining the Xorg log file


_Option "AperTexSize" "integer"_ Default: 32768


I suggest these settings: Cachelines = 768 ; AperTexSize = 131072

However you decide those values! Still pasting from the intel website:

Option "CacheLines" "integer"
This allows the user to change the amount of graphics memory
used for 2D acceleration and video when XAA acceleration is
enabled. Decreasing this amount leaves more for 3D textures.
Increasing it can improve 2D performance at the expense of 3D
performance. Default: depends on the resolution, depth, and
available video memory. The driver attempts to allocate space
for at 3 screenfuls of pixmaps plus an HD-sized XV video. The
default used for a specific configuration can be found by exam-
ining the Xorg log file. 

Option "AperTexSize" "integer"
Give the size in kiB of the AGP aperture area that is reserved
for the DRM memory manager present in i915 drm from version
1.7.0 and upwards, and that is used with the 3D driver in Mesa
from version 6.5.2 and upwards. If the size is set too high to
make room for pre-allocated VideoRam, the driver will try to
reduce it automatically. If you use only older Mesa or DRM ver-
sions, you may set this value to zero, and activate the legacy
texture pool (see Option "Legacy3D" ). If you run 3D programs
with large texture memory requirements, you might gain some per-
formance by increasing this value. Default: 32768.

_**4) CLOSING THE LID MAKES YOUR SYSTEM FREEZE**_

Try this command in the terminal:

```
sudo gedit /etc/rc.local
```

Put this line in the text file (before the "exit 0" line):

```
echo 1 > /proc/acpi/video/*/DOS
```

now in terminal
```
sudo gedit /etc/modprobe.d/options
```

add the following string (thanx to pleusicles for this tip)
```
options video no_automatic_changes=0
```

Save, close, reboot and try. It should work!
[U][B]
5) CONFIGURING THE MICROPHONE[/B][/U]

It should not be a problem if you're eager to configure your audio devices... however there's an easy howto if you wanna use quickly programs like Skype...

1 right click on the audio icon on the upper bar on the right, then "open volume control"
2 Edit / Preferences
3 Enable everything
4 Raise the volume of the microphones, then in the "recording" section, enable the microphone in the "capture side"

It should work... cheers !!!

---

### Post by dixon on 2008-05-07
How did you solve the lid crashing laptop problem. The command ```

echo 1 > /proc/acpi/video/*/DOS 
``` from previous thread works, but I don't know where to put it. When I put it into /etc/rc.local it gets ignored. I need to run this command at start.

I'm happy that hibernation finally works, but it's really slow. Is there some way how to speed it up?

Do you have also just 1 xv port? I had maybe 16(I can't remember) xv ports in gutsy...

---

### Post by sunilvarma on 2008-05-09
I tried following your guide, but there are a few issues:

1) There is no 'linux' folder inside /usr/src

So I created the 'linux' folder and copied the patch file into this folder.

When I run the patch command, it does nothing. I mean when I hit enter the prompt goes away and it doesn't come back no matter how long I wait.

So I decided to give method 2 a try.

2) In the driver file I downloaded from the HP site, there is a bcmwl6.inf instead of the bcmwl5.inf you metioned.

I continued installation with the bcwml6.inf driver file.

From then on I followed every step but after rebooting, WLAN still doesn't work.

Am I doing something wrong here? Please help...

Thanks

---

### Post by sunilvarma on 2008-05-10
managed to grab a copy of bcmwl5.inf and its working now.

---

### Post by slayer^_^ on 2008-05-10
i managed to fix the link. correct driver (bcmwl5.inf) now.

thank you!

Dixon: your questions are really interesting... I'll try to find some answers, please let us know if you find more about'em.

thank you too :)

---

### Post by slayer^_^ on 2008-05-11
i updated the kernel-patching method. let me know if it works for you too!

---

### Post by renezito on 2008-05-29
Thanks for your post. I was looking for a EASY solution without ndiswrapper. I'm going to try it (HP dv6420la, BCM4312 Rev 2) and then posts my results, I hope not to install ndiswrapper as I did it with Gutsy. Remember to change the linux directory, but it will depends on your kernel compilation, because by default there is no a linux directory.
About your commentary "UBUNTY EATS YOUR HARD DISK", How can I now o Where can I find the cycles p/m that is configured in my fresh install? Is there a file or its by default?

---

### Post by slayer^_^ on 2008-06-01
i don't know which way you can check the amount of cycles of your hard disk when using the battery. however, as i wrote, this is not a bug. it is the respect of the hard disk manufacturers directives that ubuntu applies, that results in a damage of the hard disks.

---

### Post by drpaul on 2008-06-01
renezito:

the following will give the Load Cycle Count. Tracking it will tell you how bad the problem is on your machine.

 sudo smartctl --all /dev/sda | grep Load

you may have to install smartctl and adjust sda to meet the parameter for your hard disk.

HTH

Paul

---

### Post by slayer^_^ on 2008-06-02
thank you drpaul! ;)

---

### Post by sroland81 on 2008-06-05
Hi, as i told in the gutsy theard, i'm running Hardy on Presario F730US for amd64 and i'm having serious issues. The wireless works but the computer freezes when using it, or browsing with firefox or downloading torrents with transmission torrent client.... and the "dmesg" shows this:

[  450.882784] wlan0: associated
[  475.915455] printk: 6936 messages suppressed.
[  475.915462] b43-phy0 ERROR: PHY transmission error
[  475.915473] b43-phy0 ERROR: PHY transmission error
[  475.915481] b43-phy0 ERROR: PHY transmission error
[  475.915489] b43-phy0 ERROR: PHY transmission error
[  475.915498] b43-phy0 ERROR: PHY transmission error
[  475.915507] b43-phy0 ERROR: PHY transmission error
[  475.915515] b43-phy0 ERROR: PHY transmission error
[  475.915524] b43-phy0 ERROR: PHY transmission error
santiago@quaoar:~$ 
in fact the output is much longer of the same lines...

i heard about the kernel patching but i followed the instructions and this is what i obtain... no patch yet i guess...

santiago@quaoar:~/Desktop$ patch -p1 --dry-run < patch_2.6.24_for_4311_2
can't find file to patch at input line 13
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|This combined patch includes all the changes required to update the the mainline
|git tree, or the 2.6.24-rcX code base, to incorporate the changes needed to operate
|the BCM4311 rev02 and BCM4312 rev02 (G PHY only) chips. These patches match the
|changes incorporated in the everything branch of the wireless-2.6 git tree for which
|'git describe' yields "v2.6.24-rc1-2199-g65d438b", plus the BCM4311/2 modifications.
|
|Larry
|--------
|
|diff -up -X linux-2.6/Documentation/dontdiff linux-2.6/drivers/ssb/b43_pci_bridge.c wireless-2.6/drivers/ssb/b43_pci_bridge.c
|--- linux-2.6/drivers/ssb/b43_pci_bridge.c     2007-11-20 15:13:44.000000000 -0600
|+++ wireless-2.6/drivers/ssb/b43_pci_bridge.c  2007-11-20 18:43:49.000000000 -0600
--------------------------
File to patch: 


The thing is that i tried ndiswrapper that i found in some forums and the fw-cutter thing and i always got the wireless working but the computer hangs me like hell... no mouse or keyboard response... i think it is related to the net traffic. if i'm browsing too much and downloading a movie... it will hang me every 10 or 20 miunutes... if i'm only using pidgin it will do it once an hour... don't know....

anyway the "dmesg" was always the same error message with b43-phy0 ERROR... and please need some help...

i would like to try patching the kernel but i don't know how to do it anyway... so i'm waiting for your intructions... 

Thank you very much,

Regards,

Santiago.-

---

### Post by slayer^_^ on 2008-06-05
You got to compile a patched kernel and then install it.

Let me see, so i can update the guide too...

_Before you follow this method please take a backup of your data, the result could be a damage of your ubuntu installation..._

Let's compile a patched kernel from the linux-source  package:

```
sudo apt-get install linux-source
mkdir ~/src
cd ~/src
tar xjvf /usr/src/linux-source-2.6.24.tar.bz2
cd linux-source-2.6.24
```

Now let's configure it. We will re-use the configuration of the already running kernel:

```
sudo cp -vi /boot/config-`uname -r` .config
```

We'll need some packages now for the next step

```
sudo apt-get install libncurses5 libncurses5-dev
```

Now let's run:

```
sudo make menuconfig
```

Here you can choose your modules. you won't need this, but i suggest you to unselect "Kernel Debugging" (under "Kernel Hacking) for a lighter kernel.

Before compiling our kernel, we need to patch it!

Be sure yo ugot the necessary packages:

```
sudo apt-get install linux-source-2.6.24 kernel-package build-essential
```

Download the patch:

[http://linuxwireless.org/download/b43/patch_2.6.24_for_4311_2](http://linuxwireless.org/download/b43/patch_2.6.24_for_4311_2)

Drag and drop the patch file in the directory /yourusername/src/linux-headers-2.6.24-18-generic (well the name of the folder may be a bit different...however there should be only one!)

Now, in terminal:

```
sudo patch -p1 --dry-run < patch_2.6.24_for_4311_2
```

If all looks good, re-run the patch command and remove the --dry-run to do it for real. 

Now we got to compile our patched kernel!

If you got a dual core or quad processor, you'll be happy to use it! Give this info to the terminal _only_ 

If you got a Dual Core:

```
export CONCURRENCY_LEVEL=3
```

If you got a Quad Core:

```
export CONCURRENCY_LEVEL=5
```

because the number in the end means 1 + "the number of your processors".

Now, finally, let's compile our patched kernel (copy and paste as it is written):

```
sudo fakeroot make-kpkg --initrd --append-to-version=-some-string-here kernel-image kernel-headers
```

Let it compile...

When it has finished, you got your patched kernel in the folder /home/yourusername/src/ directory. 

It is a *deb archive (there should be two packages, one for the image, one for the headers). 

Install it and enjoy...  :)

p.s. perhaps I've forgotten one or two packages needed to perform all the operations i posted. In this case the terminal should help you ;)

_Please_ post your experience here, if this method works for you please let us all now... It is not easy to find someone that teaches you to recompile a kernel :(

---

### Post by sroland81 on 2008-06-05
Thank you very much for the quick response... i'll surely try this...

Regards,

Santiago.-

---

### Post by sroland81 on 2008-06-05
This is my status, the kernel compilation was OK, when compiling i was able to see many warning messages about some "pointers"... whatever... i installed the new patched kernel but have no nVidia graphics, no sound and in the Hardware Drivers application, it shows Broadcom driver checked and the green dot, in use.... and the wireless seems to work very nice.... i opened lots of tabs in firefox and, opened transmission torrent client.... (that was the way to hang my laptop in 2 minutes)... and it didn't hanged at all. After a while, 2 error lines in dmesg appeared:

[  860.982535] wlan0: associated
[  860.983624] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  871.065145] wlan0: no IPv6 routers present
[  918.186433] eth0: link down.
[ 1074.574308] b43-phy0 ERROR: PHY transmission error
[ 1133.012068] b43-phy0 ERROR: PHY transmission error

But only 2, i guess that this is the normal error rate? because before i used to have like tenths of these lines and lines saying "647 lines supressed" or something like that. Anyway what is the meanning of that error message... error of connection? device error?

Now i think i have to seriously thanks Slayer...


If you see that this is OK, i should find out how to install (don't know how...) the sound drivers and the nVidia video drivers... i hope somebody can help me to do this and i promess i wont badder anymore.

---

### Post by slayer^_^ on 2008-06-06
you can try recompiling WITHOUT unchecking the kernel debugging... but it should make no difference... 

however

1) nvidia drivers go away after any major kernel update or change - you can re-install it by installing the package "envyng-gtk" (that depends on "envyng") and letting it do everything

2) for the audio... well, i don't know by now. try reinstalling the "alsa" packages

please let me know your progresses ;)

---

### Post by Linuxas on 2008-06-06
Hello guys
I would like to ask a question. Is this quide for every Hp Compaq 6720s model? I have one, i installed Ubuntu and i haven't noticed any problem. I think that it has a toshiba hard disk. How can i figure out if there is the hard disk problem you mentioned?(if there is a way). If there is no way to see this, do i have to do everything said on this "how to" to fix it? 
Thank you!

---

### Post by slayer^_^ on 2008-06-06
dr paul says:

> renezito:

the following will give the Load Cycle Count. Tracking it will tell you how bad the problem is on your machine.

sudo smartctl --all /dev/sda | grep Load

you may have to install smartctl and adjust sda to meet the parameter for your hard disk.

HTH

Paul

in a previous post

---

### Post by slayer^_^ on 2008-06-06
i added the the bottom of the guide a method to correct the allocation of the video memory. Check it!

---

### Post by Linuxas on 2008-06-06
> **slayer^_^ said:**
> dr paul says:



in a previous post


Thank you for your quick response! here are the results of the command:

193 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       
876
222 Loaded_Hours            0x0032   100   100   000    Old_age   Always       -      
 18
223 Load_Retry_Count        0x0032   100   100   000    Old_age   Always       -       
0
224 Load_Friction           0x0022   100   100   000    Old_age   Always       -       
0
226 Load-in_Time            0x0026   100   100   000    Old_age   Always       -       
330


Can you understand if there is any problem?

---

### Post by Vel0x on 2008-06-06
Total Ubuntnoob here so excuse me if I make a fool of myself, but the below post found on The Enquirer suggests to change the commit instead of disabling power saving. Any thoughts? And if this idea does turn out to be a good idea how the hell do you add the command? My fstab just looks like a mess to me!

Many thanks

> It's not Ubuntu's Fault!
The "problem" is not actually a problem at all but rather a feature of the ext3 filesystem. Every 5 seconds it syncs it's journals, obviously if the disk is asleep it must wake it to do this and being a very low level process it makes sure it happens.

The solution is simply to increase the sync time by adding a "commit=xxx" line into the fstab where xxx is the number of seconds (I use 300 = 5 minutes) - do this for any ext3 drive that is mounted. I have done this on my laptop and using "smartctl" I can see that the load cycle is now only going up around once every 5 minutes.

5 seconds to 5 minutes may sound extreme, but if you are on a laptop you do not have to worry about random power outs so the only possible loss of data would be from a crash and we all know linux doesn't crash ;o)

Inquirer please spread the word!! Please post another article with this fix, everyone is looking in the wrong place (i.e. at the power management settings for a "fix" to this "bug"), if I can't publicise this fix enough everyone is going to just keep posting the stupid fix of turning off the power saving, which would give us all shorter battery lives :O(

*edit* Just starting to try and get the wireless going, my lspci doesn't list any rev 1 devices but it does list the graphics controller as rev 0c. Should I patch or go ndiswrapper?

Thanks again!

---

### Post by slayer^_^ on 2008-06-07
_To Linuxas_:

I can't understand those values, but I am pretty sure of what I've written before. So I suggest you to do a trick in order to give a longer life to the hd of your laptop.

_To Velox_:

> **Vel0x said:**
> Total Ubuntnoob here so excuse me if I make a fool of myself, but the below post found on The Enquirer suggests to change the commit instead of disabling power saving. Any thoughts? And if this idea does turn out to be a good idea how the hell do you add the command? My fstab just looks like a mess to me!

Many thanks

*edit* Just starting to try and get the wireless going, my lspci doesn't list any rev 1 devices but it does list the graphics controller as rev 0c. Should I patch or go ndiswrapper?

Thanks again!

Here's my fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=6a2ffa6e-f528-4996-84d5-686b16b2a3d2 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=74b2f489-c6be-4b25-9305-976bf92e34cb /media/archivio ext3    relatime        0       2
# /dev/sdb5
UUID=84b3c2ad-2cd8-4112-b9f2-45f144e06bcc /media/download ext3    relatime        0       2
# /dev/sdb1
UUID=BECC451ACC44CDF9 /media/windows  ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda2
UUID=32371871-cb17-45fd-b949-f5604c47f79d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

This is a device:

```
/dev/sda1
UUID=6a2ffa6e-f528-4996-84d5-686b16b2a3d2 /               ext3    relatime,errors=remount-ro 0       1
```

The one yo uquoted suggested to add commit=300 to every ext3 partition, just like this:

```
/dev/sda1
UUID=6a2ffa6e-f528-4996-84d5-686b16b2a3d2 /               ext3    relatime,errors=remount-ro 0       1 [COLOR="Red"]commit=300[/COLOR]
```

> Just starting to try and get the wireless going, my lspci doesn't list any rev 1 devices but it does list the graphics controller as rev 0c. Should I patch or go ndiswrapper?

The video card doesn't suffer of any rev01\rev02 issue, that's only for broadcom wireless cards on Hardy Heron. 
If your wireless card is a PCI Broadcom, then try the command:

```
lspci | grep Broadcom
```

The output should help you.

Please note that not every HP 6720s mounts a Broadcom wireless card, many have an Intel one (the newest, in particular).

Regards...

---

### Post by Vel0x on 2008-06-07
Great thanks! I do have a broadcom:

> 10:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 02)


So the patching should be ok then? I can't see me ever needing to use any other network device other than the built in devices.

Do you have any issues with video on your 6720s? compiz works really well and is very fast, but my only issue is the tearing (jagged lines when moving windows quickly). It's very bad even with sync to vbank switched on. Does hardy load up the correct video driver by default do you know? I also wondered if I need to set the values for the screen? (horizontal / vertical lines I think) I had to do this on my other laptop which cured it.

Cheers

---

### Post by gsczero on 2008-06-07
Certainly I don't have a HP 6720 mine is a 6710b and all drivers are working very OK, the only thing i'm having trouble with is the lid of my computer.

i did change the power configuration to "do nothing" when lid is closed but the computer still blanks the screen and when i reopen the lid it freezes completely on the last screen showed before closing the lid.

after that i'm not able to do anything (no ctrl-alt-fx), only can force the shutdown with the power button.

I'm using Hardy Heron AMD64 on this laptop.

any ideas of what could be causing the freeze?

---

### Post by slayer^_^ on 2008-06-08
_velox_: as i have written in the guide yesterday, it seems that a patch has been proposed, so you haven't to recompile a kernel. Thus, (obviously with your laptop connected to internet via ethernet) open System / Administration / Synaptic package manager , unlock the "proposed" category of the repositories, reload your packages list, mark all the updates and update. This should make your wireless device work when you install the package "b43-fwcutter".

If it doesn't work, then you can recompile your patched kernel as explained in the guide.

Please repost and let me know your progresses ;)


_gsczero_: mmm, I really don't know because I have always been interested in the 6720s. The 6720s suffered of issues like the ones you wrote about, that seem to be solved in Hardy. However I can't tell you anything 

However I am sure that here you'll find the solution:

[http://ubuntuforums.org/showthread.php?t=587390&page=3](http://ubuntuforums.org/showthread.php?t=587390&page=3)
[http://wiki.ubuntuusers.de/acpi-fix](http://wiki.ubuntuusers.de/acpi-fix)
and, of course, here: [http://ubuntuforums.org/showthread.php?t=659027&page=2](http://ubuntuforums.org/showthread.php?t=659027&page=2)

Let me know...

Regards!

---

### Post by Linuxas on 2008-06-08
@slayer^_^
I did the trick for the hard disk, but i still have a question. My laptop model is HP COMPAQ 6720S GR645EA (Intel Core 2 Duo T5470, Intel Wireless LAN 802.11a/b/g not Broadcom, 120 GB HDD possibly by Toshiba etc).Does this hdd problem exists in every 6720s model?(which one do you have?). Also, does this problem exists in every Linux version or only in Ubuntu?
Now let's say that my pc did't need that trick, is it ok that i did it? or it will be bad for my disk? 
Another question is about the "correct allocation of the video memory"
when i give sudo gedit /etc/X11/xorg.conf 
under the device section there is only this:
Section "Device"
	Identifier	"Configured Video Device"



but yours was:
Section "Device" 
          Identifier "Videocard0" 
          Driver "intel" 

so do i have to add only the underlined options you mentioned or do other changes as well?
Lastly i would like to ask you about the battery. Do you have any problems with it? I noticed that when i charge my pc(when it is turned off), when the blue light goes off (fully charged) i open my pc (after two hours for example) and the battery says 98-97% . Is this normal? I thought that it should show 100%. This doesn't happen when i charge my pc when it is open(in this case when fully charged it shows 100%).
I also have noticed that everytime i turn off my pc and turn it on after a while, my battery is 2% lower(according to Ubuntu). So is this ok? Should i do something to fix it?
Thank you very much for your time!

---

### Post by Vel0x on 2008-06-08
Slayer, your a star! Just ran through your guide above for the proposed 2.6.24-19 kernal patch and it all worked. I actually had the B43-fwcutter patch applied already so as soon as I restarted after applying 2.6.24-19 wireless just worked!

I'd missed the bit you mentioned yesterday about this patch (I was on the vodka last night!) and had actually started to go through your original guide already (which is probably quite a bad idea when half drunk but it seemed a good idea at the time...) I'd got as far as compiling the kernel but thought i'd leave the laptop imaging over night in case it got screwed when I applied it as i've spent a lot of time getting this laptop setup now. I guess I can just remove the src folder now and be back to where I was?

Not at all suggesting this is correct in any way as i'm still new to Linux, but the 'proposed' category wanted to add a hell of a lot to my machine so I unchecked all except items relating to 2.6.24-19 / source / kernal etc and it seems ok. Was I right to do this or should I just have applied the whole lot?

Thanks again for all your hard work on this. Really happy to have the last block in place!

Stephan

---

### Post by slayer^_^ on 2008-06-08
> 
I did the trick for the hard disk, but i still have a question. My laptop model is HP COMPAQ 6720S GR645EA (Intel Core 2 Duo T5470, Intel Wireless LAN 802.11a/b/g not Broadcom, 120 GB HDD possibly by Toshiba etc).Does this hdd problem exists in every 6720s model?(which one do you have?). Also, does this problem exists in every Linux version or only in Ubuntu?
Now let's say that my pc did't need that trick, is it ok that i did it? or it will be bad for my disk? 

As I wrote before, it's an Ubuntu problem (don't know about other distros), but _not an Ubuntu bug!_. The hard disk manufacturers stated that, when using the battery, in order to save power, the hard disk must do a load cycle per minute. You know, the hard disk have a limited life, that is a medium of 600.000 cycles! It means that you'd have to change your hard disk in one or two years. Uindous, for example, does not respect these directives. This trick allows you to don't respect these directives (and thus to give  your hard disk a longer life).
It is ok that you did it, you won't have any problems about it.

 
> Another question is about the "correct allocation of the video memory"
when i give sudo gedit /etc/X11/xorg.conf 
under the device section there is only this:
Section "Device"
	Identifier	"Configured Video Device"



but yours was:
Section "Device" 
          Identifier "Videocard0" 
          Driver "intel" 

so do i have to add only the underlined options you mentioned or do other changes as well?

The issue i mentioned is about the Intel 965GM X3100 video card that is present in most of the HP 6720s models. It's a kernel bug. As I can see in your xorg.conf your device is not completely configured (are you able to play 3d games like Extreme Tux Racer? I guess not).
The trick I proposed (adding lines to xorg.conf is very palliative, because noone knows the exact values of those options).
As I wrote in the guide, this bug seems to have been fixed but, in order to use it, you gotta do an update after having unlocked at least the "proposed" category (and having reloaded the package list). Try the update-method before modifying the xorg.conf file.


> Lastly i would like to ask you about the battery. Do you have any problems with it? I noticed that when i charge my pc(when it is turned off), when the blue light goes off (fully charged) i open my pc (after two hours for example) and the battery says 98-97% . Is this normal? I thought that it should show 100%. This doesn't happen when i charge my pc when it is open(in this case when fully charged it shows 100%).
I also have noticed that everytime i turn off my pc and turn it on after a while, my battery is 2% lower(according to Ubuntu). So is this ok? Should i do something to fix it?
Thank you very much for your time!

The battery charge state is always indicative, you can't expect it to be true! However you got to now that batteries tends to naturally discharge themselves naturally and, moreover, that 2% is, perhaps, discharged when the pc boots up and does all the routine-checking operations!

Ubuntu, however, tends to have a major discharge rate (than Uindous XP).

Don't be scared about it! Regards ;)

---

### Post by slayer^_^ on 2008-06-08
> Slayer, your a star! Just ran through your guide above for the proposed 2.6.24-19 kernal patch and it all worked. I actually had the B43-fwcutter patch applied already so as soon as I restarted after applying 2.6.24-19 wireless just worked!

I'd missed the bit you mentioned yesterday about this patch (I was on the vodka last night!) and had actually started to go through your original guide already (which is probably quite a bad idea when half drunk but it seemed a good idea at the time...) I'd got as far as compiling the kernel but thought i'd leave the laptop imaging over night in case it got screwed when I applied it as i've spent a lot of time getting this laptop setup now. I guess I can just remove the src folder now and be back to where I was?

Not at all suggesting this is correct in any way as i'm still new to Linux, but the 'proposed' category wanted to add a hell of a lot to my machine so I unchecked all except items relating to 2.6.24-19 / source / kernal etc and it seems ok. Was I right to do this or should I just have applied the whole lot?

Thanks again for all your hard work on this. Really happy to have the last block in place!

Stephan

Thank you! I am sorry, but i didn't understand... "b43-fwcutter" is not a patch, it is a package that downloads the broadcom wireless drivers, extracts the firmware in it and lets you use it.

So, let me understand...

1) Did you compile a patched kernel and it worked?

2) Did you just update Hardy Heron with the "proposed" category unlocked (without installing the recompiled kernel) and the "b43-fwcutter" did the job?

However:

I) If you recompiled the patched kernel and installed it, you can remove the /src directory. Perhaps you'll have to redo this recompilation every time the kernel gets a major update.

II) I never found troubles installing everything comes frmo the "proposed" category. They're usually safe (and better than the standard ones). The backports are more dangerous, but I use them too! Sometimes they make your hardware work better (for example the wireless device of my desktop works better with the backports modules than the standard ones). I suggest you to try backports too and not to be scared ;)

III) I am happy to have helped you and others with this guide (I knew it was needed). I always post my experiences and the things I learn. Don't forget to do the same when you'll be a Linux Guru, because the community behind it is what makes Ubuntu special ;)

Have a nice day :popcorn:

---

### Post by Vel0x on 2008-06-08
> 2) Did you just update Hardy Heron with the "proposed" category unlocked (without installing the recompiled kernel) and the "b43-fwcutter" did the job?

Yes this one. I got to the point of your guide just before actually installing the patched kernal I.E. I got to here: 

> When it has finished, you got your patched kernel in the folder /home/yourusername/src/ directory. 

It is a *deb archive (there should be two packages, one for the image, one for the headers). 

Install it and enjoy... 

..then I stopped and then used the "proposed" solution above so I have the .deb kernal but have not used it so hopefully I should be safe with future patches!

Cheers

---

### Post by Linuxas on 2008-06-08
> **slayer^_^ said:**
> 
The issue i mentioned is about the Intel 965GM X3100 video card that is present in most of the HP 6720s models. It's a kernel bug. As I can see in your xorg.conf your device is not completely configured (are you able to play 3d games like Extreme Tux Racer? I guess not).
The trick I proposed (adding lines to xorg.conf is very palliative, because noone knows the exact values of those options).
As I wrote in the guide, this bug seems to have been fixed but, in order to use it, you gotta do an update after having unlocked at least the "proposed" category (and having reloaded the package list). Try the update-method before modifying the xorg.conf file.



Thank you again very much for your help!:)
I really like Ubuntu and so i want it to run as well as possible, because i don't want to get back to windows. Now about the graphics card, i run without any problems compiz. I can also play tux racer but there are some "artifacts" ,i may say ,that pop up on the top of the screen while playing. I did't understand quite well what you said about doing "an update after having unlocked at least the proposed category and having reloaded the package list". I keep my system updated from the update manager and i have enabled the default repositories from the synaptic package manager. Should i do something to see if my graphics card is configured? I thought that this card is configured by default...
I've already noticed that the battery thing is a little bit tricky on Ubuntu, but it's ok...

---

### Post by slayer^_^ on 2008-06-08
Thanks to you all for having shared your precious experience!

Now, back to the video card, update manager is not enough!

Just open (if you haven't done this already) Synaptic Package manager, then find the repositories section. Be sure to enable (by checking its square) _at least_ 

-main
-universe
-restricted
-multiverse

and, (it should be) under the updates category

-hardy-proposed
-hardy-backports (not mandatory, but i suggest it... I didn't have troubles with it)

Now 

1) Reload the package list
2) Mark all upgrades
3) Apply

Try this way and let me know your progresses!

Regards...

---

### Post by Linuxas on 2008-06-08
> **slayer^_^ said:**
> Thanks to you all for having shared your precious experience!

Now, back to the video card, update manager is not enough!

Just open (if you haven't done this already) Synaptic Package manager, then find the repositories section. Be sure to enable (by checking its square) _at least_ 

-main
-universe
-restricted
-multiverse

and, (it should be) under the updates category

-hardy-proposed
-hardy-backports (not mandatory, but i suggest it... I didn't have troubles with it)

Now 

1) Reload the package list
2) Mark all upgrades
3) Apply

Try this way and let me know your progresses!

Regards...

I have already done these settings, and have my system up to date, but my xorg.conf is still the same. Does this show that my card is not configured yet? So i suppose that i have to make it manually(?)

---

### Post by jvitense on 2008-06-10
Hi there!
First of all, thank you so much for this great tutorial.
When I got my HP 6720s laptop, I installed Gutsy and everything worked fine (except Compiz 3D desktop effects). After I've upgraded to Hardy 2.6.24-19-generic, I have two issues remaining:
1) Hibernate does not work properly. After RAM is written to the hard disk, the laptop does not fully shut down. The power switch goes off for 7 seconds. Then, the laptop boots up all, restoring the state when I clicked on "Hibernate". Suspend to RAM and normal shutdown both are working fine. So why doesn't the laptop power down correctly with hinernate?
2) Compiz 3D desktop is ugly: When I switch on the 3D desktop features, they work fine - as long as they are the only 3D graphical things running. Then I start google earth for example. When I switch windows to Firefox, the picture of the earth from google earth is still all over the screen.

Concerning the hard disk bug, I found a debian fix at:
[http://wiki.ubuntuusers.de/Notebook-Festplatten-Bug](http://wiki.ubuntuusers.de/Notebook-Festplatten-Bug)
This worked fine for me.

Greetings and keep up the good work,
Jan

---

### Post by gsczero on 2008-06-10
> **slayer^_^ said:**
> 


_gsczero_: mmm, I really don't know because I have always been interested in the 6720s. The 6720s suffered of issues like the ones you wrote about, that seem to be solved in Hardy. However I can't tell you anything 

However I am sure that here you'll find the solution:

[http://ubuntuforums.org/showthread.php?t=587390&page=3](http://ubuntuforums.org/showthread.php?t=587390&page=3)
[http://wiki.ubuntuusers.de/acpi-fix](http://wiki.ubuntuusers.de/acpi-fix)
and, of course, here: [http://ubuntuforums.org/showthread.php?t=659027&page=2](http://ubuntuforums.org/showthread.php?t=659027&page=2)

Let me know...

Regards!

Hello Slayer!!!

I tried this trick before, when i was using kernel 2.6.24-16 and didn't work

echo 1 > /proc/acpi/video/*/DOS

but now i'm using 2.6.24-18 and give this another try and It Works!!!!

now i'm able to close the lid without completely freeze my system.

thank you for the tip on the disk eating problem, i'm now more confident that my system is running ok.

Maybe i will try to do a Thread regarding only the 6710b with the info i have recopilated for my system.

Thanks a lot!

---

### Post by slayer^_^ on 2008-06-12
I'll search something more about the video card in the weekend. Please note that you can add the options to the xorg.conf file that you find on the intel website.

Stay tuned for more ;)

Have a nice day

---

### Post by Vel0x on 2008-06-12
My laptop is running brilliantly now thanks to this guide except for one last issue: I still get some 'tearing' on my screen. When moving windows about quickly (can I use that word to describe a open application on Linux or will I lynched?) they have jagged edges. 

Only as an example as this problem has nothing to do with gaming, when playing a fast PC game the setting to stop this kind of effect is described as "wait for vertical sync" if that helps. My eyes are very sensitive to this tearing for some reason hence why I'd like to get it resolved if poss. I have enabled the "sync to vblank" setting in Compiz but that didn't help.

I believe the fix on my last laptop was to enter the horizontal & vertical sync values for the laptops TFT but I can't find these values for the 6720s. I thought I was onto a winner with this page, but my Xorg.conf does not show the same values:

[http://www.x.org/wiki/FAQVideoModes](http://www.x.org/wiki/FAQVideoModes) around the center of the page. Section title is "Obtaining modelines from Xorg log"

My Xorg shows: velox@linux:~$ grep sync /var/log/Xorg.0.log
(II) intel(0): Modeline "1280x800"x0.0   71.11  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.4 kHz)

.....which I presume doesn't help?

Cheers

Stephan

---

### Post by slayer^_^ on 2008-06-13
As far as I know the bug with the 3d (and other things) has not been solved yet.

You can find more info here
[https://bugs.launchpad.net/ubuntu/hardy/+source/mesa/+bug/120834](https://bugs.launchpad.net/ubuntu/hardy/+source/mesa/+bug/120834)

Let me know your progresses ;)

I'll see what I can do...

---

### Post by renezito on 2008-06-13
> **renezito said:**
> Thanks for your post. I was looking for a EASY solution without ndiswrapper. I'm going to try it (HP dv6420la, BCM4312 Rev 2) and then posts my results, I hope not to install ndiswrapper as I did it with Gutsy. Remember to change the linux directory, but it will depends on your kernel compilation, because by default there is no a linux directory.
About your commentary "UBUNTY EATS YOUR HARD DISK", How can I now o Where can I find the cycles p/m that is configured in my fresh install? Is there a file or its by default?

As I said, I come to post my results!!!
Thank you very much!!! I just update, upgrade, update, upgrade, then enabled restricted firmware drivers and reboot.  My wireless device is working!!! ... thanks again :):):)

---

### Post by sroland81 on 2008-06-14
Hey Slayer, i couldn't work out the nVidia and sound drivers and i had to get the machine ready for work 2 days later, and the solution was installing all again, that wasn't so hard because i backuped before.... but this time, instead of recompiling the kernel, y used the second method you describe... with ndiswrapper... and it worked in a snap, y didn't even compile ndiswrapper.... i followed every command you posted and worked perfectly, even better than the kernel compile, and this is because that in dmesg i have NO message of PHY0-error... transmission error... whatever.... I have not seen this messages any more... GREAT !!
So, i'm back with the wireless at full throtle!!! and no hangs, no disconnections... just working! Now i have the WL (wierdy lines) at the shutdown, instead of probress bar... like X server gone for good.
The WL problem is even when logging out and re enter in the GDM user login window.... the WL appears in the transition.... gdm? xorg? WTF?

Regards,

Santiago.-

---

### Post by slayer^_^ on 2008-06-15
> **sroland81 said:**
> Hey Slayer, i couldn't work out the nVidia and sound drivers and i had to get the machine ready for work 2 days later, and the solution was installing all again, that wasn't so hard because i backuped before.... but this time, instead of recompiling the kernel, y used the second method you describe... with ndiswrapper... and it worked in a snap, y didn't even compile ndiswrapper.... i followed every command you posted and worked perfectly, even better than the kernel compile, and this is because that in dmesg i have NO message of PHY0-error... transmission error... whatever.... I have not seen this messages any more... GREAT !!
So, i'm back with the wireless at full throtle!!! and no hangs, no disconnections... just working! Now i have the WL (wierdy lines) at the shutdown, instead of probress bar... like X server gone for good.
The WL problem is even when logging out and re enter in the GDM user login window.... the WL appears in the transition.... gdm? xorg? WTF?

Regards,

Santiago.-


wireless device: it has been updated, now the device works with an update (after having unlocked the "hardy-proposed" repositories)

video card device: try installing the package "envyng-gtk" , it searches, downloads and installs the correct nvidia or ati drivers

weird lines at startup\shutdown : the package "startupmanager" allows you to configure these two things (i changed 'em with better ones that i found in [www.gnome-look.org](www.gnome-look.org) )

let me know...

have a nice day ;)

---

### Post by apos on 2008-06-15
> UBUNTU EATS YOUR HARD DISK

Put 99-hdd-spin-fix.sh into 

 /etc/acpi/suspend.d/
 /etc/acpi/resume.d/
 /etc/acpi/start.d/ 


Just like to remark, that ubuntu hardy / 8.04 uses **pm-utils** package for suspend/hibernation.

The corresponding files are located in 

```
/etc/pm/sleep.d/
/usr/lib/pm-utils/sleep.d/
```

Therfore you should put your script into **/etc/sleep.d/** instead.

Please correct me, if I am wrong.
Greet's Axel

---

### Post by sroland81 on 2008-06-16
I changed the boot splash to the fingerprint usplash, and i have no shut down progress bar.... even with this new usplash... Don't know why... and some times i have WL all over the shutdown... i can take a pic of that for you can see it.

I noticed that using compiz-fusion sometimes making right click the menu box appears but it is filled with color lines, and a fraction pf a second later the menu appears normally... i noticed this also with the entire window of evolution mail... sometimes it last for half a second... may be a problem with the video driver? buffer? thanks for everything....

Also noticed that the click sound of mi hard drive is not gone.... it makes like 2 or 3 per session... (3 or 4 hours)...

The sound is like openning the CD drive... it makes a high pitch sound like something is released. Ovbiously is not that loud... and it may it depends on what CD drive you have to think in a good comparison... but it reminds me that...

Any suggestion thanks...

---

### Post by slayer^_^ on 2008-06-17
> **apos said:**
> Just like to remark, that ubuntu hardy / 8.04 uses **pm-utils** package for suspend/hibernation.

The corresponding files are located in 

```
/etc/pm/sleep.d/
/usr/lib/pm-utils/sleep.d/
```

Therfore you should put your script into **/etc/sleep.d/** instead.

Please correct me, if I am wrong.
Greet's Axel

I guess I must study this [https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/59695](https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/59695) and this: [http://en.opensuse.org/Disk_Power_Management](http://en.opensuse.org/Disk_Power_Management)

I'll see what I can do when I've got time to do it... What do you know about it?

> **sroland81 said:**
> I changed the boot splash to the fingerprint usplash, and i have no shut down progress bar.... even with this new usplash... Don't know why... and some times i have WL all over the shutdown... i can take a pic of that for you can see it.


Is the same to me with a totally different machine... If you search on launchpad you'll find that is a bug of the "startupmanager" package, not of the laptop.


> I noticed that using compiz-fusion sometimes making right click the menu box appears but it is filled with color lines, and a fraction pf a second later the menu appears normally... i noticed this also with the entire window of evolution mail... sometimes it last for half a second... may be a problem with the video driver? buffer? thanks for everything....

The X3100 video card actually has some issues that have not been solved. I've read it has been solved for Ubuntu 8.10 Intrepid Ibex. I hope it will be solved for Hardy too... You can find more info here [https://bugs.launchpad.net/bugs/120834](https://bugs.launchpad.net/bugs/120834)


> Also noticed that the click sound of mi hard drive is not gone.... it makes like 2 or 3 per session... (3 or 4 hours)...

The sound is like openning the CD drive... it makes a high pitch sound like something is released. Ovbiously is not that loud... and it may it depends on what CD drive you have to think in a good comparison... but it reminds me that...

Any suggestion thanks...

Mmm, try this on terminal and see if it works:

In terminal:

```
sudo apt-get install laptop-mode
```

Thern:

```
sudo laptop-mode start
```

Now let's cofigure it_

```
sudo gedit /etc/laptop-mode/laptop-mode.conf
```

it gotta look like this:

```
# Enable laptop mode when on battery power.
ENABLE_LAPTOP_MODE_ON_BATTERY=1

# Enable laptop mode when on AC power.
ENABLE_LAPTOP_MODE_ON_AC=1
```

If it doesn't work try this:

```
sudo hdparm -B 255 /dev/sda
```

and see if it works.

Please let me know which method works better for you.

have a nice day ;)

---

### Post by shoaibi on 2008-06-17
any way to get 6720s's modem working?

---

### Post by slayer^_^ on 2008-06-18
ah........ I never thought about the 56k modem!

I'll see what I can do...

---

### Post by sreenathsreenath on 2008-07-01
This how to is great, i was breaking my head with trying to get my broadcom card to work, but with no luck after 2 days and 500mb of download. Thats when i stumbled on this document, it hardly took me 5 minutes and my wireless was working with the ndiswrapper package.

You are the Dude man.. !!!!

---

### Post by Bucky Ball on 2008-07-08
> ... try to unlock the "proposed" repository and do a full update of Hardy. Then install the package b43-fwcutter. It has been reported that working drivers have been put there. Just if this doesn't work go forward.

When I upgraded to Hardy, this was all done easily and my wireless card was up and running in 5 minutes. All seemed a bit too easy after wracking my brain for months with Gutsy. Excellent, worked almost 'out of the box'.

---

### Post by sroland81 on 2008-07-08
New about my WL that i talked before. A couple of weeks ago, i plugged a LCD TFT flat external monitor in my laptop and everything was delicious. I had fingerprint usplash in both monitors at the same time... and when the sesion started, the external went off and i logged in. Then went to the nVidia X server settings and enabled the external monitor in the TwinView mode and i had dual desktop... a 2-monitor sized desktop... very useful. Then (the relevant thing), when shutdown, in the laptop screen the WL appeared as usual, BUT the fingerprint usplash of shutdown was shown beautiful in the external LCD monitor that i had plugged!!! so, i guess this may help....

Thanks, 

Santiago.-

---

### Post by pleusicles on 2008-07-24
I bought a 6720s a couple of days ago and installed Hardy (8.04.1, KDE4 edition) on it. I decided to post my experiences here, just to summarize the current state of affairs on this hardware. But first of all, many thanks to Slayer and others in this thread, it was a great help!

- I used the Alternate CD; had to boot it with vga=791
- my model shipped with an Intel wifi, which worked out of the box
- Intel X3100 video worked without problems, I did not have to use the tricks mentioned on the first page under "Correct allocation of video memory". Composite effects in KDE4 work beautifully.
- I still had to use the fix for "Closing the lid makes your system freeze"
- I also applied the "Ubuntu eats your hard disk" fix, but I am experimenting with ```
hdparm -B 200 -S 252 /dev/sda
``` which is mentioned on the Opensuse page linked in by Slayer. I am not experiencing more Load_Cycle_Counts this way than with power management turned off completely (-B 255).

- there was a problem with changing lcd brightness. I could change it with fn+F7/F8, but in a few seconds it was restored to 100%, even when running on battery. I found [Bug 201933]("https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/201933") about a similar problem with the i915 chipset which has been fixed, but not on i960/i965 the hp6720s has. The fix suggested in the last comment on the bug helped: ```
echo "blacklist video" >> /etc/modprobe.d/blacklist
```

- it's probably not related to the laptop, but something strange happened with grub. Windows Vista was pre-installed, I left it on the machine and shrinked its partition (in the Kubuntu installer). For a while, everything worked, I could boot both systems. Then grub began refusing to boot Vista (or: Vista began refusing to be booted by grub ;) ), the error message from grub being "Selected item can not fit into memory". I changed root to rootnoverify in Vista' menu.lst entry and the problem went away. I'm still unsure what caused it; I don't remember changing anything related to grub when it appeared.

That's for now. All in all, I am very satisfied with how this laptop functions under linux!

---

### Post by dixon on 2008-08-02
Thanks pleusicles the
```
[FONT=monospace]echo "blacklist video" >> /etc/modprobe.d/blacklist[/FONT]
```
line fixed my brightness and also closing the lid problem...

---

### Post by pleusicles on 2008-08-03
Yes, the other fix for the lid closing problem is not needed if the video module is blacklisted. However, I've just [found]("https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/121833/comments/11") another solution which seems to work. Instead of blacklisting 'video' altogether, you can add```
options video no_automatic_changes=0
``` to **/etc/modprobe.d/options**, and apply the lid closing fix as well. This way I can both set brightness manually using the fn keys, and use the auto-dimming feature of e.g. kpowersave, which is really handy because the bottom part of the lid on the 6720s becomes really hot when the screen is constantly on 100% brightness.

---

### Post by Linuxas on 2008-08-08
> **pleusicles said:**
> Yes, the other fix for the lid closing problem is not needed if the video module is blacklisted. However, I've just [found]("https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/121833/comments/11") another solution which seems to work. Instead of blacklisting 'video' altogether, you can add```
options video no_automatic_changes=0
``` to **/etc/modprobe.d/options**, and apply the lid closing fix as well. This way I can both set brightness manually using the fn keys, and use the auto-dimming feature of e.g. kpowersave, which is really handy because the bottom part of the lid on the 6720s becomes really hot when the screen is constantly on 100% brightness.

Hello everyone! The whole thread is very useful for all 6720 owners. I have solved many problems because of you guys!:) I solved the "closing lid" as well as the brightness problem with the "blacklist video" thing. 

Maybe your solution is beter. So can you explain it a little bit more? my /etc/modprobe.d/options looks like this:

# Enable double-buffering so gstreamer et. al. work
options quickcam compatible=2

# Default hostap to managed mode
options hostap_pci iw_mode=2
options hostap_cs iw_mode=2

Where do i have to write the code you gave?(options video no_automatic_changes=0)

Now again for the hard disk thing, slayer^_^ what do you thing? I used the code you suggest on the guide, but i read some posts with different ways to do the same thing. Should i try something else, or leave it that way?

---

### Post by pleusicles on 2008-08-13
> **Linuxas said:**
> Maybe your solution is beter. So can you explain it a little bit more? my /etc/modprobe.d/options looks like this:

# Enable double-buffering so gstreamer et. al. work
options quickcam compatible=2

# Default hostap to managed mode
options hostap_pci iw_mode=2
options hostap_cs iw_mode=2

Where do i have to write the code you gave?(options video no_automatic_changes=0)

Sorry, I can't explain it better. I've seen it in the bug report I've linked to, tried it, and it worked - better than the blacklist solution, since I can use both autodimming and suspend.

You have to add the the "options" line as a new line at the end (or at the beginning, it does not matter) of /etc/modprobe.d/options.

---

### Post by slayer^_^ on 2008-08-14
I´m sorry guys, but I´m on vacation right now... :(

I&#314;l update the guide as soon as I have time, as I always did..

Please try the new restricted drivers for the broadcom wireless and tell me if they work for you (and, obviously, if they work better than the other ones).

Here is the link...

[http://ubuntuforums.org/showthread.php?t=765448](http://ubuntuforums.org/showthread.php?t=765448)

Greetings from Hungary :D

---

### Post by jarome on 2008-08-22
On my HP mini-note, the hardware fwcutter left the wireless light off. Installing ndiswrapper turned it on, but it still does not work.

```

~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1f:29:9a:e4:14  
          inet addr:192.168.1.28  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:29ff:fe9a:e414/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:31 errors:0 dropped:0 overruns:0 frame:0
          TX packets:47 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4298 (4.1 KB)  TX bytes:7293 (7.1 KB)
          Interrupt:22 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6270 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6270 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6059635 (5.7 MB)  TX bytes:6059635 (5.7 MB)

wlan1     Link encap:Ethernet  HWaddr 00:21:00:36:db:fd  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21 Memory:fdffc000-fe000000 

wlan1:avahi Link encap:Ethernet  HWaddr 00:21:00:36:db:fd  
          inet addr:169.254.9.33  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:21 Memory:fdffc000-fe000000 
```

what is wlan1.avahi? It is the interface used in the wireless gizmo at the top right of my screen, and when I try to configure that, it says the interface does not exist.

It sometimes seems to work, but is in fact going through the wires connection (since it dies when I unplug it).

Help please,
Jim

---

### Post by slayer^_^ on 2008-08-23
are you sure that you've got a broadcom wireless device? some models have an intel one that works out of the box...

the method on the guide should work, however...

check if you've got a broadcom device and which model is it.

regards

---

### Post by jarome on 2008-08-23
> **slayer^_^ said:**
> are you sure that you've got a broadcom wireless device? some models have an intel one that works out of the box...

the method on the guide should work, however...

check if you've got a broadcom device and which model is it.

regards

I for sure have a BCM4312 rev2

---

### Post by slayer^_^ on 2008-08-25
i saw you have solved by changing your network manager into wicd. that's good, I'm happy for ya :D

---

### Post by rozyk on 2008-08-29
I had a little problem with setting:

> echo 1 > /proc/acpi/video/*/DOS

via rc.local

So, in order to avoid further problems, that's the way how I(*) did it:

> In : /etc/sudoers:
comment:
#%admin ALL=(ALL) ALL

uncomment:
%sudo ALL=NOPASSWD: ALL


Add yourself to sudo group:
> gpasswd -a $username sudo

Make script:
> 

#!/bin/bash

sudo chmod 666 /proc/acpi/video/*/DOS
sudo echo 1 > /proc/acpi/video/*/DOS



And add it to boot level.

If somebody else has/had such a problem it would be a good idea to stuck this to the first post of this topic.

Sorry for my English and if there is any mistake, please correct it. 

rozyk

*- with a friend's help;)

---

### Post by rcostanz on 2008-09-18
I have a laptop hp compaq 6720s with ubuntu 8.04: this thread is the most beautiful place where you can fix every problem !!! Thank you.
Now I have a little problem to ask for.
My Wireless 3945ABG is working right, so I can use without problem my work wifi connection.
My problem is about my bluetooth connections, I can't use bluetooth to connect with my mobile and I don't know if I have to install a particular driver or if I have to use/install a particular software to do it :confused:

Every ideas to fix my problem is appreciated!!!!
  

lspci
00:00.0 Host bridge: Intel Corporation Mobile GME965/GLE960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GME965/GLE960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GME965/GLE960 Integrated Graphics Controller (rev 0c)
00:19.0 Ethernet controller: Intel Corporation 82562GT 10/100 Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
10:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

Thank you in advance for all your work

Riccardo

---

### Post by AlesUbu123 on 2008-09-20
Hey Riccardo,
what does this command tell you:
```
hcitool dev
```

---

### Post by depeha on 2008-09-20
@ slayer^_^: thx for great tutorial :D
But I have still one problem... look on this: [http://www.youtube.com/watch?v=Y506mfeWEYQ](http://www.youtube.com/watch?v=Y506mfeWEYQ)
Starting up is so slow without reducing LCD's LED intensity... (I've sloved second problem with login on that video)

---

### Post by slayer^_^ on 2008-09-22
actually i am still in hungary, so i cannot fully work on the laptop troubles... well, what can i say, the intrepid ibex is gonna come out soon, as well. I think I'll wait for it.

BUT

some little troubles left in hardy (and that's what i am asking you for feedback)

1) the hard drive cycle count... 

2) 3d acceleration

3) when closing the lid the laptop doesn't freeze (with the trick) but the screen isn't shut down

any ideas?

---

### Post by depeha on 2008-10-06
my laptop was freezing also with your guide...
but I found this:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/65027](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/65027)

and editing /etc/acpi/lid.sh works...
it's not freezing anymore, but display is turned off just for 1-2 sec.
I think is because of this:
> 
#!/bin/sh

# turns the screen off on lid close & on on lid open

grep -q closed /proc/acpi/button/lid/*/state
if [ $? = 0 ]
then
       sudo /usr/sbin/vbetool dpms off
else
       **sudo /usr/sbin/vbetool dpms on**
fi

and I think it should look like this:

> 
#!/bin/sh

# turns the screen off on lid close & on on lid open

grep -q closed /proc/acpi/button/lid/*/state
if [ $? = 0 ]
then
       sudo /usr/sbin/vbetool dpms off
fi

grep -q open /proc/acpi/button/lid/*/state
if [ $? = 0 ]
then
       sudo /usr/sbin/vbetool dpms on
fi

But I'm not programmer or something, so I don't know right form...

---

### Post by mad_gcc on 2008-10-08
> **depeha said:**
> my laptop was freezing also with your guide...
but I found this:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/65027](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/65027)

and editing /etc/acpi/lid.sh works...
it's not freezing anymore, but display is turned off just for 1-2 sec.
I think is because of this:


and I think it should look like this:



But I'm not programmer or something, so I don't know right form...

I've been following this thread for a couple of days, trying to help a friend of mine. I helped this friend some time ago to buy a new laptop. It was an HP Compaq 6720s.

Well, he eventually got sick of the preloaded Windows Vista that came with it, and installed a fresh copy of Kubuntu Hardy.

So far, so good. He had some other problems, but not directly related to Kubuntu itself, but related to the lack of knowledge of his new system.

One of the problems he faced was the complete freeze of the system when closing the lid. 

After some search, I found a lot of information about this (well known) problem. It was an ACPI problem. Some people suggested soft hacks (e.g. the file /etc/acpi/lid.sh), some other saying that echoing this and that to an acpi control file would do it.

Definitely, the *best* thing you can do about this is to upgrade the BIOS of your machine. Just download the softpaq available on the HP support page to this laptop:

[http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareDescription.jsp?lang=es&cc=es&prodTypeId=321957&prodSeriesId=3442832&prodNameId=3442833&swEnvOID=1093&swLang=13&mode=2&taskId=135&swItem=ob-63988-1](http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareDescription.jsp?lang=es&cc=es&prodTypeId=321957&prodSeriesId=3442832&prodNameId=3442833&swEnvOID=1093&swLang=13&mode=2&taskId=135&swItem=ob-63988-1)

Download and apply it. It will (hopefully) solve all the ACPI problems like the one I've related above.

Just my 2 cents.

:-)

---

### Post by shoaibi on 2008-10-08
@mad_gcc:
how am i suppose to apply that upgrade under ubuntu? i don't do dual boot. Only have Ubuntu.

@Everyone:
Anyone successfull in configuring its modem?

---

### Post by dixon on 2008-10-10
> **shoaibi said:**
> @mad_gcc:
how am i suppose to apply that upgrade under ubuntu? i don't do dual boot. Only have Ubuntu.

@Everyone:
Anyone successfull in configuring its modem?

Last time I upgraded BIOS I used [ this ]("http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareDescription.jsp?lang=en&cc=us&prodTypeId=321957&prodSeriesId=3442832&prodNameId=3442833&swEnvOID=1093&swLang=8&mode=2&taskId=135&swItem=ob-62319-1"). It's a utility to create bootable media for bios upgrading and it ran fine in wine.

---

### Post by slayer^_^ on 2008-10-12
yeah, but upgrading th ebios is very dangerous... with laptops mor ethan with desktop computers...

...is it worth?

---

### Post by shoaibi on 2008-10-27
[REPOST]
I am asking the same question again after this long.

Has anyone had any luck with configuring its modem? I tried and failed..

---

### Post by slayer^_^ on 2008-10-28
not me... sorry... :(

---

### Post by Gardenee on 2008-11-01
what about Ubuntu 8.10 ?

---

### Post by depeha on 2008-11-03
Ubuntu 8.10...

**WiFi** still doesn't work, so you must use tutorial in first post.

**Lid** works (almost) perfect... isn't freezing anymore, but if you want turn off display by closing lid, you must turn off display some way, and after that it will turn off always when you close lid :D

BTW here is lid.sh: (if someone wont update)

```
#!/bin/bash
# TODO:  Change the above to /bin/sh

test -f /usr/share/acpi-support/state-funcs || exit 0

. /usr/share/acpi-support/power-funcs
. /usr/share/acpi-support/policy-funcs
. /etc/default/acpi-support

[ -x /etc/acpi/local/lid.sh.pre ] && /etc/acpi/local/lid.sh.pre

if [ `CheckPolicy` = 0 ]; then exit; fi

grep -q closed /proc/acpi/button/lid/*/state
if [ $? = 0 ]
then
    for x in /tmp/.X11-unix/*; do
	displaynum=`echo $x | sed s#/tmp/.X11-unix/X##`
	getXuser;
	if [ x"$XAUTHORITY" != x"" ]; then
	    export DISPLAY=":$displaynum"	    
	    . /usr/share/acpi-support/screenblank
	fi
    done
else
    for x in /tmp/.X11-unix/*; do
	displaynum=`echo $x | sed s#/tmp/.X11-unix/X##`
	getXuser;
	if [ x"$XAUTHORITY" != x"" ]; then
	    export DISPLAY=":$displaynum"
	    grep -q off-line /proc/acpi/ac_adapter/*/state
	    if [ $? = 1 ]
		then
		if pidof xscreensaver > /dev/null; then 
		    su $user -c "xscreensaver-command -unthrottle"
		fi
	    fi
	    if [ x$RADEON_LIGHT = xtrue ]; then
		[ -x /usr/sbin/radeontool ] && radeontool light on
	    fi
	    if [ `pidof xscreensaver` ]; then
		su $user -c "xscreensaver-command -deactivate"
	    fi
	    su $user -c "xset dpms force on"
	fi
    done
fi
[ -x /etc/acpi/local/lid.sh.post ] && /etc/acpi/local/lid.sh.post
```

---

### Post by Gardenee on 2008-11-10
wireless device worked fine for me in 8.04.
after upgrading to 8.10, the **network-manager** of gnome doesn't worked properly - i've installed **wicd**

so, wicd collapsed, wireless doesn't work. (have intel device, not broadcom)
also had mobile device, connected it with HSOconnect - now it's crashing too... :S

oaky, so we need a new topic of HP Compaq 6720s and Ubuntu 8.10 :)

---

### Post by vdfbelial on 2008-11-30
> **Gardenee said:**
> oaky, so we need a new topic of HP Compaq 6720s and Ubuntu 8.10 :)

I'm a 6720s owner with Ubuntu Hardy Heron. I tested out 8.10 and had wireless problems and not only, so yes, it might be a good idea to have such a thread.

---

### Post by slayer^_^ on 2008-12-10
here you are, as you requested...


_The new thread dedicated to HP Compaq 6720s and Ubuntu 8.10 Intrepid Ibex_

[http://ubuntuforums.org/showthread.php?p=6348468#post6348468](http://ubuntuforums.org/showthread.php?p=6348468#post6348468)

I found that my only problem with the new distro was the wireless device, but it was very easy to solve the trouble... take a look and, of course, post your experience!

We'll solve all your problems together ;)

---

