---
title: "Asus Eee PC 1015PN  - graphic cards: Optimus and ION"
date: 2011-01-29
forum: Hardware
---

### Post by barthus on 2011-01-29
[B][COLOR=Red][SIZE=3]All scripts published and discussed in this thread 
will work for the Asus EeePC 1015 PN only !!! [/SIZE][/COLOR][/B]

[SIZE="3"][B][COLOR="Blue"]
'See [http://mtron.co.nr/projects/eee1015pn](http://mtron.co.nr/projects/eee1015pn) for up-to-date information' [/COLOR][/B][/SIZE]


[COLOR=Red]** Alternative solution: (Updated: 2011-08-05)**[/COLOR]
[COLOR=Red]**FOR VERSION 10.10 and Linux Mint 11.04 Katya. Should work also for Ubuntu 11.04**[/COLOR][COLOR=Red]** (not tested)**[/COLOR] 
**1. **Install your Ubuntu system
**2. **Update the system (restricted nvidia drivers, etc.)
**3.** Download the acpi_call module from here: [https://github.com/mkottman/acpi_call](https://github.com/mkottman/acpi_call)
**4.** ... and rebuild it for the current kernel:
```
cd path_to_acpi_call
make clean
make 
sudo insmod acpi_call.ko
```Replace 'path_to_acpi_call' with the correct path (path to the file acpi_call.ko).
** 5. **Save the following script for switching to the intel card before a boot. (execute: sudo Switch_intel.sh) 
```

#!/bin/bash
# Enable intel glx on Asus EeePC 1015pn 

# Check if we are root, else exit
if [[ $EUID -ne 0 ]]; then
    echo "This script needs to be run as root"
    exit 1
fi

# is the acpi module loaded?
if lsmod | grep -q acpi_call; then
    echo "ACPI does not need to be loaded."    
else
    echo "ACPI needs to be loaded."    
    cd path_to_acpi_call
    insmod acpi_call.ko
    sleep 3
fi

# The call for the next time
echo ""
echo "Mode 1 is now set: After the next boot only the Intel chip is visible."
echo "\OSGS 0x01" > /proc/acpi/call

echo ""
echo "The 'update-alternatives' has been set"
update-alternatives --set gl_conf /usr/lib/mesa/ld.so.conf
ldconfig

# Very important: fiddle with glx and libgl
if [ -f "/usr/lib/xorg/extra-modules/libglx.so" ] 
then
        echo ""
    echo "The library 'libglx.so' has been deleted."
    sudo rm /usr/lib/xorg/extra-modules/libglx.so
else
        echo ""
    echo "The library 'libglx.so' doesn't exist and must therefore not be deleted."
fi

echo ""
echo "Finished! Push a button ..."
read eingabe

```Replace 'path_to_acpi_call' with the correct path.


**6.** Save the following script for switching to the nvidia card before a boot (execute: sudo Switch_nvidia.sh) 
```

#!/bin/bash
# Disabe Intel Chip and enable nvidia on Asus EeePC 1015pn

# Check if we are root, else exit
if [[ $EUID -ne 0 ]]; then
    echo "This script needs to be run as root"
    exit 1
fi

# is the acpi module loaded?
if lsmod | grep -q acpi_call; then
    echo "ACPI does not need to be loaded."    
else
    echo "ACPI needs to be loaded."    
    cd path_to_acpi_call
    insmod acpi_call.ko
    sleep 3
fi

# The system is prepared such that the nvidia card is onlt visible
echo ""
echo "Mode 2 is now set: After the next boot only the Nvidia chip is visible."
echo "\OSGS 0x02" > /proc/acpi/call

# Copy the libglx file into usr/lib/xorg/extra-modules/
# Without doing this, compiz does not work properly (I have no idea why) 
if ! [ -f "/usr/lib/xorg/extra-modules/libglx.so.260.19.06" ] 
then
   cp /usr/lib/nvidia-current/xorg/libglx.so.260.19.06 /usr/lib/xorg/extra-modules/
   chmod 644 /usr/lib/xorg/extra-modules/libglx.so.260.19.06
   echo ""
   echo "The libglx has been copied"
fi

# Copy also the nvidia_drv.so file into usr/lib/xorg/extra-modules/
# As above: compiz needs this (I have no idea why) 
if ! [ -f "/usr/lib/xorg/extra-modules/nvidia_drv.so" ] 
then
   cp /usr/lib/nvidia-current/xorg/nvidia_drv.so /usr/lib/xorg/extra-modules/
   chmod 644 /usr/lib/xorg/extra-modules/nvidia_drv.so
   echo ""
   echo "The nvidia_drv.so has been copied"
fi

update-alternatives --set gl_conf /usr/lib/nvidia-current/ld.so.conf
ldconfig
echo ""
echo "update-alternatives ... and ... ldconfig"

# Very important: The link 'libglx.so' needs to be created
if ! [ -f "/usr/lib/xorg/extra-modules/libglx.so" ] 
then
   ln -s /usr/lib/xorg/extra-modules/libglx.so.260.19.06 /usr/lib/xorg/extra-modules/libglx.so
   echo ""
   echo "The libglx link has been set"
else
   echo ""
   echo "The libglx link already exists"   
fi

echo ""
echo "Push a button ..."
read eingabe

```You need to search the right name for the lib 'libglx.so...' and 'nvidia_drv.so' in the /usr/lib/nvidia-current/xorg/ directory.

That's it!

**Notes**
0. When you start the laptop the first time, you probably get into the shell first because of an error (sorry, I cannot fix this). Execute either 'Switch_intel.sh' or  'Switch_intel.sh'. Reboot after, then everything should be fine.
1. Note that you have to execute always the script 'Switch_intel.sh'  whenever you want to boot and use the intel card. In the case of the  nvidia card you must execute the script 'Switch_nvidia' only once for  all other following 'future boots' with the nvida card. 
2. The scripts are written such you can call them from a starter of a panel. Don't forget to make the scripts executable.
3. There is some output text, which comments all operations and which can be used to see what the system is doing. 
4. HDMI is perfectly working with Nvidia.

I hope that all this helps.

















**********************************************************
**First, original email** (January 29th, 2011                                                        &nbsp;)
**********************************************************

Hi all.

I bought just recently an Asus Eee PC 1015PN. For those who have an interest in this netbook and who want to install Ubuntu 10.10 32bit on it: It works quite well, almost out of the box! This is somewhat a report, but I have also a question with respect to the switch of graphic cards (see below) 

- Wlan works (driver needs to be installed via LAN and additional hardware drivers)
- Webcam works oob
- Audio works oob (despite micro ... there is some installation to be done, see below)
- Keyboard is very nice
- Nvidia works (needs to be installed with additional hardware drivers)
- With help of disper ([http://willem.engen.nl/projects/disper/](http://willem.engen.nl/projects/disper/)), the HDMI works perfectly!
- USB is fast, three slots
- Ubuntu can be installed just 'à coté' of Windows (pay attention with partitions though)
- and so on ...

Some advices for installing Ubuntu are described here:

[https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks)

However, there is only one issue for me, which needs still some work: Switching between the graphic cards, nvidia and intel.


On this site ...

[https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks)

... a small description is given about how to switch on the intel graphic card. 

```
 git clone http://github.com/mkottman/acpi_call.git
 cd acpi_call
 make
 sudo insmod acpi_call.ko

 echo "\OSGS 0x03" > /proc/acpi/call

 #Set the intel driver in xorg.conf
     ...
     Section "Device"
     Identifier "Device0"
     Driver "intel"
     VendorName "Intel GMA 3150"
     BusID "PCI:0:2:0"
     EndSection
     ...

 rm /usr/lib/xorg/extra-modules/libglx.so
 update-alternatives --set gl_conf /usr/lib/mesa/ld.so.conf
 ldconfig
```I followed all parts and rebooted the system. And indeed, I could boot into Ubuntu without no problems. The following commands output

```

> lsmod | grep videodev
videodev               43098  1 uvcvideo
v4l1_compat            13359  2 uvcvideo,videodev

> lspci
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge (rev 02)
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller (rev 02)
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02)
01:00.0 Ethernet controller: Atheros Communications AR8132 Fast Ethernet (rev c0)
02:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g LP-PHY (rev 01)
04:00.0 VGA compatible controller: nVidia Corporation GT218 [ION] (rev a2)
04:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)

```There is no Nvidia config panel and no visible 'signs' of the nvidia presence, althoug the chip is still visible (see list of lspci). The Optimus is also visible (lspci)

```

00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller (rev 02)
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller (rev 02)

```So then, on the site ([https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks)) it is written that one has to input the following in order to switch off the nvidia graphic card:

```

sudo insmod acpi_call.ko
echo "\_SB.PCI0.P0P4.DGPU.DOFF" > /proc/acpi/call

```I tried it out, and in the first seconds everything was fine. However, then the systems played nuts and got  completely frozen so that I had to do a hard reset with a following loud klick of the hard disk. I tried the whole procedure two times but the system always freezes.

Can somebody help me? If needed, I have also all data asked on this site here: [http://linux-hybrid-graphics.blogspot.com/2010/10/1000-plant-transcriptomes-project.html](http://linux-hybrid-graphics.blogspot.com/2010/10/1000-plant-transcriptomes-project.html)

Thanks a lot in advance!

---

### Post by mtron on 2011-01-31
Hello! 

Most probably you got hit by the kslowd bug introduced in linux kernels from 2.6.35 onwards. See e.g. launchpad bugs #595764 or #662946 

there are also numerous kernel bugs filled about this issue. See [https://bugzilla.kernel.org/show_bug.cgi?id=16265](https://bugzilla.kernel.org/show_bug.cgi?id=16265)
[https://bugzilla.kernel.org/show_bug.cgi?id=18802](https://bugzilla.kernel.org/show_bug.cgi?id=18802)

You might want to try some of the suggested workarounds but i found that none of them works reliable. I ended up using the latest lucid kernel in maverick what works good

Beware that you'll need to install fitting alsa modules in this case and this will only work with the GMA3150 vga.

Hopefully 2.6.38 will fix this.

---

### Post by mtron on 2011-01-31
ok, as a follow-up on this i want to explain a bit more in-deph what i did to get this working in maverick.

first: (to avoid any confusion)

Hot switching of the intel vga and the nvidia vga is currently not possible. The reason is that the open source intel i915 driver can't be unloaded once it's running. 

This is because it produces nasty memory leaks when rmmoding so the kernel devs "locked" the i915 module once its loaded. This might get fixed in the upcoming 2.6.38 but i havn't checked.

So the only way to switch vga's is to reboot.

If you want to use the nvidia vga there is no special action and acpi_call required. just use current maverick kernel and get the nvidia binary driver as described on the wiki.

The disadvantage is that the nvidia GT218  chip will draw a lot of power and shorten the battery life of your netbook to about 4 hours.

To save enery you can use the acpi_call module and use 2 calls to:
- enable the intel GMA3150 for next boot
- disable the nvidia chip

This method will double the battery life of the netbook. With turned off nvidia chip (and some other power tweaks) my Eee runs for approx 8 hours with normal surfing .

Unfortunately the acpi_call module triggers the kslowd bug in current maverick kernel so i used the kernel from lucid to work around this. 

A short howto:

1.) get the kernel image, headers and alsa modules (either the 32bit or amd64 version, depending on your install)
 

-32 bit
```
wget http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.32-28_2.6.32-28.55_all.deb
wget http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.32-28-generic_2.6.32-28.55_i386.deb
wget http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.32-28-generic_2.6.32-28.55_i386.deb
wget https://launchpad.net/~ubuntu-audio-dev/+archive/ppa/+files/linux-alsa-driver-modules-2.6.32-28-generic_2.6.32-28.201101311053_i386.deb
wget https://launchpad.net/~ubuntu-audio-dev/+archive/ppa/+files/linux-headers-alsa-driver-2.6.32-28-generic_2.6.32-28.201101311053_i386.deb
```

-64 bit
```
wget http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.32-28_2.6.32-28.55_all.deb
wget http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.32-28-generic_2.6.32-28.55_amd64.deb
wget http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.32-28-generic_2.6.32-28.55_amd64.deb
wget https://launchpad.net/~ubuntu-audio-dev/+archive/ppa/+files/linux-alsa-driver-modules-2.6.32-28-generic_2.6.32-28.201101311053_amd64.deb
wget https://launchpad.net/~ubuntu-audio-dev/+archive/ppa/+files/linux-headers-alsa-driver-2.6.32-28-generic_2.6.32-28.201101311053_amd64.deb
```

2.) install the deb's

cd into the folder where you downloaded the kernel packages and install them with 
```
sudo dpkg -i *.deb
```

3.) reboot in the new kernel, cd in the folder where you saved the acpi_call module and rebuild it for the current kernel:
```
cd /path/to/acpi_call
make clean
make 
sudo insmod acpi_call.ko
```

4.) now pass the 2 calls
```
sudo -s
echo "\OSGS 0x03" > /proc/acpi/call
echo "\_SB.PCI0.P0P4.DGPU.DOFF" > /proc/acpi/call
```

5.) check dmesg to see if it was successful
dmesg | grep acpi_call
```
[  532.962061] acpi_call: Module loaded successfully
[  535.966319] acpi_call: Calling \_SB.PCI0.P0P4.DGPU.DOFF
[  536.021541] acpi_call: Call successful: 0x0
[  536.021843] acpi_call: Calling \OSGS
[  536.024617] acpi_call: Call successful: 0x1
```


If it worked create a script to preform those steps automatically and configure grub to boot the 2.6.32-28 as default [grub-customizer]("https://launchpad.net/grub-customizer") makes this easy)

A very basic script for this would be:
```
#!/bin/bash
# Disabe Nvidia Chip and enable intel glx on Asus EeePC 1015pn

# check if we are root, else exit
if [[ $EUID -ne 0 ]]; then
	echo "This script needs to be run as root"
	exit 1
fi

# is the acpi module loaded?
if lsmod | grep -q acpi_call; then
	echo '\_SB.PCI0.P0P4.DGPU.DOFF' > /proc/acpi/call
	echo "\OSGS 0x03" > /proc/acpi/call
	#set intel xorg.conf
	cd /etc/X11
	cp xorg.conf.intel xorg.conf

	# fiddle with glx and libgl
	rm /usr/lib/xorg/extra-modules/libglx.so
	# fix: ln -s /usr/lib/xorg/extra-modules/libglx.so.260.19.29 /usr/lib/xorg/extra-modules/libglx.so
	update-alternatives --set gl_conf /usr/lib/mesa/ld.so.conf
	ldconfig
	exit 0
else
	cd /path/to/acpi_call
	insmod acpi_call.ko
	sleep 3
	echo '\_SB.PCI0.P0P4.DGPU.DOFF' > /proc/acpi/call
	echo "\OSGS 0x03" > /proc/acpi/call
	#set intel xorg.conf
	cd /etc/X11
	cp xorg.conf.intel xorg.conf
	# fiddle with glx and libgl
	rm /usr/lib/xorg/extra-modules/libglx.so
	update-alternatives --set gl_conf /usr/lib/mesa/ld.so.conf
	ldconfig
	exit 0
fi
```

edit the line /path/to/acpi_call to reflect the full path on your system. Also note that i have 2 xorg.conf files one for nvidia (named xorg.conf.nvidia) and the other one for intel (named xorg.conf.intel) see attachment... place them in /etc/X11

another script i use that might be useful to you is to check current power consumption. it queries /proc/acpi/battery/BAT0/state and uses notify-osd to display current power usage. if it's around 600-700 mA you've successfully turned off the nvidia chip

```
#!/bin/bash
POWER=$(grep rate /proc/acpi/battery/BAT0/state | cut  -c 25-32) && REMAINING=$(grep remaining /proc/acpi/battery/BAT0/state | cut  -c 25-34) && DISPLAY=:0.0 notify-send -t 6000 -i /usr/share/notify-osd/icons/gnome/scalable/status/notification-gpm-battery-100-charging.svg "Battery Information" "current power rate: $POWER \n remaining capacity: $REMAINING"
```

i use a keyboard shortcut to run the script with a keypress (use gnome-keybinding-properties for this)

Cheers and Good Luck!

---

### Post by barthus on 2011-01-31
mtron, thx for all this info.

Is it possible to choose the graphic card by just choosing the Kernel in the Grub menu? For example, if you want to use the nvidia choose entry No.1 otherwise entry No. 2. Is this possible?

---

### Post by mtron on 2011-01-31
yes, that should be possible (at least in theory) That's a good idea actually :)

in this case you need to create a init.d script that checks if you are running the 2.6.35 kernel and if yes, copies the xorg.conf.nvidia to xorg.conf, sets the glx symlink and updates ld.so.conf

I'll try to create the necessary scipt tomorrow and report here if i got this working. 

Cheers!

---

### Post by barthus on 2011-01-31
I have tried all what mtron told us on the top: I installed the Linux Kernel 2.6.32 into Maverick (now, I have the 2.6.35 and 2.6.32 one), executed the script and so on ... . During the last 3 days, I worked a lot with this Ubuntu Maverick 10.10 system (2.6.32 Kernel) AND ONLY WITH THE INTEL GPU and must recognise: **It's really a perfect and very nice system! I doubled the battery life, the netbook does not become hot, the display brightness is still okay under sunny conditions, etc.** - Thanks mtron.

So, what one has to do is to do all the steps mtron is describing on the top. And: If one always wants to work with the intel chip, one has always to execute the script after a boot. That's it.

By the way, I modified the script a bit (named Switch_intel.sh):

```

#!/bin/bash
# Disabe Nvidia Chip and enable intel glx on Asus EeePC 1015pn

# check if we are root, else exit
if [[ $EUID -ne 0 ]]; then
    echo "This script needs to be run as root"
    exit 1
fi

# is the acpi module loaded?
if lsmod | grep -q acpi_call; then
    echo "ACPI does not need to be loaded."    
else
    echo "ACPI needs to be loaded."    
    cd /path/to/acpi_call
    insmod acpi_call.ko
    sleep 3
fi

echo '\_SB.PCI0.P0P4.DGPU.DOFF' > /proc/acpi/call
echo "\OSGS 0x03" > /proc/acpi/call

# Set intel xorg.conf
cd /etc/X11
cp xorg.conf.intel xorg.conf

# Fiddle with glx and libgl
if [ -f "/usr/lib/xorg/extra-modules/libglx.so" ] 
then
    echo "libglx.so has been deleted"
    rm /usr/lib/xorg/extra-modules/libglx.so
fi

update-alternatives --set gl_conf /usr/lib/mesa/ld.so.conf
ldconfig

exit 0

```Don't forget to replace '/path/to/acpi_call' with the correct path. Execute the script with 'sudo Switch_intel.sh'




**Note 1:** For reading the current power consumption proposed by mtron one has to install libnotify-bin! However, one can also use:

```

cat /proc/acpi/battery/BAT0/state

```I measure the following mean values:

nvidia+intel: 1100mA - 1500mA
intel: 750 - 850 mA

**Note 2:** I have noticed that whenever you put your netbook to sleep (closing netbook) and then back to life, the
Nvidia chip is switched on again. Therefore, one has always to switch off the chip after having started the netbook. In this case, a

```

echo "\_SB.PCI0.P0P4.DGPU.DOFF" > /proc/acpi/call

```is sufficient.

---

### Post by gregb49 on 2011-02-04
**Dull Screen**
I have an Asus Eee PC 1015PEB which hasn't the Nvidia chip, mores the pity, but it was exceptionally good value. 

I get the same lsmod and lspci outputs as you but without this line> 04:00.0 VGA compatible controller: nVidia Corporation GT218 [ION] (rev a2)Mine is maybe a far more simple problem than yours. How do you get a screen as bright as under the installed Win7 and Puppy linux, under Ubuntu 10:10? The brightness keys, Fn F5 & F6 give strange variable results but the max brightness is below that of the other OS'.

---

### Post by barthus on 2011-02-04
Hi gregb49.

> **gregb49 said:**
> How do you get a screen as bright as under the installed Win7 and Puppy linux, under Ubuntu 10:10? The brightness keys, Fn F5 & F6 give strange variable results but the max brightness is below that of the other OS'.

Have a look here:

[https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#Asus%20Eee%20PC%201015PN](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#Asus%20Eee%20PC%201015PN)

There might be some info for you. For instance, for the 1015PN some stuff needs to be loaded. I hope that helps.

---

### Post by zylon on 2011-02-07
Hi barthus,

did you messure the power consumption with activated WIFI or without. 
Because i have, afer activation of the intel chip, a consumption of about 1.400mA but with active WIFI.

Greatings

---

### Post by barthus on 2011-02-07
> **zylon said:**
> 
did you messure the power consumption with activated WIFI or without. 
Because i have, afer activation of the intel chip, a consumption of about 1.400mA but with active WIFI.


The measurement is done in almost idle state without the power cable plugged in. With WIFI, I have about ~100mV more. However, this all strongly depends on the circumstances. This is why I have written: 750-900 mA. It seems that with 1400 mA you still have the intel switched on!  Did you use this command?

```
echo "\_SB.PCI0.P0P4.DGPU.DOFF" > /proc/acpi/call
```

---

### Post by zylon on 2011-02-07
well yes i thought i did it. Now i repeated the steps, and now i have with WIFI on about 800mA --> very fine!

Thanks a very lot for helping!!!

Greatings

---

### Post by barthus on 2011-02-08
**Edit: The script has been improved and the corresponding text changed, thanks to the help from [r_ed-flex_]("http://ubuntuforums.org/member.php?u=1242801"). ****(13/02/2011)**
**Edit No. 2: I updated the script, more details in message #1 (16/02/2011)**

Hi all.

After some 'experiments' I found somewhat a 'solution' for switching between the cards. However, you need to stay with the 2.6.32 Kernel and you need to install the restricted drivers for the nvidia again (only one time) after you have booted with the 2.6.32 Kernel. All seems to work nicely.

So, follow these steps:

1. Instructions of mtron (message #3): [http://ubuntuforums.org/showpost.php?p=10415693&postcount=3](http://ubuntuforums.org/showpost.php?p=10415693&postcount=3) (including step 3 but then stop)
2. Boot with the 2.6.32 Kernel and install via internet  the restricted drivers for the nvidia card.
3. Use the ones below. Check all paths, nvidia version numbers, etc.


*************** Start ***************

Here is what I always use for switching to the intel card before a boot - it is basically a modified script from mtron. (execute: sudo Switch_intel.sh) 

```

#!/bin/bash
# Enable intel glx on Asus EeePC 1015pn 

# Check if we are root, else exit
if [[ $EUID -ne 0 ]]; then
    echo "This script needs to be run as root"
    exit 1
fi

# is the acpi module loaded?
if lsmod | grep -q acpi_call; then
    echo "ACPI does not need to be loaded."    
else
    echo "ACPI needs to be loaded."    
    cd /home/cle/Switch
    insmod acpi_call.ko
    sleep 3
fi

# The call for the next time
echo ""
echo "Mode 1 is now set: After the next boot only the Intel chip is visible."
echo "\OSGS 0x01" > /proc/acpi/call

# Set intel xorg.conf
echo ""
echo "A xorg.conf file has been prepared such that the Intel chip can be used for X11."
cp /etc/X11/xorg.conf.intel /etc/X11/xorg.conf

echo ""
echo "The 'update-alternatives' has been set"
update-alternatives --set gl_conf /usr/lib/mesa/ld.so.conf
ldconfig

# Very important: fiddle with glx and libgl
if [ -f "/usr/lib/xorg/extra-modules/libglx.so" ] 
then
        echo ""
    echo "The library 'libglx.so' has been deleted."
    sudo rm /usr/lib/xorg/extra-modules/libglx.so
else
        echo ""
    echo "The library 'libglx.so' doesn't exist and must therefore not be deleted."
fi

echo ""
echo "Finished! Push a button ..."
read eingabe

```Replace 'path_to_acpi_call' with the correct path.


Here is what I use for switching to the nvidia card before a boot (execute: sudo Switch_nvidia.sh) 
```

#!/bin/bash
# Disabe Intel Chip and enable nvidia on Asus EeePC 1015pn

# Check if we are root, else exit
if [[ $EUID -ne 0 ]]; then
    echo "This script needs to be run as root"
    exit 1
fi

# is the acpi module loaded?
if lsmod | grep -q acpi_call; then
    echo "ACPI does not need to be loaded."    
else
    echo "ACPI needs to be loaded."    
    cd /home/cle/Switch
    insmod acpi_call.ko
    sleep 3
fi

# The system is prepared such that the nvidia card is onlt visible
echo ""
echo "Mode 2 is now set: After the next boot only the Nvidia chip is visible."
echo "\OSGS 0x02" > /proc/acpi/call

# Copy the libglx file into usr/lib/xorg/extra-modules/
# Without doing this, compiz does not work properly (I have no idea why) 
if ! [ -f "/usr/lib/xorg/extra-modules/libglx.so.260.19.06" ] 
then
   cp /usr/lib/nvidia-current/xorg/libglx.so.260.19.06 /usr/lib/xorg/extra-modules/
   chmod 644 /usr/lib/xorg/extra-modules/libglx.so.260.19.06
   echo ""
   echo "The libglx has been copied"
fi

# Copy also the nvidia_drv.so file into usr/lib/xorg/extra-modules/
# As above: compiz needs this (I have no idea why) 
if ! [ -f "/usr/lib/xorg/extra-modules/nvidia_drv.so" ] 
then
   cp /usr/lib/nvidia-current/xorg/nvidia_drv.so /usr/lib/xorg/extra-modules/
   chmod 644 /usr/lib/xorg/extra-modules/nvidia_drv.so
   echo ""
   echo "The nvidia_drv.so has been copied"
fi

# Set the intel xorg.conf
echo ""
echo "A xorg.conf file has been prepared such that the Nvidia chip can be used for X11."
cp /etc/X11/xorg.conf_nvidia /etc/X11/xorg.conf

update-alternatives --set gl_conf /usr/lib/nvidia-current/ld.so.conf
ldconfig
echo ""
echo "update-alternatives ... and ... ldconfig"

# Very important: The link 'libglx.so' needs to be created
if ! [ -f "/usr/lib/xorg/extra-modules/libglx.so" ] 
then
   ln -s /usr/lib/xorg/extra-modules/libglx.so.260.19.06 /usr/lib/xorg/extra-modules/libglx.so
   echo ""
   echo "The libglx link has been set"
else
   echo ""
   echo "The libglx link already exists"   
fi

echo ""
echo "Push a button ..."
read eingabe

```You need to search the right name for the lib 'libglx.so...' and 'nvidia_drv.so' in the /usr/lib/nvidia-current/xorg/ directory.
The xorg.files can be taken from mtron (see above).


********* That's it *********

**Notes (old, more details in message #1)**
1. Note that you have to execute always the script 'Switch_intel.sh' whenever you want to boot and use the intel card. In the case of the nvidia card you must execute the script 'Switch_nvidia' only once for all other following 'future boots' with the nvida card. 
2. In intel-mode: If the 1015PN is put to sleep and afterwards waken up (closing and opening the 1015PN), the nvidia must not be switched off!  
3. The scripts are written such you can call them from a starter of a panel. Don't forget to make the scripts executable.
4. There is some output text, which comments all operations and can be used to see what the system is doing. 
5. HDMI is perfectly working with Nvidia.

I hope that all this helps.

Cheers.

---

### Post by red-flex on 2011-02-12
I dont know if this is new, 
but i found out that you can directly boot using the intel chip only (nvidia ION is not visible at all)

in my case i just changed the acpi call command for the reboot:

echo "\OSGS** 0x01**" > /proc/acpi/call

(for optimus choose 0x03, for nvidia only 0x02)
after rebooting it is not necessary to switch off anything!

But can someone tell me why this acpi call module is not working with the new kernel?:confused:

---

### Post by barthus on 2011-02-13
Hi red-flex.

> **red-flex said:**
> I dont know if this is new, 
but i found out that you can directly boot using the intel chip only (nvidia ION is not visible at all)

in my case i just changed the acpi call command for the reboot:

echo "\OSGS** 0x01**" > /proc/acpi/call

(for optimus choose 0x03, for nvidia only 0x02)
after rebooting it is not necessary to switch off anything!

Thanks a lot for this very good comment! I could considerably improve the script, and now I can switch without any major problems between the cards. The system has become quite nice.

> **red-flex said:**
> 
But can someone tell me why this acpi call module is not working with the new kernel?:confused:
Well, I don't know. mtron says that it is due to a driver, which still needs some improvement. Look here:

[http://ubuntuforums.org/showpost.php?p=10414911&postcount=2](http://ubuntuforums.org/showpost.php?p=10414911&postcount=2)

Cheers.

---

### Post by barthus on 2011-02-13
Hi all.

I thought that this might be somewhat interesting for you: Thanks to the help of all others here in this thread, I could change the scripts such I can easily switch between the cards. The scripts are in message #12:

[http://ubuntuforums.org/showpost.php?p=10440845&postcount=12](http://ubuntuforums.org/showpost.php?p=10440845&postcount=12)

I hope that it is for some good use.

---

### Post by red-flex on 2011-02-13
Hey thanks for the scripts!

i had no time to test them, but they looks quite good.
but i saw one point which might be useful to improove:

a xorg.conf file is not obligatory necessary. i deleted mine, because there was no important information i wanted to set.
Of course its easy to delete those lines from the script :D, but maybe we can create a script which is working fine for everybody.

im am quite new to all this linux stuff, but acutally it should be possible to create a script which is always executed when ubuntu starts.

this script does nothing execpt loading the acpi module, sending the actual defined mode (for beeing sure that this mode is set for the next reboot) and unloading the module again.

If the you want to change the mode, a second script is started by the user. this prepares the pc for the new mode (like your switch_intel), but also writes the new mode in the booting script.

I would try to implement this on my own, but i am really busy at the moment. So if someone is bored ...:P
otherwise ill try to get this working in a few weeks. :)

---

### Post by barthus on 2011-02-13
Thanks. I will test this with the xorg files. 

Of course, it makes much sense to include all into the boot process. A good idea has been discussed recently: one uses the grub menu where the user chooses the graphic card. However, I'm also busy, and I must admit that I'm not really a big specialist in hacking the system. :D Well, in fact mtron wrote that he wants to change the boot. Since then, I'm waiting. Let's see ... cheers.

PS: I booted and switched the cards a dozen of times and: all is quite stable!

---

### Post by Draugen River on 2011-02-14
Followed the instructions above and it worked out very well. 
Soo thanks to you guys that has been working hard to find this solution and actually took time to share it with the rest of us.

Seems like its possible to run the script on halt and reboot, have not noticed any problems doing that...
Even using: Linux 1015PN 2.6.35-25-generic-pae #44-Ubuntu SMP Fri Jan 21 19:01:46 UTC 2011 i686 GNU/Linux

---

### Post by barthus on 2011-02-15
> **Draugen River said:**
> Followed the instructions above and it worked out very well. 
Soo thanks to you guys that has been working hard to find this solution and actually took time to share it with the rest of us.

Seems like its possible to run the script on halt and reboot, have not noticed any problems doing that...
Even using: Linux 1015PN 2.6.35-25-generic-pae #44-Ubuntu SMP Fri Jan 21 19:01:46 UTC 2011 i686 GNU/Linux

Nice to hear that! Do I have correctly understood: You use the 2.6.35 Kernel? - I will try that out later ... cheers.

---

### Post by barthus on 2011-02-15
Yes, the first tests show that it works indeed with the 2.6.35 Kernel (I have the 2.6.35-25 one). This is simply great and things get quite simple now!

Cheers.

PS: I will do some changes in my first contribution. (done, see first message)

---

### Post by mcstayinskool on 2011-02-16
I haven't found a root cause yet, but after I ran the Switch_intel.sh script and rebooted I couldn't get past the Ubuntu boot splash screen. 

I'm sure this was user error on my part, but if anyone else comes across this problem, here's the steps to fix:

1. Hold space bar down during boot to drop to a Grub menu
2. Select a recovery mode kernel for your boot option
3. You will be presented with a list of options in recovery mode. Select "drop to root shell"
4. Execute the Switch_nvidia.sh script
5. Reboot

This got me back to square 1, which for now is going to have to be enough. I'm excited to have a future option of switching to the intel graphics chip for battery saving goodness, but I'm going to wait for this to evolve a bit (and some needed kernel fixes to happen).

cheers,
#!/ben

---

### Post by barthus on 2011-02-16
> **mcstayinskool said:**
> I haven't found a root cause yet, but after I ran the Switch_intel.sh script and rebooted I couldn't get past the Ubuntu boot splash screen. 

I'm sure this was user error on my part, but if anyone else comes across this problem, 

Oh dear, you have probably taken the script from message #12. Then it's my mistake, the newest script is in message #1. I will change the script in #12 ...

If possible, try again and report. If there are errors copy&paste the output text during executing the code. Thx.

PS: Is your output like ?:
```
ACPI needs to be loaded.
Mode 1 is now set: After the next boot only the Intel chip is visible.
A xorg.conf file has been prepared such that the Intel chip can be used for X11.
The 'update-alternatives' has been set
The library 'libglx.so' doesn't exist and must therefore not be deleted.
Finished! Push a button ...

```

---

### Post by mtron on 2011-02-17
Thanks barthus for fixing the script. it was knocked together without much thinking ;)

Anyways, Sorry for the late reply but analog life came in the way... 

I have created a new set of scripts to make the gpu switching more user friendly. 

You can choose your gpu for the next boot via a simple gui script and it does not require root password any more. The actual acpi_call is send during shutdown or reboot.

Also i have packed the acpi_call kernel module in a dkms deb file (It's included in the zip). This means that it will auto rebuild for all installed kernels.  


[SIZE="4"]Provided scripts[/SIZE]

**1. display-settings**

This script is installed in /usr/local/bin/display-settings and hosts all the acpi_calls & functions and needs to be called as root (or with sudo)

Following Options are provided:

> **display-settings auto**
In this mode the script will look for a .vga-selector file in the local users homedirs (if it finds multiple files the newest will be used) and executes the acpi_call for the desired option (Intel,Nvidia or Optimus mode) and will prepare the xorg configuration for the next boot. If it does not find any .vga-selector file it will default to Intel mode.

**display-settings status**
This will output current VGA Mode. E.g "Active GPU: Intel GMA3150 on PCI 00:02.0"

**display-settings reboot-intel**
activate intel for next boot and prepare xorg conffiles for intel. The nvidia chip won't be visible via lspci and is disabled so it won't draw any power from the battery.

**display-settings reboot-nvidia**
activate nvidia for next boot and prepare xorg conffiles for nvidia. The intel chip won't be visible via lspci.

**display-settings reboot-optimus**
activate both gpu's for next boot and prepare xorg conffiles for intel. NOTE: intel/nvidia hot-switching is currently not possible!

**display-settings powersave**
For Optimus Mode only! This will disable the nvidia chip to save some enery. NOTE: intel/nvidia hot-switching is currently not possible!

**display-settings config-intel**
This option is for emrgency purposes. If xorg can't start and you are dropped to a text shell after boot fix your configuration by running "display-settings status". If you get "Active GPU: Intel GMA3150" run this Option and restart gdm.

**display-settings config-nvidia**
This option is for emrgency purposes. If xorg can't start and you are dropped to a text shell after boot fix your configuration by running "display-settings status". If you get "Active GPU: Nvidia GT218" run this Option and restart gdm.

**2. zenity-vga-select**

this script should be placed in $HOME/scripts/zenity-vga-select. When called it provides the user the option to choose the vga mode for the next boot and writes this choice in the hidden file $HOME/.vga-selector

**3. vga-selector shutdown script**

This simple init script is copied to /etc/init.d/vga-selector and triggers "display-settings auto" (see above) during shutdown and reboot. If there is no user-set .vga-selector choice available it will default to intel mode. 


[SIZE="4"]How it works:[/SIZE]

The user opens the zenity-vga-select script and chooses the vga for the next boot. The zenity scripts writes this selection to the temporary file ~/.vga-selector. 

During shutdown or reboot (early in runlevel 0 and 6) the init-script /etc/init.d/vga-selector triggers the display-settings script in "auto" mode. 

The script will look for a .vga-selector file in the users homedirs (if it finds multiple files the newest will be used) and execute the acpi_call for the desired option. Also it will prepare the xorg and glx configuration for the next boot.


[SIZE="4"]Installation[/SIZE]

there is now a deb package for easy un-/installation available! see [post #61]("http://ubuntuforums.org/showpost.php?p=10556760&postcount=61")

---

### Post by barthus on 2011-02-17
> **mtron said:**
> Thanks barthus for fixing the script. it was knocked together without much thinking ;)
Anyways, Sorry for the late reply but analog life came in the way... 
I have created a new set of scripts to make the gpu switching more user friendly. 

Good, I will put a comment into message No. 1. 

So far, my scripts work perfectly without a single problem. I will try yours over the weekend. Summarizing, the switching can be indeed considered as to be solved for the 1015PN. This is why I marked the thread 'as solved'.

Cheers.

PS: I had just a look into your scripts and recognized that you have done some big work! :-)

---

### Post by red-flex on 2011-02-22
great stuff mtron!
thanks a lot for this script :-)! I'll try it the next few days!

---

### Post by mtron on 2011-02-22
cool . Feedback appreciated ;)

I have updated the ubuntu wiki page for the [Eee PC 1015PN]("https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#Asus Eee PC 1015PN") with the findings in this thread, so please have a look if i messed something up.

If anyone could test HDMI audio and video out (maybe [http://ubuntuforums.org/showpost.php?p=10390615&postcount=2](http://ubuntuforums.org/showpost.php?p=10390615&postcount=2) works) and add the necessary steps to get alsa/pulseaudio working with hdmi it would be great.

---

### Post by Etienne63 on 2011-02-23
Hello everyone,

Tanks a lot for these scripts, the switching to intel works perfectly on my 1015PN, but I still a problems with the nvidia ion.
Actually, even before I try the switching, the screen was messed up when I activate the nvidia drivers in ubuntu "Hardware drivers".

It is not a real problem for me because I use ubuntu mostly for programming so the intel GMA is enough for my usage of ubuntu. (I kept windows to play games or HD videos with the ION)

So, finally my question is:
How do I do to use only the intel GMA for ubuntu? or at least make it the default choice if no script had been run before the last shutdown.

Thanks in advance

---

### Post by mtron on 2011-02-24
> How do I do to use only the intel GMA for ubuntu?

If you are using the display-settings script:
```
sudo display-settings reboot-intel
```

Or manual:
```
echo "\OSGS 0x01" > /proc/acpi/call
```

This will enable the Intel Cip and disables the Nvidia chip totally (also the nvidia chip won't consume any power) 

> or at least make it the default choice if no script had been run before the last shutdown.

Again, if you use my latest scripts and make no selection with the zenity script it will default to intel. 

So if you want to boot to nvidia use the zenity script to select nvidia or just:
```
echo "nvidia" > $HOME/.vga-selector
```

Then reboot.

---

### Post by Etienne63 on 2011-02-24
I have a weird error when I want to put the valu in /proc/acpi/call


bash: /proc/acpi/call: No such file or directory


even if I'm in root, there is the same error, so even root seems to not have the permission to create the file /proc/acpi/call... :confused:

Any idea on how I can force the creation of this file?

---

### Post by mtron on 2011-02-24
you need to load the acpi_call.ko kernel module.

install [acpicall-dkms_0.1_all.deb]("http://ubuntuone.com/p/dil/") and run:
```
sudo insmod /lib/modules/$( uname -r )/kernel/drivers/acpi/acpi_call.ko
```

or to load it automatically during boot add the line "acpi_call" to /etc/modules.

After loading, check dmesg output to read the hopefully good news ;)

---

### Post by Etienne63 on 2011-02-24
Thanks a lot, it worked.

But a new problem appeared, it seems that the intel is not fully functional (I cannot activate the visual effects, even the normal while I could before when I was under the intel).

Do I have to install drivers for the intel chip?

---

### Post by BenoitL03 on 2011-02-25
I try to re-work the scripts to apply them on Debian but there is no "/usr/lib/nvidia-current/ld.so.conf" and no alternatives for gl_conf.
Have you got a idea to solve it?


And about Etienne63's message Ithink it's a problem of GL library.
Can you try to launch compiz (compiz --replace ) in a terminal and post the result

---

### Post by barthus on 2011-02-26
I also had some problems with these libs from GL library etc. until I found out by try-and-error that one has to copy some libs always during switching. 
You can see it in the 2 scripts of message No #1 (first 2 scripts, at the end). With these scripts I have no problem at all. Compiz, which is important for the visual effects, is quite well working.

So, may be, the lines dealing with the libs can be included somewhere into mtrons scripts. However, I have no idea where. What do you think, mtron? :o

---

### Post by BenoitL03 on 2011-02-26
First thank you for your answer.

I analysed the script but the problem is that the way to install NVIDIA driver is different for Debian, I took it on the official website. So there is no "/usr/lib/nvidia-current/xorg/..." but I found a equivalent for that.
I think I just have one problem left which is the update-alternatives of gl_conf which don't exist "there isn't alternative ...)

:/

---

### Post by Etienne63 on 2011-02-26
Here is the result:

```
etienne@1015PN:~$ compiz --replace
Xlib:  extension "GLX" missing on display ":0.0".
compiz (core) - Fatal: Root visual is not a GL visual
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0

Launching fallback window manager
```

And also the output of lspci when I'm on intel graphics mode, if it can help.

```

00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge (rev 02)
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller (rev 02)
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02)
01:00.0 Ethernet controller: Atheros Communications Atheros AR8132 / L1c Gigabit Ethernet Adapter (rev c0)
02:00.0 Network controller: Broadcom Corporation Device 4727 (rev 01)
```

---

### Post by BenoitL03 on 2011-02-26
I will post the issue tomorrow ^_^' I'm working on and tired

---

### Post by stronkyz on 2011-02-27
hi to all,
i have a eeepc 1015pn :)
when i activate the intel gma and reboot, ubuntu start as a terminal...
these procedures are for only the kernel you have linked in the 3rd post or for all?

---

### Post by barthus on 2011-02-27
It seems that we all do not use same type of Linux distribution (see BenoitL03: Debian), so lets always mention what one uses.

Etienne63, this is what I have seen also before fixing the Compiz problem in my case. If you use Ubuntu 10.10, the first two scripts in message 1 should help. However, note that my scripts are independent on what mtron has created in message #23.

Stronzky, the 3rd message contains old stuff. Either you use my scripts (see message No. #1) or you use the stuff from mtron (message #23). My scripts are working perfectly well.

---

### Post by stronkyz on 2011-02-27
ok but when i start your intel script my pc reboot as a terminal
what i can do?
( i have also installed mtron stuff  )

P.S. how i can make the script executable?

---

### Post by barthus on 2011-02-27
> **stronkyz said:**
> ok but when i start your intel script my pc reboot as a terminal
what i can do?
( i have also installed mtron stuff  )

P.S. how i can make the script executable?

1. Do not mix mtrons stuff with my scripts ! Once installed mtrons scripts the boot is constantly changed. My scripts do not change anything permanently in the boot sequence. So, either you take only my scripts or the the stuff from mtron. 
We all hope that mtrons scripts will be at one level, where everything works quite well and where my scripts are not needed anymore. 
2. I see now what your problem is: So, when you are again in a shell execute the intel script. Then boot and it should work. - I rarely boot my linux system and I forgot to mention that one has to activate the intel script in a shell after one switched off-on the computer. Sorry.
4. Open the nautilus explorer, search the script, mark it with the mouse and push the right mouse button. Go into the menu and chose properties. There you find somewhere an option where it says executable. Activate this option.

---

### Post by stronkyz on 2011-02-27
when i reboot, my pc doesn't charge gnome but it's in terminal mode
what i can do to charge gnome UI?

but with the mtron script happens the same thing?
sorry for my english :)

---

### Post by barthus on 2011-02-27
> sorry for my english :smile:No problem. I understand everything. 8)

> **stronkyz said:**
> when i reboot, my pc doesn't charge gnome but it's in terminal mode what i can do to charge gnome UI?
When you are in the terminal mode, go to the directory where the script 'Switch_intel.sh' is located. Then, type:

```

sh ./Switch_intel.sh

``` Reboot after. Your system should then boot into the intel mode. BTW: post the output of the latter command here into this forum. Thx. 

> but with the mtron script happens the same thing?So please, before all: What have you done? Did you already install mtrons scripts via this deb file or are you using other scripts only (2 scripts from message #1)? 

The more precise you are the more we understand and the better we can help.

---

### Post by stronkyz on 2011-02-28
ok finally i understand :)
it's work 
thanks a lot!!! :)

---

### Post by barthus on 2011-02-28
> **stronkyz said:**
> ok finally i understand :)
it's work 
thanks a lot!!! :)
Good. So you used only my scripts?

---

### Post by stronkyz on 2011-02-28
yes :)
another question :)
how i can make long the battery life?
(sorry for the OT :) )

---

### Post by mtron on 2011-03-01
> **barthus said:**
> Once installed mtrons scripts the boot is constantly changed 

No, the scripts change nothing at the boot up sequence. Only at shutdown the display-settings script sets the gpu (and prepares the config) for the next boot.
 
> **barthus said:**
> We all hope that mtrons scripts will be at one level

Is there anything missing / not working for you? If so i'll try my best to fix it but it's working very nice for me here.

---

### Post by mtron on 2011-03-01
> **BenoitL03 said:**
> I try to re-work the scripts to apply them on Debian but there is no "/usr/lib/nvidia-current/ld.so.conf" and no alternatives for gl_conf.
Have you got a idea to solve it?

Hello! 

/usr/lib/nvidia-current/ld.so.conf just points ld to the nvidia libs. on debian the proper path is /usr/lib/nvidia/.For squeeze you might want to use the helper scripts provided by the packages "libgl1-nvidia-alternatives" and "libglx-nvidia-alternatives" to do this.

I'm not sure about your second question (have not used debian since 2004) but "update-alternatives --config gl_conf" just sets the proper paths for the nvidia libs as provided by ld.so.conf, so if you use the native debian helper scripts from above there should be no need to fiddle with this.

---

### Post by barthus on 2011-03-01
> **mtron said:**
> Is there anything missing / not working for you? If so i'll try my best to fix it but it's working very nice for me here.

I tried once but it was done in a hurry somehow. I remember that I couldn't start the X server. I will try again the next days. 

When I used your first scripts I had problems with Compiz during switching from one card to the other one via a boot. I found out that one needs to copy some libraries when going to the Ion card. Do you work with Compiz and do you deal somehow with the libs for compiz?

---

### Post by barthus on 2011-03-01
> **stronkyz said:**
> 
another question :)
how i can make long the battery life?
(sorry for the OT :) )

What do you mean? By using the intel graphic chip you consume already ~half of the power.

---

### Post by Draugen River on 2011-03-01
Have had the earlier version of this working for a few weeks now untill I allowed for todays system update...
Along with that the nvidia libglx.so.270.29 driver arrived and kinda broke my system a bit.... Im no longer able to get any further than the splash window when booting in nvidia mode. It also stops me from doing much else but reboot... Switched back to intel now, but I would like to go back to the earlier nvidia driver or know if you have the same problems?

---

### Post by barthus on 2011-03-01
> **Draugen River said:**
> Have had the earlier version of this working for a few weeks now untill I allowed for todays system update...
Along with that the nvidia libglx.so.270.29 driver arrived and kinda broke my system a bit.... Im no longer able to get any further than the splash window when booting in nvidia mode. It also stops me from doing much else but reboot... Switched back to intel now, but I would like to go back to the earlier nvidia driver or know if you have the same problems?

How have you installed the nvidia driver? By yourself via downloading the driver from the nvidia homepage or via the Ubuntu repository? Do you use mtrons last scripts?

---

### Post by barthus on 2011-03-01
Are you sure about the 270 driver for the ION? On the nvidia homepage, I couldn't find any:

[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

There is only the 260.19.36 one. :confused:

---

### Post by mtron on 2011-03-01
> **barthus said:**
> Do you work with Compiz and do you deal somehow with the libs for compiz?


Sure, compiz works nice with both intel and nvidia if the right libglx.so is loaded by xorg

You can check the used libglx.so by looking in the server log (/var/log/Xorg.0.log

Have a look in the "install" script from the zip. 

It copies the nvidia glx from /usr/lib/nvidia-current/xorg/libglx.so to /usr/lib/xorg/modules/extensions/libglx.so.nvidia

and the mesa libglx (used by the intel driver) from /usr/lib/xorg/modules/extensions/libglx.so to /usr/lib/xorg/modules/extensions/libglx.so.intel
 
Then the script removes the mesa glx /usr/lib/xorg/modules/extensions/libglx.so and the nvidia glx file from /usr/lib/xorg/extra-modules/libglx.so (it is copied there by the nvidia installer and xorg priorizes files in the extra-modules directory, so it will always load the nvidia glx lib from there if it's present)

After this is done we have both glx libs in the correct place:

Nvidia: /usr/lib/xorg/modules/extensions/libglx.so.nvidia
Intel: /usr/lib/xorg/modules/extensions/libglx.so.intel

so, depending on the selected gpu for the next boot the display-settings script symlinks the needed glx lib libglx.so.nvidia or libglx.so.intel to /usr/lib/xorg/modules/extensions/glx.so

I hope you understood this :) after all it's pretty easy once you understand the logic behind this.

---

### Post by mtron on 2011-03-01
> **Draugen River said:**
> 
Along with that the nvidia libglx.so.270.29 driver arrived and kinda broke my system a bit.... Im no longer able to get any further than the splash window when booting in nvidia mode. 

I'm also using the same version (@ barthus: you can grab the driver from the x-swat ppa ... see the wiki) without any problem.

If you updated, just run the "install" script from the Eee1015_acpitools-0.1.zip again. It will copy the nedded (updated) libglx file in the expected place and should hopefully fix your problem.

If not, please provide the relevant Xorg logfile. It is either /var/log/Xorg.0.log for the current session, or /var/log/Xorg.1.log for the previous one. Easiest might be to open /var/log and put all Xorg.*.log files in an archive and attach it here.

---

### Post by barthus on 2011-03-01
I see the point with the libs, okay.

> **mtron said:**
> I'm also using the same version (@ barthus: you can grab the driver from the x-swat ppa ... see the wiki) without any problem.

Oh, I didn't know this. But, there is a driver higher than the one nvidia proposes itself on their site? Who is programming these higher drivers then?

---

### Post by mtron on 2011-03-01
probably they just publish stable drivers on their website. version 270.29 is the current beta release.

For linux best place to keep up-to-date with nvidia is the Linux section of the nvnews form. Many talented Programmers, kernel hackers and nvidia devs hang out there.

[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

---

### Post by Draugen River on 2011-03-01
Sorry for a little informative post... I will try a bit more when im off the GRPS connection again.
Would however issue a slight warning when it comes to uninstall the acpitools, I did it twice just to make sure it worked...
Looking at the script its kinda obvious that was not very clever... It will delete the  /usr/lib/xorg/modules/extensions/libglx.so file and I had to reinstall the xserver-xorg-core package to restore.

---

### Post by mtron on 2011-03-02
look at the install script once again ;)

during install the mesa libglx is copied from libglx.so to libglx.so.intel

so when using the display-settings script libglx.so is a symlink pointing either to libglx.so.intel or libglx.so.nvidia.

during uninstallation you delete the libglx.so symlink and copy the libglx.so.intel back to its original name and location.

So if it really does not work for you (i tested it here and it did work for me...) its not related to libglx. please provide your xorg logfile to see whats going on at your Eee

---

### Post by Draugen River on 2011-03-03
My problems where most likely caused by me messing up. After some trial and error I ran the Addtional Drivers from the menu, and enabled the nvidia driver that now was greyed out. After rebooting it worked just fine.

My Xorg file ended like this:
[    41.343] (II) Loading extension DRI2
[    41.343] (II) LoadModule: "nvidia"
[    41.343] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    41.344] (II) Module nvidia: vendor="NVIDIA Corporation"
[    41.345]     compiled for 4.0.2, module version = 1.0.0
[    41.345]     Module class: X.Org Video Driver
[    41.345] (II) NVIDIA dlloader X Driver  270.29  Wed Feb 23 16:18:22 PST 2011
[    41.345] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    41.345] (--) using VT number 7

[    41.373] (EE) No devices detected.
[    41.373] 
Fatal server error:
[    41.373] no screens found
[    41.373] 
Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 
[    41.373] Please also check the log file at "/var/log/Xorg.3.log" for additional information.
[    41.373] 

Not sure what that indicates, but it is however working now.

(But if you run the uninstall script twice on row you will wipe out the libglx.so...)
Another thought: I have encrypted my home dir during install. This probably will restrict access to the  .vga-selector file in the case where I boot but do not log in before shutdown. Whould it be better to put this file somewhere else... I have put mine in the /usr/src folder just for now.

---

### Post by mtron on 2011-03-03
well, of course if you run the uninstall instructions twice it won't do any good, but you shouldn't have a reason to do this anyway...

regarding encrypted homedisks: for this you might want to move the .vga-selector file to /tmp. to do this edit the display-settings script and remove the userhome function, hardcode $dirname to /tmp and in the script actions remove "userhome" from auto mode. This should do it. (if you want to use the zenity gui don't forget to edit this as well. should be self explaining) 

this is not very elegant but every user should have read/write support in the /tmp diretory. /usr/src is not writable by a normal user so this location is not optimal either.

if you got root access anyway, just call the display-settings script directly. e.g

to activate intel & prepare the config
sudo display-settings boot-intel

and for nvidia
sudo display-settings boot-nvidia

read the instructions i posted on page 2 ;)

---

### Post by mtron on 2011-03-13
hello!

over the weekend i have prepared a deb package for easy installation and uninstallation of the EeePC 1015PN vga switching script.

so the current steps to utilize both chips are:

- install the maverick (or natty) desktop version (i use the amd64 variant)
- go through the Eee-fixes checklist on the [wiki]("https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#Asus Eee PC 1015PN") (not needed for natty)
- install the build-essential and kernel-header packages
- install the nvidia binary driver as described on the [wiki]("https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#Asus Eee PC 1015PN")
- download the [acpicall-dkms_0.1_all.deb]("http://ubuntuone.com/p/dil/") kernel module and install it with 
```
sudo dpkg -i acpicall-dkms_0.1_all.deb
```
- **Maverick** 10.10 only : download the [acpitools_0.2_all.deb]("http://ubuntuone.com/p/h1a/") Package and install it with 
```
sudo dpkg -i acpitools_0.2_all.deb
```
- **Natty** 11.04 only : download the [acpitools_0.3_all.deb]("http://ubuntuone.com/p/pPr/") Package and install it with 
```
sudo dpkg -i acpitools_0.3_all.deb
```

after the install go to "Applications -> System Tools -> Vga Selector" and choose the desired vga mode for the next boot.

If you reboot without using the vga selector gui the script will default to intel mode.

the script has more options when called from a terminal with
```
sudo display-settings <option>
```

where <option> is one of the following:

> **auto**
In this mode the script will look for a .vga-selector file in the local users homedirs (if it finds multiple files the newest will be used) and executes the acpi_call for the desired option (Intel,Nvidia or Optimus mode). it will also prepare the xorg configuration and glx libraries for the next boot. If the script can't find any .vga-selector file it will default to Intel-only mode.

**status**
This will output current VGA Mode. E.g "Active GPU: Intel GMA3150 on PCI 00:02.0"

**fix**
This will fix the glx libraries after the install of a new nvidia driver version. 

**reboot-intel**
activate intel for next boot and prepare xorg conffiles for intel. The nvidia chip will be disabled and won't be visible via lspci (so it won't draw any power from the battery)

**reboot-nvidia**
activate nvidia for next boot and prepare xorg conffiles for nvidia. The intel chip won't be visible via lspci.

**reboot-optimus**
activate both gpu's for next boot and prepare xorg conffiles for intel. NOTE: intel/nvidia hot-switching is currently not possible!

**powersave**
For Optimus Mode only! This will disable the nvidia chip to save some enery. NOTE: intel/nvidia hot-switching is currently not possible!

**config-intel**
This option is for emergency purposes. If xorg can't start and you are dropped to a text shell after boot fix your configuration by running "display-settings status". If you get "Active GPU: Intel GMA3150" run this Option and restart gdm.

**config-nvidia**
This option is for emergency purposes. If xorg can't start and you are dropped to a text shell after boot fix your configuration by running "display-settings status". If you get "Active GPU: Nvidia GT218" run this Option and restart gdm.

For more information how this script works see [this post]("http://ubuntuforums.org/showpost.php?p=10467121&postcount=23") from page 2.

I have also created a webpage with full install instructions [here]("http://mtron.co.nr/howtos/eeepc-1015pn") hopefully this makes the whole procedure much easier. :D

---

### Post by darkjh on 2011-03-20
im using ASUS N82, also a notebook with OPTIMUS. Can i use these scripts on my 10.04 ubuntu to switch the graphic card&#65311;

---

### Post by foutes on 2011-03-20
> **mtron said:**
> hello!

over the weekend i have prepared a deb package for easy installation and uninstallation of the EeePC 1015PN vga switching script.

so the current steps to utilize both chips are:

- install the maverick desktop version (i use the amd64 variant)
- go through the Eee-fixes checklist on the [wiki]("https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#Asus%20Eee%20PC%201015PN")
- install the build-essential and kernel-header packages
- install the nvidia binary driver as described on the [wiki]("https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#Asus%20Eee%20PC%201015PN")
- download the [acpicall-dkms_0.1_all.deb]("http://ubuntuone.com/p/dil/") kernel module and install it with 
```
sudo dpkg -i acpicall-dkms_0.1_all.deb
```- download the [acpitools_0.2_all.deb]("http://ubuntuone.com/p/h1a/") Package and install it with 
```
sudo dpkg -i acpitools_0.2_all.deb
```after the install go to "Applications -> System Tools -> Vga Selector" and choose the desired vga mode for the next boot.

If you reboot without using the vga selector gui the script will default to intel mode.

the script has more options when called from a terminal with
```
sudo display-settings <option>
```where <option> is one of the following:



For more information how this script works see [this post]("http://ubuntuforums.org/showpost.php?p=10467121&postcount=23") from page 2.

I have also created a webpage with full install instructions [here]("http://mtron.co.nr/howtos/eeepc-1015pn") hopefully this makes the whole procedure much easier. :D


Just wanted to give a big THANKS!! for your work.

I have the 1215n and thanks to this thread I now have 7 hours battery life instead of 4:15.

This little net book rocks with 64 bit and now has great battery life to boot!!!!

---

### Post by mtron on 2011-03-21
@ darkjh: No idea. but most probably not. you could check the same stuff i'm asking foutes (see below)

@ foutes: Wow. i'm very surprised this works on other netbooks than the EeePC 1015PN. Could you please provide some more info for others?

e.g. i guess you used the acpi_call deb kernel module so please test the following:

After reboot open a terminal and type 
```
sudo modprobe acpi_call
```

post the new dmesg output after this. easiest is to open another terminal window and in this window use "dmesg | tail -f" to constantly monitor dmesg.

Now back in the first terminal switch to root (sudo -s) and type
```
echo "\OSGS 0x01" > /proc/acpi/call 
```

and again post the dmesg output. After a reboot only the intel card should be active. Same for those commands:

```
echo "\OSGS 0x02" > /proc/acpi/call
echo "\OSGS 0x03" > /proc/acpi/call
```

Also the output of this acpi call is interesting:
```
echo "\AMW0.DSTS 0x90013" > /proc/acpi/call
```

this will tell us what acpi calls your netbook supports. Just for completeness, please also attach the output of "lspci -v" after echo "\OSGS 0x03" > /proc/acpi/call and a reboot (this should switch to dual gpu (optimus) mode.

---

### Post by darkjh on 2011-03-21
OH i tried the script, and ubuntu boots into black screen..
What can i do?

---

### Post by mtron on 2011-03-21
well it was never supposed to work on a ASUS N82, so no surprise it did not work.

boot with the grub recovery mode, drop to a root shell and uninstall the debs with

sudo dpkg -r acpicall-dkms acpitools 

now reboot again with recovery mode and choose "safe graphics mode".

---

### Post by foutes on 2011-03-21
> **mtron said:**
> @ darkjh: No idea. but most probably not. you could check the same stuff i'm asking foutes (see below)

@ foutes: Wow. i'm very surprised this works on other netbooks than the EeePC 1015PN. Could you please provide some more info for others?

e.g. i guess you used the acpi_call deb kernel module so please test the following:

After reboot open a terminal and type 
```
sudo modprobe acpi_call
```post the new dmesg output after this. easiest is to open another terminal window and in this window use "dmesg | tail -f" to constantly monitor dmesg.

Now back in the first terminal switch to root (sudo -s) and type
```
echo "\OSGS 0x01" > /proc/acpi/call 
```and again post the dmesg output. After a reboot only the intel card should be active. Same for those commands:

```
echo "\OSGS 0x02" > /proc/acpi/call
echo "\OSGS 0x03" > /proc/acpi/call
```Also the output of this acpi call is interesting:
```
echo "\AMW0.DSTS 0x90013" > /proc/acpi/call
```this will tell us what acpi calls your netbook supports. Just for completeness, please also attach the output of "lspci -v" after echo "\OSGS 0x03" > /proc/acpi/call and a reboot (this should switch to dual gpu (optimus) mode.


I will post this later tonight or in the morning,

The gui scripts to switch gpu's does not work for me.
I have to open treminal and 

```

cd  acpi_call

```then
```

sudo insmod acpi_call.ko

```then
```

./asus1215n.sh off

```whuch gives me
```

linus@linus:~/acpi_call$ sudo ./asus1215n.sh off
_DSM {0x59, 0x00, 0x00, 0x11}
_PS3 0x0
P3MO 0x0
DGPS 0x1
_PSC 0x3
Asus 1215N Optimus appears to be off

```and battery remaining doubles but after restart or after hibernate I have to run above commands to turn off ION.

---

### Post by mtron on 2011-03-22
ok, thanks for the info.

You don't need to run any of the commands i wrote about the previous post. they will all fail ;)

if you want to run your script automatically after coming back from sleep put it in /etc/pm/sleep.d/ . Quoting the manpage:

> /etc/pm/sleep.d
Programs in these directories (we call them hooks) are combined and
executed in C sort order before suspend and hibernate with as argument ´suspend´ or ´hibernate´. Afterwards they are called in reverse order with argument ´resume´ and ´thaw´ respectively.

so look at the provided example script and adjust it to your needs.

---

### Post by darkjh on 2011-03-25
I redo the system and i just want to disable the nvidia card on my N82 (GT335) when im using linux. I tried sometime myself but no result and have broken my system one time, any help on this? 
Just disable the very-hot nvidia card and use the intel chips....

Ubuntu 10.04, on wubi installation, just clean system right now no changes made

---

### Post by marcussive on 2011-04-03
hi, I am new to linux. I have an Asus N53J and have tried to install/run these scripts. when I run the script from the command line with 'status' argument:```
   sudo display-settings status
```
 the output is: No useable output found.

Please help. THanks,
Crag

---

### Post by mtron on 2011-04-04
The debs and scripts in this thread are written for the Asus **_EeePC 1015PN_**. 

No other Models of the EeePC are supported and i don't intend to extend the support for more Laptops.

Please open new threads for your problems because they have nothing to do with the subject.

---

### Post by barthus on 2011-04-04
Hi mtron.

You have done some great work! I updated my first message, which includes now a note with a link to your recent development (message #61). I hope that the people drop onto this message at once.

Cheers!

---

### Post by barthus on 2011-04-04
> **marcussive said:**
> hi, I am new to linux. I have an Asus N53J and have tried to install/run these scripts. when I run the script from the command line with 'status' argument:```
   sudo display-settings status
``` the output is: No useable output found.

Please help. THanks,
Crag

As mtron says, the scripts published in this thread are only for the Asus Eee PC 1015PN.

What concerns the VGA and HDMI output of Nvidia graphic cards, the program 'disper' can be used. On my 1015PN, it works perfectly!

[http://willem.engen.nl/projects/disper/](http://willem.engen.nl/projects/disper/)

---

### Post by mtron on 2011-04-05
thanks for getting into the hdmi stuff barthus! As soon as i get my hands on a hdmi display device i will give disper a try.

i have received some positive feedback from users so the vga switching scripts seem to work pretty reliable :D

---

### Post by unaigs on 2011-04-05
Thanks!!
Perfect on Maverick, but dual gpu is not working on Natty.

---

### Post by mtron on 2011-04-06
> dual gpu is not working on Natty

No time to testdrive natty just now, sorry :(  I'll give it a go next week.

---

### Post by barthus on 2011-04-06
> **mtron said:**
> No time to testdrive natty just now, sorry :(  I'll give it a go next week.

Funny ... :P

---

### Post by barthus on 2011-04-06
Ah, finally, I found some time for some small talk ... :

The last weeks I saw a couple of net-books and most of them were running Windows 7 Starter and all this kind of stuff.
I always need to grin since with Windows the net-books are sooooo awful slow: Lame ducks! 

In comparison Linux/Ubuntu Maverick on the PN1015 is sooo fast. :guitar:

VGA or HDMI and disper: I gave already some talks by using Oo and a video projector, it is simply a pleasure! Colleagues always wonder why Linux on this machine is so fast and why it has no problems with a video projector. 

So you all change to Unity? Or do you stay with the GNOME shell?

---

### Post by Nisitiiapi on 2011-04-06
Thanks barthus and mtron for all your work.  I've been trying to set  up my new 10105PN with the debs from mtron and it seems to be failing.  I've followed mtron's instructions each time, but end up in the same place each time with the nvidia option not working.  Here's what I've done and where things end up:

-install ubuntu desktop x64 and all updates
-install the latest nvidia driver from x-swat (everything's good and the nvidia driver is used)
-blacklist the nouveau and nv drivers
-install acpicall-dkms_0.1_all.deb (modprobe reports loaded successfully)
-install acpitools_0.2_all.deb

When I select to restart with nvidia, I reboot, check the status using display-settings and it tells me the Intel chip is in use and the output of lspci doesn't show any nvidia chipset at all.  (Of course, the Additional Drivers GUI doesn't show any nvidia option either and the nvidia settings won't start up).  Same if I use the optimus option.

The xorg.conf.nvidia and xorg.conf.intel files are created.  When I try the manual method, same result.

Is there some step I'm missing?  Is there still an issue with using the newest kernel (2.6.35-28)?

Thanks in advance for any help.

---

### Post by mtron on 2011-04-07
Are you using an encrypted homedrive / totally encrypted system? The gui script won't work then. 

If only the intel vga is active and visible via lspci it means that the switching by itself works but the auto triggered shutdown script can't find any useable .vga-selector file in your homedir and thus defaults to intel only mode to save power. 

If you want to use nvidia instead of intel as default vga you just need to change 1 line in the display-settigns script. 

So to resolve your issue try the following:
- do a normal boot and run "sudo display-settings reboot-nvidia" from a terminal & reboot . This should enable the nvidia chip with all the needed settings for the next boot.

- if this won't do it, uninstall the acpitools deb, and run the manual instructions for enabling nvidia from the [wiki]("https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#Graphics%20Chips") ( I called it "Mode 2" there)

I could make a version that writes the temporary file to /tmp instead of $HOME but this is strongly discouraged by all the Linux gurus i talked to. (reason is that this is a security risk...)

Or if anyone has a better solution for this problem please don't hesitate to enlighten me ;)

---

### Post by Nisitiiapi on 2011-04-08
I didn't encrypt my home folder specifically to make sure that wouldn't  cause a problem.  I was messing with things myself.  Thought maybe  creating an xorg.conf file before installing the debs (after a clean  install) would help, but no change. 
 
After installing the debs and trying a reboot selecting nvidia (both  with the GUI and with the CLI), I did find a .vga-selector file in my  home director.  It just had the word "nvidia" in it and nothing else.   But, dispaly-settings status still said "Intel" and lscpi showed no  nvidia. 
 
So, I uninstalled the acpitools deb and tried the manual method.  That  worked and it booted using the nvidia chip (showed nvidia splash screen  and nvidia shows in lspci).

So, what could be the difference in error between the acpitools and the  manual method? I'm wondering if it's a symlink or something that's off  or a missing file.

---

### Post by mtron on 2011-04-08
yes most probably it's a missind / invalid symlink. though the postinstall script should take care of creating these...

so let's check everything is in place ;). Please undo all of your changes. before proceeding and after this re-install the acpitools deb and check that the following files exist:

- /usr/local/bin/display-settings: main script
- /etc/X11/xorg.conf.intel
- /etc/X11/xorg.conf.nvidia
- /usr/local/bin/vga-selector-gui: the gui script to select the vga card
- /etc/init.d/vga-selector: the shutdown script that triggers the vga selection

and following symlinks should exist and point to /etc/init.d/vga-selector
/etc/rc0.d/K10vga
/etc/rc6.d/K10vga

Also remove any existing /etc/X11.xorg.conf file before installing the acpitools package.

Now call the gui scipt, select nvidia press ok but don't shutdown. Check that $HOME/.vga-selector exists and has the word "nvidia" in it. If it still does not work we need to do a in-deph debugging. I'll prepare a special version of the script with debugging output to see where it is failing in your case.

---

### Post by Nisitiiapi on 2011-04-09
Thanks once again, mtron.

I ended up reformatting and reinstalling -- for some reason removing the acpitools and trying to reinstall it caused an error and then the package became messed up and I couldn't reinstall or remove without errors.

Anyway, after reinstalling and installing the nvidia x-swat driver, I installed acpicall (it loads without error, by the way) and then acpitools.  All of the files are there (and no xorg.conf file even after installation of acpitools) and selecting nvidia from the GUI created the .vga_selector file in $HOME and it said 'nvidia.'  Then, I rebooted, checked display-settings status and it says the Intel chip is being used.  And even after reboot, .vga-selector is still in $HOME and still says nvidia.

To see again what the error was in uninstalling acpitools, I unistalled it again (using --purge).  Interestingly, it says both /etc/rc0.d/K10vga and /etc/rc6.d/K10vga cannot be removed because they don't exist ("No such file or directory").  It also says it can't remove /usr/lib/xorg/modules/extensions/libglx.so.intel or /usr/lib/xorg/modules/extensions/libglx.so.nvidia because they don't exist.

A reboot after that dropped into terminal, but deleting xorg.conf fixed that and both chips appear in lspci.

A reinstall of acpitools repeated the message that libglx.so cannot be found, so I re-activated the nvidia binary driver.  After rebooting (and being on the Intel chip), I looked again at all the files and they are there (as well as an xorg.conf file configured for intel).  I decided to look at the driver files that were noted as missing during removal and installation of acpitools and found that the symlink /usr/lib/xorg/modules/extensions/libglx.so exists, but is broken (it wants to point to libglx.so.intel, but that's not there and neither is libglx.so.nvidia).  The only actual libglx.so file in the system is /usr/lib/nvidia/current/xorg/libglx.so.270.29 (the x-swat driver).

Since the manual method works and the difference I see between that and acpitools is where the symlink points to the driver, it crossed my mind last night that the issue could be that the symlink acpitools creates doesn't point to the installed nvidia video driver.  After seeing the missing files in removal and reinstall, tonight, I tried creating a symlink of libglx.so.nvidia to libglx.so.270.29 and even manually recreating the libglx.so symlink to point at libglx.so.nvidia, but it didn't help - on reboot, libglx.so still tries to point at libglx.so.intel (even though .vga-selector still says nvidia).  Still, maybe that is starting to hint at the issue?

---

### Post by mtron on 2011-04-09
ok, let's debug this better. 

Do you have skype or prefer IRC? chat is much more efficient for this.

I'm in GMT+2 and today or tomorrow evening is cool for me. please drop me a pm when you have time to do this.

---

### Post by Draugen River on 2011-04-09
Maybe a bit off topic off topic, but I have used my pc to run the xbmc. The xbmc is you is probably unrelated to the tweak in this thread, but Im just wondering if you guys have seen high temperatures as well?

---

### Post by fiox on 2011-04-12
Hi guys, this can work on my asus k52jc with nvidia optimus??

---

### Post by mtron on 2011-04-12
no. 1015PN only

---

### Post by fiox on 2011-04-12
Hi and thanks for your reply

can you tell me why can not it work with my laptop?

[SIZE=1]Sorry for my english[/SIZE]

---

### Post by mtron on 2011-04-13
the used acpi_calls to switch gpu's are hardware specific for this laptop ONLY.

They were reverse-engineered by Raphael Metzler from a Windows-only Binary Program by Asus called "Graphics Switching Utility for EeePC 1015PN"

**So this is no general fix for the non-working Optimus Technology on Linux systems!** 

It's a (dirty?) hack that **makes basic GPU switching via Reboot work for one model** (namely the 1015pn) where we have a useable hardware design, and the needed acpi calls are already known.

To make this work on your laptop i would need:

- clarification on the hardware design of your laptop. is the nvidia chip able to draw to the display device directly or does it need a intel framebuffer like most other Optimus laptops do? 

- reverse-engineer the needed acpi calls to switch GPU's. This can either be done by looking into the Asus windows binary or dump your laptop's DSDT.dsl information and try the calls in there. (usually there are 100 of them...)

---

### Post by fiox on 2011-04-13
Ok man..i have understand. Seems that there is no solution for my laptop...unfortunately

Thanks anyway


p.s. first time i have test the solution for 1015PN on my ubuntu 10.04 64bit, and on the next reboot i have black screen, This may be interesting?

Maybe the switch works? I do not have all the correct paths in the scrit when i have make it

---

### Post by Emissär on 2011-04-13
I am another who also needs help!

 I was directed here after.
 [http://mtron.co.nr/howtos/eeepc-1015pn](http://mtron.co.nr/howtos/eeepc-1015pn)

 I chose the method with the GUI. 

The switch works fine, but i can not activate the desktop-effekts! :sad:

Also does the graphic-switch only worked on the GUI.
 If I was in the terminal "sudo display nvidia-settings-reboot" enter,  then I just get error messages at the moment if I used the intel-mode.

How can I activate the desktop-effects for both cards? 

My english is very bad, I know! Sorry for this, I hope you understand me und you can help me. Thanks!

---

### Post by mtron on 2011-04-13
> **fiox said:**
> Maybe the switch works? 

I don't think so. But it's easy to check. Run "lspci | grep -i VGA" If the switching worked you should only get one VGA Controller (either Nvidia OR Intel)

Again, it all depends on the hardware design of your Laptop. If your nvidia chip can't access the display device directly, there is currently no Software only way i am aware of to make the nvidia card work on linux

---

### Post by mtron on 2011-04-13
> **Emissär said:**
> The switch works fine, but i can not activate the desktop-effekts!

Drop me a pm. We will debug this via chat.

---

### Post by fiox on 2011-04-13
> **mtron said:**
> I don't think so. But it's easy to check. Run "lspci | grep -i VGA" If the switching worked you should only get one VGA Controller (either Nvidia OR Intel)

Again, it all depends on the hardware design of your Laptop. If your nvidia chip can't access the display device directly, there is currently no Software only way i am aware of to make the nvidia card work on linux

I always get black screen before I see anything, I installed ubuntu again.

For test the script and not destroy ubuntu, if i run only Switch_intel.sh, I have only see intel card?

Thanks

---

### Post by mtron on 2011-04-13
so use recovery mode in grub and drop to a root shell...

Please open a new thread. This is getting really off-topic here.

---

### Post by fiox on 2011-04-13
Yes this is off-topic, sorry for this.

If i have news with optimus and method for 1015PN i post my results

---

### Post by rushingad on 2011-04-15
> **mtron said:**
> hello!

over the weekend i have prepared a deb package for easy installation and uninstallation of the EeePC 1015PN vga switching script.

so the current steps to utilize both chips are:

- install the maverick desktop version (i use the amd64 variant)
- go through the Eee-fixes checklist on the [wiki]("https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#Asus Eee PC 1015PN")
- install the build-essential and kernel-header packages
- install the nvidia binary driver as described on the [wiki]("https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#Asus Eee PC 1015PN")
- download the [acpicall-dkms_0.1_all.deb]("http://ubuntuone.com/p/dil/") kernel module and install it with 
```
sudo dpkg -i acpicall-dkms_0.1_all.deb
```
- download the [acpitools_0.2_all.deb]("http://ubuntuone.com/p/h1a/") Package and install it with 
```
sudo dpkg -i acpitools_0.2_all.deb
```

after the install go to "Applications -> System Tools -> Vga Selector" and choose the desired vga mode for the next boot.

If you reboot without using the vga selector gui the script will default to intel mode.

the script has more options when called from a terminal with
```
sudo display-settings <option>
```

where <option> is one of the following:



For more information how this script works see [this post]("http://ubuntuforums.org/showpost.php?p=10467121&postcount=23") from page 2.

I have also created a webpage with full install instructions [here]("http://mtron.co.nr/howtos/eeepc-1015pn") hopefully this makes the whole procedure much easier. :D

When switching to nvidia and rebooting, I get no display. The screen is backlit but is black. The sound works and the OS is running (I know because I hear the login screen sound, then after I hit Enter and type in the password, I hear the sound played when the computer boots up. Then hitting ctrl+alt+delete and Enter, the computer shuts down.) Any ideas whats causing this?

EDIT: I have the 1215N. I know this is for the 1015PN but I tried anyway because they are virtually the same PC.

---

### Post by mtron on 2011-04-16
Morning! 
> tried anyway because they are virtually the same PC. 

Well, _virtually_ is not enough in this case. There seems to be a huge difference between this 2 models: The nVidia GPU of this model is not directly wired to the display device so it can't  draw to it.

So, the procedure for the 1015PN won't work on the 1215N. No way Jose.

---

### Post by barthus on 2011-04-16
Hi all.

I think we all have to thank mtron who is doing really a great job here in this thread!

I just updated the introduction such that the people immediately drop to message #61 from mtron.

All the best, barthus!

---

### Post by barthus on 2011-04-16
> **Emissär said:**
> I am another who also needs help!

 I was directed here after.
 [http://mtron.co.nr/howtos/eeepc-1015pn](http://mtron.co.nr/howtos/eeepc-1015pn)

 I chose the method with the GUI. 

The switch works fine, but i can not activate the desktop-effekts! :sad:

Also does the graphic-switch only worked on the GUI.
 If I was in the terminal "sudo display nvidia-settings-reboot" enter,  then I just get error messages at the moment if I used the intel-mode.

How can I activate the desktop-effects for both cards? 

My english is very bad, I know! Sorry for this, I hope you understand me und you can help me. Thanks!


Emissär, did you try the second alternative version in message #1?

---

### Post by mtron on 2011-04-17
We already fixed his problem. He fiddled with the glx libs and broke the script.

Anyway.. For others with non-working glx : The diaplay-settings script has a recovery function for this situations. Just call

```
sudo display-settings fix
```

@ Barthus: could you please put a fat warning in the first post that this will only work for the Asus EeePC 1015PN ? No need to try this on other Eee Models. It will fail and most probably leave your system in a broken state. (just to scare people enough ;)

---

### Post by barthus on 2011-04-17
> **mtron said:**
> @ Barthus: could you please put a fat warning in the first post that this will only work for the Asus EeePC 1015PN ? No need to try this on other Eee Models. It will fail and most probably leave your system in a broken state. (just to scare people enough ;)

Done ...

---

### Post by magical2hobo on 2011-04-19
Will this work with 10.04 LTS or just 10.10?

---

### Post by snizzo92 on 2011-04-20
will this work also with 1215N?

thanks

---

### Post by mtron on 2011-04-20
@ snizzo92: See first post...

> **barthus said:**
> [B][COLOR=Red][SIZE=3]All scripts published and discussed in this thread 
will only work for the Asus EeePC 1015 PN !!![/SIZE][/COLOR][/B]

---

### Post by mtron on 2011-04-20
> **magical2hobo said:**
> Will this work with 10.04 LTS or just 10.10?

Well, It's not a good idea to use 10.04 at all on this netbook. It needs newer nvidia drivers, newer alsa drivers, newer acpi packages (and so on..) than published in the lucid repositories. 

So you will save yourself a lot of headache if you use maverick.

---

### Post by whitec on 2011-04-20
Will this work with 11.04?   Just got one of these, and was wondering if I would be wasting my time trying to get this to work on 11.04 :-)

Would honestly probably be ok with 10.10 - but usually like to run latest if i can!

---

### Post by mtron on 2011-04-21
the manual method as described on the wiki page will work also on natty.a user reported that the auto method with the gui script is not working.

i did not test natty till now, but i promise to get everything in place until natty reaches it's release date at the end of April.

---

### Post by --cam-- on 2011-04-29
Hi,

i am having a problem with the intel card´s resolution. I have ubuntu 11.04 64 bits, mtrons VGA-Selector GUI is working for me, i can switch between intel and nvidia, but with intel the system starts with 640x480 res. With xrandr i can insert the right resolution (1024x600) but it only works for the session. I tried editing xorg.conf like described in [http://wiki.ubuntu.com/X/Config/Resolution]("http://wiki.ubuntu.com/X/Config/Resolution") to make it permanent but it doesnt work. Does anyone else have this problem? any ideas to resolve it?

---

### Post by mtron on 2011-04-29
Hello! 

Yes, this seems to be caused by "invalid" horizontal sync settings in the xorg.conf file for intel.

I've updated the acpitools package and added some new stuff. Get the new deb from [http://ubuntuone.com/p/pPr/](http://ubuntuone.com/p/pPr/) and install it (you don't need to uninstall the old version) with 

```
sudo dpkg -i acpitools_0.3_all.deb
```

Let me know if this fixes it. 

Changelog for acpitools_0.3:
* fixed the glx libraries regeneration after a nvidia driver update 
* fixed xorg.conf.intel
* added automatic Desktop Enviroment detection (Unity, Gnome or KDE) to use native toolkits for the vga-selector-gui
* added kde native kdialog gui to switch VGA chips (so no gtk stuff needed any more)
* added support for encrypted homedrives. (.vga-selector file is moved to /tmp in this case) 
* added zenity or kdialog as package depends (depending on DE)

I will update the howto for natty in the coming days.

Cheers!

---

### Post by Klaster on 2011-04-29
> **mtron said:**
> Hello! 

Yes, this seems to be caused by "invalid" horizontal sync settings in the xorg.conf file for intel.

I've updated the acpitools package and added some new stuff. Get the new deb from [http://ubuntuone.com/p/pPr/](http://ubuntuone.com/p/pPr/) and install it (you don't need to uninstall the old version) with 

[....]

I will update the howto for natty in the coming days.

Cheers!

Hey mtron,
so this release is working for 11.04?
I got my 1015 today and am all excited about getting everything set up. :o)

Thanks a lot for your work!

Klaster

---

### Post by mtron on 2011-04-29
here be dragons ...

---

### Post by mtron on 2011-04-29
> **Klaster said:**
> so this release is working for 11.04?

Yes, I hope so ;) 

For natty you still need the [acpicall-dkms_0.1_all.deb ]("http://ubuntuone.com/p/dil/") and the  [acpitools_0.3_all.deb]("http://ubuntuone.com/p/pPr/") package from above

---

### Post by --cam-- on 2011-04-30
Thank you mtron, it works!!! XD

---

### Post by barthus on 2011-05-02
Hi all.

I just updated my first message.

Cheers all.

---

### Post by doc.maizo on 2011-05-02
> **mtron said:**
> 
- go through the Eee-fixes checklist on the [wiki]("https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#Asus Eee PC 1015PN") (not needed for natty)


You are saying that (at least yours) 1015PN works with Natty ootb?! Great! :)

---

### Post by mtron on 2011-05-02
yes, the spin-down problems of the Western Digital HDD seems to be fixed, also the special grub settings and newer alsa drivers are not needed any more. 

Great news is that the open source driver for the Broadcom BCM4313 Wlan chip is now shipped with the kernel so you don't need the binary blob any more. (Just ignore that ubuntu still offers the Binary blob via restricted drivers manager... this seems to be a bug) 

jupiter is still needed for the CPU preformance mode toggle and multitoch is still disabled per default.

Unfortunatly Bluetooth is still very fragile ( i think this can only be fixed by asus with a bios update) and the Hardware button on the left top to switch cpu power mode and toggle bluetooth and wlan still does nothing (and does not produce any kernel output at all).

And the worst problem: the kernel power bug in natty cuts down the run time on battery drastically :( 

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/760131](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/760131) 

on maverick i got 6 hours runtime. on natty my eee dies after max. 4 hours (both with intel vga) so if you need long runtime on battery don't upgrade to natty just now. 

cheers

---

### Post by doc.maizo on 2011-05-03
> **mtron said:**
> 
And the worst problem: the kernel power bug in natty cuts down the run time on battery drastically :( 

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/760131](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/760131) 

on maverick i got 6 hours runtime. on natty my eee dies after max. 4 hours (both with intel vga) so if you need long runtime on battery don't upgrade to natty just now. 


I think that I'll wait, please keep us up to date!

---

### Post by doc.maizo on 2011-05-03
> **mtron said:**
> on natty my eee dies after max. 4 hours (both with intel vga)

And what about ION? With "both with intel vga" do you mean that there is no difference?

---

### Post by mtron on 2011-05-03
ion draws more power from the battery. so you won't even get up to 4 hours on natty

What i ment was:
Runtime on maverick with a full battery charge and Intel GPU: 6h
Runtime on maverick with a full battery charge and Nvidia GPU: 4h
Runtime on natty with a full battery charge and Intel GPU: 4h
Runtime on natty with a full battery charge and Nvidia GPU: <not tested>

---

### Post by doc.maizo on 2011-05-03
Ok, now it's all clear... but I'm still undecided! :confused:
Thx for the help!

---

### Post by barthus on 2011-05-03
> **mtron said:**
> Runtime on maverick with a full battery charge and Intel GPU: 6h
Runtime on maverick with a full battery charge and Nvidia GPU: 4h
Runtime on natty with a full battery charge and Intel GPU: 4h
Runtime on natty with a full battery charge and Nvidia GPU: <not tested>

So, natty is using indeed more power! 

BTW: Are these values for the idle state? When I work with the intel (surfing, writing, copying, etc) I have 4 hours.

---

### Post by beast.dk on 2011-05-04
I tried to install 11.04 some time after Mtrons modifications to 10.10 and it broke my installation :-(

Only able to start up in FailsafeX mode.

Installed acpitools_0.3_all.deb to fix it with no luck. Just get to the place where the startup log states "Checking battery state...." and the the boot process stops?

Properbly because it is unable to start the GUI shell.

Any hints about how to fix my installation without a complete new installation?

Also tried display-settings fix etc.

Thank you in advance
Benny

---

### Post by mtron on 2011-05-04
look at this guys:

[http://www.martin-juhl.dk/2011/05/optimus-on-linux-problem-solved/](http://www.martin-juhl.dk/2011/05/optimus-on-linux-problem-solved/)

seems we are very close to a real solution for Optimus on linux!

---

### Post by Klaster on 2011-05-05
Hey there, 

so I installed everything as described and a couple of days back I found that the nVidia-card was active. I didn't really mind since I didn't need the battery.  

Today I wanted to connect my eee to my TV and as it turned out, my Intel-chip was running (checked via the script from mtron).  I wanted to switch to nvidia with the given command but it didn't work:

```
asche@sweet1015:~$ sudo display-settings statusActive GPU: Intel GMA3150 on PCI 00:02.0

asche@sweet1015:~$ sudo display-settings reboot-nvidia
update-alternatives: using /usr/lib/nvidia-current/ld.so.conf to provide /etc/ld.so.conf.d/GL.conf (gl_conf) in manual mode.
update-alternatives: warning: skip creation of /usr/lib32/vdpau/libvdpau_nvidia.so.1 because associated file /usr/lib32/nvidia-current/vdpau/libvdpau_nvidia.so.1 (of link group gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libvdpau_nvidia.so because associated file /usr/lib32/nvidia-current/vdpau/libvdpau_nvidia.so (of link group gl_conf) doesn't exist.

```I rebootet anyway but as expected the Intel-chip was still active. My nVidia-drivers are up to date (checked).
The TV isn't detected via the HDMI. I assume that the Intel-chip isn't capable to do it? Otherwise it's another issue, for now, I'd like to know about the problem above (however, I'd appreciate tips regarding the TV, too).

I use Natty.

Thanks a  lot!

Klaster

EDIT: I saw mtron's post #80 and use the home-folder encryption myself: [http://ubuntuforums.org/showpost.php?p=10648223&postcount=80](http://ubuntuforums.org/showpost.php?p=10648223&postcount=80)
I obviously tried the Terminal-thing (the VGA-selector isn't shown in my system settings).By changing the first line of the script, would I change the boot preference? Is there any other option or do I have to change the script every time I want to change card?

---

### Post by mtron on 2011-05-05
You're not alone ;) there are now some people reporting problems with natty. I think that the 0.3 version of the switcher script might have a problem. i'll check it tomorrow. Thanks for the hint.

Please remove the acpicall deb & the xorg.conf
```
sudo apt-get purge acpicall
sudo rm /etc/X11/xorg.conf
```

and reinstall the xorg & nvidia packages:
```
sudo apt-get install --reinstall xserver-xorg-core
sudo apt-get install --reinstall nvidia-current
sudo nvidia-xconfig
```


Now try rebooting (min. twice!) and see if the nvidia chip is active again. If so try the manual method on the wiki or barthus switcher script from the first post. Does it work with one of those?

---

### Post by Klaster on 2011-05-05
I found the VGA selector (with Gnome and now also with Unity) and apparently the switching works perfectly fine with the GUI. However, the terminal command still shows the same error.

Thanks again for your work, mtron! I really do appreciate it!

---

### Post by Lochlainn on 2011-05-07
> **Klaster said:**
> I found the VGA selector (with Gnome and now also with Unity) and apparently the switching works perfectly fine with the GUI. However, the terminal command still shows the same error.

Thanks again for your work, mtron! I really do appreciate it!

Unfortunately it didn't work for me with the GUI. when looking at the lspci -l, I don't see nVidia listed. I'm likely going to stick with the Intel chip for now since it increased my battery life by a couple of hours, but it would be nice to be able to switch using a GUI.

Thanks to mtron too!

---

### Post by barthus on 2011-05-08
I updated the first page. It says now more clearly that things still need some time with Natty.

Cheers.

PS: We have 128 contributions in this thread and amazing []("http://ubuntuforums.org/misc.php?do=whoposted&t=1677780")15,158 visitors, which shows that our discussions are of importance.

---

### Post by KyleHyde on 2011-05-09
I just wanted to thank mtron for taking the time to personally try to debug some of the graphic switching problems in natty I was having.  Hopefully, it was of some help for you mtron.

In summary, I still can't get nvidia to load after installing the acpicall on natty, and I would get a strange pixilated screen after grub.  

I reverted back to 10.10 and it's working perfectly.  I hope we can get natty working well, as I actually kind of started to like unity, and it would be nice to get natty flowing smoothly.  

Is there a way to make booting into optimus with powersave the default login?  I usually want more battery life over performance.

Annother question: in maverick I can perfectly choose between graphics cards.  However, I can't for the life of me get the hdmi to external monitor to work.  Sometimes nvidia detects my samsung plasma and other times it doesn't.  Anyone having similar problems?

PS. How many people prefer unity's dash to gnome-do.  I like the concept and layout of the dash (though the lack of customization irks me), but gnome-do seems faster and far more applicable while accomplishing the same tasks.

Am I just clueless about the true power of unity's dash?

---

### Post by bero74 on 2011-05-09
First of all I would like to thank mtron and barthus for their hard work!

I’m running Ubuntu Natty (11.04) on my Asus 1015PN. Like for everybody else (?) the vga-selector switches to intel, but I’m not able to switch back to nvidia.
I have removed acpitools_0.3_all.deb and run with the nvidia graphics for now on.

When testing the scrips in acpitools_0.3_all.deb I found out that I got strange ownership of the files included. They wore not owned by root. I installed them using “sudo dpkg -i acpitools_0.3_all.deb”.

---

### Post by mtron on 2011-05-09
thanks for all the bugreports.

here is a new test-version: [acpitools_0.4_all.deb]("http://ubuntuone.com/p/s1l/") 

if you update from a previous version please remove any old acpitools package and reinstall the xorg-core and nvidia-current package to assure that everything is in place.

```
sudo apt-get remove acpitools
sudo apt-get install --reinstall xserver-xorg-core
sudo apt-get install --reinstall nvidia-current
```

now install acpitools :
```
wget http://ubuntuone.com/p/s1l -O acpitools_0.4_all.deb
sudo dpkg -i acpitools_0.4_all.deb
```

Hopefully this should fix some of your problems

>  
Changelog acpitools-0.4
 * added "defaultgpu" Variable (used to set your default gpu if no user selection is available). Adjust it in the display-settings script at the "Settings" Section on top of the script
 * added more debug output
 * fixed glx libraries regeneration. Should now work for all nvidia driver versions installed via the packaging system 
 * fixed permissions (Thanks to bero74)

---

### Post by bero74 on 2011-05-09
I have been playing a bit with your new scripts. For me it changes the graphics to intel and I'm not able to switch to nvidia.
I know that I have a .vga-selector file in my home directory containing "nvidia", but running sudo display-settings auto gives the following:

INFO: acpi_call Kernel module is available
INFO: nothing useable found in /tmp. Moving on...
INFO: No user preference found in /home/donald. Moving on...
INFO: No user preference found in /home/duck. Moving on...
cat: /home/.vga-selector: Filen eller katalogen finns inte (swedish for file or directory missing) 
cat: /home/.vga-selector: Filen eller katalogen finns inte
cat: /home/.vga-selector: Filen eller katalogen finns inte
INFO: No User selection found. Using intel as default GPU
INFO: VGA for next boot is Intel GMA 3150
INFO: triggering mesa ldconfig...
INFO: prepare mesa glx lib...
INFO: preparing xorg configuration...
INFO: Pre-reboot configuration for Intel GMA 3150 completed!

---

### Post by mtron on 2011-05-09
interesting. Do you have any special (= non latin) character in your username(s)? how many accounts are on your laptop? Please post "echo $HOME" from all the user
accounts.

to force nvidia try 
```
sudo display-settings reboot-nvidia
```
this should override any gui settings

---

### Post by bero74 on 2011-05-09
No, I have only Latin characters in both user names. I have two user accounts. I will post echo $HOME tomorrow ... :-)

---

### Post by ms-trex on 2011-05-10
Doesn't work for me in natty. When I try to install acpitool I get
> 
rm: cannot remove '/etc/rc0.d/K10vga': No such file or directory
cp: target '/usr/lib/xorg/extra-modules/libglx.so is not a directory

and more.

---

### Post by mtron on 2011-05-10
this is some dirt left behind from an older version. Did you uninstall the old package before installing the new one?

come to IRC #eee-1015pn on freenode.net

---

### Post by ms-trex on 2011-05-10
> **mtron said:**
> this is some dirt left behind from an older version. Did you uninstall the old package before installing the new one?
Yes.
> 
come to IRC #eee-1015pn on freenode.net

I dont know how to use IRC.

Well I tried manual method and intel works now, but 3D effects dont work.

EDIT 1:
I dropped ubuntu and I installed debian 6. I tried this part:
```

git clone http://github.com/mkottman/acpi_call.git
cd acpi_call
make
insmod acpi_call.ko
echo "\OSGS 0x01" > /proc/acpi/call

```
and after reboot nvidia was turned off, but what to do to make this permanent, because after another reboot intel is turned off. Help please.

EDIT 2:
Whether such script placed in /etc/init.d would work to disable ion constantly, on every boot?
```

#!/bin/bash
insmod /home/user/acpi_call/acpi_call.ko
echo "\OSGS 0x01" > /proc/acpi/call

```

---

### Post by bero74 on 2011-05-10
sudo display-settings reboot-nvidia does override the settings in .vga-selector file. This way the script works great!

I will post echo $HOME in a private message for you (mtron). Thanks for your efforts!

---

### Post by mtron on 2011-05-10
> **ms-trex said:**
> 
Whether such script placed in /etc/init.d would work to disable ion constantly, on every boot?
```

#!/bin/bash
insmod /home/user/acpi_call/acpi_call.ko
echo "\OSGS 0x01" > /proc/acpi/call

```

yes. write a proper init script and place symlinks in the runlevels rc0.d and rc6.d (shutdown and reboot).

---

### Post by bero74 on 2011-05-11
mtron:

I have made some chages of the userhome function in your display-seloctor script. What do you think of the following? Seems to work for me :-)

## figure out the location of the .vga-selector file
userhome () {
if [ -s /tmp/.vga-selector ] ; then 
 echo "/tmp is the way to go";
 dirname=/tmp
 echo "INFO: User preference found! Using /tmp/.vga-selector"
else 
 echo "INFO: nothing useable found in /tmp. Moving on..."; 
 for dir in `ls /home` 
 do
 file=/home/$dir/.vga-selector
 dirname=`dirname "$file"`
  if [ ! -s $file ]; then
    echo "INFO: No user preference found in /home/$dir. Moving on..."
  else
    echo "INFO: User preference found! Using $file"
    break
  fi
 done
fi
}

---

### Post by mtron on 2011-05-11
ah, exiting the loop is a good idea ):P

Thanks! new deb package following...

---

### Post by Lochlainn on 2011-05-11
> **bero74 said:**
> sudo display-settings reboot-nvidia does override the settings in .vga-selector file. This way the script works great!

 
I had this same problem. Using sudo display-settings reboot-nvidia worked for switching for me too. I just dropped a launcher on my desktop to switch to nVidia if I want to so I won't forget the commands. 
 
Thanks so much for the help on this. Will the new fix you're working on make the desktop launcher unnecessary?

---

### Post by mtron on 2011-05-11
Let's see ;)

---

### Post by Nisitiiapi on 2011-05-13
I was able to get the switching working well with barthus's scripts in the first post (with a slight change for automatically pointing to acpi_call.ko).  I then created two menu entries to run the nvidia and intel scripts.  This seems to work best for me because 99% of the time, I'm plugged in to AC power, so booting to nvidia by default is good.  I do think a kernel option to boot into intel only would be best -- that way I could select it on boot when on battery power.  But, restarting into intel works for now.

On a side note, has anyone noticed very poor speed and performance on the Broadcom wireless in natty?  At best, I can get it to show 75 mb/s on a wireless N network.  That's with the sta driver.  With b43, I'm luck to get 60 mb/s.  My old 1005ha with atheros, shows 150 mb/s on the same network.  Haven't been able to figure out if this is a change from maverick or not -- the sta driver doesn't seem to want to install on LiveUSB.

---

### Post by Markino76 on 2011-05-15
Hi guys!
I really need your help: I'm trying to use the nvidia card in order to connect my tv via hdmi with the info in the post #1 but I'm always getting this error:

"cp: cannot stat `/etc/X11/xorg.conf_nvidia': No such file or directory"

How can I solve that problem?

I'm running Ubuntu 11.04 and I'd like to run always nvdia because I'd like to use my 1015PN as mediacenter with XBMC.

---

### Post by Markino76 on 2011-05-16
Hi, I'm keep trying to use ION on my Asus and after a fresh instalaltion of the new 11.04 with all the updates installed and the 3 new drivers I can use the hdmi out of the box!

In order to use the TV as clone display I had just to open the NVIDIA "X Server settings", detect my TV (connected via hdmi) and configure it as twindisplay and clone mode.

Now my question is: can I assume that if I can see my desktop "cloned" in my TV via hdmi I'm running correctly the Nvidia ION2 card? How can I check if is it really running instead of the Intel?

I've tryed to play hd video in 720p without probelm but full-hd 1080p videa won't play and freeze vlc... :(

Last problem: Nvidia X server settings lose the configuration when I reboot the system even if I launch it with sudo and I save the .conf file. :(


No one can really help me starting from a fresh installation of 11.04? :(

---

### Post by Nisitiiapi on 2011-05-16
This is somewhat of a guess, but if you're using the scripts, don't modify xorg.conf directly, modify xorg.conf.nvidia or whatever you have your nvida configuration file called.  The xorg.conf should change when you reboot if you're using one of the scripts -- by becoming a symlink to xorg.conf.nvida or xorg.conf.intel.

To see if the nvidia chip is active, if you're using mtron's scripts:
```
sudo display-settings status
```Otherwise, do:
```
lspci | grep VGA
```

---

### Post by oniboni on 2011-05-17
Hello,

i had a problem installing the acpitools 0.4!

i did not have a xorg.conf, 

and thus the backup copy in the postinstall script did not succeed resulting in a partially installed acpitools

"dpkg -C" said:
```
Die folgenden Pakete sind nur halb konfiguriert, wahrscheinlich durch
Probleme während der ersten Konfiguration. Die Konfiguration sollte mit
dpkg --configure <Paket> oder mit dem Konfigurations-Menüeintrag in
dselect erneut versucht werden:
 acpitools            Helper scripts to select used GPU on Asus EeePC 1015PN 


```Solution:
```
cd /var/lib/dpkg/info
mv acpitools.postinst acpitools.postinst.off
dpkg --configure acpitools
mv acpitools.postinst.off acpitools.postinst
```now everything works perfectly on natty! Thank you really much mtron! :KS

---

### Post by mtron on 2011-05-20
Thanks for the info.

Didn't know that there is no xorg.conf after a standard install :(

I'll fix the deb!

---

### Post by doc.maizo on 2011-05-25
[Alternative solution for Optimus support!]("https://github.com/MrMEEE/bumblebee") 1215N is supported, 1015PN not yet!

---

### Post by mcstayinskool on 2011-05-25
> **doc.maizo said:**
> [Alternative solution for Optimus support!]("https://github.com/MrMEEE/bumblebee") 1215N is supported, 1015PN not yet!

Boy, that looks promising. Anyone know, is it just that 1015PN hasn't been tried yet, or is it known to be not working yet?

cheers,
#!/ben

---

### Post by johnnycasher on 2011-05-31
Hi everyone!

First of all i wanna thank all the contributions to get things to work. Second, i'm running Xubuntu 11.04 on 1015pn Asus EEE and i was stucked one night long cuz i don't know why but the vga selector didn't worked to change to nvidia settings (only intel worked).

The scripts in the first page either don't worked with me.

I found that after installing 0.4 package and forcing (display settings -reboot-nvidia) i can use the nvidia card aswell wich is a great advance! The only problem is that by default i have INTEL GMA, so i can only have Nvidia if i execute the forcing cmd. Someone know how to get nvidia by default and not GMA?

Thanks and i'll be waiting for further developments!

---

### Post by Markino76 on 2011-06-01
Same problem here... can't get the switch works. :(

---

### Post by doc.maizo on 2011-06-06
[Ubuntu Control Center]("http://www.webupd8.org/2011/06/ubuntu-control-center-061-released.html")
> UCC also lets you switch between low and high performance graphics cards (if you have a netbook with 2 GPUs) which is possible starting with Linux Kernel 2.6.35

---

### Post by mtron on 2011-06-06
Hello! 

I fixed some bugs (thanks to all the people sending their logs) and prepared a new version. I hope that 0.5 fixes the bugs with natty and makes reliable switching work.

Please remove any old acpitools package you might have installed 
```
sudo dpkg -r acpitools
```

and reinstall the nvidia and intel drivers to ensure everything is in place.
```
sudo apt-get install --reinstall xserver-xorg-core
sudo apt-get install --reinstall nvidia-current
```

**Download and Install**

1.) Download and install the acpi_call.ko Kernel module in dkms format. This module will auto update itself for newer kernels. (Not needed if you update from an older acpitools version)

```
wget http://ubuntuone.com/3n8QokeGLExVImO76WYNUh -O acpi-call-dkms_240611-1~nattyubuntu1_all.deb
wget http://ubuntuone.com/1xcOJ4oGH71pISrzjL2i5u -O acpi-call-source_240611-1~nattyubuntu1_all.deb
sudo apt-get install build-essential debhelper module-assistant
sudo dpkg -i acpi-call*.deb
```

2.) Download and install the acpitools 0.5.1 deb

```
wget http://ubuntuone.com/4T8W2CNST8ToZsp7s2d2hJ -O acpitools_0.5.1_all.deb
sudo dpkg -i acpitools_0.5.1_all.deb
```

**Changelog **

acpitools 0.5.1 MD5:6699c293e66fa9b16e36ef0fd73feeb0
> * fixed acpi_call dkms kernel module
* gnome/kde gui: added option to change the default GPU (root pw required)
* fixed nouveau blacklist for natty 
* added a ".vga-lock" file in /tmp to prevent multiple selections of the VGA device for the next boot. the lock is set when a acpi_call triggers the gpu for the next boot. Debugging showed that the next boot VGA Mode can only be set once every boot cycle or it messes up this script
* added nv-on and nv-off command line options to toggle the Power of the Nvidia GPU (this will become useful for bumblebee integration)
* moved .vga-selector file to /tmp


**FAQ** 

Q: I have installed the deb. How do i switch the VGA cards ?
A: Go to "Applications - System Tools - Vga Selector" and select either intel, nvidia or optimus

Q: Whats the "Change Default GPU" Option in the gui for?
A: If you reboot without selecting a VGA Card manually the script will fall back to the selected default GPU. You need to provide the root password to change your Default GPU. Available GPU Modes are "intel" (Intel GMA 3150 exclusive mode. The nvidia chip won't be visible via lspci and is powered off) "nvidia" (nVidia GT218 exclusive mode) and "optimus" (Dual VGA Mode)

Q: How can i check the used gpu?
A: sudo display-settings status

Q: When running the script i get "ERROR: Could not load acpi_call.ko. Please rebuild the kernel module". What can i do?
A: You need to install the acpi-call kernel module. see the Install section above

Q: What is the Optimus Mode for?
A: In this mode both cards are active (but the nvidia chip can be separately powered on or off). The [Bumblebee project]("https://github.com/MrMEEE/bumblebee/") might make the nvidia gpu useable "on-demand"

**Command Line switches**

the script has more options when called from a terminal with
```
sudo display-settings <option>
```

where <option> is one of the following:

> **auto**
In this mode the script will look for a .vga-selector file written by the GUI script and executes the acpi_call for the desired option (Intel,Nvidia or Optimus mode). It will also prepare the xorg configuration and glx libraries for the next boot. If the script can't find any .vga-selector file it will default to Intel mode. Adjust the default VGA Mode in the Settings section of the display-settings shell script

**status**
This will output current VGA Mode. E.g "Active GPU: Intel GMA3150 on PCI 00:02.0"

**fix**
This will fix the glx libraries after the install of a newer nvidia driver version. 

**reboot-intel**
activate intel for next boot and prepare xorg conffiles for intel. The nvidia chip will be disabled and won't be visible via lspci (so it won't draw any power from the battery)

**reboot-nvidia**
activate nvidia for next boot and prepare xorg conffiles for nvidia. The intel chip won't be visible via lspci.

**reboot-optimus**
activate both gpu's for next boot and prepare xorg conffiles for intel. NOTE: intel/nvidia hot-switching is currently not possible.

**nv-off**
For Optimus Mode only! This will disable the nvidia chip to save some energy. NOTE: intel/nvidia hot-switching is currently not possible.

**nv-on**
For Optimus Mode only! This will enable the nvidia chip. NOTE: intel/nvidia hot-switching is currently not possible.

**config-intel**
This option is for emergency purposes. If xorg can't start and you are dropped to a text shell after boot fix your configuration by running "display-settings status". If you get "Active GPU: Intel GMA3150" run this Option and restart gdm.

**config-nvidia**
This option is for emergency purposes. If xorg can't start and you are dropped to a text shell after boot fix your configuration by running "display-settings status". If you get "Active GPU: Nvidia GT218" run this Option and restart gdm.

---

### Post by johnnycasher on 2011-06-07
Many many thanks for the hard work mtron! I will test your packages today with my Asus 1015pn.

---

### Post by johnnycasher on 2011-06-08
mtron. I've tested all your list of settings using my Asus 1015pn - OS: Xubuntu 11.04. Everything seems to be working (according to your instructions).

Thank you again for your efforts!

---

### Post by johnnycasher on 2011-06-08
> **doc.maizo said:**
> [Ubuntu Control Center]("http://www.webupd8.org/2011/06/ubuntu-control-center-061-released.html")

This UCC switch between GPU works?

---

### Post by NoYes on 2011-06-08
any1 know about progress with 1015pn and OPTIMUS ? any1 checked how it works now ?

---

### Post by johnnycasher on 2011-06-09
> **NoYes said:**
> any1 know about progress with 1015pn and OPTIMUS ? any1 checked how it works now ?

I've already talked about that. If you follow mtron instructions (selecting the switch to optimus) you can use optimus the way he said:

[B]Q: What is the Optimus Mode for?
A: In this mode both cards are active (but the nvidia chip can be separately powered on or off). The Bumblebee project might make the nvidia gpu useable "on-demand"[/B]

---

### Post by mtron on 2011-06-09
Hello! 

The posted link to "Ubuntu Control Center" does not support our EeePC for gpu switching, but since this UCC is not an official Project either i'd rather prefer getting the support for the 1015pn in the bumblebee project. 

Unfortunately bumblebee does currently not work on the 1015pn, so next step is to get the needed bits glue together and render this small hack here unnecessary.

Some notes if you want to test-drive bumblebee:
- You need to be in optimus mode to install or use bumblebee!
- There are no pre-defined calls to toggle the power state of the nvidia chip shipped with bumblebee, so edit the default calls in the conffiles to "display-settings nv-on" or  "display-settings nv-off"
- backup your xorg.conf.intel and xorg.conf.nvidia because bumblebee installs new versions. (with wrong HorizSync & VertRefresh values...)
- There is still something missing in bumblebee. The nvidia module can't load, so no optirun is possible. 


So if you try it please have a look here [https://github.com/MrMEEE/bumblebee/issues/254](https://github.com/MrMEEE/bumblebee/issues/254) and raise some awareness that the 1015pn is still not working with bumblebee ;)

For now, i think the [acpitools 0.5]("http://ubuntuforums.org/showpost.php?p=10909836&postcount=156")~beta2 works ok on natty, so i will promote beta2 to final.

---

### Post by johnnycasher on 2011-06-09
> **mtron said:**
> Hello! 

The posted link to "Ubuntu Control Center" does not support our EeePC for gpu switching, but since this UCC is not an official Project either i'd rather prefer getting the support for the 1015pn in the bumblebee project. 

Unfortunately bumblebee does currently not work on the 1015pn, so next step is to get the needed bits glue together and render this small hack here unnecessary.

Some notes if you want to test-drive bumblebee:
- You need to be in optimus mode to install or use bumblebee!
- There are no pre-defined calls to toggle the power state of the nvidia chip shipped with bumblebee, so edit the default calls in the conffiles to "display-settings nv-on" or  "display-settings nv-off"
- backup your xorg.conf.intel and xorg.conf.nvidia because bumblebee installs new versions. (with wrong HorizSync & VertRefresh values...)
- There is still something missing in bumblebee. The nvidia module can't load, so no optirun is possible. 


So if you try it please have a look here [https://github.com/MrMEEE/bumblebee/issues/254](https://github.com/MrMEEE/bumblebee/issues/254) and raise some awareness that the 1015pn is still not working with bumblebee ;)

For now, i think the [acpitools 0.5]("http://ubuntuforums.org/showpost.php?p=10909836&postcount=156")~beta2 works ok on natty, so i will promote beta2 to final.

Beta 2 is working! I don't need bumblebee for nothing at this point. Thanks again mtron!

---

### Post by NoYes on 2011-06-10
after running on optimus mode and nv-off, nvidia module still remains in memory. is that correct ?

---

### Post by mtron on 2011-06-10
yes. nv-off / nv-on toggles only the power state of the nvidia chip but does not touch any modules. 

This will hopefully do bumblebee in future.

---

### Post by Markino76 on 2011-06-11
> **mtron said:**
> Hello! 

I fixed some bugs (thanks to all the people sending their logs) and prepared a new version. I hope that 0.5 fixes the bugs with natty and makes reliable switching work.

Please remove any old acpitools package you might have installed 
```
sudo dpkg -r acpitools
```and reinstall the nvidia and intel drivers to ensure everything is in place.
```
sudo apt-get install --reinstall xserver-xorg-core
sudo apt-get install --reinstall nvidia-current
```**Download and Install**

1.) Download and install the acpi_call.ko Kernel module in dkms format. This module will auto update itself for newer kernels. (Not needed if you update from an older acpitools version)

```
wget http://ubuntuone.com/p/dil/ -O acpicall-dkms_0.1_all.deb
sudo dpkg -i acpicall-dkms_0.1_all.deb
```2.) Download and install the acpitools 0.5 deb

```
wget http://ubuntuone.com/p/yN2/ -O acpitools_0.5_all.deb
sudo dpkg -i acpitools_0.5_all.deb
```**Changelog **

[acpitools 0.5]("http://ubuntuone.com/p/yN2/") MD5:f7d7ca729b7c84b59d871e33c0e510e6


**FAQ** 

Q: I have installed the deb. How do i switch the VGA cards ?
A: Go to "Applications - System Tools - Vga Selector" and select either intel, nvidia or optimus

Q: Whats the "Change Default GPU" Option in the gui for?
A: If you reboot without selecting a VGA Card manually the script will fall back to the selected default GPU. You need to provide the root password to change your Default GPU. Available GPU Modes are "intel" (Intel GMA 3150 exclusive mode. The nvidia chip won't be visible via lspci and is powered off) "nvidia" (nVidia GT218 exclusive mode) and "optimus" (Dual VGA Mode)

Q: How can i check the used gpu?
A: sudo display-settings status

Q: When running the script i get "ERROR: Could not load acpi_call.ko. Please rebuild the kernel module". What can i do?
A: You need to install the [acpicall-dkms_0.1_all.deb]("http://ubuntuone.com/p/dil/") kernel module.

Q: What is the Optimus Mode for?
A: In this mode both cards are active (but the nvidia chip can be separately powered on or off). The [Bumblebee project]("https://github.com/MrMEEE/bumblebee/") might make the nvidia gpu useable "on-demand"

**Command Line switches**

the script has more options when called from a terminal with
```
sudo display-settings <option>
```where <option> is one of the following:


Thnak you very much mtron!
It worked for me too... I'm very happy! :popcorn:


Keep up the good work!
Marco

---

### Post by barthus on 2011-06-12
Dear all,

I see that things go well for natty and therefore I updated the first message. The instructions can be found in mtron's message #156.

BTW: I still have 10.10 and give a lot of presentations with the 1015PN (Nvidia, HDMI, VGA)! It is just great, it works perfectly well! Furthermore, travelling is such a pleasure with this netbook, especially in view of the long battery life. With the Intel I have 5-6 hours. In the air-plane it is nice since the 1015PN takes only a bit space. I see always people with 13 and 15 inch screens which is really a joke. 


Cheers.

PS: We already had 21,498 visitors in this thread!

---

### Post by Markino76 on 2011-06-13
Hi guys, I've got one last think to understand/solve: connecting the 1015PN (Natty) on my TV via HDMI.
I can connect it and it seems to work ok but I can't find a way to make it works even if I close the lid (set to black screen when closed) and/or when I restart the netbook: every time I reboot the system I have to detect and reconfigure the display...
Can someone please help me for that thing too?


Thanks!

---

### Post by johnnycasher on 2011-06-13
> **barthus said:**
> Dear all,

I see that things go well for natty and therefore I updated the first message. The instructions can be found in mtron's message #156.

BTW: I still have 10.10 and give a lot of presentations with the 1015PN (Nvidia, HDMI, VGA)! It is just great, it works perfectly well! Furthermore, travelling is such a pleasure with this netbook, especially in view of the long battery life. With the Intel I have 5-6 hours. In the air-plane it is nice since the 1015PN takes only a bit space. I see always people with 13 and 15 inch screens which is really a joke. 


Cheers.

PS: We already had 21,498 visitors in this thread!

Hehe. I have 1015pn too. It's really useful cuz i have to travel a lot too. In wich concerns to the battery life and to the size of the netbook that is just perfect :)

---

### Post by mtron on 2011-06-23
Hello! 

some of you may have read that bumblebee supports our 1015pn now ( [bumblebee commit]("https://github.com/MrMEEE/bumblebee/commit/0435ee9796d2e4785a158c83dd59d395735137d5")). 

This is great news and thanks a lot to aurelgadjo who did the commit patch. Unfortunately there are still some Problems:

- currently bumblebee sets the gpu mode for the next boot every time the nvidia gpu is turned off. Since our test showed that the gpu mode for the next boot should only be set once every boot cycle this is sub-optimal. The system might completly lock up and become unresponsive when doing this. Best would be to change bumblebee to set the next boot vga mode during shutdown

- preformance of the nvidia chip via optirun is bad. I tested this with the game extreme tux racer.  In nvidia exclusive mode i get ~ 80 FPS. when the laptop is booted to Optimus mode and bumblebee's optirun is used i get only 40-50 FPS. Intel preforms the same in intel exclusive & optimus mode with 30 FPS.

- hdmi out does not work in Optimus mode with optirun

- also vdpau acceleration is currently not working with optirun

So until bumblebee gets fixed i will continue to maintain our custom vga switching script. (next version will be compatible with bumblebee so you will be able to use the nvidia gpu in Optimus mode, and switch to dedicated vga modes for intel & nvidia)

Cheers!

---

### Post by Jynxx on 2011-06-24
> **mtron said:**
> Hello! 

I fixed some bugs (thanks to all the people sending their logs) and prepared a new version. I hope that 0.5 fixes the bugs with natty and makes reliable switching work.

Please remove any old acpitools package you might have installed 
```
sudo dpkg -r acpitools
```

and reinstall the nvidia and intel drivers to ensure everything is in place.
```
sudo apt-get install --reinstall xserver-xorg-core
sudo apt-get install --reinstall nvidia-current
```

**Download and Install**

1.) Download and install the acpi_call.ko Kernel module in dkms format. This module will auto update itself for newer kernels. (Not needed if you update from an older acpitools version)

```
wget http://ubuntuone.com/p/dil/ -O acpicall-dkms_0.1_all.deb
sudo dpkg -i acpicall-dkms_0.1_all.deb
```

2.) Download and install the acpitools 0.5 deb

```
wget http://ubuntuone.com/p/yN2/ -O acpitools_0.5_all.deb
sudo dpkg -i acpitools_0.5_all.deb
```

**Changelog **

[acpitools 0.5]("http://ubuntuone.com/p/yN2/") MD5:f7d7ca729b7c84b59d871e33c0e510e6


**FAQ** 

Q: I have installed the deb. How do i switch the VGA cards ?
A: Go to "Applications - System Tools - Vga Selector" and select either intel, nvidia or optimus

Q: Whats the "Change Default GPU" Option in the gui for?
A: If you reboot without selecting a VGA Card manually the script will fall back to the selected default GPU. You need to provide the root password to change your Default GPU. Available GPU Modes are "intel" (Intel GMA 3150 exclusive mode. The nvidia chip won't be visible via lspci and is powered off) "nvidia" (nVidia GT218 exclusive mode) and "optimus" (Dual VGA Mode)

Q: How can i check the used gpu?
A: sudo display-settings status

Q: When running the script i get "ERROR: Could not load acpi_call.ko. Please rebuild the kernel module". What can i do?
A: You need to install the [acpicall-dkms_0.1_all.deb]("http://ubuntuone.com/p/dil/") kernel module.

Q: What is the Optimus Mode for?
A: In this mode both cards are active (but the nvidia chip can be separately powered on or off). The [Bumblebee project]("https://github.com/MrMEEE/bumblebee/") might make the nvidia gpu useable "on-demand"

**Command Line switches**

the script has more options when called from a terminal with
```
sudo display-settings <option>
```

where <option> is one of the following:

This is the most beautiful thing I have ever seen! Thank you!

---

### Post by mtron on 2011-07-01
finally we have a work-around for the power bug in natty :). To fix the kernel power regression on BIOSes with buggy ASPM support. (See LP Bug #760131) do:
```
sudo gedit /etc/default/grub
```

Add "pcie_aspm=force" to the default grub boot parameters. After the edit the line should read:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pcie_aspm=force" 
```

and run update grub to regenerate the boot image:

```
sudo update-grub
```

---

### Post by barthus on 2011-07-01
Hi mtron, I have some questions: 

1. Do you use Ubuntu Natty 64 Bit?

2. Do you think that Linux Mint Katya 64 Bit (11.04) is going to work also with your stuff?

Thx.

---

### Post by mtron on 2011-07-03
yes i use the 64bit Version.

As far as i know Linux Mint has a regular ubuntu "under the hood" so it will most probably work.

---

### Post by JMED106 on 2011-07-13
Hi!

First I want to thank you for all this work you are doing.

I've been using mtron's script untill now, but I always have the same problem. Every time I restart, no matter which card I had activated before, Intel activates.

Example:

I use vga-selector to activate nvidia for the next boot, I restart, nvidia is activated.
I restart again and Intel activates.

Is not a big problem, but I would like to know why is this happening.

Thanks, again.

P.D.: Sorry for my poor English. (I use ubuntu natty)

---

### Post by Nisitiiapi on 2011-07-13
I believe that is by design.  Whenever you want to start with nvidia using mtron's scripts, you have to choose nvidia or else it will boot with intel.

I set mine up to default to nvidia, but I am using the scripts in the first post.

---

### Post by mtron on 2011-07-15
Yes, as Nisitiiapi said, this is intentional "by design".

The latest version (acpitools-0.5) let's you change the default gpu via the gui so you might want to update ;)

---

### Post by mtron on 2011-07-27
CC'ing from a PM:

[QUOTE=KyleHyde]Hello mtron,

I am using 11.04 with the unity interface on the Asus 1015pn.  For some reason, I am not seeming to get that great of battery life.  Which VGA choice is best for battery life?  Is it optimus with nv-off or intel?  Are there other changes necessary to get the most out of the battery life.  If I remember, it was advertised to get around 8 hours with Windows.

Any advice?

Thanks a lot,

Kyle[/QUOTE]

---

### Post by mtron on 2011-07-27
Battery life won't reach 8 hours on linux. Max is ~5 Hours with this netbook on natty. 

To get longest runtime, use the power fix (see this thread, some posts [above]("http://ubuntuforums.org/showpost.php?p=11000927&postcount=172")) and intel GPU.

Also disable un-needed system services (like ubuntu one, tracker, and so on) and turn off wireless and bluetooth & use the lowest display brightness possible.

---

### Post by barthus on 2011-07-27
> **mtron said:**
> yes i use the 64bit Version.
As far as i know Linux Mint has a regular ubuntu "under the hood" so it will most probably work.

Hi mtron.

So, in the last days I tried to install Linux Mint Katya (11.04) 64 Bit onto the 1015PN. The installation was just great, all was recognised including WLAN.

I then installed your scripts:
```

wget http://ubuntuone.com/p/dil/ -O acpicall-dkms_0.1_all.deb
wget http://ubuntuone.com/p/yN2/ -O acpitools_0.5_all.deb
sudo dpkg -i acpicall-dkms_0.1_all.deb
sudo dpkg -i acpitools_0.5_all.deb

```This is what happened during the installation:
```

acpicall-dkms
=============

Selecting previously deselected package acpicall-dkms.
(Reading database ... 122820 files and directories currently installed.)
Unpacking acpicall-dkms (from acpicall-dkms_0.1_all.deb) ...
Setting up acpicall-dkms (0.1) ...
Loading new acpicall-0.1 DKMS files...

Loading tarball for module: acpicall / version: 0.1

Creating /var/lib/dkms/acpicall/0.1/source
Copying dkms.conf to /var/lib/dkms/acpicall/0.1/source...
Loading /var/lib/dkms/acpicall/0.1/2.6.32-27-generic/x86_64...

DKMS: ldtarball Completed.
First Installation: checking all kernels...
Building only for 2.6.38-8-generic
Building for architecture amd64
Building initial module for 2.6.38-8-generic
Done.

acpi_call.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/2.6.38-8-generic/kernel/drivers/acpi/

depmod......

DKMS: install Completed.




acpitools
=========

Selecting previously deselected package acpitools.
(Reading database ... 122832 files and directories currently installed.)
Unpacking acpitools (from acpitools_0.5_all.deb) ...
Setting up acpitools (0.5) ...
options nouveau modeset=0
update-initramfs: deferring update (trigger activated)
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.38-8-generic
Warning: No support for locale: de_DE.utf8
Processing triggers for python-support ...

```After, I have chosen 'Intel' in the preferences and booted the system. However, the 1015PN stopped during the boot and hang. Here is a photo which shows the 'end': [http://imageshack.us/photo/my-images/853/img7568b.jpg/](http://imageshack.us/photo/my-images/853/img7568b.jpg/)
[IMG]http://imageshack.us/photo/my-images/853/img7568b.jpg/[/IMG][IMG]http://imageshack.us/photo/my-images/853/img7568b.jpg/[/IMG]
Then, I restarted the 1015 and chose the 'recovery' boot option in grub. I have chosen 'boot normally' after and got into the shell. There, I tried:
```

shell $ sudo display-settings config-intel
ERROR: Could not load /lib/modules/2.6.38-8-generic/updates/dkms/acpi_call.ko. Please rebuild the kernel module

```and
```

shell $ sudo display-settings reboot-intel
ERROR: Could not load /lib/modules/2.6.38-8-generic/updates/dkms/acpi_call.ko. Please rebuild the kernel module

```Well, after all I removed the packages 'acpicall-dkms' and 'acpitools_0.5_all' and everything worked well again as before: the boot, gnome, etc. 

Do you have any idea? Thanks in advance,

Cheers.

---

### Post by mtron on 2011-07-28
oh, this problem seems to be related to a change in the new kernel that got shipped to natty last week.

Can you please try to manually load the module
sudo insmod /path/to/acpi_call.ko

and check the "dmesg" output afterwards? 

**EDIT** see: [https://github.com/MrMEEE/bumblebee/issues/335](https://github.com/MrMEEE/bumblebee/issues/335)

Please try the following:

/usr/bin/gcc
ls -la /usr/bin/gcc
dkms status

So it seems to be related to a bug in natty's gcc. a "sudo chmod +x /usr/bin/gcc" might fix this.

---

### Post by barthus on 2011-07-28
Thanks mtron.

So, I reinstalled the Linux system to be on the safe side (In fact I have done a tarzip file of the whole system after its very first installation but before doing anything with your stuff. This greatly helps to reinstall the system: Boot from a LiveUSB stick, delete old system and re-install it via the tar file. Reboot).

So, this is what I got before installing your packages:
```

shell:~$ /usr/bin/gcc
gcc: no input files
shell:~$ ls -la /usr/bin/gcc
lrwxrwxrwx 1 root root 7 2011-07-26 00:25 /usr/bin/gcc -> gcc-4.5
shell:~$ dkms status
nvidia-current, 270.41.06, 2.6.38-8-generic, x86_64: installed 
bcmwl, 5.100.82.38+bdcom, 2.6.38-8-generic, x86_64: installed 
shell:~$ 

```Then I installed your stuff, and see what comes out: Many errors (?)!
```

wget http://ubuntuone.com/p/dil/ -O acpicall-dkms_0.1_all.deb
wget http://ubuntuone.com/p/yN2/ -O acpitools_0.5_all.deb
sudo dpkg -i acpicall-dkms_0.1_all.deb
sudo dpkg -i acpitools_0.5_all.deb


yields:



--2011-07-28 11:15:28--  http://ubuntuone.com/p/dil/
Resolving ubuntuone.com... 91.189.89.205
Connecting to ubuntuone.com|91.189.89.205|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 14446 (14K) [application/x-deb]
Saving to: `acpicall-dkms_0.1_all.deb'

100%[======================================>] 14.446      73,8K/s   in 0,2s    

2011-07-28 11:15:29 (73,8 KB/s) - `acpicall-dkms_0.1_all.deb' saved [14446/14446]

--2011-07-28 11:15:29--  http://ubuntuone.com/p/yN2/
Resolving ubuntuone.com... 91.189.89.205
Connecting to ubuntuone.com|91.189.89.205|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 6532 (6,4K) [application/x-debian-package]
Saving to: `acpitools_0.5_all.deb'

100%[======================================>] 6.532       --.-K/s   in 0,09s   

2011-07-28 11:15:31 (73,1 KB/s) - `acpitools_0.5_all.deb' saved [6532/6532]

[sudo] password for ?????: 
**dpkg-deb: error: `acpicall-dkms_0.1_all.deb' is not a debian format archive**
dpkg: error processing acpicall-dkms_0.1_all.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 acpicall-dkms_0.1_all.deb
(Reading database ... 122827 files and directories currently installed.)
Preparing to replace acpitools 0.5 (using acpitools_0.5_all.deb) ...
Unpacking replacement acpitools ...
rm: cannot remove `/etc/rc0.d/K10vga': No such file or directory
rm: cannot remove `/etc/rc6.d/K10vga': No such file or directory
cp: `/usr/lib/nvidia-current/xorg/libglx.so.270.41.06' and `/usr/lib/xorg/extra-modules/libglx.so' are the same file
cp: cannot stat `/usr/lib/xorg/modules/extensions/libglx.so.intel': No such file or directory
rm: cannot remove `/usr/lib/xorg/modules/extensions/libglx.so.intel': No such file or directory
rm: cannot remove `/usr/lib/xorg/modules/extensions/libglx.so.nvidia': No such file or directory
rm: cannot remove `/etc/modprobe.d/nouveau-kms.conf': No such file or directory
update-initramfs: deferring update (trigger activated)
dpkg: dependency problems prevent configuration of acpitools:
 acpitools depends on acpicall-dkms; however:
  Package acpicall-dkms is not installed.
dpkg: error processing acpitools (--install):
 dependency problems - leaving unconfigured
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for ureadahead ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.38-8-generic
Warning: No support for locale: de_DE.utf8
Processing triggers for python-support ...
Errors were encountered while processing:
 acpitools

```Then, I tried to find 'acpi_call.ko' but couldn't find it.


Hmmm, did you change meanwhile your packages?

---

### Post by thuysanboy on 2011-08-02
[SIZE=2]Hi all,

I just installed Ubuntu 11.04 on 1015PN. I followed Mr.Tron's guide to install acpi tool and it worked properly in terms of power control of nvidia chip. However I couldn't play videos file when in nVidia mode although it runs properly on intel chip set. At first I thought it was software and I installed VLC, but it doesn't work either. I reinstalled the codec packages for h264 and other formats. But the results were the same. Here's the log in terminal when play videos in VLC : 
[/SIZE][I]
hiep@hiep-1015PN:~$ vlc
VLC media player 1.1.9 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[0x9998914] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
Blocked: call to setlocale(6, "")
Warning: call to srand(1311802499)
Warning: call to rand()
Blocked: call to setlocale(6, "")

(process:1769): Gtk-WARNING **: Locale not supported by C library.
    Using the fallback 'C' locale.
Warning: call to rand()
Warning: call to rand()
Warning: call to rand()
Warning: call to rand()
libva: libva version 0.31.1
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/dri/nvidia_drv_video.so
libva: va_openDriver() returns -1
[0x9ace244] signals interface error: signal 17 overriden (0x28e24c0)
[0x9ace244] signals interface error:  /usr/lib/libQtCore.so.4(?)[(nil)]
[0x9ace244] signals interface error: signal 17 overriden (0x28e24c0)
[0x9ace244] signals interface error:  /usr/lib/libQtCore.so.4(?)[(nil)]
[/I]
[SIZE=2]I guess there's something wrong with the driver. I tried to reinstall the nVidia-current driver but it didn't help. In flash video, nVidia chip still work, however it couldn't run full screen 720p video on Vevo smoothly, I don't know the nVIdia GPU runs full power or not? Could anyone check this for me? 

Thanks, [/SIZE]

---

### Post by zoltux on 2011-08-03
I worked through the various information about 1015pn optimus and mtrons scripts, but (at least) one question remains:

Are the mtron-scripts necessary for bumblebee or can I safely remove them and use only the bumblebee?

---

### Post by mtron on 2011-08-04
@ barthus: Seems there was a bug in ubuntu's kernel. To rebuild the acpi_call kernel module just purge the installed package and re-download & install it. Everything works after that.

@ zoltux: of course you can use bumblebee alone. 

Current bumblebee problems are:
- no intel/nvidia only modes
- no vdpau acceleration
- no hdmi audio/video out
- bad preformance of the nvidia chip with bumblebee's optirun

@ thuysanboy: vlc does not use nvidias vdpau directly. It uses the so called "vaapi". So you need to install this lib and the fitting nvidia vdpau backend for vaapi.

Still i recommend mplayer /smplayer with direct vdpau support. It has much better performance compared to vlc's vaapi

---

### Post by thuysanboy on 2011-08-05
Thank you a lot, mtron!

Actually I installed smplayer before and it didn't work as VLC. However you said it use vdpau directly to decode video, so I selected its output driver (Option->General->Video->Output driver) to vdpau (default is XV). And it does work! Now I can enjoy HD movies! :popcorn:
I also looked for the libva and nvidia vdpau-va driver to test it with VLC. It require much more work to do, and I'm satisfied with SMPlayer. But here're the link to download all those needed files (may be?) to let VLC work for one who interests: [http://www.splitted-desktop.com/~gbeauchesne](http://www.splitted-desktop.com/~gbeauchesne)

---

### Post by barthus on 2011-08-05
> **mtron said:**
> @ barthus: Seems there was a bug in ubuntu's kernel. To rebuild the acpi_call kernel module just purge the installed package and re-download & install it. Everything works after that.

Well, meanwhile I re-installed the system and gave it a second try and installed your packages. It worked once (I have chosen Intel, then reboot) but then I got into the same problem ([message]("http://ubuntuforums.org/showpost.php?p=11093087&postcount=180") 180), which I described some days ago,  after a second boot. So, it failed again and I have no idea why. :(

I then tried my old procedure (message #1), and it is quite amazing: It works! Don't ask me why. 


Notice that it wasn't due to the problem you mentioned:

> Please try the following:
/usr/bin/gcc
ls -la /usr/bin/gcc
dkms status

So it seems to be related to a bug in natty's gcc. a "sudo chmod +x /usr/bin/gcc" might fix this.     
The gcc compiler worked, there was no error.

---

### Post by rodvil on 2011-08-13
Hello!

I see you have been helping plenty of guys with this problem. I hope you can hep me.

I've been going around trying to make this Optimus think to work. I tried to install bumblebee but it never worked. Now I tryed your way and still nothing.
This is what I get on the last step of your process (i'm running Lubuntu 11.04)

```
rodvil@mini-asus:~$ sudo dpkg -i acpitools_0.5_all.deb
(Reading database ... 123210 files and directories currently installed.)
Unpacking acpitools (from acpitools_0.5_all.deb) ...
dpkg: error processing acpitools_0.5_all.deb (--install):
 trying to overwrite '/etc/X11/xorg.conf.nvidia', which is also in package bumblebee 2.2.0-1~nattyubuntu10
rm: cannot remove `/etc/rc0.d/K10vga': No such file or directory
rm: cannot remove `/etc/rc6.d/K10vga': No such file or directory
cp: cannot stat `/usr/lib/xorg/modules/extensions/libglx.so.intel': No such file or directory
rm: cannot remove `/usr/lib/xorg/modules/extensions/libglx.so.intel': No such file or directory
rm: cannot remove `/usr/lib/xorg/modules/extensions/libglx.so.nvidia': No such file or directory
rm: cannot remove `/etc/X11/xorg.conf': No such file or directory
rm: cannot remove `/etc/modprobe.d/nouveau-kms.conf': No such file or directory
update-initramfs: deferring update (trigger activated)
Processing triggers for desktop-file-utils ...
Processing triggers for ureadahead ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.38-10-generic
Errors were encountered while processing:
 acpitools_0.5_all.deb
rodvil@mini-asus:~$
```

Thanks for the help!

---

### Post by barthus on 2011-08-15
> **rodvil said:**
> Hello!

```
rodvil@mini-asus:~$ sudo dpkg -i acpitools_0.5_all.deb
(Reading database ... 123210 files and directories currently installed.)
Unpacking acpitools (from acpitools_0.5_all.deb) ...
dpkg: error processing acpitools_0.5_all.deb (--install):
 trying to overwrite '/etc/X11/xorg.conf.nvidia', which is also in package bumblebee 2.2.0-1~nattyubuntu10
rm: cannot remove `/etc/rc0.d/K10vga': No such file or directory
rm: cannot remove `/etc/rc6.d/K10vga': No such file or directory
cp: cannot stat `/usr/lib/xorg/modules/extensions/libglx.so.intel': No such file or directory
...

```

Hi.

Looks like you still have some interference with bumblebee. I would completely remove bumblebee (also the deb files via UbuntuTweak or 'sudo apt-get clean'+ 'sudo apt-get autoclean'). Then try again. Or: You re-install the whole system and try again.

However, best is to wait for a response from mtron.

PS: If you try out some of the stuff mentioned in this thread it is highly advisable to perform tests with a fresh install of Ubuntu only, which you can always easily re-install onto your hard drive. For instance:
```
1. Install a new Ubuntu system
2. Update the system
3. Backup the system (look here: [http://ubuntuforums.org/showthread.php?t=81311](http://ubuntuforums.org/showthread.php?t=81311)). It creates a file named: backup.tgz, e.g. placed in the root directory /
```So far so good. Now you can do one test. If the result of this test is negative and you would like to do another one with, again, a new, fresh Ubuntu system, do the following:
```
1. Boot with the live CD
2. Mount the partition of the OS
3. Open a shell and delete as root the whole OS on the partition of your hard disk (in /media/) but not the backup.tgz file
4. Decompress the file backup.tgz
5. Reboot => You have back your system
```

---

### Post by whitec on 2011-08-17
Hello.

I just did a fresh install of 11.04 and installed everything here.  I am having one problem that I am not sure of the cause of, and wondered if anyone else had this.

Anytime I boot with Nvidia, my sound works perfectly fine, but if I reboot into Intel, it does not work, and is grayed out.  When I try to go to sound properities, after a few seconds, it pops up a box saying it is waiting for sound system to respond.

Thx

---

### Post by barthus on 2011-08-18
> **whitec said:**
> Hello.
I just did a fresh install of 11.04 and installed everything here.  I am having one problem that I am not sure of the cause of, and wondered if anyone else had this.

Anytime I boot with Nvidia, my sound works perfectly fine, but if I reboot into Intel, it does not work, and is grayed out.  When I try to go to sound properities, after a few seconds, it pops up a box saying it is waiting for sound system to respond.
Thx

So, you installed mtrons deb files? With the sound I have no idea, best is to wait for mtron since he knows best (he seems to be on holiday I guess). May be, you supply some error outputs ...

---

### Post by KyleHyde on 2011-08-18
When I boot into the system using the intel chip, is the nvidia still running?  I'm looking to get the most battery life out of the computer.  Is using optimus and then turning off the nvidia the best option for battery conservation?

---

### Post by Nisitiiapi on 2011-08-18
If you boot to intel only, nvidia should be off.  You can check in terminal with lspci | grep nVidia.  If nothing shows up, the nvidia chip is off.  You can also do lspci | grep VGA and see if only Intel shows up.

---

### Post by whitec on 2011-08-22
> **whitec said:**
> Hello.

I just did a fresh install of 11.04 and installed everything here.  I am having one problem that I am not sure of the cause of, and wondered if anyone else had this.

Anytime I boot with Nvidia, my sound works perfectly fine, but if I reboot into Intel, it does not work, and is grayed out.  When I try to go to sound properities, after a few seconds, it pops up a box saying it is waiting for sound system to respond.

Thx


I actually figured out my problem.  I messed up this part of the guide, and when I fixed it was good to go.


Search for the "load-module" section in this configuration file and add a  line like:

load-module module-alsa-sink device=hw:1,8

---

### Post by nrabett on 2011-09-09
Many thanks for the scripts, which work with one exception. I used the script for Ubuntu 11.04. When I use the Nvidia card, I am not able to use and external monitor. Both LCD monitors I have tried, are detected as CRT monitors, and are shown as "Disabled" when I look for them in the nvidia-settings GUI. 

My attempts at configuring the monitors have not been successful - even after using gksudo to enter nvidia-settings, and after manually copy-pasting the Nvidia-generated, new xorg.conf file into xorg.conf (also tried to paste it into xorg.conf.nvidia - no luck). Whatever I to, the external screen is black; when I try to switch beween the internal and the external screen, Ubuntu tells me that it can't find any external screen. But it is evidently discovered by nvidia-settings (albeit incorrectly as CRT). The external screens also are shown in Xorg.n.log -  e.g., for one of them: 

```
[    31.729] (II) NVIDIA(0): NVIDIA GPU ION (GT218) at PCI:4:0:0 (GPU-0)
[    31.729] (--) NVIDIA(0): Memory: 524288 kBytes
[    31.729] (--) NVIDIA(0): VideoBIOS: 70.18.82.00.07
[    31.729] (II) NVIDIA(0): Detected PCI Express Link width: 1X
[    31.730] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    31.730] (--) NVIDIA(0): Connected display device(s) on ION at PCI:4:0:0
[    31.730] (--) NVIDIA(0):     Samsung SyncMaster (CRT-0)
[    31.730] (--) NVIDIA(0):     HannStar Display Corp (DFP-0)
[    31.730] (--) NVIDIA(0): Samsung SyncMaster (CRT-0): 400.0 MHz maximum pixel clock
[    31.730] (--) NVIDIA(0): HannStar Display Corp (DFP-0): 330.0 MHz maximum pixel clock
[    31.730] (--) NVIDIA(0): HannStar Display Corp (DFP-0): Internal Dual Link LVDS
[    31.807] (II) NVIDIA(0): Assigned Display Device: DFP-0
[    31.807] (==) NVIDIA(0): 
[    31.807] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    31.807] (==) NVIDIA(0):     will be used as the requested mode.

```

I am not sure if it should actually be necessary to enter nvidia-settings in order to do what I want. I simply want to switch between the screens, and when using the Intel chip, this is possible without configuring anything.

Edit: Curiously, when i check the hardware drivers, Ubuntu tells me that the "version current" of the nvidia driver is installed, "but currently not in use". I suspect that this is why Ubuntu does not know about the connected, external screen.

Edit II: The Ubuntu message concerning the nvidia drivers is evidently an error - the PC obviously uses the Nvidia card.

Editing again: I suspect this is this:
[http://ubuntuforums.org/showthread.php?t=1783636](http://ubuntuforums.org/showthread.php?t=1783636)

---

### Post by mtron on 2011-09-21
Hello 1015PN owners!

[SIZE="3"]Update: See post [#301]("http://ubuntuforums.org/showpost.php?p=11748295&postcount=301") for precise 12.04![/SIZE]

Since oneiric is shaping up pretty well i have prepared a new version of the vga switching helper scripts. 

**News:**
- New GUI using the zenity fork [yad]("http://code.google.com/p/yad/") 
- automatically fix the display configuration if xorg fails to start. So no more text login shell.
- many bugfixes and adjustments for oneiric. Full Changelog is [here]("https://launchpad.net/~mtron/+archive/eee1015pn/+packages")

From now on i publish the packages in a ppa repository to make installing and updating easier. Supported is only oneiric (i386 & amd64) so i suggest you do a clean oneiric desktop install  ;)

**Installation:**
Please check that the ubuntu universe & multiverse Repositories are enabled and your system is fully updated. 

Now open a terminal and type
```
sudo add-apt-repository ppa:mtron/eee1015pn
sudo apt-get update
sudo apt-get install build-essential debhelper module-assistant eee1015pn-acpitools
```

this will install the latest version of the VGA switching scripts as well as its dependencies (like the nvidia drivers, the acpi_call kernel module, ect.). After the install completed reboot. 

[Screenshots]("https://sites.google.com/site/mtrons/howtos/eeepc-1015pn#TOC-VGA-Selector-Screenshots")

**Upgrades from earlier ubuntu releases:**
upgraded installations from natty are not supported nor tested, so make a fresh install! If you really do not want to reinstall see bero's post [#226]("http://ubuntuforums.org/showpost.php?p=11380532&postcount=226") 

**Switching GPUs**
to switch between the power saving intel GMA3150 mode and the nvidia mode open the "vga selector" application and click on the "reboot with..." button. Now choose the GPU Mode you want to use and press ok.

**Set Default GPU Mode**
To set your primary GPU Mode go to the Settings Window and click on the "set default..." button and choose your preferred mode from the drop-down menu.

**Settings**

Each line in the table represents a settings option and it's current status ([COLOR="Green"]green[/COLOR]=on / [COLOR="Red"]red[/COLOR]=off / [COLOR="Yellow"]yellow[/COLOR]=not supported on your Desktop Environment) . To change a setting double click on the corresponding line. 

The available Settings currently include:

[LIST]
[*] **Optimus mode: Auto Disable nvidia chip on boot** 
 If active (green status icon) the nvidia chip is turned off autonatically in Optimus Mode
If inactive (red status icon) the power state of the nvidia chip is not changed in Optimus Mode

[*] **Shortcut: GPU info notify-osd**
If active (green status icon) the Keyboad shortcut 'Ctrl+2' will show a notify-osd bubble with GPU Info 
[IMG]http://ubuntuone.com/03ZKMR4qq7vZqCKOZsxKtD[/IMG] [IMG]http://ubuntuone.com/3o4WCQS8C5mV30xlQgAEKD[/IMG]

The Temperature readings are gathered by using the external application lm-sensors. Install the lm-sensors package and run the auto configuration 

```
sudo apt-get install lm-sensors
sudo sensors-detect
``` 

Just press enter at each question to use the default answer. Only the last question should be answered with 'yes':

> "Do you want to add these lines automatically to /etc/modules? (yes/NO)"[COLOR="DarkRed"]YES[/COLOR] 

[*] **Shortcut: Battery info notify-osd **
If active (green status icon) the Keyboad shortcut 'Ctrl+1' will show a notify-osd bubble with the current Power consumption and remaining battery load value. 
[IMG]http://ubuntuone.com/0w0H50cU6f0UBHgTWEC2zK[/IMG]

[*] **Shortcut: Toggle Super Hybrid Engine (SHE)**
If active (green status icon) the Hardware button to toggle the CPU state will be mapped to Jupiter's 'Toggle SHE State' Script. You need to have the jupiter power management applet installed.

[*] **Log to File **
If active (green status icon) all debug output of the display-settings script will be saved in the logfile /var/log/acpi-call.log

[*] **Generate Debug info**
If active (green status icon) some basic system info is written to a debug file $HOME/eee1015pn-debug.txt
[/LIST]

**Configure HDMI Video out with Nvidia**
see Post [#232]("http://ubuntuforums.org/showpost.php?p=11414521&postcount=232")

**Configure HDMI Audi out**
See the 'Fixes' Section @ [http://mtron.co.nr/howtos/eeepc-1015pn](http://mtron.co.nr/howtos/eeepc-1015pn)


**command line switches**
usage: sudo display-settings <option>  - where <option> is one of the following 

> **auto**: In this mode the script will look for a .vga-selector file written by the GUI script and executes the acpi_call for the desired option (Intel,Nvidia or Optimus mode). It will also prepare the xorg configuration and glx libraries for the next boot. If the script can't find any .vga-selector file it will use the selected default GPU.

**status**: This will output current VGA Mode. E.g "Active GPU: Intel GMA3150 on PCI 00:02.0"

**fix**: This will automatically fix the display configuration depending on the available VGA Chips that can be accessed via lspci. It will also update the nvidia glx libraries after the install of a new(er) nvidia driver version.

**reboot-inte**l: activate intel for next boot. The nvidia chip won't be visible via lspci and is disabled so it won't draw any power from the battery.

**reboot-nvidia**: activate nvidia for next boot. The intel chip won't be visible via lspci.

**reboot-optimus**: activate both gpu's for next boot and prepare xorg conffiles for intel.

**nv-off**: For Optimus Mode only! This will disable the nvidia chip to save some energy.

**nv-on**: For Optimus Mode only! This will enable the nvidia chip.

**config-intel**: prepare libglx.so and xorg.conf for intel

**config-nvidia**: prepare libglx.so and xorg.conf for nvidia

**Bumblebee/ironhide project**
the bumblebee project [https://launchpad.net/~bumblebee](https://launchpad.net/~bumblebee) is working on a way to use the nvidia gpu on demmand. Our eeepc needs to be in Optimus mode to work with bumblebee. bumblebee and this helper script can be installed next to each other but be aware that this is in a very early development state and might break anytime. 

*Update 14/02/2012: Bumblebee 3.0 finally works! See post [#274]("http://ubuntuforums.org/showpost.php?p=11657158&postcount=274") for a short bumblebee install howto.*

Happy hacking ;)

---

### Post by cabbrick1243 on 2011-09-26
Hello mtron!
Thanks for all the info [on your Google Site.]("https://sites.google.com/site/mtrons/howtos/eeepc-1015pn")

I have one question though, and I will work on this and let you know how it goes. Did you ever get the Asus Express Gate running on this? From what I understand thus fare is that it has to be on a Windows compatible partition, and can be installed via wine to that.

I'm not sure if the Express Gate would really be useful, but I am curious as to getting it to work.

---

### Post by mtron on 2011-09-27
Hello! 

I did not finish the update of the google site for oneiric, so please be careful when following this ;)

To get express-gate working you need to edit the splash.idx file, see [http://ubuntuforums.org/showpost.php?p=6608594&postcount=1](http://ubuntuforums.org/showpost.php?p=6608594&postcount=1) or if you wanna make a grub entry for Expressgate:

```
sudo gedit /etc/grub.d/40_custom
```

add at the end:

```
menuentry 'ExpressGate' {
   set root='(hd0,7)'
   linux16 /ASUS.SYS/CE_BZ
}
```

Of course you need to replace the  hd0,7 part and you need to keep the hidden efi partition on the eee's harddrive (i swaped my HDD with a SSD drive, so i can't verify this)

Good luck ;)

---

### Post by berardi1111 on 2011-09-30
Thanks so much for the tool and instructions and everything!!!

I had this setup before but cannot get it working again. I get the following error when attempting to install the display settings gui tool:

Err [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources                                
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main amd64 Packages                         
  404  Not Found

Am I missing something?

Thanks so much

---

### Post by mtron on 2011-10-01
> Supported is only oneiric (i386 & amd64) so i suggest you do a clean oneiric desktop install
So no joy with natty but Oneiric is in a pretty good shape already (or wait for the final release of oneiric that should happen around mid- October).

---

### Post by bdalgetty on 2011-10-04
I'm having the same problem as berardi where I get 404 errors when trying to download the files. I ran into 404 errors when trying to use the acpi call repository listed [http://ubuntuforums.org/showpost.php?p=10909836&postcount=156](http://ubuntuforums.org/showpost.php?p=10909836&postcount=156). Any idea what's going on?

---

### Post by mtron on 2011-10-04
Hello !

Sorry about that. Since i moved to oneiric some time ago i forgot to fix the natty dkms problem. But i did so now and uploaded a working acpi call kernel module for natty and edited the download instructions in the post you linked, so it should be ok now.

But honestly, update to ubuntu oneiric ;)

---

### Post by Sketchworks on 2011-10-13
i appologize for not posting this question somewhere else but on this page [http://sites.google.com/site/mtrons/howtos/eeepc-1015pn](http://sites.google.com/site/mtrons/howtos/eeepc-1015pn) dude says he uses amd64 to utilize the atom cores... super confused sence im not using it and seems to work fine. should i switch? whats the difference? how is it supposed to be better? please let me know cuz ive been googling this... thanks

---

### Post by mtron on 2011-10-13
I'm the "dude" so no probelm ;)

The Processor in the 1015PN is a intel Atom N550. It's a dualcore Procressor with 4 threads. 

So if you use the 64 bit Version of ubuntu your computer will preform significatly smoother when working with integer values (this is relevant if you use encryption or do video en/decoding)  

But if you feel safer with i386 (=32bit) go for it ;)

---

### Post by stronkyz on 2011-10-14
hi to all,
i have installed ubuntu 11.10 and the vga selector from mtron repository, but i have a brightness problem, it's not possibile set the screen with the max brightness... how i can fix it?

---

### Post by mtron on 2011-10-14
was it a update from natty or a fresh install? on what vga chip do you have the brightness problem ? (intel or nvidia)

did you add any parameters to grub?

---

### Post by stronkyz on 2011-10-14
i do a fresh install and i have added the parameters to grub, the problem is with the intel chip

---

### Post by mtron on 2011-10-14
ok, remove both parameters from the grub default line (so that only 'quiet splash' remains) and run 'sudo update-grub' & reboot

If this fixes the brightness problem try to find out if the acpi_osi=Linux  or the pcie_aspm=force parameter causes this, Thanks!

---

### Post by stronkyz on 2011-10-14
thanks mtron!!!
the 2 parameters don't create problems, i think it's because i put some paramenters between quiet splash.

---

### Post by mtron on 2011-10-14
Ok cool. Thanks for checking. Keep us Updated if you find the cause of your problem.
Cheers!

---

### Post by Klaster on 2011-10-14
Many thanks, mtron! Everything working fine after updating with your package (had issues starting lightdm beforehand). :)

---

### Post by mtron on 2011-10-14
you're welcome :D always nice to hear a success story.

---

### Post by Isma-ct on 2011-10-18
Hi,

I'm on Ubuntu 11.10 and 1015pn, the precedent versions of acpitools in precedent Ubuntu versions worked like a charm, but with the last version I can't make the program work.

When I install it and execute display-settings, I obtain the following message:
```
root@ee:~# display-settings 
INFO: arch is i386
insmod: error inserting '/lib/modules/3.0.0-12-generic/updates/dkms/acpi_call.ko': -1 Invalid module format
ERROR: Could not load /lib/modules/3.0.0-12-generic/updates/dkms/acpi_call.ko. Please rebuild the kernel module
```

and when I reboot it gets stuck rebooting and I had to purge the program to be able to reboot.

That's the output of the installation:
```
root@ee:~# apt-get install eee1015pn-acpitools 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
S'insta&#320;laran els paquets NOUS següents:
  eee1015pn-acpitools
0 actualitzats, 1 nous a insta&#320;lar, 0 a suprimir i 0 no actualitzats.
S'ha d'obtenir 0 B/21,3 kB d'arxius.
Després d'aquesta operació s'empraran 81,9 kB d'espai en disc addicional.
S'està seleccionant el paquet eee1015pn-acpitools prèviament no seleccionat.
(S'està llegint la base de dades… hi ha 241116 fitxers i directoris insta&#320;lats actualment.)
S'està desempaquetant eee1015pn-acpitools (de …/eee1015pn-acpitools_0.6.3-0ubuntu1_all.deb)…
S'estan processant els activadors per a ureadahead…
S'estan processant els activadors per a gnome-menus…
S'estan processant els activadors per a desktop-file-utils…
S'estan processant els activadors per a bamfdaemon…
Rebuilding /usr/share/applications/bamf.index...
S'està configurant eee1015pn-acpitools (0.6.3-0ubuntu1)…
cp: cannot stat `/usr/lib/xorg/modules/extensions/libglx.so': No such file or directory
options nouveau modeset=0
update-initramfs: deferring update (trigger activated)
S'estan processant els activadors per a initramfs-tools…
update-initramfs: Generating /boot/initrd.img-3.0.0-12-generic

```

The only error that I see is this:
cp: cannot stat `/usr/lib/xorg/modules/extensions/libglx.so': No such file or directory



Someone had the same issue or know how to fix it?
Thanks.

---

### Post by bero74 on 2011-10-19
At first I would like to thank mtron for all his work making the grafic switching possible on Ubunu!

I just upgraded to ubuntu 11.10 oneiric and also did run into some problems.

Just as previous post the acpi-call module did not compile correctly, but I think that was a result of not removing the old version correctly before installing the new one. At least I got it to compile correctly after the remove. Both the display-setting program and lsmod shows that it does load correctly.

But after the reboot the computer does stop at the splash screen and it seems that gdm does not load. I'm suspecting that the display-setting script have a problem creating the symlinks for the libglx? Will try to investigate this further later on.

Any way removing the acpitools package and reinstalling intel and nvidia xorg drivers makes gmd load correctly again.

---

### Post by mtron on 2011-10-20
> **Isma-ct said:**
> /dkms/acpi_call.ko': -1 Invalid module format

Hello! Please check that you have the build-essential and kernel header package of your used kernel installed.
```
sudo apt-get install build-essential dkms linux-headers-$(uname -r)
```

then try to reinstall the acpi_call package. 
```
sudo apt-get install --reinstall acpi-call-dkms acpi-call-source
```

> **Isma-ct said:**
> 
The only error that I see is this:
cp: cannot stat `/usr/lib/xorg/modules/extensions/libglx.so': No such file or directory

fix this by reinstalling the packages for mesa-glx and nvidia glx
```
sudo apt-get install --reinstall xserver-xorg-core 
sudo apt-get install --reinstall nvidia-current
sudo display-settings fix
```

now restart the xserver.

---

### Post by mtron on 2011-10-20
> **bero74 said:**
> after the reboot the computer does stop at the splash screen and it seems that gdm does not load.

Press <CTRL> + <ALT> + <F2> and login at the text console. Now run
```
sudo display-settings fix
```
and post the output please.


To remove everything:
```
sudo apt-get remove eee1015pn-acpitools
sudo apt-get install --reinstall xserver-xorg-core 
sudo apt-get install --reinstall nvidia-current
```

The laptop will be in nvidia only mode after a reboot.

---

### Post by Isma-ct on 2011-10-20
> **mtron said:**
> Hello! Please check that you have the build-essential and kernel header package of your used kernel installed.
```
sudo apt-get install build-essential dkms linux-headers-$(uname -r)
```

then try to reinstall the acpi_call package. 
```
sudo apt-get install --reinstall acpi-call-dkms acpi-call-source
```



fix this by reinstalling the packages for mesa-glx and nvidia glx
```
sudo apt-get install --reinstall xserver-xorg-core 
sudo apt-get install --reinstall nvidia-current
sudo display-settings fix
```

now restart the xserver.

Hello! Many thanks Mtron, I followed your instructions and still the same error.

```
sudo apt-get install build-essential dkms linux-headers-$(uname -r)
```
That was already installed.

And the error bellow doesn't appear after reinstalling the programs you said.
cp: cannot stat `/usr/lib/xorg/modules/extensions/libglx.so': No such file or directory

But it re-appears after purging (to be able to reboot) and reinstalling eee1015pn-acpitools.


So the output is still:
```
root@ee:~# display-settings fix
INFO: arch is i386
insmod: error inserting '/lib/modules/3.0.0-12-generic/updates/dkms/acpi_call.ko': -1 Invalid module format
ERROR: Could not load /lib/modules/3.0.0-12-generic/updates/dkms/acpi_call.ko. Please rebuild the kernel module

```

And I'm still getting stuck in the splash screen, if I do not purge eee1015pn-acpitools

Any other idea?
Thank you very much!

---

### Post by mtron on 2011-10-20
CC'ing a Private Message to this thread:

[QUOTE=sebbag]Hey mtron, its a kind of strange thing... 

I figured out that the cpu-temp is always that high if I'm using the nvidia-card. The gpu-temp itself is around 78-80°C and my cpu-temp is even higher at 80-85°C.

Do you experience the same? 

Even though I dont know whether the nvidia card is working properly. I tried to view some (hd-videos) at youtube in 720p and it was stucking. 

It seems there was not difference with viewing them with the Intel graphic card. Then I downloaded some 720p and 1080p videos (mp4-format) and still I'm not able to watch them fluently. (I was using vlc) e.g. this one -> [http://www.youtube.com/watch?v=s1bC1kGgM74](http://www.youtube.com/watch?v=s1bC1kGgM74)  nice greetings sebastian[/QUOTE]

Hello !

Yes, the nvidia chip gets very hot over time. That's why we started this thread to turn it off ;)

When running in intel mode on battery (jupiter power saving setting) the temperatures are ok. My values for oneiric:

Core0: 45°c
Core1: 46°c
HDD: 33°c
nvidia: <powered off>
Current power rate on Battery: 770 mA

in nvidia mode on battery (jupiter power saving setting) the oneiric readings are:

Core0: 57°c
Core1: 58°c
HDD: 33°c
nvidia 64°c
Current power rate on Battery: 1266 mA

Of course the temperatures will get higher in AC-Mode with jupiter "Max Preformance" setting. (heavy plad on the gpu)

Core0: 68°c
Core1: 70°c
HDD: 34°c
nvidia 73°c
Current power rate on Battery: <on AC>


Vdpau Benchmarks for oneiric on AC-Line (Jupiter max preformance) with nvidia driver version 280.13

[vdpauinfo & qvdpautest]("http://pastebin.ubuntu.com/714124")


So the compiz Features and new desktop enviroments don't pull a heavier load from the battery. The power consuption compares to the previous releases, imho.

---

### Post by mtron on 2011-10-20
> **Isma-ct said:**
> I followed your instructions and still the same error.

since the acpi_call kernel module does not build in your case the script can't work, thats normal.

So let's find out why it does not build ;) login to a text shell and post "dkms status" or even better, if you have another computer, come to IRC (channel #eee1015pn on freenode.net) to debug this.

---

### Post by Isma-ct on 2011-10-20
> **mtron said:**
> since the acpi_call kernel module does not build in your case the script can't work, thats normal.

So let's find out why it does not build ;) login to a text shell and post "dkms status" or even better, if you have another computer, come to IRC (channel #eee1015pn on freenode.net) to debug this.

That's the output of dkms status:

```
root@ee:~# dkms status
acpicall, 0.1, 2.6.32-27-generic, x86_64: built
acpicall, 0.1, 2.6.38-11-generic, i686: installed
acpicall, 0.1, 3.0.0-12-generic, i686: installed
acpi-call, 240611, 3.0.0-12-generic, i686: installed (WARNING! Diff between built and installed module!)
nvidia-current, 285.05.09, 3.0.0-12-generic, i686: installed

```

Thank you for your time!

---

### Post by mtron on 2011-10-20
it seems you have multiple versions of the kernel modules installed. Remove them:

```
sudo dkms remove acpicall/0.1 --all
sudo dkms remove acpi-call/240611 --all
dkms status
```

check that all acpi*call modules are removed. Now change to the /usr/src folder and run:
```
sudo dkms add -m acpi-call -v 240611 --all
sudo dkms autoinstall -m acpi-call -v 240611

```
After this command you should get a message that the dkms install completed and it should work.

---

### Post by Isma-ct on 2011-10-20
> **mtron said:**
> it seems you have multiple versions of the kernel modules installed. Remove them:

```
sudo dkms remove acpicall/0.1 --all
sudo dkms remove acpi-call/240611 --all
dkms status
```

check that all acpi*call modules are removed. Now change to the /usr/src folder and run:
```
sudo dkms add -m acpi-call -v 240611 --all
sudo dkms autoinstall -m acpi-call -v 240611

```
After this command you should get a message that the dkms install completed and it should work.

Hello Mtron!

I followed your instructions and all seamed to work until I rebooted, that it still gets stuck in the splash screen.

That's the output, all seems okay:
```
root@ee:~# dkms status
acpi-call, 240611, 3.0.0-12-generic, i686: installed
nvidia-current, 285.05.09, 3.0.0-12-generic, i686: installed

root@ee:~# apt-get install eee1015pn-acpitools 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed
  eee1015pn-acpitools
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/21,3 kB of archives.
After this operation, 81,9 kB of additional disk space will be used.
Selecting previously deselected package eee1015pn-acpitools.
(Reading database ... 241116 files and directories currently installed.)
Unpacking eee1015pn-acpitools (from .../eee1015pn-acpitools_0.6.3-0ubuntu1_all.deb) ...
Processing triggers for ureadahead ...
Processing triggers for gnome-menus ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Setting up eee1015pn-acpitools (0.6.3-0ubuntu1) ...
cp: cannot stat `/usr/lib/xorg/modules/extensions/libglx.so': No such file or directory
options nouveau modeset=0
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.0.0-12-generic

root@ee:~# display-settings fix
INFO: arch is i386
INFO: acpi_call Kernel module is available
INFO: Nothing to do. libglx.so.nvidia is up-to-date
INFO: Configuring System for intel
INFO: triggering mesa ldconfig...
INFO: prepare mesa glx lib...
INFO: preparing xorg configuration...
INFO: System configuration for Intel completed

``` 

What could be happening?
Thank you very much!

---

### Post by mtron on 2011-10-20
please post the output of the following commands
```
lspci
lsmod | grep video
cat /etc/X11/xorg.conf | grep -i driver
readlink /usr/lib/xorg/modules/extensions/libglx.so
sudo display-settings status
dmesg | grep -i acpi_call
```

---

### Post by bero74 on 2011-10-20
I feel really silly ... can't find out a way to fetch all the output from display-settings fix without X. :confused:
Redirecting with > output.txt doesn't fetch all the output ...

---

### Post by mtron on 2011-10-21
You can enable logging to file by editing the display-settigns script

```
sudo gedit /usr/bin/display-settings
```

in the settings section on top of the file remove the # from the exec line:

> ## uncomment next line to enable logging to file instead of sdout
exec >> $logfile 2>&1 

now display-settings will output debug info to /var/log/acpi-call.log. To read it use e.g. 'cat /var/log/acpi-call.log'

---

### Post by bero74 on 2011-10-22
OK! Finaly got it to work! :)

First I had to reinstall xserver-xorg-core after installing nvidia-current. Otherwice I ended up without the intel libglx. (Not quite verified.)

Then I installed eee1015pn-acpitools. No errors this time.
Run sudo display-settings reboot-intel.

After the reboot I still ended up with only the splashscreen. No login manager ... Tried to run start lightdm and stop lightdm with no succes. Tried sudo lightdm and voilà lightdm fired up. :confused:

Got tired of fiddling with lightdm and selected gdm as default login manager with sudo dpkg-reconfigure gdm. Rebooted and everything is working since.

---

### Post by mtron on 2011-10-23
bero, did you upgrade from natty?

i never experienced any of this when trying a fresh oneiric install. But great you got it to work!

---

### Post by bero74 on 2011-10-28
Yes, I did an upgrade. Some time maby I will try doing a clean install ...

---

### Post by mtron on 2011-10-31
Hello!

Thanks to the patch submitted by Gerald Schnabel the gui scripts now support LXDE (eee1015pn-acpitools 0.6.6 onwards). 

So we cover now most of the available Desktop Enviroments in ubuntu (unity/unity-2d, gnome-classic/gnome-shell, kde, xfe and lxde).

The update is rolled out via the [eee1015pn-acpitools ppa]("https://launchpad.net/~mtron/+archive/eee1015pn") so you should receive it via the regular system updates.

For potential contributors:

i uploaded the scripts to a bzr branch, so if you found a bug or want to extend the code get the sources via 
```
bzr branch lp:~mtron/+junk/eee1015pn-acpitools
```

If you want to contribute (please do ;) ) make your changes in the source tree and run 
```
bzr diff >> mypatch.diff
```


forward the patch to me and please include a line of text what your patch does.

cheers!

---

### Post by deltha on 2011-11-01
hello everybody, and thanks for all the support you're giving =)
I followed mtron's guide, but it seems I'm not able to use the HDMI out: when I switch to nvidia graphic card my tv is shown on the nvidia settings panel, but I get nothing on the display, and in the display tab (under system settings) it just recognize my netbook display.
Do you have any clue?
Thanks in advance, and sorry if the answer has already been given (I tried to find it but I couldn't).

EDIT: I'm using ubuntu 11.10 BTW...

---

### Post by mtron on 2011-11-01
As you guys might have heard [ubuntu developer summit]("http://uds.ubuntu.com/") is currently taking place. One of the Panels was [hybrid-graphics support]("https://blueprints.launchpad.net/ubuntu/+spec/desktop-p-hybrid-graphics") in ubuntu.

session notes are here [http://pastebin.com/FJg5Dzk4](http://pastebin.com/FJg5Dzk4)

This is a good round up of the current development state. 

Our EeePC's are build with a mux-less hardware design so when running in Optimus mode the video output is routed via the integrated (IGP) chipset and the more intense graphics work is offloaded to the discrete GPU.

Ironhide (formerly known as Bumblebee)  is currently the best/only way to provide  MUXless systems support.  Presently only NVIDIA discrete GPUs are supported.

Still the known problems with Ironhide in Optimus mode persist ( preformance lost, HDMI out not possible ) but the long-term plans look very promising:

> **Kernel & Xorg**
The kernel DRM work required for sharing GPU objects is not too complicated, according to Airlie [1].

The biggest blocker at the moment is that the X server has limitations which prevent using GPU’s without attaching a screen to them. Airlie proposed changes to the X server on the xorg-devel mailing list [2], and he has been doing some work on this area [3].

**Upstream (NVIDIA/AMD) Schedule**
Once the X server re-architecting is finished and released, the drivers just need to add support for the new ABI  in order to work. Highly dependant on when the actual X server release is, of course. Aaron Plattner from NVIDIA has already showed  interest in helping with the redesign work [4], so it’s likely that at least NVIDIA has support for it right from the start.

[1] [http://airlied.livejournal.com/71734.html](http://airlied.livejournal.com/71734.html)
[2] [http://lists.x.org/archives/xorg-devel/2011-March/020557.html](http://lists.x.org/archives/xorg-devel/2011-March/020557.html)
[3] [http://cgit.freedesktop.org/~airlied/xserver/log/?h=drvmodelv2-wip](http://cgit.freedesktop.org/~airlied/xserver/log/?h=drvmodelv2-wip)
[4] [http://lists.x.org/archives/xorg-devel/2011-April/021225.html](http://lists.x.org/archives/xorg-devel/2011-April/021225.html)

So to sum this up:
ubuntu won't do anything and wait for "upstream" to fix this issue. a developer helping at the xorg side would have been a huge step but the only planned action for precise is to "add a early boot startup script to switch the alternatives if user has switched gfx in bios".

Well this might save us 3 lines of code in the switching script :)

---

### Post by mtron on 2011-11-01
> **deltha said:**
> when I switch to nvidia graphic card my tv is shown on the nvidia settings panel, but I get nothing on the display

Hello! 

First: use gnome-classic or xfce / lxde Desktop environment for this. unity and gnome-shell both don't play nice with multi-desktop setups currently. You need to set up your workspaces to show 4 Desktops on a 2x2 grid.   

Now in nvidia-settings go on the "Xserver Display Configuration" Tab and click on your tv (it gets a red border if it's selected) under the image go on Configuration and select "Seperate X-screens".


[IMG]http://ubuntuone.com/3VMyHqlv0X5WpKJXd2iIua[/IMG]


go to the "Save to X Configuration File" button on the bottom of the screen. This is tricky since the button is below our small display and in gnome-shell or unity you cant just scroll down to the next desktop and see the desktop overlapping window. This should work with xfce / lxde though so use "STRG+ALT+DOWN" and switch to the lower workspace to get to the button & press it. 

If you still have problems to get to the "Save to X Configuration File" button use the jupiter panel applet and switch the resolution from 1024x600 to 1024x768. Now the whole nvidia-settings dialog should fit on one desktop


[IMG]http://ubuntuone.com/3mZxk5m2XmIq8bKNyUuaKi[/IMG]


A popup dialog will open and ask for a file name, enter 
```
/etc/X11/xorg.conf.asus1015pn.nvidia
```

and press save. To start an application on the TV screen add the following line at the bottom if your .bashrc file:

```
gedit ~/.bashrc 
```

> alias tv="DISPLAY=:0.1" 

Now logout & back in. Your TV should show you the XFCE desktop wallpaper now and to start an application on the television open a terminal and prefix the app you want to launch with "tv". E.g. if you want to run xbmc on the tv:
```
tv xbmc
```

---

### Post by berardi1111 on 2011-11-04
W: Failed to fetch [http://ppa.launchpad.net/mtron/eee1015pn/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/mtron/eee1015pn/ubuntu/dists/natty/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/mtron/eee1015pn/ubuntu/dists/natty/main/binary-amd64/Packages](http://ppa.launchpad.net/mtron/eee1015pn/ubuntu/dists/natty/main/binary-amd64/Packages)  404  Not Found


I continue to receive the above messages when following the steps on the site.  Can someone please point me in the right direction? I'm no Linux Guru but I know what a 404 error is... is there a new site to use? I am using instructions from the making ubuntu rock site to install graphic switch utility.

Also earlier it was said that it was related to natty, but I am running oneric and I am not explicitly calling the above URL, those error messages occur when I issue the commands:

sudo add-apt-repository ppa:mtron/eee1015pn && sudo apt-get update
sudo apt-get install eee1015pn-acpitools

Appreciate any further pointers you may have! =)

---

### Post by mtron on 2011-11-05
you are trying to install this package on ubuntu natty 11.04. 

This ubuntu version is not supported by the ppa. Only the latest version ubuntu oneiric 11.10 is.

---

### Post by berardi1111 on 2011-11-05
> **mtron said:**
> you are trying to install this package on ubuntu natty 11.04. 

This ubuntu version is not supported by the ppa. Only the latest version ubuntu oneiric 11.10 is.

Sorry if I wasn't clear - I am positively on oneiric the 11.10 newest kernel.  

Any ideas of how I might be able to clear out whatever is making the ppa think I am on natty? I really am not, I swear :)

---

### Post by mtron on 2011-11-05
Hello! 

Was not reading you post till the end. Sorry wont happen again :(  If you are on oneiric this should not happen (D'ohhh) and seems to be a bug in the python-software-properties package so please submit a bugreport about this issue to the ubuntu devs.

To fix this manually change the sources.list entry.
```
sudo gedit /etc/apt/sources.list.d/mtron-eee1015pn-oneiric.list
```

if this file does not exist on your system or has a different name (e.g. mtron-eee1015pn-natty.list) Delete the other file and create a new one with the name given above.

the line inside the text file should read:
```
deb http://ppa.launchpad.net/mtron/eee1015pn/ubuntu oneiric main
```

Now reload your package info and try to reinstall

---

### Post by mtron on 2011-11-14
Hello! 

I'm currently working on a new version with a settings window to manipulate the power state of the nvidia script in Optimus mode, Generate a bugreport and add custom keyboard shortcuts. Currently Keyboard shortcuts only work on gnome based desktops; Patches for other DE's are welcome ;) 

Since this is new and not extensively tested code there might be hidden bugs & malfunctions and i do not want to push it to the ppa for now. So if somebody wants to volunteer beta-testing the new code, please send me a pm. 

[IMG]http://ubuntuone.com/6NjnJmZSxeauSiEId1CRGp[/IMG]

Configuration is very easy: 

Each line in the table represents a settings option and it's current status (green=on / red=off / yellow=not supported) . To change a setting double click on the corresponding line. 

The available Settings currently include:

[LIST]
[*] **Optimus mode: Auto Disable nvidia chip on boot** 
 If active (green status icon) the nvidia chip is turned off autonatically in Optimus Mode
If inactive (red status icon) the power state of the nvidia chip is not changed in Optimus Mode

[*] **Shortcut: GPU info notify-osd**
If active (green status icon) the Keyboad shortcut 'Ctrl+2' will show a notify-osd bubble with GPU Info 
[IMG]http://ubuntuone.com/03ZKMR4qq7vZqCKOZsxKtD[/IMG] [IMG]http://ubuntuone.com/3o4WCQS8C5mV30xlQgAEKD[/IMG]

The Temperature readings are gathered by using the external application lm-sensors. Install the lm-sensors package and run the auto configuration 

```
sudo apt-get install lm-sensors
sudo sensors-detect
``` 

Just press enter at each question to use the default answer. Only the last question should be answered with 'yes':

> "Do you want to add these lines automatically to /etc/modules? (yes/NO)"[COLOR="DarkRed"]YES[/COLOR] 


[*] **Shortcut: Battery info notify-osd **
If active (green status icon) the Keyboad shortcut 'Ctrl+1' will show a notify-osd bubble with the current Power consumption and remaining battery load vale. 
[IMG]http://ubuntuone.com/0w0H50cU6f0UBHgTWEC2zK[/IMG]

[*] **Shortcut: Toggle Super Hybrid Engine (SHE)**
If active (green status icon) the Hardware button to toggle the CPU state will be mapped to Jupiter's 'Toggle SHE State' Script. You need to have the jupiter power management applet installed.

[*] **Log to File **
If active (green status icon) all debug output of the display-settings script will be saved in the logfile /var/log/acpi-call.log

[*] **Generate Debug info**
If active (green status icon) some basic system info is written to a debug file $HOME/eee1015pn-debug.txt
[/LIST]

If a setting does not work and the script exists unexpected, start a terminal and run 'vga-selector-gui' & reproduce the bug. The debug output should tell you the function where it failed.

---

### Post by barthus on 2011-11-15
Mtron,

this looks really, really good! Quite professional. They should include it into Ubuntu. - Unfortunately, I have not much time to try it out ... let's see may be later on.

---

### Post by mtron on 2011-11-15
Hello! 

i already got 2 nice people testing, so let's see what they think. If everything works out good i will push it to the ppa in the coming days.

> They should include it into Ubuntu

well, this means i need to support it for various releases over the whole support time. To be honest: i do not want to do that...

---

### Post by mtron on 2011-11-16
Hello! 

I've just pushed a new version to the ppa, so eee1015pn-acpitools 0.6.7 should be installed when you run your next system update. 

The changes in this Version are already explained in Post [#237]("http://ubuntuforums.org/showpost.php?p=11455505&postcount=237")

A 'diff' for the previous Version 0.6.6 is provided at the [bzr webfrontend]("http://bazaar.launchpad.net/~mtron/+junk/eee1015pn-acpitools/revision/28?remember=1&compare_revid=1")  

Happy Hacking ;)

---

### Post by mtron on 2011-11-30
Hello! 

2 weeks since release and over 200 people downloaded (and presumeably use) it already. This is a much larger number than i anticipated so i'm surprised about the huge download stats .. 

I thought that i have 10 - 20 users max :) Guess i was wrong :P

4 bug reports came in and it turned out all of them were using a unsupported distribution. 

So a general word of warning: 
- Linux Mint 12 / Linux mint Debian Edition is not tested and not supported! 
- Debian stable / unstable is not tested and not supported! 

Supported Distribution of the current Version is only Ubuntu Oneiric 11.10 (32bit & 64bit) with unity, unity-2d, gnome-shell, gnome-fallback, xfce, kde and lxde desktop.

Sorry guys... it's not possible for me as a hobbyist to support various distributions and releases. Hope you understand.

---

### Post by mirthless on 2011-12-01
mtron: no apologies necessary. it`s amazing how much work you put into providing us with the goods! thanks so much, from me and my eee!

---

### Post by Tersus* on 2011-12-11
Ich wollte mtron ebenfalls meinen Dank noch mal offiziel aussprechen! 


Allerdings habe ich noch eine Frage. Ist diese Seite "http://sites.google.com/site/mtrons/howtos/eeepc-1015pn" aktuell? Gibt es eine noch aktuellere Seite? Danke für die Antwort! 

Grüße!

---

### Post by mtron on 2011-12-15
yes, the page you linked is the place where i collect all the tweaks for our Eee's.

What makes you think that it's not up-to-date?

---

### Post by Ron Ronsen on 2011-12-17
Hello together.

I have a little problem with the GPU info notify-osd (Ctrl+2) at the Eee PC 1015PN GPU Tool.

It works, but there is no temperature shown with Nvidia & Intel GPU.
Is there a way to enable it?


Thanks,

RonRonson@BalticSea

---

### Post by mtron on 2011-12-17
Hello!

This function uses the nvidia-settings program (command line version) so check that [nvidia-settings]("apt://nvidia-settings") is installed.

If it is, please post the output of
```
nvidia-settings -q all | grep -i temp | head -1
```

---

### Post by Ron Ronsen on 2011-12-17
Ok. nvidia-settings is intalled.

That's the output:

(nvidia-settings:2519): Gtk-WARNING **: Im Modulpfad »pixmap« konnte keine Themen-Engine gefunden werden,

---

### Post by mtron on 2011-12-17
There is something wrong with your installation that has nothing to do with my package. Can you run the nvidia-settings program at all?

Unrelated to your specific issue there is another ugly bug in this function. I'm an idiot.... Just realized that i did something very stupid there. D'ohhh 

I will fix this in the coming days but now it's time to hit the Saturday nightlife ;)

---

### Post by Ron Ronsen on 2011-12-17
Yes, i can run Nvidia-Settings without problems and it's showing me the temperature under "Thermal Settings".

--> I open the terminal and run various programs (cheese, pinta, guvcview etc.) and everytime i get this "Gtk-WARNING **: Im Modulpfad »pixmap« konnte keine Themen-Engine gefunden werden, 		                   		  		  		  		  		 		 			 				".

I think i've got a major problem.

So i will try a new installation of Ubuntu 11.10 (64bit) and then we will see.


But like you said, it's Saturday and we want to have some fun... :)

---

### Post by mtron on 2011-12-20
Hello! 

The nVidia Gpu Temperature detection of the GPU info notify-osd (Ctrl+2) script is fixed in eee1015pn-acpitools Version 0.6.8 that should get installed when you run the next system update.

Thanks to "Ron Ronsen" for reporting this bug.

Cheers!

---

### Post by Nisitiiapi on 2011-12-20
Temperature seems to be working great now, mtron.  Thanks.  It was showing strange values like "8.°C" before.  Now, shows "73 °C".

---

### Post by Ron Ronsen on 2011-12-23
Yeah, thank you for fixing this issue. Now it shows the correct temperature. 

But one question: Does the Intel 3150 in our Eee's have a sensor for temperature?

I didn't think so, or?

---

### Post by mtron on 2011-12-23
The intel GMA 3150 is embedded in the Atom CPU (a so called 'Integrated graphics processor') so i took the CPU temperature reading from Core0 for the notify osd.

---

### Post by Ron Ronsen on 2011-12-23
I see, in Intel-Mode i've got the same problem...

No temp is shown. Only "Temp:°C"

Hmmmmmm...

---

### Post by Tersus* on 2011-12-23
> **mtron said:**
> yes, the page you linked is the place where i collect all the tweaks for our Eee's.

What makes you think that it's not up-to-date?

Ein paar winzige Fehler habe ich gefunden. Wahrscheinlich liegt es auch an meinem System. Ich nutze nicht, wie empfohlen, Ubuntu sondern auf eigene Gefahr hin Linux Mint 12. 

[QUOTE=http://sites.google.com/site/mtrons/howtos/eeepc-1015pn]

**Multitouch II :** [COLOR=Red]...[/COLOR]

```
sudo apt-get build-dep xserver-xorg-input-synaptics
```[/QUOTE]

Führt bei mir zu der Ausgabe: "[FONT=Courier New]E: Quellpaket für xserver-xorg-input-synaptics kann nicht gefunden werden[/FONT]"

[QUOTE=http://sites.google.com/site/mtrons/howtos/eeepc-1015pn]

**Set Gdebi as default file handler for debian packages**

```
gedit ~/.local/share/applications/mimeapps.list
```[/QUOTE]


Das Verzeichnis "share" enthält bei mir gar kein weiteres Verzeichnis "applications", geschweige denn eine "mimeappps.list". 

[QUOTE=http://sites.google.com/site/mtrons/howtos/eeepc-1015pn]

**Reduce Size of the Unity Application Launcher**

```
sudo apt-get install compizconfig-settingsmanager
```[/QUOTE]

Es wurde ein '-' vergessen: [FONT=Courier New]compizconfig-settings[COLOR=Red]-[/COLOR]manager[/FONT]

Mehr ist mir jetzt spontan nicht aufgefallen. Sind halt nur Kleinigkeiten.

---

### Post by Ron Ronsen on 2011-12-24
Happy X-mas to all !!!

---

### Post by mtron on 2011-12-25
@ Tersus: Thanks, i'll correct those. Keep them coming ;)

@ Ron Ronsen: check that the package [lm-sensors]("apt://lm-sensors") is installed and run 
```
sudo sensors-detect
```

if it still does not work post the output of "sudo lsmod" Maybe lm-sensors loaded the wrong kernel modules. 

Merry Xmas!

---

### Post by Ron Ronsen on 2011-12-26
Thx mtron. It was the missing "lm-sensors" package. After installing it, i run 

"sudo sensors-detect" 

in a terminal, he asks some questions and  i pressed ENTER each time.


The last question is:

"Do you want to add these lines automatically to /etc/modules? (yes/NO)"

I prefer "yes"


And after that i run 

"sudo service module-init-tools start"

[FONT=Verdana]
Now it shows the temperature of the GMA 3150 by pressing Ctrl+2. Even after a reboot :)[/FONT]



Ron Ronsen

---

### Post by mtron on 2011-12-26
Ok coolio ;)

I have updated the instructions at post [#237]("http://ubuntuforums.org/showpost.php?p=11455505&postcount=237").

Thanks!

---

### Post by barthus on 2011-12-26
Hi all,

Merry Christmas! 

So, since the start of this thread we have had 259 contributions and stunning 43 222 visitors. Good work!

Cheers.

---

### Post by barthus on 2012-01-16
Hi mtron.

I have a question: I would like to encrypt my whole system + all partitions I have on the 1015PN. Does your tool still work under such conditions? Have you ever tried to encrypt the system? Which Ubuntu version should I take?

Thanks for some advices ... .

---

### Post by mtron on 2012-01-16
Hello! 

It should work just fine on oneiric with the latest version. If not, please send me a bugreport via the gui.

Best,
mtron

---

### Post by red-flex on 2012-01-25
Hey mtron!

Yesterday i decided to give ubuntu a new chance on my 1015pn. ;-)
i installed Xubuntu 11.10 (home is encripted), updated whole system and followed your steps to install vga-selector.
but somehow there are some problems. first thing was that the acpi module was build in the wrong direction (was put in lib/modules/3.0.0-12-generic/..., not in lib/modules/3.0.0-15-generic/...).
at first i thought acpi build failed so i did it manually :D 

the other thing is that the gui does not work fine, my desktop environment is not supported (xfce?)- fallback menue!
but which one are really supported? gnome?

btw. the script display-settings  itself works fine :-) good job!

---

### Post by mtron on 2012-01-26
> first thing was that the acpi module was build in the wrong direction (was put in lib/modules/3.0.0-12-generic/..., not in lib/modules/3.0.0-15-generic/...)

oh. very strange... the acpi_call dkms is not my work. it's build by martin juhl but i will have a look if i can find the bug. Wondering why you are the only one who got hit by this malfunction. Can you please find & post the dkms build log so i can debug this?

> my desktop environment is not supported (xfce?)
the xfce support was added by an external contributor, so it seems he/she missed a desktop session stanza. Those are different depending on the install method. (Xubuntu iso has a different desktop session stanza than a regular ubuntu iso install with xfce packages installed on top of it. Don't ask me why...) 

Anyway, to fix this please open a terminal and post the output of  
```
echo $DESKTOP_SESSION
```

---

### Post by red-flex on 2012-01-26
```
echo $DESKTOP_SESSION
xubuntu
```I will also install lxde, maybe the gui is working there :P

but where can i find this dkms build log file?:oops:  ;-)

Thanks,..!

*edit:

wow damn you're right, there is a "xubuntu" session and a "xfce" session, too. in xfce there is no problem with the gui :-)

After installing lubuntu from the official sources i got three more sessions! In "Lubuntu" and "LXDE" the gui works, except in "Lubuntu-Netbook", but that does not matter its a really ugly desktop :-D

---

### Post by mtron on 2012-01-26
ok, Thanks. I have added the other stanza for xfce. Could you please also post the $DESKTOP_SESSION output for Lubuntu-Netbook login session?

> **red-flex said:**
> 
but where can i find this dkms build log file?

taken from the ubuntu [dkms wiki page]("https://help.ubuntu.com/community/Kernel/DkmsDriverPackage") :

If there are problems with failed DKMS builds and the /var/lib/dkms/${PKG_NAME}/${PKG_VERSION}/build/make.log is almost empty of useful information add the make debug option (-d) to the dkms.conf MAKE="" configurations.

That'll ensure make reports everything it is doing to the log-file.

Cheers!

---

### Post by finny388 on 2012-01-29
mtron, thank you so much for all your help to others with their 1015PNs.

I'm running xubuntu 11.10. I've tried to follow the steps on your "making it rock" page but it would never output to hdmi. (everytime I reboot with nvidia selected, nvidia doesn't load and when I start it it says the intel GPU is being used)

1. I too am getting "my desktop is not supported". I just added the repo and installed acpitool so I thought it would now be since you added the stanza.

2. Do I have to have my laptop screen enabled as in the instructions? My tv is my only needed display (the laptop sits behind it).

3. Do I want to follow "https://sites.google.com/site/mtrons/howtos/eeepc-1015pn#TOC-Install-Ubuntu" or some post in this thread?

The whole reason I bought a new laptop was to be able to display HD video quality on my tv (by linux). I'm so grateful you are making this possible.

I'm willing to fresh install if need be with xubuntu or ubuntu.

---

### Post by mtron on 2012-01-30
Hello! 

To fix the gui for xubuntu copy & paste the following in a terminal session while you are logged in your Desktop Enviroment:

```
gksudo gedit /usr/bin/vga-selector-gui
```

Change the line 658 (close to the end of the file) to read:
```
elif [[ $DESKTOP_SESSION = 'xfce' || $DESKTOP_SESSION = 'xubuntu' ]]; then
```

this will add support for the xubuntu login session.

> everytime I reboot with nvidia selected, nvidia doesn't load and when I start it it says the intel GPU is being used

Once you got the fix from above, open the Vga-Selector, click on the 'Advanced' button and double click on the lines 'Generate Debug info' and 'Log to File'. (both status icons will turn green). 

Now please try once again to set the vga mode for the next boot to nvidia, reboot and if it still does not use nvidia run 
```
sudo display-settings status
```
from a terminal and send me the bugreport. 

To do this either configure Thunderbird to send and receive Mail and use the inbuilt Bug Report Function ( Vga Selector - Advanced - Report Bug ) or attach the files /var/log/acpi-call.log and $HOME/eee1015pn-debug.txt here in the forum.

Thanks!

---

### Post by finny388 on 2012-01-30
Thanks mtron, I will try to get to this very soon.

Can you also respond to questions 2 and 3 please? thank you

---

### Post by finny388 on 2012-01-30
I did the edit and finally saw the interface you developed. Very nice!

Set it to reboot with nVidia and it did. I opened VGA selector again it said I was using nVidia.
But when I went to terminal with sudo display-settings status nothing happened. No error and no text, just another prompt.

So I went into nvidia settings and changed my tv to separate x display, saved the file to /etc/X11/xorg.conf.asus1015pn.nvidia with merge checked, went into vga selector to set nvidia to start on reboot, rebooted, but it ignores my settings and tv goes back to disabled.

I'm open to suggestions and looking forward to your answers to 2 and 3 of my previous post. Thanks.

---

### Post by mtron on 2012-01-31
> **finny388 said:**
>  
But when I went to terminal with sudo display-settings status nothing happened. No error and no text, just another prompt.

that's normal. Once you enable logging to file all output is redirected to the logfile. 

Please send me the logfile and debug info. (see my post above) I can't help you if you don't provide the requested information.

> So I went into nvidia settings and changed my tv to separate x display, saved the file to /etc/X11/xorg.conf.asus1015pn.nvidia with merge checked

So nvidia-settings detects your TV? Once you did the edit to  /etc/X11/xorg.conf.asus1015pn.nvidia just log out and back in. No need to reboot in this stage.

Probably the display driver can't detect the eld info of your TV. Ca you post the output of  ```
cat /proc/asound/card1/eld#1.0
``` (or one of the other eld modes , see the HDMI section [here]("https://sites.google.com/site/mtrons/howtos/eeepc-1015pn#TOC-Fixes") ) 

Also post the /var/log/Xorg.0.log . You might need to load a custom edid.bin for your HDMI device.

> 2. Do I have to have my laptop screen enabled as in the instructions? My tv is my only needed display 

No, you can set the laptop monitor to 'disabled' in the nvidia-settings, but let's first fix your other problems.

> 3. Do I want to follow "https://sites.google.com/site/mtrons/howtos/eeepc-1015pn#TOC-Install-Ubuntu" or some post in this thread?

This website is just a collection of all the information we gathered in this thread to tweak ubuntu for our eee pc's. It's my personal setup howto. You are free to use this information to tweak the system but you don't need to follow this guide step by step 

So, to sum this up: I need the following logfiles / debug information from your system:
[LIST]
[*]/var/log/acpi-call.log
[*]/home/yourusername/eee1015pn-debug.txt
[*]/var/log/Xorg.0.log (with your laptop in nvidia mode, hdmi device connected, xorg.conf.nvidia edited to use seperate X-Screens, and after you tried to logout and back in)
[*]terminal output of ```
cat /proc/asound/card1/eld#1.0
``` (or one of the other eld modes, depending on your hdmi device)
[/LIST]

---

### Post by finny388 on 2012-01-31
okay
I did as you asked
The tv lit up with the an xfce wallpaper I had used before, but not the default one
I can drag the pointer to it like an extended display but can't drag windows to it (when I drag windows to it they fall off the laptop screen but don't appear on the tv). The laptop has the panels, the tv is just blank (except the wallpaper) 

Thank you for all your help so far. Hopefully we're on our way.

(i had to divide the xorg log file as it is 26k and the limit is 19k for upload):)

---

### Post by mtron on 2012-02-01
according to your logfiles everything is working properly. 

> The tv lit up with the an xfce wallpaper I had used before, but not the default one

You can set the used wallpaper for every x-screen in the xfce settings.

> I can drag the pointer to it like an extended display but can't drag windows to it 

Thats normal for the "Seperate X - Screen" configuration. You need to start a window on the desired X-Screen directly and configure your Desktop enviroment to draw both screens. Search the forum for information. That's not the scope of this thread.

There are various ways to Start an application on the TV Screen directly:

- move your mouse pointer to the TV and use 'alt + F2' to open the run dialog and start the application

- add ```
alias tv="DISPLAY=:0.1"
``` to your $HOME/.bashrc file and prefix the app you want to launch with "tv". E.g. if you want to run xbmc on the tv open a terminal on your Laptops X-Screen and type ```
tv xbmc
``` 

Another option is to use "Twinview" instead of Seperate X-Screens in nvidia-settings. this approach allows you to drag windows from one screen to the other but does not allow you to disable the laptop's monitor (among other shortcomings) 

But as stated above this is a configuration issue of your Desktop Environment . The switching script is working as expected.

---

### Post by mtron on 2012-02-01
just wanted to tell you that bumblebee 3 is a huge step forward and works very good here.

As before you can install bumblebee next to our switching script without any problem (in fact you will need the GPU tool to put your laptop in optimus mode) 

a quick bumblebee install howto:

- Open the gpu tool and set it to use 'Optimus' as default gpu mode (Advanced - Set default GPU)
- disable "Optimus Mode: Auto disable nvidia gpu" (Advanced) => bbswitch - which is part of the bumblebee package - takes care of the power state of the nvidia gpu   
- install bumblebee 
```
sudo add-apt-repository ppa:bumblebee/stable
sudo apt-get update && sudo apt-get dist-upgrade
sudo apt-get install bumblebee
sudo usermod -a -G bumblebee $USER => replace $USER with your username
```


- reboot
- test it with 'glxspheres' (drawing ~ 10 FPS using the intel GPU) and 'optirun glxsperes' (drawing ~ 50 FPS using the nvidia GPU)

Current Limitations of bumblebee:

- vdpau is not useable with bumblebee. You need to boot into nvidia exclusive mode to use nvidia's hardware accel for video
- GPU modes are not handeld by bumblebee (we have the switching script so not a real problem for us 1015PN owners ;) )
- The HDMI port is not useable with bumblebee. You need to boot into nvidia exclusive mode to use it.

Thats it. Optimus mode is finally useable! Thanks to the bumblebee devs!

---

### Post by finny388 on 2012-02-01
Thanks for all your help mtron. It is greatly appreciated. I'll be home soon to test making the tv the only enabled display and see if audio works.

Cheers

Once that's settled I may well try bumblebee.

---

### Post by finny388 on 2012-02-01
I set it to tv display only, logged out and in and thought I was on my way.

Now to put the laptop away: I set Closed Lid to Do Nothing, shut the lid and the mouse pointer started moving on it's own and my workspace switcher was lighting up different workspaces like a wind mill.

[LIST]
[*]So I rebooted. Boom. Back to laptop display, tv disabled.
[*]Set it up again. Rebooted, same thing.
[*]Set it up again, logged out and back in, that works - tv displays and laptop off.
[*](this whole time I'm always in nvidia mode)
[*]I tried setting it up again, setting vga selector to reboot with nvidia, 
[*]reboot, settings lost again.
[/LIST]

1. What is the deal with xorg.conf.1015pnvidia file? Is it now default? Is it only used when vga selector is used to reboot? Why does it exist?

2. Why can't the settings survive a reboot?

3. With the display on the tv (after log in/out) the sound continues to come from the laptop.```
aplay -Dplughw:1,7 /usr/share/sounds/alsa/Noise.wav
```
produces sound from the TV
but when I go into Sound Settings/Hardware, I've tried every Profile and *all* of them output to the laptop speakers. I'm stumped.

4. How do I set nVidia powermizer to 500MHz? It always defaults to Adaptive (Perf Level 0). So I set it to Prefer Max Performance (perf level 1) b/c Performance level 2 has always been greyed out.

5. I tested an mkv 720p file just to see how the video was doing but it eventually stutters and shows major artifacts.

Sorry mtron, I thought I as out of the woods but I still have more questions. thanks again.

---

### Post by red-flex on 2012-02-03
hey mtron,

sry i was a bit busy last week!

the session names are those which i put in brackets (from my last reply):
```

xubuntu
xfce
Lubuntu
LXDE
Lubuntu-Netbook

```

mfg

---

### Post by mtron on 2012-02-05
@ redflex: Thanks, i will add those Desktop sessions. 

@finny: > What is the deal with xorg.conf.1015pn.nvidia file? 

There a 2 GPU's in your laptop. Those gpu's require different configurations. The intel gpu config is /etc/X11/xorg.conf.1015pn.intel and the nvidia Xorg config is in xorg.conf.1015pn.nvidia. The switcher script handles the xorg.conf files for the detected gpu's, updates the glx libs and the ld.so configurations. The reason for those hacks is that Xorg does not support multiple GPU's so we need to use those quirks to work around this. 

> 2. Why can't the settings survive a reboot?

They should, and usually do. Please post a Xorg.0.log (and all the other relevant stuff) after a unsucessful reboot so i can debug what's going wrong on your system.

> 3. ...sound continues to come from the laptop.

You need to set the profile on the "hardware" tab and set the device on the output tab. Most players (like mplayer) allow you to define the alsa device via the command line, so direct the mplayer sound output directly to the working plughw device. 

> 4. How do I set nVidia powermizer to 500MHz? 
this is a limitation of the nvidia binary driver. You might want to redirect this question to nvidia.

> 5. I tested an mkv 720p file just to see how the video was doing but it eventually stutters and shows major artifacts.

Seems you were not using vdpau. What player do you use ? (vlc's & totems vdpau support sucks.) Good players for vdpau are all xine based players and recent mplayer builds.

---

### Post by finny388 on 2012-02-06
thanks mtron, will post the files soon

---

### Post by finny388 on 2012-02-06
I use VLC. I love VLC. So sad it does not support vdpau.

I tried gnome mplayer but the audio is 2-3 seconds out of sync with video on various files that sync fine with VLC. (video looks good though)

And there is no setting for audio sync like in VLC. I know I can use the keyboard shortcuts but it is easier to just enter a number like in VLC.

Obviously I got audio working, thanks for the tip. (thought I can already done that but hey, it worked).

thanks again mtron

---

### Post by mtron on 2012-02-07
Hello! 

There are some strage things happening on your system. Let's break it down with your provided logs.

First the switching script sets the GPU for the next boot to nvidia:
```
INFO: display-settings starting at 01:44:57 UTC 03022012
INFO: arch is i386
INFO: acpi_call Kernel module is available
INFO: Configuring System for nvidia
INFO: nvidia glx module is up-to-date
INFO: NVidia GPU enabled
INFO: triggering nVidia ldconfig...
INFO: prepare nVidia glx lib...
INFO: preparing xorg configuration
ln: creating symbolic link `/lib/modules/3.0.0-15-generic/updates/dkms/nvidia.ko': File exists
WARNING: Can't read module /lib/modules/3.0.0-15-generic/updates/dkms/nvidia.ko: No such file or directory
INFO: System configuration for nVidia completed
```

the last warning about nvidia.ko is strange. First it says that it can't create the symlink because the file already exists, then it can't find any file... ??? It seems the cat bites his own tail.

Now you're rebooting the system and it seems everything is in place and the Xserver is starting up (taken from Xorg.0.log)

Your server Layout as detected by the Xserver::
```
[    37.544] (==) Using config file: "/etc/X11/xorg.conf"
[    37.545] (==) ServerLayout "Layout0"
[    37.545] (**) |-->Screen "Screen0" (0)
[    37.545] (**) |   |-->Monitor "Monitor0"
[    37.546] (**) |   |-->Device "Device0"
[    37.546] (**) |-->Input Device "Keyboard0"
[    37.546] (**) |-->Input Device "Mouse0"
```

This is not valid for a Dual X-Screen config. Please attach your edited  /etc/X11/xorg.conf.1015pn.nvidia and make sure that is is the same file as /etc/X11/xorg.conf (during boot the switching script looks at lspci output what vga devices are availalbe and copies either /etc/X11/xorg.conf.1015pn.intel or /etc/X11/xorg.conf.1015pn.nvidia to /etc/X11/xorg.conf )

Probably your edits for dual X-screens have not been saved.

The switching script itself is working. It sends the correct acpi call to set your laptop in nvidia mode, loads the nvidia driver,
```
[    37.601] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    37.602] (II) Module nvidia: vendor="NVIDIA Corporation"
[    37.602] 	compiled for 4.0.2, module version = 1.0.0
[    37.602] 	Module class: X.Org Video Driver
[    37.602] (II) NVIDIA dlloader X Driver  280.13  Wed Jul 27 16:57:12 PDT 2011
```

and maps the correct nvidia glx libs:
```
[    37.554] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/libglx.so
[    37.596] (II) Module glx: vendor="NVIDIA Corporation"
[    37.596] 	compiled for 4.0.2, module version = 1.0.0
[    37.596] 	Module class: X.Org Server Extension
[    37.596] (II) NVIDIA GLX Module  280.13  Wed Jul 27 17:14:51 PDT 2011
[    37.596] (II) Loading extension GLX
```

So, what to do?

- First, update the nvidia driver to the latest version (currently 290.10) from the [x-swat ppa]("https://launchpad.net/~ubuntu-x-swat/+archive/x-updates"). (i hope that the strange symlinking error goes away after this)

- Post your /etc/X11/xorg.conf.1015pn.nvidia for dual X-Screen setup. There must be a mistake in this conffile.

- try vdpau with latest mplayer2 & smplayer as a user friendly frontend. I had very good results with this combo.

get mplayer2 from:
```
sudo add-apt-repository ppa:motumedia/mplayer-daily
sudo apt-get update && sudo apt-get install mplayer2
```

and smplayer
```
sudo add-apt-repository ppa:rvm/smplayer
sudo apt-get update && sudo apt-get install smplayer
```

Configure Smplayer for vdpau:

> **Options - Preferences - General - Video Tab**
 => Output Driver: vdpau 
 => Configure: Set all the checkboxes and the "disable Video filter" checkbox

**Options - Preferences - General - Audio Tab**
  => Output Driver: pulse
  => Checkbox 'Enable Audio Equalizer'
  => Checkbox 'Global Volume'
  => Checkbox 'Use Software Volume Control'

**Options - Preferences - Preformance**
  => Checkbox 'Allow Frame Drop'
  => Loop Filter: 'Skip only on HD Videos'

**Options - Interface**
  => Autoresize: 'Never'

**Options - Advanced - Options for Mplayer** 
  => Extra options for mplayer: 
     -vc ffmpeg12vdpau,ffh264vdpau,ffwmv3vdpau,ffvc1vdpau,


You can set Audio Sync during playback via the + and - Keys on your Keyboard. But sync is usually ok here and HD contend plays very smooth.

This is a 720p HD stream from TV (1280x720, 50Hz, H264) playing at 15% CPU usage with ffh264vdpau in smplayer.

[[Screenshot]("http://ubuntuone.com/06NlzOOI0tZWYZSLwnL1fq")]

Good Luck!

---

### Post by finny388 on 2012-02-07
thanks mtron
You asked for 
/etc/X11/xorg.conf.1015pn.nvidia
for dual x-screen setup
The setup that is lost over reboot is the TV as only display. I hope that's what you meant. Find it attached.

and now I'll move on to your instructions...

---

### Post by finny388 on 2012-02-07
My attempt to install the ppa for the nvidia driver failed. Bad key (see attached)
Then I tried it manually:
```
frank@1015PN:~$ sudo leafpad /etc/apt/sources.list
```> ## manually adding x-swat for new nVidia drivers from [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)
deb [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) oneiric main
deb-src [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) oneiric main```
frank@1015PN:~$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys AF1CDFA9
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.udvn8KVJuQ --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys AF1CDFA9
gpg: requesting key AF1CDFA9 from hkp server keyserver.ubuntu.com
gpg: key AF1CDFA9: "Launchpad PPA for Ubuntu-X" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1

```

Sorry to be so much trouble. Hope you can help.
Thanks.

---

### Post by mtron on 2012-02-08
Hello! 

The signing key is ok. You tried to install a non-existent package ;) do this:
```
sudo apt-get update && sudo apt-get dist-upgrade
```

this will update the nvidia driver. The command to only update the nvidia driver (and not the other packages)
```
sudo apt-get install nvidia-current
```

As suspected your xorg.conf for nvidia was not valid for 2 X-Screens.  Open the nvidia xorg.conf: 
```
sudo leafpad /etc/X11/xorg.conf.asus1015pn.nvidia
```

delete the contents and paste this into the editor window  
```
# /etc/X11/xorg.conf.asus1015pn.nvidia
# for 2 seperate X-Screens on the eee1015pn using the Nvidia GPU on PCI 4:0:0
# X-Screen 1: Laptop Display DFP-0
# X-Screen 2: HDMI Display DFP-1

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Files"
EndSection

Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "HannStar"
    ModelName      "HannStar Display Corp"
    HorizSync       37.0 - 41.0
    VertRefresh     60.0 - 65.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Samsung"
    ModelName      "Samsung-TV"
    HorizSync       15.0 - 81.0
    VertRefresh     49.0 - 76.0
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "ION"
    Option         "NoLogo" "True"
    BusID          "PCI:4:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "ION"
    Option         "NoLogo" "True"
    BusID          "PCI:4:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP-0: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP-1: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

Save the file, connect your HDMI device, and log out & back in. Now your settings should survive a reboot.

I have attached the xorg.conf from above to this post. if you've got problems to make the edit above download it (save it to the 'Downloads' folder in your homedir), open a terminal and copy it to the proper location. (just copy & paste the next line)

```
sudo cp $HOME/Downloads/xorg.conf.asus1015pn.nvidia.txt /etc/X11/xorg.conf.asus1015pn.nvidia
```

---

### Post by finny388 on 2012-02-08
Well the fun never ends.:cry:](*,)
After distupgrade and aptget update I tried to install the driver:> $ sudo apt-get install nvidia-current
[sudo] password for frank: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
nvidia-current is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up vlc-nox (1.1.12-2~oneiric1) ...
/var/lib/dpkg/info/vlc-nox.postinst: 10: /usr/lib/vlc/vlc-cache-gen: not found
dpkg: error processing vlc-nox (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of vlc:
 vlc depends on vlc-nox (= 1.1.12-2~oneiric1); however:
  Package vlc-nox is not configured yet.
dpkg: error processing vlc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mozilla-plugin-vlc:
 mozilla-plugin-vlc depends on vlc; however:
  Package vlc is not configured yet.
 mozilla-plugin-vlc depends on vlc-nox (= 1.1.12-2~oneiric1); however:
  Package vlc-nox is not configured yet.
dpkg: error processing mozilla-plugin-vlc (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            No apport report written because MaxReports is reached already
                          Errors were encountered while processing:
 vlc-nox
 vlc
 mozilla-plugin-vlc
E: Sub-process /usr/bin/dpkg returned an error code (1)


In case this has anything to do with it:
Back when I was having trouble with audio (only in VLC, browser worked and produced sound) I tried to uninstall/reinstall VLC b/c audio used to work. That didn't work. So I thought the uninstall couldn't have been clean. So I followed some instructions and:```
rm -rf /usr/lib/vlc
rm -rf /usr/include/vlc
```
since then I haven't been able to play anything with VLC> Your input can't be opened:
VLC is unable to open the MRL 'file:///media/HITACHI/Videos/homedkd22.avi'. Check the log for details.
It says this for mp4's, avi's, anything I've tried. But I didn't care b/c I'm switching to mplayer. (and I can't find even by googling or desktop searching where this vlc log file is)

mtron, I am open to a fresh xubuntu install though it would have to wait until Sunday to do.

Let me know what you think. Thanks  :-|

---

### Post by mtron on 2012-02-09
> nvidia-current is already the newest version.

all ok, the driver is installed and up to date. 

don't follow those harmful advises like to delete /usr/lib/vlc. Those commands can f*ck up your system pretty bad! As a general guideline look at the "beans count" a person has. The higher the beans count the more likely people know their way around linux/ubuntu and don't give stupid advises like these...

ok, first reinstall vlc
```
sudo apt-get install -f
sudo apt-get clean
sudo apt-get update
sudo apt-get install --reinstall vlc
sudo apt-get dist-upgrade
```

VlC's mozilla browser plugin ist not really good. The already pre-installed totem browser plugin (at least on a regular ubuntu) works much better. if it is not installed on a xubuntu do this:
```
sudo apt-get install totem totem-mozilla totem-plugins totem-plugins-extra
```

now restart firefox and type ```
about:plugins
``` in the address bar. Make sure that only the totem plugins are active.

> mtron, I am open to a fresh xubuntu install

no need for this. we'll get there ;)

---

### Post by finny388 on 2012-02-09
](*,)

```
frank@1015PN:~$ sudo apt-get install -f
[sudo] password for frank: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up vlc-nox (1.1.12-2~oneiric1) ...
/var/lib/dpkg/info/vlc-nox.postinst: 10: /usr/lib/vlc/vlc-cache-gen: not found
dpkg: error processing vlc-nox (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of vlc:
 vlc depends on vlc-nox (= 1.1.12-2~oneiric1); however:
  Package vlc-nox is not configured yet.
dpkg: error processing vlc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mozilla-plugin-vlc:
 mozilla-plugin-vlc depends on vlc; however:
  Package vlc is not configured yet.
 mozilla-plugin-vlc depends on vlc-nox (= 1.1.12-2~oneiric1); however:
  Package vlc-nox is not configured yet.
dpkg: error processing mozilla-plugin-vlc (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            No apport report written because MaxReports is reached already
                          Errors were encountered while processing:
 vlc-nox
 vlc
 mozilla-plugin-vlc
E: Sub-process /usr/bin/dpkg returned an error code (1)

```also, I don't thing I have the current driver: (see the bottom)```
frank@1015PN:~$ cat /var/log/Xorg.0.log[   197.156] 
X.Org X Server 1.10.4
Release Date: 2011-08-19
[   197.157] X Protocol Version 11, Revision 0
[   197.157] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[   197.157] Current Operating System: Linux 1015PN 3.0.0-15-generic #26-Ubuntu SMP Fri Jan 20 15:59:53 UTC 2012 i686
[   197.157] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-15-generic root=UUID=d8bc9135-0842-401f-a11a-a4a841ed5263 ro quiet splash vt.handoff=7
[   197.157] Build Date: 19 October 2011  05:09:41AM
[   197.157] xorg-server 2:1.10.4-1ubuntu4.2 (For technical support please see http://www.ubuntu.com/support) 
[   197.157] Current version of pixman: 0.22.2
[   197.157] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[   197.157] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   197.157] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Feb  6 21:45:38 2012
[   197.158] (==) Using config file: "/etc/X11/xorg.conf"
[   197.158] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   197.159] (==) ServerLayout "Layout0"
[   197.159] (**) |-->Screen "Screen0" (0)
[   197.159] (**) |   |-->Monitor "Monitor0"
[   197.160] (**) |   |-->Device "Device0"
[   197.160] (**) |-->Input Device "Keyboard0"
[   197.160] (**) |-->Input Device "Mouse0"
[   197.160] (**) Option "Xinerama" "0"
[   197.160] (==) Automatically adding devices
[   197.160] (==) Automatically enabling devices
[   197.160] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   197.160] 	Entry deleted from font path.
[   197.160] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[   197.160] 	Entry deleted from font path.
[   197.160] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   197.160] 	Entry deleted from font path.
[   197.160] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[   197.161] 	Entry deleted from font path.
[   197.161] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   197.161] 	Entry deleted from font path.
[   197.161] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[   197.161] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   197.161] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[   197.161] (WW) Disabling Keyboard0
[   197.161] (WW) Disabling Mouse0
[   197.161] (II) Loader magic: 0x823ada0
[   197.161] (II) Module ABI versions:
[   197.161] 	X.Org ANSI C Emulation: 0.4
[   197.161] 	X.Org Video Driver: 10.0
[   197.161] 	X.Org XInput driver : 12.3
[   197.161] 	X.Org Server Extension : 5.0
[   197.163] (--) PCI:*(0:4:0:0) 10de:0a6f:1043:8470 rev 162, Mem @ 0xfa000000/16777216, 0xe0000000/268435456, 0xf2000000/33554432, I/O @ 0x0000ec00/128, BIOS @ 0x????????/524288
[   197.163] (II) Open ACPI successful (/var/run/acpid.socket)
[   197.163] (II) LoadModule: "extmod"
[   197.165] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[   197.165] (II) Module extmod: vendor="X.Org Foundation"
[   197.165] 	compiled for 1.10.4, module version = 1.0.0
[   197.165] 	Module class: X.Org Server Extension
[   197.165] 	ABI class: X.Org Server Extension, version 5.0
[   197.165] (II) Loading extension MIT-SCREEN-SAVER
[   197.165] (II) Loading extension XFree86-VidModeExtension
[   197.166] (II) Loading extension XFree86-DGA
[   197.166] (II) Loading extension DPMS
[   197.166] (II) Loading extension XVideo
[   197.166] (II) Loading extension XVideo-MotionCompensation
[   197.166] (II) Loading extension X-Resource
[   197.166] (II) LoadModule: "dbe"
[   197.167] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[   197.167] (II) Module dbe: vendor="X.Org Foundation"
[   197.167] 	compiled for 1.10.4, module version = 1.0.0
[   197.167] 	Module class: X.Org Server Extension
[   197.167] 	ABI class: X.Org Server Extension, version 5.0
[   197.167] (II) Loading extension DOUBLE-BUFFER
[   197.167] (II) LoadModule: "glx"
[   197.167] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/libglx.so
[   197.211] (II) Module glx: vendor="NVIDIA Corporation"
[   197.211] 	compiled for 4.0.2, module version = 1.0.0
[   197.211] 	Module class: X.Org Server Extension
[   197.211] (II) NVIDIA GLX Module  280.13  Wed Jul 27 17:14:51 PDT 2011
[   197.211] (II) Loading extension GLX
[   197.211] (II) LoadModule: "record"
[   197.212] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[   197.212] (II) Module record: vendor="X.Org Foundation"
[   197.212] 	compiled for 1.10.4, module version = 1.13.0
[   197.212] 	Module class: X.Org Server Extension
[   197.212] 	ABI class: X.Org Server Extension, version 5.0
[   197.212] (II) Loading extension RECORD
[   197.212] (II) LoadModule: "dri"
[   197.213] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[   197.214] (II) Module dri: vendor="X.Org Foundation"
[   197.214] 	compiled for 1.10.4, module version = 1.0.0
[   197.214] 	ABI class: X.Org Server Extension, version 5.0
[   197.214] (II) Loading extension XFree86-DRI
[   197.214] (II) LoadModule: "dri2"
[   197.215] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[   197.215] (II) Module dri2: vendor="X.Org Foundation"
[   197.215] 	compiled for 1.10.4, module version = 1.2.0
[   197.215] 	ABI class: X.Org Server Extension, version 5.0
[   197.215] (II) Loading extension DRI2
[   197.215] (II) LoadModule: "nvidia"
[   197.216] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/nvidia_drv.so
[   197.217] (II) Module nvidia: vendor="NVIDIA Corporation"
[   197.217] 	compiled for 4.0.2, module version = 1.0.0
[   197.217] 	Module class: X.Org Video Driver
[   197.217] (II) NVIDIA dlloader X Driver  280.13  Wed Jul 27 16:57:12 PDT 2011
[   197.217] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[   197.217] (++) using VT number 7
```Hopefully I will have time to respond sometime before Sunday otherwise it will be Sunday. You are a lifesaver mtron.
=D>

---

### Post by finny388 on 2012-02-09
in case this of interest, an ubuntu update failed for SSL shared libraries and one other. Rechecking for updates shows none available:> installArchives() failed: Preconfiguring packages ...
Preconfiguring packages ...
Preconfiguring packages ...
(Reading database ... 
(Reading database ... 5%%
(Reading database ... 10%%
(Reading database ... 15%%
(Reading database ... 20%%
(Reading database ... 25%%
(Reading database ... 30%%
(Reading database ... 35%%
(Reading database ... 40%%
(Reading database ... 45%%
(Reading database ... 50%%
(Reading database ... 55%%
(Reading database ... 60%%
(Reading database ... 65%%
(Reading database ... 70%%
(Reading database ... 75%%
(Reading database ... 80%%
(Reading database ... 85%%
(Reading database ... 90%%
(Reading database ... 95%%
(Reading database ... 100%%
(Reading database ... 242380 files and directories currently installed.)
Preparing to replace libssl1.0.0 1.0.0e-2ubuntu4 (using .../libssl1.0.0_1.0.0e-2ubuntu4.2_i386.deb) ...
Unpacking replacement libssl1.0.0 ...
Setting up libssl1.0.0 (1.0.0e-2ubuntu4.2) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 
(Reading database ... 5%%
(Reading database ... 10%%
(Reading database ... 15%%
(Reading database ... 20%%
(Reading database ... 25%%
(Reading database ... 30%%
(Reading database ... 35%%
(Reading database ... 40%%
(Reading database ... 45%%
(Reading database ... 50%%
(Reading database ... 55%%
(Reading database ... 60%%
(Reading database ... 65%%
(Reading database ... 70%%
(Reading database ... 75%%
(Reading database ... 80%%
(Reading database ... 85%%
(Reading database ... 90%%
(Reading database ... 95%%
(Reading database ... 100%%
(Reading database ... 242380 files and directories currently installed.)
Preparing to replace openssl 1.0.0e-2ubuntu4 (using .../openssl_1.0.0e-2ubuntu4.2_i386.deb) ...
Unpacking replacement openssl ...
Processing triggers for man-db ...
Setting up vlc-nox (1.1.12-2~oneiric1) ...
/var/lib/dpkg/info/vlc-nox.postinst: 10: /usr/lib/vlc/vlc-cache-gen: not found
dpkg: error processing vlc-nox (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of vlc:
 vlc depends on vlc-nox (= 1.1.12-2~oneiric1); however:
  Package vlc-nox is not configured yet.
dpkg: error processing vlc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mozilla-plugin-vlc:
 mozilla-plugin-vlc depends on vlc; however:
  Package vlc is not configured yet.
 mozilla-plugin-vlc depends on vlc-nox (= 1.1.12-2~oneiric1); however:
  Package vlc-nox is not configured yet.
dpkg: error processing mozilla-plugin-vlc (--configure):
 dependency problems - leaving unconfigured
Setting up openssl (1.0.0e-2ubuntu4.2) ...
No apport report written because the error message indicates its a followup error from a previous failure.
No apport report written because MaxReports is reached already
Errors were encountered while processing:
 vlc-nox
 vlc
 mozilla-plugin-vlc
Error in function: 
Setting up vlc-nox (1.1.12-2~oneiric1) ...
/var/lib/dpkg/info/vlc-nox.postinst: 10: /usr/lib/vlc/vlc-cache-gen: not found
dpkg: error processing vlc-nox (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of mozilla-plugin-vlc:
 mozilla-plugin-vlc depends on vlc-nox (= 1.1.12-2~oneiric1); however:
  Package vlc-nox is not configured yet.
dpkg: error processing mozilla-plugin-vlc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of vlc:
 vlc depends on vlc-nox (= 1.1.12-2~oneiric1); however:
  Package vlc-nox is not configured yet.
dpkg: error processing vlc (--configure):
 dependency problems - leaving unconfigured


---

### Post by finny388 on 2012-02-09
Regarding the nvidia driver this may also be interesting:```
frank@1015PN:~$ firefox -V
Mozilla Firefox 10.0
frank@1015PN:~$ Error: API mismatch: the NVIDIA kernel module has version 280.13,
but this NVIDIA driver component has version 290.10.  Please make
sure that the kernel module and all NVIDIA driver components
have the same version.

```

---

### Post by mtron on 2012-02-10
this error about the nvidia driver should go away after you restart. 

We should move this discussion to a new thread. Your problems have nothing to do with the Subject of this thread and i want to keep it on-topic.

So please open a new thread for your vlc problem. I'll try to help with any problem my package might be responsible for, but in your case it's not in my area of responsibility ;)

---

### Post by BenoitL03 on 2012-02-13
Hello, 
 
I have a 1015pn, and i have just installed bumblebee 3.0, bbswitch and virualGL.
When I restart my windows 7 with the optimus GC option, erverything work fine but when I restart my Linux, the intel VGA is no longer detected.
 
I didnt find a solution to this problem.
 
I think if Install acpi_call and restart with optimus option it will work but I dlike to find another solution.
 
Any idea?

---

### Post by mtron on 2012-02-14
hello! 

to use bumblebee 3.0 you need to install the switcher script we're talking about in this thread.

Once you got the package discussed here installed (see post [#196]("http://ubuntuforums.org/showpost.php?p=11273185&postcount=196")) & you preformed the mandatory reboot, open the VGA-Selector , click on the "Advanced" - "set default gpu" Button and choose "Optimus" as Default GPU in the Drop Down menu & press OK.

Now your laptop will stay in Optimus mode across reboots and you can use bumblebee to start applications on the nvidia GPU. I've already posted a small bumblebee install howto for our eee's at post [#274]("http://ubuntuforums.org/showpost.php?p=11657158&postcount=274")

Be aware that bumblebee does not work with vdpau (nvidia's hardware accel for video) and the HDMI port is also not useable. 

If you need those, reboot to nvidia exclusive mode. (VGA Selector - Reboot with...)

---

### Post by BenoitL03 on 2012-02-14
I m on Debian, I will use tour manual method on your google website.
Is your git up to date ?

---

### Post by mtron on 2012-02-14
> I m on Debian, I will use tour manual method on your google website.

Yes. Install the acpi call kernel module, and send the 
```
echo "\OSGS 0x03" > /proc/acpi/call
```

call for optimus mode. You need to do this every boot cycle, so you might want to write yourself a init script to send the call.

> Is your git up to date?
 
I use bzr, but it's not really updated. I am currently working on native debian (& mint debian edition) support, but it's not done and i'll commit it once it's ready for business.

---

### Post by finny388 on 2012-02-17
thanks for all your help mtron
I appreciate it all
I will be away for  a week or two, then return with an update
thanks

---

### Post by duggula on 2012-02-23
Hi mtron,

I used your vga selector and acpi_call with ubuntu 11.04 and everything worked fine. Even with 11.10 but now i got problems with broadcom wlan. If I set the router (german telecom 921) to wlan b+g+n the broadcom card connects but did not offer internet connection. I own a eepc 1015pn.
Did you get same problems? Or do you know a solution? 
Due to these problems I tried a switch to mint debian. wlan is ok here, but optimus works horrible with bumblebee. After a restart the intel card is no longer detected and so bumblebeed can not start. Then I have to start Windows, set optimus there, restart to mint and then it works until the next restart. 
I would like to switch back to ubuntu since I like your solution for vga. Hope anyone has an idea about the wlan problem. If i set the router to b+g everything works dine but slow. :-(

And many thanks for your work!

Bests
Ralph

---

### Post by Nisitiiapi on 2012-02-23
Ralph,

I had problems with the wlan as well -- I could connect, but it lost connection every few minutes and I would have to manually disconnect and reconnect.  The problem only occurred with the N protocol (b and g were fine).  After a long time, I finally found the solution and it has been fine for several months:

1. Install the proprietary Broadcom STA driver from Additional Drivers 
2. Enter terminal:
```
sudo gedit /etc/modprobe.d/blacklist-bcm43.conf
```
     Add  the following to the end of the file:
```
blacklist brcmsmac 
blacklist bcma
```

You might have to restart for the changes to take effect, but basically, the open source driver does not operate with N well at all.  But, when you install the proprietary driver, the system will keep using the open source drivers unless you blacklist them.  Once you blacklist them, it will use the Broadcom STA driver.

If you still have issues, try modifying your wireless settings and set the MTU size to 1500 & IPV6 to Ignore.

Hope that helps.

---

### Post by duggula on 2012-02-24
Hi Nisitiiapi,

many thanks for your fast answer.
I will try it at the weekend, because I first have to reinstall ubuntu.
I will report, if it works.

Bests
Ralph

---

### Post by gewone on 2012-03-07
Hi guys!

I know this is probably mentioned several times in this long thread, but I'm bumping for joy and hopefully someone will fill me in nice and quick. So, here goes.

I have a 1015PN with W7 and 'Buntu running side to side. I never play games or do graphics demanding stuff so I really only need the (less power-consumptive) Intel GMA chip. In Windoze, I use the "Graphics Switcher" and (obviously) have it set to Optimus mode. This is nice. However, sometimes when I restart my computer, and either accidentally let GRUB default into Ubuntu, or deliberately chose to go into Ubuntu.

Nb. I have never dazzled with the graphics in Ubuntu. I did a clean install of proprietary Nvidia drivers and this is what's running. Anyways. The annoying thing is that the next time I reboot and boot into Windoze, I am suddenly into Performance mode, with the ION chip eating power like a mother.

I assume(!) this is because Linux somehow made a ACPI call somewhere during its init/boot, which is later inherited by Windows. Anyways, this sucks. I don't want to use the ION at all, never. So, what ACPI(?) procedure call command lines should I add into what rc.d (on boot script) file to make it always use the Intel GMA chip only? Needless to say; I'm looking for the cleanest approach.

Oh gosh. I wrote a small novel just for a simple matter. It guess this calls for a simplification. Here goes..


[SIZE="3"]TLDR:[/SIZE]
What lines to put in what files in Ubuntu for Intel GMA chipset to be the only one initialized slash used by Ubuntu?

---

### Post by mtron on 2012-03-07
install the eee1015pn-acpitools package, go to 'VGA-Selector - Advanced - Set Default GPU' choose 'Intel' from the drop down menu and press 'ok'.

Now intel will be used automatically as default boot option for the next boot cycle (no matter what OS you boot)

---

### Post by mtron on 2012-03-08
Hello!

i have uploaded Version 0.7.x to the eee-1015pn ppa some days ago (thanks to the people who provided feedback!) which is now ready for ubuntu precise 12.04 LTS.

[SIZE="3"]News[/SIZE]

- added multi-distro support. Scripts work on Oneiric, Precise, Mint 12/13, Debian testing and Mint Debian Edition (incomplete!)
- run second Xserver on nvidia gpu in Optimus Mode and output it via hdmi to a external display device.

Full Changelog & bzr branch is [here]("http://bazaar.launchpad.net/~mtron/+junk/eee1015pn/changes")

[SIZE="3"]What the scripts do[/SIZE]

Our Netbooks (EeePc 1015PN) are a corner case of hybrid graphics  because they have a rather unusual hybird setup. The nvidia chip is directly wired to the display device and hdmi port (most muxless hybrid setups are build without this feature) allowing this model to switch the GPU modes manually or use a dual gpu mode (there is no bios change required to set the gpu mode. Everything is done in Software via sending a acpi_call ). 

This Laptop defaults to nvidia - only mode in Linux (the intel GPU is not visible via lspci) but via sending a specific acpi-call you can set the VGA Mode for the next boot cycle manually.

Available VGA Modes are:

[LIST]Intel GMA 3150 only Mode (the nvidia chip is powered off and not visible via lspci)[/LIST]
[LIST]Nvidia GT218 only Mode (the intel chip is not visible via lspci)[/LIST]
[LIST]Optimus Mode (both chips are visible via lspci => bumblebee works only in this mode)[/LIST]

We have prepared some gui scripts to manage the GPU states for the 1015pn as painless as possible.

[SIZE="3"]Installation[/SIZE]

**Before proceeding, check that your system is fully updated. If the update installed a new kernel reboot before installing this package!**

=> Install the latest version of the VGA switching scripts as well as its dependencies (like the nvidia drivers, the acpi_call kernel module, yad, ect.).

```
sudo add-apt-repository ppa:mtron/eee1015pn
sudo apt-get update
sudo apt-get install build-essential debhelper module-assistant eee1015pn-acpitools
```

If you didn't reboot in the latest installed kernel before installing the eee1015pn-acpitools package (bad boy! ;) ) the acpi call module is missing. 'dkms status' from the terminal should list the acpi_call module as installed for all kernels. If not, trigger the dkms build manually:

```
sudo dkms autoinstall -k $(uname -r) -m acpi_call -v 0.0.1
```

=> install the [jupiter]("http://www.jupiterapplet.org/") power management applet to get SHE support. This is a special power-saving feature. it drastically reduces power consumption (at the price of performance of course) by altering some of the frequencies and voltages on the motherboard.

```
sudo add-apt-repository ppa:webupd8team/jupiter
sudo apt-get update
sudo apt-get install jupiter jupiter-support-eee 
``` 

After the install completed reboot to initialize the acpi state

[SIZE="3"]Configuration[/SIZE]

**Configure Monitors**

Open the VGA Selector and double click on the icon of the active GPU. In intel and optimus mode the default randr manager of your Desktop Environment will open (in nvidia mode the nvidia-settings gui is launched) and assist you in setting up the new screens. The VGA Port works in intel & Optimus mode, the HDMI Port in nvidia & Optimus mode

**Default Xserver settings**

The default settings for the x Server depend on the VGA Mode. /etc/X11/xorg.conf is linked automatically during boot and all changes to this file will be lost.

To change the Default setup edit 
Mode1: [FONT="Courier New"]/etc/X11/xorg.conf.asus1015pn.intel[/FONT]
Mode2: [FONT="Courier New"]/etc/X11/xorg.conf.asus1015pn.nvidia[/FONT]
Mode3: [FONT="Courier New"]/etc/X11/xorg.conf.asus1015pn.intel[/FONT]

**Special case - optimus mode**
Optimus Mode uses the intel GPU & config as default. Same as in bumblebee you can start a new x-server that draws to the Nvidia GPU (see '*Advanced - Optimus : Start Xserver (nvidia) on HDMI*' ) and run another independent X-Server on a external HDMI Display.

Bumblebee draws the window also on the nvidia gpu but puts its output via virtualgl back to the Intel GPU so the HDMI port of our Eee's can't be used.

To edit the default configuration for this second X-server (you need to manually adjust your local config to allow a second Xserver. see post #[325]("http://ubuntuforums.org/showpost.php?p=11901720&postcount=325")) open 
[FONT="Courier New"]/etc/X11/xorg.conf.asus1015pn.optimushdmi[/FONT]


[SIZE="3"]Usage[/SIZE]

Run the gui script via 'System Tools - VGA Selector'

[IMG]http://sites.google.com/site/mtrons/_/rsrc/1321452434418/howtos/eeepc-1015pn/activegpu.jpg?height=207&width=320[/IMG]

The Main Screen shows the current GPU Mode. Double click on the icon to open the native xrandr manager of your Desktop Enviroment. (Supported DE's are unity, unity-2d, gnome-shell, gnome-fallback, cinnamon, xfce, lxde and kde) 

**Reboot Window**

To switch between the power saving intel GMA3150 mode and the nvidia mode click on the "reboot with..." button. Now choose the GPU Mode you want to use and press ok. 

[IMG]https://sites.google.com/site/mtrons/_/rsrc/1316638432762/howtos/eeepc-1015pn/vgasel-boot.jpg?height=193&width=200[/IMG]

**Settings Window**:

Each line in the table represents a settings option and it's current status ([COLOR="Green"]green[/COLOR]=on / [COLOR="Red"]red[/COLOR]=off / [COLOR="Yellow"]yellow[/COLOR]=not supported on your Desktop Environment) . To change a setting double click on the corresponding line. 

[IMG]https://sites.google.com/site/mtrons/_/rsrc/1321451667639/howtos/eeepc-1015pn/vgaseletor-settings.jpg?height=287&width=320[/IMG]

The available Settings are:

[LIST]
[*] _Optimus mode: Auto Disable nvidia chip on boot_
 If active (green status icon) the nvidia chip is turned off autonatically in Optimus Mode
If inactive (red status icon) the power state of the nvidia chip is not changed in Optimus Mode. **NOTE**: Set this to inactive if you want to use bumblebee!
[*] _Shortcut: GPU info notify-osd_
If active the Keyboad shortcut 'Ctrl+2' will show a notify-osd bubble with GPU Info 
[IMG]http://ubuntuone.com/03ZKMR4qq7vZqCKOZsxKtD[/IMG] [IMG]http://ubuntuone.com/3o4WCQS8C5mV30xlQgAEKD[/IMG]
[*] _Shortcut: Battery info notify-osd_
If active the Keyboad shortcut 'Ctrl+1' will show a notify-osd bubble with the current Power consumption and remaining battery load value. 
[IMG]http://ubuntuone.com/0w0H50cU6f0UBHgTWEC2zK[/IMG]
[*] _Shortcut: Toggle Super Hybrid Engine (SHE)_
If active the Hardware button to toggle the CPU state (left on top of the keyboard) will be mapped to Jupiter's 'Toggle SHE State' Script.
[*] _Log to File_ 
If active (green status icon) all debug output of the display-settings script will be saved in the logfile /var/log/acpi-call.log
[*] _Generate Debug info_
If active (green status icon) some basic system info is written to a debug file $HOME/eee1015pn-debug.txt
[/LIST]

**Set Default GPU Window**
To set your primary GPU Mode go to the Settings Window and click on the "set default..." button.

[IMG]https://sites.google.com/site/mtrons/_/rsrc/1316638353771/howtos/eeepc-1015pn/vgasel-default.jpg[/IMG]

[SIZE="3"]FAQ[/SIZE]

**Upgrades from earlier ubuntu releases:**
upgraded installations from oneiric to precise should work without a problem. Just make sure that you eee1015pn-acpitools package is version 0.7.x

You might need to regenerate the glx libs. After the system upgrade completed open a terminal, and run
```
sudo display-settings regenerate-glx
```

**Configure HDMI Video out with Nvidia**
see Post [#232]("http://ubuntuforums.org/showpost.php?p=11414521&postcount=232")

**Configure HDMI Audi out**
See the 'Fixes' Section @ [http://mtron.co.nr/howtos/eeepc-1015pn](http://mtron.co.nr/howtos/eeepc-1015pn)

**Bumblebee/ironhide project**
the bumblebee project [https://launchpad.net/~bumblebee](https://launchpad.net/~bumblebee) is working on a way to use the nvidia gpu on demmand. Our eeepc needs to be in Optimus mode to work with bumblebee. bumblebee and this helper script can be installed next to each other but be aware that this is in a very early development state and might break anytime. 

See post [#274]("http://ubuntuforums.org/showpost.php?p=11657158&postcount=274") for a short bumblebee install howto.

**Supported Distributions**
ubuntu 11.10 and 12.04 & it's direct spins are fully supported (Lubuntu, Xubuntu, Kbuntu, Mint 12 & mint 13).  Debian testing (Mint Debian Edition) is mostly done but gdm start might fail (see debian below)

**Mint 13 with Cinnamon Desktop**
Mint 13 comes with Cinnamon DE and a new Login Manager called Mint Display Manager (mdm). This display manager is still buggy and does not emit a notification event to the system i use to trigger the auto display configuration.

So replace mdm with lightdm. Instructions are [here]("http://www.webupd8.org/2012/06/how-to-use-lightdm-instead-of-mdm-in.html") 

**Debian**
Debian support is mostly done. Manually install the acpi_call dkms package, yad and the lastest eee1015pn-acpitools deb from the ppa. The package does not add any init.d scripts automatically because I'm having problems with them. Since debian does not use upstart, how can i make sure that my scripts finishes before gdm tries to start ? 

If you want to test the init scripts add it via update-rc.d
```
update-rc.d fixvga.debian defaults
```

With the traditional init.d scripts i managed to get it working most of the time but sometimes gdm/kdm starts too fast and the script is not done preparing the configuration for the xserver so you will be dropped to a terminal login shell. Just login and run as root:
```
display-settings fix && /etc/init.d/gdm restart
```

**command line switches**

usage: sudo display-settings <option>  - where <option> is one of the following 

> **auto**: In this mode the script will look for a .vga-selector file written by the GUI script and executes the acpi_call for the desired option (Intel,Nvidia or Optimus mode). It will also prepare the xorg configuration and glx libraries for the next boot. If the script can't find any .vga-selector file it will use the selected default GPU.

**status**: This will output current VGA Mode. E.g "Active GPU: Intel GMA3150 on PCI 00:02.0"

**fix**: This will automatically fix the display configuration depending on the available VGA Chips that can be accessed via lspci. It will also update the nvidia glx libraries after the install of a new(er) nvidia driver version.

**reboot-inte**l: activate intel for next boot. The nvidia chip won't be visible via lspci and is disabled so it won't draw any power from the battery.

**reboot-nvidia**: activate nvidia for next boot. The intel chip won't be visible via lspci.

**reboot-optimus**: activate both gpu's for next boot and prepare xorg conffiles for intel.

**nv-off**: For Optimus Mode only! This will disable the nvidia chip to save some energy.

**nv-on**: For Optimus Mode only! This will enable the nvidia chip.

**config-intel**: prepare libglx.so and xorg.conf for intel

**config-nvidia**: prepare libglx.so and xorg.conf for nvidia

**regenerate-glx:**	regenerate the gpu dependant glx libraries. Use this option if 3d does not work after a distribution upgrade. It will reinstall the xserver & nvidia packages and symlinks the libglx.so files to work with this script.

Note that command Line switches override gui settings. e.g. if you set intel for reboot via the gui, and later run 'display-settings reboot-nvidia' via the terminal, the system will reboot to nvidia mode.

---

### Post by mtron on 2012-03-14
Hello!

this is a tip for all people test-driving precise who got hit by the touchpad bug (not functional after login)

The Elantech Touchpad works in lightdm though so i suspect a specific setting run during gnome startup disables it. 

I did not track this bug down to a specific cause (it might be related to the jupiter power management applet) but a temporary workaround is to reset the touchpad state in dconf:
```
gsettings reset org.gnome.settings-daemon.peripherals.touchpad touchpad-enabled
```

a startup autorun scipt:
```
#!/bin/bash
sleep 8
gsettings reset org.gnome.settings-daemon.peripherals.touchpad touchpad-enabled
```

the sleep is needed on my system to make sure the state gets reset after the desktop finished loading.

---

### Post by barthus on 2012-03-18
mtron.

Excellent work!  As soon as 12.04 is out in April I will change to it, with your script.

Thanks for all !

---

### Post by halestorm222 on 2012-03-19
First, mtron, thank you for your incredible work. You've taken a great piece of hardware and made it usable in the world of Linux, and for your pioneering work, we're all grateful.

I've successfully used your scripts on the 1015pn in Ubuntu, and have had success multiple times.  I recently installed Ultimate Edition 3.01, which you know is based on Natty.

However, now, in trying to configure UE to your script, when I follow these steps:

```
sudo add-apt-repository ppa:mtron/eee1015pn
sudo apt-get update
sudo apt-get install build-essential debhelper module-assistant eee1015pn-acpitools
```


I get:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package eee1015pn-acpitools

```

It updates the repos fine; it just can't find the script. I've searched the thread and no one else has "unable to locate".

Please help. I'm stuck in Nvidia mode for a laptop I need more than 3 hours of battery life from.

Thank you.

---

### Post by mtron on 2012-03-19
Hello 
Ultimate Edition 3.01 is not supported by the ppa (only oneiric and precise based distros are) 

But you can update to UE 3.2 [http://ultimateedition.info/ultimate-edition/ultimate-edition-3-2/](http://ultimateedition.info/ultimate-edition/ultimate-edition-3-2/) which is based on oneiric.

Once you got the new version login to your desktop and copy & paste the output from these terminal commands 

```
echo $DESKTOP_SESSION
lsb_release --id --release --short
gnome-wm --version
gnome-shell --version
```

with this info i can add support for your distro

---

### Post by halestorm222 on 2012-03-19
Thank you for the reply. I'm sorry that you're not supporting 3.01. 

I tried the new 3.2 on my 1015pn, but with the exception of the very first build, all logins (Ubuntu, Gnome, etc) hid the top/bottom taskbars and menus. There wasn't even a way to log off without holding the power button for a hard power off.

After trying updates and without updates, using the "Additional drivers" for Nvidia and the native, downloading extensions for Advanced Settings to add/remove panels, I got frustrated and installed 3.01 over it, knowing that at least *this* would get me a usable desktop. Of course, usable as it is, it's very short-lived.

If it helps you, I can put 3.2 back on the drive as a separate boot option. But it seemed like no matter what I did, I couldn't get access to apps, menu or taskbars.

Kindly advise, and I'll be happy to help you develop, be it for 3.01 or 3.2.. especially if you have ideas for the buggy 3.2 desktop.

---

### Post by mtron on 2012-03-20
hello! 

well, i won't work on natty support, sorry. Reason is that natty will reach EOL in October and is based on the old gnome desktop as well as a old xorg stack.

A lot of configuration details changed from natty => oneiric so i'll focus on new(er) versions. 

You might want to give precise or Linux Mint a try.

---

### Post by halestorm222 on 2012-03-20
As you requested, here are the results for the Ultimate Edition 3.2. Note that, at the login prompt, there are 5 desktops to log into (Gnome 3, ubuntu 2, etc).  Below is the default from the LiveCD.

```

ubuntu@ubuntu:~$ echo $DESKTOP_SESSION
gnome-fallback
ubuntu@ubuntu:~$ lsb_release --id --release --short
Ubuntu
11.10
ubuntu@ubuntu:~$ gnome-wm --version
Compiz 0.9.6
ubuntu@ubuntu:~$ gnome-shell --version
GNOME Shell 3.2.2.1

```While I can understand your desire to avoid supporting a dying 3.01, perhaps 3.2 support will help others since it was just released last week.

Thanks again.  Your scripts are amazing, and the support is even better.

---

### Post by halestorm222 on 2012-03-21
Mtron, 

As I'm sure you gathered from the version-info, I've installed your amazing script and it works perfectly on Ultimate Edition 3.2.

I may be straying off-topic for the thread, but I've also reviewed [your home page]("https://sites.google.com/site/mtrons/howtos/eeepc-1015pn") and followed the steps. Wireless isn't working, with or without activating the STA. The card isn't acknowledged. 

Do you have a trick to get the 1015pn wireless card seen which I may have overlooked? It works fine in Mint, Ubuntu, etc, just not in UE. Thanks!

---

### Post by mtron on 2012-03-21
ah, great you figured it out. I forgot to post that it should already work. Your distro is very close to upstream ubuntu so there are no compatibility problems.

> Do you have a trick to get the 1015pn wireless card seen

The wlan chip in the 105pn is a Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller and is supported by the 'brcmsmac' driver included in the Kernel from 3.0.0 onwards. The modules are bcma and brcmsmac

i have the following modules loaded: 
*lsmod | grep brcmsmac*
```
brcmsmac              631693  0 
brcmutil               17837  1 brcmsmac
mac80211              462046  1 brcmsmac
cfg80211              199630  2 brcmsmac,mac80211
crc_ccitt              12667  1 brcmsmac
```


post the output of 
```
lsmod
lspci -v -s 02:00.0
```

Also make sure that the other (older) drivers for the device are uninstalled 
```
sudo apt-get remove broadcom-sta-source broadcom-sta-common bcmwl-kernel-source
```

---

### Post by halestorm222 on 2012-03-21
Thanks for the reply. After uninstalling the original Broadcom drivers, the output of "lsmod" is

```


wl                   2646601  0 
lib80211               14570  1 wl
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55577  1 vfat
snd_hrtimer            12648  1 
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
acpi_call              12652  0 
kvm_intel              55857  0 
kvm                   336923  1 kvm_intel
parport_pc             32114  0 
ppdev                  12849  0 
joydev                 17393  0 
eeepc_wmi              12722  0 
asus_wmi               19333  1 eeepc_wmi
sparse_keymap          13658  1 asus_wmi
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
snd_hda_codec_realtek   254163  1 
snd_hda_intel          28358  2 
snd_hda_codec          91859  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  2 snd_hda_intel,snd_hda_codec
psmouse                63474  0 
serio_raw              12990  0 
snd_seq_midi           13132  0 
binfmt_misc            17292  1 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  3 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  3 snd_hrtimer,snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  14 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
bcma                   19571  0 
i915                  509554  2 
soundcore              12600  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
drm_kms_helper         32889  1 i915
drm                   196290  3 i915,drm_kms_helper
wmi                    18744  1 asus_wmi
i2c_algo_bit           13199  1 i915
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usb_storage            44173  1 
uas                    17699  0 
ahci                   21634  2 
libahci                25761  1 ahci
atl1c                  36638  0 

```

And the output of "lspci -v -s 02:00.0" is

```

02:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
	Subsystem: AzureWave Device 2047
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at fbffc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: bcma-pci-bridge
	Kernel modules: bcma, brcmsmac

```

As always, much appreciated.

---

### Post by mtron on 2012-03-22
hello!

Try to blacklist the conflicting modules.
```
sudo gedit /etc/modprobe.d/blacklist.conf
```

Add this lines at the bottom of the file
```
#wlan
blacklist wl
blacklist bcma
```

now reboot and see via lsmod what module is in use. If it's still the wrong one, remove the module with 'sudo modprobe -r <modulename>' and load the 'brcmsmac' module

---

### Post by halestorm222 on 2012-03-23
Blacklisted as you suggested. No wireless in UE 3.2 yet. So, must have been the wrong one. I don't know how to identify the right one unless I am random. Forgive me, I also don't know how to load 'brcmsmac' module. I can follow specific terminal commands, though. 

Can you help further? Here's my current lsmod:

```


Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55577  1 vfat
snd_hrtimer            12648  1 
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
acpi_call              12652  0 
kvm_intel              55857  0 
kvm                   336923  1 kvm_intel
parport_pc             32114  0 
ppdev                  12849  0 
vesafb                 13489  1 
joydev                 17393  0 
snd_hda_codec_hdmi     31426  4 
nvidia              10390874  33 
binfmt_misc            17292  1 
eeepc_wmi              12722  0 
asus_wmi               19333  1 eeepc_wmi
sparse_keymap          13658  1 asus_wmi
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
snd_hda_codec_realtek   254163  1 
nouveau               667322  0 
psmouse                63474  0 
serio_raw              12990  0 
snd_hda_intel          28358  3 
snd_hda_codec          91859  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_pcm                80435  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi_event     14475  1 snd_seq_midi
ttm                    65224  1 nouveau
drm_kms_helper         32889  1 nouveau
drm                   196290  3 nouveau,ttm,drm_kms_helper
snd_seq                51567  3 snd_seq_midi,snd_seq_midi_event
i2c_algo_bit           13199  1 nouveau
mxm_wmi                12859  1 nouveau
snd_timer              28932  3 snd_hrtimer,snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  17 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_rawmidi,snd_pcm,snd_seq,snd_timer,snd_seq_device
wmi                    18744  2 asus_wmi,mxm_wmi
video                  18908  1 nouveau
soundcore              12600  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usb_storage            44173  1 
uas                    17699  0 
ahci                   21634  2 
libahci                25761  1 ahci
atl1c                  36638  0 

```

---

### Post by mtron on 2012-03-23
to load a module use
```
sudo modprobe <modulename>

```
to remove a module use
```
sudo modprobe -r <modulename>

```
check 'dmesg' output for debug messages. 

to check for loaded wlan module:
```
lspci -v -s 02:00.0
```

this will output
> ... 
Kernel driver in use: brcmsmac
Kernel modules: wl, bcma, brcmsmac
...

the first line is the currently active driver, the second like lists all available drivers for this device. 

so if the kernel driver in use is empty, load one of the available drivers manually. (we use brcmsmac)
```
sudo modprobe brcmsmac

```
now look at the dmesg output (last few lines) if the module loaded ok. If there is no error restart network-manager and it should work.

if the 'Kernel driver in use:' line shows another driver (e.g. wl) remove this driver with
```
sudo modprobe -r wl

```
and load the brcmsmac driver
```
sudo modprobe brcmsmac

```

---

### Post by halestorm222 on 2012-03-25
Still talking about Ultimate Edition 3.2:

When I typed "lspci -v -s 02:00.0" the key output was bcma, brcmsmac

Then, when I entered

```

sudo modprobe brcmsmac

```

Wireless came alive!

Stupid newb question: how do I do this on startup?

Thank you!

---

### Post by mtron on 2012-03-26
add 'brcmsmac' to a new line in the /etc/modules file. See [https://help.ubuntu.com/community/Loadable_Modules](https://help.ubuntu.com/community/Loadable_Modules)

Cheers!

---

### Post by ToJa92 on 2012-03-28
Hi,

I've managed to install bumblebee along with the Nvidia drivers in Ubuntu 11.10 on the 1015PN.

However, I can't use optirun and it also seems like it's running the nvidia card all the time causing the fan to run continuously. In Windows 7 the fan only spin up when I play a high-res video, do something CPU-intensive or play a 3D game, as expected.

Optirun gives me this:
> toja92@toja92-eee:~$ optirun glxspheres 
[ERROR]Cannot access secondary GPU - error: [XORG] (EE) NVIDIA(0): The NVIDIA kernel module does not appear to be receiving

[ERROR]Aborting because fallback start is disabled.But the kernel module seems to be loaded:
> toja92@toja92-eee:~$ lsmod | grep nvidia
nvidia              10390874  0 
Any hints?
I've tried setting "Intel only mode" in VGA selector gui, but the fan kept on running.

EDIT: Turning off the card by loading the bbswitch module works, but unfortunately no change in fan speed.
EDIT2: Wow, suddenly the fan went almost quiet. Stopping **bumblebeed **however revved up the fan by a small amount. Not sure why.

---

### Post by eupharis on 2012-03-31
> **ToJa92 said:**
> Hi,

I've managed to install bumblebee along with the Nvidia drivers in Ubuntu 11.10 on the 1015PN.

However, I can't use optirun and it also seems like it's running the nvidia card all the time causing the fan to run continuously"

Hi ToJa2. My fan also sounds like its on all the time. But my power-savings from running in Optimus mode are undeniable, so I'm sure it's really using just the Intel for me.

I run Ubuntu 11.10 and the instructions at [post 196]("http://ubuntuforums.org/showpost.php?p=11273185&postcount=196") when combined with the bumblee install instructions worked absolutely great.

Have you tried those yet?

So many thanks Mtron for all your hard work! I usually use this laptop for games and stuff at home, and mostly just programming when I'm out and about. You've given me at least another two hours away from the outlet! Again, thanks so much. Feels a bit like Christmas! :)

---

### Post by Tersus* on 2012-04-09
> sudo optirun glxspheres
[ERROR]Cannot access secondary GPU - error: [XORG] (EE) NVIDIA(0): Failed to initialize the NVIDIA GPU at PCI:4:0:0.  Please

[ERROR]Aborting because fallback start is disabled.


I get the same message. I use Linux Mint LXDE (Openbox). Before the LoginScreen is coming, the bugmessage "hda-intel: spurious response 0x0:0x0, last cmd=0x000000" appears several times  one below. 

Here the output from "display-settings status": 
> sudo display-settings status
INFO: display-settings starting at 07:59:22 UTC 09042012
INFO: detected Ubuntu Distro
INFO: arch is i386
INFO: acpi_call Kernel module is available
INFO: Active GPU is Optimus Mode - Intel GMA 3150 on PCI 00:02.0 and Nvidia GT218 on 04:00.0


Does the error occur because of the desktopmanager "Openbox"?

Thank for help!

---

### Post by mtron on 2012-04-09
> **Tersus* said:**
> Does the error occur because of the desktopmanager "Openbox"?

No.

Your problem is related to bumblebee and optirun, so you might want to redirect this bugreport to the bumblebee devs.

I still consider bumblebee a very hackish approach (real hot switching will be ready for business in ~ 1 year hopefully) and since it produces a lot of overhead you've got better options to utilize the nvidia gpu on this netbook.

One option is to reboot to nvidia exclusive mode, another one is to start a second xserver on the nvidia gpu next to the main xserver running on the intel gpu. 

This method is hackish as well, but you'll get much less performance loss and vdpau is useable.

---

### Post by Tersus* on 2012-04-19
Ich habe hier noch eine kleine Aktualisierung. 

Unter *Linux Mint LXDE* (Ubuntu basierend) ist [FONT=Courier New]$DESKTOP_SESSION[/FONT] wie folgt gesetzt: 

```
echo $DESKTOP_SESSION
Mint-LXDE
```Zeile 828 in [FONT=Courier New]/usr/bin/vga-selector-gui[/FONT] müßte entsprechen angepaßt werden. ;)


Grüße, Tersus

---

### Post by mtron on 2012-04-19
thanks .

can you please also send me the Mint $DESKTOP_SESSION for
- gnome-shell
- gnome-fallback (or classic)
- cinnamon
- mate
- xfce

If not, i'll add those when somebody complains ;)

---

### Post by Tersus* on 2012-04-21
ALso ich habe hier einige Ausgaben durch das [deutsche Linux Mint Forum]("http://www.linuxmintusers.de/index.php?topic=6985.0") gesammelt: 

Linux Mint 12 (Ubuntu 11.10 basierend) mit Gnome-Shell: 'gnome-shell'
Linux Mint 12 (Ubuntu 11.10 basierend) mit Cinnamon: 'cinnamon'
Linux Mint 12 (Ubuntu 11.10 basierend) mit Gnome-Classic: 'gnome-classic'
Linux Mint 12 (Ubuntu 11.10 basierend) mit Mate: 'mate'
Linux Mint 12 (Ubuntu 11.10 basierend) mit LXDE: 'Mint-LXDE'
Linux Mint 12 (Ubuntu 11.10 basierend) mit KDE: 'default'

Linux Mint Debian Edition mit Xfce: 'default'
Linux Mint Debian Edition mit Gnome-Shell: 'gnome'
Linux Mint Debian Edition mit Cinnamon: 'cinnamon'

Gruß

---

### Post by mtron on 2012-04-21
thanks! i'll add those sessions for mint.

I still have no idea how to fix the $desktop_session on debian.  maybe querying dpkg but if multiple desktops are installed, this is a no-go.

Easiest would be if the MintDE devs set the environment variable properly.  i should file a bugreport about this.

---

### Post by mtron on 2012-05-03
Hello! 

I have pushed a new version (eee1015pn-acpitools 0.7.2) to the [ppa]("https://launchpad.net/~mtron/+archive/eee1015pn"). It should get installed automatically once you run a system upgrade. To trigger such an upgrade now use
```
sudo apt-get update && sudo apt-get dist-upgrade
```

Changelog:
```
  * display-settings: use bbswitch to manipulate the power state of the nvidia gpu
  * display-settings: added setting to disable debug output to terminal
  * display-settings: ds status will output power state of the nvidia gpu in optimus mode
  * debian/rules: added nvidia-glx as alternative to nvidia-current to package dependencies for debian compat
  * debian/control: added bbswitch-dkms to package dependencies
  * vga-selector-gui: added option to start second Xserver on nvidia GPU and output to HDMI in Optimus mode
  * vga-selector-gui: added drag and drop window to play file with smplayer on nvidia xserver
  * vgaselector.desktop: added quicklink shortcuts to set gpu mode (unity only)
  * display-settings: added LinuxMint 13 support
  * display-settings: added support for Mate Desktop Enviroment
```

From now on i use the [bbswitch]("https://github.com/Bumblebee-Project/bbswitch") kernel module (developed by the [bumblebee devs]("https://github.com/Lekensteyn")) to manipulate the power state of the nvidia gpu in Optimus mode. 

I have also updated the "[Tweak ubuntu for the EeePC 1015PN]("http://mtron.co.nr/howtos/eeepc-1015pn")" Guide to Precise 12.04. Suggestions & Comments welcome ;)

**Testing (for advanced users only)**

Following the release early, release often paradigm there is another new option in the 'Advanced' window called 
"Optimus Mode: Start Second Xserver on HDMI"

This is still in Development and manual setup is required to make this work (hence the yellow status icon). It will start a second Xserver on the nvidia GPU and output to HDMI (Of course this will work only in Optimus mode and is an alternative approach to bumblebee)

Requirements:

- You need to install openbox and smplayer, and connect the powered HDMI device to the Netbook before selecting this menu option.
```
sudo apt-get install openbox smplayer
```

- check that your Xserver is set to allow "anybody" in the "/etc/X11/Xwrapper.config" file:
```
sudo less /etc/X11/Xwrapper.config | grep allowed
```

if the terminal output reads "allowed_users=anybody" you're ready to proceed.

If not, open the file in a text editor and change the allowed_users Option to "anybody"
```
sudo gedit /etc/X11/Xwrapper.config
```

now, back in a terminal type:

```
xauth
```
followed by  
```
list
```

And you should get an output like:
> ananke/unix:0 MIT-MAGIC-COOKIE-1 9fde426e5g03b20f4b7e51cb329d3033
localhost.localdomain/unix:0 MIT-MAGIC-COOKIE-1 9fde426e5g03b20f4b7e51cb329d3033

Your long alphanumeric string WILL be different, thats ok. Now we need to add a new line and then exit to save it. So we type in (of course replace Your-alpha-numeric-string) 
```
add :1.0 MIT-MAGIC-COOKIE-1 your-alpha-numeric-string
```

and exit the xauth shell
```
exit
```

- copy the configuration file for the Second XServer [xorg.conf.asus1015pn.optimushdmi]("http://paste.ubuntu.com/964565/") to /etc/X11

- copy the config file [smplayer.ini]("http://paste.ubuntu.com/964561/") to /usr/share/acpitools/smplayer (you might need to create this folder first)


As the name implies, the 'Second Xserver' command starts another xserver and puts the output directly on a connected HDMI device. You main X-Server on the laptop display will run in the background. You can switch between the two XServers with STRG+ALT+F8 or STRG+ALT+F9

This approach has some advantages as compared to bumblebee:
- vdpau is fully working
- performance of the nvidia chip is much better as compared to bumblebee
- less overhead

**NOTE:** This is still new and might be rough around the edges, so please only give it a try if you know how to fix a broken system!

---

### Post by finny388 on 2012-05-03
That is awesome mtron! I've moved to Ubuntu 12.04 so the update is great.

I was just reading through your page and saw this: "my video Player of choice is VLC."

I was using VLC before but couldn't get nvidia drivers to acclerate hd rendering. You recommended SMPlayer to me because it supports vdpau and VLC didn't. (and SMPlayer is pretty awesome) Is that no longer true?

Also, there is no note about what your Firefox Tweak does. I assume it is to buffer session caching to RAM?

Thanks for all your sharing of knowledge.

---

### Post by guitwo on 2012-05-03
Hi everyone !

I recently upgrade my distro from oeniric to precise and can not anymore get unity 3D.
It seems that GLX is not loading with the intel driver but I don't know why.

Has anyone a idea how I could fix this ?

thanks for helping !

All the stuff you made for us is amazing btw.

---

### Post by mtron on 2012-05-04
> **finny388 said:**
> 
I was just reading through your page and saw this: "my video Player of choice is VLC."

You are totally right. Smplayer works much better with vdpau. I will correct this in the howto.


> Also, there is no note about what your Firefox Tweak does. I assume it is to buffer session caching to RAM?

The firefox tweak changes the cache directory to the temp ramdrive (you need to do all the steps in the 'Move your logs and temporary files to RAM' section.

If you activate this it will reduce disk writes, saves energy and response times from cache will be much faster. I suggest to give chromium / google chrome a try. with the memory model & cache tweak it preforms outstanding on this little netbook.

@ guitwo: what version of the eee1015pn-acpitools package is installed on your system?

Try to reinstall the following packages:
```
sudo apt-get install --reinstall xserver-xorg-core
sudo apt-get install --reinstall nvidia-current
sudo apt-get install --reinstall eee1015pn-acpitools
```

Now post the output of the following commands
```
find /usr/lib -name libglx.so
sudo display-settings status
sudo display-settings fix
```

And attach the /var/log/Xorg.0.log file

---

### Post by guitwo on 2012-05-04
Thanks for the answer !
I reinstalled the packages then reboot. Still 2D instead of 3D. My eee101pn acpi-tools version was 0.7.2.1~precise2

Here is what you asked for :

```
--@--:~$ find /usr/lib -name libglx.so
/usr/lib/nvidia-current/xorg/libglx.so
/usr/lib/nvidia-current-updates/xorg/libglx.so
/usr/lib/xorg/modules/extensions/libglx.so
--@--:~$ sudo display-settings status
INFO: display-settings starting at 10:54:15 UTC 04052012
INFO: We are running on a EeePC-1015PN
INFO: detected Ubuntu based Distro
INFO: arch is i386
INFO: acpi_call Kernel module is available
INFO: active GPU is Intel GMA3150 on PCI 00:02.0
--@--:~$ sudo display-settings fix
INFO: display-settings starting at 10:54:35 UTC 04052012
INFO: We are running on a EeePC-1015PN
INFO: detected Ubuntu based Distro
INFO: arch is i386
INFO: acpi_call Kernel module is available
INFO: Configuring System for intel
INFO: triggering mesa ldconfig...
INFO: prepare mesa glx lib...
INFO: preparing xorg configuration...
INFO: System configuration for Intel completed

```And the Xorg log is attached.

---

### Post by mtron on 2012-05-04
Something went wrong with your upgrade

[    28.904] (EE) module ABI major version (5) doesn't match the server's version (6)
[    28.904] (EE) Failed to load module "glx" (module requirement mismatch, 0)

The glx module does not fit the xorg sxerver version. the package xserver-xorg-core reinstalled the current glx libs but they still don't fit. 

This is a bug introduced by the system update, but i don't know how to fix this.

You can try this:
```
wget http://archive.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.11.4-0ubuntu10_i386.deb
sudo dpkg -i xserver-xorg-core_1.11.4-0ubuntu10_i386.deb
sudo cp /usr/lib/xorg/modules/extensions/libglx.so /usr/lib/xorg/modules/extensions/libglx.so.intel
sudo cp /usr/lib/nvidia-current/xorg/libglx.so.295.40 /usr/lib/xorg/modules/extensions/libglx.so.nvidia
sudo rm /usr/lib/xorg/modules/extensions/libglx.so
sudo ln -sf /usr/lib/xorg/modules/extensions/libglx.so.intel /usr/lib/xorg/modules/extensions/libglx.so
```

Now logout and back in. IF glx still does not work, repost the Xorg.0.log

---

### Post by guitwo on 2012-05-04
It worked ! Unity 3D is back again !

Now my 1015PN really rocks !

Thanks for everything.

---

### Post by mtron on 2012-05-07
hello! 

i uploaded a new version (eee1015pn-acpitools 0.7.3) to the [ppa]("https://launchpad.net/~mtron/+archive/eee1015pn"). It should get installed automatically once you run a system upgrade. To trigger such an upgrade now use 
```
sudo apt-get update && sudo apt-get dist-upgrade
```

It's a bugfix for the broken glx libs after a dist-upgrade. If you upgraded from oneiric to precise and get a broken desktop (no 3d because libglx ABI version doesn't match the server's version) run:

```
sudo display-settings regenerate-glx
```

This will update the glx libraries and remove the mismatch error. You need to re-login to make Xorg reload the libglx.so files. 

Thanks guitwo for reporting this bug!

---

### Post by barthus on 2012-05-17
Hi Mtron.

I just installed Ubuntu 12.04 64Bit onto my 1015PN, and also your scripts. All runs perfectly well out-of-the-box. Thanks a lot for your work.

 :guitar:

---

### Post by guitwo on 2012-05-22
Hi again !

Here's a little thing about wifi power tweaks.
On my distro it's not called "wlan0" but "eth1".

When trying with "wlan0" I got the message "no such device". Looking with ifconfig it seems I have eth0 and eth1. The operation was not supported for eth0 but worked with eth1. So I guess eth1 is my broadcasting device.

Here's another thing :
When waking up for hibernation, sometimes I get messages about :

Uhhuh. Intel reveived for unknown reason 3d on CPU 0  #(or someting like that)
do you have strange power saving mode enable?
Dazed and confused but trying to continue


PS: I changed my 32bits distro of precise to the 64bits version. It seems to be quite faster.

---

### Post by mtron on 2012-05-23
> **barthus said:**
>  All runs perfectly well out-of-the-box. 

nice, i like ;)

@guitwo the wlan name depends on the driver you use (open source 'brcmsmac' or closed source 'wl'). one calls the wlan device eth1 (eth0 is always the wired port) the other driver calls it wlan1.
> 
Uhhuh. Intel reveived for unknown reason 3d on CPU 0 #(or someting like that)
do you have strange power saving mode enable?
Dazed and confused but trying to continue

this is caused by the Super hybrid engine (SHE). If you hibernate when running in "power save" mode, you will get this message because the power saving feature undervolts the mainboard and processor so it confuses the kernel a bit but should not yield any other negative effects.

---

### Post by guitwo on 2012-05-23
Great, I supposed it was somehow related to Jupiter SHE but wanted to be sure.

---

### Post by mtron on 2012-06-11
Hello!

I have pushed a new version (eee1015pn-acpitools 0.7.4) to the [ppa]("https://launchpad.net/~mtron/+archive/eee1015pn"). It should get installed automatically once you run a system upgrade. To trigger such an upgrade now use

```
sudo apt-get update && sudo apt-get dist-upgrade
```

Changelog:> 
  * vga-selector-gui: added support for Cinnamon Desktop Environment 
  * vga-selector-gui: some fixes for second xserver in optimus mode
  * fixvga.conf: added trigger for mint display manager
  * dropped dependency on lm-sensors. temperature readings are taken from /sys/class/hwmon/hwmon1/device node

_Note for Cinnamon users:_

Cinnamon is the default Desktop Environment on Linux Mint 13 (a ubuntu spin based on precise) that comes with Mint Display Manager (mdm). This display manager is still buggy and does not emit a notification event to the system i use to trigger the auto display configuration.

So replace mdm with lightdm. Instructions are [here]("http://www.webupd8.org/2012/06/how-to-use-lightdm-instead-of-mdm-in.html") 

_Note to everybody doing a fresh install:_

If you do a fresh install of ubuntu don't forget to run a full system upgrade.

**You will get a new kernel** (currently 3.2.0-24-generic) **and it is very important to reboot with this new kernel** (as the system instructs you) before you install the acpitools package or the install of the acpi call dkms kernel module will fail.

I can't fix this because there is a bug in ubuntu's dkms package that installs a new module only on the currently running kernel. So if there is a later kernel version installed - but not in use - you won't get the module for this newer kernel.

Thanks to Frank Materna for the dkms bugreport and the help to add cinnamon support!

---

### Post by gumbomumbo on 2012-06-11
Hi guys, when running:

sudo apt-get install eee1015pn-acpitools build-essential debhelper module-assistant lm-sensors

I always get:  eee1015pn-acpitools not found

Does anybody know why and what I can do about it?

---

### Post by mtron on 2012-06-11
Hello! 

Did you add the ppa repository like this?

```
sudo add-apt-repository ppa:mtron/eee1015pn
sudo apt-get update && sudo apt-get upgrade
sudo apt-get install eee1015pn-acpitools
```

what distro are you using ?

---

### Post by gumbomumbo on 2012-06-11
Thats exactly what I did. I'm using bodhi linux, which is based on the minimal version of ubuntu. Any other ubuntu-program I've tried to install so far, worked without flaws. Can you think of a workaround for this? Thanks for your help, appreciate it.

---

### Post by Ron Ronsen on 2012-06-11
Heyhey, after a long time i am back with Ubuntu 12.04 64bit.

The Fn-F7 (Display off / Backlight off) and Fn-F9 (Taskmanager) keys are without a function. Is it normal? Jupiter + Eee support is installed (like your instructions).

I remember that they worked in Ubuntu 11.10.

---

### Post by mtron on 2012-06-12
> **gumbomumbo said:**
> Thats exactly what I did.

Strange. Can you post the output of
```
cat /etc/apt/sources.list.d/*eee*.list
```

> 
The Fn-F7 (Display off / Backlight off) and Fn-F9 (Taskmanager) keys are without a function. 

FN-F9 can be mapped via keyboard shortcuts to gnome-system-monitor. Same for FN-F7 but you might need to write yourself a proper xrandr script.

---

### Post by Ron Ronsen on 2012-06-12
Okidoki, i've made a keyboard shortcut to gnome-system-monitor and it works.

But the xrandr script for display off is too much for me :)


Thx mtron.

P.S. Nice touchpad bug...Pressing Fn-F3 twice works for me.

---

### Post by gumbomumbo on 2012-06-12
I've had to reinstall my system because I ****** up my bootloader and tried everything again, now I'm getting:

W: failed to fetch [http://ppa.launchpad.net/mtron/eee1015pn/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/mtron/eee1015pn/ubuntu/dists/lucid/main/binary-i386/Packages.gz) 404 Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

Trying to install eee1015pn-acpitools still gives me:

E: Couldn't find package eee1015pn-acpitools

Running cat gives me:

deb [http://ppa.launchpad.net/mtron/eee1015pn/ubuntu](http://ppa.launchpad.net/mtron/eee1015pn/ubuntu) lucid main

Thanks for your help mate

---

### Post by mtron on 2012-06-12
lucid is not supported. 

Only oneiric and precise based distributions are.

---

### Post by gumbomumbo on 2012-06-12
Ah... looks like the problem was found. Bodhi will be updated to 12.04 withing the next few weeks, I guess I'll try again then ;)

Anyway, thanks for your great work mtron, I really hate  Nvidia optimus, because it nevers works, not on Windows and not on Linux either, I even wish my 1015pn didn't even have a Nvidia-graphics card, but only the intel Gma... So thank god there are people like you, fixing this kind of stuff, thanks a lot man ;)

---

### Post by areUKEidding on 2012-06-15
Hey there, anybody here using an external monitor with the 1015PN an also experiencing problems?

I updated everything yesterday and now after the next boot ubuntu does not recognize my external monitor anymore. Already at GRUB only the laptop display is working, so xrandr also only shows me the laptop display.

I am asking here as I feel it might be something specific to the 1015PN and also the tools from the PPA to get optimus working were updated yesterday with everything else, so I wondered if there is a connection.


edit:
Just checked the vga selector tool (should have done that earlier, I know) and it was set to NVIDIA mode even though I always have set it to optimus and never change the mode. So I though I just switch everything back to how I used to have it (auto power down for NVIDIA card was also on even though I had it off before) but after what felt like a gazillion reboots I can now say that somehow the vga selector only lets me stay in NVIDIA mode.
Neither Intel nor optimus mode work anymore, no matter what I have selected as default boot option. Somehow I feel like the last time I booted into NVIDIA mode my external display also did not work, but since I only did that once I am not quite sure. So maybe that is where my problem is... why can't I switch into optimus or even Intel mode anymore? Anybody else having these problems?


edit2:
Allright, solved it. First I activated the acpi_call.log file option, then checked after reboot for errors, got this one:

ERROR: Could not load /lib/modules/3.2.0-25-generic-pae/updates/dkms/acpi_call.ko Please rebuild the kernel module

And thats what I did, reinstalled acpi-call-dkms and then everything worked fine again. I thought the dkms part is there so I actually do not have to rebuild it with updating the kernel (not sure if that was the problem though)? Anyways, everything works as it used to, problem solved.

---

### Post by areUKEidding on 2012-06-16
Ok, after I did everything I mentioned in the post above I am left with  a more ridiculous problem. Both displays work fine in GRUB, while booting and at the login.
But as soon as I am logged in and see the desktop, my external one is switched off and I only have the laptop display. I can switch the external monitor on in the display settings, but it switches off everytime I log in. How can I set permanently that both displays are on when I enter the desktop environment? It works at all times before.

---

### Post by mtron on 2012-06-16
In what mode are you running? (intel exclusive, nvidia exclusive or optimus?

the external vga connector is wired to the intel gma 3150 and nvidia gt 218 but the hdmi port is wired to the nvidia gpu only. if you want to change the config for nvidia exclusive mode use the nvidia-settings program to configure the screens (i use seperate x screens, but if you want use twinview to drag & drop the windows from one monitor to the other)

Then, click on save x configuration file, select 'merge with existing xorg.conf' and put the new nvidia configuration to
**/etc/X11/xorg.conf.asus1015pn.nvidia**

the script copies the fitting xorg.conf (either /etc/X11/xorg.conf.asus1015pn.nvidia or /etc/X11/xorg.conf.asus1015pn.intel) automatically to /etc/X11/xorg.conf during boot. Which one it chooses depens on the available gpu's). that's why your custom edit to xorg.conf is lost.

---

### Post by areUKEidding on 2012-06-17
I am running in optimus mode, did not try pure intel yet but will do that on one of the next reboots. My external monitor is hooked up through the VGA port.  So nvidia-settings does not work for me.

---

### Post by mtron on 2012-06-19
If you want to change the default config for intel mode set the parameters in /etc/X11/xorg.conf.asus1015pn.intel or use randr to setup the dual monitors. see [here]("https://wiki.ubuntu.com/X/Config/Resolution")

---

### Post by PietroZ on 2012-06-20
> **mtron said:**
> Hello! 

I have pushed a new version (eee1015pn-acpitools 0.7.2) to the [ppa]("https://launchpad.net/~mtron/+archive/eee1015pn"). It should get installed automatically once you run a system upgrade. To trigger such an upgrade now use
```
sudo apt-get update && sudo apt-get dist-upgrade
```

Changelog:
```
  * display-settings: use bbswitch to manipulate the power state of the nvidia gpu
  * display-settings: added setting to disable debug output to terminal
  * display-settings: ds status will output power state of the nvidia gpu in optimus mode
  * debian/rules: added nvidia-glx as alternative to nvidia-current to package dependencies for debian compat
  * debian/control: added bbswitch-dkms to package dependencies
  * vga-selector-gui: added option to start second Xserver on nvidia GPU and output to HDMI in Optimus mode
  * vga-selector-gui: added drag and drop window to play file with smplayer on nvidia xserver
  * vgaselector.desktop: added quicklink shortcuts to set gpu mode (unity only)
  * display-settings: added LinuxMint 13 support
  * display-settings: added support for Mate Desktop Enviroment
```

From now on i use the [bbswitch]("https://github.com/Bumblebee-Project/bbswitch") kernel module (developed by the [bumblebee devs]("https://github.com/Lekensteyn")) to manipulate the power state of the nvidia gpu in Optimus mode. 

I have also updated the "[Tweak ubuntu for the EeePC 1015PN]("http://mtron.co.nr/howtos/eeepc-1015pn")" Guide to Precise 12.04. Suggestions & Comments welcome ;)

**Testing (for advanced users only)**

Following the release early, release often paradigm there is another new option in the 'Advanced' window called 
"Optimus Mode: Start Second Xserver on HDMI"

This is still in Development and manual setup is required to make this work (hence the yellow status icon). It will start a second Xserver on the nvidia GPU and output to HDMI (Of course this will work only in Optimus mode and is an alternative approach to bumblebee)

Requirements:

- You need to install openbox and smplayer, and connect the powered HDMI device to the Netbook before selecting this menu option.
```
sudo apt-get install openbox smplayer
```

- check that your Xserver is set to allow "anybody" in the "/etc/X11/Xwrapper.config" file:
```
sudo less /etc/X11/Xwrapper.config | grep allowed
```

if the terminal output reads "allowed_users=anybody" you're ready to proceed.

If not, open the file in a text editor and change the allowed_users Option to "anybody"
```
sudo gedit /etc/X11/Xwrapper.config
```

now, back in a terminal type:

```
xauth
```
followed by  
```
list
```

And you should get an output like:


Your long alphanumeric string WILL be different, thats ok. Now we need to add a new line and then exit to save it. So we type in (of course replace Your-alpha-numeric-string) 
```
add :1.0 MIT-MAGIC-COOKIE-1 your-alpha-numeric-string
```

and exit the xauth shell
```
exit
```

- copy the configuration file for the Second XServer [xorg.conf.asus1015pn.optimushdmi]("http://paste.ubuntu.com/964565/") to /etc/X11

- copy the config file [smplayer.ini]("http://paste.ubuntu.com/964561/") to /usr/share/acpitools/smplayer (you might need to create this folder first)


As the name implies, the 'Second Xserver' command starts another xserver and puts the output directly on a connected HDMI device. You main X-Server on the laptop display will run in the background. You can switch between the two XServers with STRG+ALT+F8 or STRG+ALT+F9

This approach has some advantages as compared to bumblebee:
- vdpau is fully working
- performance of the nvidia chip is much better as compared to bumblebee
- less overhead

**NOTE:** This is still new and might be rough around the edges, so please only give it a try if you know how to fix a broken system!

Is it possible to view nvidia xserver directly on netbook display?

Sorry for my english.

EDIT:

In Optimus Mode does not work disable the nvidia graphics

Works only with:
echo '\_SB.PCI0.P0P4.DGPU.DOFF' > /proc/acpi/call

The energy absorbed by the netbook:
Before 18 Watt
After 11 Watt

---

### Post by mtron on 2012-06-20
> In Optimus Mode does not work disable the nvidia graphics


it works for me. 

Optimus Mode with NVidia GPU powered off draws 883 mA
Optimus Mode with Nvidia GPU powered on takes 1519 mA


So there might be a problem on your system. post the output of 'dmesg | grep bbswitch' and your syslog


> Is it possible to view nvidia xserver directly on netbook display?


yes, that should also work. Edit /etc/X11/xorg.conf.asus1015pn.optimushdmi and change the screen to lvds (the laptop panel) see /var/log/Xorg.0.log)

Then the new Xserver will start on the laptop. Use STRG+ALT+F7 and STRG+ALT+F8 to switch between the two x-screens.

---

### Post by PietroZ on 2012-06-23
> **mtron said:**
> it works for me. 

Optimus Mode with NVidia GPU powered off draws 883 mA
Optimus Mode with Nvidia GPU powered on takes 1519 mA


So there might be a problem on your system. post the output of 'dmesg | grep bbswitch' and your syslog




yes, that should also work. Edit /etc/X11/xorg.conf.asus1015pn.optimushdmi and change the screen to lvds (the laptop panel) see /var/log/Xorg.0.log)

Then the new Xserver will start on the laptop. Use STRG+ALT+F7 and STRG+ALT+F8 to switch between the two x-screens.

```
~$ dmesg | grep bbswitch
~$ 
```

```
~$ sudo modprobe bbswitch
FATAL: Module bbswitch not found.
~$
```

Disable is working only with:
```
echo '\_SB.PCI0.P0P4.DGPU.DOFF' > /proc/acpi/call
```

Enable with:
```
echo '\_SB.PCI0.P0P4.DGPU.DON' > /proc/acpi/call
```

My /etc/X11/xorg.conf.asus1015pn.optimushdmi:
```
# start second xserver on nvidia gpu for hdmi out

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Files"
  ModulePath "/usr/lib/nvidia-current"
  ModulePath "/usr/lib/xorg/modules"
EndSection

Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "HDMI-TV"
    HorizSync       15.0 - 81.0
    VertRefresh     49.0 - 76.0
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "ION"
    Option         "NoLogo" "True"
    Option 	   "UseEDID" "True"
    Option 	   "ConnectedMonitor" "LVDS"
    BusID          "PCI:4:0:0"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "metamodes" "LVDS: nvidia-auto-select"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

The nvidia xsession not working. When I toggle Ctrl + Alt + F8, I see a black screen.

```
~$ cat /var/log/Xorg.0.log
[    50.539] (II) No input driver specified, ignoring this device.
[    50.539] (II) This device may have been added with another device file.
[    50.540] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=7 (/dev/input/event14)
[    50.540] (II) No input driver specified, ignoring this device.
[    50.540] (II) This device may have been added with another device file.
[    50.541] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=3 (/dev/input/event15)
[    50.541] (II) No input driver specified, ignoring this device.
[    50.541] (II) This device may have been added with another device file.
[    50.542] (II) config/udev: Adding input device A4Tech USB Mouse (/dev/input/event7)
[    50.542] (**) A4Tech USB Mouse: Applying InputClass "evdev pointer catchall"
[    50.542] (II) Using input driver 'evdev' for 'A4Tech USB Mouse'
[    50.542] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    50.542] (**) A4Tech USB Mouse: always reports core events
[    50.542] (**) evdev: A4Tech USB Mouse: Device: "/dev/input/event7"
[    50.585] (--) evdev: A4Tech USB Mouse: Vendor 0x9da Product 0xa
[    50.586] (--) evdev: A4Tech USB Mouse: Found 12 mouse buttons
[    50.586] (--) evdev: A4Tech USB Mouse: Found scroll wheel(s)
[    50.586] (--) evdev: A4Tech USB Mouse: Found relative axes
[    50.586] (--) evdev: A4Tech USB Mouse: Found x and y relative axes
[    50.586] (II) evdev: A4Tech USB Mouse: Configuring as mouse
[    50.586] (II) evdev: A4Tech USB Mouse: Adding scrollwheel support
[    50.586] (**) evdev: A4Tech USB Mouse: YAxisMapping: buttons 4 and 5
[    50.586] (**) evdev: A4Tech USB Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    50.586] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/input/input7/event7"
[    50.586] (II) XINPUT: Adding extended input device "A4Tech USB Mouse" (type: MOUSE, id 11)
[    50.587] (II) evdev: A4Tech USB Mouse: initialized for relative axes.
[    50.587] (**) A4Tech USB Mouse: (accel) keeping acceleration scheme 1
[    50.587] (**) A4Tech USB Mouse: (accel) acceleration profile 0
[    50.587] (**) A4Tech USB Mouse: (accel) acceleration factor: 2.000
[    50.587] (**) A4Tech USB Mouse: (accel) acceleration threshold: 4
[    50.588] (II) config/udev: Adding input device A4Tech USB Mouse (/dev/input/mouse0)
[    50.589] (II) No input driver specified, ignoring this device.
[    50.589] (II) This device may have been added with another device file.
[    50.590] (II) config/udev: Adding input device USB2.0 UVC VGA WebCam (/dev/input/event9)
[    50.590] (**) USB2.0 UVC VGA WebCam: Applying InputClass "evdev keyboard catchall"
[    50.590] (II) Using input driver 'evdev' for 'USB2.0 UVC VGA WebCam'
[    50.590] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    50.590] (**) USB2.0 UVC VGA WebCam: always reports core events
[    50.590] (**) evdev: USB2.0 UVC VGA WebCam: Device: "/dev/input/event9"
[    50.590] (--) evdev: USB2.0 UVC VGA WebCam: Vendor 0x13d3 Product 0x5702
[    50.590] (--) evdev: USB2.0 UVC VGA WebCam: Found keys
[    50.590] (II) evdev: USB2.0 UVC VGA WebCam: Configuring as keyboard
[    50.590] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-6/1-6:1.0/input/input9/event9"
[    50.590] (II) XINPUT: Adding extended input device "USB2.0 UVC VGA WebCam" (type: KEYBOARD, id 12)
[    50.590] (**) Option "xkb_rules" "evdev"
[    50.590] (**) Option "xkb_model" "pc105"
[    50.590] (**) Option "xkb_layout" "pl"
[    50.592] (II) config/udev: Adding input device Asus EeePC extra buttons (/dev/input/event8)
[    50.592] (**) Asus EeePC extra buttons: Applying InputClass "evdev keyboard catchall"
[    50.592] (II) Using input driver 'evdev' for 'Asus EeePC extra buttons'
[    50.592] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    50.593] (**) Asus EeePC extra buttons: always reports core events
[    50.593] (**) evdev: Asus EeePC extra buttons: Device: "/dev/input/event8"
[    50.593] (--) evdev: Asus EeePC extra buttons: Vendor 0 Product 0
[    50.593] (--) evdev: Asus EeePC extra buttons: Found keys
[    50.593] (II) evdev: Asus EeePC extra buttons: Configuring as keyboard
[    50.593] (**) Option "config_info" "udev:/sys/devices/platform/eeepc/input/input8/event8"
[    50.593] (II) XINPUT: Adding extended input device "Asus EeePC extra buttons" (type: KEYBOARD, id 13)
[    50.593] (**) Option "xkb_rules" "evdev"
[    50.593] (**) Option "xkb_model" "pc105"
[    50.593] (**) Option "xkb_layout" "pl"
[    50.595] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event0)
[    50.595] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    50.595] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    50.595] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    50.595] (**) AT Translated Set 2 keyboard: always reports core events
[    50.595] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event0"
[    50.595] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    50.595] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    50.595] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    50.595] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input0/event0"
[    50.596] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 14)
[    50.596] (**) Option "xkb_rules" "evdev"
[    50.596] (**) Option "xkb_model" "pc105"
[    50.596] (**) Option "xkb_layout" "pl"
[    50.598] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/event16)
[    50.598] (**) ETPS/2 Elantech Touchpad: Applying InputClass "evdev touchpad catchall"
[    50.598] (**) ETPS/2 Elantech Touchpad: Applying InputClass "touchpad catchall"
[    50.598] (II) LoadModule: "synaptics"
[    50.598] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    50.628] (II) Module synaptics: vendor="X.Org Foundation"
[    50.628] 	compiled for 1.11.3, module version = 1.6.0
[    50.628] 	Module class: X.Org XInput Driver
[    50.628] 	ABI class: X.Org XInput driver, version 16.0
[    50.628] (II) Using input driver 'synaptics' for 'ETPS/2 Elantech Touchpad'
[    50.628] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    50.628] (**) ETPS/2 Elantech Touchpad: always reports core events
[    50.628] (**) Option "Device" "/dev/input/event16"
[    50.639] (II) synaptics: ETPS/2 Elantech Touchpad: ignoring touch events for semi-multitouch device
[    50.639] (--) synaptics: ETPS/2 Elantech Touchpad: x-axis range 0 - 1216
[    50.639] (--) synaptics: ETPS/2 Elantech Touchpad: y-axis range 0 - 512
[    50.639] (--) synaptics: ETPS/2 Elantech Touchpad: pressure range 0 - 255
[    50.639] (--) synaptics: ETPS/2 Elantech Touchpad: finger width range 0 - 15
[    50.639] (--) synaptics: ETPS/2 Elantech Touchpad: buttons: left right double triple
[    50.639] (--) synaptics: ETPS/2 Elantech Touchpad: Vendor 0x2 Product 0xe
[    50.639] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[    50.639] (**) ETPS/2 Elantech Touchpad: always reports core events
[    50.658] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input16/event16"
[    50.658] (II) XINPUT: Adding extended input device "ETPS/2 Elantech Touchpad" (type: TOUCHPAD, id 15)
[    50.658] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) MinSpeed is now constant deceleration 2.5
[    50.658] (**) synaptics: ETPS/2 Elantech Touchpad: MaxSpeed is now 1.75
[    50.658] (**) synaptics: ETPS/2 Elantech Touchpad: AccelFactor is now 0.152
[    50.659] (**) ETPS/2 Elantech Touchpad: (accel) keeping acceleration scheme 1
[    50.659] (**) ETPS/2 Elantech Touchpad: (accel) acceleration profile 1
[    50.659] (**) ETPS/2 Elantech Touchpad: (accel) acceleration factor: 2.000
[    50.659] (**) ETPS/2 Elantech Touchpad: (accel) acceleration threshold: 4
[    50.659] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[    50.660] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/mouse1)
[    50.660] (**) ETPS/2 Elantech Touchpad: Ignoring device from InputClass "touchpad ignore duplicates"
[    55.493] (II) intel(0): EDID vendor "HSD", prod id 1001
[    55.493] (II) intel(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[    55.493] (II) intel(0): Printing DDC gathered Modelines:
[    55.493] (II) intel(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz)
[    55.493] (II) intel(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz)
[    58.138] (II) intel(0): EDID vendor "HSD", prod id 1001
[    58.138] (II) intel(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[    58.138] (II) intel(0): Printing DDC gathered Modelines:
[    58.138] (II) intel(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz)
[    58.138] (II) intel(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz)
[    68.319] (II) intel(0): EDID vendor "HSD", prod id 1001
[    68.319] (II) intel(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[    68.319] (II) intel(0): Printing DDC gathered Modelines:
[    68.319] (II) intel(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz)
[    68.319] (II) intel(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz)
[    69.386] (II) intel(0): EDID vendor "HSD", prod id 1001
[    69.386] (II) intel(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[    69.386] (II) intel(0): Printing DDC gathered Modelines:
[    69.386] (II) intel(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz)
[    69.386] (II) intel(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz)
[    70.942] (II) intel(0): EDID vendor "HSD", prod id 1001
[    70.942] (II) intel(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[    70.942] (II) intel(0): Printing DDC gathered Modelines:
[    70.942] (II) intel(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz)
[    70.942] (II) intel(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz)
[    71.035] (II) intel(0): EDID vendor "HSD", prod id 1001
[    71.035] (II) intel(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[    71.035] (II) intel(0): Printing DDC gathered Modelines:
[    71.035] (II) intel(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz)
[    71.035] (II) intel(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz)
[    71.089] (II) intel(0): EDID vendor "HSD", prod id 1001
[    71.089] (II) intel(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[    71.089] (II) intel(0): Printing DDC gathered Modelines:
[    71.089] (II) intel(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz)
[    71.089] (II) intel(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz)
[    71.155] (II) intel(0): EDID vendor "HSD", prod id 1001
[    71.155] (II) intel(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[    71.155] (II) intel(0): Printing DDC gathered Modelines:
[    71.155] (II) intel(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz)
[    71.155] (II) intel(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz)
[    71.206] (II) intel(0): EDID vendor "HSD", prod id 1001
[    71.206] (II) intel(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[    71.206] (II) intel(0): Printing DDC gathered Modelines:
[    71.206] (II) intel(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz)
[    71.206] (II) intel(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz)
[    71.271] (II) intel(0): EDID vendor "HSD", prod id 1001
[    71.271] (II) intel(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[    71.271] (II) intel(0): Printing DDC gathered Modelines:
[    71.271] (II) intel(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz)
[    71.272] (II) intel(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz)
[    71.319] (II) intel(0): EDID vendor "HSD", prod id 1001
[    71.319] (II) intel(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[    71.319] (II) intel(0): Printing DDC gathered Modelines:
[    71.319] (II) intel(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz)
[    71.319] (II) intel(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz)
[    72.589] (II) intel(0): EDID vendor "HSD", prod id 1001
[    72.590] (II) intel(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[    72.590] (II) intel(0): Printing DDC gathered Modelines:
[    72.590] (II) intel(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz)
[    72.590] (II) intel(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz)
[    85.506] (II) intel(0): EDID vendor "HSD", prod id 1001
[    85.506] (II) intel(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[    85.507] (II) intel(0): Printing DDC gathered Modelines:
[    85.507] (II) intel(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz)
[    85.507] (II) intel(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz)
[    90.759] (II) intel(0): EDID vendor "HSD", prod id 1001
[    90.759] (II) intel(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[    90.759] (II) intel(0): Printing DDC gathered Modelines:
[    90.759] (II) intel(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz)
[    90.760] (II) intel(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz)
[    92.579] (II) XKB: reuse xkmfile /var/lib/xkb/server-BB30603403EA5CA80021759C5589420AD206E6BC.xkm
[   205.905] (II) AIGLX: Suspending AIGLX clients for VT switch
[   206.760] (II) Open ACPI successful (/var/run/acpid.socket)
[   206.761] (II) AIGLX: Resuming AIGLX clients after VT switch
[   206.814] (II) intel(0): EDID vendor "HSD", prod id 1001
[   206.814] (II) intel(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[   206.814] (II) intel(0): Printing DDC gathered Modelines:
[   206.814] (II) intel(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz)
[   206.814] (II) intel(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz)
[   206.856] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[   209.167] (II) AIGLX: Suspending AIGLX clients for VT switch
[   210.484] (II) Open ACPI successful (/var/run/acpid.socket)
[   210.484] (II) AIGLX: Resuming AIGLX clients after VT switch
[   210.484] (EE) intel(0): Couldn't create pixmap for fbcon
[   210.538] (II) intel(0): EDID vendor "HSD", prod id 1001
[   210.538] (II) intel(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[   210.538] (II) intel(0): Printing DDC gathered Modelines:
[   210.538] (II) intel(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz)
[   210.538] (II) intel(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz)
[   210.579] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[   211.777] (II) AIGLX: Suspending AIGLX clients for VT switch
[   215.326] (II) Open ACPI successful (/var/run/acpid.socket)
[   215.326] (II) AIGLX: Resuming AIGLX clients after VT switch
[   215.326] (EE) intel(0): Couldn't create pixmap for fbcon
[   215.378] (II) intel(0): EDID vendor "HSD", prod id 1001
[   215.378] (II) intel(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[   215.378] (II) intel(0): Printing DDC gathered Modelines:
[   215.378] (II) intel(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz)
[   215.378] (II) intel(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz)
[   215.420] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[   277.983] (II) AIGLX: Suspending AIGLX clients for VT switch
[   282.571] (II) Open ACPI successful (/var/run/acpid.socket)
[   282.571] (II) AIGLX: Resuming AIGLX clients after VT switch
[   282.572] (EE) intel(0): Couldn't create pixmap for fbcon
[   282.624] (II) intel(0): EDID vendor "HSD", prod id 1001
[   282.624] (II) intel(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[   282.624] (II) intel(0): Printing DDC gathered Modelines:
[   282.624] (II) intel(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz)
[   282.624] (II) intel(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz)
[   282.673] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[   283.929] (II) AIGLX: Suspending AIGLX clients for VT switch
[   284.714] (II) Open ACPI successful (/var/run/acpid.socket)
[   284.715] (II) AIGLX: Resuming AIGLX clients after VT switch
[   284.715] (EE) intel(0): Couldn't create pixmap for fbcon
[   284.766] (II) intel(0): EDID vendor "HSD", prod id 1001
[   284.766] (II) intel(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[   284.766] (II) intel(0): Printing DDC gathered Modelines:
[   284.766] (II) intel(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz)
[   284.766] (II) intel(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz)
[   284.811] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[   396.061] (II) intel(0): EDID vendor "HSD", prod id 1001
[   396.061] (II) intel(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[   396.061] (II) intel(0): Printing DDC gathered Modelines:
[   396.061] (II) intel(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz)
[   396.061] (II) intel(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz)
[   432.014] (II) AIGLX: Suspending AIGLX clients for VT switch
[   435.922] (II) Open ACPI successful (/var/run/acpid.socket)
[   435.922] (II) AIGLX: Resuming AIGLX clients after VT switch
[   435.922] (EE) intel(0): Couldn't create pixmap for fbcon
[   435.974] (II) intel(0): EDID vendor "HSD", prod id 1001
[   435.974] (II) intel(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[   435.974] (II) intel(0): Printing DDC gathered Modelines:
[   435.974] (II) intel(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz)
[   435.974] (II) intel(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz)
[   436.023] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[   506.957] (II) AIGLX: Suspending AIGLX clients for VT switch
[   508.629] (II) Open ACPI successful (/var/run/acpid.socket)
[   508.629] (II) AIGLX: Resuming AIGLX clients after VT switch
[   508.629] (EE) intel(0): Couldn't create pixmap for fbcon
[   508.680] (II) intel(0): EDID vendor "HSD", prod id 1001
[   508.680] (II) intel(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[   508.680] (II) intel(0): Printing DDC gathered Modelines:
[   508.680] (II) intel(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz)
[   508.680] (II) intel(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz)
[   508.733] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[   627.240] (II) AIGLX: Suspending AIGLX clients for VT switch
[   631.592] (II) Open ACPI successful (/var/run/acpid.socket)
[   631.592] (II) AIGLX: Resuming AIGLX clients after VT switch
[   631.592] (EE) intel(0): Couldn't create pixmap for fbcon
[   631.612] (II) intel(0): EDID vendor "HSD", prod id 1001
[   631.612] (II) intel(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[   631.612] (II) intel(0): Printing DDC gathered Modelines:
[   631.612] (II) intel(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz)
[   631.612] (II) intel(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz)
[   631.667] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[   804.691] (II) AIGLX: Suspending AIGLX clients for VT switch
[   806.497] (II) Open ACPI successful (/var/run/acpid.socket)
[   806.498] (II) AIGLX: Resuming AIGLX clients after VT switch
[   806.498] (EE) intel(0): Couldn't create pixmap for fbcon
[   806.550] (II) intel(0): EDID vendor "HSD", prod id 1001
[   806.550] (II) intel(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[   806.550] (II) intel(0): Printing DDC gathered Modelines:
[   806.550] (II) intel(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz)
[   806.550] (II) intel(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz)
[   806.615] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[   808.015] (II) AIGLX: Suspending AIGLX clients for VT switch
[   825.537] (II) Open ACPI successful (/var/run/acpid.socket)
[   825.537] (II) AIGLX: Resuming AIGLX clients after VT switch
[   825.537] (EE) intel(0): Couldn't create pixmap for fbcon
[   825.552] (II) intel(0): EDID vendor "HSD", prod id 1001
[   825.552] (II) intel(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[   825.552] (II) intel(0): Printing DDC gathered Modelines:
[   825.552] (II) intel(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz)
[   825.552] (II) intel(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz)
[   825.610] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[   893.978] (II) AIGLX: Suspending AIGLX clients for VT switch
[   901.842] (II) Open ACPI successful (/var/run/acpid.socket)
[   901.842] (II) AIGLX: Resuming AIGLX clients after VT switch
[   901.843] (EE) intel(0): Couldn't create pixmap for fbcon
[   901.850] (II) intel(0): EDID vendor "HSD", prod id 1001
[   901.850] (II) intel(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[   901.850] (II) intel(0): Printing DDC gathered Modelines:
[   901.850] (II) intel(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz)
[   901.850] (II) intel(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz)
[   901.910] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[   907.698] (II) AIGLX: Suspending AIGLX clients for VT switch
[   908.546] (II) Open ACPI successful (/var/run/acpid.socket)
[   908.546] (II) AIGLX: Resuming AIGLX clients after VT switch
[   908.546] (EE) intel(0): Couldn't create pixmap for fbcon
[   908.598] (II) intel(0): EDID vendor "HSD", prod id 1001
[   908.598] (II) intel(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[   908.598] (II) intel(0): Printing DDC gathered Modelines:
[   908.598] (II) intel(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz)
[   908.598] (II) intel(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz)
[   908.657] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[   932.166] (II) AIGLX: Suspending AIGLX clients for VT switch
[   935.721] (II) Open ACPI successful (/var/run/acpid.socket)
[   935.721] (II) AIGLX: Resuming AIGLX clients after VT switch
[   935.721] (EE) intel(0): Couldn't create pixmap for fbcon
[   935.732] (II) intel(0): EDID vendor "HSD", prod id 1001
[   935.732] (II) intel(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[   935.732] (II) intel(0): Printing DDC gathered Modelines:
[   935.732] (II) intel(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz)
[   935.732] (II) intel(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz)
[   935.796] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[  1177.466] (II) AIGLX: Suspending AIGLX clients for VT switch
[  1180.364] (II) Open ACPI successful (/var/run/acpid.socket)
[  1180.364] (II) AIGLX: Resuming AIGLX clients after VT switch
[  1180.364] (EE) intel(0): Couldn't create pixmap for fbcon
[  1180.416] (II) intel(0): EDID vendor "HSD", prod id 1001
[  1180.416] (II) intel(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[  1180.416] (II) intel(0): Printing DDC gathered Modelines:
[  1180.416] (II) intel(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz)
[  1180.416] (II) intel(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz)
[  1180.483] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[  1221.878] (II) AIGLX: Suspending AIGLX clients for VT switch
[  1223.141] (II) Open ACPI successful (/var/run/acpid.socket)
[  1223.141] (II) AIGLX: Resuming AIGLX clients after VT switch
[  1223.141] (EE) intel(0): Couldn't create pixmap for fbcon
[  1223.192] (II) intel(0): EDID vendor "HSD", prod id 1001
[  1223.192] (II) intel(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[  1223.192] (II) intel(0): Printing DDC gathered Modelines:
[  1223.192] (II) intel(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz)
[  1223.192] (II) intel(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz)
[  1223.260] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[  1257.862] (II) AIGLX: Suspending AIGLX clients for VT switch
[  1259.910] (II) Open ACPI successful (/var/run/acpid.socket)
[  1259.910] (II) AIGLX: Resuming AIGLX clients after VT switch
[  1259.910] (EE) intel(0): Couldn't create pixmap for fbcon
[  1259.962] (II) intel(0): EDID vendor "HSD", prod id 1001
[  1259.962] (II) intel(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[  1259.962] (II) intel(0): Printing DDC gathered Modelines:
[  1259.962] (II) intel(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz)
[  1259.962] (II) intel(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz)
[  1260.025] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[  1260.891] (II) AIGLX: Suspending AIGLX clients for VT switch
[  1261.676] (II) Open ACPI successful (/var/run/acpid.socket)
[  1261.676] (II) AIGLX: Resuming AIGLX clients after VT switch
[  1261.676] (EE) intel(0): Couldn't create pixmap for fbcon
[  1261.730] (II) intel(0): EDID vendor "HSD", prod id 1001
[  1261.730] (II) intel(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[  1261.730] (II) intel(0): Printing DDC gathered Modelines:
[  1261.730] (II) intel(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz)
[  1261.730] (II) intel(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz)
[  1261.806] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[  1341.015] (II) AIGLX: Suspending AIGLX clients for VT switch
[  1343.997] (II) Open ACPI successful (/var/run/acpid.socket)
[  1343.997] (II) AIGLX: Resuming AIGLX clients after VT switch
[  1343.997] (EE) intel(0): Couldn't create pixmap for fbcon
[  1344.048] (II) intel(0): EDID vendor "HSD", prod id 1001
[  1344.048] (II) intel(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[  1344.048] (II) intel(0): Printing DDC gathered Modelines:
[  1344.048] (II) intel(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz)
[  1344.048] (II) intel(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz)
[  1344.106] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[  1345.799] (II) AIGLX: Suspending AIGLX clients for VT switch
[  1346.578] (II) Open ACPI successful (/var/run/acpid.socket)
[  1346.579] (II) AIGLX: Resuming AIGLX clients after VT switch
[  1346.579] (EE) intel(0): Couldn't create pixmap for fbcon
[  1346.630] (II) intel(0): EDID vendor "HSD", prod id 1001
[  1346.630] (II) intel(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[  1346.630] (II) intel(0): Printing DDC gathered Modelines:
[  1346.630] (II) intel(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz)
[  1346.630] (II) intel(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz)
[  1346.693] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
```

EDIT:

Ok, bbswitch is working:
```
~$ dmesg | grep bbswitch
bbswitch: version 0.4.2
bbswitch: Found integrated VGA device 0000:00:02.0: \_SB_.PCI0.VGA_
bbswitch: Found discrete VGA device 0000:04:00.0: \_SB_.PCI0.P0P4.DGPU
bbswitch: detected an Optimus _DSM function
bbswitch: Succesfully loaded. Discrete card 0000:04:00.0 is on
bbswitch: device 0000:04:00.0 is in use by driver 'nvidia', refusing OFF
~$
```

But nvidia on boot is still running! The battery is discharged faster, and fan still running loud. Only command:
```
echo '\_SB.PCI0.P0P4.DGPU.DOFF' > /proc/acpi/call
```
Turns off the discrete graphics

Nvidia xserver not working :/

---

### Post by mtron on 2012-06-25
> sudo modprobe bbswitch
FATAL: Module bbswitch not found.

is it build and installed for your current kernel?

see 'dkms status' from the terminal. The old nvidia disable method via acpi_Call is sub-optimal because it can lead to a total system lockup. bbswitch is much better for this.

> Ok, bbswitch is working... But nvidia on boot is still running!

i guess you already checked if the corresponding option is turned on in the Advanced window? if so, turn on logging to file, set to reboot in optimus mode, do the reboot and then attach the logfile it created as well as your 'dmesg' output.

i will have a look why the xorg.conf for the optimus overlay xserver does not do what it should.

---

### Post by PietroZ on 2012-06-25
acpi-call.log
```
INFO: display-settings starting at 14:30:56 UTC 25062012
INFO: We are running on a EeePC-1015PN
INFO: detected Ubuntu based Distro
INFO: arch is i386
INFO: acpi_call Kernel module is available
INFO: bbswitch Kernel module is available
ON
INFO: NVidia GPU enabled
INFO: nvidia kernel module already loaded
INFO: display-settings starting at 14:31:14 UTC 25062012
INFO: We are running on a EeePC-1015PN
INFO: detected Ubuntu based Distro
INFO: arch is i386
INFO: acpi_call Kernel module is available
INFO: bbswitch Kernel module is available
INFO: No nvidia kernel module found
INFO: NVidia GPU is already powered off
INFO: display-settings starting at 14:31:22 UTC 25062012
INFO: We are running on a EeePC-1015PN
INFO: detected Ubuntu based Distro
INFO: arch is i386
INFO: acpi_call Kernel module is available
INFO: bbswitch Kernel module is available
INFO: No User selection found. Using optimus as default GPU
INFO: VGA Mode for next boot is set to Optimus Mode (intel/nvidia)
INFO: Auto Pre-reboot configuration for Optimus Mode completed!
INFO: display-settings starting at 14:39:44 UTC 25062012
INFO: We are running on a EeePC-1015PN
INFO: detected Ubuntu based Distro
INFO: arch is i386
INFO: acpi_call Kernel module is available
INFO: loaded bbswitch Kernel module
INFO: Configuring System for intel
INFO: triggering mesa ldconfig...
INFO: prepare mesa glx lib...
INFO: preparing xorg configuration...
INFO: System configuration for Intel completed
INFO: No nvidia kernel module found
OFF
INFO: NVidia GPU disabled
INFO: We're done
INFO: display-settings starting at 14:41:58 UTC 25062012
INFO: We are running on a EeePC-1015PN
INFO: detected Ubuntu based Distro
INFO: arch is i386
INFO: acpi_call Kernel module is available
INFO: bbswitch Kernel module is available
INFO: NVidia GPU is already powered on
INFO: nvidia kernel module already loaded
INFO: display-settings starting at 14:42:16 UTC 25062012
INFO: We are running on a EeePC-1015PN
INFO: detected Ubuntu based Distro
INFO: arch is i386
INFO: acpi_call Kernel module is available
INFO: bbswitch Kernel module is available
INFO: No nvidia kernel module found
OFF
INFO: NVidia GPU disabled
```

dmesg:
```
Initializing cgroup subsys cpu
Linux version 3.3.7-ext73-f1-19.1-atom-ags-cfs (root@ext73-stacjonarka) (gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) ) #2 SMP Wed May 30 20:31:13 CEST 2012
KERNEL supported cpus:
  Intel GenuineIntel
  AMD AuthenticAMD
BIOS-provided physical RAM map:
 BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
 BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
 BIOS-e820: 00000000000e2000 - 0000000000100000 (reserved)
 BIOS-e820: 0000000000100000 - 000000007f670000 (usable)
 BIOS-e820: 000000007f670000 - 000000007f67e000 (ACPI data)
 BIOS-e820: 000000007f67e000 - 000000007f6c0000 (ACPI NVS)
 BIOS-e820: 000000007f6c0000 - 0000000080000000 (reserved)
 BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
 BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
Notice: NX (Execute Disable) protection cannot be enabled: non-PAE kernel!
DMI present.
DMI: ASUSTeK Computer INC. 1015PN/1015PN, BIOS 0701    04/18/2011
e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
last_pfn = 0x7f670 max_arch_pfn = 0x100000
MTRR default type: uncachable
MTRR fixed ranges enabled:
  00000-9FFFF write-back
  A0000-BFFFF uncachable
  C0000-CFFFF write-protect
  D0000-DFFFF uncachable
  E0000-EFFFF write-through
  F0000-FFFFF write-protect
MTRR variable ranges enabled:
  0 base 000000000 mask 080000000 write-back
  1 base 07F700000 mask 0FFF00000 uncachable
  2 base 07F800000 mask 0FF800000 uncachable
  3 disabled
  4 disabled
  5 disabled
  6 disabled
  7 disabled
x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
original variable MTRRs
reg 0, base: 0GB, range: 2GB, type WB
reg 1, base: 2039MB, range: 1MB, type UC
reg 2, base: 2040MB, range: 8MB, type UC
total RAM covered: 2039M
Found optimal setting for mtrr clean up
 gran_size: 64K 	chunk_size: 16M 	num_reg: 3  	lose cover RAM: 0G
New variable MTRRs
reg 0, base: 0GB, range: 2GB, type WB
reg 1, base: 2039MB, range: 1MB, type UC
reg 2, base: 2040MB, range: 8MB, type UC
found SMP MP-table at [b00ff780] ff780
initial memory mapped : 0 - 01c00000
Base memory trampoline at [b009b000] 9b000 size 16384
init_memory_mapping: 0000000000000000-00000000477fe000
 0000000000 - 0000400000 page 4k
 0000400000 - 0047400000 page 2M
 0047400000 - 00477fe000 page 4k
kernel direct mapping tables up to 477fe000 @ 1bfb000-1c00000
RAMDISK: 35ab4000 - 36d52000
ACPI: RSDP 000fbb50 00024 (v02 ACPIAM)
ACPI: XSDT 7f670100 0006C (v01 A_M_I_ OEMXSDT  04001118 MSFT 00000097)
ACPI: FACP 7f670290 000F4 (v04 A_M_I_ OEMFACP  04001118 MSFT 00000097)
ACPI: DSDT 7f6704a0 09204 (v02  A1681 A1681000 00000000 INTL 20051117)
ACPI: FACS 7f67e000 00040
ACPI: APIC 7f670390 0006C (v02 A_M_I_ OEMAPIC  04001118 MSFT 00000097)
ACPI: MCFG 7f670400 0003C (v01 A_M_I_ OEMMCFG  04001118 MSFT 00000097)
ACPI: ECDT 7f670440 00055 (v01 A_M_I_ OEMECDT  04001118 MSFT 00000097)
ACPI: OEMB 7f67e040 00061 (v01 A_M_I_ AMI_OEM  04001118 MSFT 00000097)
ACPI: HPET 7f67b4a0 00038 (v01 A_M_I_ OEMHPET  04001118 MSFT 00000097)
ACPI: GSCI 7f67e0b0 02024 (v01 A_M_I_ GMCHSCI  04001118 MSFT 00000097)
ACPI: RTCF 7f6800e0 002EF (v01  A1234 RTCONFIG 00000001 INTL 20060113)
ACPI: SSDT 7f681610 00999 (v01  PmRef   CpuPm4 00003000 INTL 20051117)
ACPI: Local APIC address 0xfee00000
894MB HIGHMEM available.
1143MB LOWMEM available.
  mapped low ram: 0 - 477fe000
  low ram: 0 - 477fe000
Zone PFN ranges:
  DMA      0x00000010 -> 0x00001000
  Normal   0x00001000 -> 0x000477fe
  HighMem  0x000477fe -> 0x0007f670
Movable zone start PFN for each node
Early memory PFN ranges
    0: 0x00000010 -> 0x0000009f
    0: 0x00000100 -> 0x0007f670
On node 0 totalpages: 521727
free_area_init_node: node 0, pgdat b1542a80, node_mem_map f680d200
  DMA zone: 32 pages used for memmap
  DMA zone: 0 pages reserved
  DMA zone: 3951 pages, LIFO batch:0
  Normal zone: 2256 pages used for memmap
  Normal zone: 286510 pages, LIFO batch:31
  HighMem zone: 1789 pages used for memmap
  HighMem zone: 227189 pages, LIFO batch:31
Using APIC driver default
ACPI: PM-Timer IO Port: 0x808
ACPI: Local APIC address 0xfee00000
ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] enabled)
ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
IOAPIC[0]: apic_id 4, version 32, address 0xfec00000, GSI 0-23
ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
ACPI: IRQ0 used by override.
ACPI: IRQ2 used by override.
ACPI: IRQ9 used by override.
Using ACPI (MADT) for SMP configuration information
ACPI: HPET id: 0xffffffff base: 0xfed00000
SMP: Allowing 4 CPUs, 0 hotplug CPUs
nr_irqs_gsi: 40
PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
PM: Registered nosave memory: 00000000000a0000 - 00000000000e2000
PM: Registered nosave memory: 00000000000e2000 - 0000000000100000
Allocating PCI resources starting at 80000000 (gap: 80000000:7ee00000)
setup_percpu: NR_CPUS:4 nr_cpumask_bits:4 nr_cpu_ids:4 nr_node_ids:1
PERCPU: Embedded 12 pages/cpu @f67d1000 s25152 r0 d24000 u49152
pcpu-alloc: s25152 r0 d24000 u49152 alloc=12*4096
pcpu-alloc: [0] 0 [0] 1 [0] 2 [0] 3 
Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 517650
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.3.7-ext73-f1-19.1-atom-ags-cfs root=UUID=44c10ca6-2422-4b29-9eaa-21ee39420de3 ro plymouth:force-splash quiet splash pcie_aspm=force acpi_osi=Linux acpi_enforce_resources=lax i915.i915_enable_rc6=1 i915.i915_enable_fbc=1 i915.lvds_downclock=1 i915.semaphores=1 vt.handoff=7
PCIe ASPM is forcibly enabled
PID hash table entries: 4096 (order: 2, 16384 bytes)
Dentry cache hash table entries: 262144 (order: 8, 1048576 bytes)
Inode-cache hash table entries: 131072 (order: 7, 524288 bytes)
Initializing CPU#0
Initializing HighMem for node 0 (000477fe:0007f670)
Memory: 2043512k/2087360k available (4243k kernel code, 43396k reserved, 1167k data, 380k init, 915912k highmem)
virtual kernel memory layout:
    fixmap  : 0xfff67000 - 0xfffff000   ( 608 kB)
    pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
    vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
    lowmem  : 0xb0000000 - 0xf77fe000   (1143 MB)
      .init : 0xb1549000 - 0xb15a8000   ( 380 kB)
      .data : 0xb1424cb8 - 0xb1548b80   (1167 kB)
      .text : 0xb1000000 - 0xb1424cb8   (4243 kB)
Checking if this processor honours the WP bit even in supervisor mode...Ok.
SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Hierarchical RCU implementation.
	RCU dyntick-idle grace-period acceleration is enabled.
NR_IRQS:2304 nr_irqs:712 16
CPU 0 irqstacks, hard=f600a000 soft=f600c000
Extended CMOS year: 2000
Console: colour dummy device 80x25
console [tty0] enabled
hpet clockevent registered
Fast TSC calibration using PIT
Detected 1496.237 MHz processor.
Calibrating delay loop (skipped), value calculated using timer frequency.. 2992.47 BogoMIPS (lpj=2992474)
pid_max: default: 32768 minimum: 301
Security Framework initialized
AppArmor: AppArmor initialized
Mount-cache hash table entries: 512
Initializing cgroup subsys blkio
CPU: Physical Processor ID: 0
CPU: Processor Core ID: 0
mce: CPU supports 5 MCE banks
CPU0: Thermal monitoring enabled (TM2)
using mwait in idle threads.
ACPI: Core revision 20120111
Enabling APIC mode:  Flat.  Using 1 I/O APICs
..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
CPU0: Intel(R) Atom(TM) CPU N550   @ 1.50GHz stepping 0a
Performance Events: PEBS fmt0+, Atom events, Intel PMU driver.
... version:                3
... bit width:              40
... generic registers:      2
... value mask:             000000ffffffffff
... max period:             000000007fffffff
... fixed-purpose events:   3
... event mask:             0000000700000003
CPU 1 irqstacks, hard=f6082000 soft=f6084000
Booting Node   0, Processors  #1
smpboot cpu 1: start_ip = 9b000
Initializing CPU#1
TSC synchronization [CPU#0 -> CPU#1]:
Measured 99 cycles TSC warp between CPUs, turning off TSC clock.
Marking TSC unstable due to check_tsc_sync_source failed
CPU 2 irqstacks, hard=f6092000 soft=f6094000
 #2
smpboot cpu 2: start_ip = 9b000
Initializing CPU#2
CPU 3 irqstacks, hard=f609e000 soft=f60a0000
 #3 Ok.
smpboot cpu 3: start_ip = 9b000
Initializing CPU#3
Brought up 4 CPUs
Total of 4 processors activated (11969.89 BogoMIPS).
devtmpfs: initialized
PM: Registering ACPI NVS region at 7f67e000 (270336 bytes)
print_constraints: dummy: 
NET: Registered protocol family 16
ACPI: bus type pci registered
PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xb0000000-0xbfffffff] (base 0xb0000000)
PCI: not using MMCONFIG
PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=5
PCI: Using configuration type 1 for base access
bio: create slab <bio-0> at 0
ACPI: Added _OSI(Module Device)
ACPI: Added _OSI(Processor Device)
ACPI: Added _OSI(3.0 _SCP Extensions)
ACPI: Added _OSI(Processor Aggregator Device)
ACPI: Added _OSI(Linux)
ACPI: EC: EC description table is found, configuring boot EC
[Firmware Bug]: ACPI: BIOS _OSI(Linux) query honored via cmdline
ACPI: Executed 2 blocks of module-level executable AML code
ACPI: SSDT 7f680a30 002FC (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
ACPI: Dynamic OEM Table Load:
ACPI: SSDT   (null) 002FC (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
ACPI: SSDT 7f680ee0 00724 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
ACPI: Dynamic OEM Table Load:
ACPI: SSDT   (null) 00724 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
ACPI: SSDT 7f680810 00217 (v01  PmRef  Cpu1Ist 00003000 INTL 20051117)
ACPI: Dynamic OEM Table Load:
ACPI: SSDT   (null) 00217 (v01  PmRef  Cpu1Ist 00003000 INTL 20051117)
ACPI: SSDT 7f680e50 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20051117)
ACPI: Dynamic OEM Table Load:
ACPI: SSDT   (null) 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20051117)
ACPI: SSDT 7f6805f0 00217 (v01  PmRef  Cpu2Ist 00003000 INTL 20051117)
ACPI: Dynamic OEM Table Load:
ACPI: SSDT   (null) 00217 (v01  PmRef  Cpu2Ist 00003000 INTL 20051117)
ACPI: SSDT 7f680dc0 00085 (v01  PmRef  Cpu2Cst 00003000 INTL 20051117)
ACPI: Dynamic OEM Table Load:
ACPI: SSDT   (null) 00085 (v01  PmRef  Cpu2Cst 00003000 INTL 20051117)
ACPI: SSDT 7f6803d0 00217 (v01  PmRef  Cpu3Ist 00003000 INTL 20051117)
ACPI: Dynamic OEM Table Load:
ACPI: SSDT   (null) 00217 (v01  PmRef  Cpu3Ist 00003000 INTL 20051117)
ACPI: SSDT 7f680d30 00085 (v01  PmRef  Cpu3Cst 00003000 INTL 20051117)
ACPI: Dynamic OEM Table Load:
ACPI: SSDT   (null) 00085 (v01  PmRef  Cpu3Cst 00003000 INTL 20051117)
ACPI: Interpreter enabled
ACPI: (supports S0 S3 S4 S5)
ACPI: Using IOAPIC for interrupt routing
PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xb0000000-0xbfffffff] (base 0xb0000000)
PCI: MMCONFIG at [mem 0xb0000000-0xbfffffff] reserved in ACPI motherboard resources
PCI: Using MMCONFIG for extended config space
ACPI: EC: GPE = 0x1c, I/O: command/status = 0x66, data = 0x62
ACPI: No dock devices found.
PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000dffff]
pci_root PNP0A08:00: host bridge window [mem 0x7f700000-0xfed8ffff]
PCI host bridge to bus 0000:00
pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000dffff]
pci_bus 0000:00: root bus resource [mem 0x7f700000-0xfed8ffff]
pci 0000:00:00.0: [8086:a010] type 0 class 0x000600
pci 0000:00:02.0: [8086:a011] type 0 class 0x000300
pci 0000:00:02.0: reg 10: [mem 0xf5e00000-0xf5e7ffff]
pci 0000:00:02.0: reg 14: [io  0xcc00-0xcc07]
pci 0000:00:02.0: reg 18: [mem 0xc0000000-0xcfffffff pref]
pci 0000:00:02.0: reg 1c: [mem 0xf5d00000-0xf5dfffff]
pci 0000:00:02.1: [8086:a012] type 0 class 0x000380
pci 0000:00:02.1: reg 10: [mem 0xf5e80000-0xf5efffff]
pci 0000:00:1b.0: [8086:27d8] type 0 class 0x000403
pci 0000:00:1b.0: reg 10: [mem 0xf5cf8000-0xf5cfbfff 64bit]
pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
pci 0000:00:1c.0: [8086:27d0] type 1 class 0x000604
pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
pci 0000:00:1c.1: [8086:27d2] type 1 class 0x000604
pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
pci 0000:00:1c.3: [8086:27d6] type 1 class 0x000604
pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
pci 0000:00:1d.0: [8086:27c8] type 0 class 0x000c03
pci 0000:00:1d.0: reg 20: [io  0xc400-0xc41f]
pci 0000:00:1d.1: [8086:27c9] type 0 class 0x000c03
pci 0000:00:1d.1: reg 20: [io  0xc480-0xc49f]
pci 0000:00:1d.2: [8086:27ca] type 0 class 0x000c03
pci 0000:00:1d.2: reg 20: [io  0xc800-0xc81f]
pci 0000:00:1d.3: [8086:27cb] type 0 class 0x000c03
pci 0000:00:1d.3: reg 20: [io  0xc880-0xc89f]
pci 0000:00:1d.7: [8086:27cc] type 0 class 0x000c03
pci 0000:00:1d.7: reg 10: [mem 0xf5cf7c00-0xf5cf7fff]
pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
pci 0000:00:1e.0: [8086:2448] type 1 class 0x000604
pci 0000:00:1f.0: [8086:27bc] type 0 class 0x000601
pci 0000:00:1f.2: [8086:27c0] type 0 class 0x000101
pci 0000:00:1f.2: reg 10: [io  0xc080-0xc087]
pci 0000:00:1f.2: reg 14: [io  0xc000-0xc003]
pci 0000:00:1f.2: reg 18: [io  0xbc00-0xbc07]
pci 0000:00:1f.2: reg 1c: [io  0xb880-0xb883]
pci 0000:00:1f.2: reg 20: [io  0xb800-0xb80f]
pci 0000:00:1f.2: reg 24: [mem 0xf5cf7800-0xf5cf7bff]
pci 0000:00:1f.2: PME# supported from D3hot
pci 0000:04:00.0: [10de:0a6f] type 0 class 0x000300
pci 0000:04:00.0: reg 10: [mem 0xfa000000-0xfaffffff]
pci 0000:04:00.0: reg 14: [mem 0xe0000000-0xefffffff 64bit pref]
pci 0000:04:00.0: reg 1c: [mem 0xf2000000-0xf3ffffff 64bit pref]
pci 0000:04:00.0: reg 24: [io  0xec00-0xec7f]
pci 0000:04:00.0: reg 30: [mem 0xfbf00000-0xfbf7ffff pref]
pci 0000:04:00.1: [10de:0be3] type 0 class 0x000403
pci 0000:04:00.1: reg 10: [mem 0xfbffc000-0xfbffffff]
pci 0000:00:1c.0: PCI bridge to [bus 04-04]
pci 0000:00:1c.0:   bridge window [io  0xe000-0xefff]
pci 0000:00:1c.0:   bridge window [mem 0xfa000000-0xfbffffff]
pci 0000:00:1c.0:   bridge window [mem 0xe0000000-0xf3ffffff 64bit pref]
pci 0000:02:00.0: [14e4:4727] type 0 class 0x000280
pci 0000:02:00.0: reg 10: [mem 0xf9ffc000-0xf9ffffff 64bit]
pci 0000:02:00.0: supports D1 D2
pci 0000:02:00.0: PME# supported from D0 D3hot D3cold
pci 0000:00:1c.1: PCI bridge to [bus 02-03]
pci 0000:00:1c.1:   bridge window [mem 0xf6000000-0xf9ffffff]
pci 0000:00:1c.1:   bridge window [mem 0xdc000000-0xdfffffff 64bit pref]
pci 0000:01:00.0: [1969:1062] type 0 class 0x000200
pci 0000:01:00.0: reg 10: [mem 0xf5fc0000-0xf5ffffff 64bit]
pci 0000:01:00.0: reg 18: [io  0xdc00-0xdc7f]
pci 0000:01:00.0: PME# supported from D0 D1 D2 D3hot D3cold
pci 0000:00:1c.3: PCI bridge to [bus 01-01]
pci 0000:00:1c.3:   bridge window [io  0xd000-0xdfff]
pci 0000:00:1c.3:   bridge window [mem 0xf5f00000-0xf5ffffff]
pci 0000:00:1e.0: PCI bridge to [bus 05-05] (subtractive decode)
pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
pci 0000:00:1e.0:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
pci 0000:00:1e.0:   bridge window [mem 0x7f700000-0xfed8ffff] (subtractive decode)
pci_bus 0000:00: on NUMA node 0
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P5._PRT]
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P7._PRT]
 pci0000:00: Requesting ACPI _OSC control (0x1d)
 pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
ACPI _OSC control for PCIe not granted, disabling ASPM
ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11 12 14 *15)
ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 *7 10 11 12 14 15)
ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 *11 12 14 15)
ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 *5 6 7 10 11 12 14 15)
ACPI: PCI Interrupt Link [LNKG] (IRQs 3 *4 5 6 7 10 11 12 14 15)
ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 6 7 10 11 12 14 15)
vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
vgaarb: device added: PCI:0000:04:00.0,decodes=io+mem,owns=none,locks=none
vgaarb: loaded
vgaarb: bridge control possible 0000:04:00.0
vgaarb: no bridge control possible 0000:00:02.0
SCSI subsystem initialized
libata version 3.00 loaded.
usbcore: registered new interface driver usbfs
usbcore: registered new interface driver hub
usbcore: registered new device driver usb
PCI: Using ACPI for IRQ routing
PCI: pci_cache_line_size set to 64 bytes
Expanded resource reserved due to conflict with PCI Bus 0000:00
reserve RAM buffer: 000000000009fc00 - 000000000009ffff 
reserve RAM buffer: 000000007f670000 - 000000007fffffff 
NetLabel: Initializing
NetLabel:  domain hash size = 128
NetLabel:  protocols = UNLABELED CIPSOv4
NetLabel:  unlabeled traffic allowed by default
HPET: 3 timers in total, 0 timers will be used for per-cpu timer
hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
hpet0: 3 comparators, 64-bit 14.318180 MHz counter
Switching to clocksource hpet
AppArmor: AppArmor Filesystem Enabled
pnp: PnP ACPI init
ACPI: bus type pnp registered
pnp 00:00: [bus 00-ff]
pnp 00:00: [io  0x0cf8-0x0cff]
pnp 00:00: [io  0x0000-0x0cf7 window]
pnp 00:00: [io  0x0d00-0xffff window]
pnp 00:00: [mem 0x000a0000-0x000bffff window]
pnp 00:00: [mem 0x000d0000-0x000dffff window]
pnp 00:00: [mem 0x7f700000-0xfed8ffff window]
pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
pnp 00:01: [mem 0xfed14000-0xfed19fff]
pnp 00:01: [mem 0xfed90000-0xfed93fff]
system 00:01: [mem 0xfed14000-0xfed19fff] has been reserved
system 00:01: [mem 0xfed90000-0xfed93fff] has been reserved
system 00:01: Plug and Play ACPI device, IDs PNP0c01 (active)
pnp 00:02: [dma 4]
pnp 00:02: [io  0x0000-0x000f]
pnp 00:02: [io  0x0081-0x0083]
pnp 00:02: [io  0x0087]
pnp 00:02: [io  0x0089-0x008b]
pnp 00:02: [io  0x008f]
pnp 00:02: [io  0x00c0-0x00df]
pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
pnp 00:03: [io  0x0070-0x0071]
pnp 00:03: [irq 8]
pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
pnp 00:04: [io  0x0060]
pnp 00:04: [io  0x0064]
pnp 00:04: [irq 1]
pnp 00:04: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
pnp 00:05: [irq 12]
pnp 00:05: Plug and Play ACPI device, IDs SYN0a13 SYN0a00 SYN0002 PNP0f13 (active)
pnp 00:06: [io  0x0061]
pnp 00:06: Plug and Play ACPI device, IDs PNP0800 (active)
pnp 00:07: [io  0x00f0-0x00ff]
pnp 00:07: [irq 13]
pnp 00:07: Plug and Play ACPI device, IDs PNP0c04 (active)
pnp 00:08: [io  0x0010-0x001f]
pnp 00:08: [io  0x0022-0x003f]
pnp 00:08: [io  0x0044-0x004d]
pnp 00:08: [io  0x0050-0x005e]
pnp 00:08: [io  0x0063]
pnp 00:08: [io  0x0065]
pnp 00:08: [io  0x0067-0x006f]
pnp 00:08: [io  0x0072-0x007f]
pnp 00:08: [io  0x0080]
pnp 00:08: [io  0x0084-0x0086]
pnp 00:08: [io  0x0088]
pnp 00:08: [io  0x008c-0x008e]
pnp 00:08: [io  0x0090-0x009f]
pnp 00:08: [io  0x00a2-0x00bf]
pnp 00:08: [io  0x00e0-0x00ef]
pnp 00:08: [io  0x025c-0x025f]
pnp 00:08: [io  0x0380-0x0383]
pnp 00:08: [io  0x0400-0x041f]
pnp 00:08: [io  0x04d0-0x04d1]
pnp 00:08: [io  0x0800-0x087f]
pnp 00:08: [io  0x0400-0x03ff disabled]
pnp 00:08: [io  0x0480-0x04bf]
pnp 00:08: [mem 0xfed1c000-0xfed1ffff]
pnp 00:08: [mem 0xfed20000-0xfed3ffff]
pnp 00:08: [mem 0xfed50000-0xfed8ffff]
pnp 00:08: [mem 0xffb00000-0xffbfffff]
pnp 00:08: [mem 0xfff00000-0xffffffff]
system 00:08: [io  0x025c-0x025f] has been reserved
system 00:08: [io  0x0380-0x0383] has been reserved
system 00:08: [io  0x0400-0x041f] has been reserved
system 00:08: [io  0x04d0-0x04d1] has been reserved
system 00:08: [io  0x0800-0x087f] has been reserved
system 00:08: [io  0x0480-0x04bf] has been reserved
system 00:08: [mem 0xfed1c000-0xfed1ffff] has been reserved
system 00:08: [mem 0xfed20000-0xfed3ffff] has been reserved
system 00:08: [mem 0xfed50000-0xfed8ffff] has been reserved
system 00:08: [mem 0xffb00000-0xffbfffff] has been reserved
system 00:08: [mem 0xfff00000-0xffffffff] has been reserved
system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
pnp 00:09: [mem 0xfed00000-0xfed003ff]
pnp 00:09: Plug and Play ACPI device, IDs PNP0103 (active)
pnp 00:0a: [mem 0xfec00000-0xfec00fff]
pnp 00:0a: [mem 0xfee00000-0xfee00fff]
system 00:0a: [mem 0xfec00000-0xfec00fff] could not be reserved
system 00:0a: [mem 0xfee00000-0xfee00fff] has been reserved
system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
pnp 00:0b: [mem 0xb0000000-0xbfffffff]
system 00:0b: [mem 0xb0000000-0xbfffffff] has been reserved
system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
pnp 00:0c: [mem 0x00000000-0x0009ffff]
pnp 00:0c: [mem 0x000c0000-0x000cffff]
pnp 00:0c: [mem 0x000e0000-0x000fffff]
pnp 00:0c: [mem 0x00100000-0x7f6fffff]
pnp 00:0c: [mem 0xfed90000-0xffffffff]
system 00:0c: [mem 0x00000000-0x0009ffff] could not be reserved
system 00:0c: [mem 0x000c0000-0x000cffff] could not be reserved
system 00:0c: [mem 0x000e0000-0x000fffff] could not be reserved
system 00:0c: [mem 0x00100000-0x7f6fffff] could not be reserved
system 00:0c: [mem 0xfed90000-0xffffffff] could not be reserved
system 00:0c: Plug and Play ACPI device, IDs PNP0c01 (active)
pnp: PnP ACPI: found 13 devices
ACPI: ACPI bus type pnp unregistered
PCI: max bus depth: 1 pci_try_num: 2
pci 0000:00:1c.3: BAR 15: assigned [mem 0x80000000-0x801fffff 64bit pref]
pci 0000:00:1c.1: BAR 13: assigned [io  0x1000-0x1fff]
pci 0000:00:1c.0: PCI bridge to [bus 04-04]
pci 0000:00:1c.0:   bridge window [io  0xe000-0xefff]
pci 0000:00:1c.0:   bridge window [mem 0xfa000000-0xfbffffff]
pci 0000:00:1c.0:   bridge window [mem 0xe0000000-0xf3ffffff 64bit pref]
pci 0000:00:1c.1: PCI bridge to [bus 02-03]
pci 0000:00:1c.1:   bridge window [io  0x1000-0x1fff]
pci 0000:00:1c.1:   bridge window [mem 0xf6000000-0xf9ffffff]
pci 0000:00:1c.1:   bridge window [mem 0xdc000000-0xdfffffff 64bit pref]
pci 0000:00:1c.3: PCI bridge to [bus 01-01]
pci 0000:00:1c.3:   bridge window [io  0xd000-0xdfff]
pci 0000:00:1c.3:   bridge window [mem 0xf5f00000-0xf5ffffff]
pci 0000:00:1c.3:   bridge window [mem 0x80000000-0x801fffff 64bit pref]
pci 0000:00:1e.0: PCI bridge to [bus 05-05]
pci 0000:00:1c.1: enabling device (0106 -> 0107)
pci 0000:00:1e.0: setting latency timer to 64
pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
pci_bus 0000:00: resource 8 [mem 0x7f700000-0xfed8ffff]
pci_bus 0000:04: resource 0 [io  0xe000-0xefff]
pci_bus 0000:04: resource 1 [mem 0xfa000000-0xfbffffff]
pci_bus 0000:04: resource 2 [mem 0xe0000000-0xf3ffffff 64bit pref]
pci_bus 0000:02: resource 0 [io  0x1000-0x1fff]
pci_bus 0000:02: resource 1 [mem 0xf6000000-0xf9ffffff]
pci_bus 0000:02: resource 2 [mem 0xdc000000-0xdfffffff 64bit pref]
pci_bus 0000:01: resource 0 [io  0xd000-0xdfff]
pci_bus 0000:01: resource 1 [mem 0xf5f00000-0xf5ffffff]
pci_bus 0000:01: resource 2 [mem 0x80000000-0x801fffff 64bit pref]
pci_bus 0000:05: resource 4 [io  0x0000-0x0cf7]
pci_bus 0000:05: resource 5 [io  0x0d00-0xffff]
pci_bus 0000:05: resource 6 [mem 0x000a0000-0x000bffff]
pci_bus 0000:05: resource 7 [mem 0x000d0000-0x000dffff]
pci_bus 0000:05: resource 8 [mem 0x7f700000-0xfed8ffff]
NET: Registered protocol family 2
IP route cache hash table entries: 65536 (order: 6, 262144 bytes)
TCP established hash table entries: 262144 (order: 9, 2097152 bytes)
TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
TCP: Hash tables configured (established 262144 bind 65536)
TCP reno registered
UDP hash table entries: 1024 (order: 3, 32768 bytes)
UDP-Lite hash table entries: 1024 (order: 3, 32768 bytes)
NET: Registered protocol family 1
pci 0000:00:02.0: Boot video device
PCI: CLS 32 bytes, default 64
Unpacking initramfs...
Freeing initrd memory: 19064k freed
audit: initializing netlink socket (disabled)
type=2000 audit(1340642360.161:1): initialized
highmem bounce pool size: 64 pages
HugeTLB registered 4 MB page size, pre-allocated 0 pages
VFS: Disk quotas dquot_6.5.2
Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
fuse init (API version 7.18)
msgmni has been set to 2239
Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
io scheduler noop registered
io scheduler deadline registered
io scheduler cfq registered (default)
pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
pcieport 0000:00:1c.1: irq 41 for MSI/MSI-X
pcieport 0000:00:1c.3: irq 42 for MSI/MSI-X
vesafb: mode is 800x600x32, linelength=3200, pages=0
vesafb: scrolling: redraw
vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
vesafb: framebuffer at 0xc0000000, mapped to 0xf8080000, using 1920k, total 1920k
fb0: VESA VGA frame buffer device
intel_idle: MWAIT substates: 0x20220
intel_idle: v0.4 model 0x1C
intel_idle: lapic_timer_reliable_states 0x2
ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
ACPI: AC Adapter [AC0] (off-line)
Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
Linux agpgart interface v0.103
loop: module loaded
Fixed MDIO Bus: probed
ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
ehci_hcd 0000:00:1d.7: setting latency timer to 64
ehci_hcd 0000:00:1d.7: EHCI Host Controller
ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
ehci_hcd 0000:00:1d.7: using broken periodic workaround
ehci_hcd 0000:00:1d.7: debug port 1
ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf5cf7c00
ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 8 ports detected
ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
uhci_hcd: USB Universal Host Controller Interface driver
uhci_hcd 0000:00:1d.0: setting latency timer to 64
uhci_hcd 0000:00:1d.0: UHCI Host Controller
uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000c400
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 2 ports detected
uhci_hcd 0000:00:1d.1: setting latency timer to 64
uhci_hcd 0000:00:1d.1: UHCI Host Controller
uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000c480
hub 3-0:1.0: USB hub found
hub 3-0:1.0: 2 ports detected
uhci_hcd 0000:00:1d.2: setting latency timer to 64
uhci_hcd 0000:00:1d.2: UHCI Host Controller
uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000c800
hub 4-0:1.0: USB hub found
hub 4-0:1.0: 2 ports detected
uhci_hcd 0000:00:1d.3: setting latency timer to 64
uhci_hcd 0000:00:1d.3: UHCI Host Controller
uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000c880
hub 5-0:1.0: USB hub found
hub 5-0:1.0: 2 ports detected
i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
serio: i8042 KBD port at 0x60,0x64 irq 1
serio: i8042 AUX port at 0x60,0x64 irq 12
rtc_cmos 00:03: RTC can wake from S4
rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
cpuidle: using governor ladder
cpuidle: using governor menu
Registering the dns_resolver key type
Using IPI No-Shortcut mode
registered taskstats version 1
rtc_cmos 00:03: setting system clock to 2012-06-25 16:39:20 UTC (1340642360)
input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input0
usb 1-5: new high-speed USB device number 3 using ehci_hcd
ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
ACPI: Battery Slot [BAT0] (battery present)
Freeing unused kernel memory: 380k freed
Write protecting the kernel text: 4244k
Write protecting the kernel read-only data: 988k
usb 1-6: new high-speed USB device number 4 using ehci_hcd
udevd[65]: starting version 175
input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
ACPI: Lid Switch [LID]
input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
ACPI: Sleep Button [SLPB]
input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input3
ACPI: Power Button [PWRB]
input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input4
ACPI: Power Button [PWRF]
agpgart-intel 0000:00:00.0: Intel GMA3150 Chipset
agpgart-intel 0000:00:00.0: detected gtt size: 524288K total, 262144K mappable
agpgart-intel 0000:00:00.0: detected 8192K stolen memory
agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
thermal LNXTHERM:00: registered as thermal_zone0
ACPI: Thermal Zone [TZ00] (44 C)
ata_piix 0000:00:1f.2: version 2.13
ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
Console: switching to colour frame buffer device 100x37
atl1c 0000:01:00.0: version 1.0.1.0-NAPI
[drm] Initialized drm 1.1.0 20060810
ata_piix 0000:00:1f.2: setting latency timer to 64
scsi0 : ata_piix
scsi1 : ata_piix
ata1: SATA max UDMA/133 cmd 0xc080 ctl 0xc000 bmdma 0xb800 irq 21
ata2: SATA max UDMA/133 cmd 0xbc00 ctl 0xb880 bmdma 0xb808 irq 21
i915 0000:00:02.0: setting latency timer to 64
i915 0000:00:02.0: irq 43 for MSI/MSI-X
[drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[drm] Driver supports precise vblank timestamp query.
[drm:intel_dsm_platform_mux_info] *ERROR* MUX INFO call failed
[drm:intel_dsm_platform_mux_info] *ERROR* MUX INFO call failed
vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=none:owns=io+mem
vgaarb: transferring owner from PCI:0000:00:02.0 to PCI:0000:04:00.0
composite sync not supported
ata1.00: ATA-8: WDC WD2500BEVT-80A23T0, 01.01A01, max UDMA/133
ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
ata1.00: configured for UDMA/133
scsi 0:0:0:0: Direct-Access     ATA      WDC WD2500BEVT-8 01.0 PQ: 0 ANSI: 5
[drm] initialized overlay support
composite sync not supported
checking generic (c0000000 1e0000) vs hw (c0000000 10000000)
fb: conflicting fb hw usage inteldrmfb vs VESA VGA - removing generic driver
Console: switching to colour dummy device 80x25
fbcon: inteldrmfb (fb0) is primary device
usbcore: registered new interface driver uas
Initializing USB Mass Storage driver...
scsi2 : usb-storage 1-5:1.0
usbcore: registered new interface driver usb-storage
USB Mass Storage support registered.
Console: switching to colour frame buffer device 128x37
fb0: inteldrmfb frame buffer device
drm: registered panic notifier
acpi device:14: registered as cooling_device4
input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:11/LNXVIDEO:00/input/input5
ACPI: Video Device [DGPU] (multi-head: yes  rom: yes  post: no)
usb 2-2: new low-speed USB device number 2 using uhci_hcd
acpi device:1a: registered as cooling_device5
input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input6
ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
composite sync not supported
sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
sd 0:0:0:0: [sda] Write Protect is off
sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
 sda: sda1 sda2 sda3 < sda5 sda6 > sda4
sd 0:0:0:0: [sda] Attached SCSI disk
usbcore: registered new interface driver usbhid
usbhid: USB HID core driver
input: A4Tech USB Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/input/input7
a4tech 0003:09DA:0006.0001: input,hidraw0: USB HID v1.10 Mouse [A4Tech USB Optical Mouse] on usb-0000:00:1d.0-2/input0
usb 5-2: new full-speed USB device number 2 using uhci_hcd
EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: (null)
scsi 2:0:0:0: Direct-Access     Multiple Card  Reader     1.00 PQ: 0 ANSI: 0
sd 2:0:0:0: [sdb] Attached SCSI removable disk
Adding 1998844k swap on /dev/sda5.  Priority:-1 extents:1 across:1998844k 
udevd[351]: starting version 175
wmi: Mapper loaded
pci_hotplug: PCI Hot Plug PCI Core version: 0.5
coretemp coretemp.0: Using relative temperature scale!
coretemp coretemp.0: Using relative temperature scale!
eeepc_laptop: Eee PC Hotkey Driver
eeepc_laptop: Hotkey init flags 0x41
eeepc_laptop: TYPE (2000000) not reported by BIOS, enabling anyway
eeepc_laptop: PANELPOWER (4000000) not reported by BIOS, enabling anyway
eeepc_laptop: TPD (8000000) not reported by BIOS, enabling anyway
eeepc_laptop: Get control methods supported: 0xe001613
eeepc_laptop: Error reading CAMG
eeepc_laptop: Backlight controlled by ACPI video driver
input: Asus EeePC extra buttons as /devices/platform/eeepc/input/input8
Registered led device: eeepc::touchpad
asus_wmi: ASUS WMI generic driver loaded
bcma: Core 0 found: ChipCommon (manuf 0x4BF, id 0x800, rev 0x24, class 0x0)
bcma: Core 1 found: IEEE 802.11 (manuf 0x4BF, id 0x812, rev 0x18, class 0x0)
bcma: Core 2 found: PCIe (manuf 0x4BF, id 0x820, rev 0x11, class 0x0)
bcma: Bus registered
lib80211: common routines for IEEE802.11 drivers
lib80211_crypt: registered algorithm 'NULL'
eeepc_wmi: Found legacy ATKD device (ASUS010)
eeepc_wmi: WMI device present, but legacy ATKD device is also present and enabled
eeepc_wmi: You probably booted with acpi_osi="Linux" or acpi_osi="!Windows 2009"
eeepc_wmi: Can't load eeepc-wmi, use default acpi_osi (preferred) or eeepc-laptop
eeepc-wmi: probe of eeepc-wmi failed with error -16
psmouse serio1: elantech: assuming hardware version 2 (with firmware version 0x140100)
psmouse serio1: elantech: Synaptics capabilities query result 0x68, 0x15, 0x0a.
psmouse serio1: elantech: retrying ps2 command 0xe6 (2).
Bluetooth: Core ver 2.16
NET: Registered protocol family 31
Bluetooth: HCI device and connection manager initialized
Bluetooth: HCI socket layer initialized
Bluetooth: L2CAP socket layer initialized
Bluetooth: SCO socket layer initialized
nvidia: module license 'NVIDIA' taints kernel.
Disabling lock debugging due to kernel taint
nvidia 0000:04:00.0: power state changed by ACPI to D0
nvidia 0000:04:00.0: power state changed by ACPI to D0
nvidia 0000:04:00.0: enabling device (0000 -> 0003)
vgaarb: device changed decodes: PCI:0000:04:00.0,olddecodes=io+mem,decodes=none:owns=none
NVRM: loading NVIDIA UNIX x86 Kernel Module  295.59  Wed Jun  6 21:24:41 PDT 2012
psmouse serio1: elantech: retrying ps2 command 0xf8 (2).
mousedev: PS/2 mouse device common for all mice
Linux media interface: v0.10
Linux video capture interface: v2.00
uvcvideo: Found UVC 1.00 device USB2.0 UVC VGA WebCam (13d3:5702)
input: USB2.0 UVC VGA WebCam as /devices/pci0000:00/0000:00:1d.7/usb1/1-6/1-6:1.0/input/input9
usbcore: registered new interface driver uvcvideo
USB Video Class driver (1.1.1)
usbcore: registered new interface driver btusb
eeepc_laptop: Unable to find port
cfg80211: Calling CRDA to update world regulatory domain
snd_hda_intel 0000:00:1b.0: irq 44 for MSI/MSI-X
input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
hda_intel: Disabling MSI
brcmsmac bcma0:0: mfg 4bf core 812 rev 24 class 0 irq 17
psmouse serio1: elantech: retrying ps2 command 0xf8 (1).
ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
brcms_module_init: register returned 0
cfg80211: World regulatory domain updated:
cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
cfg80211: Calling CRDA for country: US
HDMI status: Codec=0 Pin=5 Presence_Detect=0 ELD_Valid=0
cfg80211: Regulatory domain changed to country: US
cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
cfg80211:   (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
cfg80211:   (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
HDMI status: Codec=1 Pin=5 Presence_Detect=0 ELD_Valid=0
HDMI status: Codec=2 Pin=5 Presence_Detect=0 ELD_Valid=0
HDMI status: Codec=3 Pin=5 Presence_Detect=0 ELD_Valid=0
input: HDA NVidia HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:1c.0/0000:04:00.1/sound/card1/input12
input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:1c.0/0000:04:00.1/sound/card1/input13
input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:1c.0/0000:04:00.1/sound/card1/input14
input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1c.0/0000:04:00.1/sound/card1/input15
type=1400 audit(1340635171.237:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=819 comm="apparmor_parser"
type=1400 audit(1340635171.237:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=650 comm="apparmor_parser"
type=1400 audit(1340635171.239:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=819 comm="apparmor_parser"
type=1400 audit(1340635171.239:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=650 comm="apparmor_parser"
type=1400 audit(1340635171.241:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=650 comm="apparmor_parser"
type=1400 audit(1340635171.241:7): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=666 comm="apparmor_parser"
type=1400 audit(1340635171.241:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=819 comm="apparmor_parser"
type=1400 audit(1340635171.243:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=666 comm="apparmor_parser"
type=1400 audit(1340635171.243:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=666 comm="apparmor_parser"
input: ETPS/2 Elantech Touchpad as /devices/platform/i8042/serio1/input/input16
Bluetooth: hci0 command tx timeout
device-mapper: uevent: version 1.0.3
device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro
EXT4-fs (sda6): warning: maximal mount count reached, running e2fsck is recommended
EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
init: ureadahead-other main process (956) terminated with status 127
init: failsafe main process (983) killed by TERM signal
NET: Registered protocol family 10
type=1400 audit(1340635177.261:11): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1052 comm="apparmor_parser"
type=1400 audit(1340635177.265:12): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1052 comm="apparmor_parser"
type=1400 audit(1340635177.267:13): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1052 comm="apparmor_parser"
type=1400 audit(1340635177.313:14): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=1051 comm="apparmor_parser"
type=1400 audit(1340635177.377:15): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=1058 comm="apparmor_parser"
type=1400 audit(1340635177.449:16): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1056 comm="apparmor_parser"
type=1400 audit(1340635177.451:17): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=1056 comm="apparmor_parser"
type=1400 audit(1340635177.485:18): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=1055 comm="apparmor_parser"
type=1400 audit(1340635177.485:19): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=1055 comm="apparmor_parser"
type=1400 audit(1340635177.649:20): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=1074 comm="apparmor_parser"
Bluetooth: RFCOMM TTY layer initialized
Bluetooth: RFCOMM socket layer initialized
Bluetooth: RFCOMM ver 1.11
Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Bluetooth: BNEP filters: protocol multicast
ieee80211 phy0: brcms_ops_bss_info_changed: qos enabled: false (implement)
ieee80211 phy0: brcms_ops_config: change power-save mode: false (implement)
ADDRCONF(NETDEV_UP): wlan0: link is not ready
atl1c 0000:01:00.0: irq 45 for MSI/MSI-X
ADDRCONF(NETDEV_UP): eth0: link is not ready
NET: Registered protocol family 17
zram: module is from the staging directory, the quality is unknown, you have been warned.
zram: Creating 4 devices ...
Adding 515736k swap on /dev/zram0.  Priority:100 extents:1 across:515736k SS
Adding 515736k swap on /dev/zram1.  Priority:100 extents:1 across:515736k SS
Adding 515736k swap on /dev/zram2.  Priority:100 extents:1 across:515736k SS
Adding 515736k swap on /dev/zram3.  Priority:100 extents:1 across:515736k SS
/dev/vmmon[1232]: Module vmmon: registered with major=10 minor=165
/dev/vmmon[1232]: Module vmmon: initialized
[1246]: VMCI: shared components initialized.
[1246]: VMCI: host components initialized.
[1246]: VMCI: Module registered (name=vmci,major=10,minor=58).
[1246]: VMCI: Using host personality
[1246]: VMCI: Module (name=vmci) is initialized
wlan0: authenticate with 00:17:31:f4:d5:ac (try 1)
wlan0: authenticated
wlan0: associate with 00:17:31:f4:d5:ac (try 1)
wlan0: RX AssocResp from 00:17:31:f4:d5:ac (capab=0x411 status=0 aid=1)
wlan0: associated
wlan0: moving STA 00:17:31:f4:d5:ac to state 1
wlan0: moving STA 00:17:31:f4:d5:ac to state 2
ieee80211 phy0: brcms_ops_bss_info_changed: qos enabled: false (implement)
ieee80211 phy0: brcmsmac: brcms_ops_bss_info_changed: associated
ieee80211 phy0: changing basic rates failed: -22
ieee80211 phy0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 0 (implement)
ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
wlan0: moving STA 00:17:31:f4:d5:ac to state 3
ieee80211 phy0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 1 (implement)
acpi_call: Module loaded successfully
bbswitch: version 0.4.2
bbswitch: Found integrated VGA device 0000:00:02.0: \_SB_.PCI0.VGA_
bbswitch: Found discrete VGA device 0000:04:00.0: \_SB_.PCI0.P0P4.DGPU
bbswitch: detected an Optimus _DSM function
bbswitch: Succesfully loaded. Discrete card 0000:04:00.0 is on
netlink: 12 bytes leftover after parsing attributes.
netlink: 12 bytes leftover after parsing attributes.
netlink: 12 bytes leftover after parsing attributes.
/dev/vmnet: open called by PID 1354 (vmnet-bridge)
/dev/vmnet: hub 0 does not exist, allocating memory.
/dev/vmnet: port on hub 0 successfully opened
bridge-wlan0: device is wireless, enabling SMAC
bridge-wlan0: up
bridge-wlan0: attached
acpi_call: Calling \AMW0.DSTS
acpi_call: Call successful: 0x30003
/dev/vmnet: open called by PID 1366 (vmnet-netifup)
/dev/vmnet: hub 1 does not exist, allocating memory.
/dev/vmnet: port on hub 1 successfully opened
/dev/vmnet: open called by PID 1385 (vmnet-dhcpd)
/dev/vmnet: port on hub 1 successfully opened
bbswitch: device 0000:04:00.0 is in use by driver 'nvidia', refusing OFF
/dev/vmnet: open called by PID 1419 (vmnet-natd)
/dev/vmnet: hub 8 does not exist, allocating memory.
/dev/vmnet: port on hub 8 successfully opened
netlink: 12 bytes leftover after parsing attributes.
netlink: 12 bytes leftover after parsing attributes.
netlink: 12 bytes leftover after parsing attributes.
netlink: 12 bytes leftover after parsing attributes.
userif-3: sent link down event.
userif-3: sent link up event.
/dev/vmnet: open called by PID 1425 (vmnet-netifup)
/dev/vmnet: port on hub 8 successfully opened
/dev/vmnet: open called by PID 1432 (vmnet-dhcpd)
/dev/vmnet: port on hub 8 successfully opened
userif-3: sent link down event.
userif-3: sent link up event.
composite sync not supported
composite sync not supported
vboxdrv: Found 4 processor cores.
vboxdrv: fAsync=0 offMin=0x61e offMax=0x37a7
vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
vboxdrv: Successfully loaded version 4.1.18 (interface 0x00190000).
vboxpci: IOMMU not found (not registered)
wlan0: no IPv6 routers present
WARNING! power/level is deprecated; use power/control instead
composite sync not supported
vmnet1: no IPv6 routers present
vmnet8: no IPv6 routers present
composite sync not supported
ip_tables: (C) 2000-2006 Netfilter Core Team
init: plymouth-stop pre-start process (2231) terminated with status 1
composite sync not supported
composite sync not supported
composite sync not supported
composite sync not supported
composite sync not supported
composite sync not supported
composite sync not supported
composite sync not supported
composite sync not supported
composite sync not supported
composite sync not supported
composite sync not supported
bbswitch: device 0000:04:00.0 is in use by driver 'nvidia', refusing OFF
```

eee1015pn-debug.txt
```
Distributor ID:	Ubuntu
Description:	Ubuntu 12.04 LTS
Release:	12.04
Codename:	precise

Installed Program Versions:
eee1015pn-acpitools version 0.7.4
nvidia binary driver 295.59

Used Desktop Enviroment:
ubuntu

installed glx files:
/usr/lib/nvidia-current/xorg/libglx.so
/usr/lib/nvidia-current/xorg/libglx.so.295.59
/usr/lib/xorg/modules/extensions/libglx.so
/usr/lib/xorg/modules/extensions/libglx.so.intel
/usr/lib/xorg/modules/extensions/libglx.so.nvidia

installed dkms modules:
acpi-call, 0.0.1, 3.3.5-ext73-f1-19.0-atom-ags-cfs, i686: installed
acpi-call, 0.0.1, 3.3.7-ext73-f1-19.1-atom-ags-cfs, i686: installed
bbswitch, 0.4.2, 3.3.7-ext73-f1-19.1-atom-ags-cfs, i686: installed
nvidia-current, 295.59, 3.3.7-ext73-f1-19.1-atom-ags-cfs, i686: installed
vboxhost, 4.1.18, 3.3.7-ext73-f1-19.1-atom-ags-cfs, i686: installed

00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge (rev 02)
	Subsystem: ASUSTeK Computer Inc. Device 83ac
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller (rev 02) (prog-if 00 [VGA controller])
	Subsystem: ASUSTeK Computer Inc. Device 83ac
	Flags: bus master, fast devsel, latency 0, IRQ 43
	Memory at f5e00000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at cc00 [size=8]
	Memory at c0000000 (32-bit, prefetchable) [size=256M]
	Memory at f5d00000 (32-bit, non-prefetchable) [size=1M]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915

00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller (rev 02)
	Subsystem: ASUSTeK Computer Inc. Device 83ac
	Flags: bus master, fast devsel, latency 0
	Memory at f5e80000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
	Subsystem: ASUSTeK Computer Inc. Device 841c
	Flags: bus master, fast devsel, latency 0, IRQ 44
	Memory at f5cf8000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: fa000000-fbffffff
	Prefetchable memory behind bridge: 00000000e0000000-00000000f3ffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=03, sec-latency=0
	I/O behind bridge: 00001000-00001fff
	Memory behind bridge: f6000000-f9ffffff
	Prefetchable memory behind bridge: 00000000dc000000-00000000dfffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: f5f00000-f5ffffff
	Prefetchable memory behind bridge: 0000000080000000-00000000801fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
	Subsystem: ASUSTeK Computer Inc. Device 83ad
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at c400 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
	Subsystem: ASUSTeK Computer Inc. Device 83ad
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at c480 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.2 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
	Subsystem: ASUSTeK Computer Inc. Device 83ad
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at c800 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.3 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
	Subsystem: ASUSTeK Computer Inc. Device 83ad
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at c880 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 USB controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
	Subsystem: ASUSTeK Computer Inc. Device 83ad
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at f5cf7c00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=32
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
	Subsystem: ASUSTeK Computer Inc. Device 83ad
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt

00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA Controller [IDE mode] (rev 02) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: ASUSTeK Computer Inc. Device 83ad
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 21
	I/O ports at c080 [size=8]
	I/O ports at c000 [size=4]
	I/O ports at bc00 [size=8]
	I/O ports at b880 [size=4]
	I/O ports at b800 [size=16]
	Memory at f5cf7800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ata_piix
	Kernel modules: ata_piix

01:00.0 Ethernet controller: Atheros Communications Inc. AR8132 Fast Ethernet (rev c0)
	Subsystem: ASUSTeK Computer Inc. Device 838a
	Physical Slot: eeepc-wifi
	Flags: bus master, fast devsel, latency 0, IRQ 45
	Memory at f5fc0000 (64-bit, non-prefetchable) [size=256K]
	I/O ports at dc00 [size=128]
	Capabilities: <access denied>
	Kernel driver in use: atl1c
	Kernel modules: atl1c

02:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
	Subsystem: AzureWave Device 2047
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at f9ffc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: bcma-pci-bridge
	Kernel modules: wl, bcma

04:00.0 VGA compatible controller: NVIDIA Corporation GT218 [ION] (rev ff) (prog-if ff)
	!!! Unknown header type 7f
	Kernel driver in use: nvidia

04:00.1 Audio device: NVIDIA Corporation High Definition Audio Controller (rev ff) (prog-if ff)
	!!! Unknown header type 7f
	Kernel driver in use: snd_hda_intel


acpi-call related dmesg output:
acpi_call: Module loaded successfully
acpi_call: Calling \AMW0.DSTS
acpi_call: Call successful: 0x30003
acpi_call: Calling \_SB.PCI0.P0P4.DGPU.DOFF
acpi_call: Call successful: 0x0
```

xorg.conf.asus1015pn.optimushdmi
```
# start second xserver on nvidia gpu for hdmi out

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Files"
  ModulePath "/usr/lib/nvidia-current"
  ModulePath "/usr/lib/xorg/modules"
EndSection

Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "HDMI-TV"
    HorizSync       15.0 - 81.0
    VertRefresh     49.0 - 76.0
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "ION"
    Option         "NoLogo" "True"
    Option 	   "UseEDID" "True"
    Option 	   "ConnectedMonitor" "LVDS1"
    BusID          "PCI:4:0:0"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "metamodes" "LVDS1: nvidia-auto-select"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

Messages in the files show nvidia graphics disabled, but that's not true.

Feature: "TODO: Start Xserver (nvidia) on HDMI" is yellow, the rest of the options is in green.

I hope that all my posts are to be read correctly ;)

---

### Post by mtron on 2012-06-26
ok i see your problem. During boot the nvidia module loads automatically and prevents bbswitch from disabling the card. You are the first person where this happens and i don't know why this happens in your case. It might be related to your Kernel. You can try to blacklist the nvidia module (so it does not load on boot time).  

also test if bbswitch works on your kernel at all. 
as root:

remove all nvidia modules
```
rmmod -f nvidia
```
check that lsmod does not list the nvidia module any more 
now use bbswitch to disable the nvidia chip
```
tee /proc/acpi/bbswitch <<<ON
```
see the dmesg output if the power state got changed or not.

> Messages in the files show nvidia graphics disabled, but that's not true.

Yes, the script currently does not check if the power state changed, but it's on my todo list ;)

---

### Post by mtron on 2012-06-28
> **mtron said:**
> Yes, the script currently does not check if the power state changed, but it's on my todo list ;)

New version 0.7.5 uploaded to the [ppa]("https://launchpad.net/~mtron/+archive/eee1015pn"). It should get installed automatically once you run a system update. To trigger such an update now use:
```
sudo apt-get update && sudo apt-get dist-upgrade
```

```
Changelog:

  * added conffile /etc/eee1015pn/ds.conf
  * vga-selector-gui: implemented conffile.
  * display-settings: implemented conffile
  * display-settings: check if nvidia gpu really changed power mode
  * gpustatus: fix temperature readings. hwmon device node is not static 
```

The display settings script now checks if the nvidia gpu really changed the power state. This should fix the bug "PietroZ" reported.

Also the display-settings script reads it s settings from the config file /etc/eee1015pn/ds.conf

This file is a commented textfile. You can edit it manually or use the provided VGA-Selector gui. 

The conffile won't be overridden when updating the package so your custom defaultgpu and nvidia power state ect. will survive a version upgrade.

**Important Notice:**

Ubuntu Forums admins do NOT allow edits to posts any more so **up-to-date Documentation on the eee1015pn-acpitools Package is available at [http://mtron.co.nr/projects/eee1015pn](http://mtron.co.nr/projects/eee1015pn)**

The documentation in this thread (especially the links in the first post) is outdated!

I will update the [http://mtron.co.nr/projects/eee1015pn](http://mtron.co.nr/projects/eee1015pn) Page with every new release and post a release announcement here in this thread.

---

### Post by areUKEidding on 2012-07-01
> **mtron said:**
> If you want to change the default config for intel mode set the parameters in /etc/X11/xorg.conf.asus1015pn.intel or use randr to setup the dual monitors. see [here]("https://wiki.ubuntu.com/X/Config/Resolution")

I kind of solved my problem, I tried to have the resolution set automatically with xrandr, but it always reverted back to using the laptop display only. I was wondering if there is anything automatically run at startup that might do this and the only thing remotely close to that was the "jupiter restore configuration" setting.
I unchecked that and I am back again to automatic detection of my two displays. Now the question is, do I actually need that "restore configuration" feature at all or can I leave it off? I tried to set everything up with the jupiter tool, but it does only know the mirror mode for two displays, so not good enough for me.

---

### Post by mtron on 2012-07-02
don't you wanna get in touch with fewt (jupiter developer) to have this bug fixed ?

I dunno what implications your workaround might have, sorry.

---

### Post by Tersus* on 2012-07-02
Hallo mtron! :o

Ich wollte mal fragen, ob Du es bereits geschafft hast, das Scheduling-Problem Deines Skripts mit *SysVinit* unter Debian zu beseitigen. 

In einem Debian-Forum wurde mir gesagt, man könne auch *systemd* unter Debian installieren. Würde das Scheduling damit funktionieren? 


Beste Grüße! ;)

---

### Post by mtron on 2012-07-04
hello ! 

don't install a non default service manager. it has the potential to break everything badly. Debian wheezy (currently in feature freeze) will use systemd directly, so your best option is to just wait ;)

---

### Post by qt77h on 2012-07-06
I have a weird problem with the VGA switcher as I'm unable to launch any applications utilizing 3D effects whichever mode I boot in. (without eee1015pn-acpitools everything's working fine). My best guess it's a problem with the different Xorg configs and maybe the bleeding edge Nvidia drivers but I'm a bit of a novice when it comes to that. I've been contemplating installing noveau and would appreciate a link to a guide that outlines the clean removal of Nvidia drivers and replacing them with Noveau.

**System:**
EEE 1015PN, Xubuntu 12.04
Using nvidia drivers from ppa:ubuntu-x-swat/x-updates.

**Display-settings status** when booting with Nvidia or Optimus (nv-on)
```
INFO: ==== Loading Config ====
INFO: defaultgpu is set to nvidia
INFO: logging to file is disabled
INFO: nvidia auto power down disabled
INFO: ==== Config End ====
INFO: display-settings starting at 21:30:46 UTC 05072012
INFO: We are running on a EeePC-1015PN
INFO: detected Ubuntu based Distro
INFO: arch is i386
INFO: acpi_call Kernel module is available
```

Error-message examples:
*Torcs*
```
Xlib:  extension "GLX" missing on display ":0.0".
OpenGL GLX extension not supported by display ':0.0'
```
*glxspheres*
```
Xlib:  extension "GLX" missing on display ":0.0".
ERROR (593): Could not obtain RGB visual with requested properties
```

Slightly Off-Topic but EEE related:
I've having problems with my EEE Display for a while, getting non-reproducible screen flickering. I've tried the different fixes linked to a problem with the downclocking of the Nvidia driver but to no avail. Have other EEE users experienced similar problems? I had no luck with google as it's hard to narrow down the search. If this strays to much from the topic I'm sorry and feel free to ignore it ;)

---

### Post by mtron on 2012-07-06
glx libs can be fixed with:
```
sudo display-settings regenerate-glx
```

Now log out & back in (you need to restart the xserver)


No screen flickering here ;)

---

### Post by arunpatal on 2012-07-13
Hi, I have used a trick with which i can run Ubuntu with Express Gate button. [http://ubuntuforums.org/archive/index.php/t-1410167.html]("http://ubuntuforums.org/archive/index.php/t-1410167.html") Now the problem i am facing is that each time i run Ubuntu with express gate button it start with Nvidia only (1015PN). But if i start with normal power button via grub it works fine. I mean i can select any display with normal power button but with express gate button it works only with Nvidia..

I think there must be some setting in EFI Partition or Bios.

Can someone check and solve this Problem???

Thanks

---

### Post by mtron on 2012-07-14
No, i don't think that's the problem. It's more likely that this crippled Linux called "splashtop" OS has a very poor acpi implementation. 

Following the "Advanced Configuration and Power Interface Specification Rev5 (see [here]("http://www.acpi.info/spec.htm")) operating systems should query the _GPD (Get POST Device) _SPD (Set POST Device) and _VPO (Video POST Options) tables

A very short explanation of those Methods: (for more see Appendix B in the Acpi Specs linked above) 

- gpd method is used as a mechanism for the OS to query a CMOS value that determines which VGA device will be posted at boot. 

- spd method sets the active vga card for the next boot (we use this method to force vga modes)

- vpo method is used as a mechanism for the OS to determine what options are implemented. This method will be used in conjunction with _GPD and _SPD

So in your case it's most probably the routine to boot this splashtop os that has no proper acpi support. A possible fix might be to let this splashtop os boot via regular grub. this might work but i don't use splashtop so no guaranties ;)

---

### Post by arunpatal on 2012-07-14
> **mtron said:**
> So in your case it's most probably the routine to boot this splashtop os that has no proper acpi support. A possible fix might be to let this splashtop os boot via regular grub. this might work but i don't use splashtop so no  guaranties ;)

There are two ways to boot.
1st via kernal
2nd via grub.

i have tried both way but no use.
even if i boot windows 7 from splashtop via grub.....   it start nvidia only.
i love Ubuntu but i need battery life also.
I hope some one can look into this matter.

Thanks for quick reply

---

### Post by mtron on 2012-07-14
> **arunpatal said:**
> There are two ways to boot.
1st via kernal
2nd via grub.

this does not make any sense. you will always need a bootloader to boot a kernel.

> i have tried both way but no use. even if i boot windows 7 from splashtop via grub..... it start nvidia only.

again: i guess splashtop is crippled and has no proper - or a very buggy - acpi support, hence it resets the spd method to nvidia.

> i love Ubuntu but i need battery life also.

So forget about splashtop and just use ubuntu. VGA mode switching on the eee1015pn works flawlessly since more than a year already...

---

### Post by arunpatal on 2012-08-10
Hi, i install Ubuntu 10.10 and it runs really fast....
Everything is working really good except  acpitools.

I try to run 

(sudo apt-get install eee1015pn-acpitools build-essential debhelper module-assistant lm-sensors) 

but it says

(Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package eee1015pn-acpitools)

I know that support for Ubuntu 10.10 is not anymore but can anyone help with this please??

---

### Post by Nisitiiapi on 2012-08-10
Make sure you add the repository for eee1015pn-acpitools.  But, I do not know if it will work with 10.10.  I believe the repository is only for 11.10 and 12.04.  You may need to download an older deb that is compatible with 10.10.  Mtron can confirm this.

---

### Post by arunpatal on 2012-08-10
> **Nisitiiapi said:**
> Make sure you add the repository for eee1015pn-acpitools.  But, I do not know if it will work with 10.10.  I believe the repository is only for 11.10 and 12.04.  You may need to download an older deb that is compatible with 10.10.  Mtron can confirm this.

Thats true that it works with 11.10 and 12.04
But it use to work with 10.10 also
I also think that i need the old .deb which is compatible with 10.10 but i can not find it anymore. :(
Please upload this file if anyone have it

---

### Post by arunpatal on 2012-08-12
Hi Mtron, i am waiting for your reply... can you please confirm this... I know support for 10.10 is not anymore, but still trying my luck.

---

### Post by mtron on 2012-08-13
Hello! 

As you suspected, 10.10 and 11.04 are not supported by the current version of the scripts. A lot of internal configuration stuff changed from gnome2 to gnome3 and also the xserver config changed.

But i will have a look if i can find a old version on my backups for you. I'm currently on holidays so it will take me some days.

cheers!

---

### Post by arunpatal on 2012-08-13
> **mtron said:**
> Hello! 

As you suspected, 10.10 and 11.04 are not supported by the current version of the scripts. A lot of internal configuration stuff changed from gnome2 to gnome3 and also the xserver config changed.

But i will have a look if i can find a old version on my backups for you. I'm currently on holidays so it will take me some days.

cheers!

Thanks, i will be waiting....
wish you nice holidays

---

### Post by AmiNimA on 2012-08-25
Good for 1015n owners... and poor 1215n ones...
As I read some parts of this thread, I found that 1215n is not supported by your script. I'm using bumblebee in my 1215n, but as you might know, it's useless. It's only useful to turn off the Nvidia card.
But your script allows users to choose the default device for the next boot. intel, nvidia, or both of them (optimus). I wanted to know how I can choose nvidia or intel as the default device for the next boot (in 1215n) without your script? as you've developed such a great script, you might help me doing this. It's not important to make it GUI, commandline is ok ;)

I'm using debian wheezy + gnome-shell + bumblebee installed

Thanks in advance

---

### Post by mtron on 2012-08-27
> I wanted to know how I can choose nvidia or intel as the default device for the next boot (in 1215n) without your script?

Hello! 

The 1015pn has a quite rare hardware design. Both gpu's are directly wired to the Laptop's LVDS panel and this physical connection is the important part.

Most "optimus" laptops don't have this wire from the nvidia gpu to the display, so the nvidia gpu draws to the intel framebuffer and not to the screen directly.

Easiest to check if your laptop has this design feature is to turn it off & back on and see what gpu is active per default. If the nvidia gpu is active your hardware design is ok (if the intel gpu is active you're out of luck)

Then you need to dump the dsdt tables to find the acpi_call, but let's see if your hardware design is useable first ;)

---

### Post by AmiNimA on 2012-08-27
> **mtron said:**
> Hello! 
Easiest to check if your laptop has this design feature is to turn it off & back on and see what gpu is active per default. If the nvidia gpu is active your hardware design is ok (if the intel gpu is active you're out of luck)

Then you need to dump the dsdt tables to find the acpi_call, but let's see if your hardware design is useable first ;)

The default GPU is intel. I don't get your meaning, every time, the default gpu is intel. how can we confirm it with a command?!

find the attachment, this is an output of lspci -vv of this laptop. maybe it could help.

---

### Post by mtron on 2012-08-28
> **mtron said:**
> Hello! 
if the intel gpu is active you're out of luck

i guess this is pretty clear. Your laptop does not have the required hardware mux so you can't use this script.

---

### Post by arunpatal on 2012-08-31
Hi Mtron, i was looking for 1015pn graphic cards script for Ubuntu 10.10 but i could not find on internet.
You told be that you might have it in your backup....  can you please check for me and upload if you have...

Thanks

---

### Post by barthus on 2012-09-19
Dear all.

This thread seems to be frequently visited: We have had 378 replies and about 65 508 visitors. Thanks to mtron, the switching between the two GPUs is working quite well for the 1015PN ! :popcorn: (well, at least in my case) 

Thanks mtron! 

Cheers.

---

### Post by mtron on 2012-10-11
Hello! 

I've just uploaded the new Version 0.8.0 to the [ppa]("https://launchpad.net/~mtron/+archive/eee1015pn") 

Changelog:

  * Added Support for ubuntu Quantal 12.10
  * migrated keybindings to dconf

Since Quantal keybindings are stored in dconf schemas, so i needed to migrate them from the old gconf xml files. Currently the new version is only available & useful for quantal installs.

Cheers!

---

### Post by finny388 on 2012-10-11
Thanks for all your ongoing work mtron. I hope you know there are many, many people that appreciate it all.

I for one am very grateful.

):P

---

### Post by petehild on 2012-10-26
Hi,

I have a problem with my 1015pn and quantal.

I did a fresh quantal install (including all the updates).

I installed mtrons ppa with:
sudo add-apt-repository ppa:mtron/eee1015pn
sudo apt-get update && sudo apt-get dist-upgrade
sudo apt-get install eee1015pn-acpitools

Now after rebooting, I end up with just the shell. The desktop will not load anymore.

sudo display-settings status
tells me acpi_call.ko could not be loaded.

Any idea what the problem might be and why the modules can't be loaded?

Thanks.
Pete

---

### Post by mtron on 2012-10-27
yes. Probably you did not reboot to the latest installed kernel before installing the dkms module. 

For a better bug analysis i need the dkms log of the faild build.

to check if this is your problem:
Reboot in the lastest installed Kernel and run from the command prompt
```
uname -a
dkms status
```

if the acpi-call module does not show up at all:

```
sudo apt-get install --reinstall acpi-call-tools
```

if acpi-call is listed for an older kernel but not the current one 

Switch to root or prefix with sudo

```
dkms build -m acpi-call -v 1.1.1 -k $(uname -r)
dkms install -m acpi-call -v 1.1.1 -k $(uname -r)
depmod 
modprobe acpi-call
```

What the commands do:
- build acpi-call module version for the current kernel
- install the compiled module to /lib/modules
- re-generate kernel modules (with our new one)
- load the acpi-call module 

You can check acpi_call related kernel messages with

```
dmesg | grep acpi_call
```

---

### Post by petehild on 2012-10-27
Hi mtron,

thanks for helping me.

I know now why acpi_call didn't compile for me, I had the wrong kernel-headers installed.

I can load acpi_call now, but it still won't boot into the graphical desktop.

```
$ uname -a
Linux seashell 3.5.0-17-generic #28-Ubuntu SMP Tue Oct 9 19:31:23 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
``````
$ dkms status
acpi-call, 1.1.1, 3.5.0-17-generic, x86_64: installed
bbswitch, 0.4.2, 3.5.0-17-generic, x86_64: installed
bcmwl, 5.100.82.112+bdcom, 3.5.0-17-generic, x86_64: installed
nvidia-current, 304.43, 3.5.0-17-generic, x86_64: installed
```After boot:
```
$ dmesg | grep acpi_call
[   24.121845] acpi_call: Module loaded successfully
[   24.426121] acpi_call: Calling \AMW0.DSTS 0x90013
[   24.426847] acpi_call: Call successful: 0x30001
```Like I said my 1015pn doesn't boot to the graphical desktop, but the stange thing is, when I do
```
$ sudo apt-get remove eee1015pn-acpitools
``` the boot process continues and lightdm starts. I don't have to reboot only launching apt-get remove leads to the start of lightdm...

I'm confused... ;)

---

### Post by mtron on 2012-10-28
hello! 

Please post /var/log/Xorg.0.log when lightdm fails to start. Also did you try to start lightdm from a terminal directly?  (just "sudo lightdm") This might show a error message.

---

### Post by petehild on 2012-10-28
After doing:
```
sudo apt-get install eee1015pn-acpitools
```the boot process hangs on "F7" with the ubuntu screen and the five red dots moving from left to right. When I push ESC I see only "OKs" and no "Fails" the last 4 lines are:
```
Starting GNOME Display Manager
Stopping GNOME Display Manager
Starting Mount network filesystem
Stopping Mount network filesystem
```When I log in like on "Strg+Alt+F1", and do a ll /var/log I see that the Xorg.0.log is not from the current boot. It's from the last time X worked, because the timestamp is to far in the past.

sudo service lightdm stop     ----> hangs
sudo service lightdm start     ----> hangs

sudo lightdm    ----> and lightdm starts immediately

all I did so far on my 1015pn
- install quantal
- install all the updates
- install gnome-shell
- add your ppa

---

### Post by mtron on 2012-10-29
HEllo! 

I tried to reproduce this bug, and got the same result. the problem is that gnome-shell depends on gdm (the native gnome login manager => this is a Packaging bug. gnome-shell should just suggest or recommend gdm, not depend on it. Please report this bug to the gnome-shell ubuntu maintainers) so it gets installed automatically with gnome shell. 

Although in theory gnome's gdm and ubuntu's lightdm shold co-exist next to each other in practice they don't.

What i did to work around this bug: Use one of the 2 login managers and purge the other one. I kept lightdm, so

sudo apt-get purge gdm
sudo apt-ger install --reinstall lightdm unity-greeter

After doing this i rebooted and lightdm auto starts again. If the Login manager still does not start on you system please provide the /var/log/lightdm/lightdm.log file

---

### Post by petehild on 2012-10-29
Thanks a lot, that helped :)

I had to go with gdm, because purge gdm also purges the gnome-shell.
I noticed that when I use gdm, lightdm can be installed next to gdm. When I use lightdm, gdm can not be present.

Any idea, why 
**sudo apt-get remove eee1015pn-acpitools**
seems to "fix" the issue?

---

### Post by mtron on 2012-10-29
I suspect a bug in lightdm. Since it's been rewritten recently it might block something in the start process. 

But this is just a guess ;) you could compare the changes in the lightdm package since precise and test what commit broke this. 

Best workaround is to fix the gnome-shell package and remove the gdm Dependency.

---

### Post by petehild on 2012-10-30
I might have look into the gnome-shell package, when I find the time :)

thanks again for your help :)

---

### Post by guitwo on 2012-11-09
Hi Mtron, hi everyone,

I'm back again with a question, I was trying to use the "start a second X server (nvidia) on HDMI, I configured it as it has to be done, but when I launch the vga-selector-gui I get theses error messages when going to advance settings :

```

** (gnome-control-center:5467): WARNING **: Ignoring additional argument Open Display Settings

(gnome-control-center:5467): Gtk-WARNING **: GtkTable does not have a property called expand

(gnome-control-center:5467): Gtk-WARNING **: GtkTable does not have a property called fill

(gnome-control-center:5467): Gtk-WARNING **: GtkTable does not have a property called position

(gnome-control-center:5467): GLib-GIO-CRITICAL **: g_settings_get_value: assertion `G_IS_SETTINGS (settings)' failed

(gnome-control-center:5467): GLib-CRITICAL **: g_variant_get_type: assertion `value != NULL' failed

(gnome-control-center:5467): GLib-CRITICAL **: g_variant_type_is_subtype_of: assertion `g_variant_type_check (type)' failed

(gnome-control-center:5467): GLib-CRITICAL **: g_variant_get_int32: assertion `g_variant_is_of_type (value, G_VARIANT_TYPE_INT32)' failed

(gnome-control-center:5467): GLib-CRITICAL **: g_variant_unref: assertion `value != NULL' failed
Xlib:  extension "NV-GLX" missing on display ":0.0".
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  153 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  17
  Current serial number in output stream:  18

```

Here is the result of sudo display-settings status :

```

INFO: ==== Loading Config ====
INFO: defaultgpu is set to optimus
INFO: logging to file is disabled
INFO: nvidia auto power down enabled
INFO: ==== Config End ====
INFO: display-settings starting at 23:13:11 UTC 10112012
INFO: We are running on a EeePC-1015PN
INFO: detected Ubuntu based Distro
INFO: arch is x86_64
INFO: acpi_call Kernel module is available
INFO: bbswitch Kernel module is available
INFO: Optimus dual gpu mode active
INFO: Intel GMA 3150 on PCI 00:02.0 and Nvidia GT218 on 04:00.0
INFO: NVidia GPU is powered off

```


Should I be worried ?
Shall I regenerate GLX ?

Thanks in advance for the help !
And congratulations for all this wonderful work !

---

### Post by mtron on 2012-11-10
what nvidia driver version do you have installed? if the optirun session fails for some reason run 'sudo display-settings fix' from a terminal. This will reset the glx libs to intel. 

can you send me a email with the report bug wizzard in the gui script please? This collects some debug info that makes my life easier ;)

---

### Post by zoltux on 2012-11-11
Hi,

first, thank you mtron for your great work. 

Since updating to 12.10, with the Intel graphics active the unity launcher (left icon bar) does not appear after login. There is only the  blank desktop. 
Booting with the nvidia graphics everything is fine.

Any hints to get Unity working with the intel graphics?

---

### Post by mtron on 2012-11-12
@zoltux when the login screen appears press STRG+ALT+F2 to switch to a text login, and provide your username and password.

After the login check that your internet connection works (nmcli) and run
```
sudo display-settings regenerate-glx
```

now restart lightdm.

@guitwo: thanks, i recieved your logs. Will have a look at them today after work.

---

### Post by Tersus* on 2012-11-20
Hello mtron,

I allready sent you a pm, but I want to make my issue public. 

In the optimus-mode or intel-mode, my screen resolution is for a few seconds 640*480 (or 800*600). Thereafter, the resolution changes to 1024*600. 
In the nvidia-mode the (mouse)cursor is flickering and when I start the NVIDIA X-Server-Settings the following message appears: 
"You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."

Do you know whats wrong with my system?

---

### Post by mtron on 2012-11-21
do you mind sending me a bugreport? i need more info on your setup to debug this.

---

### Post by barthus on 2012-11-21
Hello all.

I know, its not related to the GPU switch, it's related rather to compiz etc. May be you can help.
Since the last Ubuntu update I have a severe problem: When starting the laptop compiz crashes. Manually  starting compiz yields:
```

$ compiz --replace
Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : gconf
Integration : true
Profile     : default
Adding plugins
Initializing core options...done
Initializing composite options...done
Speicherzugriffsfehler (Speicherabzug geschrieben)
```Do you experienced same problems? Can somebody help? - I have other 2 laptops (no 1015PN) and the update perfectly worked!

Thanks!

Cheers.

**EDIT:** I deleted the complete root system and played a backup of it which I once obtained before. This version certainly worked since it was a stable one. After having done a 'sudo apt-get udate & upgrade', the system was still okay, compiz had no problem. But then I have done a 'sudo apt-get dist-upgrade' => COMPIZ CRASHES.

So, it must be one of these:
```
eee1015pn-acpitools linux-generic linux-headers-generic linux-image-generic

```I try now to determine the source by upgrading one package after the other one.

---

### Post by barthus on 2012-11-22
This concerns message 398!

I just found out some minutes ago that the phenomena of compiz crashing on my 1015PN appears when I upgrade my system with 

```
eee1015pn-acpitools
```The latter was manually upgraded with 'sudo apt-get install eee1015pn-acpitools'.

Mtron, do you have any idea? :P Just tell me what you need to know ... .

---

### Post by Tersus* on 2012-11-22
I thought it was all right, but I was wrong. Exactly does it clean?

 - sudo display-settings regenerate-glx
```
INFO: ==== Loading Config ====
INFO: defaultgpu is set to optimus
INFO: logging to file is disabled
INFO: nvidia auto power down enabled
INFO: ==== Config End ====
INFO: display-settings starting at 19:16:51 UTC 22112012
INFO: We are running on a EeePC-1015PN
INFO: detected Ubuntu based Distro
INFO: arch is x86_64
INFO: acpi_call Kernel module is available
INFO: Regenerating the glx libraries
INFO: Reinstalling glx core packages
Paketlisten werden gelesen...
Abhängigkeitsbaum wird aufgebaut...
Statusinformationen werden eingelesen...
0 aktualisiert, 0 neu installiert, 1 erneut installiert, 0 zu entfernen und 0 nicht aktualisiert.
Es müssen noch 0 B von 67,8 MB an Archiven heruntergeladen werden.
Nach dieser Operation werden 0 B Plattenplatz zusätzlich benutzt.
(Lese Datenbank ...  (Lese Datenbank ... 5% (Lese Datenbank ... 10% (Lese Datenbank ... 15% (Lese Datenbank ... 20% (Lese Datenbank ... 25% (Lese Datenbank ... 30% (Lese Datenbank ... 35% (Lese Datenbank ... 40% (Lese Datenbank ... 45% (Lese Datenbank ... 50% (Lese Datenbank ... 55% (Lese Datenbank ... 60% (Lese Datenbank ... 65% (Lese Datenbank ... 70% (Lese Datenbank ... 75% (Lese Datenbank ... 80% (Lese Datenbank ... 85% (Lese Datenbank ... 90% (Lese Datenbank ... 95% (Lese Datenbank ... 100% (Lese Datenbank ... 166992 Dateien und Verzeichnisse sind derzeit installiert.) 
Vorbereitung zum Ersetzen von nvidia-current 304.64-0ubuntu1~precise~xup1 (durch .../nvidia-current_304.64-0ubuntu1~precise~xup1_amd64.deb) ... 
Removing all DKMS Modules 
Done. 
Ersatz für nvidia-current wird entpackt ... 
Trigger für man-db werden verarbeitet ... 
nvidia-current (304.64-0ubuntu1~precise~xup1) wird eingerichtet ... 
update-initramfs: deferring update (trigger activated) 
INFO:Enable nvidia-current 
DEBUG:Parsing /usr/share/nvidia-common/quirks/put_your_quirks_here 
DEBUG:Parsing /usr/share/nvidia-common/quirks/lenovo_thinkpad 
DEBUG:Parsing /usr/share/nvidia-common/quirks/dell_latitude 
DEBUG:Processing quirk ThinkPad T420s 
DEBUG:Failure to match ASUSTeK Computer INC. with LENOVO 
DEBUG:Quirk doesn't match 
DEBUG:Processing quirk Latitude E6530 
DEBUG:Failure to match ASUSTeK Computer INC. with Dell Inc. 
DEBUG:Quirk doesn't match 
Loading new nvidia-current-304.64 DKMS files... 
Building only for 3.2.0-33-generic 
Building for architecture x86_64 
Building initial module for 3.2.0-33-generic 
Done. 
 
nvidia_current: 
Running module version sanity check. 
 - Original module 
   - No original module exists within this kernel 
 - Installation 
   - Installing to /lib/modules/3.2.0-33-generic/kernel/drivers/char/drm/ 
 
depmod.... 
 
DKMS: install completed. 
Trigger für bamfdaemon werden verarbeitet ... 
Rebuilding /usr/share/applications/bamf.index... 
Trigger für initramfs-tools werden verarbeitet ... 
update-initramfs: Generating /boot/initrd.img-3.2.0-33-generic 
Warning: No support for locale: de_DE.utf8 
Paketlisten werden gelesen...
Abhängigkeitsbaum wird aufgebaut...
Statusinformationen werden eingelesen...
0 aktualisiert, 0 neu installiert, 1 erneut installiert, 0 zu entfernen und 0 nicht aktualisiert.
Es müssen noch 0 B von 1.719 kB an Archiven heruntergeladen werden.
Nach dieser Operation werden 0 B Plattenplatz zusätzlich benutzt.
(Lese Datenbank ...  (Lese Datenbank ... 5% (Lese Datenbank ... 10% (Lese Datenbank ... 15% (Lese Datenbank ... 20% (Lese Datenbank ... 25% (Lese Datenbank ... 30% (Lese Datenbank ... 35% (Lese Datenbank ... 40% (Lese Datenbank ... 45% (Lese Datenbank ... 50% (Lese Datenbank ... 55% (Lese Datenbank ... 60% (Lese Datenbank ... 65% (Lese Datenbank ... 70% (Lese Datenbank ... 75% (Lese Datenbank ... 80% (Lese Datenbank ... 85% (Lese Datenbank ... 90% (Lese Datenbank ... 95% (Lese Datenbank ... 100% (Lese Datenbank ... 166992 Dateien und Verzeichnisse sind derzeit installiert.) 
Vorbereitung zum Ersetzen von xserver-xorg-core 2:1.11.4-0ubuntu10.8 (durch .../xserver-xorg-core_2%3a1.11.4-0ubuntu10.8_amd64.deb) ... 
Ersatz für xserver-xorg-core wird entpackt ... 
Trigger für man-db werden verarbeitet ... 
xserver-xorg-core (2:1.11.4-0ubuntu10.8) wird eingerichtet ... 
INFO: updating MD5sums for libglx.so
INFO: linking libglx.so
INFO: setting active libglx.so
INFO: Regeneration completed. Log out and back in to activate the new glx libs
```

---

### Post by Tersus* on 2012-11-29
I ask again: Is the above output correct? What does mean the lines that beginn with DEBUG? Is it possible that the driver (304.64-0ubuntu1~precise~xup1) is not suppoerted?

---

### Post by mtron on 2012-11-30
hello! 

The output looks good, so nothing to worry here. Those debug lines are part of the nvidia drivers package for ubuntu and since none of the quirks match they do nothing.

After your last pm i thought your problem is solved, so i did not comment on this. 

If you're still hit buy this or another bug please send me a bugreport via the gui containing
- description of the bug
- clear steps to reproduce
- attach the auto collected logs

Cheers!

---

### Post by Klaster on 2013-01-15
Hey there,
I updated to 12.10 a few days ago and it turned out badly (no unity 3d support, so no panels at all). Anyway, I downgraded today again and with unity 2d everything works well so far.

Since I have to set up my computer, I was wondering whether a combination of mtrons tools and bumblebee has ever been tested? I like the idea of the optirun-function of bumblebee, however, I've never used Bumblebee and had a stable system with mtrons tools (thanks again, mtron!).

So - anybody with experience regarding mtron-eee1015-tool + bumblebee?

Cheers,
Jakob

---

### Post by mtron on 2013-01-16
> **Klaster said:**
>  I was wondering whether a combination of mtrons tools and bumblebee has ever been tested

sure it was tested when i introduced it :) i don't use 12.10 (still on the 12.04 lts ubuntu version) so it might be broken there. 

But i have not used bumblebee in ages (because of the known problems like no vdpau, bad preformance ect. our nvidia exclusive mode does not show any of those, so...)

If you want to debug the Bumblebee problem read on.

Did you disable the auto power down of the nvidia chip on boot? (it's a option in the settings dialog of the vga-selector app) bumblebee gets confused if the nvidia chip is not powered on during boot.

To debug what's happening enable "write debug output" and "log to file" in the settings dialog of the vga-selector app.  Now reboot to optimus mode and try to run a application prefixed with 'optirun' from the terminal and post the errors you get there, as well as the logfile created by the vga-selector app.

---

### Post by doc.maizo on 2013-01-17
> **mtron said:**
> still on the 12.04 lts ubuntu version

Hi mtron!
I have made a fresh install of 12.04 on the 1015pn following your instructions; everithing's ok, but I don't have HDMI audio out; in optimus mode I can send video out through HDMI but audio doesn't work.
The strange thing is that when I go to audio settings I can only see internal audio and not hdmi; this happens only in unity mode; if I rebbot in gnome classic mode I can choose HDMI audio (but I cannot test it now because since I realized that I could not reach an HDMI monitor).
I've tried also whit ```
alsamixer
``` but there is no HDMI and I can reach spdif "mute switch" only pressing F6 to switch sound board.
Another strange thing is that, booting in fallback gnome I cannot add buttons to the bars on top and bottom of the screen: if I press right button on them nothing happens, amd in system settings there isn't any "set of settings" where I can solve this.
Thanks in advance for the help, and for all your work for 1015PN.
maizo

---

### Post by mtron on 2013-01-17
My hdmi monitor does not have any speakers so i can't test the audio over hdmi part when running a second X Screen. 

If you figure out how to make this work let me know :)

does aplay -l list the nvidia device when started from a terminal on the second X-Screen?

---

### Post by doc.maizo on 2013-01-18
> **mtron said:**
> If you figure out how to make this work let me know

I've configured gnome-fallback properly. As soon as I'll have an HDMI monitor to test I'll post the results. Thx!

---

### Post by Lead Expression on 2013-02-19
**[COLOR=Red]Update in next post[/COLOR]**

Hi, mtron,
Tried to install optimus on a fresh 12.04 LTS installation on ASUS 1015pn using this guide [https://sites.google.com/site/mtrons/howtos/eeepc-1015pn](https://sites.google.com/site/mtrons/howtos/eeepc-1015pn). 
After:

```
sudo sensors-detect
sudo reboot
```I get a completely blank screen.  
What do you suggest to do? This is my second trial and the result is the same (the first with 12.10).

Thanks a lot.

Edit: 
```
dmesg | grep acpi_call
[13.080324] acpi_call: Module loaded successfully
[13.563595] acpi_call: Calling \AMW0.DSTS
[13.564415] acpi_call: Call successful: 0x30001
```I tried to load from shell "sudo lightdm". It sends me to shell 7 (the one of the GUI) which last line is:
```
* Checking battery state...   [OK]
```or sometimes:
I had this message pressing CTRL-ALT-F7:
```
[7.458236] INFO @w1_cfg80211_attach : Registered CFG80211 phy
[7.697036] cdc_acm 1-2:1.3: This device cannot do calls on its own, it is not a modem.
could not write bytes: Broken pipe
```Sometimes the line changes and arrives to "LightDM Display Manager start (OK status). After that is completely frozen, CTRL-C doesn't work. CTRL-ALT-F1 have this output after sudo lightdm:
```
Failed to use bus name org.freedesktop.DisplayManager, do you have appropriate permissions?
```The strange is that if I am on shell 7 and the system freeze, I cannot access to other shells. Also removing eee1015pn-acpitools doesn't fix the problem.

Note: package gdm (I read from [#388]("http://ubuntuforums.org/showpost.php?p=12324033&postcount=388")) is not installed. I tried to reinstall lightdm but no differences.

Please tell me what can I paste here something helpful (I have another PC).

Thanks a lot.

---

### Post by Lead Expression on 2013-02-19
Ok, let's start from the beginning.
I've installed freshly Ubuntu 12.04 LTS Desktop i386 without internet connection. Trying to install nvidia-current and nvidia-settings:
```
sudo apt-get install nvidia-current nvidia-settings
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 nvidia-current : Depends: xorg-video-abi-11
                  Depends: xserver-xorg-core (>= 2:1.10.99.901)
E: Unable to correct problems, you have held broken packages.

```

After update
```
sudo apt-get update && sudo apt-get dist-upgrade
```

I got the same error. Previously I resolved by installing xorg-video-abi-11. Is it correct? How I have to proceed? I haven't found same error in the Internet and I am not able to figure out how to go on...

Thank you

---

### Post by mtron on 2013-02-20
Hello! 

Can you boot into a text console and examine the /var/log/Xorg.log file?
(you can copy it to a usb stick and post it here) 

If you want we can meet in a IRC chat. write me a pm and we can shedule a time.

---

### Post by Lead Expression on 2013-02-20
Dear mtron,

Thank you very much for your reply. Currently I made a fresh Ubuntu installation as said so I am writing from my 1015pn (with two graphic cards enabled and vulcanic temperature under the keyboard :) ). Currently /var/log/Xorg.0.log (I think you are referring to this) is the following:

```
[    12.026] 
X.Org X Server 1.13.0
Release Date: 2012-09-05
[    12.026] X Protocol Version 11, Revision 0
[    12.026] Build Operating System: Linux 2.6.42-34-generic i686 Ubuntu
[    12.026] Current Operating System: Linux nik-1015PN 3.5.0-24-generic #37~precise1-Ubuntu SMP Thu Feb 7 13:50:53 UTC 2013 i686
[    12.026] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-24-generic root=UUID=87099e87-41c7-4ce7-8c28-05ec5780dcd2 ro quiet splash vt.handoff=7
[    12.026] Build Date: 19 January 2013  12:41:05PM
[    12.026] xorg-server 2:1.13.0-0ubuntu6.1~precise2 (For technical support please see http://www.ubuntu.com/support) 
[    12.026] Current version of pixman: 0.24.4
[    12.026] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    12.026] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    12.027] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Feb 20 09:07:56 2013
[    12.048] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    12.049] (==) No Layout section.  Using the first Screen section.
[    12.049] (==) No screen section available. Using defaults.
[    12.049] (**) |-->Screen "Default Screen Section" (0)
[    12.049] (**) |   |-->Monitor "<default monitor>"
[    12.050] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    12.050] (==) Automatically adding devices
[    12.050] (==) Automatically enabling devices
[    12.050] (==) Automatically adding GPU devices
[    12.051] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    12.051] 	Entry deleted from font path.
[    12.051] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    12.051] 	Entry deleted from font path.
[    12.051] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    12.051] 	Entry deleted from font path.
[    12.051] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    12.051] 	Entry deleted from font path.
[    12.051] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    12.051] 	Entry deleted from font path.
[    12.051] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    12.051] 	Entry deleted from font path.
[    12.051] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[    12.051] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    12.051] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    12.051] (II) Loader magic: 0xb77e4620
[    12.051] (II) Module ABI versions:
[    12.052] 	X.Org ANSI C Emulation: 0.4
[    12.052] 	X.Org Video Driver: 13.0
[    12.052] 	X.Org XInput driver : 18.0
[    12.052] 	X.Org Server Extension : 7.0
[    12.053] (II) config/udev: Adding drm device (/dev/dri/card0)
[    12.058] (--) PCI:*(0:4:0:0) 10de:0a6f:1043:8470 rev 162, Mem @ 0xfa000000/16777216, 0xe0000000/268435456, 0xf2000000/33554432, I/O @ 0x0000ec00/128, BIOS @ 0x????????/524288
[    12.058] (II) Open ACPI successful (/var/run/acpid.socket)
[    12.058] Initializing built-in extension Generic Event Extension
[    12.058] Initializing built-in extension SHAPE
[    12.058] Initializing built-in extension MIT-SHM
[    12.058] Initializing built-in extension XInputExtension
[    12.059] Initializing built-in extension XTEST
[    12.059] Initializing built-in extension BIG-REQUESTS
[    12.059] Initializing built-in extension SYNC
[    12.059] Initializing built-in extension XKEYBOARD
[    12.059] Initializing built-in extension XC-MISC
[    12.059] Initializing built-in extension SECURITY
[    12.059] Initializing built-in extension XINERAMA
[    12.059] Initializing built-in extension XFIXES
[    12.059] Initializing built-in extension RENDER
[    12.059] Initializing built-in extension RANDR
[    12.059] Initializing built-in extension COMPOSITE
[    12.059] Initializing built-in extension DAMAGE
[    12.059] Initializing built-in extension MIT-SCREEN-SAVER
[    12.059] Initializing built-in extension DOUBLE-BUFFER
[    12.059] Initializing built-in extension RECORD
[    12.059] Initializing built-in extension DPMS
[    12.059] Initializing built-in extension X-Resource
[    12.059] Initializing built-in extension XVideo
[    12.059] Initializing built-in extension XVideo-MotionCompensation
[    12.059] Initializing built-in extension XFree86-VidModeExtension
[    12.060] Initializing built-in extension XFree86-DGA
[    12.060] Initializing built-in extension XFree86-DRI
[    12.060] Initializing built-in extension DRI2
[    12.060] (II) LoadModule: "glx"
[    12.349] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    12.350] (II) Module glx: vendor="X.Org Foundation"
[    12.350] 	compiled for 1.13.0, module version = 1.0.0
[    12.350] 	ABI class: X.Org Server Extension, version 7.0
[    12.350] (==) AIGLX enabled
[    12.350] Loading extension GLX
[    12.350] (==) Matched nvidia as autoconfigured driver 0
[    12.350] (==) Matched nouveau as autoconfigured driver 1
[    12.350] (==) Matched nv as autoconfigured driver 2
[    12.350] (==) Matched nvidia as autoconfigured driver 3
[    12.350] (==) Matched nouveau as autoconfigured driver 4
[    12.350] (==) Matched nv as autoconfigured driver 5
[    12.350] (==) Matched vesa as autoconfigured driver 6
[    12.351] (==) Matched modesetting as autoconfigured driver 7
[    12.351] (==) Matched fbdev as autoconfigured driver 8
[    12.351] (==) Assigned the driver to the xf86ConfigLayout
[    12.351] (II) LoadModule: "nvidia"
[    12.353] (WW) Warning, couldn't open module nvidia
[    12.354] (II) UnloadModule: "nvidia"
[    12.354] (II) Unloading nvidia
[    12.354] (EE) Failed to load module "nvidia" (module does not exist, 0)
[    12.354] (II) LoadModule: "nouveau"
[    12.356] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    12.358] (II) Module nouveau: vendor="X.Org Foundation"
[    12.358] 	compiled for 1.13.0, module version = 1.0.2
[    12.358] 	Module class: X.Org Video Driver
[    12.358] 	ABI class: X.Org Video Driver, version 13.0
[    12.358] (II) LoadModule: "nv"
[    12.360] (WW) Warning, couldn't open module nv
[    12.360] (II) UnloadModule: "nv"
[    12.360] (II) Unloading nv
[    12.360] (EE) Failed to load module "nv" (module does not exist, 0)
[    12.360] (II) LoadModule: "vesa"
[    12.362] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    12.362] (II) Module vesa: vendor="X.Org Foundation"
[    12.362] 	compiled for 1.13.0, module version = 2.3.2
[    12.362] 	Module class: X.Org Video Driver
[    12.362] 	ABI class: X.Org Video Driver, version 13.0
[    12.362] (II) LoadModule: "modesetting"
[    12.363] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    12.364] (II) Module modesetting: vendor="X.Org Foundation"
[    12.364] 	compiled for 1.13.0, module version = 0.5.0
[    12.364] 	Module class: X.Org Video Driver
[    12.364] 	ABI class: X.Org Video Driver, version 13.0
[    12.364] (II) LoadModule: "fbdev"
[    12.365] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    12.365] (II) Module fbdev: vendor="X.Org Foundation"
[    12.365] 	compiled for 1.13.0, module version = 0.4.3
[    12.365] 	Module class: X.Org Video Driver
[    12.366] 	ABI class: X.Org Video Driver, version 13.0
[    12.366] (==) Matched nvidia as autoconfigured driver 0
[    12.366] (==) Matched nouveau as autoconfigured driver 1
[    12.366] (==) Matched nv as autoconfigured driver 2
[    12.366] (==) Matched nvidia as autoconfigured driver 3
[    12.366] (==) Matched nouveau as autoconfigured driver 4
[    12.366] (==) Matched nv as autoconfigured driver 5
[    12.366] (==) Matched vesa as autoconfigured driver 6
[    12.366] (==) Matched modesetting as autoconfigured driver 7
[    12.366] (==) Matched fbdev as autoconfigured driver 8
[    12.366] (==) Assigned the driver to the xf86ConfigLayout
[    12.366] (II) LoadModule: "nvidia"
[    12.368] (WW) Warning, couldn't open module nvidia
[    12.368] (II) UnloadModule: "nvidia"
[    12.368] (II) Unloading nvidia
[    12.368] (EE) Failed to load module "nvidia" (module does not exist, 0)
[    12.368] (II) LoadModule: "nouveau"
[    12.369] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    12.369] (II) Module nouveau: vendor="X.Org Foundation"
[    12.370] 	compiled for 1.13.0, module version = 1.0.2
[    12.370] 	Module class: X.Org Video Driver
[    12.370] 	ABI class: X.Org Video Driver, version 13.0
[    12.370] (II) UnloadModule: "nouveau"
[    12.370] (II) Unloading nouveau
[    12.370] (II) Failed to load module "nouveau" (already loaded, 0)
[    12.370] (II) LoadModule: "nv"
[    12.372] (WW) Warning, couldn't open module nv
[    12.373] (II) UnloadModule: "nv"
[    12.373] (II) Unloading nv
[    12.373] (EE) Failed to load module "nv" (module does not exist, 0)
[    12.373] (II) LoadModule: "vesa"
[    12.374] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    12.374] (II) Module vesa: vendor="X.Org Foundation"
[    12.374] 	compiled for 1.13.0, module version = 2.3.2
[    12.374] 	Module class: X.Org Video Driver
[    12.374] 	ABI class: X.Org Video Driver, version 13.0
[    12.374] (II) UnloadModule: "vesa"
[    12.374] (II) Unloading vesa
[    12.374] (II) Failed to load module "vesa" (already loaded, 0)
[    12.374] (II) LoadModule: "modesetting"
[    12.375] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    12.375] (II) Module modesetting: vendor="X.Org Foundation"
[    12.375] 	compiled for 1.13.0, module version = 0.5.0
[    12.376] 	Module class: X.Org Video Driver
[    12.376] 	ABI class: X.Org Video Driver, version 13.0
[    12.376] (II) UnloadModule: "modesetting"
[    12.376] (II) Unloading modesetting
[    12.376] (II) Failed to load module "modesetting" (already loaded, 0)
[    12.376] (II) LoadModule: "fbdev"
[    12.377] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    12.377] (II) Module fbdev: vendor="X.Org Foundation"
[    12.377] 	compiled for 1.13.0, module version = 0.4.3
[    12.377] 	Module class: X.Org Video Driver
[    12.377] 	ABI class: X.Org Video Driver, version 13.0
[    12.377] (II) UnloadModule: "fbdev"
[    12.377] (II) Unloading fbdev
[    12.377] (II) Failed to load module "fbdev" (already loaded, 0)
[    12.377] (II) NOUVEAU driver Date:   Wed Sep 12 13:42:43 2012 +0200
[    12.377] (II) NOUVEAU driver for NVIDIA chipset families :
[    12.377] 	RIVA TNT        (NV04)
[    12.378] 	RIVA TNT2       (NV05)
[    12.378] 	GeForce 256     (NV10)
[    12.378] 	GeForce 2       (NV11, NV15)
[    12.378] 	GeForce 4MX     (NV17, NV18)
[    12.378] 	GeForce 3       (NV20)
[    12.378] 	GeForce 4Ti     (NV25, NV28)
[    12.378] 	GeForce FX      (NV3x)
[    12.379] 	GeForce 6       (NV4x)
[    12.379] 	GeForce 7       (G7x)
[    12.379] 	GeForce 8       (G8x)
[    12.379] 	GeForce GTX 200 (NVA0)
[    12.379] 	GeForce GTX 400 (NVC0)
[    12.379] (II) VESA: driver for VESA chipsets: vesa
[    12.380] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    12.380] (II) FBDEV: driver for framebuffer: fbdev
[    12.380] (++) using VT number 7

[    12.380] (WW) Falling back to old probe method for vesa
[    12.380] (WW) Falling back to old probe method for modesetting
[    12.381] (WW) Falling back to old probe method for fbdev
[    12.381] (II) Loading sub module "fbdevhw"
[    12.381] (II) LoadModule: "fbdevhw"
[    12.382] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    12.382] (II) Module fbdevhw: vendor="X.Org Foundation"
[    12.382] 	compiled for 1.13.0, module version = 0.0.2
[    12.382] 	ABI class: X.Org Video Driver, version 13.0
[    12.421] (II) Loading sub module "dri"
[    12.421] (II) LoadModule: "dri"
[    12.421] (II) Module "dri" already built-in
[    12.421] (II) NOUVEAU(0): Loaded DRI module
[    12.422] (II) [drm] DRM interface version 1.4
[    12.422] (II) [drm] DRM open master succeeded.
[    12.422] (--) NOUVEAU(0): Chipset: "NVIDIA NVa8"
[    12.422] (II) NOUVEAU(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    12.422] (==) NOUVEAU(0): Depth 24, (--) framebuffer bpp 32
[    12.422] (==) NOUVEAU(0): RGB weight 888
[    12.422] (==) NOUVEAU(0): Default visual is TrueColor
[    12.423] (==) NOUVEAU(0): Using HW cursor
[    12.423] (==) NOUVEAU(0): GLX sync to VBlank enabled.
[    12.423] (==) NOUVEAU(0): Page flipping enabled
[    12.423] (==) NOUVEAU(0): Swap limit set to 2 [Max allowed 2]
[    12.528] (II) NOUVEAU(0): Output LVDS-1 has no monitor section
[    12.620] (II) NOUVEAU(0): Output VGA-1 has no monitor section
[    12.623] (II) NOUVEAU(0): Output HDMI-1 has no monitor section
[    12.675] (II) NOUVEAU(0): EDID for output LVDS-1
[    12.675] (II) NOUVEAU(0): Manufacturer: HSD  Model: 3e9  Serial#: 87033
[    12.675] (II) NOUVEAU(0): Year: 2010  Week: 43
[    12.675] (II) NOUVEAU(0): EDID Version: 1.3
[    12.675] (II) NOUVEAU(0): Digital Display Input
[    12.675] (II) NOUVEAU(0): Max Image Size [cm]: horiz.: 22  vert.: 13
[    12.676] (II) NOUVEAU(0): Gamma: 2.20
[    12.676] (II) NOUVEAU(0): No DPMS capabilities specified
[    12.676] (II) NOUVEAU(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    12.676] (II) NOUVEAU(0): First detailed timing is preferred mode
[    12.676] (II) NOUVEAU(0): redX: 0.580 redY: 0.340   greenX: 0.317 greenY: 0.564
[    12.676] (II) NOUVEAU(0): blueX: 0.152 blueY: 0.131   whiteX: 0.310 whiteY: 0.330
[    12.676] (II) NOUVEAU(0): Manufacturer's mask: 0
[    12.676] (II) NOUVEAU(0): Supported detailed timing:
[    12.676] (II) NOUVEAU(0): clock: 45.0 MHz   Image Size:  220 x 129 mm
[    12.676] (II) NOUVEAU(0): h_active: 1024  h_sync: 1077  h_sync_end 1112 h_blank_end 1200 h_border: 0
[    12.676] (II) NOUVEAU(0): v_active: 600  v_sync: 604  v_sync_end 609 v_blanking: 625 v_border: 0
[    12.676] (II) NOUVEAU(0): Supported detailed timing:
[    12.676] (II) NOUVEAU(0): clock: 51.4 MHz   Image Size:  220 x 129 mm
[    12.676] (II) NOUVEAU(0): h_active: 1024  h_sync: 1117  h_sync_end 1152 h_blank_end 1240 h_border: 0
[    12.676] (II) NOUVEAU(0): v_active: 600  v_sync: 617  v_sync_end 622 v_blanking: 638 v_border: 0
[    12.676] (II) NOUVEAU(0):  
[    12.676] (II) NOUVEAU(0):  
[    12.676] (II) NOUVEAU(0): EDID (in hex):
[    12.676] (II) NOUVEAU(0): 	00ffffffffffff002264e903f9530100
[    12.677] (II) NOUVEAU(0): 	2b14010380160d780a86269457519027
[    12.677] (II) NOUVEAU(0): 	214f5400000001010101010101010101
[    12.677] (II) NOUVEAU(0): 	010101010101941100b0405819203523
[    12.677] (II) NOUVEAU(0): 	4500dc8100000019161400d840582620
[    12.677] (II) NOUVEAU(0): 	5d231504dc8100000000000000fe0000
[    12.677] (II) NOUVEAU(0): 	000000000000000000000000000000fe
[    12.677] (II) NOUVEAU(0): 	00000000000000000001000000000060
[    12.677] (II) NOUVEAU(0): Printing probed modes for output LVDS-1
[    12.677] (II) NOUVEAU(0): Modeline "1024x600"x60.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz eP)
[    12.677] (II) NOUVEAU(0): Modeline "1024x600"x65.0   51.42  1024 1117 1152 1240  600 601 606 638 -hsync -vsync (41.5 kHz e)
[    12.677] (II) NOUVEAU(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz e)
[    12.677] (II) NOUVEAU(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz e)
[    12.677] (II) NOUVEAU(0): Modeline "720x400"x59.6   22.25  720 744 808 896  400 403 413 417 -hsync +vsync (24.8 kHz e)
[    12.677] (II) NOUVEAU(0): Modeline "640x400"x60.0   20.00  640 664 720 800  400 403 409 417 -hsync +vsync (25.0 kHz e)
[    12.677] (II) NOUVEAU(0): Modeline "640x350"x59.8   17.50  640 664 720 800  350 353 363 366 -hsync +vsync (21.9 kHz e)
[    12.769] (II) NOUVEAU(0): EDID for output VGA-1
[    12.771] (II) NOUVEAU(0): EDID for output HDMI-1
[    12.771] (II) NOUVEAU(0): Output LVDS-1 connected
[    12.771] (II) NOUVEAU(0): Output VGA-1 disconnected
[    12.771] (II) NOUVEAU(0): Output HDMI-1 disconnected
[    12.771] (II) NOUVEAU(0): Using exact sizes for initial modes
[    12.771] (II) NOUVEAU(0): Output LVDS-1 using initial mode 1024x600
[    12.771] (II) NOUVEAU(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    12.771] (--) NOUVEAU(0): Virtual size is 1024x600 (pitch 0)
[    12.771] (**) NOUVEAU(0):  Driver mode "1024x600": 45.0 MHz (scaled from 0.0 MHz), 37.5 kHz, 60.0 Hz
[    12.771] (II) NOUVEAU(0): Modeline "1024x600"x60.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz eP)
[    12.771] (**) NOUVEAU(0):  Driver mode "1024x600": 51.4 MHz (scaled from 0.0 MHz), 41.5 kHz, 65.0 Hz
[    12.772] (II) NOUVEAU(0): Modeline "1024x600"x65.0   51.42  1024 1117 1152 1240  600 601 606 638 -hsync -vsync (41.5 kHz e)
[    12.772] (**) NOUVEAU(0):  Driver mode "800x600": 38.2 MHz (scaled from 0.0 MHz), 37.4 kHz, 59.9 Hz
[    12.772] (II) NOUVEAU(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz e)
[    12.772] (**) NOUVEAU(0):  Driver mode "640x480": 23.8 MHz (scaled from 0.0 MHz), 29.7 kHz, 59.4 Hz
[    12.772] (II) NOUVEAU(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz e)
[    12.772] (**) NOUVEAU(0):  Driver mode "720x400": 22.2 MHz (scaled from 0.0 MHz), 24.8 kHz, 59.6 Hz
[    12.772] (II) NOUVEAU(0): Modeline "720x400"x59.6   22.25  720 744 808 896  400 403 413 417 -hsync +vsync (24.8 kHz e)
[    12.772] (**) NOUVEAU(0):  Driver mode "640x400": 20.0 MHz (scaled from 0.0 MHz), 25.0 kHz, 60.0 Hz
[    12.772] (II) NOUVEAU(0): Modeline "640x400"x60.0   20.00  640 664 720 800  400 403 409 417 -hsync +vsync (25.0 kHz e)
[    12.772] (**) NOUVEAU(0):  Driver mode "640x350": 17.5 MHz (scaled from 0.0 MHz), 21.9 kHz, 59.8 Hz
[    12.772] (II) NOUVEAU(0): Modeline "640x350"x59.8   17.50  640 664 720 800  350 353 363 366 -hsync +vsync (21.9 kHz e)
[    12.772] (==) NOUVEAU(0): DPI set to (96, 96)
[    12.772] (II) Loading sub module "fb"
[    12.772] (II) LoadModule: "fb"
[    12.773] (II) Loading /usr/lib/xorg/modules/libfb.so
[    12.773] (II) Module fb: vendor="X.Org Foundation"
[    12.773] 	compiled for 1.13.0, module version = 1.0.0
[    12.773] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    12.773] (II) Loading sub module "exa"
[    12.773] (II) LoadModule: "exa"
[    12.774] (II) Loading /usr/lib/xorg/modules/libexa.so
[    12.774] (II) Module exa: vendor="X.Org Foundation"
[    12.774] 	compiled for 1.13.0, module version = 2.6.0
[    12.774] 	ABI class: X.Org Video Driver, version 13.0
[    12.774] (II) Loading sub module "shadowfb"
[    12.774] (II) LoadModule: "shadowfb"
[    12.775] (II) Loading /usr/lib/xorg/modules/libshadowfb.so
[    12.776] (II) Module shadowfb: vendor="X.Org Foundation"
[    12.776] 	compiled for 1.13.0, module version = 1.0.0
[    12.776] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    12.776] (II) UnloadModule: "vesa"
[    12.776] (II) Unloading vesa
[    12.776] (II) UnloadModule: "modesetting"
[    12.776] (II) Unloading modesetting
[    12.776] (II) UnloadModule: "fbdev"
[    12.776] (II) Unloading fbdev
[    12.776] (II) UnloadSubModule: "fbdevhw"
[    12.776] (II) Unloading fbdevhw
[    12.776] (--) Depth 24 pixmap format is 32 bpp
[    12.780] (II) NOUVEAU(0): Opened GPU channel 2
[    12.798] (II) NOUVEAU(0): [DRI2] Setup complete
[    12.798] (II) NOUVEAU(0): [DRI2]   DRI driver: nouveau
[    12.798] (II) NOUVEAU(0): [DRI2]   VDPAU driver: nouveau
[    12.802] (II) EXA(0): Driver allocated offscreen pixmaps
[    12.802] (II) EXA(0): Driver registered support for the following operations:
[    12.802] (II)         Solid
[    12.803] (II)         Copy
[    12.803] (II)         Composite (RENDER acceleration)
[    12.803] (II)         UploadToScreen
[    12.803] (II)         DownloadFromScreen
[    12.803] (==) NOUVEAU(0): Backing store disabled
[    12.803] (==) NOUVEAU(0): Silken mouse enabled
[    12.803] (II) NOUVEAU(0): [XvMC] Associated with Nouveau GeForce 8/9 Textured Video.
[    12.803] (II) NOUVEAU(0): [XvMC] Extension initialized.
[    12.803] (==) NOUVEAU(0): DPMS enabled
[    12.803] (II) NOUVEAU(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    12.804] (--) RandR disabled
[    12.883] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    12.883] (II) AIGLX: enabled GLX_INTEL_swap_event
[    12.883] (II) AIGLX: enabled GLX_ARB_create_context
[    12.883] (II) AIGLX: enabled GLX_ARB_create_context_profile
[    12.883] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[    12.883] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    12.883] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    12.884] (II) AIGLX: Loaded and initialized nouveau
[    12.884] (II) GLX: Initialized DRI2 GL provider for screen 0
[    12.900] (II) NOUVEAU(0): NVEnterVT is called.
[    13.167] (II) NOUVEAU(0): Setting screen physical size to 270 x 158
[    13.167] resize called 1024 600
[    13.201] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    13.210] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    13.210] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    13.210] (II) LoadModule: "evdev"
[    13.211] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    13.211] (II) Module evdev: vendor="X.Org Foundation"
[    13.211] 	compiled for 1.13.0, module version = 2.7.3
[    13.211] 	Module class: X.Org XInput Driver
[    13.211] 	ABI class: X.Org XInput driver, version 18.0
[    13.212] (II) Using input driver 'evdev' for 'Power Button'
[    13.212] (**) Power Button: always reports core events
[    13.212] (**) evdev: Power Button: Device: "/dev/input/event3"
[    13.212] (--) evdev: Power Button: Vendor 0 Product 0x1
[    13.212] (--) evdev: Power Button: Found keys
[    13.212] (II) evdev: Power Button: Configuring as keyboard
[    13.212] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[    13.212] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    13.212] (**) Option "xkb_rules" "evdev"
[    13.212] (**) Option "xkb_model" "pc105"
[    13.212] (**) Option "xkb_layout" "it"
[    13.220] (II) XKB: reuse xkmfile /var/lib/xkb/server-3781FECB9CB8D26EE03343DB2C93394EA704B98F.xkm
[    13.222] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[    13.222] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    13.222] (II) Using input driver 'evdev' for 'Video Bus'
[    13.223] (**) Video Bus: always reports core events
[    13.223] (**) evdev: Video Bus: Device: "/dev/input/event5"
[    13.223] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    13.223] (--) evdev: Video Bus: Found keys
[    13.223] (II) evdev: Video Bus: Configuring as keyboard
[    13.223] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:25/LNXVIDEO:00/input/input5/event5"
[    13.223] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    13.223] (**) Option "xkb_rules" "evdev"
[    13.223] (**) Option "xkb_model" "pc105"
[    13.223] (**) Option "xkb_layout" "it"
[    13.225] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    13.225] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    13.225] (II) Using input driver 'evdev' for 'Power Button'
[    13.225] (**) Power Button: always reports core events
[    13.225] (**) evdev: Power Button: Device: "/dev/input/event2"
[    13.225] (--) evdev: Power Button: Vendor 0 Product 0x1
[    13.225] (--) evdev: Power Button: Found keys
[    13.225] (II) evdev: Power Button: Configuring as keyboard
[    13.225] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input2/event2"
[    13.225] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[    13.225] (**) Option "xkb_rules" "evdev"
[    13.226] (**) Option "xkb_model" "pc105"
[    13.226] (**) Option "xkb_layout" "it"
[    13.227] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    13.227] (II) No input driver specified, ignoring this device.
[    13.227] (II) This device may have been added with another device file.
[    13.228] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[    13.228] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    13.228] (II) Using input driver 'evdev' for 'Sleep Button'
[    13.229] (**) Sleep Button: always reports core events
[    13.229] (**) evdev: Sleep Button: Device: "/dev/input/event1"
[    13.229] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    13.229] (--) evdev: Sleep Button: Found keys
[    13.229] (II) evdev: Sleep Button: Configuring as keyboard
[    13.229] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1/event1"
[    13.229] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 9)
[    13.229] (**) Option "xkb_rules" "evdev"
[    13.229] (**) Option "xkb_model" "pc105"
[    13.229] (**) Option "xkb_layout" "it"
[    13.231] (II) config/udev: Adding input device HDA Intel Mic (/dev/input/event6)
[    13.231] (II) No input driver specified, ignoring this device.
[    13.231] (II) This device may have been added with another device file.
[    13.232] (II) config/udev: Adding input device HDA Intel Headphone (/dev/input/event7)
[    13.232] (II) No input driver specified, ignoring this device.
[    13.232] (II) This device may have been added with another device file.
[    13.232] (II) config/udev: Adding drm device (/dev/dri/card0)
[    13.234] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=9 (/dev/input/event10)
[    13.234] (II) No input driver specified, ignoring this device.
[    13.234] (II) This device may have been added with another device file.
[    13.235] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=8 (/dev/input/event11)
[    13.235] (II) No input driver specified, ignoring this device.
[    13.235] (II) This device may have been added with another device file.
[    13.236] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=7 (/dev/input/event12)
[    13.236] (II) No input driver specified, ignoring this device.
[    13.236] (II) This device may have been added with another device file.
[    13.237] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=3 (/dev/input/event13)
[    13.237] (II) No input driver specified, ignoring this device.
[    13.237] (II) This device may have been added with another device file.
[    13.238] (II) config/udev: Adding input device USB2.0 UVC VGA WebCam (/dev/input/event8)
[    13.238] (**) USB2.0 UVC VGA WebCam: Applying InputClass "evdev keyboard catchall"
[    13.238] (II) Using input driver 'evdev' for 'USB2.0 UVC VGA WebCam'
[    13.238] (**) USB2.0 UVC VGA WebCam: always reports core events
[    13.238] (**) evdev: USB2.0 UVC VGA WebCam: Device: "/dev/input/event8"
[    13.238] (--) evdev: USB2.0 UVC VGA WebCam: Vendor 0x13d3 Product 0x5702
[    13.238] (--) evdev: USB2.0 UVC VGA WebCam: Found keys
[    13.238] (II) evdev: USB2.0 UVC VGA WebCam: Configuring as keyboard
[    13.238] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-6/1-6:1.0/input/input8/event8"
[    13.238] (II) XINPUT: Adding extended input device "USB2.0 UVC VGA WebCam" (type: KEYBOARD, id 10)
[    13.238] (**) Option "xkb_rules" "evdev"
[    13.238] (**) Option "xkb_model" "pc105"
[    13.238] (**) Option "xkb_layout" "it"
[    13.240] (II) config/udev: Adding input device Eee PC WMI hotkeys (/dev/input/event9)
[    13.240] (**) Eee PC WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    13.241] (II) Using input driver 'evdev' for 'Eee PC WMI hotkeys'
[    13.241] (**) Eee PC WMI hotkeys: always reports core events
[    13.241] (**) evdev: Eee PC WMI hotkeys: Device: "/dev/input/event9"
[    13.241] (--) evdev: Eee PC WMI hotkeys: Vendor 0 Product 0
[    13.241] (--) evdev: Eee PC WMI hotkeys: Found keys
[    13.241] (II) evdev: Eee PC WMI hotkeys: Configuring as keyboard
[    13.241] (**) Option "config_info" "udev:/sys/devices/platform/eeepc-wmi/input/input9/event9"
[    13.241] (II) XINPUT: Adding extended input device "Eee PC WMI hotkeys" (type: KEYBOARD, id 11)
[    13.241] (**) Option "xkb_rules" "evdev"
[    13.241] (**) Option "xkb_model" "pc105"
[    13.241] (**) Option "xkb_layout" "it"
[    13.243] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[    13.243] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    13.243] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    13.243] (**) AT Translated Set 2 keyboard: always reports core events
[    13.243] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[    13.243] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    13.243] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    13.243] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    13.244] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[    13.244] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 12)
[    13.244] (**) Option "xkb_rules" "evdev"
[    13.244] (**) Option "xkb_model" "pc105"
[    13.244] (**) Option "xkb_layout" "it"
[    13.246] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/event14)
[    13.246] (**) ETPS/2 Elantech Touchpad: Applying InputClass "evdev touchpad catchall"
[    13.246] (**) ETPS/2 Elantech Touchpad: Applying InputClass "touchpad catchall"
[    13.246] (**) ETPS/2 Elantech Touchpad: Applying InputClass "Default clickpad buttons"
[    13.246] (II) LoadModule: "synaptics"
[    13.246] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    13.247] (II) Module synaptics: vendor="X.Org Foundation"
[    13.247] 	compiled for 1.13.0, module version = 1.6.2
[    13.247] 	Module class: X.Org XInput Driver
[    13.247] 	ABI class: X.Org XInput driver, version 18.0
[    13.247] (II) Using input driver 'synaptics' for 'ETPS/2 Elantech Touchpad'
[    13.247] (**) ETPS/2 Elantech Touchpad: always reports core events
[    13.247] (**) Option "Device" "/dev/input/event14"
[    13.326] (II) synaptics: ETPS/2 Elantech Touchpad: ignoring touch events for semi-multitouch device
[    13.326] (--) synaptics: ETPS/2 Elantech Touchpad: x-axis range 0 - 1216
[    13.326] (--) synaptics: ETPS/2 Elantech Touchpad: y-axis range 0 - 512
[    13.326] (--) synaptics: ETPS/2 Elantech Touchpad: pressure range 0 - 255
[    13.326] (--) synaptics: ETPS/2 Elantech Touchpad: finger width range 0 - 15
[    13.326] (--) synaptics: ETPS/2 Elantech Touchpad: buttons: left right double triple
[    13.326] (--) synaptics: ETPS/2 Elantech Touchpad: Vendor 0x2 Product 0xe
[    13.326] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[    13.326] (**) ETPS/2 Elantech Touchpad: always reports core events
[    13.348] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input14/event14"
[    13.348] (II) XINPUT: Adding extended input device "ETPS/2 Elantech Touchpad" (type: TOUCHPAD, id 13)
[    13.348] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) MinSpeed is now constant deceleration 2.5
[    13.348] (**) synaptics: ETPS/2 Elantech Touchpad: MaxSpeed is now 1.75
[    13.348] (**) synaptics: ETPS/2 Elantech Touchpad: AccelFactor is now 0.152
[    13.348] (**) ETPS/2 Elantech Touchpad: (accel) keeping acceleration scheme 1
[    13.348] (**) ETPS/2 Elantech Touchpad: (accel) acceleration profile 1
[    13.349] (**) ETPS/2 Elantech Touchpad: (accel) acceleration factor: 2.000
[    13.349] (**) ETPS/2 Elantech Touchpad: (accel) acceleration threshold: 4
[    13.349] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[    13.349] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/mouse0)
[    13.350] (**) ETPS/2 Elantech Touchpad: Ignoring device from InputClass "touchpad ignore duplicates"
[    13.370] (II) config/udev: Adding input device HDA Intel Headphone (/dev/input/event7)
[    13.370] (II) No input driver specified, ignoring this device.
[    13.370] (II) This device may have been added with another device file.
[    13.371] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=7 (/dev/input/event12)
[    13.371] (II) No input driver specified, ignoring this device.
[    13.371] (II) This device may have been added with another device file.
[    13.372] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=3 (/dev/input/event13)
[    13.372] (II) No input driver specified, ignoring this device.
[    13.372] (II) This device may have been added with another device file.
[    13.373] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=9 (/dev/input/event10)
[    13.373] (II) No input driver specified, ignoring this device.
[    13.373] (II) This device may have been added with another device file.
[    13.374] (II) config/udev: Adding input device HDA Intel Mic (/dev/input/event6)
[    13.374] (II) No input driver specified, ignoring this device.
[    13.374] (II) This device may have been added with another device file.
[    13.375] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=8 (/dev/input/event11)
[    13.375] (II) No input driver specified, ignoring this device.
[    13.375] (II) This device may have been added with another device file.
[    13.376] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/mouse0)
[    13.376] (**) ETPS/2 Elantech Touchpad: Ignoring device from InputClass "touchpad ignore duplicates"
[    13.376] (II) config/udev: removing device ETPS/2 Elantech Touchpad
[    13.480] (II) UnloadModule: "synaptics"
[    13.481] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/event14)
[    13.481] (**) ETPS/2 Elantech Touchpad: Applying InputClass "evdev touchpad catchall"
[    13.481] (**) ETPS/2 Elantech Touchpad: Applying InputClass "touchpad catchall"
[    13.481] (**) ETPS/2 Elantech Touchpad: Applying InputClass "Default clickpad buttons"
[    13.481] (II) Using input driver 'synaptics' for 'ETPS/2 Elantech Touchpad'
[    13.481] (**) ETPS/2 Elantech Touchpad: always reports core events
[    13.481] (**) Option "Device" "/dev/input/event14"
[    13.572] (II) synaptics: ETPS/2 Elantech Touchpad: ignoring touch events for semi-multitouch device
[    13.572] (--) synaptics: ETPS/2 Elantech Touchpad: x-axis range 0 - 1216
[    13.572] (--) synaptics: ETPS/2 Elantech Touchpad: y-axis range 0 - 512
[    13.572] (--) synaptics: ETPS/2 Elantech Touchpad: pressure range 0 - 255
[    13.572] (--) synaptics: ETPS/2 Elantech Touchpad: finger width range 0 - 15
[    13.572] (--) synaptics: ETPS/2 Elantech Touchpad: buttons: left right double triple
[    13.572] (--) synaptics: ETPS/2 Elantech Touchpad: Vendor 0x2 Product 0xe
[    13.572] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[    13.572] (**) ETPS/2 Elantech Touchpad: always reports core events
[    13.608] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input14/event14"
[    13.608] (II) XINPUT: Adding extended input device "ETPS/2 Elantech Touchpad" (type: TOUCHPAD, id 13)
[    13.608] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) MinSpeed is now constant deceleration 2.5
[    13.608] (**) synaptics: ETPS/2 Elantech Touchpad: MaxSpeed is now 1.75
[    13.608] (**) synaptics: ETPS/2 Elantech Touchpad: AccelFactor is now 0.152
[    13.608] (**) ETPS/2 Elantech Touchpad: (accel) keeping acceleration scheme 1
[    13.608] (**) ETPS/2 Elantech Touchpad: (accel) acceleration profile 1
[    13.609] (**) ETPS/2 Elantech Touchpad: (accel) acceleration factor: 2.000
[    13.609] (**) ETPS/2 Elantech Touchpad: (accel) acceleration threshold: 4
[    13.609] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[    14.623] (II) NOUVEAU(0): EDID vendor "HSD", prod id 1001
[    14.623] (II) NOUVEAU(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[    14.623] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    14.624] (II) NOUVEAU(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz eP)
[    14.624] (II) NOUVEAU(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz e)
[    18.557] (II) NOUVEAU(0): EDID vendor "HSD", prod id 1001
[    18.557] (II) NOUVEAU(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[    18.557] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    18.557] (II) NOUVEAU(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz eP)
[    18.557] (II) NOUVEAU(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz e)
[   752.659] (II) NOUVEAU(0): EDID vendor "HSD", prod id 1001
[   752.660] (II) NOUVEAU(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[   752.660] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[   752.660] (II) NOUVEAU(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz eP)
[   752.660] (II) NOUVEAU(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz e)
[   753.372] resize called 1024 600
[   753.956] (II) NOUVEAU(0): EDID vendor "HSD", prod id 1001
[   753.956] (II) NOUVEAU(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[   753.956] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[   753.956] (II) NOUVEAU(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz eP)
[   753.956] (II) NOUVEAU(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz e)
[   755.508] (II) NOUVEAU(0): EDID vendor "HSD", prod id 1001
[   755.508] (II) NOUVEAU(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[   755.509] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[   755.509] (II) NOUVEAU(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz eP)
[   755.509] (II) NOUVEAU(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz e)
[   755.661] (II) NOUVEAU(0): EDID vendor "HSD", prod id 1001
[   755.661] (II) NOUVEAU(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[   755.661] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[   755.661] (II) NOUVEAU(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz eP)
[   755.661] (II) NOUVEAU(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz e)
[   755.796] (II) NOUVEAU(0): EDID vendor "HSD", prod id 1001
[   755.796] (II) NOUVEAU(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[   755.796] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[   755.796] (II) NOUVEAU(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz eP)
[   755.796] (II) NOUVEAU(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz e)
[   755.931] (II) NOUVEAU(0): EDID vendor "HSD", prod id 1001
[   755.931] (II) NOUVEAU(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[   755.931] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[   755.931] (II) NOUVEAU(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz eP)
[   755.931] (II) NOUVEAU(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz e)
[   756.066] (II) NOUVEAU(0): EDID vendor "HSD", prod id 1001
[   756.066] (II) NOUVEAU(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[   756.066] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[   756.066] (II) NOUVEAU(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz eP)
[   756.066] (II) NOUVEAU(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz e)
[   756.201] (II) NOUVEAU(0): EDID vendor "HSD", prod id 1001
[   756.201] (II) NOUVEAU(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[   756.201] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[   756.201] (II) NOUVEAU(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz eP)
[   756.201] (II) NOUVEAU(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz e)
[   756.419] (II) NOUVEAU(0): EDID vendor "HSD", prod id 1001
[   756.419] (II) NOUVEAU(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[   756.419] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[   756.419] (II) NOUVEAU(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz eP)
[   756.420] (II) NOUVEAU(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz e)
[   756.559] (II) NOUVEAU(0): EDID vendor "HSD", prod id 1001
[   756.559] (II) NOUVEAU(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[   756.559] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[   756.559] (II) NOUVEAU(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz eP)
[   756.559] (II) NOUVEAU(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz e)
[   756.696] (II) NOUVEAU(0): EDID vendor "HSD", prod id 1001
[   756.696] (II) NOUVEAU(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[   756.696] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[   756.696] (II) NOUVEAU(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz eP)
[   756.696] (II) NOUVEAU(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz e)
[   756.831] (II) NOUVEAU(0): EDID vendor "HSD", prod id 1001
[   756.831] (II) NOUVEAU(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[   756.831] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[   756.831] (II) NOUVEAU(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz eP)
[   756.831] (II) NOUVEAU(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz e)
[   757.027] (II) NOUVEAU(0): EDID vendor "HSD", prod id 1001
[   757.027] (II) NOUVEAU(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[   757.027] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[   757.027] (II) NOUVEAU(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz eP)
[   757.027] (II) NOUVEAU(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz e)
[   757.165] (II) NOUVEAU(0): EDID vendor "HSD", prod id 1001
[   757.165] (II) NOUVEAU(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[   757.165] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[   757.165] (II) NOUVEAU(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz eP)
[   757.165] (II) NOUVEAU(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz e)
[   757.305] (II) NOUVEAU(0): EDID vendor "HSD", prod id 1001
[   757.305] (II) NOUVEAU(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[   757.305] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[   757.305] (II) NOUVEAU(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz eP)
[   757.305] (II) NOUVEAU(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz e)
[   757.443] (II) NOUVEAU(0): EDID vendor "HSD", prod id 1001
[   757.443] (II) NOUVEAU(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[   757.443] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[   757.443] (II) NOUVEAU(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz eP)
[   757.443] (II) NOUVEAU(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz e)
[   757.618] (II) NOUVEAU(0): EDID vendor "HSD", prod id 1001
[   757.618] (II) NOUVEAU(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[   757.618] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[   757.618] (II) NOUVEAU(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz eP)
[   757.618] (II) NOUVEAU(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz e)
[   757.758] (II) NOUVEAU(0): EDID vendor "HSD", prod id 1001
[   757.758] (II) NOUVEAU(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[   757.759] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[   757.759] (II) NOUVEAU(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz eP)
[   757.759] (II) NOUVEAU(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz e)
[   757.893] (II) NOUVEAU(0): EDID vendor "HSD", prod id 1001
[   757.893] (II) NOUVEAU(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[   757.894] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[   757.894] (II) NOUVEAU(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz eP)
[   757.894] (II) NOUVEAU(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz e)
[   758.075] (II) NOUVEAU(0): EDID vendor "HSD", prod id 1001
[   758.075] (II) NOUVEAU(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[   758.075] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[   758.076] (II) NOUVEAU(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz eP)
[   758.076] (II) NOUVEAU(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz e)
[   758.222] (II) NOUVEAU(0): EDID vendor "HSD", prod id 1001
[   758.222] (II) NOUVEAU(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[   758.222] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[   758.222] (II) NOUVEAU(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz eP)
[   758.222] (II) NOUVEAU(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz e)
[   758.361] (II) NOUVEAU(0): EDID vendor "HSD", prod id 1001
[   758.361] (II) NOUVEAU(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[   758.361] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[   758.361] (II) NOUVEAU(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz eP)
[   758.361] (II) NOUVEAU(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz e)
[   758.570] (II) NOUVEAU(0): EDID vendor "HSD", prod id 1001
[   758.571] (II) NOUVEAU(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[   758.571] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[   758.571] (II) NOUVEAU(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz eP)
[   758.571] (II) NOUVEAU(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz e)
[   758.710] (II) NOUVEAU(0): EDID vendor "HSD", prod id 1001
[   758.710] (II) NOUVEAU(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[   758.710] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[   758.710] (II) NOUVEAU(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz eP)
[   758.711] (II) NOUVEAU(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz e)
[   758.845] (II) NOUVEAU(0): EDID vendor "HSD", prod id 1001
[   758.846] (II) NOUVEAU(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[   758.846] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[   758.846] (II) NOUVEAU(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz eP)
[   758.846] (II) NOUVEAU(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz e)
[   759.012] (II) NOUVEAU(0): EDID vendor "HSD", prod id 1001
[   759.012] (II) NOUVEAU(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[   759.012] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[   759.012] (II) NOUVEAU(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz eP)
[   759.012] (II) NOUVEAU(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz e)
[   759.161] (II) NOUVEAU(0): EDID vendor "HSD", prod id 1001
[   759.161] (II) NOUVEAU(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[   759.161] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[   759.161] (II) NOUVEAU(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz eP)
[   759.161] (II) NOUVEAU(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz e)
[   759.326] (II) NOUVEAU(0): EDID vendor "HSD", prod id 1001
[   759.326] (II) NOUVEAU(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[   759.326] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[   759.326] (II) NOUVEAU(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz eP)
[   759.326] (II) NOUVEAU(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz e)
[   759.489] (II) NOUVEAU(0): EDID vendor "HSD", prod id 1001
[   759.489] (II) NOUVEAU(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[   759.489] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[   759.489] (II) NOUVEAU(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz eP)
[   759.490] (II) NOUVEAU(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz e)
[   759.649] (II) NOUVEAU(0): EDID vendor "HSD", prod id 1001
[   759.650] (II) NOUVEAU(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[   759.650] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[   759.650] (II) NOUVEAU(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz eP)
[   759.650] (II) NOUVEAU(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz e)
[   759.865] (II) NOUVEAU(0): EDID vendor "HSD", prod id 1001
[   759.865] (II) NOUVEAU(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[   759.865] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[   759.866] (II) NOUVEAU(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz eP)
[   759.866] (II) NOUVEAU(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz e)
[   760.015] (II) NOUVEAU(0): EDID vendor "HSD", prod id 1001
[   760.015] (II) NOUVEAU(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[   760.015] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[   760.015] (II) NOUVEAU(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz eP)
[   760.015] (II) NOUVEAU(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz e)
[   760.160] (II) NOUVEAU(0): EDID vendor "HSD", prod id 1001
[   760.160] (II) NOUVEAU(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[   760.160] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[   760.160] (II) NOUVEAU(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz eP)
[   760.160] (II) NOUVEAU(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz e)
[   760.298] (II) NOUVEAU(0): EDID vendor "HSD", prod id 1001
[   760.298] (II) NOUVEAU(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[   760.298] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[   760.298] (II) NOUVEAU(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz eP)
[   760.298] (II) NOUVEAU(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz e)
[   760.450] (II) NOUVEAU(0): EDID vendor "HSD", prod id 1001
[   760.450] (II) NOUVEAU(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[   760.450] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[   760.450] (II) NOUVEAU(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz eP)
[   760.451] (II) NOUVEAU(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz e)
[   760.589] (II) NOUVEAU(0): EDID vendor "HSD", prod id 1001
[   760.589] (II) NOUVEAU(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[   760.589] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[   760.589] (II) NOUVEAU(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz eP)
[   760.589] (II) NOUVEAU(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz e)
[   760.749] (II) NOUVEAU(0): EDID vendor "HSD", prod id 1001
[   760.750] (II) NOUVEAU(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[   760.750] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[   760.750] (II) NOUVEAU(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz eP)
[   760.750] (II) NOUVEAU(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz e)
[   760.892] (II) NOUVEAU(0): EDID vendor "HSD", prod id 1001
[   760.892] (II) NOUVEAU(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[   760.893] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[   760.893] (II) NOUVEAU(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz eP)
[   760.893] (II) NOUVEAU(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz e)
[   761.059] (II) NOUVEAU(0): EDID vendor "HSD", prod id 1001
[   761.059] (II) NOUVEAU(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[   761.059] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[   761.059] (II) NOUVEAU(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz eP)
[   761.059] (II) NOUVEAU(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz e)
[   761.202] (II) NOUVEAU(0): EDID vendor "HSD", prod id 1001
[   761.202] (II) NOUVEAU(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[   761.202] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[   761.203] (II) NOUVEAU(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz eP)
[   761.203] (II) NOUVEAU(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz e)
[   761.339] (II) NOUVEAU(0): EDID vendor "HSD", prod id 1001
[   761.339] (II) NOUVEAU(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[   761.339] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[   761.339] (II) NOUVEAU(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz eP)
[   761.339] (II) NOUVEAU(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz e)
[   761.476] (II) NOUVEAU(0): EDID vendor "HSD", prod id 1001
[   761.476] (II) NOUVEAU(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[   761.476] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[   761.476] (II) NOUVEAU(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz eP)
[   761.476] (II) NOUVEAU(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz e)
[   761.662] (II) NOUVEAU(0): EDID vendor "HSD", prod id 1001
[   761.662] (II) NOUVEAU(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[   761.662] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[   761.662] (II) NOUVEAU(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz eP)
[   761.662] (II) NOUVEAU(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz e)
[   761.811] (II) NOUVEAU(0): EDID vendor "HSD", prod id 1001
[   761.811] (II) NOUVEAU(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[   761.811] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[   761.811] (II) NOUVEAU(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz eP)
[   761.811] (II) NOUVEAU(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz e)
[   761.954] (II) NOUVEAU(0): EDID vendor "HSD", prod id 1001
[   761.954] (II) NOUVEAU(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[   761.954] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[   761.954] (II) NOUVEAU(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz eP)
[   761.954] (II) NOUVEAU(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz e)
[   762.098] (II) NOUVEAU(0): EDID vendor "HSD", prod id 1001
[   762.098] (II) NOUVEAU(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[   762.098] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[   762.098] (II) NOUVEAU(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz eP)
[   762.099] (II) NOUVEAU(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz e)
[   762.254] (II) NOUVEAU(0): EDID vendor "HSD", prod id 1001
[   762.254] (II) NOUVEAU(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[   762.254] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[   762.254] (II) NOUVEAU(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz eP)
[   762.254] (II) NOUVEAU(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz e)
[   762.419] (II) NOUVEAU(0): EDID vendor "HSD", prod id 1001
[   762.419] (II) NOUVEAU(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[   762.419] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[   762.419] (II) NOUVEAU(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz eP)
[   762.419] (II) NOUVEAU(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz e)
[   762.560] (II) NOUVEAU(0): EDID vendor "HSD", prod id 1001
[   762.560] (II) NOUVEAU(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[   762.560] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[   762.561] (II) NOUVEAU(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz eP)
[   762.561] (II) NOUVEAU(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz e)
[   763.419] (II) NOUVEAU(0): EDID vendor "HSD", prod id 1001
[   763.419] (II) NOUVEAU(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[   763.419] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[   763.419] (II) NOUVEAU(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz eP)
[   763.419] (II) NOUVEAU(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz e)
[   764.392] (II) NOUVEAU(0): EDID vendor "HSD", prod id 1001
[   764.392] (II) NOUVEAU(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[   764.392] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[   764.392] (II) NOUVEAU(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz eP)
[   764.392] (II) NOUVEAU(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz e)
[   764.633] (II) NOUVEAU(0): EDID vendor "HSD", prod id 1001
[   764.633] (II) NOUVEAU(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[   764.633] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[   764.633] (II) NOUVEAU(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz eP)
[   764.633] (II) NOUVEAU(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz e)
[   764.780] (II) NOUVEAU(0): EDID vendor "HSD", prod id 1001
[   764.780] (II) NOUVEAU(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[   764.780] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[   764.780] (II) NOUVEAU(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz eP)
[   764.780] (II) NOUVEAU(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz e)
[   764.929] (II) NOUVEAU(0): EDID vendor "HSD", prod id 1001
[   764.929] (II) NOUVEAU(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[   764.929] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[   764.929] (II) NOUVEAU(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz eP)
[   764.929] (II) NOUVEAU(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz e)
[   765.096] (II) NOUVEAU(0): EDID vendor "HSD", prod id 1001
[   765.096] (II) NOUVEAU(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[   765.096] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[   765.096] (II) NOUVEAU(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz eP)
[   765.096] (II) NOUVEAU(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz e)
[   766.127] (II) XKB: reuse xkmfile /var/lib/xkb/server-578FE579C1DA334EA8BF25F338A218BFA489E7F5.xkm
[   775.422] (II) NOUVEAU(0): EDID vendor "HSD", prod id 1001
[   775.422] (II) NOUVEAU(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[   775.422] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[   775.422] (II) NOUVEAU(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz eP)
[   775.422] (II) NOUVEAU(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz e)
[  1975.485] (II) NOUVEAU(0): EDID vendor "HSD", prod id 1001
[  1975.485] (II) NOUVEAU(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[  1975.485] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[  1975.485] (II) NOUVEAU(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz eP)
[  1975.485] (II) NOUVEAU(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz e)
[  4154.654] (II) NOUVEAU(0): EDID vendor "HSD", prod id 1001
[  4154.654] (II) NOUVEAU(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
[  4154.654] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[  4154.655] (II) NOUVEAU(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz eP)
[  4154.655] (II) NOUVEAU(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz e)
```

Now I cannot install nvidia-current package, I tried to install xorg-video-abi-11 package but I went into the problem described. 
Up to now I don't think there's something in your procedure, there's some problems in Ubuntu 12.04 (I read some bugs on that but I am not an expert) about nvidia-current package dependencies.

Thanks a lot, I will contact you via pm.

---

### Post by mtron on 2013-02-22
yes, this seems to be a problem with ubuntu base packages. Did you try the latest nvidia drivers from the [x-swat]("https://launchpad.net/~ubuntu-x-swat/+archive/x-updates") ppa?

---

### Post by Lead Expression on 2013-02-24
Just to update, I am trying to resolve the issue on nvidia-current, I have installed nvidia drivers 310.xx from nvidia website successfully, now I have to resolve the dependencies issue.
```
~$ sudo apt-get install eee1015pn-acpitools build-essential debhelper module-assistant lm-sensors
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 eee1015pn-acpitools : Depends: nvidia-current but it is not going to be installed or
                                nvidia-glx but it is not installable
E: Unable to correct problems, you have held broken packages.
```

I will come back as I achieve the resolution. ):P

---

### Post by mtron on 2013-02-25
[here]("http://ubuntuone.com/7KE2j4DDkNEnAdfd6Kxbgl") is a package that does not depend on the nvidia binary blob. 

First install the dependencies:
```
sudo apt-get install mesa-utils openbox acpi-call-tools bbswitch-dkms yad libnotify-bin
```

now install the alternate Version of the acpitools package
```
sudo dpkg -i eee1015pn-acpitools_0.8.3-2~precise1_all.deb
```

Note: to remove a package dependency edit the 'control' file under the debian directory of the source package and rebuild it ;)

---

### Post by Lead Expression on 2013-02-25
Dear mtron,
Now I am with Lynx :(
I successfully installed the package but the result is the same as presented previously.
The system is frozen in "* Starting LightDM Display Manager" and that's all.
Tomorrow I will post the content of /var/log/Xorg.0.log but consider that the last update is just before the installation of the package. 
If there is some other log that can help tell me and I will try to paste it here.

Thank you for your help

---

### Post by mtron on 2013-02-26
> **doc.maizo said:**
> Hi mtron!
I have made a fresh install of 12.04 on the 1015pn following your instructions; everithing's ok, but I don't have HDMI audio out; in optimus mode I can send video out through HDMI but audio doesn't work.

Sorry for the late reply but i finally found a fix for this: You need to run 
```
ck-launch-session &
``` 

on the Second X-Server (the '&' puts it to the background) Now the normal pulseaudio Volume Control tools can be used to change the output device to nvidia hdmi.

I will fix this in the next version of the acpitools package. Thanks for reporting this bug!

Cheers!

---

### Post by doc.maizo on 2013-02-27
Great! I'll try as soon as I can, thanks!

I've been having another little, but annoying, problem: sometimes (I can't say if there is some particular configuration that causes it) after the login the video output goes by default to vga and I have to press Fn+F8 to switch to lcd.
Do you know how to fix it?

Thx!

---

### Post by Lead Expression on 2013-03-08
Trying to resolve my problem, I'm seeing that there are a few logs updated. One of them is lightdm.log

```
[+0.00s] DEBUG: Logging to /var/log/lightdm/lightdm.log
[+0.00s] DEBUG: Starting Light Display Manager 1.2.3, UID=0 PID=1585
[+0.00s] DEBUG: Loaded configuration from /etc/lightdm/lightdm.conf
[+0.00s] DEBUG: Using D-Bus name org.freedesktop.DisplayManager
[+0.00s] DEBUG: Registered seat module xlocal
[+0.00s] DEBUG: Registered seat module xremote
[+0.00s] DEBUG: Adding default seat
[+0.00s] DEBUG: Starting seat
[+0.00s] DEBUG: Starting new display for greeter
[+0.00s] DEBUG: Starting local X display
[+0.01s] DEBUG: Using VT 7
[+0.01s] DEBUG: Activating VT 7
[+0.01s] DEBUG: Logging to /var/log/lightdm/x-0.log
[+0.01s] DEBUG: Can't launch X server X, not found in path
[+0.01s] DEBUG: X server stopped
[+0.01s] DEBUG: Releasing VT 7
[+0.01s] DEBUG: Display server stopped
[+0.01s] DEBUG: Stopping display
[+0.01s] DEBUG: Display stopped
[+0.01s] DEBUG: Stopping X local seat, failed to start a display
[+0.01s] DEBUG: Stopping seat
[+0.01s] DEBUG: Seat stopped
[+0.01s] DEBUG: Stopping Plymouth, no displays replace it
[+0.79s] DEBUG: Acquired bus name org.freedesktop.DisplayManager
```

The line
[+0.01s] DEBUG: Can't launch X server X, not found in path
really frightned me. anyone know what does it means?

Thanks a lot

---

### Post by Lead Expression on 2013-03-10
I'm trying to fix using various advice on the net but the cloud is always darker. I tried bumblebee, the result is different but even bad.  If I type $ grep bumblebeed /var/log/syslog
```
$ grep bumblebeed /var/log/syslog
Mar 10 18:41:02 nik-1015PN bumblebeed[1227]: No integrated video card found, quitting.
Mar 10 18:41:02 nik-1015PN bumblebeed[1237]: No integrated video card found, quitting.
Mar 10 18:41:02 nik-1015PN bumblebeed[1247]: No integrated video card found, quitting.
Mar 10 18:41:02 nik-1015PN bumblebeed[1259]: No integrated video card found, quitting.
Mar 10 18:41:02 nik-1015PN bumblebeed[1297]: No integrated video card found, quitting.
Mar 10 18:41:02 nik-1015PN bumblebeed[1344]: No integrated video card found, quitting.
Mar 10 18:41:02 nik-1015PN bumblebeed[1353]: No integrated video card found, quitting.
Mar 10 18:41:09 nik-1015PN bumblebeed[1860]: No integrated video card found, quitting.
Mar 10 18:41:09 nik-1015PN bumblebeed[1868]: No integrated video card found, quitting.
Mar 10 18:41:09 nik-1015PN bumblebeed[1876]: No integrated video card found, quitting.
Mar 10 18:41:09 nik-1015PN bumblebeed[1887]: No integrated video card found, quitting.
Mar 10 18:41:09 nik-1015PN bumblebeed[1904]: No integrated video card found, quitting.
Mar 10 18:41:09 nik-1015PN bumblebeed[1919]: No integrated video card found, quitting.
Mar 10 18:41:10 nik-1015PN bumblebeed[1933]: No integrated video card found, quitting.
Mar 10 18:41:10 nik-1015PN bumblebeed[1941]: No integrated video card found, quitting.
Mar 10 18:41:10 nik-1015PN bumblebeed[1949]: No integrated video card found, quitting.
Mar 10 18:41:10 nik-1015PN bumblebeed[1957]: No integrated video card found, quitting.
Mar 10 18:41:10 nik-1015PN bumblebeed[1965]: No integrated video card found, quitting.


```
and
```
nik@nik-1015PN:~$ lspci |grep VGA
04:00.0 VGA compatible controller: NVIDIA Corporation GT218 [ION] (rev a2)
nik@nik-1015PN:~$ lspci |grep Intel
00:00.0 Host bridge: Intel Corporation Atom Processor D4xx/D5xx/N4xx/N5xx DMI Bridge (rev 02)
00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation NM10/ICH7 Family SATA Controller [AHCI mode] (rev 02)
```

Does this mean that the Intel card is not recognized?

---

### Post by mtron on 2013-03-11
yes, this means that you are in the wrong video mode. use "sudo display-settings status" to see the gpu mode

You're currently in Mode 2 (nvidia only). bumblebee only works in mode 3 (optimus mode). Please read the general documentation at [http://mtron.co.nr/projects/eee1015pn](http://mtron.co.nr/projects/eee1015pn)

Since your system seems to be totally messed up i suggest you backup your data and do a complete reinstall. Follow the linked setup instructions (use 12.04 LTS for best results) and you will get a fully working system.

---

### Post by Lead Expression on 2013-03-11
I made this trial with a freshly installed Ubuntu 12.10. 

Actually I tried the procedure 4 times (all fresh installations, 3 with 12.04 and 1 with 12.10) but the result is always the same. At least for the 12.04 I have the problem of the dependencies on nvidia-current.
In any case ok, as the system now is using the nvidia only and it is very hot and power consuming, I will try a further time. It would have been more efficient to understand where the problem is before retrying following the same procedure without modification but unfortunately I really cannot figure out :(

---

### Post by mtron on 2013-03-12
ok, so we will go another route. Please to the following

- start with a complete fresh install of ubuntu 12.04 LTS
- update your system (don't forget to reboot in the Latest installed kernel)
- add the 1015pn and the x-swat ppa and install the "eee1015pn-acpitools" package and reboot

if it does not work after this i suspect a hardware problem on your Netbook. It works on numerous other 1015PN's so yours seems to be "special". If you are thus far please send me ssh or teamviewer account data via PM and i will poke around a bit to find out whats going wrong on your system.

---

### Post by Lead Expression on 2013-03-16
The last time I tried... It does work!
I have followed the same steps but no error in nvidia-current and nvidia-settings dependencies I have always had in 12.04. 
The other difference is that I have installed the eee1015tool only without build-essential, debhelper, module-assistant and lm-sensors packets.

I don't know why... but now is working, this is the important thing.
Thank you very very much for your help and your time, mtron!

---

### Post by mtron on 2013-03-20
> I don't know why... but now is working

Great! Though it would have been interresting to know what happened on your system...

I have also pushed a new version (eee1015pn-acpitools 0.9.0) to the [ppa]("https://launchpad.net/~mtron/+archive/eee1015pn"). It should get installed automatically once you run a system upgrade. To trigger such an upgrade now use
```
sudo apt-get update && sudo apt-get dist-upgrade
```

**Changelog:**

  * added Ubuntu 13.04 support
  * updated fixglx and regenerate-glx functions for ubuntus new nvidia binary driver naming schema like nvidia-<first 3 digits of driver version> 
  * updated search path for nvidia kernel module for ubuntus new nvidia binary driver naming schema
  * packaging: fixed postinstall script to find all installed nvidia drivers

**Documentation /How to use: **
[http://mtron.co.nr/projects/eee1015pn](http://mtron.co.nr/projects/eee1015pn)

**Distribution Upgrades:**
If you plan to upgrade from quantal to raring make sure that you have min. 0.9.0 installed. After the upgrade completed run
```
sudo display-settings regenerate-glx 
```
and reboot.

---

### Post by gumbomumbo on 2013-03-25
I just installed ubuntu and when I followed your "how to" I ran into problems. Your stuff has always worked for me, but it seems like some update killed it.

When rebooting after running "sudo sensors-detect". I now get

Starting Configure Display Device for EeePC 1015PN [fail]. How do I fix this?

Thanks a lot for your help mtron.

---

### Post by talksloudsaysnothing on 2013-03-25
I am having similar trouble like Lead Expression up there, I've just reinstalled 12.04 and as soon as I want to install your acpitools, it tells me that there is a problem with nvidia-current. Of note, it worked just a few days ago, back then I had a working 12.04 installed from last year with your tools working nicely. Either I did something to mess my installation up or it got messed up by something, either way I had to reinstall. 12.10 gave me random freezes so I tried to go back to 12.04 but keep getting the "nvidia-current is not going to be installed..." error (see previous page of this thread) when I try to install your stuff.

I tried your suggestions from above, tried to install the nvidia driver from x-swat and then install the acpitools. Upon reboot it looked fine at first, the fan got much quieter so it seemed to work, but weird enough the x-server wouldn't start anymore. Instead of seeing the login manager, I was kicked to commandline login. When I tried the start the xserver manually, I got this error:

/etc/X11/xinit/xserverrc: 3: exec: /usr/bin/X: not found
xinit: giving up
xinit: unable to connect to Xserver: no such file or directory

I rebooted into recovery mode as I thought maybe repairing broken packages might help, but all it did was throw out all the Xserver packages, so I had to reinstall again. Now I am on a fresh system, updated all my packages, still can't install your tools and don't know what to do.

---

### Post by mtron on 2013-03-25
can you provide me with ssh or teamviewer access to the netbook please? i'm really interested to see whats going on there since i cant reproduce this here. i'm too on 12.04 with nvidia driver 304.84 and everything works as it should.

---

### Post by talksloudsaysnothing on 2013-03-25
Did you actually try and reinstall it completely? Because everything did work for me a couple days back when I was still using my previous installation. It is installing it now that for some reason has everything messed up.

---

### Post by mtron on 2013-03-26
> **talksloudsaysnothing said:**
> Did you actually try and reinstall it completely?

Yes. Here is what i did:

- default install from usb-stick. no updates during install

- rebooted

edited /etc/apt/sources.list (not via gui!)

```
# See http://help.ubuntu.com/community/UpgradeNotes

## Ubuntu 12.04.1 LTS main archive
deb http://archive.ubuntu.com/ubuntu precise main restricted universe multiverse

## Major bug fix and security updates 
deb http://archive.ubuntu.com/ubuntu precise-updates main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu precise-security main restricted universe multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu precise-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
```

- only syc online repositories, don't actually install updates
```
sudo apt-get update
```

- install the ee1015pn-acpitools package
```
sudo apt-get install eee1015pn-acpitools
```

and i get:

```
The following NEW packages will be installed:
  acpi acpi-call-dkms acpi-call-source bbswitch-dkms build-essential debhelper
  dh-apparmor dkms dpkg-dev eee1015pn-acpitools fakeroot g++ g++-4.6 gettext
  html2text intltool-debian libalgorithm-diff-perl libalgorithm-diff-xs-perl
  libalgorithm-merge-perl libdpkg-perl libgettextpo0 libgif4 libglade2-0
  libid3tag0 libimlib2 libmail-sendmail-perl libobrender27 libobt0
  libstdc++6-4.6-dev libsys-hostname-long-perl libtimedate-perl libunistring0
  mesa-utils module-assistant nvidia-current nvidia-settings obconf openbox
  openbox-themes po-debconf screen-resolution-extra yad
```

the 'nvidia-current' driver comes in this case from the ubuntu "precise-updates" repository and is the nvidia binary blob version 295.40

install works fine:

```
Setting up nvidia-current (295.40-0ubuntu1.3) ...
update-alternatives: using /usr/lib/nvidia-current/ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-alternatives: warning: skip creation of /usr/lib32/libOpenCL.so because associated file /usr/lib32/nvidia-current/libOpenCL.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/vdpau/libvdpau_nvidia.so.1 because associated file /usr/lib32/nvidia-current/vdpau/libvdpau_nvidia.so.1 (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libvdpau_nvidia.so because associated file /usr/lib32/nvidia-current/vdpau/libvdpau_nvidia.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: using /usr/lib/nvidia-current/alt_ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-initramfs: deferring update (trigger activated)
INFO:Enable nvidia-current
DEBUG:Parsing /usr/share/nvidia-common/quirks/dell_latitude
DEBUG:Parsing /usr/share/nvidia-common/quirks/put_your_quirks_here
DEBUG:Parsing /usr/share/nvidia-common/quirks/lenovo_thinkpad
DEBUG:Processing quirk Latitude E6530
DEBUG:Failure to match ASUSTeK Computer INC. with Dell Inc.
DEBUG:Quirk doesn't match
DEBUG:Processing quirk ThinkPad T420s
DEBUG:Failure to match ASUSTeK Computer INC. with LENOVO
DEBUG:Quirk doesn't match
Loading new nvidia-current-295.40 DKMS files...
First Installation: checking all kernels...
Building only for 3.2.0-32-generic-pae
Building for architecture i686
Building initial module for 3.2.0-32-generic-pae
Done.

bbswitch:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-32-generic-pae/updates/dkms/

depmod....

DKMS: install completed.
```

- also the glx libs are properly created and everything works here.
```
sudo display-settings fix
...
INFO: mesa glx MD5 sums are
      4f5109cec4bee6e1edfe4cc03c3f3d8c
      4f5109cec4bee6e1edfe4cc03c3f3d8c
INFO: mesa checksums OK
INFO: nvidia glx MD5 sums are
      ab5d73191f397fbe120eb63001d5623c
      ab5d73191f397fbe120eb63001d5623c
INFO: nvidia checksums OK
...
```


so i cant reproduce this at this stage. i will try to actually install all system updates after initial install but i can't see a reason why it should break then. I need very percise steps to reproduce this bug please.

**EDIT:** next try. this time install all upgrades, updated kernel and nvidia drivers via x-swat ppa:
- basic install usb stick
- sources.list update as above
- full system update
```
sudo apt-get update && sudo apt-get dist-upgrade
```
- install latest 3.5 kernel from quantal for precise
```
sudo apt-get install linux-image-generic-lts-quantal linux-headers-generic-lts-quantal
```
- add the x-swat and eee1015pn ppa
```
sudo add-apt-repository ppa:mtron/eee1015pn 
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update && sudo apt-get dist-upgrade
```
- reboot into 3.5 kernel
- install acpitools and nvidia driver
```
sudo apt-get install eee1015pn-acpitools
```

now it's kernel 3.5 with nvidia binary blob 304.84 and again everything works here. No idea what's wrong in your case.

---

### Post by talksloudsaysnothing on 2013-03-26
Ah, thats much different from what I did. I basically always updated everything before trying to install the acpitools. Will try this again when I am back at my computer later. Thanks! I'll report back if it worked.

---

### Post by ebilpanda on 2013-03-26
hi I have a problem:
I have installed mint(mate) and everything worked, installed bumblebee and so on

but after I installed your script (eee1015pn-acpitools) gdm won't start and if I start display-settings in the console there comes:
"ERROR: Could not find nvidia.ko kernel module. Adjust the path manually in the Variables section of the display-settings script"
if i remove your script my netbook the gdm start...but so I get an error :)

have I to write in the file like the message says (but which file exactly -> you conf file says nothing about the nvidia.ko file or so) or is Linux Mint 14.1 Mate simply not supportet? :/



oh and btw: with 12.10 and so i have no problems with your script - but i wanted to use linux mint so i would like to fix this error :)


so far ~ panda

---

### Post by talksloudsaysnothing on 2013-03-26
> **mtron said:**
> Yes. Here is what i did:

- default install from usb-stick. no updates during install

- rebooted

edited /etc/apt/sources.list (not via gui!)

```
# See http://help.ubuntu.com/community/UpgradeNotes

## Ubuntu 12.04.1 LTS main archive
deb http://archive.ubuntu.com/ubuntu precise main restricted universe multiverse

## Major bug fix and security updates 
deb http://archive.ubuntu.com/ubuntu precise-updates main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu precise-security main restricted universe multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu precise-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
```

- only syc online repositories, don't actually install updates
```
sudo apt-get update
```

- install the ee1015pn-acpitools package
```
sudo apt-get install eee1015pn-acpitools
```

and i get:

```
The following NEW packages will be installed:
  acpi acpi-call-dkms acpi-call-source bbswitch-dkms build-essential debhelper
  dh-apparmor dkms dpkg-dev eee1015pn-acpitools fakeroot g++ g++-4.6 gettext
  html2text intltool-debian libalgorithm-diff-perl libalgorithm-diff-xs-perl
  libalgorithm-merge-perl libdpkg-perl libgettextpo0 libgif4 libglade2-0
  libid3tag0 libimlib2 libmail-sendmail-perl libobrender27 libobt0
  libstdc++6-4.6-dev libsys-hostname-long-perl libtimedate-perl libunistring0
  mesa-utils module-assistant nvidia-current nvidia-settings obconf openbox
  openbox-themes po-debconf screen-resolution-extra yad
```

the 'nvidia-current' driver comes in this case from the ubuntu "precise-updates" repository and is the nvidia binary blob version 295.40

install works fine:

```
Setting up nvidia-current (295.40-0ubuntu1.3) ...
update-alternatives: using /usr/lib/nvidia-current/ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-alternatives: warning: skip creation of /usr/lib32/libOpenCL.so because associated file /usr/lib32/nvidia-current/libOpenCL.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/vdpau/libvdpau_nvidia.so.1 because associated file /usr/lib32/nvidia-current/vdpau/libvdpau_nvidia.so.1 (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libvdpau_nvidia.so because associated file /usr/lib32/nvidia-current/vdpau/libvdpau_nvidia.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: using /usr/lib/nvidia-current/alt_ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-initramfs: deferring update (trigger activated)
INFO:Enable nvidia-current
DEBUG:Parsing /usr/share/nvidia-common/quirks/dell_latitude
DEBUG:Parsing /usr/share/nvidia-common/quirks/put_your_quirks_here
DEBUG:Parsing /usr/share/nvidia-common/quirks/lenovo_thinkpad
DEBUG:Processing quirk Latitude E6530
DEBUG:Failure to match ASUSTeK Computer INC. with Dell Inc.
DEBUG:Quirk doesn't match
DEBUG:Processing quirk ThinkPad T420s
DEBUG:Failure to match ASUSTeK Computer INC. with LENOVO
DEBUG:Quirk doesn't match
Loading new nvidia-current-295.40 DKMS files...
First Installation: checking all kernels...
Building only for 3.2.0-32-generic-pae
Building for architecture i686
Building initial module for 3.2.0-32-generic-pae
Done.

bbswitch:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-32-generic-pae/updates/dkms/

depmod....

DKMS: install completed.
```

- also the glx libs are properly created and everything works here.
```
sudo display-settings fix
...
INFO: mesa glx MD5 sums are
      4f5109cec4bee6e1edfe4cc03c3f3d8c
      4f5109cec4bee6e1edfe4cc03c3f3d8c
INFO: mesa checksums OK
INFO: nvidia glx MD5 sums are
      ab5d73191f397fbe120eb63001d5623c
      ab5d73191f397fbe120eb63001d5623c
INFO: nvidia checksums OK
...
```


so i cant reproduce this at this stage. i will try to actually install all system updates after initial install but i can't see a reason why it should break then. I need very percise steps to reproduce this bug please.

**EDIT:** next try. this time install all upgrades, updated kernel and nvidia drivers via x-swat ppa:
- basic install usb stick
- sources.list update as above
- full system update
```
sudo apt-get update && sudo apt-get dist-upgrade
```
- install latest 3.5 kernel from quantal for precise
```
sudo apt-get install linux-image-generic-lts-quantal linux-headers-generic-lts-quantal
```
- add the x-swat and eee1015pn ppa
```
sudo add-apt-repository ppa:mtron/eee1015pn 
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update && sudo apt-get dist-upgrade
```
- reboot into 3.5 kernel
- install acpitools and nvidia driver
```
sudo apt-get install eee1015pn-acpitools
```

now it's kernel 3.5 with nvidia binary blob 304.84 and again everything works here. No idea what's wrong in your case.


So tonight I tried a lot of stuff to get it working again. Long story short, none of your suggestions worked. Either I again could not install nvidia-current (when using your first suggestion) or I couldn't get the X server to load (with your second suggestion), so same as before essentially. 
Then I noticed from your sources.list that it says "Ubuntu 12.04.1 LTS". The image I downloaded a couple days ago is 12.04.2 LTS. This one already comes with the 3.5 kernel, so in your second suggestion I didn't have a choice of installing it, it was already there. So I reinstalled everything once again using the installation for 12.04.1, and almost everything works as before, the only exception being that I have to use Intel mode all the time to have a quiet computer (low fan noise). When I switch to optimus mode the temperature shown by Jupiter increases by 10°C and the fan starts working more, on my old installation for some reason optimus mode was quiet as well. But I can live with that.
So now I use kernel 3.2.0.39, could it be that the kernel 3.5 messes up some stuff which lead to all the errors? I didn't try installing kernel 3.5 manually now, as this is my only computer and I am pretty sick of testing and reinstalling, at the moment I am just relieved it all works again.

---

### Post by muskelbiber on 2013-03-26
> **ebilpanda said:**
> hi I have a problem:

but after I installed your script (eee1015pn-acpitools) gdm won't start and if I start display-settings in the console there comes:
"ERROR: Could not find nvidia.ko kernel module. Adjust the path manually in the Variables section of the display-settings script"
if i remove your script my netbook the gdm start...but so I get an error :)



Same problem with my mint 14, but just since last week...

---

### Post by Mizio on 2013-03-27
Hi all, I come and sorry my bad english
My name is Maurizio and I also have a beautiful 1015PN
In next week i last week I installed ubuntu 12.04.02 amd64 with new Nvidia driver 310.32 (from PPA xorg-edger) and everything works fine.

Then I installed the acpitools and I encountered the following problem:
- If I start 
[HTML]sudo display-settings status[/HTML]
I have not answer
- Also on the startup screen (user logon) if I move the mouse the screen goes black and (it is my impression) restarts the xserver

Can you help me to solve the problem 
Thanks to all
Maurizio

---

### Post by mtron on 2013-03-27
> **talksloudsaysnothing said:**
> 
Then I noticed from your sources.list that it says "Ubuntu 12.04.1 LTS". The image I downloaded a couple days ago is 12.04.2 LTS. This one already comes with the 3.5 kernel, so in your second suggestion I didn't have a choice of installing it, it was already there.

As you see i tested both and both work for me. 

> **talksloudsaysnothing said:**
> So now I use kernel 3.2.0.39, could it be that the kernel 3.5 messes up some stuff which lead to all the errors? 

Probably. Let's see if all kernel modules are build for all kernels. Post the outout of
```
dkms status
```

> **muskelbiber said:**
> Same problem with my mint 14, but just since last week...

thanks for the bugreport. i have pushed a fix to the bzr repository. Could you please test it? (replace /usr/bin/display-settings with [this revision 120]("http://bazaar.launchpad.net/~mtron/+junk/eee1015pn/download/head:/displaysettings-20111031094943-fe0sfodfaz9g8u6d-24/display-settings"). then mark it executeable with chmod +x /usr/bin/display-settings )

> **ebilpanda said:**
> 
but after I installed your script (eee1015pn-acpitools) gdm won't start and if I start display-settings in the console there comes:
"ERROR: Could not find nvidia.ko kernel module. Adjust the path manually in the Variables section of the display-settings script"

hello! this is the same bug as muskelbiber refers to. Fix should be in bzr.

> **ebilpanda said:**
> is Linux Mint 14.1 Mate simply not supportet? :/

No, Linux Mint support was written by a contributor because i don't use it. There should have been a warning in the debug output that your distro is not supported and that the ubuntu fallback will be used. I have enabled mint 14 support now but i don't want to include mint 14 support without ever testing it. Could you please download the latest version of the /usr/bin/display-settings script from bzr (see the answer to muskelbiber question above) and test it?

---

### Post by ebilpanda on 2013-03-27
> **mtron said:**
> 
No, Linux Mint support was written by a contributor because i don't use it. There should have been a warning in the debug output that your distro is not supported and that the ubuntu fallback will be used. I have enabled mint 14 support now but i don't want to include mint 14 support without ever testing it. Could you please download the latest version of the /usr/bin/display-settings script from bzr (see the answer to muskelbiber question above) and test it?

ah thank you! :)
with this your script is working with Linux Mint! :)
afaik everythink is working (optimus start, nvidia on (on/off handled by bumblebee :)), haven't tried the shortcuts (no need for me :)) yet

---

### Post by mtron on 2013-03-27
> **ebilpanda said:**
> with this your script is working with Linux Mint! :)

ok Thanks.I will enable mint 14 support with the next release. one more bugfix related to nvidia mode: Can you please test with the latest [revision 120]("http://bazaar.launchpad.net/~mtron/+junk/eee1015pn/download/head:/displaysettings-20111031094943-fe0sfodfaz9g8u6d-24/display-settings") if glx & vdpau works in nvidia mode? open nvidia-settings and see if Direct Rendering says 'Yes' on the 'GLX Information' tab.

Cheers!

---

### Post by ebilpanda on 2013-03-27
> **mtron said:**
> ok Thanks.I will enable mint 14 support with the next release. one more bugfix related to nvidia mode: Can you please test with the latest [revision 120]("http://bazaar.launchpad.net/~mtron/+junk/eee1015pn/download/head:/displaysettings-20111031094943-fe0sfodfaz9g8u6d-24/display-settings") if glx & vdpau works in nvidia mode? open nvidia-settings and see if Direct Rendering says 'Yes' on the 'GLX Information' tab.



hmm i can't get nvidia-settings to get started ^^' it days that i'm not using the nvidia x driver and that I should run "nvidia-xconfig" as root (already done and restarted with only nvidia mode) but the error won't go away :/

oh and glxspheres is not working in nvidia only mode for me :/

in optimus mode glxspheres and so on is working :)

---

### Post by mtron on 2013-03-27
hm. tricky. heres the next try [rev 122]("http://bazaar.launchpad.net/~mtron/+junk/eee1015pn/download/head:/displaysettings-20111031094943-fe0sfodfaz9g8u6d-24/display-settings"). if nvidia mode fails again please add the /var/log/Xorg.0.log. (or Xorg.1.log... just use the one with the most recent modification time) 

also check if the right ld.so.conf is linked by update-alternatives. 
```
update-alternatives --get-selections | grep i386-linux-gnu_gl_conf
```

this should output a manual link to /usr/lib/nvidia-current/ld.so.conf

---

### Post by ebilpanda on 2013-03-27
> [COLOR=#000000]hm. tricky. heres the next try [/COLOR][rev 122]("http://bazaar.launchpad.net/~mtron/+junk/eee1015pn/download/head:/displaysettings-20111031094943-fe0sfodfaz9g8u6d-24/display-settings")[COLOR=#000000]. if nvidia mode fails again please add the /var/log/Xorg.0.log. (or Xorg.1.log... just use the one with the most recent modification time) [/COLOR]

[COLOR=#000000]also check if the right ld.so.conf is linked by update-alternatives. [/COLOR]
[COLOR=#000000]Code:

update-alternatives --get-selections | grep i386-linux-gnu_gl_conf[/COLOR]
[COLOR=#000000]this should output a manual link to /usr/lib/nvidia-current/ld.so.conf
[/COLOR]

hmm nvidia-settings are still not working
i used you display-settings (copied to /usr/bin) and restartet - now the resolution was good and so on but nvidia still fails
-> i used the command nvidia tells me and relogged -> still xserver error by nvidia
->if i user your command:

```
$ update-alternatives --get-selections | grep i386-linux-gnu_gl_conf
i386-linux-gnu_gl_conf         manual   /usr/lib/nvidia-current/ld.so.conf

```

:)

and here my xorg.0.log:

[http://pastebin.com/QsBYCWNu](http://pastebin.com/QsBYCWNu)

---

### Post by mtron on 2013-03-27
looks good as far as i can see. Only the driver fails to load.
[   169.120] (EE) NVIDIA: Failed to load the NVIDIA kernel module. Please check your
[   169.120] (EE) NVIDIA:     system's kernel log for additional error messages.

is there anything interresting in dmesg or syslog ? Seems I need to test this when i get to my eee. Thanks for your time

EDIT: Just realized that there was a known bug concerning mint display manager. Replace mdm with lightdm and nvidia mode will work.
```
sudo apt-get remove mdm
sudo apt-get install --no-install-recommends lightdm gnome-settings-daemon unity-greeter ubuntu-mono light-themes
```

---

### Post by ebilpanda on 2013-03-27
> **mtron said:**
> looks good as far as i can see. Only the driver fails to load.
[   169.120] (EE) NVIDIA: Failed to load the NVIDIA kernel module. Please check your
[   169.120] (EE) NVIDIA:     system's kernel log for additional error messages.

is there anything interresting in dmesg or syslog ? Seems I need to test this when i get to my eee. Thanks for your time


nope i'm sorry haven't seen anything strange, error, or something like this :/
but i could post the logs tomorrow ;)

> **mtron said:**
> EDIT: Just realized that there was a known bug concerning mint display manager. Replace mdm with lightdm and nvidia mode will work.
```
sudo apt-get remove mdm
sudo apt-get install --no-install-recommends lightdm gnome-settings-daemon unity-greeter ubuntu-mono light-themes
```

hmm nope still not working :/ same problem as before :/
what i tried:
```
sudo display-settings reboot-nvidia
sudo reboot
```

```
sudo display-settings config-nvidia
```
(because not working ;))
-> logged out & in

```
sudo nvidia-xconfig
```
->logged out & in
(still not working)

```
sudo display-settings fix
```
->logged out & in
(result the same...;))

hmm but as long as optimus mode works :)

oh and after all this failed i deinstalleed lgihtdm and reinstalled mdm =D (i think its kind of faster -> and there are themes and so on =D)

---

### Post by muskelbiber on 2013-03-28
> **mtron said:**
> 


thanks for the bugreport. i have pushed a fix to the bzr repository. Could you please test it? (replace /usr/bin/display-settings with [this revision 120]("http://bazaar.launchpad.net/~mtron/+junk/eee1015pn/download/head:/displaysettings-20111031094943-fe0sfodfaz9g8u6d-24/display-settings"). then mark it executeable with chmod +x /usr/bin/display-settings )




The Intel-card now works for me, thank you! The Nvidia-Card isn't working anymore, X-server isn't starting. For me it's okay because I don't want to use it. I tested rev. 122, too, same problem.

```
 update-alternatives --get-selections | grep i386-linux-gnu_gl_conf
```

gave 

```
[COLOR=#ff0000]i386-linux-gnu_gl_conf[/COLOR]         auto     /usr/lib/fglrx/alt_ld.so.conf
```

Perhaps there is the error for me because the link refers to the fglrx-driver for a ati-card I don't have :)

Anyway, thanks mtron for the quick help and preventing my 1015pn from overheating ;)

---

### Post by Mizio on 2013-03-28
> **Mizio said:**
> ..... I installed ubuntu 12.04.02 amd64 with new Nvidia driver 310.32 (from PPA xorg-edger) and everything works fine.
Then I installed the acpitools and I encountered the following problem:
- If I start 
[HTML]sudo display-settings status[/HTML]
I have not answer
- Also on the startup screen (user logon) if I move the mouse the screen goes black and (it is my impression) restarts the xserver.....
Hello
 I did some tests with the two graphics cards for my problem.
If I use the intel graphics card I have the above problems (not answer whit "sudo display-setting status" and if i move the mouse the screen goes black in the startup screen) and I noticed another problem:
- while working suddenly the screen returns to black and the session is ended and you return to the startup screen.

If I start the nvidia ION grafic card I have no problems for this session, but the command  "sudo display-setting status" still does not answer and, on the next reboot, the card intel start without being set
Tanks for your help

---

### Post by gumbomumbo on 2013-04-03
Hey mtron, how is it going with supporting linux mint 14? Any progress?

---

### Post by mtron on 2013-04-13
> **Mizio said:**
> 
sudo display-setting status" still does not answer

so logging to file is turned on ;) check /var/log/acpi-call.log

[QUOTE=gumbomumbo]Hey mtron, how is it going with supporting linux mint 14? Any progress? [/QUOTE]

current Version should work. Just replace mdm with lightdm.

---

### Post by mtron on 2013-04-14
hello! 

Nvidia finally [offically introduced optimus support]("http://www.nvidia.com/object/linux-display-amd64-319.12-driver.html") on Linux. This was a very long and hard battle and the nvidia linux devs are ~ 3 years late. But better late than never :P

Did anyone try the "[Offloading Graphics Display with RandR 1.4]("http://us.download.nvidia.com/XFree86/Linux-x86/319.12/README/randr14.html")"  support of new nvidia drivers 319.12+ on our eeepc's ?

Appearantly this might simplify the needed job on our netbooks drastically. As i understand the doc all we need is a upstart job that permanently sets the reboot mode to optimus, the rest will be handled by the nvidia driver (minor customisation on xorg.conf is needed though) 

Unfortunatly this needs some newer xrandr version than in raring so we will have to wait for a ppa to provide the needed randr version or worst case we have to wait for raring+1 .

But it seems this hack will be unnecessary very soon. Yay ... and thanks nVidia for finally supporting your own product ;)

---

### Post by mtron on 2013-04-22
Hello readers!

I have pushed a new version (eee1015pn-acpitools 0.9.2) to the [ppa]("https://launchpad.net/~mtron/+archive/eee1015pn"). It should get installed automatically once you run a system upgrade. To trigger such an upgrade now use
```
sudo apt-get update && sudo apt-get dist-upgrade
```

**Changelog:**

  * added Mint 14 and Ubuntu Raring 13.04 support
  * fixed some more problems with new nvidia driver naming shema
  * vga-selector-gui: fixed Second X-Server in Optirun Mode

**Documentation /How to use:**
[http://mtron.co.nr/projects/eee1015pn](http://mtron.co.nr/projects/eee1015pn)

**Distribution Upgrades:**
If you plan to upgrade from quantal to raring make sure that you have min. 0.9.0 installed. After the upgrade completed run
```
sudo display-settings regenerate-glx
```

and reboot. 

**Release Notes:**
This release fixes the (hopefully) last bugs with the new nvidia binary driver naming shema. Now both driver names (nvidia-current and nvidia-304, nvidia-310 ect.) will work. Also the optirunsession got some fixes and starting another X-Server on the nvidia gpu and draw to a hdmi device works again.

Have fun!

---

### Post by eats7 on 2013-05-24
have just downloaded with the instructions from your site. computer loads up fine, but cinnamon crashes into fallback and is unable to recover. using mint 15.

---

### Post by mtron on 2013-05-25
replace mdm with lightdm. see the [FAQ]("https://sites.google.com/site/mtrons/projects/eee1015pn#TOC-FAQ").

---

### Post by mtron2 on 2013-08-06
Hello Everybody.

I started to add support for the upcoming Saucy release but it turns out to be a bumpy road. The acpi-call kernel module fails to build so we can't set the Gaphics mode. 

So for now Saucy is a no-go for the 1015pn.

---

### Post by mahen2 on 2013-08-12
Hi ! First, thanks for your work !!

I have just acquired an used 1015PN laptop and noticed it quickly got very hot when using the Nvidia GPU. So I installed your PPA and planned to disable the Nvidia GPU and only keep the intel one : I'm using Xubuntu 13.04 anyway, so I don't need any fancy graphical feature (just using www / thunderbird / etc).

However, I think I followed the right step, but I get the following error when trying to install eee1015pn-acpitools :
depends on : bbswitch-source but is not installable.

Any idea ?
Best regards,
Mahen

---

### Post by Draugen River on 2013-08-15
Installed 13.04 a few days ago, get the same issue as mentioned here:

The following packages have unmet dependencies:
 eee1015pn-acpitools : Depends: bbswitch-source but it is not installable
E: Unable to correct problems, you have held broken packages.


sudo add-apt-repository **ppa:bumblebee/testing**

allowed me to install eee1015pn-acpitools again...

Just a few days with no intel mode makes you miss the eee1015pn-acpitools a lot...

---

### Post by mtron2 on 2013-08-18
Hello! 

Thanks for reporting this! i introduced this bug when adding support for the next Ubuntu release (saucy) since bbswitch is in the official ubuntu repositories from this release onwards. I forgot that the package i referenced won't be available on earlier Ubuntu releases.

Fix is already in bzr and updated packages should be available soon.

Cheers!

---

### Post by finny388 on 2013-08-19
Hello mtron and all,

I just installed Netflix Desktop and playback is unwatchably choppy as if I'm watching a slide show instead of video.
I'm using nvidia drivers on xubuntu
I know I can play 1080 content because xmbc plays them easily (oddly vlc does not)
My bandwidth avg's 20mbps/2mbps 

Does anyone have this working? Or is the hardware just not strong enough to handle it?

:(

---

### Post by mtron2 on 2013-08-20
hello! 

i have no experience with netflix so i can't comment on that. the GT218 nvidia chip should be capable of playing it though. i tested 720p and 1080i videos with vdpau and they worked well. (deinterlacing is not needed for 720p but the temporal deinterlacer also worked without frame-drops for 1080i)

> I know I can play 1080 content because xmbc plays them easily (oddly vlc does not)

Thats no big surprise. xbmc and mplayer have good vdpau support what vlc lacks. vlc only supports a subset of vdpau via vaapi, not the full set of features like the others. Imho best media players for vdpau are mplayer (you can also use the smplayer frontend if you like) or xbmc. Also xine based media players work pretty good (it's much trickier to configure though).

Cheers!

---

### Post by finny388 on 2013-08-20
Thanks for the confirmation on vdpau support. That's exactly what I suspected with xbmc and vlc.

I think the issue is that the silverlight wrapped into the wine installation doesn't use the video card or doesn't use it properly. And I'm happy with the nvidia drivers otherwise - I don't want to mess with the open ones.

I dug around my smart tv features and the tv handles it fine so that's how I'll use netflix

For anyone interested, this was the q/a I tried to follow:

[https://answers.launchpad.net/netflix-desktop/+question/233085]("https://answers.launchpad.net/netflix-desktop/+question/233085")

But I didn't have an X11 Driver key in the registry. Creating it and adding the string value didn't make a difference either.

---

### Post by lead-expression-u on 2013-09-23
Dear all,

After a dist-upgrade performed 3 weeks ago I have now the same problem reported here: [http://ubuntuforums.org/showthread.php?t=1677780&p=12518003#post12518003](http://ubuntuforums.org/showthread.php?t=1677780&p=12518003#post12518003)

How can I solve it and restore the previous situation? I really want to avoid to re-install the system completely...

Regards

Nicola

---

### Post by mtron2 on 2013-10-06
Hello! 

Could you please provide more system information? (Release, Arch, acpi-call-tools version, dkms status, syslog, Xorg.log ect.) 

If you are on Precise LTS you coud try to remove 'quiet splash' from the grub command line and replace it with 'textonly'. This will boot into a text shell instead of the display manager. 

Login, connect to the internet and reinstall lightdm
```
sudo apt-get update && sudo apt-get dist-upgrade
sudo apt-get remove mdm 
sudo apt-get install --no-install-recommends lightdm gnome-settings-daemon unity-greeter ubuntu-mono light-themes
```

Now try to start lightdm with:
```
sudo lightdm
```

If lightdm still crashes you will get some debug info in the shell, and we can see what's wrong.

Cheers!

---

### Post by k3v1n-aznar on 2013-10-08
Hello, how can I change the default boot vga (intel or nvidia) with a terminal?

---

### Post by mtron2 on 2013-10-09
> **k3v1n-aznar said:**
> how can I change the default boot vga (intel or nvidia) with a terminal?

change the configuration file /etc/eee1015pn/ds.conf with a text editor of your choice:

```
## set the default GPU mode 
## Options: intel|nvidia|optimus
defaultgpu=intel
```

and reboot. You can find a detailed description of the other options here: [http://mtron.co.nr/projects/eee1015pn](http://mtron.co.nr/projects/eee1015pn)

---

### Post by finny388 on 2014-01-30
Hello Mtron

Are you able to watch youtube flash videos smoothly in 720p or 1080p?
If so, how did you go about it?
If not, what is the best we can expect and how to do it?

Thanks for your help

---

### Post by mtron2 on 2014-02-01
I just tested this:

- boot to nvidia mode
- install smplayer (mplayer frontend) and a recent mplayer build and configure it to use vdpau 
- use smplayers youtube browser (just press F11 in smplayer)
- in the Youtube Browser settings I set it to use '720p mp4' streams
- enter the url to the youtube video and hit search ( eg. [http://www.youtube.com/watch?v=txRAL49PCYM](http://www.youtube.com/watch?v=txRAL49PCYM) )

This  works good for me.

---

### Post by finny388 on 2014-02-01
mplayer is installed and up to date
installed smplayer
changed the Output Driver to vdpau
I can't find a youtube section and F11 does nothing

do I have to install smtube?

---

### Post by mtron2 on 2014-02-02
yes :) i thought apt auto-pulls smtube with smplayer, sorry. 

get it from smplayer's developer ppa [https://launchpad.net/~rvm/+archive/smplayer](https://launchpad.net/~rvm/+archive/smplayer)

---

### Post by finny388 on 2014-02-02
Ah yes thanks
I got it installed last night v0.8.6
It would play fine at 720p but then the video would start to lag behind the audio until it was seconds out of sync

I'm having trouble with video in general and all of a sudden.

If you have any time please have a look at this [thread]("http://ubuntuforums.org/showthread.php?t=2199817")

I've since tried to start fresh but still with the same lagging/studdering video playback (my main concern is getting XBMC/vdpau to play nice)

Do you plan on a hardware upgrade any time soon? the 1015pn has been good to me but only when I can squeeze max performance out of it.

---

### Post by mtron2 on 2014-02-14
I got a new Laptop from the Company i work for. It's a ThinkPad X1 Carbon Ultrabook which is a very nice (but unfortunatly also very expensive) Laptop ;)

---

### Post by finny388 on 2014-02-14
nice
Is that your main pc now and is it running linux?
Also, does that mean you are not supporting 1015pn anymore?

---

### Post by mtron2 on 2014-02-19
Nope, it's a work laptop. At home i still prefer my workstation. > Also, does that mean you are not supporting 1015pn anymore?

I will defiantly release a last version with ubuntu 14.04 support, but this will be the last ubuntu release i support for the eee 1015pn. This hardware will reach end of life pretty soon and i doubt there are still may eee users out there in the wild.

---

### Post by mtron2 on 2014-03-16
Hello! 

Unfortunately nvidias dualgpu implementation shipped with trusty & nvidia 331 does not support our eee's so i updated the scripts for ubuntu trusty. Hopefully this will be the last release because i expect  that the nvidia devs add more platforms to their implementation soon. 

To install eee1015pn-acpitools Version 0.11.0 add the [ppa]("https://launchpad.net/%7Emtron/+archive/eee1015pn") to your system and install the **eee1015pn-acpitools** Package or run a system upgrade if you have already done so. To trigger such an upgrade now use
```
sudo apt-get update && sudo apt-get dist-upgrade
```

**Changelog:**

      * added Ubuntu [Trusty]("https://launchpad.net/%7Emtron/+archive/eee1015pn/+packages?field.name_filter=&field.status_filter=published&field.series_filter=trusty") 14.04 support (Use the [PPA]("https://launchpad.net/%7Emtron/+archive/eee1015pn") to install!)
  * optimus: fixed detection of nvidia gpu power state 
  * use unity-control-center for display management with intel on trusty

**Documentation /How to use:**
[http://mtron.co.nr/projects/eee1015pn](http://mtron.co.nr/projects/eee1015pn)

**Distribution Upgrades:**
If you plan to upgrade to trusty make sure that you have min. 0.11.0 installed. After the upgrade completed run
```
sudo display-settings regenerate-glx
```
and reboot. 

**Release Notes:**
This release introduces Support for ubuntu trusty thar 14.04 LTS and works with the following nvidia drivers available via ubuntus Repositories: nvidia-current, nvidia-304, nvidia-310, nvidia-319, nvidia-331

Have fun!

---

### Post by nonragiono2 on 2014-05-02
Hello.

I'm trying to make optirun work on my 1015pn.

I'm using Lubuntu 14.04 with nvidia-304 and your tools from ppa repository (thanks for the great job!).

when I run:

optirun glxinfo 

i get:

[  847.241959] [ERROR]Cannot access secondary GPU - error: [XORG] (EE) NVIDIA(0): Failed to initialize the NVIDIA GPU at PCI:4:0:0.  Please

[  847.242156] [ERROR]Aborting because fallback start is disabled.

and dmesg:

[  846.673067] bbswitch: enabling discrete graphics
[  847.128393] vgaarb: device changed decodes: PCI:0000:04:00.0,olddecodes=none,decodes=none:owns=none
[  847.128892] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  304.117  Tue Nov 26 21:25:36 PST 2013
[  847.232629] NVRM: failed to copy vbios to system memory.
[  847.233201] NVRM: RmInitAdapter failed! (0x30:0xffffffff:867)
[  847.233225] NVRM: rm_init_adapter(0) failed
[  866.576187] bbswitch: disabling discrete graphics
[  866.576230] ACPI Warning: \_SB_.PCI0.P0P4.DGPU._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
[  866.592086] pci 0000:04:00.0: Refused to change power state, currently in D0

After running optirun, module nvidia stays loaded and discrete nvidia is ON in /proc/acpi/bbswitch and i have to manually disable nvidia (sudo display-settings nv-off)

This is my lscpi:

00:02.0 VGA compatible controller: Intel Corporation Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller (rev 02)
04:00.0 VGA compatible controller: NVIDIA Corporation GT218 [ION] (rev ff)

Thanks.
Gio

---

### Post by vincent-kubicki on 2014-05-04
Hi.

Optimus is available since Nvidia drivers version 319.12 [http://www.webupd8.org/2013/04/nvidia-releases-linux-graphics-drivers.html](http://www.webupd8.org/2013/04/nvidia-releases-linux-graphics-drivers.html). The Nvidia-Prime modifies the computer configuration so that the discrete GPU can be used [http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html](http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html). Additionally, the Prime Indicator [http://www.webupd8.org/2014/01/prime-indicator-lets-you-quickly-switch.html](http://www.webupd8.org/2014/01/prime-indicator-lets-you-quickly-switch.html) allows for the restart of the Xserver without rebooting, to switch between the integrated and discrete graphic cards.

As mtron mentionned in a previous post, the 1015pn implementation of Optimus is very peculiar: "The 1015pn has a quite rare hardware design. Both gpu's are directly wired to the Laptop's LVDS panel and this physical connection is the important part."

How does all this is playing together ? I understand that acpi calls are used in the 1015pn to select the mode at next boot. I imagine that Bumblebee or Prime Indicator use another acpi call to disable the discrete gpu, as this option is available on more classical Optimus configuration where the discrete gpu connects to the LCD panel throught the integrated gpu.

Suppose I want to use nvidia-prime on my 1015pn as this seems to become a more standard option than Bumlebee (and on-the-fly switch seems to be on the way). Is it logical to use the 1015pn Optimus mode, and then, inside this mode, use Prime Indicator to switch without rebooting ?

Or, am I misunderstanding the whole thing completely, and the capabilities provided by the nvidia-prime package are only usable by the standard versions of Optimus, and not the one used in the 1015pn. Is just completely useless on a 1015pn then ?

All this lead me to a more general question. On the Wikipedia page [https://en.wikipedia.org/wiki/Nvidia_Optimus#GNU.2FLinux_support](https://en.wikipedia.org/wiki/Nvidia_Optimus#GNU.2FLinux_support) it is mentioned that "As in the Windows implementation, by default all applications run through the integrated graphics processor.". I understand that this is not the case on the 1015pn, so what is the meaning of the Optimus mode on that machine ? How can both graphic cards be connected to the LCD panel at the same time ? Are the two paths available, meaning direct discrete gpu access to the panel and throught the integrated graphic card, the latter mode being the Optimus mode ?

I really like my 1015pn and hope to be able to continue to use the latest Ubuntu on it :) !

---

### Post by nonragiono2 on 2014-05-10
Hi,
I tried many configurations and I obtained good results:

1015pn with PRIME

This is what I did:

1. Lubuntu 14.04 x64 fresh installation.
2. Reboot - after reboot nouveau drivers are used by kernel.
3. In "Software & Update" I selected "Additional Drivers" and I installed nvidia proprietary driver 331 - it installs also nvidia-prime and bbswitch (if not install them).
4. I installed acpi_call dkms module (I had some problem compiling git version 0.0.1 thus I extracted acpi_call from mtron's package eee1015pn-acpitools_0.11.0-1~trusty1_all.deb)
5. I loaded acpi_call module: sudo modprobe acpi_call
6. Select Optimus for next reboot: echo "\OSGS 0x03" > /proc/acpi/call
7. Reboot
8. After reboot I have both Intel and Nvidia are working and in nvidia-setting I can chose to use Intel or nvidia - need log out to activate selected VGA!
9. I created a script in init.d to select Optimus at every reboot

N.B.
a) to obtain "real" fps in glxgears with nvidia you have to deselect "Sync to Vblak" option in nvidia-settings - remember to activate it again after trying glxgears!

b) I tried to install eee1015pn-acpitools from mtron's ppa but xorg files in this package conflict with nvidia-prime and on every reboot display-settings started to reinstall nvidia and xorg-core.

c) I tried to reboot in "only intel" mode (echo "\OSGS 0x01" > /proc/acpi/call)  and "only nvidia" mode (echo "\OSGS 0x02" > /proc/acpi/call) and I had working lxde but with stranges resolution using nvidia.

d) I'll try to remove nvidia-prime and use bumblebee... I'll let you know.

Regards.
Gio

---

### Post by mtron2 on 2014-05-23
> **nonragiono2 said:**
> 
I tried to install eee1015pn-acpitools from mtron's ppa but xorg files in this package conflict with nvidia-prime 

Those bastards. I was here first ;) I'll see if i can fix this soon.


> **nonragiono2 said:**
> and on every reboot display-settings started to reinstall nvidia and xorg-core.

Yes this is expected behaviour when the md5 checksums of the linked glx libs don't match those the kernel driver wants.

---

### Post by vincent-kubicki on 2014-05-25
Hi,

thank for the answers. I guess I will not be of much help here, because I did the update from 13.10 to 14.04 and I can not remember if I had packages conflicts ! So basically I am using:
[LIST]
[*]the graphical swith provided by mtron 
[*]nvidia-prime 
[*]nvidia driver 331 
[/LIST]
I can confirm the hypothesis of my previous post. If you choose Optimus in the mtron graphical switch, you have access to the PRIME settings in the nvidia driver. That means that in order to use the GPU, you can either:

[LIST]
[*]select GPU with the ACPI tool 
[*]Optimus in the ACPI tool and GPU in the driver 
[/LIST]
Personnally I do not have much use for the GPU on this machine, so I will just go with the second solution to keep configuration consistent with the other machine (N76VZ) I am using. There are still other things to test, like HDMI output. It works using nvidia-prime on the N76VZ, and I will share whatever test results I get here.

Note that in both ways to get the GPU, I have the good screen resolution. However, the fonts are too large using the GPU. I changed all the fonts to 9 points, and when I use the GPU the fonts seem to have reverted to their original sizes. Of course the last time I used Bumblebee there was no font problem.

Cheers !

---

### Post by sam-c on 2014-06-17
similar with asus 904hd windows xp and ubuntu 14.04 lts and linuxmint

---

### Post by yanndan on 2014-10-19
Hello,

I have an issue with the 1015pn and ubuntu 14.04. I did not manage to reach a working system. I followed the instructions of this thread. 

I reinstall the computer from scratch 
I install your tools from the repository (thanks by the way)
I switched the CPU to intel only since this computer is only used for the Web and office small jobs

This worked for some times. But comparing to the 12.04, the battery lasts only 3h now (it was ~ 6 before), and it becomes very hot after few minutes. 
Now I have a new problem. I cannot reach the desktop: after the login, I am stuck on this screen. 

I am ready to reinstall from scratch. Could you give me a hint how to get back this netbook on 14.04, without heat and with a good battery ? Is  bumblebee a possible solution? I am a bit lost right now. 

Thanks in advance, 
yanndan

P.S.: My twins arrived early this month. I might be slow to answer.

---

### Post by mtron2 on 2014-10-27
Hello! 

It seems your problem is that the nvidia chip is not deactivated. Probably the acpi-call Kernel module is not build against your current running kernel. Can you please submit a bugreprot via the vga-selector gui? This auto-collects some debug info i need to help you with your problem.

Cheers! 
mtron

---

### Post by yanndan on 2014-11-04
Hey mtron,

Thanks for your answer. You are right, there is a problem with the acpi_call.
Below is the bug report. Do you have any idea how to build acpi_call for my kernel?

Thanks again and sorry for the late answer, diapers can be really time consuming.

Cheers,
yanndan

```
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

Installed Program Versions:
eee1015pn-acpitools version 0.11.0
nvidia binary driver

Used Desktop Enviroment:
gnome-fallback-compiz

installed glx files:
/usr/lib/nvidia-331/xorg/libglx.so
/usr/lib/nvidia-331/xorg/libglx.so.331.38
/usr/lib/xorg/modules/extensions/libglx.so
/usr/lib/xorg/modules/extensions/libglx.so.intel

display-settings config:
defaultgpu=intel
debug=1
logtofile=1
nvautopowerdown=1
#DESKTOP_SESSION=gnome
#distconf="arch"
#arc="i386"
#settingsbackend="dconf"

installed dkms modules:
acpi-call, 20140823, 3.13.0-34-generic, x86_64: installed
acpi-call, 20140823, 3.13.0-36-generic, x86_64: installed
acpi-call, 20140823, 3.13.0-37-generic, x86_64: installed
bbswitch, 0.8, 3.13.0-24-generic, x86_64: installed
bbswitch, 0.8, 3.13.0-34-generic, x86_64: installed
bbswitch, 0.8, 3.13.0-36-generic, x86_64: installed
bbswitch, 0.8, 3.13.0-37-generic, x86_64: installed
fwts-efi-runtime-dkms, 14.03.01, 3.13.0-34-generic, x86_64: installed
fwts-efi-runtime-dkms, 14.03.01, 3.13.0-36-generic, x86_64: installed
fwts-efi-runtime-dkms, 14.03.01, 3.13.0-37-generic, x86_64: installed
tp-smapi, 0.41, 3.13.0-34-generic, x86_64: installed
tp-smapi, 0.41, 3.13.0-36-generic, x86_64: installed
tp-smapi, 0.41, 3.13.0-37-generic, x86_64: installed

00:00.0 Host bridge: Intel Corporation Atom Processor D4xx/D5xx/N4xx/N5xx DMI Bridge (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device 83ac
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel

00:02.0 VGA compatible controller: Intel Corporation Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller (rev 02) (prog-if 00 [VGA controller])
    Subsystem: ASUSTeK Computer Inc. Device 83ac
    Flags: bus master, fast devsel, latency 0, IRQ 44
    Memory at f7e00000 (32-bit, non-prefetchable) [size=512K]
    I/O ports at dc00 [size=8]
    Memory at e0000000 (32-bit, prefetchable) [size=256M]
    Memory at f7d00000 (32-bit, non-prefetchable) [size=1M]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915

00:02.1 Display controller: Intel Corporation Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device 83ac
    Flags: bus master, fast devsel, latency 0
    Memory at f7e80000 (32-bit, non-prefetchable) [size=512K]
    Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device 841c
    Flags: bus master, fast devsel, latency 0, IRQ 45
    Memory at f7cf8000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel

00:1c.0 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport

00:1c.1 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 2 (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=03, sec-latency=0
    I/O behind bridge: 00001000-00001fff
    Memory behind bridge: f8000000-fbffffff
    Prefetchable memory behind bridge: 00000000f0000000-00000000f6ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport

00:1c.3 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 4 (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: f7f00000-f7ffffff
    Prefetchable memory behind bridge: 0000000080000000-00000000801fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport

00:1d.0 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
    Subsystem: ASUSTeK Computer Inc. Device 83ad
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at d400 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
    Subsystem: ASUSTeK Computer Inc. Device 83ad
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at d480 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
    Subsystem: ASUSTeK Computer Inc. Device 83ad
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at d800 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.3 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
    Subsystem: ASUSTeK Computer Inc. Device 83ad
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at d880 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB controller: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
    Subsystem: ASUSTeK Computer Inc. Device 83ad
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at f7cf7c00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci-pci

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=64
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device 83ad
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: lpc_ich

00:1f.2 SATA controller: Intel Corporation NM10/ICH7 Family SATA Controller [AHCI mode] (rev 02) (prog-if 01 [AHCI 1.0])
    Subsystem: ASUSTeK Computer Inc. Device 83ad
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 43
    I/O ports at d080 [size=8]
    I/O ports at d000 [size=4]
    I/O ports at cc00 [size=8]
    I/O ports at c880 [size=4]
    I/O ports at c800 [size=32]
    Memory at f7cf7800 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ahci

01:00.0 Ethernet controller: Qualcomm Atheros AR8132 Fast Ethernet (rev c0)
    Subsystem: ASUSTeK Computer Inc. Device 838a
    Flags: bus master, fast devsel, latency 0, IRQ 46
    Memory at f7fc0000 (64-bit, non-prefetchable) [size=256K]
    I/O ports at ec00 [size=128]
    Capabilities: <access denied>
    Kernel driver in use: atl1c

02:00.0 Network controller: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter (rev 01)
    Subsystem: AzureWave Device 2047
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at fbffc000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: bcma-pci-bridge


acpi-call related dmesg output:
[   26.045252] acpi_call: module verification failed: signature and/or  required key missing - tainting kernel
[   28.584262] acpi_call: Cannot get handle: Error: AE_NOT_FOUND
[   28.584464] acpi_call: Cannot get handle: Error: AE_NOT_FOUND
[   28.584604] acpi_call: Cannot get handle: Error: AE_NOT_FOUND
[   28.584736] acpi_call: Cannot get handle: Error: AE_NOT_FOUND
[   28.584891] acpi_call: Cannot get handle: Error: AE_NOT_FOUND
[   28.655071] acpi_call: Cannot get handle: Error: AE_NOT_FOUND
[   28.655406] acpi_call: Cannot get handle: Error: AE_NOT_FOUND
[   28.655704] acpi_call: Cannot get handle: Error: AE_NOT_FOUND
[   28.656081] acpi_call: Cannot get handle: Error: AE_NOT_FOUND
[   28.656418] acpi_call: Cannot get handle: Error: AE_NOT_FOUND

bbswitch related dmesg output
```

---

### Post by mtron2 on 2014-11-13
Hello! 

```
acpi_call: Cannot get handle: Error: AE_NOT_FOUND
```

strange error. Never had this on my system but i still use precise on my eeepc (works best for me ;)

can you manually checkout the latest acpi_call git and change line 9 in the file acpi_call.c 

from
```
#include <acpi/acpi.h> 
```
to
```
#include <linux/acpi.h>
```

and rebuild & reload the kernel module. Now try to manually send a acpi-call as described [here]("https://sites.google.com/site/mtrons/howtos/eeepc-1015pn#TOC-Graphics-Card-Switching") in the section "Alternative: Set the VGA Mode manually"

---

### Post by luk4 on 2014-11-14
Hello everyone, I just wanted to have a couple of questions: On my netbook I,ve installed Xubuntu 14.04.1 (LTS). What is the correct procedure to install the switch?


this:
sudo apt-get update && sudo apt-get dist-upgrade
sudo add-apt-repository ppa: Mtron / eee1015pn
sudo apt-get update
sudo apt-get install build-essential eee1015pn-acpitools


or this:
sudo add-apt-repository ppa: Mtron / eee1015pn
sudo apt-get update && sudo apt-get dist-upgrade
sudo apt-get install eee1015pn-acpitools


Keyboard brightness controls will work after installation?
I also have to install the nvidia driver?


Many thanks and congratulations to Mtron for the great work!

---

### Post by mtron2 on 2014-11-14
doesn't really matter. Use the first one to be on the safe side.

But a user reported that the acpi_call kernel module does not work with 3.13 so you might want to wait until we can figure out whats wrong.

---

### Post by luk4 on 2014-11-15
Thanks Mtron, after installation I was finally able to use the integrated VGA (Intel). The only thing that does not work is the brightness control; after every reboot is activated at maximum brightness. Is it the problem of acpi-call were talking about? Is there any solution? Thanks again, bye.

---

### Post by mtron2 on 2014-11-16
No, Brightness control works flawlessly on my system with intel and nvidia. 
Do you use any special kernel command line parameters in grub? 
like pci=noacpi or acpi=force[COLOR=#000000][FONT=sans-serif]  or [/FONT][/COLOR][COLOR=#000000][FONT=monospace]acpi_osi="Linux" (or any other non default parameter ? [/FONT][/COLOR] 

If so remove all of them. They are not needed and do more harm than help.

I am a bit surprised that the acpi call module build for you. [COLOR=#000000]yanndan reported that the kernel module does not build with 3.13. Can you please post a 'uname -a' and 'dkms status' output?[/COLOR]

---

### Post by luk4 on 2014-11-16
Mtron Hello, I'm not very experienced with Linux, but if you explain to me how to do, now I will post what I get. I have not added anything in the grub. How do I check that the parameters have to show me?

---

### Post by luk4 on 2014-11-17
Hello Mtron, these are the details that you needed?

luk@X-ino:~$ uname -a
Linux X-ino 3.13.0-39-generic #66-Ubuntu SMP Tue Oct 28 13:30:27 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
luk@X-ino:~$ dkms status
acpi-call, 1.1.2, 3.13.0-39-generic, x86_64: installed
bbswitch, 0.8, 3.13.0-39-generic, x86_64: installed
nvidia-304, 304.117, 3.13.0-39-generic, x86_64: installed

---

### Post by mtron2 on 2014-11-20
Hello Luk!

the kernel module is build so its all good with the gpu switching. 

Did adjusting display brightness work before you installed the eee1015pn-acpitools package? 

you could start with debugging by testing if setting the brightness via terminal works. Also please  do what Toz suggests in [this post]("http://ubuntuforums.org/showthread.php?t=2156192&p=12701098#post12701098") and post the pastebin link.

Cheers!

---

### Post by luk4 on 2014-11-23
Hi Mtron, this is my pastebin link:

luk@X-ino:~$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.13.0-39-generic root=UUID=2148aa82-79df-4e39-b188-168a1e11f5d3 ro quiet acpi_osi=Linux acpi_backlight=vendor splash
luk@X-ino:~$ for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; done
/sys/class/backlight/eeepc
0
15
/sys/class/backlight/intel_backlight
250
250
luk@X-ino:~$ lsmod
Module                  Size  Used by
hid_microsoft          12805  0 
hidp                   23826  1 
hid                   106148  2 hidp,hid_microsoft
ctr                    13049  2 
ccm                    17773  2 
bbswitch               13943  0 
acpi_call              12714  0 
bnep                   19624  2 
rfcomm                 69160  12 
binfmt_misc            17468  1 
arc4                   12608  2 
snd_hda_codec_hdmi     46368  4 
brcmsmac              563041  0 
cordic                 12574  1 brcmsmac
brcmutil               15618  1 brcmsmac
b43                   387371  0 
mac80211              630653  2 b43,brcmsmac
cfg80211              484040  3 b43,brcmsmac,mac80211
ssb                    62379  1 b43
snd_hda_codec_realtek    65580  1 
keucr                  72238  0 
usb_storage            62209  0 
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40664  1 uvcvideo
videodev              134688  2 uvcvideo,videobuf2_core
coretemp               13435  0 
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_hda_intel          56451  10 
snd_rawmidi            30144  1 snd_seq_midi
snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
joydev                 17381  0 
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_hwdep              13602  1 snd_hda_codec
i915                  783961  4 
serio_raw              13462  0 
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
btusb                  32412  0 
drm_kms_helper         55071  1 i915
lpc_ich                21080  0 
bluetooth             391136  27 bnep,hidp,btusb,rfcomm
snd_timer              29482  2 snd_pcm,snd_seq
drm                   303102  5 i915,drm_kms_helper
snd                    69322  31 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
bcma                   52096  3 b43,brcmsmac
soundcore              12680  1 snd
i2c_algo_bit           13413  1 i915
eeepc_laptop           19867  0 
mxm_wmi                13021  0 
asus_wmi               24191  0 
sparse_keymap          13948  2 eeepc_laptop,asus_wmi
video                  19476  2 i915,asus_wmi
wmi                    19177  2 mxm_wmi,asus_wmi
mac_hid                13205  0 
parport_pc             32701  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
ahci                   25819  3 
psmouse               106714  0 
libahci                32716  1 ahci
atl1c                  46086  0 
luk@X-ino:~$ pastebinit /var/log/dmesg


[http://paste.ubuntu.com/9204622/](http://paste.ubuntu.com/9204622/)

Bye.

---

### Post by luk4 on 2014-11-24
Hi Mtron, I've tried to change live VGA through nVidia Prime, but this is the result. My error, or impossible think?

---

### Post by casio2 on 2015-03-06
Hey there,

I gave it a try with elementary OS 0.3 (based on ubuntu 14.04) -> Kernel 3.13, nvidia 331 drivers, seems to work as the system settings show both graphics cards if I reboot into Optimus, only Intel rebooting into Intel mode,..

**uname -a:**
Linux casio-1015PN 3.13.0-46-generic #77-Ubuntu SMP Mon Mar 2 18:26:13 UTC 2015 i686 i686 i686 GNU/Linux

**dkms status:**
acpi-call, 1.1.2, 3.13.0-46-generic, i686: installedbbswitch, 0.7, 3.13.0-46-generic, i686: installed
bcmwl, 6.30.223.248+bdcom, 3.13.0-45-generic, i686: installed
bcmwl, 6.30.223.248+bdcom, 3.13.0-46-generic, i686: installed
nvidia-331, 331.113, 3.13.0-46-generic, i686: installed
nvidia-331-uvm, 331.113, 3.13.0-46-generic, i686: installed

But I can't seem to use the Optimus Mode, I get the same Error as luk4. I can also start the X-Server settings in Intel mode, getting the same error when trying to switch vga mode.
I was able to adjust brightness before installing the acpi tools, afterwards I wasn't but adding kernel parameters **acpi_osi=Linux acpi_backlight=vendor **did help me though.

What really annoys me is that booting takes forever, it seems to be stuck on
'*Stopping Read required files in advance'
for quite a while.
'*Starting NVIDIA Persistenced Daemon' seems to fail a couple of times during boot up.

I hope to get that old netbook to work on optimus again!

---

