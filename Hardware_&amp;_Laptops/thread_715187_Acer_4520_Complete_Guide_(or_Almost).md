---
title: "Acer 4520 Complete Guide (or Almost)"
date: 2008-03-04
forum: Hardware &amp; Laptops
---

### Post by felipefoz on 2008-03-04
This guide is intended to users from an Acer 4520, some variants of this model may work with the tips here, some may not.
I am writing this post from the installation until the setup of all hardware, or almost all hardware, since there are some things that we were not able to setup yet. 
The intention is to keep upgrading the content of this post with tips from community.
The distribution used is the Ubuntu 7.10 32 Bits, and only this one, the 7.04, or 8.04, or any other may be different and the tips here may work or not. 
I decided to install the 32 Bits version, 'cause I have to do so many workarounds in this version, that I can't have time enough to do the same in the 64 bits, plus another issues that the 64 bits version has. So I keep the 32 bits, although the tips here and many steps can be followed by 64 bits users.
Note: 64 Bits user look at this post from "afterstep13" [http://ubuntuforums.org/showpost.php?p=4462539&postcount=5]("http://ubuntuforums.org/showpost.php?p=4462539&postcount=5")
I assume you have  wired internet available, because to set up the wireless Internet we need it. I also believe you have a little bit of knowledge in Linux, not all the things are very well explained, my fault. BTW. As  it is the first guide, I accept suggestions, and don't worry about my English, it's not my first language.

My Hardware Specs:
Acer 4520 - 5726 -  AMD Turion 64 X2 Mobile TL-58 (1.9 Ghz, 2 x 512 L2 Cache)
Chipset Nvidia Nforce 610M
VGA - Nvidia GeForce 7000M - 14" WXGA+ WideScreen 1280x800
2GB DDR2 667 - 160 GB HDD - DVD-RW
Atheros AR5007EG 802.11b/g WLAN
Card Reader- Express Card Slot
S-Video e Monitor OUT
4 USB 2.0 - 1 Mini-Firewire (4 Pinos)
```
$lspci
00:00.0 RAM memory: nVidia Corporation Unknown device 0547 (rev a2)
00:01.0 ISA bridge: nVidia Corporation Unknown device 0548 (rev a2)
00:01.1 SMBus: nVidia Corporation Unknown device 0542 (rev a2)
00:01.2 RAM memory: nVidia Corporation Unknown device 0541 (rev a2)
00:01.3 Co-processor: nVidia Corporation Unknown device 0543 (rev a2)
00:02.0 USB Controller: nVidia Corporation Unknown device 055e (rev a2)
00:02.1 USB Controller: nVidia Corporation Unknown device 055f (rev a2)
00:04.0 USB Controller: nVidia Corporation Unknown device 055e (rev a2)
00:04.1 USB Controller: nVidia Corporation Unknown device 055f (rev a2)
00:06.0 IDE interface: nVidia Corporation Unknown device 0560 (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation Unknown device 0561 (rev a2)
00:09.0 SATA controller: nVidia Corporation Unknown device 0555 (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation Unknown device 054c (rev a2)
00:0c.0 PCI bridge: nVidia Corporation Unknown device 0563 (rev a2)
00:0e.0 PCI bridge: nVidia Corporation Unknown device 0563 (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation Unknown device 0533 (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
01:09.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
01:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
01:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
01:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
07:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)

```
So let's start:

**1) The BIOS Setup configuration**

- Get to the BIOS, make sure you're using the AHCI mode in "Sata Mode" and put the CDROM as primary boot device.

**2) Booting the Live-CD**

- After choosing the language, if needed, choose "Start Ubuntu in safe graphics mode". And wait until gnome is loaded.

[B]3) Normal Installation
[/B]
- Do a normal installation, the problems will start happening later. Make sure your swap size is as big as your RAM size, otherwise you won't be able to hibernate sometimes.
[B]
4) Rebooting[/B]

- Here comes the problem, the system won't boot, so here are the steps:

In GRUB menu select the appropriate line, press "e" to edit the options, select the second line, the one beginning with "kernel" and append the "break=top" to the end, after editing press "enter" and then "b" to boot. After few seconds you'll fall into a shell frame, with "initramfs" written and a blinking cursor. Then type the following:

```
<initramfs> modprobe sata_nv
<initramfs> modprobe ata_generic
<initramfs> exit
```
You'll boot normally after this. Some people typed to load other modules, but with these combination I got 100% of success.

**5) Fix the boot issue **

First thing is fixing the issue, there were many workarounds about this problem, the plausible solution was found in this thread [http://ubuntuforums.org/showpost.php?p=4394099&postcount=131]("http://ubuntuforums.org/showpost.php?p=4394099&postcount=131") (thanks to "afterstep13"):
Still in gnome, with a low resolution, don't worry we'll fix the vga problem soon, create a script:
```
$ sudo gedit /etc/initramfs-tools/scripts/init-premount/fix 
```
Add the following lines to its content:
```
#!/bin/sh

PREREQ=""
prereqs()
{
echo "$PREREQ"
}
case $1 in
# get pre-requisites
prereqs)
prereqs
exit 0
;;
esac
sleep 10
```
Then make it executable with:
```
$ sudo chmod +x /etc/initramfs-tools/scripts/init-premount/fix 
```
Update the initramfs:
```
$ sudo update-initramfs -u
```
Reboot, now it's going to boot normally, this script make a ten seconds delay, so it'll take 10 seconds before starting the boot process, anyhow it works very well, better waiting 10 seconds, than typing every time the commands from last step. Some tweaks make the boot process real faster in dual core processors, write about this later.

**6) Wired LAN**

Works out of the box*.
Incrementing eth# problem, look at this tip in this same thread  [http://ubuntuforums.org/showpost.php?p=4462539&postcount=5]("http://ubuntuforums.org/showpost.php?p=4462539&postcount=5")

**7) Updates**

Active the repositories needed, and update all the software, before tweaking the system. Updates may break some tweaks. This is a very important step. After updating, reboot.

**8 ) Sound - High Definition Audio** 

