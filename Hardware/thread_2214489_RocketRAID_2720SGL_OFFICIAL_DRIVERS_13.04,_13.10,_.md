---
title: "RocketRAID 2720SGL OFFICIAL DRIVERS 13.04, 13.10, 14.04, 14.10"
date: 2014-04-01
forum: Hardware
---

### Post by JohnAreBee on 2014-04-01
[CENTER][B][U]
So I decided to do a rewrite so its a little more strait forward for the novice user to get there system rolling, and to clean it up a bit. 
In future edits I will change the date below so you know what version you are working off of and if there is newer software for you.[/U][/B][B][COLOR=#ff0000][SIZE=6][U]
June 19th 2015[/U][/SIZE][/COLOR][/B]
[/CENTER]
 [B][COLOR=#000000][SIZE=2]First off lets get the relevant links out of the way  along with their md5sums in "s:[/SIZE][/COLOR][COLOR=#ff0000][SIZE=2]
*** Any drivers/software listed as "Unpublished" were provided to me directly from Highpoint Tech Support, I did not make any changes  unless noted below.[/SIZE][SIZE=4][SIZE=2] ***[/SIZE][/SIZE][/COLOR][COLOR=#000000][SIZE=4][U]
RocketRAID 2720SGL[/U][/SIZE][/COLOR][/B]
[LIST]
[*][SIZE=3]RocketRAID 2720SGL Manual: [v2.2]("http://www.highpoint-tech.com/PDF/rr2700/RR271x_272x_User_Guide_v2.2_12_10_11.pdf")      "0986553d727c7d79ba153703f3d61b79"[/SIZE] 
[*] [SIZE=3]Published Linux Drivers: [v1.5.18]("http://www.highpoint-tech.com/BIOS_Driver/rr272x_1x/Linux/RR272x_1x_Linux_Src_v1.5.18_15_04_21.tar.gz")      "965dc82803b498c27f167fdaf40f4d2d[/SIZE]" 
[*] [SIZE=3]Published Web RAID Management (WebGUI): [v2.1.5.13.0409]("http://www.highpoint-tech.com/BIOS_Driver/HRM/Linux/WebGUI-Linux-v2.1.5-130409.tgz")      "e65216725b279e74d583768a989e2ee7[/SIZE]" 
[*] [SIZE=3]Published Command Line Interface (CLI): [v3.5]("http://www.highpoint-tech.com/BIOS_Driver/HRM/Linux/CLI-Linux-3.5-100701.tgz")      "3bebb9a4902e65ca3b374e716a6d8c0e[/SIZE]" 
[*] [SIZE=3]Published SGL BIOS: [v1.12.0]("http://www.highpoint-tech.com/BIOS_Driver/rr272x_1x/BIOS/RR272x_1x_BIOS_v1.12.0_15_01_28.zip")      "d0387ab31b71846bac59e3bad8f5c3d4[/SIZE]" 
[*] [SIZE=3]Unpublished WebGUI: [v2.1.6.0.1_14_04_25]("https://www.dropbox.com/s/mvxmxzg3o0oiyxi/WebGUI_Linux_v2.1.6.0.1_14_04_25.tgz")      "2dfe330e67c5c9eebe0b0325dccbaabd[/SIZE]" 
[*] [[SIZE=3]Manufacture Webpage[/SIZE]]("http://www.highpoint-tech.com/USA_new/series_rr272x.htm") 
[*][SIZE=3][Compiled Kernel Drivers]("https://www.dropbox.com/s/ore6z6n8uvd9e3v/2720SGL.preos.drivers.only.tar.gz")  "18af9c9ac77533e696e48153b2b6b7bf" [COLOR=#ff0000]**THIS IS ONLY THE DRIVER FILES FEEL FREE TO SUBMIT ANY MISSING AND I WILL ADD TO THE PACKAGE**[/COLOR][/SIZE] 
[/LIST]

[CENTER][SIZE=3][COLOR=#ff0000][B]***Official driver pakage now officially supports up to kernel v4.0.4, may work on later versions but they only technically support up to v4.0.4***
[/B][/COLOR][/SIZE][/CENTER]
 [B][COLOR=#000000][SIZE=4][U]
RocketRAID 2720C2[/U][/SIZE][/COLOR][/B]
 
[LIST]
[*] [SIZE=3]RocketRAID 2720C2 Manual: [v1.0]("http://www.highpoint-tech.com/PDF/rr2700/RR2720C2/RocketRAID%202720C2%20User%20Manual_v1.00.pdf")  "d4eb3751870cbd950d71c8c5ac7a19b8"[/SIZE] 
[*] [SIZE=3]Publish C2 BIOS: [v1.0]("http://www.highpoint-tech.com/BIOS_Driver/RR2720C2/BIOS/RR272xC-BIOS-v1.0-130925.zip")  "8fd1f69f23f44f5467557c11f5aa66a7"[/SIZE] 
[*] [SIZE=3]Published Web RAID Management: [v2.1.6-131015]("http://www.highpoint-tech.com/BIOS_Driver/RR2720C2/WebGUI/WebGUI-Linux-v2.1.6-131015.tgz")[/SIZE]  [SIZE=3]"20d63065009a120baae8a266983e2964"[/SIZE] 
[*] [SIZE=3]Published Linux Drivers: [v1.0.1]("http://www.highpoint-tech.com/BIOS_Driver/RR2720C2/Linux/RR272x_1xC_Linux_Src_v1.0.1_13_10_16.tar.gz") "415168ffb795bcb892125fb9d34daf00"[/SIZE] 
[*] [SIZE=3]Unpublished Linux Drivers: [v1.0.2_15_04_29]("https://www.dropbox.com/s/a5271hjen2v3gcc/RR272x_1xC_Linux_Src_v1.0.2_15_04_29.tar.gz")[/SIZE] [SIZE=3] "89850273a7483a60ba114d846b12ec2b"[/SIZE] 
[*] [[SIZE=3]Manufacture Webpage[/SIZE]]("http://www.highpoint-tech.com/USA_new/series_rr2720C2-Overview.htm") 
[/LIST]
 [SIZE=4]
[/SIZE]**[SIZE=4]_RocketRAID 2720SGL/2720C2 Pre OS Driver Manual_[/SIZE]****_:_** [SIZE=3][05.19.2012]("http://www.highpoint-tech.com/BIOS_Driver/rr272x_1x/Linux/Install_Ubuntu_RR271x_RR272x.pdf")  "d18f18d563c58a36ef61f6fa82c34849"
[/SIZE]**[SIZE=4]_RocketRAID 2720SGL/2720C2 Pre OS Drivers Base_[/SIZE]**: [SIZE=3][i386]("http://www.highpoint-tech.com/BIOS_Driver/rr272x_1x/linux_1.5/Binary/Ubuntu/rr272x_1x-ubuntu-12.10-i386-v1.5.13.0327.tgz"), [x86_64]("http://www.highpoint-tech.com/BIOS_Driver/rr272x_1x/linux_1.5/Binary/Ubuntu/rr272x_1x-ubuntu-12.10-x86_64-v1.5.13.0327.tgz")   "cacf0074b48068240027409e2b8f91df"   "2ed3c810e3b225a6a9b323f18a684b08"[/SIZE]

[SIZE=4]
[/SIZE]**[SIZE=4]_RocketRAID 2720SGL / 2720C2 General Info:_[/SIZE]**
     [SIZE=3]The RocketRAID 2720SGL and the 2720C2 (Cross Card Arrays) are the same card. If you purchase a 2720C2 you get 2 x 2720SGL cards, the software and BIOS needed to turn them into 2720C2 cards. What the C2 firmware offers that the SGL does not is "Cross Card Sync" What that means is you can have a single array that spans more than 1 2720 card. The most I personally have used in a single installation is 3x 2720 cards with 1 array containing 24 SAS Drives, that being said it will also work fine with a single 2720C2 (but that is kind of pointless). Now you will probably say great why bother even using the 2720SGL firmware over the C2 firmware? Well you will be trading off some features and specs that the C2 firmware does not support (at least as of the time of the post). Highpoint has recently given us 2720 owners a new v1.12.0 SGL BIOS that brings a bunch of new features as well as some performance improvements, LTO Tape support, and 4Kn support. I am not going to get into everything but you can go to the Highpoint Tech site and compare the features of the 2720SGL and the 2720C2. Unless I absolutely need 1 array over 8+ disc I run the SGL firmware at the moment because it is the newest, and it offers more features that I deem more important than simply having 1 array. Again everyone is different every system is different, you are going to have to look at everything and make your own decision. Hopefully soon Highpoint will release an updated C2 BIOS with new features like the did with the SGL but until then I like the SGL personally. The BIOS flashing process is the same regardless of what you choose to use. The simplest way for a novice to change/update they cards BIOS is to use the WebGUI, obviously this can only be done if the card is already installed and configured on a system. Your only other option is to flash the BIOS in DOS.[/SIZE]

[B][SIZE=4][U]Flashing BIOS with WebGUI Access:
[/U][/SIZE][/B][SIZE=3]Log into your WebGUI with localhost or your internal IP address using port 7402 the default user and password are "RAID" and "hpt" obviously without the "s. Click the "Physical" Tab, if you have more than one card installed you can switch between what card you are looking at with the dropdown menu on the top left, click browse, choose BIOS image file, then submit. DO NOT power off the pc, stop or refresh webpage untill it tells you it is complete. The new BIOS image will not be loaded until you power off or reboot the machine. Again if you have more than one card installed you have to repeat this process for each card you want to update/change BIOS version. You do not need to flash one, reboot, flash, reboot, you can flash as many cards as you like and then reboot. [/SIZE][B][SIZE=4]

[IMG]http://i62.tinypic.com/2itk9w8.jpg[/IMG]
_Flashing BIOS without WebGUI Access:_[/SIZE][/B]
     [SIZE=3]The easiest way to flash it for initial setup is to use Unetbootin and create a free dos usb drive extract the BIOS image and flash software to that usb, then boot your machine off the usb and execute the flash command then follow instructions.[/SIZE]
To Install Unetbootin:
```
sudo apt-get install unetbootin
```

To Flash BIOS from FreeDOS :
```
load.exe rr2720.112
```

[IMG]http://i57.tinypic.com/33xejhc.jpg[/IMG]

**[SIZE=4]_Installing PreOS Drivers (_[/SIZE]****[COLOR=#ff0000][SIZE=4]_this is only needed if you want to use the RAID Array as Main System Drive, if only using RAID for non-system drive you can skip this_[/SIZE][/COLOR]**[B][SIZE=4][U]).
[/U][/SIZE][/B][SIZE=4]       [SIZE=3]This is where things can get a little tricky for the novice user. If you are running 12.04/12.10 you can just download the preOS base and follow the default instructions, but if you are running anything newer than that a bit of modification is required, but the process is universal for every version the only thing that changes in the base package is the actual driver.you can have as many driver versions as you want in with the base it will automatically pick the correct one and it will tell you if the correct one is missing. Linux being the way it is there is always more than one way to skin a cat, all i can do is tell you the way I do things. I have had a lot of exposure to the Ubuntu/RocketRAID combo, a client of mine who has many servers and workstations exclusively use Ubuntu and the RocketRAID 2720 so I have had much experience with the setup/update of drivers and BIOS. Again I will repeat this, YOU ONLY NEED TO GO THROUGH THE PRE-OS PROCEDURE IF YOU WANT YOUR SYSTEM INSTALLED ON THE RAID ARRAY! If you are going to use the Array as an add-on to the system you can just install the drivers normally once installed and booted into your system. Now if you are still reading this part then you have decided that you do want your RR array as a system drive, that being said you need to make sure that the RR BIOS is initialized (when the blue press ctrl+h screen appears) prior to any other storage related add-on ROM or you may have issues getting the system to boot. I have not run into this issue personally but this is what Highpoint recommends. 

Now we need 2 basic things to move forward, an Ubuntu CD/DVD/USB and a RR driver USB. The base package and procedure is going to be the same regardless of Ubuntu version only the actual driver version is different, later on I will explain how to create you own driver and insert it into the preOS base. 

[SIZE=3]So now that you have your Ubuntu media and your RR preOS base USB go ahead and boot into Ubuntu (or Ubuntu Server) choosing install Ubuntu option at the grub menu. [/SIZE][/SIZE][/SIZE][SIZE=3]After choosing your language hit ctrl+alt+f2 to enter shell, basically you need to take the files from the USB, copy them to the system, then run the script. Your USB address may differ in my case it is /dev/sda. It will make things easier on you if the only things on the driver USB is the base and drivers.[/SIZE]

[SIZE=3]```
:# mount /dev/sda1 /mnt
:# mkdir /tmp/hptdd
:# cp -rf /mnt/* /tmp/hptdd
:# umount /mnt
:# sh /tmp/hptdd/preinst.sh
```[/SIZE]
[SIZE=3]Next switch backto the instalation and finish the install, when you get to the "Instalation Complete Restart System" prompt DONOT REBOOT! You will have to redo the installation  if you do. Switch back to the shell and execute the final command.
```
:# sh /tmp/hptdd/postinst.sh
```
Now you will be able to boot into your system to take care and wrap up the last few steps with the RAID Management software.
[SIZE=4][U][B]
Installing Drivers in Ubuntu
[/B][/U][SIZE=3]Highpoint recently updated the 2720SGL drivers and simplified the installation a bit, so download the drivers and the WebGUI or CLI packages ([COLOR=#ff0000]you can only have 1 installed either the WebGUI or the CLI NOT BOTH[/COLOR]). Open a terminal session and navigate to the location that you saved the packages to, and extract them:

[SIZE=3]```
:$ tar -xzf RR272x_1x_Linux_Src_v1.5.18_15_04_21.tar.gz
```

Next make sure we can execute the driver file:
```
:$ chmod +x RR272x_1x_Linux_Src_v1.5.18_15_04_21.tar.gz

```[/SIZE][/SIZE][/SIZE] 
Now execute the driver package, this should take care of any missing dependencies but if it doesnt, refer to the logs and manually take care of the missing packages and then rerun the driver package:
```

:~/Downloads$ sudo ./RR272x_1x_Linux_Src_v1.5.18_15_04_21.bin 
[sudo] password for user: 
Verifying archive integrity... All good.
Uncompressing RR272x_1x Linux Open Source package  installer.......................................................................
Checking and installing required toolchain and utility ...
Found program make (/usr/bin/make)
Found program gcc (/usr/bin/gcc)
Found program perl (/usr/bin/perl)
Found program wget (/usr/bin/wget)
```[/SIZE]

[SIZE=3]That will install the drivers and the supported software. The new package comes with software that should automatically build new drivers as needed (for kernel updates), along with the generic drivers source. Here is the list of files and locations the package will install.[/SIZE]

```
_**Scripts**_
/etc/cron.daily/hptdrv-update
/etc/init.d/hptdrv-monitor
/usr/sbin/hptdrv-rebuild
/usr/share/hptdrv/hptdrv-function

_**Driver Source Files**_
/usr/share/rr272x_1x
```

[SIZE=3]Now that you have the driver source you can compile your own driver and insert it into the preOS base to add support for that kernel, that driver will then work for any machine with the same kernel version, it is not limited to the unique pc it was compiled on. All that is left now is to install the RAID Management Software.
[B]
[U][SIZE=4]Installing RAID Management Software
[/SIZE][/U][/B][SIZE=3]In the links section you will see the "Unpublished WebGUI and CLI" this is the version I use. I opened a support ticket with Highpoint when I ran into issues while installing WebGUI and it's init.d scripts on one of my headless servers, I had to make changes to the package and manually edit files in order for it to install and run properly. They then sent me this package to see if the issues had been resolved, needless to say that had been so I put it out there for others. I provided factory driver links to those paranoid few who think that I may have embedded some malicious code, but who's to say Highpoint hasn't burried some malicious code in the driver? ;) This version of the WebGUI lets you choose your sector size 512b/1K/2K/4K (I can not tell you if the other version have this feature, only know this one does).

[SIZE=3]Extract WebGUI package:
```
:$ tar -xzf WebGUI_Linux_v2.1.6.0.1_14_04_25.tgz
```[/SIZE][/SIZE]

Then install the .deb file (the second command will fix any outstanding package issues 99.9% of the time there will be none it's just a habbit of mine running the "-f" command after "dpkg"):
```
:$ sudo dpkg -i hptsvr_2.1.6_amd64.deb
:$ sudo apt-get -f install
```

After reboot you should have a file /etc/hptcfg if not run the following command and then reboot:

[SIZE=3]```
:$ sudo -s
:# echo rr27 > /etc/hptcfg 
```[/SIZE][/SIZE]

[SIZE=3]That's it, now you should be fully functional, all that is left to cover is manual driver building and most of you will have no use for it. [/SIZE]

[B][U][SIZE=4]Manual Driver Building
[/SIZE][/U][/B][SIZE=3]You can either download the source files from the links above or copy them from /usr/share/hptdrvrr272x_1x to another location to work on them. You shouldn't work on them from the /usr/share directory so you always have a clean copy of the source on your system. It's very simple, all you have to do is open terminal and navigate to .../rr272x_1x/product/rr272x/linux and run the following commands:
```
:$ sudo make
```
This will create a file named "rr272x_1x.ko" this is your driver file if you built this driver in order to add it to the preOS base pack right click the file, click compress, choose .gz extension NOT tar.gz then click create. Then just rename it using the following naming scheme, this is important so the preOS script knows what driver to use, rr272x_1x3.19.0-22-genericx86_64.ko.gz  If that is all you needed to do then you are done, if for some reason you need to also install the driver you just built then you do the following:
```
:$ sudo make install
```[/SIZE]
[SIZE=3][SIZE=3]This will return the source files to it's original state:
[/SIZE]```
:$ sudo make clean
```[/SIZE]
[SIZE=3]If you need to build a driver for a kernel that you have installed on your system but are not currently booted into you can use the following commands:
```
:$ sudo make KERNELDIR=/lib/modules/3.19.0-15-generic/build/
```
If you need to install it for that kernel also then you need to run:
```
:$ sudo make install KERNELDIR=/usr/src/linux-headers-3.19.0-22-generic
```

That's all you need to know about manual driver building. If you run into issues you can reach out to me on gtalk that's your best chance of reaching me, and ill do my  best to get back to you unfortunately I do not have as much free time as  I would like, but then again who does. Feel free to submit driver  versions not included in the links or any type of edits and I will  update the post and give credit where it is due.

Here is the manufacture support link that I rounded up the information and software from: [http://www.highpoint-tech.com/USA_new/product_support_sas6.htm](http://www.highpoint-tech.com/USA_new/product_support_sas6.htm)
[/SIZE]

---

### Post by wannesd on 2014-06-27
Hi,

Thank you for these drivers and bios.
I have a weird problem getting it to work actually:

The bios attached is v1.6, my card uses bios v4.0.0.1805, and is detected (even at POST) as Marvell 88SE9480.
Hence the bios flash in Dos refuses operation.

Secondly, building the driver doesn't work:
I go to the extracted directory cd rr272x-linux-src-v1.xx/product/rr272x/linux/When I do make install it finishes but with one error: 

```
wannes@server:/mnt/Torrent/product/rr272x/linux$ sudo make install
make[1]: Entering directory `/usr/src/linux-headers-3.13.0-30-generic'
  CC [M]  /mnt/Torrent/product/rr272x/linux/.build/os_linux.o
  CC [M]  /mnt/Torrent/product/rr272x/linux/.build/osm_linux.o
  CC [M]  /mnt/Torrent/product/rr272x/linux/.build/div64.o
  CC [M]  /mnt/Torrent/product/rr272x/linux/.build/hptinfo.o
  CC [M]  /mnt/Torrent/product/rr272x/linux/.build/config.o
  LD [M]  /mnt/Torrent/product/rr272x/linux/.build/rr272x_1x.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: could not find /mnt/Torrent/product/rr272x/linux/.build/.him_rr272x.o.cmd for /mnt/Torrent/product/rr272x/linux/.build/him_rr272x.o
  LD [M]  /mnt/Torrent/product/rr272x/linux/.build/rr272x_1x.ko
make[1]: Leaving directory `/usr/src/linux-headers-3.13.0-30-generic'
You made a module which is for current kernel 3.13.0-30-generic.
Deleting previous installed driver module rr272x_1x...
Install the new driver module...
Removing conflicted driver module...
Updating module dependencies...Done.
Checking for initrd images to be updated...



```

when I do "sudo modprobe rr272x_1x", it does not do anything until I cancel the operation.
Any idea what could be wrong?

---

### Post by JohnAreBee on 2014-06-28
*updated OP*

---

### Post by ted_bonar on 2014-08-22
Hi JohnAreBee,

I was glad when I found your post with instructions and downloads  because my rr2720sgl gives me headaches. I'm trying to install it in a  HP proliant microserver n54l. When running make I get this output:

~/Downloads/rr272x/rr272x_1x-linux-src-v1.6.1/product/rr272x/linux$ sudo make ARCH=x86_64
make[1]: Entering directory `/usr/src/linux-headers-3.13.0-34-generic'
  CC [M]  /Downloads/rr272x/rr272x_1x-linux-src-v1.6.1/product/rr272x/linux/.build/os_linux.o
  CC [M]  /Downloads/rr272x/rr272x_1x-linux-src-v1.6.1/product/rr272x/linux/.build/osm_linux.o
  CC [M]  /Downloads/rr272x/rr272x_1x-linux-src-v1.6.1/product/rr272x/linux/.build/div64.o
  CC [M]  /Downloads/rr272x/rr272x_1x-linux-src-v1.6.1/product/rr272x/linux/.build/hptinfo.o
  CC [M]  /Downloads/rr272x/rr272x_1x-linux-src-v1.6.1/product/rr272x/linux/.build/config.o
  LD [M]  /Downloads/rr272x/rr272x_1x-linux-src-v1.6.1/product/rr272x/linux/.build/rr272x_1x.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: could not find  /Downloads/rr272x/rr272x_1x-linux-src-v1.6.1/product/rr272x/linux/.build/.him_rr272x.o.cmd  for  /Downloads/rr272x/rr272x_1x-linux-src-v1.6.1/product/rr272x/linux/.build/him_rr272x.o
  CC      /Downloads/rr272x/rr272x_1x-linux-src-v1.6.1/product/rr272x/linux/.build/rr272x_1x.mod.o
  LD [M]  /Downloads/rr272x/rr272x_1x-linux-src-v1.6.1/product/rr272x/linux/.build/rr272x_1x.ko
make[1]: Leaving directory `/usr/src/linux-headers-3.13.0-34-generic'

 Following through with the instructions yields a kernel panic on reboot.

I would greatly appreciate your help. Tried multiple patches and older  drivers, followed the highpoint-instructions on  linux/debian-installation (the script failed).

Thanks in advance,

Ted

---

### Post by David_Moore on 2014-08-23
Question: Are there any spindown or powersave features that I can disable for the raid array drives?

sudo hdparm -C /dev/sda
/dev/sda:
 drive state is:  unknown

sudo hdparm -C /dev/sdb
/dev/sdb:
 drive state is:  active/idle

sda is my array. If it's showing unknown does that mean it doesn't go into powersave or spindown? I've been losing a lot of hard drives recently (all Seagates, rechecking the individual drives with SeaTools after the fact and finding bad sectors that can't be repaired) and I want to make sure it's not some spinup/spindown issue.

---

### Post by kxb on 2014-09-01
Thanks for posting! This also worked with my RocketRaid 2722 and Ubuntu 14.04. 

To be clear, I updated the bios, built the 1.6 module, and all worked.  Previously, I was on 1.5, and was stuck on an earlier kernel version until I could upgrade.

---

### Post by JohnAreBee on 2014-09-08
*updated OP*

---

### Post by JohnAreBee on 2014-09-08
*updated OP*

---

### Post by andriy-golovnya on 2014-09-19
Hi there!  I've tried to compile the driver on Ubuntu 14.04 (kernel 3.13?) to use it with my RocketRaid 2721. It was a partial success for me:  - No dkms integration made it really tricky to integrate to my running OS with periodic updates. It's not a tragic issue but a tip for developers.  - No RAID array (which was prepared in BIOS) has been available under Linux (but was fully accessible under Windows and Mac OSX).  - All HDDs in the system including these which are attached to main board SATA controller lost their SMART information. Tools like hddtemp and smartctl could not access any SMART information of any disk.  Any comments on my success, other results and notes? I would really like to know what success other people have with 2720, 2721 under Ubuntu 14.04.  What worries me too is the firmware and the driver v.1.6 were not publicly presented on an official website of the manufacture. Why? Beta? Unstable? Any comment on this?  Thanks in advance for your answers!  --AG

---

### Post by JohnAreBee on 2014-09-20
*updated OP*

---

### Post by andriy-golovnya on 2014-09-24
Ok, let me correct myself.

I'm trying to start a RAID5 array which is connected to RR 2721 (FW 1.5) on external port. This array perfectly runs under Windows, which a second OS on the same PC.
Because of dual boot and some another reasons some HDDs (not from array) are connected to main board controller - windows boot and linux boot HDDs.

I'm trying to run the array under ubuntu 14.04 x64 desktop with 3.13.0-35 kernel on Gigabyte EX58-UD5 BIOS F12.
I've set up a dkms configuration for the driver 1.6.1 and what I got is no RAID array, no SMART info. I've deinstalled the troublesome driver right after I got this results.

Do you have any ideas on this?

-- AG

---

### Post by wannesd on 2014-10-03
> **wannesd said:**
> Hi,

Thank you for these drivers and bios.
I have a weird problem getting it to work actually:

The bios attached is v1.6, my card uses bios v4.0.0.1805, and is detected (even at POST) as Marvell 88SE9480.
Hence the bios flash in Dos refuses operation.

Secondly, building the driver doesn't work:
I go to the extracted directory cd rr272x-linux-src-v1.xx/product/rr272x/linux/When I do make install it finishes but with one error: 

```
wannes@server:/mnt/Torrent/product/rr272x/linux$ sudo make install
make[1]: Entering directory `/usr/src/linux-headers-3.13.0-30-generic'
  CC [M]  /mnt/Torrent/product/rr272x/linux/.build/os_linux.o
  CC [M]  /mnt/Torrent/product/rr272x/linux/.build/osm_linux.o
  CC [M]  /mnt/Torrent/product/rr272x/linux/.build/div64.o
  CC [M]  /mnt/Torrent/product/rr272x/linux/.build/hptinfo.o
  CC [M]  /mnt/Torrent/product/rr272x/linux/.build/config.o
  LD [M]  /mnt/Torrent/product/rr272x/linux/.build/rr272x_1x.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: could not find /mnt/Torrent/product/rr272x/linux/.build/.him_rr272x.o.cmd for /mnt/Torrent/product/rr272x/linux/.build/him_rr272x.o
  LD [M]  /mnt/Torrent/product/rr272x/linux/.build/rr272x_1x.ko
make[1]: Leaving directory `/usr/src/linux-headers-3.13.0-30-generic'
You made a module which is for current kernel 3.13.0-30-generic.
Deleting previous installed driver module rr272x_1x...
Install the new driver module...
Removing conflicted driver module...
Updating module dependencies...Done.
Checking for initrd images to be updated...



```

when I do "sudo modprobe rr272x_1x", it does not do anything until I cancel the operation.
Any idea what could be wrong?


So I figured out some time ago where I went wrong:
My card is a rocket 2720SGL (not a rocketRAID)

I just threw windows server on the machine instead, and all is well and stable.
However, I really want to go back to Ubuntu Server instead, so I'm giving this another go.

Here is the support page for my specific card: [http://www.highpoint-tech.com/USA_new/PCI-E_r_2_0_x8_Configuration.html](http://www.highpoint-tech.com/USA_new/PCI-E_r_2_0_x8_Configuration.html)
I just can't seem to get it running under ubuntu, the readme file doesnt make sense to a newbie like me at all...

If you could help me out at all, it would really be great!

This is the log when simply running make:

```
a@a-virtual-machine:~/Downloads$ cd linux_4.0.0.1528N_source/
a@a-virtual-machine:~/Downloads/linux_4.0.0.1528N_source$ cd partial/
a@a-virtual-machine:~/Downloads/linux_4.0.0.1528N_source/partial$ sudo make
make ARCH=x86_64 CC=cc LD=ld CROSS_COMPILE= V= -C /lib/modules/3.13.0-24-generic/build SUBDIRS=`pwd` modules
make[1]: Entering directory `/usr/src/linux-headers-3.13.0-24-generic'
  CC [M]  /home/a/Downloads/linux_4.0.0.1528N_source/partial/linux_main.o
In file included from /home/a/Downloads/linux_4.0.0.1528N_source/partial/hba_header.h:4:0,
                 from /home/a/Downloads/linux_4.0.0.1528N_source/partial/linux_main.h:4,
                 from /home/a/Downloads/linux_4.0.0.1528N_source/partial/linux_main.c:8:
/home/a/Downloads/linux_4.0.0.1528N_source/partial/mv_os.h:9:29: fatal error: linux/config.h: No such file or directory
 #   include <linux/config.h>
                             ^
compilation terminated.
make[2]: *** [/home/a/Downloads/linux_4.0.0.1528N_source/partial/linux_main.o] Error 1
make[1]: *** [_module_/home/a/Downloads/linux_4.0.0.1528N_source/partial] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.13.0-24-generic'
make: *** [all] Error 2


```

---

### Post by camper2 on 2014-10-06
I've made a patch for the rocket 2720SGL that fixes the compilation errors (compiled against 3.17.0 kernel). The driver is structured a bit differently and given that don't have the card I have no way to test, so most likely it won't work.
[ATTACH]256986[/ATTACH]

---

### Post by wannesd on 2014-10-06
Hey man,

thanks for taking the time to help me out!

Now, the archive contains 1 .diff file, how do I go forward from there? No such file in the original archive to overwrite...

---

### Post by camper2 on 2014-10-06
use patch. i.e., assuming you put the .diff file into the same directory as the source (~/Downloads/linux_4.0.0.1528N_source/partial):

cd ~/Downloads/linux_4.0.0.1528N_source/partial
patch -p1 <linux_4.0.0.1528N.diff
sudo make

---

### Post by wannesd on 2014-10-09
This is the result:

```
a@a-virtual-machine:~$ cd ~/Downloads/linux_4.0.0.1528N_source/partial
a@a-virtual-machine:~/Downloads/linux_4.0.0.1528N_source/partial$ patch -p1 <linux_4.0.0.1528N.diff
patching file linux_iface.c
patching file linux_iface.h
patching file linux_main.c
patching file mv_os.c
patching file mv_os.h
a@a-virtual-machine:~/Downloads/linux_4.0.0.1528N_source/partial$ sudo make
[sudo] password for a: 
make ARCH=x86_64 CC=cc LD=ld CROSS_COMPILE= V= -C /lib/modules/3.13.0-24-generic/build SUBDIRS=`pwd` modules
make[1]: Entering directory `/usr/src/linux-headers-3.13.0-24-generic'
  CC [M]  /home/a/Downloads/linux_4.0.0.1528N_source/partial/linux_main.o
/home/a/Downloads/linux_4.0.0.1528N_source/partial/linux_main.c: In function ‘scsi_cmd_to_req_conv’:
/home/a/Downloads/linux_4.0.0.1528N_source/partial/linux_main.c:909:24: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
  pReq->Device_Id     = (u32)scmd->device->hostdata;
                        ^
/home/a/Downloads/linux_4.0.0.1528N_source/partial/linux_main.c: In function ‘mv_scsi_slave_alloc’:
/home/a/Downloads/linux_4.0.0.1528N_source/partial/linux_main.c:1573:19: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
  sdev->hostdata = (void *)base_id;
                   ^
/home/a/Downloads/linux_4.0.0.1528N_source/partial/linux_main.c: At top level:
/home/a/Downloads/linux_4.0.0.1528N_source/partial/linux_main.c:1811:2: warning: initialization from incompatible pointer type [enabled by default]
  .change_queue_depth = mv_change_queue_depth,
  ^
/home/a/Downloads/linux_4.0.0.1528N_source/partial/linux_main.c:1811:2: warning: (near initialization for ‘mv_driver_template.change_queue_depth’) [enabled by default]
  CC [M]  /home/a/Downloads/linux_4.0.0.1528N_source/partial/hba_exp.o
  CC [M]  /home/a/Downloads/linux_4.0.0.1528N_source/partial/hba_mod.o
  CC [M]  /home/a/Downloads/linux_4.0.0.1528N_source/partial/hba_timer.o
  CC [M]  /home/a/Downloads/linux_4.0.0.1528N_source/partial/mv_os.o
  CC [M]  /home/a/Downloads/linux_4.0.0.1528N_source/partial/linux_iface.o
  LD [M]  /home/a/Downloads/linux_4.0.0.1528N_source/partial/mv94xx.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: could not find /home/a/Downloads/linux_4.0.0.1528N_source/partial/lib/.libmv_nonraid_64.obj.cmd for /home/a/Downloads/linux_4.0.0.1528N_source/partial/lib/libmv_nonraid_64.obj
  CC      /home/a/Downloads/linux_4.0.0.1528N_source/partial/mv94xx.mod.o
  LD [M]  /home/a/Downloads/linux_4.0.0.1528N_source/partial/mv94xx.ko
make[1]: Leaving directory `/usr/src/linux-headers-3.13.0-24-generic'


```

Why can't highpoint just make drivers that work under linux? The windoze ones work perfectly...

---

### Post by camper2 on 2014-10-09
so the driver has been built, now you just have to load it as written in the readme, i.e insmod m94xx.ko

---

### Post by David_Troendle on 2015-01-14
Followed your instructions for 14.10 and they worked great.  Thanks.  The latest Unbuntu update brings the kernel from 3.16.0-**_28_**-generic to 3.16.0-_**29**_-generic.

When I rebuild using the new kernel headers I get a driver for the old kernel.  Could you point me in the right direction to fix this?

Thanks.

David
[HR][/HR]
Execution transcript follows:

```
make[1]: Entering directory '/usr/src/linux-headers-3.16.0-29-generic'
  CC [M]  /home/david/OleMiss/Software/RocketRaid/rr272x_1x-linux-src-v1.6.1-edited/product/rr272x/linux/.build/os_linux.o
  CC [M]  /home/david/OleMiss/Software/RocketRaid/rr272x_1x-linux-src-v1.6.1-edited/product/rr272x/linux/.build/osm_linux.o
  CC [M]  /home/david/OleMiss/Software/RocketRaid/rr272x_1x-linux-src-v1.6.1-edited/product/rr272x/linux/.build/div64.o
  CC [M]  /home/david/OleMiss/Software/RocketRaid/rr272x_1x-linux-src-v1.6.1-edited/product/rr272x/linux/.build/hptinfo.o
  CC [M]  /home/david/OleMiss/Software/RocketRaid/rr272x_1x-linux-src-v1.6.1-edited/product/rr272x/linux/.build/config.o
  LD [M]  /home/david/OleMiss/Software/RocketRaid/rr272x_1x-linux-src-v1.6.1-edited/product/rr272x/linux/.build/rr272x_1x.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: could not find /home/david/OleMiss/Software/RocketRaid/rr272x_1x-linux-src-v1.6.1-edited/product/rr272x/linux/.build/.him_rr272x.o.cmd for /home/david/OleMiss/Software/RocketRaid/rr272x_1x-linux-src-v1.6.1-edited/product/rr272x/linux/.build/him_rr272x.o
  LD [M]  /home/david/OleMiss/Software/RocketRaid/rr272x_1x-linux-src-v1.6.1-edited/product/rr272x/linux/.build/rr272x_1x.ko
make[1]: Leaving directory '/usr/src/linux-headers-3.16.0-29-generic'
make[1]: Entering directory '/usr/src/linux-headers-3.16.0-29-generic'
  CC [M]  /home/david/OleMiss/Software/RocketRaid/rr272x_1x-linux-src-v1.6.1-edited/product/rr272x/linux/.build/os_linux.o
  CC [M]  /home/david/OleMiss/Software/RocketRaid/rr272x_1x-linux-src-v1.6.1-edited/product/rr272x/linux/.build/osm_linux.o
  CC [M]  /home/david/OleMiss/Software/RocketRaid/rr272x_1x-linux-src-v1.6.1-edited/product/rr272x/linux/.build/div64.o
  CC [M]  /home/david/OleMiss/Software/RocketRaid/rr272x_1x-linux-src-v1.6.1-edited/product/rr272x/linux/.build/hptinfo.o
  CC [M]  /home/david/OleMiss/Software/RocketRaid/rr272x_1x-linux-src-v1.6.1-edited/product/rr272x/linux/.build/config.o
  LD [M]  /home/david/OleMiss/Software/RocketRaid/rr272x_1x-linux-src-v1.6.1-edited/product/rr272x/linux/.build/rr272x_1x.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: could not find /home/david/OleMiss/Software/RocketRaid/rr272x_1x-linux-src-v1.6.1-edited/product/rr272x/linux/.build/.him_rr272x.o.cmd for /home/david/OleMiss/Software/RocketRaid/rr272x_1x-linux-src-v1.6.1-edited/product/rr272x/linux/.build/him_rr272x.o
  LD [M]  /home/david/OleMiss/Software/RocketRaid/rr272x_1x-linux-src-v1.6.1-edited/product/rr272x/linux/.build/rr272x_1x.ko
make[1]: Leaving directory '/usr/src/linux-headers-3.16.0-29-generic'
You made a module for 3.16.0-28-generic which does not match current kernel.
The driver will be installed for kernel 3.16.0-28-generic.
Deleting previous installed driver module rr272x_1x...
Install the new driver module...
Removing conflicted driver module...
Updating module dependencies...Done.
Checking for initrd images to be updated...
```

---

### Post by JohnAreBee on 2015-03-06
*updated OP*

---

### Post by Jody_Ledoux on 2015-03-08
hi,

I got a RocketRAID 2720SGL to attempt to install into my Ubuntu 14.10 server (GNU/Linux 3.16.0-31-generic x86_64). I followed the instructions that you provided to the best of my ability. However it doesn't work properly so clearly i did something wrong. I used the files you provided for 14.10 my web gui works however it can't see any of the drives i have connected to the card below is a screenshot of the gui.

I've connected this card to a windows machine with a couple of drives and found that it works perfectly in that environment so i don't believe that this is a hardware issue, clearly i messed up something with the drivers in ubuntu. I did notice on the windows installation the controller came up as 272x_1x when in ubuntu it comes up as 2070.

Can you help?

[ATTACH=CONFIG]260530[/ATTACH]


When i run make this is the output.

```
make[1]: Entering directory '/usr/src/linux-headers-3.16.0-31-generic'
  CC [M]  /home/nighthawke/RAID/rr272x_1x-linux-src-v1.6.1-edited/product/rr272x/linux/.build/os_linux.o
  CC [M]  /home/nighthawke/RAID/rr272x_1x-linux-src-v1.6.1-edited/product/rr272x/linux/.build/osm_linux.o
  CC [M]  /home/nighthawke/RAID/rr272x_1x-linux-src-v1.6.1-edited/product/rr272x/linux/.build/div64.o
  CC [M]  /home/nighthawke/RAID/rr272x_1x-linux-src-v1.6.1-edited/product/rr272x/linux/.build/hptinfo.o
  CC [M]  /home/nighthawke/RAID/rr272x_1x-linux-src-v1.6.1-edited/product/rr272x/linux/.build/config.o
  LD [M]  /home/nighthawke/RAID/rr272x_1x-linux-src-v1.6.1-edited/product/rr272x/linux/.build/rr272x_1x.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: could not find /home/nighthawke/RAID/rr272x_1x-linux-src-v1.6.1-edited/product/rr272x/linux/.build/.him_rr272x.o.cmd for /home/nighthawke/RAID/rr272x_1x-linux-src-v1.6.1-edited/product/rr272x/linux/.build/him_rr272x.o
  LD [M]  /home/nighthawke/RAID/rr272x_1x-linux-src-v1.6.1-edited/product/rr272x/linux/.build/rr272x_1x.ko
make[1]: Leaving directory '/usr/src/linux-headers-3.16.0-31-generic'
```

When i run make install

```
make[1]: Entering directory '/usr/src/linux-headers-3.16.0-31-generic'
  CC [M]  /home/nighthawke/RAID/rr272x_1x-linux-src-v1.6.1-edited/product/rr272x/linux/.build/os_linux.o
  CC [M]  /home/nighthawke/RAID/rr272x_1x-linux-src-v1.6.1-edited/product/rr272x/linux/.build/osm_linux.o
  CC [M]  /home/nighthawke/RAID/rr272x_1x-linux-src-v1.6.1-edited/product/rr272x/linux/.build/div64.o
  CC [M]  /home/nighthawke/RAID/rr272x_1x-linux-src-v1.6.1-edited/product/rr272x/linux/.build/hptinfo.o
  CC [M]  /home/nighthawke/RAID/rr272x_1x-linux-src-v1.6.1-edited/product/rr272x/linux/.build/config.o
  LD [M]  /home/nighthawke/RAID/rr272x_1x-linux-src-v1.6.1-edited/product/rr272x/linux/.build/rr272x_1x.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: could not find /home/nighthawke/RAID/rr272x_1x-linux-src-v1.6.1-edited/product/rr272x/linux/.build/.him_rr272x.o.cmd for /home/nighthawke/RAID/rr272x_1x-linux-src-v1.6.1-edited/product/rr272x/linux/.build/him_rr272x.o
  LD [M]  /home/nighthawke/RAID/rr272x_1x-linux-src-v1.6.1-edited/product/rr272x/linux/.build/rr272x_1x.ko
make[1]: Leaving directory '/usr/src/linux-headers-3.16.0-31-generic'
You made a module which is for current kernel 3.16.0-31-generic.
Deleting previous installed driver module rr272x_1x...
Install the new driver module...
Removing conflicted driver module...
Updating module dependencies...Done.
Checking for initrd images to be updated...
```

---

### Post by JohnAreBee on 2015-03-13
*updated OP*

---

### Post by craaaft on 2016-02-10
Could someone reupload the kernel driver package?

---

### Post by wsv2 on 2016-09-09
For those looking to solve for 16.04, the drivers prior to [RR272x_1x_Linux_Src_v1.5.24.1_16_09_02]("http://www.highpoint-tech.com/websupport/portal/download.php?id=15795") have an issue with the install script where the mvsas driver is not disabled, and therefore there is a clash with the rr272x_1x driver. Highpoint support have issued me a binary for [RR272x_1x_Linux_Src_v1.5.24.1_16_09_02]("http://www.highpoint-tech.com/websupport/portal/download.php?id=15795"), which does not have the issue.

They also (very kindly) gave me a management client binary that they say does CLI and GUI (i have only tried the CLI) - [COLOR=#000000][FONT=Tahoma]RAID_Manage_Linux_2.6.3_16_04_27[/FONT][/COLOR]. I am not sure if/when they will update their support site to provide this, but in the meantime you can unofficially take a copy here:
[https://www.dropbox.com/s/w4dhptkrnav4pu0/RAID_Manage_Linux_v2.3.6_16_04_27.tgz?dl=0](https://www.dropbox.com/s/w4dhptkrnav4pu0/RAID_Manage_Linux_v2.3.6_16_04_27.tgz?dl=0)[COLOR=#000000][FONT=Tahoma]

Of course I recommend checking the official support page just in case there are newer and/or official versions.[/FONT][/COLOR]

---

### Post by David_Moore on 2016-09-09
> **wsv2 said:**
> For those looking to solve for 16.04, the drivers prior to [RR272x_1x_Linux_Src_v1.5.24.1_16_09_02]("http://www.highpoint-tech.com/websupport/portal/download.php?id=15795") have an issue with the install script where the mvsas driver is not disabled, and therefore there is a clash with the rr272x_1x driver. Highpoint support have issued me a binary for [RR272x_1x_Linux_Src_v1.5.24.1_16_09_02]("http://www.highpoint-tech.com/websupport/portal/download.php?id=15795"), which does not have the issue.

They also (very kindly) gave me a management client binary that they say does CLI and GUI (i have only tried the CLI) - [COLOR=#000000][FONT=Tahoma]RAID_Manage_Linux_2.6.3_16_04_27[/FONT][/COLOR]. I am not sure if/when they will update their support site to provide this, but in the meantime you can unofficially take a copy here:
[https://www.dropbox.com/s/w4dhptkrnav4pu0/RAID_Manage_Linux_v2.3.6_16_04_27.tgz?dl=0](https://www.dropbox.com/s/w4dhptkrnav4pu0/RAID_Manage_Linux_v2.3.6_16_04_27.tgz?dl=0)[COLOR=#000000][FONT=Tahoma]

Of course I recommend checking the official support page just in case there are newer and/or official versions.[/FONT][/COLOR]

I didn't have any issues with 16.04 other than having to reinstall the drivers again. I was using RR272x_1x_Linux_Src_v1.5.18_15_04_21.bin. I was also able to continue using the WebUI version  hptsvr_2.2.1_amd64.deb, but attempts to upgrade to RAID_Manage_Linux_2.3.1_14_10_20.bin were failing.

I upgraded to the newer WebUI that you provided already without any issues. I'll install the new card drivers during my next maintenance.

Thank you for providing these newer drivers. (Why don't they just put them on their website??)

---

