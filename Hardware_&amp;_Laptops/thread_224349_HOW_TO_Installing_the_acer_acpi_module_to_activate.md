---
title: "HOW TO: Installing the acer_acpi module to activate wireless on Acer laptops"
date: 2006-07-27
forum: Hardware &amp; Laptops
---

### Post by ovimunt on 2006-07-27
***Last updated on 29/07/2006 21:04 GMT.***

**ATTENTION: This HOW TO covers ONLY the installation of the *acer_acpi* module and NOT of the wireless adapter drivers.**

Before you can go ahead and install the ***acer_acpi*** module you need to make sure you have some other tools installed.
```

sudo aptitude update
sudo aptitude install build-essential

```

***UPDATED:***
You'll also need the linux headers:
```

sudo aptitude install linux-headers-$(uname -r)

```
***END OF UPDATE***

Once this is done you can go ahead and install the ***acer_acpi***.
First you should create a folder to keep all your downloads in one place.
```

mkdir /home/USER_NAME/download

```
Where USER_NAME is your actual user name.

Now go to the new folder
```

cd /home/USER_NAME/download

```

and download and install the package:
```

wget http://www.archernar.co.uk/acer_acpi/acer_acpi-0.3.tar.gz
tar zxvf acer_acpi-0.3.tar.gz
cd acer_acpi-0.3
make
sudo make install
cd ../..

```

Load the acer_acpi into memory and activate the wireless:
```

su
modprobe acer_acpi
chmod 777 /proc/acpi/acer/wireless
echo "enabled: 1">/proc/acpi/acer/wireless
exit

```

And check if it worked:
```

dmesg | grep acer_acpi

```

You should get some output like this:
```

[17179594.992000] acer_acpi: Acer Laptop ACPI Extras version 0.3
[17179595.000000] acer_acpi: Wireless value 1

```

Right, this might have worked for now but you need to load and activate ***acer_acpi*** every time your computer starts. 
For this you can write a little start up script so you don't have to do it manually each and every time.

[b]ATTENTION!
For Gnome type:[/b]
```

sudo gedit /etc/init.d/acer_acpi_wireless_enable

```
**Or if you're running KDE type:**
```

sudo kate /etc/init.d/acer_acpi_wireless_enable

```

Paste the following code and save:
```

#!/bin/sh

case "$1" in

        start|"")

                modprobe acer_acpi

                chmod 777 /proc/acpi/acer/wireless

                echo "enabled: 1" >/proc/acpi/acer/wireless

                ;;

        stop)

                echo "enabled: 0" >/proc/acpi/acer/wireless

                modprobe -r acer_acpi

                ;;

esac

```

Make the file executable and add it to the appropiate linux run levels.
**ATTENTION! Don't miss ANY of the characters in the following lines, especialy the dots in the third line!**
```

su
chmod 755 /etc/init.d/acer_acpi_wireless_enable
update-rc.d acer_acpi_wireless_enable start 39 S . start 34 0 6 .
exit

```

Now check if it worked:

```

ls /etc/rcS.d/S39acer-acpi-wireless-enable
ls /etc/rc0.d/S34acer-acpi-wireless-enable
ls /etc/rc6.d/S34acer-acpi-wireless-enable

```

If you get any ***No such file or directory*** messages then something must have gone wrong during the last couple of steps but your ***acer_acpi*** is still installed and can be started manually if needed.

If you didn't get any error messages everything should be up and running. You can now restart the computer and, if you have already installed the wireless drivers, your wireless adapter should work fine and be ready to configure.

---

### Post by hizaguchi on 2006-07-28
Any chance this will fix Acers that don't suspend?  Or is it just an addon to enable the wireless and bluetooth switches?

---

### Post by ovimunt on 2006-07-28
Nope, I'm afraid this won't fix Acers that don't suspend.

---

### Post by reckentimo on 2006-08-17
Works also for activating newer Acer built-in bluetooth device!
Great! Thanks!

---

### Post by sabmann on 2006-11-14
you made some typos:

```

ls /etc/rcS.d/S39acer-acpi-wireless-enable
ls /etc/rc0.d/S34acer-acpi-wireless-enable
ls /etc/rc6.d/S34acer-acpi-wireless-enable

```

should be

```

ls /etc/rcS.d/S39acer_acpi_wireless_enable
ls /etc/rc0.d/S34acer_acpi_wireless_enable
ls /etc/rc6.d/S34acer_acpi_wireless_enable

```

---

### Post by Jonq on 2006-11-17
when I do Sudo modprobe acer_acpi

I get 

```

FATAL: Error inserting acer_acpi (/lib/modules/2.6.17-10-generic/extra/acer_acpi.ko): No such device

```

anybody know why ? :-k

---

### Post by Jonq on 2006-11-19
so no one knows how to correct this problem? this sucks ](*,) [-(

---

### Post by encompass on 2006-12-13
Try the instructions from the start... that works for me. looks like it didn't compile.

---

### Post by sarevok on 2007-01-09
You have acpi disabled, go to /boot/grub/menu.lst and remove acpi off from the kernel you are loading, save, reboot and now it'll work.

---

### Post by Apples on 2007-01-12
> **Jonq said:**
> when I do Sudo modprobe acer_acpi

I get 

```

FATAL: Error inserting acer_acpi (/lib/modules/2.6.17-10-generic/extra/acer_acpi.ko): No such device

```

anybody know why ? :-k

I'm getting the very same error, and no one seems to know how to fix it!

---

### Post by bartoknagyjanos on 2007-01-14
> **Apples said:**
> I'm getting the very same error, and no one seems to know how to fix it!

the very same problem :(

acer travelmate 2492nWLMi, bc4318, ubuntu 6.06

---

### Post by HailandKill on 2007-03-04
After typing

> # sudo modprobe acer_acpi

and getting the "Invalid" error, dmesg is reporting:

```
acer_acpi: version magic '2.6.15-27-amd64-generic SMP preempt gcc-3.4' should be '2.6.15-27-amd64-generic SMP preempt gcc-4.0'
```

I'm not really sure what this means. But sure looks like a clue! Anyone?

Sorry to repeat what I said in the other thread under the same title. :(

---

### Post by finite9 on 2007-04-27
ive had no issues building acer_acpi on Dapper Drake, but since I upgraded to Fesity, I had issues making it with 'make'.  I read the INSTALL file and issues 'make acer_acpi.ko' instead, but when doing 'sudo make install' it seems to install direct under (lib/modules/extra and not under the current kernel.

I do not know if this has any effect, but I cannot modprobe the module, I get FATAL Module not found when doing sudo modprobe acer_acpi.

Any ideas?

---

### Post by finite9 on 2007-04-27
answer to my own question...

acer_acpi-0.4 has been released which builds on later kernels including Feisty.

---

### Post by bren on 2007-06-06
Excellent HOWTO - works for me [on my Fujitsu Siemens Amilo A1650 laptop]
Post #14 is essential for Feisty
You can find the 0.4 version here
[http://public.www.planetmirror.com/pub/gentoo/distfiles/acer_acpi-0.4.tar.gz](http://public.www.planetmirror.com/pub/gentoo/distfiles/acer_acpi-0.4.tar.gz)

Does anyone know how to go one step furher...
What is the correct command(s) to turn the wireless back off again (and to turn on)
I thought I could put these in a mini script 
And put the script in a launcher on the desktop or panel

I'm learning slowly.... :)

bren

bren

---

### Post by Mr. Swiveller on 2007-06-23
[EDIT:WHAT CAUSED MY PROBLEM WAS THAT I HAD NOT BLACKLISTED THE LINUX-NATIVE DRIVER MODULE, CAUSING THE NDIS DRIVER NOT TO LOAD. EVERYTHING WORKS NOW!]


Hello everyone -

Thanks largely to this post, I have been able to compile and install acer_acpi (version 0.5) on my Acer Aspire 5020 laptop. Yet despite going through all of the steps without getting any error messages, the wireless button won't activate. The led doesn't light up, and Kubuntu 7.04 refuses to connect to wireless networks.

When I type 'dmesg | grep acer_acpi', I get the following message -

[   97.132485] acer_acpi: Acer Laptop ACPI Extras version 0.5
[   97.140500] acer_acpi: Wireless value 0
[   97.158454] acer_acpi: Wireless value 1
[  105.987849] acer_acpi: Wireless value 1

Does the second line mean that my wireless is somehow disabled? If so, how might I activate it? Does anyone know? And, if not, does anyone have any ideas as to what might be causing my problem?

Cheers & thanks,

Swiveller

---

### Post by jonttix on 2007-07-01
After I have installed acer_acpi some programs gets really slow! And the network under administration does not open at all!! Do anybody have an explanation to this?

---

### Post by coenox on 2007-07-11
Ik get jammed after 'Make' .

I use the version 6 of the acer_acpi, but get following:


coenox@ntbkcoen:~/download/acer_acpi-0.6$ make
No support for 2.4 series kernels


I use feisty fawn and I am abslotuly positive that I have the 2.6 kernel. Why do I get this message ?

---

### Post by bren on 2007-07-11
[http://code.google.com/p/aceracpi/issues/list](http://code.google.com/p/aceracpi/issues/list)

bug report for version 6 if you are using latest kernel....maybe try version 5....

bren

---

### Post by Styx on 2007-07-12
Note that the link to the acer_acpi module changed from the one in the howto. 
```

wget http://aceracpi.googlecode.com/files/acer_acpi-0.6.tar.bz2
```

Also the version is newer (as you can see). So change that as well wenn you follow the how to.

There is a new version on line this one should work for feisty. It dose for me

---

### Post by notsteve on 2007-07-20
hi everything goes good until i try to load acer_acpi

when I type "modprobe acer_acpi", i get this response:
FATAL: Error inserting acer_acpi (/lib/modules/2.6.20-15-generic/extra/acer_acpi.ko): Operation not permitted

anyone got any ideas to the problem

---

### Post by bren on 2007-07-20
try prefixing by sudo?

bren

---

### Post by kinson on 2007-09-02
Hi guys,

I'm using Ubuntu 7.04 i386 version and downloaded the acer_acpi-0.8.tar.bz2 from the google code page, and extracted it (right click and "extract"...hope that doesn't make a difference).

after I've browsed into the folder and try to issue a "make" commad, I get the following error:

```

kinson@kinTurion:~$ cd acer_acpi-0.8/
kinson@kinTurion:~/acer_acpi-0.8$ ls
acer_acpi.c  AUTHORS  ChangeLog  COPYING  INSTALL  Makefile  NEWS  README
kinson@kinTurion:~/acer_acpi-0.8$ make
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/kinson/acer_acpi-0.8 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /home/kinson/acer_acpi-0.8/acer_acpi.o
/home/kinson/acer_acpi-0.8/acer_acpi.c: In function ‘update_bl_status’:
/home/kinson/acer_acpi-0.8/acer_acpi.c:1217: error: request for member ‘brightness’ in something not a structure or union
/home/kinson/acer_acpi-0.8/acer_acpi.c: At top level:
/home/kinson/acer_acpi-0.8/acer_acpi.c:1221: error: variable ‘acer_backlight_ops’ has initializer but incomplete type
/home/kinson/acer_acpi-0.8/acer_acpi.c:1222: error: unknown field ‘get_brightness’ specified in initializer
/home/kinson/acer_acpi-0.8/acer_acpi.c:1222: warning: excess elements in struct initializer
/home/kinson/acer_acpi-0.8/acer_acpi.c:1222: warning: (near initialization for ‘acer_backlight_ops’)
/home/kinson/acer_acpi-0.8/acer_acpi.c:1223: error: unknown field ‘update_status’ specified in initializer
/home/kinson/acer_acpi-0.8/acer_acpi.c:1223: warning: excess elements in struct initializer
/home/kinson/acer_acpi-0.8/acer_acpi.c:1223: warning: (near initialization for ‘acer_backlight_ops’)
/home/kinson/acer_acpi-0.8/acer_acpi.c: In function ‘acer_backlight_init’:
/home/kinson/acer_acpi-0.8/acer_acpi.c:1231: warning: passing argument 4 of ‘backlight_device_register’ from incompatible pointer type
/home/kinson/acer_acpi-0.8/acer_acpi.c:1240: error: request for member ‘max_brightness’ in something not a structure or union
/home/kinson/acer_acpi-0.8/acer_acpi.c:1241: error: request for member ‘brightness’ in something not a structure or union
/home/kinson/acer_acpi-0.8/acer_acpi.c:1242: warning: implicit declaration of function ‘backlight_update_status’
/home/kinson/acer_acpi-0.8/acer_acpi.c: At top level:
/home/kinson/acer_acpi-0.8/acer_acpi.c:1480: warning: initialization from incompatible pointer type
/home/kinson/acer_acpi-0.8/acer_acpi.c:1481: warning: initialization from incompatible pointer type
make[2]: *** [/home/kinson/acer_acpi-0.8/acer_acpi.o] Error 1
make[1]: *** [_module_/home/kinson/acer_acpi-0.8] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [acer_acpi.ko] Error 2
kinson@kinTurion:~/acer_acpi-0.8$ 

```

I get similar errors when I try "make acer_acpi.ko" and "make acer.acpi.o". Any help would be greatly appreciated, as I really love Ubuntu :)

btw, in the first page, the command 
```

sudo aptitude install linux-headers-$(uname -r)
```
I don't have to replace "uname" with username or anything right?

the output of it is:
```

kinson@kinTurion:~/acer_acpi-0.8$ sudo aptitude install linux-headers-$(uname -r)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages have been automatically kept back:
  linux-image-generic linux-restricted-modules-common 
  linux-restricted-modules-generic 
The following packages have been kept back:
  app-install-data app-install-data-commercial apport apport-gtk bind9-host 
  capplets-data dbus dbus-1-utils dnsutils evolution-data-server 
  evolution-data-server-common file firefox firefox-gnome-support gimp 
  gimp-data gimp-python gnome-app-install gnome-control-center gnome-panel 
  gnome-panel-data hwdb-client-common hwdb-client-gnome iptables 
  language-pack-en language-pack-gnome-en libbind9-0 libcamel1.2-10 
  libcurl3 libdbus-1-3 libdns22 libebook1.2-9 libecal1.2-7 
  libedata-book1.2-2 libedata-cal1.2-6 libedataserver1.2-9 
  libedataserverui1.2-8 libegroupwise1.2-13 libexchange-storage1.2-3 
  libexif12 libfreetype6 libgimp2.0 libgl1-mesa-dri libgl1-mesa-glx 
  libglu1-mesa libgnome-window-settings1 libisc11 libisccc0 libisccfg1 
  libjasper-1.701-1 libkrb53 liblwres9 libmagic1 libmagick9 libmetacity0 
  libnspr4 libnss3 libpanel-applet2-0 libpng12-0 libpoppler1 
  libpoppler1-glib libslab0 libsmbclient libvorbis0a libvorbisenc2 
  libvorbisfile3 libwrap0 linux-generic linux-headers-generic mesa-utils 
  metacity metacity-common openoffice.org openoffice.org-base 
  openoffice.org-calc openoffice.org-common openoffice.org-core 
  openoffice.org-draw openoffice.org-evolution 
  openoffice.org-filter-mobiledev openoffice.org-gnome openoffice.org-gtk 
  openoffice.org-impress openoffice.org-java-common openoffice.org-math 
  openoffice.org-style-human openoffice.org-writer poppler-utils python 
  python-apport python-gdbm python-launchpad-bugs python-minimal 
  python-problem-report python-uno python2.5 python2.5-minimal rdesktop 
  rsync samba-common smbclient tar tcpdump ttf-opensymbol tzdata 
  unattended-upgrades update-manager update-manager-core vim-common 
  vim-tiny xscreensaver-data xscreensaver-gl 
0 packages upgraded, 0 newly installed, 0 to remove and 115 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
kinson@kinTurion:~/acer_acpi-0.8$ 

```

It kinda seems that nothing is installed.

Thanks for any help in advance ! :) Really hope I can get this working :)

Cheers,
Kinson

---

### Post by kaar3l on 2007-09-03
YEEEHAAAA:guitar::popcorn:

got it working

This loads acerhk without that stupid error. :D
```
sudo modprobe acerhk usedritek=1 autowlan=1 force_series=290
```

Wireless on:
```
echo 1 > /proc/driver/acerhk/wirelessled
```
Wireless off:
```
echo 0 > /proc/driver/acerhk/wirelessled
```
Bluetooth on:
```
echo 1 > /proc/driver/acerhk/blueled
```
Bluetooth off:
```
echo 0 > /proc/driver/acerhk/blueled
```

Now i must do it with some hotkeys, but that should be easy.:P

---

### Post by GordonMorgan on 2007-09-29
Hi i get the same problem as others here when trying to issue command:

Sudo modprobe [COLOR="Red"]acer_acpi[/COLOR]

```
FATAL: Error inserting acer_acpi (/lib/modules/2.6.20-16-generic/extra/acer_acpi.ko): No such device
```

I have tried a suggested fix

"You have acpi disabled, go to /boot/grub/menu.lst and remove acpi off from the kernel you are loading, save, reboot and now it'll work"

but i dont have any mention of acpi in the menu.lst file, so saving and rebooting is kind of moot here (although i tried it anyway). I also tried:

sudo make acer_acpi.ko 

which i found on another how to but get this error.

```
make: *** No rule to make target `acer_acpi.ko'. Stop.
```

I hope someone can help me as ive spent the best part of two weeks getting compiz to work ok-ish and the best part of 3 days trying to enable my wireless network.

---

### Post by snot on 2007-10-09
When I try make in the acer_acpi directory I'm getting a lot of errors starting with:
```

/home/snot/acer_acpi-0.9.1/acer_acpi.c:68:22: error: linux/io.h: No such file or  directory

```
I've followed all the steps including installing the linux headers. Any ideas?

---

### Post by ballboy on 2007-10-19
Acer_Acpi is now in the repositories so no more compiling required :) !!

You will need to add the mumblyworld repository:

Go to [http://code.google.com/p/acer-acpi-deb/](http://code.google.com/p/acer-acpi-deb/) for instructions.

---

### Post by snot on 2007-10-19
> **ballboy said:**
> Acer_Acpi is now in the repositories so no more compiling required :) !!



and works like charm!!  \\:D/

---

### Post by Bashorings on 2007-10-25
I installed Gutsy Gibbon on my FSC Amilo A1655G, yesterday.
It alread has the acer_acpi installed, but now I don't know how to go on. I also installed the driver for my wireless lan device using ndiswrapper.
What's the next step to turn that damn wlan on?

Please help...didn't sleep... :confused:

---

### Post by bren on 2007-10-25
the link below is for 32 bit feisty but might be worth investigating for gutsy

[http://www.amilo-forum.com/topic,1023,-Installation-script-for-Amilo-A1650G-Ubuntu-32bit.html](http://www.amilo-forum.com/topic,1023,-Installation-script-for-Amilo-A1650G-Ubuntu-32bit.html)

let us know how you get on

bren

---

### Post by mathenge on 2008-04-12
I have an Acer Aspire 5040 (Aspire 5044WLMi).

Working from a live-cd I was able to get wireless working. I used my wired connection for the downloads. I'm now typing this from the live-cd environment using the wireless connection only. The live-cd was Gutsy Gibbon (7.10).

I followed the steps except I downloaded the acer_acpi module from [http://code.google.com/p/aceracpi/](http://code.google.com/p/aceracpi/). The file is: acer_acpi-0.11.2.tar.bz2

Once I enabled the card with the command: 

sudo echo 1 > /proc/acpi/acer/wireless

The led came on, however, the networking tools still didn't pick it up. I restarted the network but still the card couldn't be seen.

I rebooted the live-cd. Guess what, the LED stayed on.

So when the live-cd environment was restored, so was my wireless connection. WITHOUT HAVING TO DO ANYTHING AT ALL.

The situation (at least for me) is much better in Hardy Heron (8.04) which will be released on April 24th,2008 (12 days from today - April 12 - according to [www.ubuntu.com](www.ubuntu.com)).

The live-cd for Hardy launches and detects everything but the wireless card. However, it does load all the restricted drivers for acer. Only one step remains to get wireless working. Type in the following commands:

sudo chmod 777 /proc/acpi/acer/wireless
sudo echo 1 > /proc/acpi/acer/wireless

After the second command, the LED comes on and you can use the network manager to configure the card. In Ubuntu that would mean typing: sudo /usr/sbin/NetworkManager.

So for me, I'm going to leave Windows XP on this Acer till the official release comes out. I'll be one of the first to download it. Meanwhile, I'll be backing up.

---

### Post by cathectic on 2008-04-13
The rfkill switch for wireless only will persist across a reboot on Acer laptops. If you switch the system off rather than reboot, don't expect this to happen :)

You can also see this effect if you enable the wireless in Windows and then reboot into Linux.

---

### Post by frankfarmer on 2008-05-23
Everything was going really well until i tried:

wget [http://www.archernar.co.uk/acer_acpi/acer_acpi-0.3.tar.gz](http://www.archernar.co.uk/acer_acpi/acer_acpi-0.3.tar.gz)
tar zxvf acer_acpi-0.3.tar.gz

then i got this error message:

Resolving [www.archernar.co.uk](www.archernar.co.uk)... failed: Name or service not known.

im very new to ubuntu im using 8.04 hardy x86_64 and having major issues getting the wifi working on my fujitsu siemens amilo a1655g laptop i even bought a new mini pci wifi card (Atheros AR5212/AR5213) and then came to realise that the problem wasnt the card it was the pc having those annoying buttons to activate and disable wifi!!!

if the link above is broken can somone let me know a working link or perhaps give me the answer for getting the button working?

i also found:

[http://damagedspline.blogspot.com/2007/02/fsc-amilo-a1650g-ubuntu-edgy-32bit-how.html](http://damagedspline.blogspot.com/2007/02/fsc-amilo-a1650g-ubuntu-edgy-32bit-how.html)

and followed the guide for installing acerhk but got stumped on how to complile acerhk.ko etc :S 

any help is very much apreciated!

many thanks in advance :)

---

### Post by frankfarmer on 2008-05-23
ok i didnt notice there were 4 pages here! lol used the updated link for the acer_acpi but its still not working i followed the instructions to the end. whats annoying is im using a cheap usb dongle to get online and it works fine but only does the computer tell me the atheros wificard exists when the usb is plugged in but when unplugged it shows nothing??? if anyone wants to send me an idiots guide to setting this up it would be much appreciated! see my last post for os and hardware. i really dont wanna go back to windows on this computer!

many thanks

---

### Post by Dcox on 2008-06-28
Hi!

trying to install the latest Ubuntu to my Acer 5021 WLMI.
Could someone please help me out installing the wireless card/button ?

I've done the following : 

- Had to disable acpi because of installation crash
- sudo apt-get install bcm43xx-fwcutter
- added the wireless credentials (WPA-TKIP) to the wirless manager

> no wireless connection :(

Debug : 
I noticed acer_acpi is installed, but I cannot echo 1 to it ... it says : write error : invalid argument.



Ok this works! Had to enable the restricted driver!!

However, every 2 minutes the connection dies and re-associates! :(

---

### Post by MindRiot101 on 2008-07-05
I had some troubles getting this to work. Ubuntu 8.04 comes with acer-acpi loaded by default so i didn't need most of this guide, but when it came to activating my wireless card a different problem arose.

At the stage:
```

echo "enabled: 1">/proc/acpi/acer/wireless
```

i found that even as superuser the file could not be written, and i had to use ```
init 1
``` to be able to write to the file. 

After this the wireless worked.

Thank you for pointing me in the right direction

---