You might be asking yourselves, why installing sound before video. I don't know why, but installing sound after the video may break nvida installation. ???? . So let's do the sound before the video. The solution is simple, downloading latest alsa drivers and compiling them. "Question: I've seen an alternative solution with ubuntu's "linux-backport-modules", isn't easier?". Actually, that solution is pretty quicker than this one, but with that one, the microphone was not working with me, so I compiled it myself.
This tip  I got partially from [https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto"). And also from another thread here in forums [http://ubuntuforums.org/showthread.php?t=577699]("http://ubuntuforums.org/showthread.php?t=577699")
I am passing all the process here, but at the end I have made some modifications in the script from this post [http://ubuntuforums.org/showpost.php?p=3603812&postcount=13]("http://ubuntuforums.org/showpost.php?p=3603812&postcount=13"), and you may want to download to automate the process. Then you should run these steps.
```
sudo sh alsa_1.sh
reboot
sudo sh alsa_2.sh
reboot
```
Sound should be working, I used this script and worked very well. 
Otherwise you may want to do it manually. With the following steps.

Install dependencies:
```
 apt-get install build-essential libncurses5-dev gettext linux-headers-`uname -r`
```
Alsa Driver, Lib and Utils:
```
wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.16.tar.bz2
wget ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.16.tar.bz2
wget ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.16.tar.bz2
```

Extracting them and removing tarballs:
```
tar -xjf alsa-driver*.tar.bz2
tar -xjf alsa-lib*.tar.bz2
tar -xjf alsa-utils*.tar.bz2
rm alsa*.tar.bz2
```
Making the directory for compiling the source:
```
sudo mkdir -p /usr/src/alsa
sudo mv alsa-* /usr/src/alsa
```
Compiling and installing alsa-driver
```
cd /usr/src/alsa/alsa-driver*
sudo ./configure --with-cards=hda-intel
sudo make
sudo make install
```
Compiling and installing alsa-libs
```
 cd /usr/src/alsa/alsa-lib*
sudo ./configure
sudo make
sudo make install
```
Compiling and installing alsa-utils
```
cd /usr/src/alsa/alsa-utils*
sudo ./configure
sudo make
sudo make install
```
Reboot the machine and run more these comands:
```
sudo cp -v /lib/modules/2.6.22-*/kernel/sound/pci/hda/snd-hda-intel.ko /lib/modules/2.6.22-*/ubuntu/media/snd-hda-intel/snd-hda-intel.ko
sudo cp -v /usr/src/alsa/alsa-driver*/modules/* /lib/modules/2.6.22-*/kernel/sound/
sudo depmod -a
```
Reboot once more. And the next time will have sound working, no extra tweaks needed, like adding some line to /etc/modprobe.d/alsa-base. The steps above must solve the problem with sound and mic. The mic will work after enabling all boxes in the Gnome mixer applet. Change the input source to "front mic" or "mic" depending on which microphone you are gonna use. That's it.

**9) Wireless LAN - Atheros AR5007EG**

Tried already the madwifi drivers, and ndiswrapper. After tested both of them, the one which best worked with me was the ndiswrapper compiled from source.
a) Download and compile ndiswrapper 1.52
```
wget http://superb-west.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.52.tar.gz
tar -zxvf ndiswrapper-1.5*
sudo mkdir -p /usr/src/ndiswrapper
sudo mv ndiswrapper-1.52/ /usr/src/ndiswrapper/
cd /usr/src/ndiswrapper/ndiswrapper-1.52/
sudo make uninstall
sudo make
sudo make install
```
b) Blacklist the native ath_pci module to prevent from loading it. 
```
sudo gedit /etc/modprobe.d/blacklist
```
Add the line:
```
blacklist ath_pci
```

c) Download the xp driver from [Atheros Site]("http://www.atheros.cz/download.php?atheros=AR5008"), look for the driver 6.0.3.85 for Windows XP 32 Bits, the file name will be xp32-6.0.3.85.zip. The file inside must be net5416.inf (not net5211.inf).

Extract and install it:
```
unzip xp32-6.0.3.85.zip
sudo ndiswrapper -i net5416.inf
sudo ndiswrapper -l
sudo ndiswrapper -m
sudo ndiswrapper -ma
sudo loadndisdriver
sudo modprobe ndiswrapper
```
It must be working now with the led, if it doesn't, make sure it isn't off, or try a reboot.

d) Fixing the LED Problem

Wireless in Linux, it's never perfect. After comparing some .inf files, and many hit and tries. I've found a solution for the LED that's always on. The solution is quite simple, but it is necessary some attention in which files we should edit. First
Find which device is listed in ndiswrapper:
```
$ndiswrapper -l
net5416 : driver installed
        device (168C:001C) present (alternate driver: ath_pci)
```
Mine device is listed on "168C:001C". The you go to /etc/ndiswrapper/net5416/, look for the files that begin with the exactly name of your device. You should edit a file with the name "XXXX:XXXX.5.conf". In my case, was:
```
sudo nano /etc/ndiswrapper/net5416/168C\:001C.5.conf
```
The beggining of the file content should be like this:
```
sys_files|ar5416.sys 
NdisVersion|0x50001
Environment|1
class_guid|4d36e972-e325-11ce-bfc1-08002be10318
driver_version|,06/05/2007,6.0.3.85
BusType|5
SlotNumber|01
NetCfgInstanceId|{28022A01-1234-5678-ABCDE-123813291A00}

abolt|191
capLinkSp|1
DriverDesc|NDIS Network Adapter
gpioPinFunc1|3
ignore11dBeacon|1 
...
```
Right below the line "gpioPinFunc1|3", you add the line:
```
gpioLedCustom|4
```
Unload and load ndiswrapper:
```
sudo modprobe -r ndiswrapper
sudo modprobe ndiswrapper
```
Now your LED will act different, will blink each 5 seconds, and always on when connected, you can change de values, instead of 4, I tried 1,2,3 and I got different results in how the LED acts. You can test different values and see which one you will like the most. I'm in doubt in 3 or 4. hehehe

**10) VGA - Nvidia**

Finally installing the Graphics Card, I let it almost for last, because I don't know why but this driver is very sensitive to system changes, I tried to install at first, but installed the sound, messed nvidia, installed wireless, messed nvidia, so I let it for last. I found a better solution compiling the latest drivers from the Nvidia Website, just because the built-in driver "nvidia-glx-new" doesn't hibernate, no matter what you do. Some may want to install it using envy, your choice, but I read that it doesn't work very well. So I'm gonna do it myself:

a) Downloading the latest driver from [Nvidia website]("http://www.nvidia.com/object/unix.html"). The latest IA32 version, not the legacy ones. Save all your job you're doing at the moment (we are going to stop Gdm). Go for a tty1 by pressing "Ctrl+Alt+F1". Login and type:
```
sudo /etc/init.d/gdm stop
```
Go to place you donwloaded the Nvidia drivers and run the executable:
```
sudo sh NVIDIA-Linux-x86-*
```
Say yes to all questions and restart the computer.

b) After restarting you'll still get the low resolution, so edit the xorg.conf and manually change the resolution.
```
 sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo gedit /etc/X11/xorg.conf
```

Then change the resolution line in the "Section "Screen"":
It was:
```
        Modes      "800x600"
```
And change to
```
         Modes      "1280x800"
```
I also disabled the logo feature by adding to this same section the line:
```
Option "NoLogo" "true"
```

There has been some problem happening to users, that the title bars keep disappearing.
The fix is adding the following line to the Device Section also in xorg.conf
```
Option “AddARGBGLXVisuals” “True”
```

So, restart X (Ctrl+Alt+Backspace) and that's it. Your pretty gnome again. Troubles: [NvidiaManual]("https://help.ubuntu.com/community/NvidiaManual")

**11) Touchpad**
It works out of the box, but you can tweak a little bit.

a) Backing up and editing xorg.conf:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup2
sudo gedit /etc/X11/xorg.conf
```
Adding the line (Option "SHMConfig" "true") to Synaptics InputDevice Section, the whole section should look like this:
```
 Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizEdgeScroll" "0"
    **Option         "SHMConfig" "true"	**
