---
title: "COMPLETE HOW TO: Dell Inspiron 6400"
date: 2006-09-14
forum: Hardware &amp; Laptops
---

### Post by lifeempowered.com on 2006-09-14
**UPDATE: This is my How-To I use for Edgy Eft only, on my Inspiron 6400**

System Tested On:

Dell Inspiron 6400
1.60 Core Duo Processor
2 GB 533 RAM
160 GB HD
x1400 ATI 256MB Video Card
15.4 XGA (1280x800) w/ TrueLife
8x DVD +/- RW/CD-RW
54Mbps Dell 1390 Wireless (Broadcom driver)
S-Video/Firewire/USB/etc.

Only thing not working: Sony card reader. 

Updated as of March 28, 2007:

**Initial Setup **

1. Install base Edgy install.
2. After install, open the sources file:
```

sudo gedit /etc/apt/sources.list

```
And uncomment all entries that begin with "deb http" or "deb-src" except for the CD ROM, make sure it's commented out

3. Next update by entering the following, twice.
```

sudo apt-get update

```

4. Now open your Software Sources in: SYSTEM > ADMINISTRATION > SOFTWARE SOURCES
and make sure all the boxes under "Downloadable from the Internet" are checked.  Click "CLOSE" and then "RELOAD"

5. Go to: SYSTEM > ADMINISTRATION > UPDATE MANAGER
and first click "CHECK", then click "INSTALL UPDATES"

After your updates are finished installing, REBOOT NOW

After a reboot, create a working folder for the following install steps.  Just a way to keep your system clean.  Go into your home folder and create a folder called "install" or something.  Now open  terminal and go to that directory before you proceed.

6. Now you're going to get some tools for future steps.
```

sudo apt-get install build-essential module-assistant build-essential fakeroot dh-make debconf libstdc++5 linux-headers-$(uname -r)

```

7. Update again, just in case, and install any updates that appear in the top right corner.
```

sudo apt-get update

```

**Now you'll install your wireless device**

1. Clean your system by entering the following code.  Disregard errors as you may not have ndiswrapper.
```

sudo rmmod ndiswrapper
sudo apt-get remove ndiswrapper-utils

```

2. Download driver files.  Unzip them.
```

wget http://www.jrdw.com/linux/wireless/bcmdrivers.tar.gz
tar -xzvf bcmdrivers.tar.gz

```

3. Download latest Ndiswrapper, I've included th latest at the time of this edit.  Unzip it.
```

wget http://superb-east.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.38.tar.gz
tar -xzvf ndiswrapper-1.38.tar.gz

```

4. Blacklist the bcm43xx firmware drivers that come default.
```

sudo gedit /etc/modprobe.d/blacklist

```
Add the following line to the end of the file and save your changes:

blacklist bcm43xx

***REBOOT NOW***

After a reboot open a terminal and go to the same folder you created earlier.

5. Get into the ndiswrapper folder it created when you unzipped it.  The [TAB] represents using your TAB key to finish the name of the folder.
```

cd ndis[TAB]

```

6. Begin the install process.  Do the following multiple times, until you see some error about no files or directories or something.
```

sudo make uninstall

```

7. Main install process
```

sudo make
sudo make install

```

8. Installing drivers, first in your terminal go to the folder that unzipped earlier with the driver files in it.
```

cd bcm[TAB]
sudo ndiswrapper -i bcmwl5.inf
sudo ndiswrapper -l

```

NOTE: If you don't see a message that says driver present, hardware detected, you may have problems.

```

sudo ndiswrapper -m
sudo modprobe ndiswrapper

```

9. Test your wireless.  You may need to reboot, however a reboot won't suffice, you'll need to shutdown and then restart.  Your WIFI light should illuminate when successful.
```

sudo iwlist scanning

```

10. Before trying to connect to a network I recommend installing Wifi-Radar to make your life simpler.  It manages your wireless networks.  To install and use it open Synaptic Package Manager and search for "wifi-radar".  Install it and then run it from the Applications-->Internet menu.

**Now time to install ATI drivers!**

1. Disable Composite Extension - In Ubuntu Edgy the Composite extension is enabled by default, however, fglrx does not yet support Composite with DRI. In order to disable Composite you have to edit the xorg.conf file:
```

sudo gedit /etc/X11/xorg.conf

```
and add these lines at the end of the file:

Section "Extensions"
        Option  "Composite" "Disable"
EndSection

Section "ServerFlags"
        Option  "AIGLX" "off"
EndSection

2. Update System & Install the 8.28.8 ATI Driver in the Ubuntu Repos.  For instructions on installing the proprietary drivers, click here: [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)
```

sudo apt-get update
sudo apt-get install linux-restricted-modules-$(uname -r) #Okay if it is already installed
sudo apt-get install xorg-driver-fglrx

```

3. Now Edit Your xorg.conf File to Reflect the Appropriate Resolutions and Replace "vesa" under the Device section with "fglrx"
```

sudo gedit /etc/X11/xorg.conf

```
To edit your resolutions, add the resolutions your monitor goes up to to each of the resolutions lines in the file.  They are set at a default of "1024x728" as the max, just add the top res in the same format.  Alternatively you can run:
```

sudo aticonfig --initial

```

4. Run the ATI config script
```

sudo aticonfig --overlay-type=Xv

```

5. Reboot and you should see your new res.  Login and type "fglrxinfo" at the terminal to see if the ATI driver is loaded.  Check for direct rendering by typing:
```

glxinfo | grep direct

```

You should now be able to install Beryl without problems.

**BERYL:**

1. Add Beryl repositories.
```

sudo gedit /etc/apt/sources.list

```
Add the following to the end:
deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main

2. Add the key
```

wget -q http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg -O- | sudo apt-key add -

```

3. Now update
```

sudo apt-get update

```

4. Install XGL Server
```

sudo apt-get install xserver-xgl

```

5. Install Beryl and Themes
```

sudo apt-get install beryl emerald-themes

```

Next you'll configure it.  I configure mine to have a seperate session so that's what I'll cover here.

6. Now create a startup script
```

sudo gedit /usr/local/bin/startxgl.sh

```

I added the following into the empty file just created:
```

#!/bin/sh
Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
exec dbus-launch --exit-with-session gnome-session

```

7. Make the script executable
```

sudo chmod a+x /usr/local/bin/startxgl.sh

```

8. Create a Login Entry
```

sudo mkdir -p /etc/X11/sessions
sudo gedit /etc/X11/sessions/xgl.desktop

```
Now add the following and save it:

[Desktop Entry]
Encoding=UTF-8
Name=Xgl
Exec=/usr/local/bin/startxgl.sh
Icon=
Type=Application

9. If it tests okay, add a script to load it automatically every time the Xgl session is loaded.  Create the script and paste the following into it as so:
```

sudo gedit /usr/local/bin/start_beryl.sh

```

Now add the following and save the changes:
```

#!/bin/bash
#
# Start beryl-manager within gnome-session
#
if (( `ps -A -o comm | grep -c '^Xgl$'` == "1" )); then
       DISPLAY=:1 beryl-manager
       DISPLAY=:1 beryl-xgl
else echo "${0}: Error: beryl-manager not launched. Xgl not running?"
fi

```

10. Now make the script executable:
```

sudo chmod a+x /usr/local/bin/start_beryl.sh

```

11. Next add the following to the "Startup Programs" inside Programs>Preferences>Sessions

/usr/local/bin/start_beryl.sh

12. Done!  You can reboot and enjoy!  Troubleshooting: [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL)

**UPDATE:** Thanks to nachotronics, the following will fix your screen brightness buttons!

1. Using a terminal, open the blacklist file again:
```

sudo gedit /etc/modprobe.d/blacklist

```
Add the following to the end:

blacklist video

2. Reboot and it should work!  Thanks Nacho!

[B]
Here's a little extra fun stuff you can add:[/B]

Fan and temp control
1. sudo apt-get install i8kutils gkrellm gkrellm-i8k
2. sudo modprobe i8k force=1
3. sudo gedit /etc/modules
4. add the following line to the end of the file: i8k force=1
5. go to System > Preferences > Sessions > Startup Programs
6. Click ADD and put the command: gkrellm
Now you will see the GKrellm utility load at startup and you can then configure your fan thresholds, etc.

Configure front panel buttons, etc.
1. System > Preferences > Keyboard Shortcuts
2. Choose custom actions for your special keys, click an action and press the key!

Automatix **For Edgy and Dapper**
1. Visit [www.GetAutomatix.com]("http://www.GetAutomatix.com") and follow instructions for your distro.


Optional things I did:

Citrix (I use this so it's optional) 
**For Edgy and Dapper**
1. Download 9.0 client for linux here: [http://www.jrdw.com/linux/citrix/linuxx86.tar.gz]("http://www.jrdw.com/linux/citrix/linuxx86.tar.gz")
2. Download and install libmotif3 here: [http://www.jrdw.com/linux/citrix/libmotif3_2.2.3-1.2ubuntu2_i386.deb]("http://www.jrdw.com/linux/citrix/libmotif3_2.2.3-1.2ubuntu2_i386.deb")
3. Extract citrix to folder and go to folder with terminal
4. sudo ./setupwfc
5. Install default with Y for all answers.  Be careful during the License acceptance as it defaults to reject so if you hold the ENTER key it will exit the install!
6. 3 to quit install

VMWare 
**For Edgy and Dapper**
1. Download vmware server tar.gz file from: [http://download3.vmware.com/software/vmserver/VMware-server-1.0.1-29996.tar.gz]("http://download3.vmware.com/software/vmserver/VMware-server-1.0.1-29996.tar.gz")
2. place downloaded file somewhere in a folder in your home folder and using terminal CD into that folder
3. tar xvzf VMware-server-1.0.1-29996.tar.gz
4. cd into the folder it creates
5. sudo ./vmware-install.pl
2. Obtain a free serial at [www.vmware.com](www.vmware.com)

IEs4Linux  
**For Edgy and Dapper**
1. First get Wine using Automatix.
2. Open a terminal
3. If you haven't, uncomment the Universe lines in sources.list
4. sudo apt-get install cabextract
5. CD into the directory you want to download the ie4linux package to
6. wget [http://www.tatanka.com.br/ies4linux/downloads/ies4linux-latest.tar.gz](http://www.tatanka.com.br/ies4linux/downloads/ies4linux-latest.tar.gz)
7. tar zxvf ies4linux-latest.tar.gz
8. cd ies4linux-*
9. ./ies4linux
10. You'll be prompted which IE you want and other options, most options just leave default.


Done and have fun!

note: I don't guarantee this will work for you so don't yell at me!:)

---

### Post by jdmturbomr2 on 2006-09-15
What did you do about partioning during the install?  On my e1505 Dell made a 20GB partition (D:) for use with Norton Ghost I think.  Did you just erase that partition and also did you dual boot w/ windows?  Just out of curiosity, how big of a partition did you give Ubuntu?

Sorry for all the questions I am only 15 and never used linux before so I'm scared to install and mess up my windows installation.  I just wanna make sure I get it right the first time.

---

### Post by lifeempowered.com on 2006-09-18
I blew it away.  Then partitioned my 120GB HD as follows:

Primary 10 Gig for / (root)
Remaining Extended Partition
Logical 1.35 Gig for swap
Logical 100 Gig for /home

(notice the 120 is actually about 110)

After you get a good, working root install, image that partition (should be about 3.4 gigs) using partimage.  What I did is download and burn the ISO they give you and booted to it.  Once booted into the Partimage Recovery CD I mounted my external drive, /dev/sdb1 to /mnt/temp4.  Then typed partimage at the command prompt.  This starts the image software and I chose to save the Image as /mnt/temp4/rootbk.  Then after choosing other options, such as whether to compress or not, etc., I ran the image.  It only took about 2 minutes to image my root partition!  Now if it goes sour I can just recover that partition and all my settings, files, etc. are in /home which is a seperate partition!

Hope this helps!

---

### Post by NTolerance on 2006-09-18
Have you had any trouble with the sound on your 6400?  Dapper doesn't like to play any sound every other reboot on my E1505.  There are also issues with fglrx breaking suspend/hibernate.  Have you had either of those issues?

---

### Post by lifeempowered.com on 2006-09-19
Did you do any updates as of today?  If so this may be why.  I'm not sure what the new kernel update is going to do as in effecting this how to and anything else with the setup.

I've had no problems with my systems audio, etc.

---

### Post by NTolerance on 2006-09-19
I haven't done any updates recently because I gave up on Ubuntu after intermittantly having no sound.  I'll re-install and give your guide a try.  Hopefully there's some magic in there that prevents sound issues.

Is your soundcard the Sigmatel Intel HDA thingy?

---

### Post by happy-and-lost on 2006-09-19
> **jdmturbomr2 said:**
> What did you do about partioning during the install?  On my e1505 Dell made a 20GB partition (D:) for use with Norton Ghost I think.  Did you just erase that partition and also did you dual boot w/ windows?  Just out of curiosity, how big of a partition did you give Ubuntu?

Sorry for all the questions I am only 15 and never used linux before so I'm scared to install and mess up my windows installation.  I just wanna make sure I get it right the first time.

IMHO, the Dell Recovery partition ain't worth having. On my I6000, it was a nightmare to access (Ctrl-F11 at a very specific time at boot), and the Windows installation image contained even included some spyware :eek: (Doubleclick trackers!).

As a Dell it should come with a util to burn a CD of whichever Windows is installed (It's usually in the "Dell" submenu on the start menu). That CD will be a cleaner install than the recovery partition, the only things you may need are drivers, which are easily obtained from M$ Upgrade or Dell's website anyway.

What you will need is a "Documents" partition, of sorts. I'm assuming your Windows is on NTFS? Well, defrag your C drive, back up everything vital and repartition as follows. (I'm assuming your HD is about 100GBish, adjust accordingly)[I use Norton Partition magic, but Ubuntu 6.06 CD has a partitioner]:

-30GB(ish) Windows XP system partition NTFS (will hold Windows and all installed programs.
-40GBish Documents partition in FAT32 (VERY IMPORTANT! Linux CANNOT write to NTFS!)
-25GB(ish) Linux partition in Ext3 (For Ubuntu :D)
-2GB (max) Linux swapspace (like virtual memory in Windows)

Now this is done, transfer everything in your "My Documents" folder to the FAT32 docs partition, and use TweakUI to repoint Windows to that drive (probably E) as its "My Documents" folder.

Phew, now boot into the Ubuntu LiveCD and install. The Root (/) drive should be in the Ext3 partition (Probably labelled hda3 [or sda3 if you have a SATA HDD like meeee]). It will tell you the formats of all the drives, so make sure you're using all the right drives for the right things.

Install.

Enjoy!

Your FAT32 documents will appear on your desktop as "hda5" (or thereabouts, there will only be one other than hda1). Both Linux and Windows can read/write to this partition :D.

You may need to change the permissions on this drive. Go into the GNOME terminal and type "sudo nautilus". Now go to hda5(or whatever), right click on an empty space, go to the Permissions tab on "Properties" and make sure owner and group have read/write checked.

Phew.
PM me if you have any problems or doubts!
:KS

---

### Post by got_nix on 2006-09-20
thanks alot man.. honestly i gotta say your how to helped me alot.. you rule i love my inspiron 6400 and i'm running a ubuntu only setup not like i didn't get xp with it but i'm tired of dual booting so its ubunto only from now on.

one question. why is it that my x1300 ati card only pics up as 64mb card tho.. i remember seeing about 128 or was it 256 the day i bought this system (when i looked at it in windows)

---

### Post by Daniel15 on 2006-09-22
You forgot one important thing: i8kutils, GKrellm and gkrellm-i8k. Without them, the system won't be able to control the fan speed, and there's a possibility of overheating. Install them via Synaptic, or apt-get (```
apt-get install i8kutils gkrellm gkrellm-i8k
```). Then, install the i8kutils module:
```
modprobe i8k force=1
```
Run GKrellm with the i8k panel, and see if the fans are working.
You'll need to add a line to the /etc/modules file:
```

i8k force=1

```

> why is it that my x1300 ati card only pics up as 64mb card tho
That's HyperMemory. Basically, the card has half of its memory as internal memory, and will borrow some memory from the system if required.
For example, my X1400 is a 256MB Hypermemory. It has 128MB onboard, and will borrow up to 128MB if it needs it.

Also, about Compiz, I made a post about it on my blog: [http://www.daniel15.com/blog/2006/09/18/laptop-linux-and-compiz/](http://www.daniel15.com/blog/2006/09/18/laptop-linux-and-compiz/) . Basically, once you install the ATI drivers (8.28.8 ), follow the tutorial at [http://www.compiz.net/topic-389-1.html](http://www.compiz.net/topic-389-1.html) (use the second howto)

EDIT: I noticed you mentioned Compiz:
> Follow this guide, the "normal" method (1st method)
I would suggest to use the **second howto**. This is so:
[LIST]
[*] If Compiz stops working, you have an alternate configuration
[*] You can still play OpenGL-accelerated games, by following the instructions at [http://www.compiz.net/topic-1623-howto-opengl-acceleration-with-session-still](http://www.compiz.net/topic-1623-howto-opengl-acceleration-with-session-still)
[/LIST]

---

### Post by infrin on 2006-09-22
I am running SuSe10.1 and my sound doesn't come on. I haven't really messed around with it since I am moving from Windows (I don't know too much about configuring devices so far). Is there an audio driver for the 6400 that I might need to download? Should I just move over to Ubuntu?

--Mike

---

### Post by trifgabi on 2006-09-22
Great 

Any ideas how to get the cardreader to work?

---

### Post by ysr on 2006-09-22
> **lifeempowered.com said:**
> 
6. sudo ./ati-driver-installer-8.28.8.run
7. install driver using the default settings and exit when finished.


Hi lifeempowered, why are the two quoted steps required? Will these need to be done everytime I download a new version of the drivers? Any clarification on what exactly is done by these two steps will be much appreciated (since you seem to be generating custom packages for ubuntu anyway in step 8 ).

---

### Post by ysr on 2006-09-22
> **NTolerance said:**
> I haven't done any updates recently because I gave up on Ubuntu after intermittantly having no sound.  I'll re-install and give your guide a try.  Hopefully there's some magic in there that prevents sound issues.

Is your soundcard the Sigmatel Intel HDA thingy?

I have been experiencing the same problem lately. I don't recall having this problem in the past though (have been running Ubuntu on this laptop for a couple of months now). I sort of (vaguely) remember noticing this for the first time after installing network-manager-gnome, but then I might be wrong. Haven't investigated much into this, but will investigate at some point. In the meantime, please do keep us posted if you have any luck.

---

### Post by zykos on 2006-09-24
I'm trying to decide which version of Ubuntu (32-bit or 64-bit) I should install on my Inspiron 6400 (centrino core 2 duo 2GHz). I know the 64-bit version is supposed to have a performance increase, but less programs support the 64-bit architecture. Any advice?

---

### Post by got_nix on 2006-09-24
yeh.. i'ld like to know how i find out if i have a 64 bit processor int he first place i have a 6400 intel dou core (not core2)

---

### Post by nischg on 2006-09-24
> **got_nix said:**
> yeh.. i'ld like to know how i find out if i have a 64 bit processor int he first place i have a 6400 intel dou core (not core2)

if you don't have a Merom (Core 2 Duo) your processor is 32 bits (Yonah).

---

### Post by ysr on 2006-09-24
> **got_nix said:**
> yeh.. i'ld like to know how i find out if i have a 64 bit processor int he first place i have a 6400 intel dou core (not core2)

The Yonah class core duo processors (which read like T2500) are all 32 bit. The merom class **core2** duo (which read like T7400) support 64 bit. For more details check out intel's laptop processor page here [http://www.intel.com/products/laptop/processors/index.htm]("http://www.intel.com/products/laptop/processors/index.htm")
Look out for the EMT64 architecture. Apparently Intel prices both the merom and yonah processors (of a given clock speed) identically. Given that the merom architecture is both deeper and wider, makes you wonder why OEM's still ship with Yonah processors. The only fly in the ointment for Merom is that at the moment, the laptop platform only supports a max FSB speed of 667 MHz, so the improvements in laptops are only marginal compared to desktop cpus.

---

### Post by james957 on 2006-09-25
I am having trouble with this procedure.
So I have gotten to step 7 successfully, but when I attempt step 8, I get the following:

> sudo make install
sudo: make: command not found

> make
bash: make: command not found

> sudo make uninstall
sudo: make: command not found

I then downloaded the drivers and skipped to step 13:

> tar xvzf bcmdrivers.tar.gz
bcmdrivers/bcmwl5.sys
tar: bcmdrivers/bcmwl5.sys: Cannot open: No such file or directory
bcmdrivers/bcmwl5.inf
tar: bcmdrivers/bcmwl5.inf: Cannot open: No such file or directory
tar: Error exit delayed from previous errors

Any ideas?  I'd greatly appreciate it.

Thanks,
James

---

### Post by Daniel15 on 2006-09-25
> So I have gotten to step 7 successfully, but when I attempt step 8, I get the following:

> sudo make install
sudo: make: command not found
That means that some packages for compiling things from source aren't installed. Running ```
sudo apt-get install build-essential
``` should solve that ;)

> Any ideas how to get the cardreader to work?
I'd also like to know this. Any ideas?

---

### Post by james957 on 2006-09-26
Daniel and lifeempowered,

I'm still having trouble with ndiswrapper.

So I installed the build-essential package successfully, I believe.
When I try step 8 now, I get the following errors:

> sudo make uninstall
make: *** No rule to make target `uninstall'.  Stop.
> make
make: *** No targets specified and no makefile found.  Stop.
> sudo make install
make: *** No rule to make target `install'.  Stop.


and after cd'ing into the directory with the unzipped bcmdrivers and ndiswrapper folders:

> sudo ndiswrapper -i bcmwl5.inf
-bash: ndiswrapper: command not found

Do you know what I'm doing wrong?

Thanks,

James

---

### Post by unshareef on 2006-09-26
guys, new to ubuntu here. got inspiron 6400 with dual core as well as ati x1300. only 1 core seems to be detected. I have been following the steps provided by lifeempowered to install wireless. However step 7 doesnt make sense to me. Do I just write my own sentence at the bottom of the file and save it. Step 8 doesnt work when i type "sudo make install". Is there a special way to type it? I am a n00b, i hope you can help!

---

### Post by lifeempowered.com on 2006-09-26
> **Daniel15 said:**
> You forgot one important thing: i8kutils, GKrellm and gkrellm-i8k. Without them, the system won't be able to control the fan speed, and there's a possibility of overheating. Install them via Synaptic, or apt-get (```
apt-get install i8kutils gkrellm gkrellm-i8k
```). Then, install the i8kutils module:
```
modprobe i8k force=1
```
Run GKrellm with the i8k panel, and see if the fans are working.
You'll need to add a line to the /etc/modules file:
```

i8k force=1

```


That's HyperMemory. Basically, the card has half of its memory as internal memory, and will borrow some memory from the system if required.
For example, my X1400 is a 256MB Hypermemory. It has 128MB onboard, and will borrow up to 128MB if it needs it.

Also, about Compiz, I made a post about it on my blog: [http://www.daniel15.com/blog/2006/09/18/laptop-linux-and-compiz/](http://www.daniel15.com/blog/2006/09/18/laptop-linux-and-compiz/) . Basically, once you install the ATI drivers (8.28.8 ), follow the tutorial at [http://www.compiz.net/topic-389-1.html](http://www.compiz.net/topic-389-1.html) (use the second howto)

EDIT: I noticed you mentioned Compiz:

I would suggest to use the **second howto**. This is so:
[LIST]
[*] If Compiz stops working, you have an alternate configuration
[*] You can still play OpenGL-accelerated games, by following the instructions at [http://www.compiz.net/topic-1623-howto-opengl-acceleration-with-session-still](http://www.compiz.net/topic-1623-howto-opengl-acceleration-with-session-still)
[/LIST]

Thanks so much for your addition, this is excellent!  I'm wondering, are both fans ever supposed to be running?  And any input on the fan speed control, namely, does this enable only monitoring of it or the actual auto control?  I just thought the fan speed was controlled through hardware.  Thanks!  And I'll add this to the how-to.  Where would you suggest adding it?

---

### Post by lifeempowered.com on 2006-09-26
> **unshareef said:**
> guys, new to ubuntu here. got inspiron 6400 with dual core as well as ati x1300. only 1 core seems to be detected. I have been following the steps provided by lifeempowered to install wireless. However step 7 doesnt make sense to me. Do I just write my own sentence at the bottom of the file and save it. Step 8 doesnt work when i type "sudo make install". Is there a special way to type it? I am a n00b, i hope you can help!

Make sure you are following all steps in order, if you don't have the appropriate packages installed you won't be able to build/install.

---

### Post by Daniel15 on 2006-09-26
> only 1 core seems to be detected.
That's what the first bit is for. ```
sudo apt-get install linux-686-smp
``` is the line which will install the proper kernel. The default 386 kernel only supports one core.

>  I'm wondering, are both fans ever supposed to be running?
Usually, the fans can remain off unless the temperature reaches about 40-45 degrees celcius. Even so, they don't need to remain on for long. Is this what you mean?

And I still don't know what the left fan in GKrellm is, I think it's some internal fan. The right one is the one at the back left of the laptop.

> And any input on the fan speed control, namely, does this enable only monitoring of it or the actual auto control?
The fans are both monitored and controlled by GKrellm. If you change the 'Automatic' to 'Manual', and click on the right fan, you'll be able to change the speed of it (if you put it on the highest setting, you'll be able to hear it -- it's quite noisy on the highest setting).

> I just thought the fan speed was controlled through hardware.
Well, it should be, but that usually doesn't work well. Even so, the BIOS has the temperature threshold set at some rediculous temperature (somewhere around 80-90 degrees celsius!). I believe that one of the programs that comes preinstalled on the PC controls the fan in Windows (I think it's the QuickSet thing).

> And I'll add this to the how-to. Where would you suggest adding it?
Well, I'd suggest to move video above the section on Wireless (as video is usually more important than wireless), and then add the GKrellm section underneath the video section.

EDIT: Missed something:
> However step 7 doesnt make sense to me. Do I just write my own sentence at the bottom of the file and save it. 
Yes, just add it to the end of the file.

EDIT2: I suggest you add something like this to the wireless section, it's probably needed:
**NOTE:** If your laptop has the Intel Pro Wireless 3945 in it, then these steps aren't neccesary (as the card is supported out of the box). ONLY follow these steps if you have the Dell 1390 or Broadcom 4311!

The IPW3945 is indeed supported out of the box, I tried it myself (well, I was having problems with WPA encryption, but the Gnome NetworkManager solved that. ```
apt-get install gnome-network-manager
```, I think [I can't remember])

---

### Post by ysr on 2006-09-26
> **Daniel15 said:**
> And I still don't know what the left fan in GKrellm is, I think it's some internal fan. The right one is the one at the back left of the laptop. The Inspiron 6400 has one fan only (which the i8k kernel module recognizes as Fan2, presumably shows up as the "right fan" by the gkrellm-i8k). The detailed internal hardware configuration of the Inspiron 6400 can be found in the dell service manual [http://support.euro.dell.com/support/edocs/systems/ins6400/en/sm/index.htm]("http://support.euro.dell.com/support/edocs/systems/ins6400/en/sm/index.htm")

> **Daniel15 said:**
> 
(well, I was having problems with WPA encryption, but the Gnome NetworkManager solved that. ```
apt-get install gnome-network-manager
```, I think [I can't remember]) Its actually
```
 sudo apt-get install network-manager-gnome 
```
Note though that network-manager won't work with an Access Point that does not broadcast its SSID. (Some people hide their SSID as a security measure, whose security value is debatable, but works against "casual intruders"). If you want WPA with hidden SSID, you will need to manually configure WPA supplicant with a conf file.

---

### Post by ysr on 2006-09-26
One final note. If the loud system beep is annoying you (for example when you press the TAB key to get argument completion in bash), you can turn it off easily enough. This beep is independent of your sound card (which you have probably discovered if you have tried to mute it using the gnome volume applet), and is produced by a system speaker (which doesn't seem to do anything else apart from beeping annoyingly).

To disable the beeps for the current session only ```
 sudo rmmod pcspkr 
``` To disable permanently ```
 sudo vim /etc/modprobe.d/blacklist 
``` Add the line "blacklist pcspkr" and save the file to prevent loading the module at boot time.

---

### Post by Daniel15 on 2006-09-26
> **ysr said:**
> To disable the beeps for the current session only ```
 sudo rmmod pcspkr 
``` To disable permanently ```
 sudo vim /etc/modprobe.d/blacklist 
``` Add the line "blacklist pcspkr" and save the file to prevent loading the module at boot time.

You can also do it via System --> Preferences --> Sound, on the 'Sound Preferences' tab. This is probably easier ;)

> ...system speaker (which doesn't seem to do anything else apart from beeping annoyingly)...
You've never played a DOS game before sound cards became popular? They changed the pitch of the 'annoying beep' to make sounds :D

---

### Post by unshareef on 2006-09-27
ok, i am a complete freshie here. I am following the steps to install the new kernel but step 2 asks me to "uncomment". I have opened the necessary file but what is meant by uncomment?

---

### Post by Daniel15 on 2006-09-27
> . I have opened the necessary file but what is meant by uncomment?
Find all the 'deb' lines that have a # character in front of them, and remove the #.
Basically, a line with a # is a comment, which isn't read by the system. Once you remove the #, the line will be read in by the system ;)

---

### Post by james957 on 2006-09-28
Once I've installed GKrellm, do I have to take any further steps to turn on the fan control (i.e. run gkrellm from a terminal each time I start up)?

Or does the fan control launch automatically on startup?


Thanks,

James

---

### Post by lifeempowered.com on 2006-09-28
> **james957 said:**
> Once I've installed GKrellm, do I have to take any further steps to turn on the fan control (i.e. run gkrellm from a terminal each time I start up)?

Or does the fan control launch automatically on startup?


Thanks,

James

Follow the complete steps, which will be in the how to shortly, and you will see it starts automatically.

---

### Post by neuropsychguy on 2006-09-28
I posted this in a different thread but I just wanted to put it here since I had a problem with screen resolution in my E1505 (6400).

The best way to get the proper resolutions showing up if sudo aticonfig --initial doesn't work properly is to run the command ```
sudo aticonfig --force --initial
```

Works like a charm for me. Of course, this is assuming that the only thing that doesn't work is having the proper resolutions show up.

---

### Post by lifeempowered.com on 2006-09-28
Thanks again Daniel!  I redid the How-To and if you'd like to edit/make changes to help me perfect it PM me and we can colaberate.

---

### Post by listerthrawn on 2006-09-28
Firstly, thanks for a good howto on the 6400.  

I just got one of these and this helped me loads.  Don't quite understand all the dpkg stuff on the ATI driver tho.  Wouldn't mind you explaining it!

Also, on the subject of temp monitoring personally I like daemons to be looking after this stuff.  My girlfriend also uses the laptop and has her own logon, she won't have any graphical things running like that and would probably shut it down.  Burnt laptop lol.  I've set up the i8kutils to run as a daemon as in this guide.

[http://www.ubuntuforums.org/showpost.php?p=1325507&postcount=128](http://www.ubuntuforums.org/showpost.php?p=1325507&postcount=128)

It's all personal taste but it gives you a choice!

Thanks

Chris

---

### Post by lifeempowered.com on 2006-09-28
Thanks for the addition Chris, truly personal preference, I'm trying to be "safe" by running it in UI so I can consistantly be aware and check on temp.

---

### Post by listerthrawn on 2006-09-28
I'm being safe that way too.  Theres a sensors applet that you can install.  See my screenshot!!

---

### Post by Daniel15 on 2006-09-29
> Thanks again Daniel!
No problem... Thank you for writing this tutorial :D 

And just one interesting thing: For some strange reason, the memory card reader seems to only work if you boot up with a memory card in it! (Well, works for me with a SD card). If you put a memory card in it while it's on, it will recognise the card (you'll get some output to /var/log/messages), but won't mount it or anything. Does anyone know how to get it working properly?

---

### Post by mattyj on 2006-09-29
Does the ATI 1300/1400 in your laptop actually use hardware accelleration, i.e. are the ATI drivers better than they used to be?

I am thinking of going with the E1505 for a laptop, but have had bad experiences with ATI cards in linux.

Thank You.

---

### Post by Daniel15 on 2006-09-29
> Does the ATI 1300/1400 in your laptop actually use hardware accelleration, i.e. are the ATI drivers better than they used to be?
Yeah, it seems to work fine... Most games I've tried run at full speed at 1280x800 (native resolution of the screen).
Indeed, the ATI drivers have improved with recent revisions. From past experience, the older drivers (around 8.24.whatever) didn't work that well, but the recent 8.29.6 drivers seem to have improved significantly. I was having problems with a few things not working correctly using the 8.28.8, but everything works fine using 8.29.6 drivers :D

---

### Post by unshareef on 2006-09-29
Really? You can play games on ubuntu? like doom3 or F.E.A.R? how?

---

### Post by Daniel15 on 2006-09-29
> Really? You can play games on ubuntu? like doom3 or F.E.A.R? how?
Not sure about those games, but you can play games, yes. Note that games *I* play are quite often emulated Sega Mega Drive, Nintendo 64 games or DOS Games, but occasionally Unreal Tournament as well :). Oh yeah, I can't forget Linux games like Planet Penguin Racer, Super Tux or Nexuiz :D

Actually, I'm sure that DOOM 3 has a Linux port, so yes, you can play it in Linux. See [http://zerowing.idsoftware.com/linux/doom/](http://zerowing.idsoftware.com/linux/doom/) for details (you'll need your game CD's to install it). F.E.A.R. I'm not so sure of, so you'll need to have a look (sites like [http://www.linuxgames.com/](http://www.linuxgames.com/), [http://www.happypenguin.org/](http://www.happypenguin.org/) and [http://www.icculus.org/lgfaq/gamelist.php](http://www.icculus.org/lgfaq/gamelist.php) might be helpful)

---

### Post by unshareef on 2006-09-29
Wow, i've installed the kernerl and the ATI card now. Thanks you! But I'm having trouble installing the fan. After entering the first step an error says:

E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
unshareef@unshareef-laptop:~$ apt-get install i8kutils gkrellm gkrellm-i8k
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

Any ideas?

Also, is it possible to adjust the settings of my ATI card, for example the anti aliasing. Is there a program like catalyst for windows?

Thanks again.:-D

---

### Post by unshareef on 2006-09-29
Sorry, one more question. What is compiz?

---

### Post by lifeempowered.com on 2006-09-29
> E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
unshareef@unshareef-laptop:~$ apt-get install i8kutils gkrellm gkrellm-i8k
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

Sorry, I forgot the "sudo" part, it's in the how to now on the first page.  All apt-get commands have to be followed by sudo as well as modprobe.

Notice how it asks above "are you root?" that's what it means.

Anyway, the guide is updated and I also added instructions for getting IE 6 with flash 9 and iTunes 6.0.5 working using Wine.

Cheers!

---

### Post by lifeempowered.com on 2006-09-29
> **unshareef said:**
> Sorry, one more question. What is compiz?

learn all about it here: [http://forum.beryl-project.org/](http://forum.beryl-project.org/).  It's basically "eyecandy" for linux. :)  VERY cool eye candy might I add.

---

### Post by Rhawi Dantas on 2006-09-29
I'm having a problem with a Inspiron 9400, dunno if its the same...

The thing is that I have a Broadcom BCM4401-B0 and everytime I try to connect to the internet I get a:

PAP Authentication Failed.

Already tried to disable ipv6 and disable the network card on gnome so I could enable it after pppoeconf but nothing happened...

Ran out of ideas and searched A LOT on this forum...

Can anyone show me a way ?

Thanks a lot...

---

### Post by Daniel15 on 2006-09-29
> Also, is it possible to adjust the settings of my ATI card, for example the anti aliasing. Is there a program like catalyst for windows?
Nope, unfortunately not. ATI haven't finished developing their Linux control panel, and it's quite lacking at the moment (If you want to get to it, Accessories --> ATI Control)
However, I believe that FSAA (Full-screen Anti-aliasing) can be controlled via the 'aticonfig' program. Try looking at the output of
```
aticonfig --help | less
``` (I'm not around my laptop at the moment, so I can't check if the option exists or not)

> What is compiz?
Yep, basically eye-candy for Linux. Some of the effects include some nice themes (with Vista-style glass effects), wobbly windows (windows 'wobble' when you drag them), semitransparent windows, a desktop cube and a whole heap more. Search for 'Compiz' on Youtube.com or Google Video to see some video's of it. I made a post on it on my blog, at [http://www.daniel15.com/blog/2006/09/18/laptop-linux-and-compiz/](http://www.daniel15.com/blog/2006/09/18/laptop-linux-and-compiz/)

---

### Post by mgolden on 2006-09-30
Am I missing something or isn't there a problem with the idea of controling the fan through gkrellm.  gkrellm only starts up when you log in.  This in principle means that if you start up the machine and then don't log in, there's no temperature control.  Or, if you accidentally close it, you can fry your machine.

I have created a set of scripts for /etc/init.d and /etc/rc*.d that turn on the i8kmon as a daemon and run it quietly in the background.  I can make a deb for it if people want.  Seems like this is a much better thing to do than relying on a user-space app to control the fan.

---

### Post by agentstewie on 2006-09-30
when ever i try to install compiz, i get the error:



```
The following packages have unmet dependencies:
  compiz: Depends: compiz-plugins (>= 0.2) but it is not going to be installed
E: Broken packages

```

---

### Post by mattyj on 2006-09-30
Can you also just follow these instructions to get the ATI card working, or is there something special?

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

Thank You.

---

### Post by Daniel15 on 2006-10-01
> when ever i try to install compiz, i get the error
Yeah, Compiz is in a sort of 'transition state' in the moment, as compiz-quinnstorm has changed name to 'Beryl'. See [http://forum.beryl-project.org/](http://forum.beryl-project.org/) to see if a newer tutorial is available.

> Can you also just follow these instructions to get the ATI card working, or is there something special?

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

Thank You.
Sure, you can follow those instructions... There's nothing special to do. Basically any instructions on getting ATI drivers working are fine (I actually followed the instructions at [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide), to install the 8.29.6 drivers). I suggest you don't use any ATI drivers older than 8.28.8, as the 8.28.8 drivers function a lot better on the X1300/X1400 than the older ones.

---

### Post by Jendall on 2006-10-03
Hi,

I tried to run wifi card dell wireless 1390, but when I compile and install new ndiswrapper, windows driver(I used instructions from this thread) and when type > sudo modprobe ndiswrapper
whole system gets completely freeze :( ... 

intel cards are ok ...but does anybody know, how to run this wifi card pls?

---

### Post by lifeempowered.com on 2006-10-03
Well everyone, I'm off to try Edgy Eft.  So far it's looking good (I've already installed it) and wireless may work out of the box for my card :)

---

### Post by BattleGnome on 2006-10-03
Hi there just having a minor issue installing the ATI drivers, I am installing 8.29.6 as thats the current driver and this is what I get when I try to run aticonfig. I have followed every step down to the line (using 8.29.6 as the version ofcourse)

> ash@ash-laptop:~$ sudo aticonfig -initial
Warning: Could not find configuration file
Please copy configuration file template to /etc/X11


How do I fix this? Thanks.

---

### Post by mattyj on 2006-10-03
Has anybody tried a Core2Duo E1505/6400?

About to pull the trigger on one.  $1485 for 2ghz, 2GB, 160HD, ATI card, 9cell battery, nice screen, intel wireless.  Pretty good deal.

Google dell evalue and you get $300 off to get that price...

mj

---

### Post by lifeempowered.com on 2006-10-04
> **BattleGnome said:**
> Hi there just having a minor issue installing the ATI drivers, I am installing 8.29.6 as thats the current driver and this is what I get when I try to run aticonfig. I have followed every step down to the line (using 8.29.6 as the version ofcourse)



How do I fix this? Thanks.

Have you done all the pre-steps in the How to?  You need to follow every step prior to ATI, because there are certain apps you get in the first initial stages.  I'll try to seperate everything into it's own mini-howto later, but for now, it's meant to be followed from start to finish as is.

---

### Post by got_nix on 2006-10-04
I realized soemthing.. i did a check yesterdday

cat /proc/cpuinfo

i cant remember my exact output and id ont have my notebook with me at work today. however one thing i did notice was cpu_cores was showing 1

i have a core duo.. whats the deal right there. what do you have lifeempowered.com?

---

### Post by aselder on 2006-10-04
Thanks for the great instructions.

I'm having a couple of problems.

First: The packages for the fan control seem to have disappeared. Neither the package manager or apt-get see them.

Second: I'm trying to install the drivers for the Dell 1390 wireless card, and I'm getting the following messages.

    1. When running "make uninstall", I'm getting can't remove directories errors.

    2. When running "make" for ndiswrapper, I'm getting can't find kernal build files.

Help would be greatly appreciated.

---

### Post by Jendall on 2006-10-04
hi aselder,
in first case, you must be root ...so type it with "sudo" ...when it will not work, try to delete it manually by "sudo rm -rf /path/"(be careful)

2. you should install "kernel headers" package, for your kernel(same cpu architecture)

however, I'm still trying to run this card, but with no success :( ...if you will be able to make it work, let me(us) know :)

---

### Post by siersmak on 2006-10-09
> First: The packages for the fan control seem to have disappeared. Neither the package manager or apt-get see them.
I've also not been able to find the i8kutils package, even though I have the universe and multiverse repositories enabled.  Even worse, it appears that the ubuntu amd64 kernels don't include the i8k.o module, so even if I could find the i8kutils package, I wouldn't be able to get it to work.

This is too bad, my temp monitor tells me the CPU idles at about 40 C, and hits 60 C with fairly minor activity before the fan comes on, and this machine is to be used for a fair amount of number crunching.

-Ken

---

### Post by mattyj on 2006-10-10
Are there any plans to get those modules moved over the 64 bit.  I had placed an order planning to use 64 bit.

MJ

---

### Post by Evdawg on 2006-10-10
Hi, I used these instructions to prepare my 6400, as well as used big-desktop to configure a second monitor. It's pretty sweet, and works nearly perfectly, except every once and a while the laptop screen flickers with two thick bars vertically on the screen.

Should I be concerned about this?

---

### Post by BattleGnome on 2006-10-11
Just about to try doing this again with a fresh install but I am not sure what you mean by the second line ?


> 2. at end of file change: DISABLED_MODULES="fglrx" ( also included nv since it's an ati card)

Does this mean I have should 'Disabled_Modules="fglrx, nv" ?

Also on my install the default res is 1024*768 and I can't get it to 1280*800, do I need to wait till the ATI drivers are installed?

---

### Post by arthur_kalm on 2006-10-11
I just wanted to ask everybody using an Inspiron 6400. How many fans do you guys have? It seems to me that while gkrellm shows that I have 2 fans, in fact I only have one (the right one). When I change the speed on the left fan I don't hear anything turning on or happening, however, when the right one is on I can hear it (especially on the second setting). Thanks.

---

### Post by .t. on 2006-10-11
You don't need i8kutils. Your laptop will not die. It has built in sensors to control the fans. If you want manual control/different sensors, that is where i8kutils comes in handy.

---

### Post by arthur_kalm on 2006-10-11
Oh OK, well then it seems the sensors wait a rather long time to turn the fan on :P

But anyways, I just wanted to know how many fans you guys have?

---

### Post by .t. on 2006-10-11
I'm running a Dell Inspiron 6000 here, and without i8kutils, the fans are on toujours. I use i8kutils mainly to keep the noise down! So far no ill effects here.

I have just the one fan.

---

### Post by rogosh55 on 2006-10-11
Hi, I have been trying to figure this out for a couple days now.

I followed the instructions in the first post trying to get my wireless installed. I did so directly after a fresh install. It now pauses during boot up for about a minute at network connections. Also it says i have the wireless card installed under System>Administration>Networking however it doesnt work. Note the light goes on and off with alt-f2 but i cant get anything to work unless im hardwired. 

Help / suggestions anyone?

thanks

---

### Post by cnbiz850 on 2006-10-16
I just got a new 6400 with Core 2 Due T5600 and 1GB double-channel RAM.  When I boot the laptop from Ubuntu CD, it takes very long time after selecting menu of booting and before window manager appears.  In the middle, something happens, among which is displaying some messages in a black screen.
One of the message I jotted down is as follows:

buffer I/O error on device sr0, logical block 349878.

Anyone knows what it means?

---

### Post by Orion2000za on 2006-10-16
> **arthur_kalm said:**
> I just wanted to ask everybody using an Inspiron 6400. How many fans do you guys have? It seems to me that while gkrellm shows that I have 2 fans, in fact I only have one (the right one). When I change the speed on the left fan I don't hear anything turning on or happening, however, when the right one is on I can hear it (especially on the second setting). Thanks.

There is only 1 fan and it is picked up as the "right" one by i8kutils (see somewhere in this thread for a link to Dell's workshop manual). 

As for i8kutils not needed - I don't know. All I know is that I can keep the PC colder using it than it otherwise will be. I am running Kubuntu and don't want gkrellm so I more or less control it manually. 

When I tried running it as a daemon I got all sorts of problems so had to give up on that. 

Sinclair

---

### Post by Orion2000za on 2006-10-17
Has anyone tried recording anything or using a  mic for Wengo or Skype? I am failing miserably but can't figure out if it is the mic that is bad or that the device is not recognized or if I did not set Kmix proper.

Sinclair

---

### Post by unbox on 2006-10-19
hi, i cant seem to get sudo apt-get to work for anything other than update, not sure whats going on,

user@user-laptop:~$ sudo apt-get install linux-686-smp
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package linux-686-smp
user@user-laptop:~$

ive tried a few other apt-get functions and they dont seem to work either, help would be appreicated

thanks

---

### Post by n0dl on 2006-10-26
Hello my I bought a Dell inspiron 6400 a couple of months ago. I have gotten widescreen resolutions (such as 1200x800) to run correctly using the 915 resolution hack with my intel Graphics media accelerator card (915). I am just wondering if anyone experiences any soft X lockups. Im using openbox version 3.3 (which i compiled myself). I know its a soft X lockup because conky, my system monitor is active (its still updating itself such as CPU usage etc) but I cant kill X using ctrl-alt-backspace  nor can I switch into TTY console. So i dont have a choice but to hold down my power button and shut it down improperly (I hope this does not physically damage my hard drive). In any case, if anyone experience this and finds a fix please tell :D

---

### Post by esaym on 2006-10-27
The laptop actually overheats unless you manually control the fans?  I thought this was only a problem in linux in the mid-1990's?  Is dell using acpi for fan control now, or is it still in the bios?

---

### Post by robgue on 2006-10-27
i have a dell e1505 and i've never had a problem with overheating with ubuntu. ive been using ubuntu with this laptop since i got it early this year.

---

### Post by Orion2000za on 2006-11-06
I actually think the overheating issue must have been caused by faulty hardware for those who experienced it. But it does get rather warm and the i8ktools represent a way of adjusting the fan/heat for those who like. I do and that means the fan runs a lot more than when I boot into MS XP. 

Sinclair 
now on Edgy

---

### Post by nagrover on 2006-12-05
> **Orion2000za said:**
> Has anyone tried recording anything or using a  mic for Wengo or Skype? I am failing miserably but can't figure out if it is the mic that is bad or that the device is not recognized or if I did not set Kmix proper.

Sinclair

I also can't get my microphone/audio input jack to work. I'm running a fresh install of Edgy. Everything else is working great. Kind of annoying that the mic won't work though.

---

### Post by lifeempowered.com on 2006-12-05
Hey folks, sorry for the absense.  I've been playing with Vista, and let me tell you, Edgy takes the cake!  vista, well, is ok, but nothing near the power of Ubuntu.  Anyway, I'm now on edgy and have updated the How To at the beginning of this thread and will continue to do so as necessary.  thanks to all who I'm linking to who have already discovered the solutions to the changes in Edgy.

---

### Post by steven2 on 2006-12-06
hi im a new user and  ihave aquestion 
i have del inspiron 6400 core 2 dou 2ghz 256 nvidia 1 gb ram
when i play games the cpu fan always is on and in some games like nfs carbon it suddenly turns off even in stating the game
and when rebooted it says its becuase of overheating i wanted to know if i can change the cpu fan RPM to make it cooler
i use windows xp home
thanks!

---

### Post by lifeempowered.com on 2006-12-07
Ok, new How to just posted at the beginning of this thread.  Let me know of any errors or suggestions.

---

### Post by pearlygate on 2006-12-16
Hello, thanks for the guide.

I am having a problem with ATI installaion. After Im done installing and now i'm at the reboot step, my ubuntu won't load up. It crashes right before it displays login screens. 
Can you help me fix this?

---

### Post by Nagus_Gint on 2006-12-29
Sorry,I am afraid I don't understand something about the fans control.
I have installed ubuntu edgy and I have followed all the instructions of the first post about fans controll.
When I log in gkrellm starts,but I cannot set anything about fans thresolds,etc.
However,fans seem to work,and the temperature is never too hot (now it is 34 C,and it seems fans are working at minimum speed).
Is it all okay?

I have also another question.
In the first post nothing is said about screen resolution.I would like to have a wide screen resolution...is it possible?

Thank you!:)

---

### Post by bsgjunkie on 2007-01-01
I'm a linux newbie, but feel comfortable with everything I've done so far. I think I've found the problem, just dont' know how to fix it.

I installed 6.10 on a Dell E1505 core 2 duo, with an ati x1400 graphics card. I used the guide found here at [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI) to install the repositories. I followed the steps, and at the end it has you verfiy the install by using the command 'fglrxinfo' - It returns the info found below instead of the ATI info as suggested in the guide.

$ fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

I followed the trouble shooting section and it seems the below is my problem -

Make sure that the resctricted-modules package installed correspond to the kernel your are running and that you can load the fglrx driver, either by issuing the command "sudo modprobe fglrx" or by verifying that the module appears in the list of loaded modules, by issuing the command "lsmod";

When I run  sudo modprobe fglrx it returns - FATAL: Error running install command for fglrx
And fglrx isn't found in the load mods list either.

The guide doesn't mention what I can do to fix this. Any help would be appreciated.

I expected this install to be much easier as my laptop seemed to be extremely supported. I had hoped for OTB wifi support as suggested, but for some reason its not.

Thanks
Junkie

---

### Post by arthur_kalm on 2007-01-02
Hi, thanks for the HowTO. However, I'm wondering if anyone with a 6400 managed to get sleep or hibernate to work on Edgy. It worked out of the box for Dapper but stopped working when I installed Edgy (fresh install). For me it goes to sleep but then doesn't come back from sleep (blank screen). Hibernate doesn't work at all. Thanks for any help you can provide!

---

### Post by lilmienboy on 2007-01-15
yea mine too, the hibernate doesn't seem to work

---

### Post by golfbuf on 2007-01-20
> **lilmienboy said:**
> yea mine too, the hibernate doesn't seem to work

Same problem here, but I solved the hibernate problem when I noticed a message flash across the screen after I tried to hibernate and it failed.  The message mentioned something about swap.  As it turns out, I had not included a swap partition, since this has 1 G of RAM, which seems to always have excess available.  But, I think hibernation uses the swap space (not really sure).  Anyway, I added a swap partition and confirmed that it's working by checking in a terminal:

golfbuf :~$ cat /proc/swaps

which should list your swaps.

Anyway, now hibernate goes all the way down, but I still haven't solved suspend.

regards,

---

### Post by Orion2000za on 2007-01-24
I want to "bump" an old issue, namely the microphone. I am running Edgy and most stuff is by now working (except hibernate but that is cause I messed the swap and don't have energy to fix right now). 

BUT getting the mic input to work is another issue. It DOES work, I installed Krec (Kubuntu in other words) and it records alright. But using a mic in any application, say Skype, is a non-starter. 

Anyone solved this or have ideas? 

Sinclair:confused:

---

### Post by citadel2 on 2007-01-26
hi
i've this system
Dell Inspiron 6400
2ghz  Core 2 Duo Processor
1 GB 533 RAM
120 GB HD
nvidia 7300 go 256MB Video Card
15.4 XGA (1280x800) w/ TrueLife
8x DVD +/- RW/CD-RW
54Mbps Dell 1390 Wireless
i've problem playing games f.first they run very well but after afew minutes it turns off automatically duo to overheating in gpu i don't know what to do.i even monitored the cpu and gpu temps and cpu is not bad(40-45 C)
is there any program controlling initial bios to avoid turning off? because it only gets hot when im in menus or short animation movies of the game not when playing the game.
I've also installed windows vista ultimate edition and when working with it when there is no load cpu temp is (40-43) and gpu is (68-73) is it ok or overheated?
tanx

---

### Post by ronlybonly on 2007-01-28
First off, THANKS for the Howto!!! Second... I just compiled and installed a patched kernel, and now the i8k fan module is not working. at all. I guess I sould have expected this, but is there an easy remedy to this problem? I'm really not too excited about my computer catching on fire or something when I run the new kernel :wink:

-Andrew

---

### Post by Aramil Moonmist on 2007-02-22
omg i love you

i have had so many troubles with my video card, have NEVER gotten beryl working before, and hadnt heard of automatix. (im a noob, yes i know, but everyone has to start somewhere)

my computer is honestly habitable now thanks to this guide *bows down*

---

### Post by Qwacko on 2007-03-02
Hey Guys

I managed to get suspend working on my Dell 6400, I used to try suspend and the screen would turn off but nothing else would happen (hard drvies still running etc..).

What i did was take a look at the file /etc/default/acpi-support and decided to try something out, what i did was change the line that said :

```
HIBERNATE_MODE=shutdown
```

to say:

```
HIBERNATE_MODE=platform
```

I am not sure why this worked but it seems to work fine, This would not fix the problems with X not starting correctly on restart. 

Just note that I have a Core 2 Duo CPU and the Intel Graphics option so this may play a part in this working.

Good Luck
James

---

### Post by lifeempowered.com on 2007-03-27
Ok, I've updated the how to, again, and am now trying out Feisty Fawn.  I'll post results and how to as soon as the actual release comes out.  Right now, in it's beta, there are too many weird issues to do a how to.  However I will say, that with some tweaking I've gotten ATI drivers with 3D working, Wireless (Dell) working, and VMWare Server installed thanks to a patch.  Now I'll try to get Beryl working:)

---

### Post by lifeempowered.com on 2007-03-27
> **pearlygate said:**
> Hello, thanks for the guide.

I am having a problem with ATI installaion. After Im done installing and now i'm at the reboot step, my ubuntu won't load up. It crashes right before it displays login screens. 
Can you help me fix this?

Are you sure your specs are the same as mine?  I only know what works for my system.

---

### Post by bigfatdummy on 2007-03-28
Got my wireless working with 7.04

I am unable to connect with 128 bit wep 

I connect to all my idiot neighbors unsecured wireless nets without any trouble. 

Got it...

I'm a tard and had pass key selected and not hex. Works like a charm.

---

### Post by lifeempowered.com on 2007-03-28
Excellent!  Yea, I noticed the wifi security is much easier to use with feisty!  Still working on getting Beryl to work, anyone have success?

---

### Post by lifeempowered.com on 2007-04-03
Ok, got Feisty working 100%!  Check out my how to: [http://www.ubuntuforums.org/showthread.php?t=399913](http://www.ubuntuforums.org/showthread.php?t=399913)

---

### Post by derail on 2007-05-04
I have the same hardware as the OP, except I only have 1GB of RAM and a 1.66 Core Duo... also I have a mobility x1300, not a 1400. When I pop in the ubuntu cd and hit START INSTALL in the first menu, X cannot start. It also occurs if I use Graphical Safe Mode, and I've checked and the driver in xorg.conf is the vesa driver. I can't understand why it doesn't work.

edit: I am using Feisty btw

---

### Post by Joedisney on 2007-05-12
I am a MCSE, after loading and looking at Linux (New Just loaded, for the first time) I would have no idea of how to get to the menus to load drivers such as WIFI, ATI CARD ETC… (CAN’T EVEN SURF THE WEB ON MY DELL 6400). Give me a break, Linux will never have a chance unless THE COMMUNITY makes it easy for the average user. If I have to read a book just to surf the web, you can keep Linux, I will have to pay Microsoft for an OS that works. 

I WOULD LOVE TO SEE COMPITION FOR MICROSOFT HOWEVER LINUX IS NOT CLOSE. USERS WILL NEVER GO FOR THIS. This is an OS for people that have way to much time. I hate Bill Gates he is a trader, to the USA, I guess I will have to make that pc of crap even more money with Vista.





> **lifeempowered.com said:**
> **UPDATE: This is my How-To I use for Edgy Eft only, on my Inspiron 6400**

System Tested On:

Dell Inspiron 6400
1.60 Core Duo Processor
2 GB 533 RAM
160 GB HD
x1400 ATI 256MB Video Card
15.4 XGA (1280x800) w/ TrueLife
8x DVD +/- RW/CD-RW
54Mbps Dell 1390 Wireless (Broadcom driver)
S-Video/Firewire/USB/etc.

Only thing not working: Sony card reader. 

Updated as of March 28, 2007:

**Initial Setup **

1. Install base Edgy install.
2. After install, open the sources file:
```

sudo gedit /etc/apt/sources.list

```
And uncomment all entries that begin with "deb http" or "deb-src" except for the CD ROM, make sure it's commented out

3. Next update by entering the following, twice.
```

sudo apt-get update

```

4. Now open your Software Sources in: SYSTEM > ADMINISTRATION > SOFTWARE SOURCES
and make sure all the boxes under "Downloadable from the Internet" are checked.  Click "CLOSE" and then "RELOAD"

5. Go to: SYSTEM > ADMINISTRATION > UPDATE MANAGER
and first click "CHECK", then click "INSTALL UPDATES"

After your updates are finished installing, REBOOT NOW

After a reboot, create a working folder for the following install steps.  Just a way to keep your system clean.  Go into your home folder and create a folder called "install" or something.  Now open  terminal and go to that directory before you proceed.

6. Now you're going to get some tools for future steps.
```

sudo apt-get install build-essential module-assistant build-essential fakeroot dh-make debconf libstdc++5 linux-headers-$(uname -r)

```

7. Update again, just in case, and install any updates that appear in the top right corner.
```

sudo apt-get update

```

**Now you'll install your wireless device**

1. Clean your system by entering the following code.  Disregard errors as you may not have ndiswrapper.
```

sudo rmmod ndiswrapper
sudo apt-get remove ndiswrapper-utils

```

2. Download driver files.  Unzip them.
```

wget http://www.jrdw.com/linux/wireless/bcmdrivers.tar.gz
tar -xzvf bcmdrivers.tar.gz

```

3. Download latest Ndiswrapper, I've included th latest at the time of this edit.  Unzip it.
```

wget http://superb-east.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.38.tar.gz
tar -xzvf ndiswrapper-1.38.tar.gz

```

4. Blacklist the bcm43xx firmware drivers that come default.
```

sudo gedit /etc/modprobe.d/blacklist

```
Add the following line to the end of the file and save your changes:

blacklist bcm43xx

***REBOOT NOW***

After a reboot open a terminal and go to the same folder you created earlier.

5. Get into the ndiswrapper folder it created when you unzipped it.  The [TAB] represents using your TAB key to finish the name of the folder.
```

cd ndis[TAB]

```

6. Begin the install process.  Do the following multiple times, until you see some error about no files or directories or something.
```

sudo make uninstall

```

7. Main install process
```

sudo make
sudo make install

```

8. Installing drivers, first in your terminal go to the folder that unzipped earlier with the driver files in it.
```

cd bcm[TAB]
sudo ndiswrapper -i bcmwl5.inf
sudo ndiswrapper -l

```

NOTE: If you don't see a message that says driver present, hardware detected, you may have problems.

```

sudo ndiswrapper -m
sudo modprobe ndiswrapper

```

9. Test your wireless.  You may need to reboot, however a reboot won't suffice, you'll need to shutdown and then restart.  Your WIFI light should illuminate when successful.
```

sudo iwlist scanning

```

10. Before trying to connect to a network I recommend installing Wifi-Radar to make your life simpler.  It manages your wireless networks.  To install and use it open Synaptic Package Manager and search for "wifi-radar".  Install it and then run it from the Applications-->Internet menu.

**Now time to install ATI drivers!**

1. Disable Composite Extension - In Ubuntu Edgy the Composite extension is enabled by default, however, fglrx does not yet support Composite with DRI. In order to disable Composite you have to edit the xorg.conf file:
```

sudo gedit /etc/X11/xorg.conf

```
and add these lines at the end of the file:

Section "Extensions"
        Option  "Composite" "Disable"
EndSection

Section "ServerFlags"
        Option  "AIGLX" "off"
EndSection

2. Update System & Install the 8.28.8 ATI Driver in the Ubuntu Repos.  For instructions on installing the proprietary drivers, click here: [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)
```

sudo apt-get update
sudo apt-get install linux-restricted-modules-$(uname -r) #Okay if it is already installed
sudo apt-get install xorg-driver-fglrx

```

3. Now Edit Your xorg.conf File to Reflect the Appropriate Resolutions and Replace "vesa" under the Device section with "fglrx"
```

sudo gedit /etc/X11/xorg.conf

```
To edit your resolutions, add the resolutions your monitor goes up to to each of the resolutions lines in the file.  They are set at a default of "1024x728" as the max, just add the top res in the same format.  Alternatively you can run:
```

sudo aticonfig --initial

```

4. Run the ATI config script
```

sudo aticonfig --overlay-type=Xv

```

5. Reboot and you should see your new res.  Login and type "fglrxinfo" at the terminal to see if the ATI driver is loaded.  Check for direct rendering by typing:
```

glxinfo | grep direct

```

You should now be able to install Beryl without problems.

**BERYL:**

1. Add Beryl repositories.
```

sudo gedit /etc/apt/sources.list

```
Add the following to the end:
deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main

2. Add the key
```

wget -q http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg -O- | sudo apt-key add -

```

3. Now update
```

sudo apt-get update

```

4. Install XGL Server
```

sudo apt-get install xserver-xgl

```

5. Install Beryl and Themes
```

sudo apt-get install beryl emerald-themes

```

Next you'll configure it.  I configure mine to have a seperate session so that's what I'll cover here.

6. Now create a startup script
```

sudo gedit /usr/local/bin/startxgl.sh

```

I added the following into the empty file just created:
```

#!/bin/sh
Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
exec dbus-launch --exit-with-session gnome-session

```

7. Make the script executable
```

sudo chmod a+x /usr/local/bin/startxgl.sh

```

8. Create a Login Entry
```

sudo mkdir -p /etc/X11/sessions
sudo gedit /etc/X11/sessions/xgl.desktop

```
Now add the following and save it:

[Desktop Entry]
Encoding=UTF-8
Name=Xgl
Exec=/usr/local/bin/startxgl.sh
Icon=
Type=Application

9. If it tests okay, add a script to load it automatically every time the Xgl session is loaded.  Create the script and paste the following into it as so:
```

sudo gedit /usr/local/bin/start_beryl.sh

```

Now add the following and save the changes:
```

#!/bin/bash
#
# Start beryl-manager within gnome-session
#
if (( `ps -A -o comm | grep -c '^Xgl$'` == "1" )); then
       DISPLAY=:1 beryl-manager
       DISPLAY=:1 beryl-xgl
else echo "${0}: Error: beryl-manager not launched. Xgl not running?"
fi

```

10. Now make the script executable:
```

sudo chmod a+x /usr/local/bin/start_beryl.sh

```

11. Next add the following to the "Startup Programs" inside Programs>Preferences>Sessions

/usr/local/bin/start_beryl.sh

12. Done!  You can reboot and enjoy!  Troubleshooting: [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL)

**UPDATE:** Thanks to nachotronics, the following will fix your screen brightness buttons!

1. Using a terminal, open the blacklist file again:
```

sudo gedit /etc/modprobe.d/blacklist

```
Add the following to the end:

blacklist video

2. Reboot and it should work!  Thanks Nacho!

[B]
Here's a little extra fun stuff you can add:[/B]

Fan and temp control
1. sudo apt-get install i8kutils gkrellm gkrellm-i8k
2. sudo modprobe i8k force=1
3. sudo gedit /etc/modules
4. add the following line to the end of the file: i8k force=1
5. go to System > Preferences > Sessions > Startup Programs
6. Click ADD and put the command: gkrellm
Now you will see the GKrellm utility load at startup and you can then configure your fan thresholds, etc.

Configure front panel buttons, etc.
1. System > Preferences > Keyboard Shortcuts
2. Choose custom actions for your special keys, click an action and press the key!

Automatix **For Edgy and Dapper**
1. Visit [www.GetAutomatix.com]("http://www.GetAutomatix.com") and follow instructions for your distro.


Optional things I did:

Citrix (I use this so it's optional) 
**For Edgy and Dapper**
1. Download 9.0 client for linux here: [http://www.jrdw.com/linux/citrix/linuxx86.tar.gz]("http://www.jrdw.com/linux/citrix/linuxx86.tar.gz")
2. Download and install libmotif3 here: [http://www.jrdw.com/linux/citrix/libmotif3_2.2.3-1.2ubuntu2_i386.deb]("http://www.jrdw.com/linux/citrix/libmotif3_2.2.3-1.2ubuntu2_i386.deb")
3. Extract citrix to folder and go to folder with terminal
4. sudo ./setupwfc
5. Install default with Y for all answers.  Be careful during the License acceptance as it defaults to reject so if you hold the ENTER key it will exit the install!
6. 3 to quit install

VMWare 
**For Edgy and Dapper**
1. Download vmware server tar.gz file from: [http://download3.vmware.com/software/vmserver/VMware-server-1.0.1-29996.tar.gz]("http://download3.vmware.com/software/vmserver/VMware-server-1.0.1-29996.tar.gz")
2. place downloaded file somewhere in a folder in your home folder and using terminal CD into that folder
3. tar xvzf VMware-server-1.0.1-29996.tar.gz
4. cd into the folder it creates
5. sudo ./vmware-install.pl
2. Obtain a free serial at [www.vmware.com](www.vmware.com)

IEs4Linux  
**For Edgy and Dapper**
1. First get Wine using Automatix.
2. Open a terminal
3. If you haven't, uncomment the Universe lines in sources.list
4. sudo apt-get install cabextract
5. CD into the directory you want to download the ie4linux package to
6. wget [http://www.tatanka.com.br/ies4linux/downloads/ies4linux-latest.tar.gz](http://www.tatanka.com.br/ies4linux/downloads/ies4linux-latest.tar.gz)
7. tar zxvf ies4linux-latest.tar.gz
8. cd ies4linux-*
9. ./ies4linux
10. You'll be prompted which IE you want and other options, most options just leave default.


Done and have fun!

note: I don't guarantee this will work for you so don't yell at me!:)

---

### Post by neptho on 2007-06-08
> **Joedisney said:**
> I am a MCSE

I know, I know, don't feed the trolls.. however, the above is your first problem.  The second is, you don't want to have to learn how to make the machine work.  You have custom hardware which is barely supported with Linux; if the hardware producers did not provide drivers for Windows, nobody would use them.

Stick with Windows.  It'll be easier on all of us.

---

### Post by nnobakht on 2007-06-16
I Tried installing My wireless card but i have the new Wireless N card and when i run your steps this is the messages that come up.```
navid@Navids:~/Desktop/file/ndiswrapper-1.38$ cd bcmdrivers/
navid@Navids:~/Desktop/file/ndiswrapper-1.38/bcmdrivers$ sudo ndiswrapper -i bcmwl5.inf
driver bcmwl5 is already installed
navid@Navids:~/Desktop/file/ndiswrapper-1.38/bcmdrivers$ sudo ndiswrapper -l
bcmwl5 : driver installed
navid@Navids:~/Desktop/file/ndiswrapper-1.38/bcmdrivers$ sudo ndiswrapper -m
module configuration already contains alias directive

navid@Navids:~/Desktop/file/ndiswrapper-1.38/bcmdrivers$ sudo modprobe ndiswrapper
navid@Navids:~/Desktop/file/ndiswrapper-1.38/bcmdrivers$ sudo iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

```

any ideas on what the error is or on what i need to do differenly?

Total specifications of my computer is: 
Intel Core 2 Duo 1.8
2 Gb ram
120gb HD
Wireless N card
Bluetooth
Dvd Burner

---

### Post by orsmate on 2007-06-24
Hello
I'm a newbie in ubuntu and hope You could give me some help,
so i installed everything just as it was written here i have almost the same configuration, but beryl does not want to work. beryl manager is running in the system tray but it does not load really. when i push the "reload window manager" button all windows flash for a moment and gnome comes back again.
hope my explanation is understandable 
and also hope you can help me
thanks

---

### Post by duydaniel on 2007-07-13
[QUOTE]> **lifeempowered.com said:**
> **UPDATE: This is my How-To I use for Edgy Eft only, on my Inspiron 6400**

System Tested On:

Dell Inspiron 6400
1.60 Core Duo Processor
2 GB 533 RAM
160 GB HD
x1400 ATI 256MB Video Card
15.4 XGA (1280x800) w/ TrueLife
8x DVD +/- RW/CD-RW
54Mbps Dell 1390 Wireless (Broadcom driver)
S-Video/Firewire/USB/etc.

Only thing not working: Sony card reader. 

Updated as of March 28, 2007:

**Initial Setup **

1. Install base Edgy install.
2. After install, open the sources file:
```

sudo gedit /etc/apt/sources.list

```
And uncomment all entries that begin with "deb http" or "deb-src" except for the CD ROM, make sure it's commented out

3. Next update by entering the following, twice.
```

sudo apt-get update

```

4. Now open your Software Sources in: SYSTEM > ADMINISTRATION > SOFTWARE SOURCES
and make sure all the boxes under "Downloadable from the Internet" are checked.  Click "CLOSE" and then "RELOAD"

5. Go to: SYSTEM > ADMINISTRATION > UPDATE MANAGER
and first click "CHECK", then click "INSTALL UPDATES"

After your updates are finished installing, REBOOT NOW

After a reboot, create a working folder for the following install steps.  Just a way to keep your system clean.  Go into your home folder and create a folder called "install" or something.  Now open  terminal and go to that directory before you proceed.

6. Now you're going to get some tools for future steps.
```

sudo apt-get install build-essential module-assistant build-essential fakeroot dh-make debconf libstdc++5 linux-headers-$(uname -r)

```

7. Update again, just in case, and install any updates that appear in the top right corner.
```

sudo apt-get update

```

**Now you'll install your wireless device**

1. Clean your system by entering the following code.  Disregard errors as you may not have ndiswrapper.
```

sudo rmmod ndiswrapper
sudo apt-get remove ndiswrapper-utils

```

2. Download driver files.  Unzip them.
```

wget http://www.jrdw.com/linux/wireless/bcmdrivers.tar.gz
tar -xzvf bcmdrivers.tar.gz

```

3. Download latest Ndiswrapper, I've included th latest at the time of this edit.  Unzip it.
```

wget http://superb-east.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.38.tar.gz
tar -xzvf ndiswrapper-1.38.tar.gz

```

4. Blacklist the bcm43xx firmware drivers that come default.
```

sudo gedit /etc/modprobe.d/blacklist

```
Add the following line to the end of the file and save your changes:

blacklist bcm43xx

***REBOOT NOW***

After a reboot open a terminal and go to the same folder you created earlier.

5. Get into the ndiswrapper folder it created when you unzipped it.  The [TAB] represents using your TAB key to finish the name of the folder.
```

cd ndis[TAB]

```

6. Begin the install process.  Do the following multiple times, until you see some error about no files or directories or something.
```

sudo make uninstall

```

7. Main install process
```

sudo make
sudo make install

```

8. Installing drivers, first in your terminal go to the folder that unzipped earlier with the driver files in it.
```

cd bcm[TAB]
sudo ndiswrapper -i bcmwl5.inf
sudo ndiswrapper -l

```

NOTE: If you don't see a message that says driver present, hardware detected, you may have problems.


Hi.

I am on the step to install the wireless driver but the following error popped up

```
daniel@daniel-laptop:~/bcmdrivers$ sudo ndiswrapper -i bcmwl5.inf
driver bcmwl5 is already installed
daniel@daniel-laptop:~/bcmdrivers$ sudo ndiswrapper -l
bcmw5 : invalid driver!
bcmwl5 : invalid driver!
bcmwls.ini : invalid driver!
bcwml5 : invalid driver!
daniel@daniel-laptop:~/bcmdrivers$ 

```

I did try another guide to install Dell Wireless... but it did not work... so that was why when I go with this guide, the system respond that "bcmwl5 is already installed"
And I suspect that because the previous guide made me install bcmwl5... and somehow... it not worked when I go with this guide. :confused:

---

### Post by svasanth on 2007-07-18
Hi,
  
    Any idea how to enable DMA for dell inspiron 6400 DVD drive?.The dvd writing is at 0.90x but it supposed to be 4x.hdparm -d 1 /dev/hdc did not work.

Thanks

---

### Post by Ylang on 2007-08-27
Thanks for a great how-to. I am really new to Ubuntu and I thought it was the easiest fix ever!

---

### Post by fadyek on 2007-12-04
concerning the mic/audio problem mentioned a couple of times in this thread:
I have Dell Inspiron 6400 nseries and Ubuntu 7.04 and had the same problem. After calling the support I was advised to do what is mentioned here [http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/Audio_recording_does_not_work](http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/Audio_recording_does_not_work) even though it applies more to the Desktop Dimension 530n.
I did and was able finally to make a successful test call using Skype. The sound recorder didn't work however. But it doesn't matter for now. I will check other applications like gaim and see if it works also.
I have been also advised to upgrade to Ubuntu 7.10, but the above solution was enough for me for now.
Hope this helps.

---

### Post by unshareef on 2008-01-20
Dear Ubuntu + dell users

I have an Inspiron 6400 and have installed gutsy.

The problem is, I believe, my processor. I have an Intel Core duo T2XXX processor but the usage keeps going upto 100%. It is normally at 46%. This is clearly abnormal as it should for the most part remain below 10% right? Any idea on how to fix this?

Also, my front control buttons on my laptop dont seem to work. When I press the volumer buttons, a pop-up volume bar does appear but the volume doesnt adjust at all. As for the play/pause/stop button, they dont work with all players e.g amarok. Any one know how to fix this?

Many thanks.

---

### Post by abo_shreek11 on 2008-03-22
> **Daniel15 said:**
> You forgot one important thing: i8kutils, GKrellm and gkrellm-i8k. Without them, the system won't be able to control the fan speed, and there's a possibility of overheating. Install them via Synaptic, or apt-get (```
apt-get install i8kutils gkrellm gkrellm-i8k
```). Then, install the i8kutils module:
```
modprobe i8k force=1
```
Run GKrellm with the i8k panel, and see if the fans are working.
You'll need to add a line to the /etc/modules file:
```

i8k force=1

```


That's HyperMemory. Basically, the card has half of its memory as internal memory, and will borrow some memory from the system if required.
For example, my X1400 is a 256MB Hypermemory. It has 128MB onboard, and will borrow up to 128MB if it needs it.

Also, about Compiz, I made a post about it on my blog: [http://www.daniel15.com/blog/2006/09/18/laptop-linux-and-compiz/](http://www.daniel15.com/blog/2006/09/18/laptop-linux-and-compiz/) . Basically, once you install the ATI drivers (8.28.8 ), follow the tutorial at [http://www.compiz.net/topic-389-1.html](http://www.compiz.net/topic-389-1.html) (use the second howto)

EDIT: I noticed you mentioned Compiz:

I would suggest to use the **second howto**. This is so:
[LIST]
[*] If Compiz stops working, you have an alternate configuration
[*] You can still play OpenGL-accelerated games, by following the instructions at [http://www.compiz.net/topic-1623-howto-opengl-acceleration-with-session-still](http://www.compiz.net/topic-1623-howto-opengl-acceleration-with-session-still)
[/LIST]

HI
I am a newbie to Ubuntu and linux. when i code the fan instructions i get:

thinkbit@dell-laptop:~$ apt-get install i8kutils gkrellm gkrellm-i8k
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

would you tell me what to do, please. and how i can sure that my fans is functioning propably. 

Thank you

---

### Post by xsouldeath on 2008-06-16
well as a windows user..
anyways LEFT CLICK THE ICON to see connections..
if you think it is NOT working run

sudo iwlist scanning

if you don't see connections scanned from there, THEN you have a problem.
But if you DO.. then you need to remember to LEFT CLICK the connection icon in that system tray. If you right click and go to edit wireless connections..
it will pretty much be useless..

Just a silly think that made me go through all the tutorials again and again.. :)

Speaking of which
for Dell Inspiron 6400 laptop
[http://ubuntuforums.org/showthread.php?t=257684](http://ubuntuforums.org/showthread.php?t=257684)
and
[http://www.dausha.net/Technical/EnablingBroadcom1390WLAN](http://www.dausha.net/Technical/EnablingBroadcom1390WLAN)
seemed the best.

---

