---
title: "Sony Vaio Z2 (2011) Howto"
date: 2011-09-26
forum: Hardware
---

### Post by dothedog on 2011-09-26
All, This is what I have done to get Ubuntu Natty working on my new Z2. I apologize for the length but I tried to be complete.

[SIZE="3"]Howto Ubuntu Natty on Sony Vaio VPC-Z21 (2011)[/SIZE]

This is a description of what I did to get Ubuntu mainly working on my Vaio Z2. It works for me, but I give no guarantees that it will work on any other machine, ymmv, if you brick your device I take no responsibility, etc. etc. blah blah. Well with that out of the way. My machine is a CTO (Configure to Order) VPC-Z2190X. Specs: VPC-z2190X, i5-2540 Sandy Bridge V2, 6GB ram, 128GB SSD dm-raid 0, PMD (BR Player, Radeon HD6650), 1600x900 screen.

Installed Ubuntu Natty Narwhal 11.04 (I tried Oneiric Beta 1 but had issues installing grub),  Actually did the partition resize in windoze, shrank the windows partition to 59GB, with 43GB left for Linux, and a 10GB swap partition. Used fakeraid instead of software raid. A couple of tips, in kernel line in grub add “nomodeset”, this will prevent booting to a black screen. Grub  will fail to load initially on install so you need to Ctrl+Alt+F2 to a TTY cd /dev/mapper then an ls -la to see which partition you installed to and make sure you put it in the installer to install to /dev/mapper/isw....Volume0. I installed on dm-6. I would highly recommend that you DON'T install the AMD fglrx driver. It completely borked my install.

Update to the latest everything:
```
Sudo apt-get update
sudo apt-get install mesa-utils (for glxinfo)
sudo apt-get dist-upgrade
```

gets you to kernel 2.6.38-11

So with a standard install you get a number of issues: 

Power consumption is really high
3d Graphics don't work – boots into gnome 2.32.1 not Unity
Brightness is always at 100% fn+F5 fn+F6 don't work
Ctrl+Alt+F2 i.e. TTY consoles don't open
Suspend and Hibernate don't work/won't wake up
WWAN card doesn't work
Fingerprint reader doesn't work
PMD graphics don't work.
PMD Docking doesn't work, must be attached on boot or doesn't recognize eth1, cdrom or USB 
Clickpad kinda works, but no multi-touch.
In order to boot need to add “nomodeset” to grub line

What does work ootb:
Proc
RAID-0
Dual boot with Windows
Actually works for both PMD and on laptop with the r8169 driver
Wifi - centrino advanced-n 6230
fn+F3 and fn+F4 work to adjust audio volume
Webcam works ootb
Microphone works ootb

So first thing to do, compile a new kernel with the Sony Vaio patch.