EndSection
```

b) Installing the Gsynaptics to manage preferences for touchpad. Available in "System > Preferences > Touchpad"
```
sudo aptitude install gsynaptics
```

c) Disabling touchpad while typing:
Put the command below in the start session of gnome, under "System > Preferences > Sessions > Add"
```
syndaemon -i 1 -d
```
**12) Webcam**
Works out of the box. Program to manage ```
sudo aptitude install cheese
```

**13) Card Reader**
Not fully functional. I couldn't test all kind of cards. But Memory Stick doesn't work. I've read SD cards only work. You may want to check this project at [BerliOS]("http://openfacts.berlios.de/index-en.phtml?title=TI%20FlashMedia%20xx12%2Fxx21%20driver")

**14) Hibernate (Suspend to disk) and Standby (Suspend to RAM)**
Should Work out of the box with latest Nvidia Drivers .Although hibernate fails sometimes. I tried with the VESA driver, it worked always. Nvidia driver problems.
So after googling a little bit, I found out about that option from xorg.conf, NvAgp, and it has many alternatives.
I added to xorg.conf in device section the following line, it's supposed to turn off agp support, nothing happened to my video anyway, but now hibernate works 90% of the times, the other 10% no reason.
The line:
```
Option "NvAgp" "0"
```
now, when I resume from hibernate, the sound stops working, "working on it" :P
Suspends works with no problems.

**15) S-Video and VGA Out**
Both work perfectly with the Nvidia X Server Settings under "Application > System Tools > Nvidia X Server Settings). It's very easy to set up different displays. Detection works fine as well.

**16) Dial-up Modem, Express Card and mini-firewire**
None of them tested, anyone?

**13)ACPI, Battery, Laptop Health and others**

a) Install Powertop, a program to monitore the consumption from your laptop, should be ran with sudo
```
sudo aptitude install powertop
```
b)Decrease disk acess, and as consequence usage of battery. Two ways of doing it, you can use both, one of them or none, since the are problems for some people using them, read where this information was taken, all the discussion here [http://ubuntuforums.org/showthread.php?t=107856]("http://ubuntuforums.org/showthread.php?t=107856")
Changin the journal type to data=writeback (only ext3). [COLOR="Red"]**this change the type of your filesystem journal, read more about it before doing this tweak**[/COLOR]
- Edit GRUB menu:
```
sudo gedit /boot/grub/menu.lst
```
Find the entry from Ubuntu, and append "rootflags=data=writeback" at the end. Then the end of the line should look like this:
```
kernel /boot/... ro quiet splash rootflags=data=writeback[code]
- Edit fstab
[code]sudo gedit /etc/fstab
```
Append the data=writeback to the end of the line of your ext3 filesystem. Looking like this:
```
... /  ext3    defaults,errors=remount-ro,data=writeback
- Change the journal type:
[code]sudo tune2fs -o journal_data_writeback /dev/sdaX
```
Where X is the number of your ext3 partition.
- Check if everything is ok.
```
sudo tune2fs -l /dev/sdaX
```
c) Change to noatime, it makes system stop updating the access time every time a file is accessed [COLOR="Red"] Warning: some programs may utilize this feature, it will improve the system speed but you may have side effects, read more about it before doing this tweak[/COLOR]
- Edit fstab
```
sudo gedit /etc/fstab
```
Append notime to the ext3 partitions options:
```
... /  ext3    defaults,errors=remount-ro,noatime,data=writeback
```
d) Deacrese the interrupts from nvidia, see powertop before and after doing this, seek for nvidia, after doing this will disappear or will be at the bottom. (Experimental Power Saving Mode)
- Edit xorg.conf
```
sudo gedit /etc/X11/xorg.conf
```
- Add the line to the Device Section or the Screen Section, depending on your configuration:
```
Option "OnDemandVBlankInterrupts" "on"
```
e) Increase the Boot Speed by starting services in parallell mode. I haven't forgot what I promessed, after the 10 seconds delay you will have a faster boot after this tip, very noticeable with the dual core processors.
- Edit the file rc
```
sudo gedit /etc/init.d/rc
```
- Look for a line "CONCURRENCY=none" and change to "CONCURRENCY=shell"
By doing this we'll have problems in simultaneuosly services. The service HAL must be delayed:
```
sudo mv /etc/rc2.d/S12hal /etc/rc2.d/S13hal
```
f) CPU Frequency Scaling Monitor

The is very useful for reducing the frequency when running on battery to save power.
- Add to the panel the applet located "CPU Frequency Scaling Monitor" under "System & Hardware".
- Run: (read all the warning, and if you are sure about this, say yes)
```
sudo dpkg-reconfigure gnome-applets
```
- If you say yes, restart the Panel or only the applet. And then you'll have four frequencies available to control.
g) Sensor - Temperature Monitoring
- Install the sensors daemon and applet:
```
sudo aptitude install lm-sensors sensors-applet hddtemp
```
- Then detect the sensors, you must say yes to all questions, run:
```
sudo sensors-detect
```
After rebooting, you can add the applet "Hardware Sensors Monitor" and see what components you want to monitore.

Cheers...

---

### Post by grn on 2008-03-05
BEEEEAAAAAUUUUUUTIFULLLLLLLLLL

YESSS. It works,

Thanks felipefoz

The perfect guide.

THANKS A TON.

:guitar:

---

### Post by LexRoss on 2008-03-05
Thanks and you did not post a fix to ethernet card random MAC address yet. I've got Asus F5N laptop based on the same chipset, and will be posting the similar guide soon. The only difference is the web cam, and special keys managed by asus-laptop kernel module. There is a page on Asus F5N that I maintain for those interested: [https://wiki.ubuntu.com/LaptopTestingTeam/AsusF5N](https://wiki.ubuntu.com/LaptopTestingTeam/AsusF5N)

Being new to Ubuntu, I thought that would be an appropriate place for laptop report. But not to worry, the guide on forums will follow!

---

### Post by felipefoz on 2008-03-05
> **grn said:**
> BEEEEAAAAAUUUUUUTIFULLLLLLLLLL

YESSS. It works,

Thanks felipefoz

The perfect guide.

THANKS A TON.

:guitar:

hey, you should also thank the community as well. I would be nothing without them. But are you still facing problems with the "forever"  - Starting Up... - screen???

---

### Post by afterstep13 on 2008-03-06
@felipefoz
  nice guide.... most of will work for 64 bit too :)

@others.
  this is how you do in 64 bit

1 Install ubuntu to the system using safe graphics or text mode, then reboot the system
Note :: It may so happen that the booting may fail. In that case do the follwing :
(i) at grub boot menu press e
(ii) goto 2nd l ine (root=...) and and press e
(iii) at the end of the line add all_generic_ide and press enter
(iv) press b to boot
Note :: You may add the above command (all_generic_ide) to /boot/grub/menu.lst
then you need not enter manually every time. just append the command to
tle line root=... for the ubuntu kernel.

2 For installing the nvidia graphics drivers
(Note you need a working internet connection)

(i) Goto menu System->Administration->Synaptic Package Manager
(ii) click on reload to reload package information (otherwise the package might not appear)
(iii) install the package nvidia-glx-new
(iv) goto menu System->Administration->Restricted Drivers Management and enable Nvidia drivers
iv) reboot the system, the graphics should be working now
(vi) goto termnal and run nvidia-settings to configure the display

3 Sound

(i) using synaptics package manager install linux-backports-module
(ii) goto a terminal and do
sudo nano -w /etc/modprobe.d/alsa-base
add the following line to the end
options snd-hda-intel model=acer
press Ctrl-X and save the file
(iii)reboot the system, now sound will be working

The other alternative is compile the latest drivers and use them as described by
felipefoz.
I suggest it's **better to compile** than use backports.


4 wifi
(i) goto [http://ndiswrapper.sourceforge.net/](http://ndiswrapper.sourceforge.net/) and goto the download section
(ii) click on "View older releases from the stable package" and dowload version 1.44. donot download other versions, for some reason they assign a 00:00... mac address and it can't be changed using ifconfig either
(you may try out newer versions but 1.44 works for sure)

(iii) extract the archive using tar xzvf ndiswrapper....
(iv) download the winxp drivers for your wifi card
(v) run the following commands
sudo modprobe -r ath_pci
sudo cat > /etc/modprobe.d/blacklist.common
enter the line blacklist ath_pci
press Ctrl-D
(vi) run sudo apt-get install build-essential
(vii) now reboot the system
(vii) after reboot, we need to compile ndiswrapper
cd <the ndiswrapper directory>
sudo make
sudo make install
(viii) extract the wireless drivers to a directory
tar xzvf <archive name>

(ix) install the drivers
cd <the wireless drivers directory>
sudo ndiswrapper -i net5211.inf

(note as of now net5416 for 64 bit is not available)

(now you can do a ndiswrapper -l to see if the drivers were installed)

sudo modprobe ndiswrapper
sudo ndiswrapper -m
sudo ndiswrapper -ma
sudo ndiswrapper -mi

(x) sometimes it happens that ndiswrapper fails to assign a MAC address to the
wifi card, to fix that do the following
sudo nano -w /etc/network/interfaces
add the line
pre-up /sbin/ifconfig wlan0 hw ether XX:XX:XX:XX:XX:XX
where XX:XX:XX:XX:XX:XX is the MAC address of the card.

now save the file and reboot.

(xi) wireless should now be working.

**Alternative** now madwifi has support for this card for 32 bit,  you may try it out

Note:: if you still can't connect then try pressing the wifi button, the wifi led does not seem to work with linux. press the wifi button and then try connecting.

5. **The problem of incrementing eth#**
This happens because somehow the MAC address is reported to linux in reverse.
To fix this do the following :
(i) dmesg | grep Mac
this gives the mac address in reverse ( a line with Invalid Mac ...)
note that down. that is the mac address in reverse

(ii) sudo nano /etc/udev/rules.d/70-persistent-net.rules
delete any line that ends with NAME="eth#"
add the following line
SUBSYSTEM=="net", DRIVERS=="forcedeth", NAME="eth0"
now save the file

(iii) now do sudo nano /etc/network/interfaces
add the line
pre-up /sbin/ifconfig eth0 hw ether <the mac address>

(iv) now reboot the system

a few tips for 64 bit:
 java web start  1.5 or 1.6 doesnot work in 64 bit, use 1.4
 you may additionally need 32bit libraries for certain (additional) things to work.

if you use 64 bit then the wifi-led and suspend might not work.

---

### Post by _godbout_ on 2008-03-06
1 word for this: awesome.

I didn't follow this topic because I've just found it and I already solved my troubles, but it seems that all the things I used are here, clearly reported. Perfect, thanks a lot to felipefoz!

Guillaume

---

### Post by scottro on 2008-03-06
I wanted to add my thanks.  I was using the MadWifi patched version which works perfectly, but I have no wireless LED.   Your way works perfectly (for an Acer Aspire 4720z) and gives me the LED.

---

### Post by grn on 2008-03-06
> **felipefoz said:**
> hey, you should also thank the community as well. I would be nothing without them. But are you still facing problems with the "forever"  - Starting Up... - screen???

Oh yes, I should thank the entire community as well. Thank You ALL. Or as they say in Africa, thanks for your UBUNTU.

Yes friend, I am still struggling with the Starting up issue. Can you guess why?

---

### Post by jalito27 on 2008-03-06
Excuse me for my english but I'd say that the guide it to much, really good explained.
In my personally case, I have to install de nvidia driver with ENVY.
Thank you a lot for the guide.

Jalito27 :)

---

### Post by _godbout_ on 2008-03-06
Actually I used this topic just for the Nvidia installation, and I found 2 problems:

1 - The refresh rate stuck to 50hz. Actually, it's just in gnome that the refresh is not correctly reported, so you can leave it like this, up to the user. So maybe there is no need to add information about that in the guide?

2 - After the installation of the Nvidia drivers, all my windows title bars disappeared. This is more troublesome. I had to edit the xorg.conf file to make them reappear. Felipe, do you want to add this in the guide?

If you want to add any of these, I'll write you how I did.

Guillaume

---

### Post by felipefoz on 2008-03-06
@afterstep13

The problem with the MAC adress happend also in the 32 Bits, if yes, may I add to the guide, the lines you explain the issue?


> **_godbout_ said:**
> Actually I used this topic just for the Nvidia installation, and I found 2 problems:

1 - The refresh rate stuck to 50hz. Actually, it's just in gnome that the refresh is not correctly reported, so you can leave it like this, up to the user. So maybe there is no need to add information about that in the guide?

2 - After the installation of the Nvidia drivers, all my windows title bars disappeared. This is more troublesome. I had to edit the xorg.conf file to make them reappear. Felipe, do you want to add this in the guide?

If you want to add any of these, I'll write you how I did.

Guillaume

So, I can add to the guide, may you give more information about the trouble!
Like, ubuntu 32 bits? Installed Nvidia after installing the nvidia from ubuntu?
Using compiz? give more detailed information, so I can add and explain all the problem, since I didn't have it. thanks...

cheers

---

### Post by afterstep13 on 2008-03-07
@felipefoz
oh sure, absolutely !

@godbout
if your title bars disappeared, that might be because of compiz, rather than Nvidia
anyways what exactly did u do ?

---

### Post by afterstep13 on 2008-03-07
@grn
my best guess is that happens because of acpi, it gets stuck there until the power button causes an interrupt, and then it gets going.

(that happened with me too in 32 bit,  the 386 kernel gets stuck like that, and it shows
only one of the processor cores, the 686 kernel doesn't boot at all. So I'm using 64bit :)

---

### Post by felipefoz on 2008-03-08
Post Update
@afterstep13
I put references to your post at the beggining for 64 bits user and in the LAN problem.

@others
ACPI, Battery section added.
Hibernate Section updated

Soon, i might find a solution for the "always on" wireless LED. Testing all possibilities. this week i come with breaking news, hehehe

---

### Post by grn on 2008-03-09
Hey, I just noticed that my CAPS Lock and NUM Lock LED are not lighting up. Anyone else with the same problem?

---

### Post by _godbout_ on 2008-03-09
> **felipefoz said:**
> 
So, I can add to the guide, may you give more information about the trouble!
Like, ubuntu 32 bits? Installed Nvidia after installing the nvidia from ubuntu?
Using compiz? give more detailed information, so I can add and explain all the problem, since I didn't have it. thanks...

I'm using ubuntu 32bits, yep. I got troubles with my wireless with the 64bits.
For the problem of the 50hz refresh rate, it's actually just the report by ubuntu which is wrong. In the nvidia control panel, the correct refresh rate is the good one. But I decided to correct it anyway, by disabling the DynamicTwinView. I added this line:
> 
Option "DynamicTwinView" "False" in the /etc/X11/xorg.conf file, in the section "Device"


About the title bar problem, I had it only once, in this installation. I installed ubuntu about 10 times and never got it. What I did to correct this problem is adding this line in the same section and same file than the tip above:
> Option “AddARGBGLXVisuals” “True”


> **afterstep13 said:**
> 
@godbout
if your title bars disappeared, that might be because of compiz, rather than Nvidia
anyways what exactly did u do ?

Yep, possible. I just installed the nvidia drivers, and then the desktop effect went from none to normal. That's when the title bar disappeared. When I put back to normal, it went to normal again.

---

### Post by felipefoz on 2008-03-10
okay! explained!
I'll append the tip about the titlebars. I remember seeing this line in my xorg once.
But about the correct rate, it's not necessary, I'll keep that way.
thanks..
;)

---

### Post by felipefoz on 2008-03-11
@all
New fix for LED issue, now you can choose how you want your LED to blink. hehehe
how ironic, couple days ago we couldn't see the led, and now we can tweak how the LED blinks and etc...

@afterstep13
that might be a way for fixing the LED issue in 64 Bits, try something related to it, and post the results. BTW I compared the .inf files from net5211 and net5416, and found out it was missing that line and other lines in net5416, after adding all of them, I noticed the difference, and started excluding one by one.

---

### Post by swampdweller on 2008-03-14
I'm a lazy fellow, and since my Gutsy32 wifi was already working (but for the LED) on the 5211 driver, I tried just grafting a chunk of your 168C:001C.5.conf file into mine, et voila!  Turns out it's orange.  Who knew?  Thanks very much!

---

### Post by _godbout_ on 2008-03-15
Hey there!
I tried to play with Ubuntu 8.04 32 but because of a package error, I had to reinstall the whole system. So I decided to try the amd64 version of the 8.04, let's go for the worst ahah!
Actually, it works quite well. I succeeded to make everything work with this thread, except for the wireless led.
I'll try to investigate a bit, and let you know if I succeeded to make it work.

Guillaume

---

### Post by _godbout_ on 2008-03-16
Just by following your procedure, felipe, I added the following in the correct file:

> 
gpioPinFunc1|3
gpioLedCustom|4


and now the led works correctly under Ubuntu 8.04 64bits!

Thanks for all ;)

---

### Post by felipefoz on 2008-03-16
> **_godbout_ said:**
> Just by following your procedure, felipe, I added the following in the correct file:



and now the led works correctly under Ubuntu 8.04 64bits!

Thanks for all ;)

hey, good to know, I think when they release the final version of 8.04, I'll try the 64 Bits. ;)
Now, i have everything I want working in this version, including hibernate, 100% of times, but first I'll test for a week, if I keep succeeding I'll post here the results, =)

---

### Post by ramadhian on 2008-03-21
13) Card Reader
Not fully functional. I couldn't test all kind of cards. But Memory Stick doesn't work. I've read SD cards only work. You may want to check this project at BerliOS

My Card Reader Work after I add :

# TI FlashMedia SD driver
tifm_sd

at /etc/modules

---

### Post by afterstep13 on 2008-03-24
@swampdweller, godbout, felipefoz
thanks for the led fix, it works in 64 bit ubuntu too

@all
i notices that sound on this laptop(at lest on mine) is somewhat low. I tried to reset the
default sample rate of alsa by doing the following :
              sudo gedit /usr/share/alsa/alsa.conf
then at the line  
              defaults.pcm.dmix.rate 48000
changed 48000 to 44100

i feel that made the sound louder, but I am not sure if it actually had an effect or i was
imagining it. 

Could any of you try this and let me know

---

### Post by Tyshalob on 2008-03-24
First off, a major heartfelt thanks to everyone that provided the information in this thread. I had initially been trying to install Slackware on the laptop using bits and pieces of this thread and found it useful. Unfortunately I couldn't get the boot issue sorted out in Slackware, and so I am now using Ubuntu on the laptop since there is a fairly comprehensive tutorial for making it work that simply doesn't exist for Slackware.

Now to the reason why I'm posting: I can't get the blasted nvidia card working properly. For whatever reason the dang thing is stuck in 800x600 mode, and when I try to use the nvidia settings tool under applications > system tools it launches with the "It appears you aren't using the nvidia driver" warning. I've tried following various links for troubleshooting the nvidia driver issue, but have failed in correcting the issue each and every time. What I really don't get is that the nvidia driver is being loaded. When I "lsmod | grep nvidia" I can see that the nvidia driver is loaded and that agpgart is using the nvidia driver.

I installed the latest driver package from nvidia which is NVIDIA-Linuxx86-169.12-pkg1.run. The nvidia website says that this driver version supports the GeForce 7000m and nForce 610m chips.

*edit*

Nevermind. I used the Envy tool to install the driver and all is now well.

---

### Post by abhilashkumar on 2008-03-25
I have an acer 4520 with the athlon processor. Loaded Vista Home Basic.
When i try and install ubuntu, just before the final step there is a summary. here the installer does not recognize windows vista bootloader....

The summary before final install is supposed to say that right?

will i still be able to dual boot if i continue with ubuntu install?

---

### Post by _godbout_ on 2008-03-25
I've exactly the same configuration than you and didn't have any trouble.
Windows doesn't know how to dual boot with Linux but Linux installs a loader, so you'll be able to choose your os, no worries :)

---

### Post by abhilashkumar on 2008-03-26
If you see this image 

[IMG]http://apcmag.com/system/files/images/vista_ubuntu_12.jpg[/IMG] 

from [http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm) and see the "Ready to Install" screenshot, you can see that the ubuntu installer has detected Windows Vista Longhorn.

I dont get that message. I get a blank area there.

---

### Post by abhilashkumar on 2008-03-26
However... I have explored various screen shots and screen casts... not everywhere does ubuntu detect vista. It seems people have been successful in installing it even if that message doesn't appear.

I guess I wont know till I try. Till now I used to come to the summary screen and then wonder if I should continue.

My hard disk is 160 GB... I have 3 partitions. Vista on C:

Do I have to shrink this partition only and make room for Ubuntu or can I install to any partition? Also, how much minimum space do I need to allot for the Ubuntu partition? 

When I shrink C: in Vista I get about 6.5 GB for the new partition.

---

### Post by zahris on 2008-03-26
i've installing Nvidia 169.xx driver using envy, but it make my webcam playing soooo slooooowww...

is there any run around to fix this?

and the wireless LED is owesome... keep the good work guys.. ;)

---

### Post by carlnz on 2008-03-26
Thank you all so very much for the information here. I've been struggling for months to get Ubuntu installed on my 4220, and this guide worked a charm.

---

### Post by grn on 2008-03-27
Hey All,

We've come a long way. Can't wait for Hardy any longer.
As for Gutsy, I am still facing the following issues. Please help.

1. After GRUB, my screen freezes up indefinitely with the text, 'Starting Up ...' .
But after I press the 'Power Button of my lappy(after 7-10 seconds), 'I get three error lines(Cannot allocate source region 7... 8... 9...), and then it boots normally and with good speed. The SATA setting in the BIOS is AHCI. I tried with the IDE setting too, but still the same.
I did check the 'fix' script, Everything is correct.

2. My Webcam was working after I installed cheese.
But to get my sound working, I had downloaded the 'linux-backports-modules'
Suddenly cheese stopped recognizing my webcam. Error window says "Unable to find a webcam, SORRY!". Tried Camorama, Ekiga, but nothing works.

Can anyone help? Especially @felipefoz, @afterstep13, I am kind of banking on you.

---

### Post by abhilashkumar on 2008-03-28
All the code that you mention in your guide, has to be typed at the command prompt right?
can this be done through the terminal in the GUI or do i need to go to the command line interface [ctrl + del + F*]?

---

### Post by abhilashkumar on 2008-03-28
Yesterday I tried using Envy for configuring the nvidia card. when i double clicked on the file... i got an error saying.

dependencies are not satisfiable

Whats this?

---

### Post by felipefoz on 2008-03-28
@grn
for the first problem, i haven't got a conclusion for it. have no idea at all.
for the second one, try unloading and loading the module from camera, i think it is "uvcvideo", after this with "lsusb" see if the camera is listed there, if the answer is yes for both. maybe you should consider seeing something about the v4linux configuration. Some tips, keep trying all possibilities and then let us know.

@abhilashkumar 
try installing a package "linux-headers" or see what are the dependencies in the site you downloaded this "envy" package.

---

### Post by sunnysujan on 2008-03-29
Finally, I've also got Ubuntu on my Acer Aspire 4520.

I had windows xp before. I downloaded**[SIZE="3"] 'Ubuntu 8.04 Beta'[/SIZE]** and installed it. 
When you run the installation on windows it gives you an option to keep a copy of your windows and install Ubuntu (dual boot). It installed perfectly. I can run Windows as well. But soon I'm gonna give up Windows completely!
[B]
I didn't have to do anything for graphics card and sound. It just worked!!![/B]

For Wireless,
Go to System>>Administration>>Synaptic Package Manager>>
Search for 'Ndiswrapper'

# Install all the three packages [ndisgtk, ndiswrapper-common, ndiswrapper-utlis-1.9]
   You need to go online to install these packages using LAN.

# Now, as mentioned above:-
   Blacklist the native ath_pci module to prevent from loading it. 
   sudo gedit /etc/modprobe.d/blacklist
# Add the code:
    blacklist ath_pci
[URL="http://www.atheros.cz/download.php?atheros=AR5008"]
# Download the xp driver from Atheros Site[/URL], look for the driver 6.0.3.85 for Windows XP 32 Bits, the  file name will be xp32-6.0.3.85.zip. The file inside must be net5416.inf (not net5211.inf).
Extract the inf file to your desktop.

Now, goto >> System>>Administration>>Windows Wireless Drivers>>
Click +Install New Driver
Select the inf file from your desktop and click Install.

Now as soon as you do that, when you click the network icon on your top panel you should see all the available wireless connections. There you go.. configure and connect!

This is how I did it and still there could be much easier way to do so!

---

### Post by abhilashkumar on 2008-03-30
Here's what I did..

1. Upgraded via LAN to 8.04 Hardy

2. Sound was working absolutely fine

3. Used the instructions by the author of this post to get my display up and running. Works fine now.

4. Wifi is not working. I tried what was given in the guide and also what was given in the last post. I get no errors, but I cant start wifi. Nothing happens when I press the wifi button and no networks are displayed to me by the network icon on the menu on top.

What am I doing wrong?

I really need the wifi to work... Please help.

---

### Post by caravena on 2008-03-30
> **sunnysujan said:**
> Finally, I've also got Ubuntu on my Acer Aspire 4520.

I had windows xp before. I downloaded**[SIZE="3"] 'Ubuntu 8.04 Beta'[/SIZE]**...

See guide: [http://ubuntuforums.org/showthread.php?t=734691&highlight=4520+hardy](http://ubuntuforums.org/showthread.php?t=734691&highlight=4520+hardy)

Guide no use ndiswrapper.

@sunnysujan: You testing Ubuntu Hardy Heron Beta 64bits in Acer Inspiron 4520?

---

### Post by abhilashkumar on 2008-03-30
I dont have a CD. I upgraded from Gibbon to Heron using the online updater!

If I follow the instruction from the step below in the tutorial, will it work for my system?


C[B]ode:

sudo su
cd /usr/src
tar -xvzf madwifi-nr-r3366+ar5007.tar.gz

##  note: You do know about tab completion, right?  Instead of typing the previous
##  command letter-for-letter, you can simply type "tar -xvzf mad" and hit Tab to auto-
##  complete the rest.  Same goes for the directory name in the next command as well.

cd madwifi-nr-r3366+ar5007
make clean
make install
[/B]

---

### Post by caravena on 2008-03-30
> **abhilashkumar said:**
> I dont have a CD. I upgraded from Gibbon to Heron using the online updater!


Ok.

[QUOTE=abhilashkumar]
If I follow the instruction from the step below in the tutorial, will it work for my system?


C[B]ode:

sudo su
cd /usr/src
tar -xvzf madwifi-nr-r3366+ar5007.tar.gz

##  note: You do know about tab completion, right?  Instead of typing the previous
##  command letter-for-letter, you can simply type "tar -xvzf mad" and hit Tab to auto-
##  complete the rest.  Same goes for the directory name in the next command as well.

cd madwifi-nr-r3366+ar5007
make clean
make install
[/B][/QUOTE]

Oummm, is advanced...

See:
[http://madwifi.org/ticket/1679#comment:112]("http://madwifi.org/ticket/1679#comment:112") He work with patch madwifi-nr-r3366+ar5007.tar.gz
[http://madwifi.org/ticket/1679#comment:115]("http://madwifi.org/ticket/1679#comment:115")

---

### Post by abhilashkumar on 2008-03-30
How do i get to know the current chipset of my wireless. The forums seem to say that the version/model given by lspci is wrongly reported. also the madwifi patch is for only one particular artheros chip. Right?

Since, I am pretty new to this... I need a little bit more verbose help/instructions.

help me if you can guys. Wifi is the only thing thats left for me to run in ubuntu hardy heron....

---

### Post by caravena on 2008-03-30
> **abhilashkumar said:**
> How do i get to know the current chipset of my wireless. The forums seem to say that the version/model given by lspci is wrongly reported. also the madwifi patch is for only one particular artheros chip. Right?

Since, I am pretty new to this... I need a little bit more verbose help/instructions.

help me if you can guys. Wifi is the only thing thats left for me to run in ubuntu hardy heron....

You use ndiswrapper, madwifi is advanced in not madure proyect for wifi card of acer aspire 4520.

You use guide: [http://ubuntuforums.org/showpost.php?p=4609715&postcount=36](http://ubuntuforums.org/showpost.php?p=4609715&postcount=36)

---

### Post by Robin J S on 2008-03-30
Thanks soo much for this guide.

I am new to Linux/ubuntu and decided to go for this system to do music with. I was unable to use headphones until now!

Cheers

Robin

---

### Post by abhilashkumar on 2008-03-31
I have just downloaded the iso for Hardy Heron. I will do a fresh install of it this evening. [i have a day job too you know :lolflag:]

Then I will try and do as this post sez: [http://ubuntuforums.org/showpost.php...5&postcount=36](http://ubuntuforums.org/showpost.php...5&postcount=36)

I had gone through this but I had already tried the other way as mentioned in the original post. This time I will only do what sunnysujan sez.

Best of Luck to me.

---

### Post by abhilashkumar on 2008-03-31
> **sunnysujan said:**
> Finally, I've also got Ubuntu on my Acer Aspire 4520.

I had windows xp before. I downloaded**[SIZE="3"] 'Ubuntu 8.04 Beta'[/SIZE]** and installed it. 
When you run the installation on windows it gives you an option to keep a copy of your windows and install Ubuntu (dual boot). It installed perfectly. I can run Windows as well. But soon I'm gonna give up Windows completely!
[B]
I didn't have to do anything for graphics card and sound. It just worked!!![/B]

For Wireless,
Go to System>>Administration>>Synaptic Package Manager>>
Search for 'Ndiswrapper'

# Install all the three packages [ndisgtk, ndiswrapper-common, ndiswrapper-utlis-1.9]
   You need to go online to install these packages using LAN.

# Now, as mentioned above:-
   Blacklist the native ath_pci module to prevent from loading it. 
   sudo gedit /etc/modprobe.d/blacklist
# Add the code:
    blacklist ath_pci
[URL="http://www.atheros.cz/download.php?atheros=AR5008"]
# Download the xp driver from Atheros Site[/URL], look for the driver 6.0.3.85 for Windows XP 32 Bits, the  file name will be xp32-6.0.3.85.zip. The file inside must be net5416.inf (not net5211.inf).
Extract the inf file to your desktop.

Now, goto >> System>>Administration>>Windows Wireless Drivers>>
Click +Install New Driver
Select the inf file from your desktop and click Install.

Now as soon as you do that, when you click the network icon on your top panel you should see all the available wireless connections. There you go.. configure and connect!

This is how I did it and still there could be much easier way to do so!

I did everything you said. Exactly as you said to do it. All I get on top when I click on the network icon is "Connect to a 802.1X protected wired network"

Is this what its supposed to show? 

It says "802.1X WIRED NETWORK"

Is that what it says for you?

Also, nothing happens when I press the wifi launcher button. You have not said anything regarding that!
Please help!!!

---

### Post by kerbeross on 2008-03-31
Felipefoz, I sent you a PM with some considerations about this topic.. maybe can help you with details.

abhilashkumar, I don't know if you already found your wireless chipset, but my laptop came with a sticker pasted below, with the numbers and everything else.

PS.: Sorry my poor english =S

---

### Post by abhilashkumar on 2008-03-31
> **kerbeross said:**
> Felipefoz, I sent you a PM with some considerations about this topic.. maybe can help you with details.

abhilashkumar, I don't know if you already found your wireless chipset, but my laptop came with a sticker pasted below, with the numbers and everything else.

PS.: Sorry my poor english =S

@kerberos
I found my wifi chipset Arteros 5007eg
and like i said in my previous post, i cant get it to work..
nothing happens when I press the wifi button

---

### Post by abhilashkumar on 2008-03-31
The sticker below my laptop says "Atheros AR5BXB63"
I cant find this model number on the Atheros website.

Editted: I found out that this model means AR5006x series chipsets.

---

### Post by grn on 2008-04-01
:confused:

---

### Post by _godbout_ on 2008-04-03
****, I installed the updates of Hardy yesterday, and now my wifi is not working anymore. I have to use Vista, that sucks a lot! :D

---

### Post by meiradarocha on 2008-04-03
Great job, felipe and co-workers.
Almost all works fine in my Acer 4520, but wifi. The wireless I could put functional with this recipe:
[http://www.ubuntugeek.com/atheros-5007eg-with-madwifi-on-i386-platform.html](http://www.ubuntugeek.com/atheros-5007eg-with-madwifi-on-i386-platform.html)

-- José Antonio Meira da Rocha
[http://meiradarocha.jor.br](http://meiradarocha.jor.br)

---

### Post by hekamiah on 2008-04-04
In 32bits this wifi works fine with madwifi too, see:
[http://www.ubuntugeek.com/atheros-5007eg-with-madwifi-on-i386-platform.html]("http://www.ubuntugeek.com/atheros-5007eg-with-madwifi-on-i386-platform.html")
And thank you for the guide... :)

---

### Post by animaCCo on 2008-04-05
TNKS for the help.  All works ok in Ubuntu Studio 7.10
Diego | [http://www.animacco.com.ar/diego]("http://www.animacco.com.ar/diego")
[IMG]http://www.animacco.com.ar/mis_imagenes/Avatar_Taringa.png[/IMG]

---

### Post by starjammer227 on 2008-04-10
been looking all over for this, and now it's in one place. have just installed gutsy 64 bit on my acer 4520g (8400G video card). can't wait to try everything tonight (am still at the office, it's only 5:30pm here..)

thanks a lot!!

---

### Post by neolithicsilence on 2008-04-10
Thanks for the post.. Has anyone tried the Express Card yet?

---

### Post by r88ney on 2008-04-12
Hi felipefoz, nice guide...
I've tried many guides from various sources and none was success until I found this page. I give it a shot and... Ubuntu Muslim Edition 7.10 is working on my Acer Aspire 4520.

**Little problem with sound**
Everything is working :) but I can't control volume via volume slider in my laptop's front side. It's not control the "master" volume but the "headphone", so I must click the volume control on the screen everytime I wanna change volume level (believe me it's little annoying) unless I'm using headphone. Have you or anyone else solved this problem?

---

### Post by pk4520 on 2008-04-12
Yesterday I tested the 8.04, Sound,and wiredLAN is working, display not running at 1280X800 too and the important thing is Atheros Wifi is not working :(

Today, I have installed this ubuntu 7.10 at my Acer4520.

for information, my sound couldnt start, I followed all the instruction here and stuck at sound, nothing happen after the reboot process.
and the display couldnt change to 1280X800 too,


* wiredLAN and Atheros Wifi working 100% with the blinking LED too.

My Hardware Specs:
Acer 4520 - AMD Turion 64 X2 Mobile TL-60 (2.0 Ghz, 2 x 512 L2 Cache)
Chipset Nvidia Nforce 610M
VGA - Nvidia GeForce 7000M - 14" WXGA+ WideScreen 1280x800
1GB+512MB DDR2 667 - 80 GB HDD - DVD-RW
Atheros AR5007EG 802.11b/g WLAN

---

### Post by pk4520 on 2008-04-13
After a new installation ubuntu7.10 :
1. I could boot normally after using the guide at the 4 point.
2. Wired LAN is working
3. Sound is working, both speaker left and right speaker.
4. Wireless LAN / Atheros AR5007EG 802.11b/g WLAN is working. the led is working 100% without fixing the led problem step.
5. here we are at the problem. after installing the vga, and restart X (ctrl+alt+backspace) that never change the resolution to 1280x800, and made an error at sound device, At the first time, speaker working both left and right side, but after several reboot, the left speaker have not working, no sound at all at the left speaker.

edited: sound working perfect... :confused: my bad.... problem in the mixer :lolflag: switch to off left speaker :lolflag:

FYI: I follow every single manual step from felipefoz as thread starter. 
I'm very newbie in linux, and this is the time I'm learning this :lolflag:
I have no problem if must to do another fresh installation. :guitar: 

Thanks if have any hint to fix the problem. and sorry for my bad english , coz it's not my first language.

---

### Post by davarse on 2008-04-13
i've acer 5920, and i have several problems...
does your giude woks in it????
do you have guide for acer aspire 5920???:confused:
i appreciate it

cheers'

---

### Post by davarse on 2008-04-13
dude does this guide work for acer aspire 5920???
i have gusty in my laptop and i got few problem like on your giude...
do you have guide for aspire 5920??:confused:
i appreciate it

cheers'

---

### Post by afterstep13 on 2008-04-18
[COLOR="Red"]**IMP IMP IMP**[/COLOR]

Has any one seen this bug ?

[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695/](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695/)

if yes what were the output of your       sudo smartctl -A /dev/sda
(note you may need to install smartmontools first)

---

### Post by VishnuThejaJ on 2008-04-22
Hi,

Why ACER 4520 is not listed in LaptopTestingTeam is there any problem. According to this thread almost was fixed. if its listed in the next version, its very easy for the new users to go for UBUNTU.

---

### Post by lingyizhenyi on 2008-04-23
I sucessfully installed ubuntu7.10 on my laptop (my video card and wireless card are different, nvidia geforce 8400mg,broadcom...). Every thing seemed to be working fine after installing some drivers manually, until I noticed xorg behaved odd. Moving an opened window can easily take 40+% cpu usage. This never happened on my desktop pc, which is also running ubuntu 7.10. Anybody else also encountered this problem?
Thanks!

---

### Post by liquerLOVER on 2008-05-02
wow.... but it seems that it fail on my laptop.(aspire 4520) i follow exactly based on ur guide but all i found is erk....ERROR!!!!(my wireless) can you plis help me HERO....eventhough after make clean, still got error wen make. can y0u giv me a full super duper complete guide 4 the wireless???????????im a loser....

---

### Post by felipefoz on 2008-05-02
> **afterstep13 said:**
> [COLOR="Red"]**IMP IMP IMP**[/COLOR]

Has any one seen this bug ?

[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695/](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695/)

if yes what were the output of your       sudo smartctl -A /dev/sda
(note you may need to install smartmontools first)

I'm long time whithout replying here!
I heard about this bug, and applied all changes necessary to decrease the load cycle count, when just installed hardy, increased 1,000 in one day, it went from 10000 to 11000, it took 4 months to get to 10000. By the way, I applied these modifications already in gutsy, but I thought it was fixed at this version. That means, no fix yet.

On the other hand, very satisfied with Hardy, some differences relevant to this first post.
- No boot problems
- Sound works out of the box, although I haven't tested microphone.
- Wireless can use the new Atheros AR5007EG driver at the atheros.cz website, add the lines
"gpioPinFunc1|3
gpioLedCustom|4"
to the same archive I wrote here, and you have the wireless LED acting just like in windows, blinking with traffic and all, exactly the same
- Nvidia driver is now at the last version, no need to install directly from website, I didn't test the Screen Manager to see how it works with the Vga and S-Video Out, but an alternate option is installing the package "nvidia-settings", and you will have the menu "Nvdia X-Server Settings" just like before, fully functional.
- Touchpad works out of the box, there is an Touchpad option under System > Preferences > Mouse, I may be wrong, but I didn't find an option about disabling touchpoad while typing, so, I did all the procedure with gsynaptics again.
- Hibernate and Suspend works with no modifications, but sound stops working after resuming. I didn't look for a fix yet.

In general, things have got pretty much better than gutsy, but still a lot to fix, once more, congrats to hardy development team.
Should we just update this thread, or create a new one for Hardy?
cheers...

---

### Post by _godbout_ on 2008-05-06
Hi felipe!

Actually I couldn't, for myself, make the wireless work anymore with ndiswrapper! I tried the old drivers and the new ones but got the same result, no connection! I ended up using the madwifi driver, under the 32bits version. It's working as long as I don't put any protection on my router, which is quite annoying :D Have to find a solution about that :)

Cheers,

---

### Post by VishnuThejaJ on 2008-05-07
Hi :),

I have Acer 4520, i installed Ubuntu 8.04 AMD64 desktop version. Got problem with wireless. After using ndiswrapper i am able to scan the wireless using the command **iwlist scan** but network manager is unable to detect.

---

### Post by felipefoz on 2008-05-07
The ndiswrapper worked with me without problems...
The file of the new driver is now called xp3264-7.4.2.75-whql.zip
Inside of the zip content, there are two .inf files, you guys should pay attention now, one is netathw.inf and the other netathwx.inf. If you use the ndiswrapper with the second one, then it's not going to work. 
so
sudo ndiswrapper -i netathw.inf
and the other steps...
Then it should work
*using also the latest version of ndiswrapper, compiled myself.

---

### Post by VishnuThejaJ on 2008-05-07
It does not work in AMD64 Ubuntu 8.04 version. Don't know about X86 version.

---

### Post by grn on 2008-05-14
Hi

Installed fresh Hardy (32-bit). Pleased with the results :).
Except for Wifi, everything else was a breeze.

**Sound** - Out of the Box
**Video** - Worked perfectly with Nvidia 'new' driver in repository
**Touchpad** - Out of the Box
**WebCam** - Out of the Box
**Wired LAN** - Out Of the Box
**WiFi** - used ndiswrapper & ndisgtk to install 6.0.3.85 drivers (net5416.inf - same as for gutsy) Works Perfectly. (Don't forget to install linux-headers* before this.)

**Suspend and Hibernate** work, but _no sound_ after resume.

Note: Do not install the Nvidia drivers from their website(they worked well in Gutsy though)
They worked, but needed to be reinstalled every time I booted. I could not get rid of them until I did a fresh install of Hardy.

And yes felipefoz, since this thread is archived, a new thread should be started.

---

### Post by felipefoz on 2008-05-16
> **grn said:**
> 
And yes felipefoz, since this thread is archived, a new thread should be started.

I see the things have gone well for you too in this version! thanks for answering, I was planning to write a new thread about 8.04, but first I need to fix the hibernate and suspend problem, the one with no sound. I'm working also on another issues, i'll try to make a complete guide, not an almost, hehehe! worth a try, doesn't it?
see ya

---

### Post by afterstep13 on 2008-05-20
hi felipefoz,

the sound issue can be resolved by simply adding 

options snd-hda-intel model=acer

to /etc/modprobe.d/alsa-base

---

### Post by grn on 2008-05-20
@ afterstep

voila! the trick works.

Thanks.

@ felipefoz

I think, your new complete guide for Hardy can now be posted.

---

### Post by grn on 2008-05-21
Now that the sound is working in suspend and hibernate, I tried it a few times to check the consistency.

1 out of 3 times on an average, my hibernation does not resume as expected.
(It is 1 out of 5 for suspend)

Although the sound works, my USB ports, wireless adapter, and camera do not function. A reboot solves the problem.

The times when hibernate and suspend are not successful, I do not get the X screen directly.
In fact I am presented with one of the tty screens.
On hitting Ctrl+Alt+F7, the Lock screen appears, and then I can resume my session. All other programs are unaffected.

Anyone else facing the same problem?

@felipefoz
> **felipefoz said:**
> I'm working also on another issues,

Did your issues include the one I am facing?

---

### Post by kerbeross on 2008-05-21
Sometimes when I resume from suspend (I almost never use hibernate), I get a blank screen instead of the lock one. It's because I use the Compiz Fusion(essentially) and other eyecandy (emerald for example). 

The solution is simply enter your pass and hit Enter, because the blank screen is only a glitch, the lock screen is hidden by the white layer. (If you search with the mouse, you will see the cursor change when it's over the pass input)

Maybe it helps someone.

---

### Post by felipefoz on 2008-05-23
> @felipefoz

Quote:
Originally Posted by felipefoz  
I'm working also on another issues, 

Did your issues include the one I am facing?

Actually no, I haven't tested hibernate and suspend, since it wasn't working the sound after resume. With this fix I'll try again and see if I'll experience the same thing. The issues I was saying concerns mainly power consumption, Hardy is very "energyholic". My battery life decreased from 2:15, 2:30 hours in Gutsy to 2:00, 1:45 hours in Hardy. I've been learning since then about power consumption and the measures I can take to improve that.
Hopefully you'll hear soon from me, if my job and college give me an extra time to tweak my laptop. hehehe

---

### Post by kerbeross on 2008-05-23
@felipefoz

Funny.. my laptop is the same as your.. and my battery life increased significantly, from 1:50 to 2:30. The unique difference is the processor, as mine is single-core. Maybe the problem resides in the processor.

---

### Post by grn on 2008-05-25
My battery has reduced significantly too.
Earlier, it would be 2:10, and now it is 1:25

I use it on AC power most of the time,so it didn't bother much. But it is most definitely a concern.

If kerbeross's single processor, gives him that good a battery life, may we should consider dynamically turning off one processor when not needed :-? Is it possible?

---

### Post by grn on 2008-05-25
Well I did find out something interesting.

I think that the **gnome power notification** is not working well.

With the Frequency-Scaling-Monitor in place, I tried changing the frequency and then checking the remaining battery by using the 'acpi' command in term. The results were relieving.

With the processor running at 100%(1.8 ghz), the remaining battery life would show as 1:25 by running acpi
```
$acpi
     Battery 1: discharging, 99%, 01:24:37 remaining

