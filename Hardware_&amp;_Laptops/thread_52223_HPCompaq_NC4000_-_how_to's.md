---
title: "HP/Compaq NC4000 - how to's"
date: 2005-07-27
forum: Hardware &amp; Laptops
---

### Post by netsyd on 2005-07-27
Hi All,

I thought I'd put this up for future reference if someone strolls along looking for some information on this laptop... I've posted a bunch of walkthrough type information on how I got suspend2 working, madwifi, and I'll be updating it later on in the week with instructions for Crossover Office which was pretty simple...

Anyway since Ubuntu is my primary OS on this laptop if you have one feel free to shoot me over any questions you may have....

[http://www.netsyd.com/content.php?content.4](http://www.netsyd.com/content.php?content.4)   (sorry the site is slow, but hey... Comcast only handles so much.   :)

[IMG]http://www.netsyd.com/e107_plugins/coppermine_menu/albums/userpics/10001/normal_Screenshot.png[/IMG]

(yes, that screenshot has shortcuts for Word, Outlook, Excel, etc... Crossover Office Kicks Ass!! Spend the $$$)

Documentation yet again... 

Ok, so I got rid of my Sony Vaio TR1, because it was just dammed annoying to be honest. I wasn't a big fan of the screen, despite it being quite similar to my favorite laptop the Fujitsu P2000 series. Something about the Sony just didn't work for me. Anyway, I'm back to using an HP/Compaq NC4000 just like I used to have at my old job. Great little laptop, battery life sucks though. 

So the the installation was nothing really to write home about. Ubuntu (Hoary 5.04) has done a great job with this distro... Although I wish brown wasn't their color of choice. It was very simple to do everything through the built in LAN connection and pull all the installation files off the web.

[size=6]Display [/size]

  ```
0000:01:05.0 VGA compatible controller: ATI Technologies Inc Radeon IGP 340M
```

Again nothing to write home about. 1024x768 is very standard (as opposed to the 1280x960 on the Sony) so xorg setup and ran without any tweaking what-so-ever. I have also come to understand that their at this time is no support for 3D graphics (yet) on this laptop so downloading and setting up fglrx drivers is useless. This isn't to say that the graphics don't work, but even 3d screensavers get horribly chunked.

 [size=6]Wireless[/size] 

 ```
0000:00:09.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
``` 

Can we say Madwifi? Ok, this sort of sucked, but honestly this is the most difficult thing in the installation.  All I really did was apt-get the newest kernel (2.6.10-5-686) and the kernel headers. ```
apt-get install linux-image-2.6.10-5-686 linux-headers-2.6.10-5-686
```The I ran the following bits of code:

 ```
sudo apt-get install build-essential
sudo apt-get install wireless-tools
wget http://otaku42.de/madwifi/madwifi-cvs-current.tar.gz
sudo apt-get install sharutils
tar xvzf madwifi-cvs-current.tar.gz 
cd madwifi
KERNELPATH=/usr/src/linux-headers-`uname -r`; export KERNELPATH
KERNELRELEASE=`uname -r`; export KERNELRELEASE
sudo make
sudo make install
``` 
Following all of this I rebooted and the card showed up in the network utility. Realistically I could have configured everything using iwconfig, but I was too lazy. 

Thanks to elvis (ubuntuforums) for his walkthrough on Madwifi... [http://ubuntuforums.org/showthread.php?t=38972](http://ubuntuforums.org/showthread.php?t=38972)

Also I found that once I got suspend2 working with this laptop, in order to not have a pain in the ass time getting wireless to come back I needed to turn off wireless before it takes a nap. so I wrote 2 short scripts because screwing around with the hibernate script just looked like trouble. One script called sleepy.sh and one called wake.sh. I put both of these in my home directory so before I close the lid I just run sleepy....
```
 sudo rmmod wlan_wep
sudo rmmod ath_pci
sudo ifdown ath0
```

and when the laptop comes out of suspend ... I run the wake script

```

sudo modprobe ath_pci
sudo modprobe wlan_wep
sudo ifup ath0
```

Obviously from looking the scripts... I have disabled sudo from asking me for my password. Bad Bad Bad!!! Don't do this. (Ah screw it. I did it anyway.)


 [size=6]Sleep/Hibernate[/size] 

Yea dream on. This is why Linux on laptops sucks. Using the default suspend/hibernate scripts It works, but only if you have no intentions of using the laptop when it comes back up. The screen doesn't come back and so it leaves you staring at the blackened screen watching your dreams of Linux on a laptop fade away. But, hark... I hear Suspend2 Calling. 

URL = [www.suspend2.net](www.suspend2.net)
URL = [www.kernel.org](www.kernel.org)

Ok, put simply enough you need to recompile the kernel (from a vanilla kernel) then patch it with Suspend2. Sounds like a pain in the ass, and honestly if it doesn't go right it can be, but hopefully this will help anyone who intends to do this. I'm including my .config for anyone on an NC4000. It's not perfect but it works for me. Get it here: [www.netsyd.com/config.txt](www.netsyd.com/config.txt)

Ok,so run on over to kernel.org and grab the tar.bz2 kernel package for 2.6.12.3 (this is just what I used, you might be able to get away with another version.) Save that to your home folder. Then go get the software-suspend-2.1.9.9-for-2.6.12 files and the newest hibernate script and save those to your home directory as well. 

OK, lets get on with the fun. 

```
In your home directory:
mkdir build           *this is where we will build the kernel
mkdir swsusp2     *this is where we will unzip suspend2
mkdir hibernate    *this is where we will unzip the hibernate script

tar xjf linux-2.6.12.3.tar.bz2 --directory build     * this unzips the kernel to the build direcoty
cd build/linux-2.6.12.3/   *this puts us into the build directory
```
* now save the config file above to this directory as .config
you will need some basic utilities so lets get those:```

sudo apt-get install build-essential
sudo apt-get install libncurses5-dev
```
Now that that's done lets get to work on the kernel
```
 make mrproper
make old config   * this may leave some unanswered questions... select what you think is best
make menuconfig  * go through this... and check if you need anything that I didn't select. 
```
Once you are done in the menuconfig, it's time to build that kernel. 
```
 make bzImage   *this builds the bzImage for us
make modules    *this builds the modules for our kernel  -- be aware that if it exits with an error here you need to fix it first before continuing!!! 
```
Ok, by now you are wondering what is going on. Well this all takes some time. Quite some time!! Once you have a clean build of the modules, lets install everything!
```
 sudo make modules_install   *this installs the modules to /lib/modules/2.6.12.3 
sudo cp /arch/i386/boot/bzImage /boot/vmlinuz-2.6.12.3  * moves the kernel to the boot directory
sudo chmod 644 /boot/vmlinuz-2.6.12.3   *makes our kernel executable
sudo cp System.map /boot/System.map-2.6.12.3   *copies our System.map file to the /boot directory
cd /boot     *puts us into the /boot directory
sudo ln -sf System.map-2.6.12.3 System.map    * creates a symbolic link from the System.map file in the /boot directory to our System.map-2.6.12.3 file.
``` 
Ok, at this point your /boot directory should like something like this:
```
drwxr-xr-x   3 root root    4096 2005-07-25 08:41 .
drwxr-xr-x  23 root root    4096 2005-07-23 13:22 ..
lrwxrwxrwx   1 root root      15 2005-07-24 21:26 config -> config-2.6.12.3
-rw-r--r--   1 root root   59797 2005-02-04 02:43 config-2.6.10-2-386
-rw-r--r--   1 root root   59423 2005-06-24 11:28 config-2.6.10-5-686
-rw-r--r--   1 root root   62118 2005-07-24 21:26 config-2.6.12.3
drwxr-xr-x   3 root root    4096 2005-07-25 08:42 grub
-rw-r--r--   1 root root 4730880 2005-07-25 00:12 initrd-2.6.12.3.img
-rw-r--r--   1 root root 4341760 2005-07-23 00:02 initrd.img-2.6.10-2-386
-rw-r--r--   1 root root 4632576 2005-07-23 19:04 initrd.img-2.6.10-5-686
-rw-r--r--   1 root root   94428 2005-03-31 04:08 memtest86+.bin
lrwxrwxrwx   1 root root      19 2005-07-25 08:41 System.map -> System.map-2.6.12.3
-rw-r--r--   1 root root  844557 2005-02-04 03:08 System.map-2.6.10-2-386
-rw-r--r--   1 root root  825157 2005-06-24 14:23 System.map-2.6.10-5-686
-rw-r--r--   1 root root  941773 2005-07-25 08:40 System.map-2.6.12.3
lrwxrwxrwx   1 root root      16 2005-07-24 21:26 vmlinuz -> vmlinuz-2.6.12.3
-rw-r--r--   1 root root 1184549 2005-02-04 03:08 vmlinuz-2.6.10-2-386
-rw-r--r--   1 root root 1229548 2005-06-24 14:23 vmlinuz-2.6.10-5-686
-rw-r--r--   1 root root 1520739 2005-07-25 08:38 vmlinuz-2.6.12.3

```
Ok, let's edit the grub menu.lst file 
```
 sudo gedit /boot/grub/menu.lst:  *ADD THE FOLLOWING ABOVE ALL OTHER KERNEL CODE
title		Ubuntu kernel 2.6.12.3 
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12.3 root=/dev/hda3 ro quiet splash
savedefault
boot
```
Save the file and give your system a reboot. Select the above line at the OS selection screen. If all went well, I'll see you back here shortly. I'm having you do all this simply to make sure that our process works and we get a good kernel. If we don't there's no sense in moving on untilwe have a working one. I would recommend doing some stress testing with your kernel build... up some stuff up, play around a bit and determine if anything is broken before moving on. 

Back? Alright, lets get going on suspend2 ... Copy the .config from your build directory (build/linux-2.6.12.3) to your home dirrectory. Now delete the entire build directory. (sudo rm -rf build)

Ok, now we are going to rebuild the kernel again from scratch this time building in suspend2. I found this to be the best way to do things since we know we have a good kernel, if something messes up it is likely suspend2 that did it and not something we missed. 

```
mkdir build
tar xjf linux-2.6.12.3.tar.bz2 --directory build 
tar xjf software-suspend-2.1.9.9-for-2.6.12.tar.bz2 --directory swsusp2
cp .config build/linux-2.6.12.3/
cd build/linux-2.6.12.3/
make oldconfig
/home/brandon/swsusp2/software-suspend-2.1.9.9-for-2.6.12/apply
make menuconfig
```
Ok, now is the time to go into the Power Management section and select the options for Suspend 2. The how to on [www.suspend2.net](www.suspend2.net) explains this quite well. (although I didn't ever find the section for userspace?)
Here's the basics: Select whether you want to suspend to swap or suspend to a file. I chose to suspend to swap and then gave it the path of /dev/hda5 which is my swap partition Yours may be different!!). I aslo disabled the old suspend...just because. Once you're done save the config. 

Let's build again!

```

make bzImage
make modules
sudo make modules_install
sudo cp arch/i386/boot/bzImage /boot/vmlinuz-2.6.12.3
sudo chmod 644 vmlinuz-2.6.12.3
sudo cp System.map /boot/System.map-2.6.12.3
cd /boot
sudo ln -sf System.map-2.6.12.3 System.map

```

Ok, init 6 and make sure it all works! (notice the refernce to suspend2 when you boot now....
If all went well you should eb abck here shortly. If so lets make hibernate work. 

```
tar xzvf hibernate-script-1.10.tar.gz
cd hibernate-script-1.10/
sudo ./install.sh      ----- chances are it gets pissed off because there is already a hibernate script where it wants to write one so it will name the new one .conf.dist or something to that effect. Well I didn't want the old one around so I chose to replace the old one. 

sudo mv /etc/hibernate/hibernate.conf.dist /etc/hibernate/hibernate.conf
```

Ok, now they recommend you run the hibernate script the first time from init 3. If you chode to do so, go right ahead. The instructions are all in the how-to from thier site. To run the script ```
sudo /usr/local/sbin/hibernate
```

That's it!!!

 [size=6]Some basic files to look at[/size] 

**Laptop Harddrive Control** This does a great job... better power management = better battery life
 ```
sudo apt-get install laptop-mode laptop-mode-tools
``` 
URL = [http://www.xs4all.nl/~bsamwel/laptop_mode/tools/faq.html](http://www.xs4all.nl/~bsamwel/laptop_mode/tools/faq.html) 


 **Grub Splash Screen**
Some handy information here about changing the splash screen for Grub... Puts a nice image behind the OS selection page...
URL = [http://sleepybuddha.sl.funpic.de/ubuntu/](http://sleepybuddha.sl.funpic.de/ubuntu/)

 **Making gnome yours....**

URL = [www.gnomelook.org](www.gnomelook.org)

System >>> Preferences >>> Theme (Change your theme. Add a new theme. Easiest to add when they are still zipped.)

Applications >>> System Tools >>> Configuration Editor >>> Apps >>> Gnome Session >>> Options (Update your splash screen with the path for your new one)

Sudo gdmsetup (Graphical tab can be used to set the screen for gdm login. Standard Greeter is where you go to set the background color for the screen that shows while gnome is setting up.)

**Replace the gnome foot with the ubuntu logo**
```
sudo cp /usr/share/pixmaps/gnome-logo-icon-transparent.png /usr/share/pixmaps/gnome-logo-icon-transparent.png.bak

sudo cp /usr/share/hwdb-client/ubuntu_logo.png /usr/share/pixmaps/gnome-logo-icon-transparent.png

killall gnome-panel
```
Excellent tip from here: URL = [http://www.ubuntuforums.org/showthread.php?t=26854](http://www.ubuntuforums.org/showthread.php?t=26854)

---

### Post by hbush on 2006-01-06
Hi netsyd,

must say I got really close to make function my wifi on nc4000. I have no experience on linux (these are my 1st three days) 

thank you for the post but it didn't went fine with me. I followed your instructions and got stuck on 
```
sudo apt-get install build-essential
sudo apt-get install wireless-tools
wget http://otaku42.de/madwifi/madwifi-cvs-current.tar.gz
**sudo apt-get install sharutils**    -->this didnt work
tar xvzf madwifi-cvs-current.tar.gz 
cd madwifi
KERNELPATH=/usr/src/linux-headers-`uname -r`; export KERNELPATH
KERNELRELEASE=`uname -r`; export KERNELRELEASE
sudo make
sudo make install
```

and kernpath&release fine 
on **make** I get 
```
root@LT:/usr/src # cd madwifi
root@LT:/usr/src/madwifi # KERNELPATH=/usr/src/linux-headers-`uname -r`; export KERNELPATH
root@LT:/usr/src/madwifi # KERNELRELEASE=`uname -r`; export KERNELRELEASE root@LT:/usr/src/madwifi # sudo make
Checking if all requirements are met... ok.
mkdir -p ./symbols
for i in ./ath_hal ath_rate/onoe ./net80211 ./ath; do \
        (cd $i; make) || exit 1; \
done
make[1]: Entering directory `/usr/src/madwifi/ath_hal'
cp ./../hal/linux/ah_osdep.c ah_osdep.c
uudecode ./../hal/public/i386-elf.hal.o.uu
make[1]: uudecode: Command not found
make[1]: *** [hal.o] Error 127
make[1]: Leaving directory `/usr/src/madwifi/ath_hal'
make: *** [all] Error 1
root@LT:/usr/src/madwifi #

```


please advice

thank you, 
h

---

### Post by hbush on 2006-01-07
> **hbush]Hi netsyd,

must say I got really close to make function my wifi on nc4000. I have no experience on linux (these are my 1st three days) 

thank you for the post but it didn't went fine with me. I followed your instructions and got stuck on 
```
sudo apt-get install build-essential
sudo apt-get install wireless-tools
wget http://otaku42.de/madwifi/madwifi-cvs-current.tar.gz
**sudo apt-get install sharutils**    -->this didnt work
tar xvzf madwifi-cvs-current.tar.gz 
cd madwifi
KERNELPATH=/usr/src/linux-headers-`uname -r` said:**
> : Entering directory `/usr/src/madwifi/ath_hal'
cp ./../hal/linux/ah_osdep.c ah_osdep.c
uudecode ./../hal/public/i386-elf.hal.o.uu
make[1]: uudecode: Command not found
make[1]: *** [hal.o] Error 127
make[1]: Leaving directory `/usr/src/madwifi/ath_hal'
make: *** [all] Error 1
root@LT:/usr/src/madwifi #

```


please advice

thank you, 
h

Hey :D this worked ... I only had to install shareutils as explained from the link on your netsyd.com site ... even a rookie like me can do it ha hahha .. thnx netsyd. 

thank you all :)

---

### Post by Offoffoff on 2007-08-04
Well... And what about IrDA? How to install it to work?
What about ATI video card (01:05.0 VGA compatible controller: ATI Technologies Inc Radeon IGP 330M/340M/350M)? Which I cannot enable to work well with direct rendering, despite messages are in logs:
```

(II) RADEON(0): [drm] Initialized kernel GART heap manager, 5111808
(WW) RADEON(0): DRI init changed memory map, adjusting ...
(WW) RADEON(0):   MC_FB_LOCATION  was: 0x1fff1e00 is: 0x1fff1e00
(WW) RADEON(0):   MC_AGP_LOCATION was: 0xffffffc0 is: 0x9c7f9c00
(**) RADEON(0): GRPH_BUFFER_CNTL from 20005c5c to 20055c5c
(II) RADEON(0): Direct rendering enabled
(**) RADEON(0): Setting up final surfaces
(**) RADEON(0): Initializing Acceleration
(II) RADEON(0): Render acceleration enabled
(**) RADEON(0): EngineInit (16/16)
(**) RADEON(0): Pitch for acceleration = 128
(**) RADEON(0): EngineRestore (16/16)
(II) RADEON(0): Using XFree86 Acceleration Architecture (XAA)

```
What about strange software modem without any known driver (ALi Corporation M5457 AC'97 Modem Controller)? Where to get it?
Please, help... I feel so suicidal...

---