Download kernel 3.1.0-rc6 from Linus Torvalds github repository (because kernel.org is still down).
 in a browser go to: [ https://github.com/torvalds/linux/ ]( https://github.com/torvalds/linux/ )
click on the “Downloads” button select View 250 other downloads highlight 3.1.0-rc6 select tar.gz (I know that rc7 is out now, but I haven't tried it yet) Also, the zip file for rc6 threw errors on me.
```
sudo mv ../Downloads/torvalds-linux-v3.1-rc6-0-gb6fd41e.tar.gz /usr/src
cd /usr/src
sudo tar xzvf  torvalds-linux-v3.1-rc6-0-gb6fd41e.tar.gz
cd torvalds-linux-8ff0291/ 
```

Download patch from here;
[http://www.absence.it/vaio-acpi/source/patches/](http://www.absence.it/vaio-acpi/source/patches/)
click on vaio-full-3.0-rc.patch 
patch the kernel
```
cd /usr/src/torvalds-linux-8ff0291/
patch -p1 < /path/to/patch/vaio-full-3.0-rc.patch 
```
Obviously change the path to where your patch downloaded to.
Should patch with no errors.

```
sudo make menuconfig
```
in General setup -> IRQ subsystem : Sparse irq numbering should be deactivated. If it says =y change to =n
from this post: [http://ubuntuforums.org/showpost.php?p=11146178&postcount=49](http://ubuntuforums.org/showpost.php?p=11146178&postcount=49)
Make sure that 
```
CONFIG_SONY_LAPTOP=m
```
I think it is by default.
Save and exit

I used a compile script to create .deb packages. Copy this into a gedit doc.
```

#!/bin/bash
# COMPILE

sourcedir=torvalds-linux-8ff0291
ver=01
cd $sourcedir
export CONCURRENCY_LEVEL=3

nohup /usr/bin/time -o TIME fakeroot make-kpkg \
  --initrd --append-to-version=-$ver \
  kernel_image kernel_headers >& OUTPUT &

```
Notes: sourcedir should be the patched 3.1.0-rc6 directory, ver= can be any number but it will append it to the end of the kernel name, CONCURRENCY_LEVEL should be number of cores + 1 (Not sure if that makes a difference though) 

save the script as COMPILE in the /usr/src/ directory and make it executable.
```
cd /usr/src
 sudo chmod +x COMPILE
```
 
Make sure you have all the dependencies required (not sure you need all of them but can't hurt):
```
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install fakeroot kernel-wedge makedumpfile libncurses5-dev libqt3-mt-dev build-essential crash kexec-tools git-core  libelf-dev asciidoc binutils-dev
sudo apt-get build-dep linux
```

run the COMPILE script:
```
sudo ./COMPILE
```
you can check the progress by
```
tail -f torvalds-linux-8ff0291/OUTPUT
```
when it completes you can check the compile time by:
```
cat torvalds-linux-8ff0291/TIME
```
Mine was ```
31:06.11elapsed
```
In the /usr/src dir you should have two .deb files.
```
-rw-r--r--  1 root src   7257380 2011-09-19 19:58 linux-headers-3.1.0-rc6-01_3.1.0-rc6-01-10.00.Custom_amd64.deb
-rw-r--r--  1 root src  42352160 2011-09-19 19:57linux-image-3.1.0-rc6-01_3.1.0-rc6-01-10.00.Custom_amd64.deb
```

Install them by 
```
sudo dpkg -i  linux-image-3.1.0-rc6-01_3.1.0-rc6-01-10.00.Custom_amd64.deb
sudo dpkg -i linux-headers-3.1.0-rc6-01_3.1.0-rc6-01-10.00.Custom_amd64.deb
```

Side note: I originally had compiled the r8168 network driver from realtek when I was using 3.1.0-rc4 but when I went to rc6, it stopped compiling. In order to get the r8169 driver to work, I had to add firmware to the /lib/firmware/rtl_nic directory. Got it from here: [https://github.com/mdamt/linux-firmware](https://github.com/mdamt/linux-firmware) download the tar.gz, extract using tar xzvf, then copy the files from rtl_nic to /lib/firmware/rtl_nic/. There were only 2 firmware files in there originally, after copying there were 6. That made the r8169 driver work.
```
sudo cp rtl_nic/* /lib/firmware/rtl_nic/
```
 Although it does sometimes go into lala land. A restart of auto eth0 on network-manager usually does the trick. For some reason I was also missing some radeon firmware. Get those from the same place.
```
sudo cp radeon/SUMO* /lib/firmware/radeon/
```

```
sudo update-initramfs -u
```

should say: 
> Generating /boot/initrd.img-3.1.0-rc6-01 
with no errors.

now edit the grub line:
sudo nano /etc/default/grub
change your GRUB_CMDLINE_LINUX line, remove the “nomodeset” and add the following.
```
GRUB_CMDLINE_LINUX="i915.i915_enable_rc6=1 pcie_aspm=force"
```
save
then do 
```
sudo update-grub
```
now reboot
```
sudo reboot now
```

On reboot You should now have Unity desktop and compiz working.  Glxgears will be pegged at 60 fps because of v-sync. Do this to make sure 3d/compiz is working:
```

$ glxinfo | grep version
server glx version string: 1.4
client glx version string: 1.4
GLX version: 1.4
OpenGL version string: 2.1 Mesa 7.10.2
OpenGL shading language version string: 1.20

$ glxinfo | grep direct
direct rendering: Yes

```
at this point if you want to add compiz effects, in Synaptic add compizconfig-settings-manager and add wobbly windows or whatever. Be careful because some stuff conflicts with Unity e.g. Desktop Cube. There are ways around this but I won't go into it here.

This may put the kernel in the “Previous kernels” sub menu in grub so watch the grub menu on reboot.
If it puts the record at the top of the grub2 menu or if you don't need to move it skip this section. If it puts the rc6 record in the sub menu and you want to move it to the front do this:
Grub2 - for whatever reason the new kernel is in the old kernel section of the menu. Download grub-customizer via this ppa.

```
sudo add-apt-repository ppa:danielrichter2007/grub-customizer
sudo apt-get update
sudo apt-get install grub-customizer
```

> GUI: Applications > System Tools > Grub Customizer

select the new kernel, use up arrow to move up. hit save.

On reboot, you  should have Brightness Controls using fn+F5 and fn+F6, power consumption should be way down (use powertop and see ACPI est power usage should be below 10W, also cat /proc/acpi/battery/BAT1/state), TTYs should work (ctrl+alt+F1-6), external display from laptop (not from PMD), suspend should work IF you have an external display attached to the laptop.

Note: with new kernel and sparse_irq but no laptop-mode-tools gettings about 10-11W. With Sparse_irq disabled getting ~10W and with laptop-mode-tools added goes to about +-9W
So you still have a few things remaining: Clickpad, WWAN, PMD Graphics, Fingerprint Reader.

Clickpad
Followed these instructions here: 
[http://bigbrovar.aoizora.org/index.php/2011/05/24/better-clickpad-support-for-ubuntu-11-04/](http://bigbrovar.aoizora.org/index.php/2011/05/24/better-clickpad-support-for-ubuntu-11-04/)
This worked. Now I have two finger scroll (Horizontal and Vertical), two finger right click, three finger middle click. Click and Drag is a pain as is highlighting text. Click and Drag you have to tap, tap and hold in the top bar of a window, then drag around. But you only have the size of the clickpad to move. If you pick your finger up you have to do it again. For highlighting text, I find if you click and hold in the middle of the clickpad (yeah, the middle actually clicks) then drag you can highlight text.
 
Fix WWAN
The wwan card is a Huawei EM680 but it also shows as a Gobi 3000.  For whatever reason it doesn't show up in network-manager. Must be too new or something. I have it currently running using wvdial and NOT network-manager.

Instructions here: [http://ubuntuforums.org/showthread.php?t=1796527](http://ubuntuforums.org/showthread.php?t=1796527)
Get driver source from here: [https://www.codeaurora.org/patches/quic/gobi/Gobi3000/](https://www.codeaurora.org/patches/quic/gobi/Gobi3000/)

Download the GobiNet and GobiSerial drivers. Not sure you need both, I only got the GobiSerial to work but it only takes a minute so might as well do both ;).  Then cp to src/ or whatever directory you are using to compile in, then  
```
tar xvzf GobiNet_2011-07-29-1026.tar.gz
tar xzvf GobiSerial_2011-07-29-1026.tar.gz
cd GobiNet
nano GobiUSBNet.c
Ctrl+W USB_DEV
```

Look for this:  USB_DEVICE( 0xXXXX, 0xXXXX )

Change the 0x05c6, 0x920c to what shows up in lsusb or lsusb -t or usb-devices mine shows like this in lsusb:

```
Bus 001 Device 006: ID 12d1:14f1 Huawei Technologies Co., Ltd.
```
So take the 12d1 for the first number and 14f1 for the second
so change it to look like this:
```
 USB_DEVICE( 0x12d1, 0x14f1 )
```

then
```
make
sudo make install
```

Do the same for GobiSerial
```
cd ../GobiSerial
nano GobiSerial.c
Ctrl + W USB_DEV

```
change this:
```
static struct usb_device_id GobiVIDPIDTable[] = 
{
   { USB_DEVICE( 0x05c6, 0x920c ) },   // Gobi 3000 QDL device
   { USB_DEVICE( 0x05c6, 0x920d ) },   // Gobi 3000 Composite Device
   { }                               // Terminating entry
};

```
to this
```
   { USB_DEVICE( 0x12d1, 0x14f1 ) },   // Gobi 3000 QDL device
   { USB_DEVICE( 0x12d1, 0x14f1 ) },   // Gobi 3000 Composite Device
```

then
```
make
sudo make install
```

Now install gnome-ppp
```
sudo apt-get install gnome-ppp wvdial
```
for AT&T in the US change /etc/wvdial.conf  to this:
```

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT+CGDCONT=1, "IP", "WAP.CINGULAR"
Modem Type = USB Modem
Baud = 460800
New PPPD = yes
Modem = /dev/ttyUSB0
ISDN = 0
Phone = *99#
Password = CINGULAR1
Username = WAP@CINGULARGPRS.COM
stupid mode = 1
```

also for gnome-ppp run as root: 
```
gksudo gnome-ppp
username: WAP@CINGULARGPRS.COM
password: CINGULAR1
check remember password
Phone number: *99#
Setup
Device: /dev/ttyUSB0
Type: USB Modem
Speed: 460800
Phone line: Tone
Volume: High
Init Strings: 
Add Init3
AT+CGDCONT=1, "IP", "WAP.CINGULAR"
Options
Stupid Mode check

```

So you can run gnome-ppp from the menu or from a terminal. In Unity, search for gnome-ppp and select. Or in terminal do gksudo gnome-ppp.

Ok weird thing, usually when gnome-ppp connects, it goes into the task bar. Apparently, this doesn't work with Unity... So best if you start it in a terminal with gksudo gnome-ppp.


Other stuff, install powertop ```
sudo apt-get install powertop
```. Install flash 11 for x86-64. I found a script that works here: [http://www.myscienceisbetter.info/install-native-64bit-flash-player-11-on-linux.html](http://www.myscienceisbetter.info/install-native-64bit-flash-player-11-on-linux.html) just copy the script in the page to a text document (gedit works), save as, name it something like installflash.sh, ```
chmod +x installflash.sh
./installflash.sh
``` just make sure that adobe hasn't updated the file name. As of this writing it is on rc1. Install laptop-mode-tools. I had a problem with it that if I had a usb mouse attached it would go to sleep in a couple of seconds. I fixed that by editing /etc/laptop-mode/conf.d/usb-autosuspend.conf and add usbhid to blacklist.

So with that, this is a very usable laptop. Super light super fast. Only thing that is really a problem now is the PMD graphics, Docking/Undocking and suspend/hibernate. It would be sweet to get that working. Suspend Hibernate isn't as big a deal as I can boot in linux in about 30 secs. Fingerprint reader, isn't that big a deal for me. Seems more of a pain than anything else. 

If you see any errors or if there are better ways to do this please let  me know and I can update this document.

Good Luck.
DoTheDog

---

### Post by tuukkah on 2011-09-30
I've installed the 11.10 Oneiric beta2 on an Sony VPCZ21S9E (256Gb SSD, 4Gb RAM, no optical drive or ATI GPU). Booted from a stick (press F11 to boot from USB) prepared with usb-creator-gtk and more or less everything worked nicely all the way up to Grub install which failed.

I booted from the stick again, and in a chroot was able to install grub and create the grub config. 

[s]
Now, the system boots but doesn't get past the splash screen. Last message says that CUPS started successfully. No console login is available.
[/s]
[B]
EDIT: What I missed first was that the installation didn't fully complete and I still needed to clean up:
[/B]
```

mv /sbin/initctl.REAL /sbin/initctl
mv /sbin/start-stop-daemon.REAL /sbin/start-stop-daemon

```

**After this the system boots without errors.**

[s]
Booting with the recovery option, I'm able to get the system running with the following commands (after installing gdm):

```

initctl.REAL start mountall
modprobe psmouse
initctl.REAL start gdm

```[/s]

I also see errors about LUNs, but these are probably harmless and go away if the card readers are disabled in BIOS.

What's more concerning is that the machine uses two 128Gb SSD in a SATA/fakeraid0 configuration. During boot I see an error like 
```

udev: /dev/dm-1: No such file or directory.

```In recovery console, I can see that the device file is there though. **EDIT: The message doesn't seem to matter. **[s]Maybe this error causes Upstart to wait for something related to the disks that never happens?[/s]

---

### Post by Lokiii on 2011-10-02
Thanks for a wonderful guide! 

I have a couple of questions though..

How is power consumption now compared to Windows? 
Does ethernet and USB2+3 work on the dock? If I understand correctly the dock works fine (except the graphics) if its connected before booting up?

Would be really nice to get suspend/hibernate working. Even though shutting down and booting up is quick, its still handy to be able to just shut down the lid and go. :)

---

### Post by tuukkah on 2011-10-02
> **Lokiii said:**
> 
Would be really nice to get suspend/hibernate working. Even though shutting down and booting up is quick, its still handy to be able to just shut down the lid and go. :)

In Oneiric Beta2, suspend seems to be working fine. Hibernate has some issues: another, empty battery appears; screen brightness stops adjusting etc.

---

### Post by dothedog on 2011-10-03
lokii, So yeah, the PMD only works for me if it is plugged in on boot. I don't have a USB3 device, but it does work with usb2 mice, disks etc. The ethernet card also works. And no I haven't gotten the ATI graphics working. I get a "bios not found" in dmesg. As for vs. Windows, good question, I haven't tried running it all the way down in Winders yet...

tuukah, so you have suspend working? The only problem I have is that it does come back up but just nothing on the screen. i can ctrl+alt+f2, blind log in and do a sudo reboot now and have it work. If I have a monitor and plug it in on resume it works to the external monitor. So all we need to figure out is how to get it to resume to the laptop screen...

for the brightness buttons etc. did you try applying the vaio patch and compiling the 3.1.0-rc6 kernel?

DoTheDog

---

### Post by Manolo35 on 2011-10-10
Hello guys,

I'm trying to install Ubuntu on my vaio Z2 and I have the problem you mentioned about grub refusing to install, could you give me more details about how to install it manually ? 

Thanks!

M.

---

### Post by Gibb on 2011-11-03
hey guys!

I'm also on the verge of buying the new Z21. Are there still any major issues with it running linux?

Also, like the poster above, I would like a step-by-step setup for the grub part as I'm not very experienced with it (you have to drop out of the installer?).

TIA!

---

### Post by gyhor on 2012-01-02
Thank you for the helpful information.

I downloaded and compiled kernel 3.2 RC7. First i had to enable the intel wireless card in menuconfig.


[LIST]
[*]The F-keys (F3,F4,F5,F6,F712) are working.
[*]Suspend is working
[*]Audio is working
[*]Wlan is working
[*]Intel gfx with 3d is working
[*]clickpad is working, followed your information
[*]PMD is only working if it is connect before booting
[*]PMD Network, USB, CD is working
[*]VGA direct from the notebook is working
[*]ASSIST and WEB Key are working
[/LIST]
Not working:

[LIST]
[*]PMD gfx Card is not working!
[*]Key "VAIO" is not working (no events with xev)
[/LIST]
I tried the whole day to get ati fglrx driver to work. But no success :(


Anyone else luckier?


regards
gyhor

---

### Post by gyhor on 2012-01-02
grub commandline:

```
GRUB_CMDLINE_LINUX="i915.i915_enable_rc6=1 pcie_aspm=force"

$ glxinfo|grep version
server glx version string: 1.4
client glx version string: 1.4
GLX version: 1.4
OpenGL version string: 2.1 Mesa 7.11
OpenGL shading language version string: 1.20

$ glxinfo|grep direct
direct rendering: Yes
```

---

### Post by gyhor on 2012-01-03
further information/bugs about the external graphic card:

[LIST]
[*][https://bugs.freedesktop.org/show_bug.cgi?id=41265](https://bugs.freedesktop.org/show_bug.cgi?id=41265)
[*][https://bugs.freedesktop.org/show_bug.cgi?id=40576](https://bugs.freedesktop.org/show_bug.cgi?id=40576)
[*][http://thread.gmane.org/gmane.linux.usb.general/55899](http://thread.gmane.org/gmane.linux.usb.general/55899)
[/LIST]

---

### Post by maxor91 on 2012-02-02
Has anyone tried to install 10.10 on the Z2? I'm having trouble getting the GUI to show up as well as getting WiFi to work. Please help! Thanks.

---

### Post by gyhor on 2012-02-03
> **maxor91 said:**
> Has anyone tried to install 10.10 on the Z2? I'm having trouble getting the GUI to show up as well as getting WiFi to work. Please help! Thanks.
Sorry, i only tried it with ubuntu 10.10. 
But the installation should work with the description in the first posts. You have to install a new kernel (3.2 for example), that should be enough.

regards
gyhor

---

### Post by bazilio1 on 2012-02-08
I made a little hack to get PMD working when it inserted.

/etc/udev/rules.d/41-dock.rules
```

KERNEL=="dock.0", RUN+="/usr/local/sbin/redock.sh"

```

/usr/local/sbin/redock.sh
```

#!/bin/bash

DEVICES="16:00.0 16:00.1 19:00.0 1a:00.0 1b:00.0"

sleep 0.1

DOCKED=$(cat /sys/devices/platform/dock.0/docked)
[ "$(cat /tmp/dockstate.txt)" == "$DOCKED" ] && exit 0

for i in $DEVICES; do
	echo 1 > /sys/bus/pci/devices/0000:$i/remove
done
sleep 0.1
echo 1 > /sys/bus/pci/rescan

echo "$DOCKED" > /tmp/dockstate.txt

```
chmod +x /usr/local/sbin/redock.sh

Put in DEVICES= string pci-ids of your PMD devices (you can get it using lspci).

[edit]
One more part - to make it not to panic when booted without dock.

/etc/modprobe.d/blacklist-radeon.conf
```

blacklist radeon

```

---

### Post by gyhor on 2012-02-08
wow! redocking is working!
Nice work, bazilio1

---

### Post by arune on 2012-04-11
> **gyhor said:**
> 
I downloaded and compiled kernel 3.2 RC7. First i had to enable the intel wireless card in menuconfig.


[LIST]
[*]The F-keys (F3,F4,F5,F6,F712) are working.
[*]Suspend is working
[*]Audio is working
[*]Wlan is working
[*]Intel gfx with 3d is working
[*]clickpad is working, followed your information
[*]PMD is only working if it is connect before booting
[*]PMD Network, USB, CD is working
[*]VGA direct from the notebook is working
[*]ASSIST and WEB Key are working
[/LIST]
...

gyhor

Did you need to use the patch to get all things working or did it work out of the box with 3.2 (except for menuconfig for intel wireless)?
Seems like the patch was written for 3.0.4 which seems a bit old :)

Anyone got a more detailed guide on how to deal with grub-issues during installation?

I'm about to buy Z23 and install 12.04 in a few weeks.

Thanks

---

### Post by gyhor on 2012-04-12
> **arune said:**
> Did you need to use the patch to get all things working or did it work out of the box with 3.2 (except for menuconfig for intel wireless)?
Seems like the patch was written for 3.0.4 which seems a bit old :)


Nope. No patches! Just compiled the kernel with the intel patch.
But beware, the graphic card in the docking station is not working.

---

### Post by MarcoDiMarco on 2012-08-06
> **bazilio1 said:**
> I made a little hack to get PMD working when it inserted.

/etc/udev/rules.d/41-dock.rules
```

KERNEL=="dock.0", RUN+="/usr/local/sbin/redock.sh"

```/usr/local/sbin/redock.sh
```

#!/bin/bash

DEVICES="16:00.0 16:00.1 19:00.0 1a:00.0 1b:00.0"

sleep 0.1

DOCKED=$(cat /sys/devices/platform/dock.0/docked)
[ "$(cat /tmp/dockstate.txt)" == "$DOCKED" ] && exit 0

for i in $DEVICES; do
    echo 1 > /sys/bus/pci/devices/0000:$i/remove
done
sleep 0.1
echo 1 > /sys/bus/pci/rescan

echo "$DOCKED" > /tmp/dockstate.txt

```chmod +x /usr/local/sbin/redock.sh

Put in DEVICES= string pci-ids of your PMD devices (you can get it using lspci).

[edit]
One more part - to make it not to panic when booted without dock.

/etc/modprobe.d/blacklist-radeon.conf
```

blacklist radeon

```

Hi,

Im trying to add this script to my device but i dont know which devices id's i must put in DEVICES. How do i recognize these id's?
Also, do i have to connect the docking station as well and then grab those devices as well ?

I hope someone could help me for i dont know much about this subject. 

Many thanks in advance!

---

### Post by bazilio1 on 2012-08-10
I updated script so it won't need device pci ids and will handle devices better.

```
#!/bin/bash

sleep 1

DOCKED=$(cat /sys/devices/platform/dock.0/docked)
[ "$(cat /tmp/dockstate.txt)" == "$DOCKED" ] && exit 0

if [ "$DOCKED" == "1" ]; then
	echo 1 > /sys/bus/pci/rescan
else
	/sbin/modprobe acpiphp
	sleep 0.1
	echo 0 > /sys/bus/pci/slots/1/power
	sleep 0.1
	/sbin/rmmod acpiphp
fi

echo "$DOCKED" > /tmp/dockstate.txt


```

---

### Post by gyhor on 2012-08-17
The external graphic card is now working:

[https://bugs.freedesktop.org/show_bug.cgi?id=41265](https://bugs.freedesktop.org/show_bug.cgi?id=41265)

:smile:

---

### Post by bazilio1 on 2012-08-24
> **gyhor said:**
> The external graphic card is now working

Could you write a short howto for lazy ones? And also does it works well with hotplugging pmd?

---

### Post by dothedog on 2012-09-11
Bazilio,
Yeah, I posted a new howto here: [http://ubuntuforums.org/showthread.php?t=2055656](http://ubuntuforums.org/showthread.php?t=2055656)

Unfortunately, I tried it with your script and it didn't seem to work. If you can get it to work please post on the linked thread.

Thanks,
Rob

---

### Post by user10 on 2013-06-14
Hello everybody,

I would like to reopen this discussion because the hotplug is working only with the ubuntu kernel 3.5 but with the 3.7 and 3.8 ubuntu kernels is not working again. it doesn't work also with the 3.5 vanilla. 

I have analyzed the patch but I'm not able to understand which is the part related to this issue.

Do you have also the same problem?

---