```

But with the processor running at 44%(800 mhz), the battery life would increase to 2:10. Great. But in the Battery notification, it still showed 1:25.

```
$acpi
     Battery 1: discharging, 99%, 02:09:40 remaining

```

And I did manage to work for a whole two hours after unplugging my AC power, and running at 800mhz.

Still more interesting is that the Battery Charge Monitor Panel Applet displays the remaining time quite correctly.

So I have turned the Power Manager Icon Notification OFF, and added the Battery Charge Monitor to my panel and dragged it to the end.

---

### Post by kerbeross on 2008-05-25
@grn
I've tested the acpi command, and the time is identical both in terminal and in the gnome power notification. Anyway, if the only problem is in the information, we're happy hehehe

---

### Post by xebec_the on 2008-06-13
man, this topic has solved all my problems, thanks!!!! :guitar::lolflag:

---

### Post by keanu_reeves on 2008-06-24
cannot thank you any less for this post my Acer 4520 is running on Ubuntu 8.04

Thanks Thanks Thanks Thanks Thanks Thanks Thanks Thanks Thanks Thanks Thanks Thanks Thanks Thanks Thanks Thanks Thanks Thanks Thanks Thanks Thanks Thanks Thanks Thanks Thanks Thanks Thanks Thanks Thanks Thanks Thanks Thanks Thanks Thanks Thanks Thanks Thanks Thanks Thanks Thanks Thanks Thanks Thanks Thanks Thanks Thanks Thanks Thanks Thanks Thanks Thanks Thanks Thanks Thanks Thanks Thanks Thanks Thanks Thanks Thanks 

:)

---

