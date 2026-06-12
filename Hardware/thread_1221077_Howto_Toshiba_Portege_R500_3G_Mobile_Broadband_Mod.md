---
title: "Howto: Toshiba Portege R500 3G Mobile Broadband Modem"
date: 2009-07-23
forum: Hardware
---

### Post by hamidaddin on 2009-07-23
[SIZE=3]**[COLOR=Red]Update 5: [/COLOR]**[/SIZE][COLOR=Red][SIZE=2]Just upgraded to Ubuntu 12.04 (Precise Pangolin). The old patches are not working anymore for 2.6.35-32-generic kernel (and probably following versions). Using the patch here ([http://schwieters.org/toshset/toshiba_acpi-current.patch](http://schwieters.org/toshset/toshiba_acpi-current.patch)) and the method of recompilation in "Update 2" below, I've recompiled the toshiba_apci module, and it's attached here as "toshiba_acpi.ko.patched4.zip"[/COLOR][/SIZE]

[SIZE=3]**[COLOR=Red]Update 4: [/COLOR]**[/SIZE][COLOR=Red][SIZE=2]The second attached toshiba_apci patch is not working anymore for 2.6.35-32-generic kernel (and probably following versions). I've found a fixed patch here: [http://schwieters.org/pipermail/toshset_schwieters.org/2011-January/000035.html](http://schwieters.org/pipermail/toshset_schwieters.org/2011-January/000035.html) and I've recompiled the toshiba_apci module, using the same method explained in Update2 below, and it's attached here as "toshiba_acpi.ko.patched3.zip"[/COLOR][/SIZE]

If you would like to do the recompilation yourself, you can follow the steps in Update 2 below but you will need to change step 3 as follows:
First, download the attached toshiba_acpi_2.36.patch.txt then copy it to /usr/src/toshiba_acpi-current.patch

[SIZE=2][COLOR=Black]
3) [/COLOR][/SIZE]```
sudo cp <DOWNLOADED PATCH FILE LOCATION>/toshiba_acpi_2.36.patch.txt /usr/src/toshiba_acpi-current.patch
```

Then continue with steps 4 onward in Update 2.

[SIZE=3]**[COLOR=Red]Update 3: [/COLOR]**[/SIZE][COLOR=Red][SIZE=2]The first attached toshiba_apci patch is not working anymore for 2.6.35-30-generic kernel (and probably following versions). I've recompiled the toshiba_apci module, using the same method explained in Update2 below, and it's attached here as "toshiba_acpi.ko.patched2.zip"[/COLOR][/SIZE]


[SIZE=3]**[COLOR=Red]Update 2: [/COLOR]**[COLOR=Red][SIZE=2]The modem was supported in [/SIZE][/COLOR][/SIZE][COLOR=Red] Ubuntu 9.10 Karmic Koala and [/COLOR][COLOR=Red] Ubuntu 10.04 Lucid Lynx. Unfortunately, in [/COLOR][COLOR=Red] Ubuntu 10.10 Maverick Meerkat[/COLOR][SIZE=3][COLOR=Red] [SIZE=2]the support was dropped from kernel 2.6.35-25-generic by the team working on drive toshiba_apci (More details here: [https://bugs.launchpad.net/ubuntu/+source/toshset/+bug/644898](https://bugs.launchpad.net/ubuntu/+source/toshset/+bug/644898))

[COLOR=Black]From that post Tomas Orgis says:
[/COLOR][/SIZE][/COLOR][/SIZE]> I see that the toshiba_acpi -dev patch has been intentionally dropped, see [https://lists.ubuntu.com/archives/kernel-team/2010-June/011112.html](https://lists.ubuntu.com/archives/kernel-team/2010-June/011112.html) . Andy wrote:
 Quote: I therefore suggest we drop this patch and see if anyone notices.
 Well, I do notice. There is no way anymore to disable the backlight  on this nice transflective screen -- or is there an alternative to  toshset yet? Please re-integrate that [SIZE=2][COLOR=Black]patch.[/COLOR][/SIZE]

        
[SIZE=2][COLOR=Black]
[/COLOR][/SIZE][SIZE=3][COLOR=Red][SIZE=2][COLOR=Black]
The solution to this is to apply a patch to toshiba_acpi and recompile the driver as explained below (this is taken from the link above by Mark van den Berg and Mark Crompton):
[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=2][COLOR=DarkOliveGreen][B]
Long Solution:[/B][/COLOR][/SIZE]
[SIZE=3][COLOR=Red][SIZE=2][COLOR=Black]1) Get ubuntu kernel source package (in this case it's [/COLOR][/SIZE][/COLOR][/SIZE][SIZE=3][COLOR=Red][SIZE=2][COLOR=Black]linux-source-2.6.35[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=3][COLOR=Red][SIZE=2][COLOR=Black]) and kernel building tools packages
 [/COLOR][/SIZE][/COLOR][/SIZE]```
sudo apt-get install linux-source-2.6.35
sudo apt-get install kernel-package libncurses5-dev fakeroot wget bzip2
```[SIZE=3][COLOR=Red][SIZE=2][COLOR=Black]
2) [/COLOR][/SIZE][/COLOR][/SIZE]```
cd /usr/src
```[SIZE=3][COLOR=Red][SIZE=2][COLOR=Black]
3) [/COLOR][/SIZE][/COLOR][/SIZE]```
sudo wget [http://schwieters.org/toshset/toshiba_acpi-current.patch](http://schwieters.org/toshset/toshiba_acpi-current.patch)
```[SIZE=3][COLOR=Red][SIZE=2][COLOR=Black]
4) [/COLOR][/SIZE][/COLOR][/SIZE]```
sudo tar -jxf linux-source-2.6.35.tar.bz2
```[SIZE=3][COLOR=Red][SIZE=2][COLOR=Black]
5) [/COLOR][/SIZE][/COLOR][/SIZE]```
cd linux-source-2.6.35
```[SIZE=3][COLOR=Red][SIZE=2][COLOR=Black]
6) [/COLOR][/SIZE][/COLOR][/SIZE]```
sudo patch -p1 < ../toshiba_acpi-current.patch
```[SIZE=3][COLOR=Red][SIZE=2][COLOR=Black]
7) [/COLOR][/SIZE][/COLOR][/SIZE]```
cd drivers/platform/x86/
```[SIZE=3][COLOR=Red][SIZE=2][COLOR=Black]
8) I only wanted to build the toshiba_acpi module. So I commented out all the other modules from the Makefile. Using sudo make a backup copy of the Makefile, then edit the Makefile to only build the toshiba_acpi module. Just put # in front of the other modules.
[/COLOR][/SIZE][/COLOR][/SIZE]```
sudo cp Makefile Makefile.backup
sudo gedit Makefile
```[SIZE=3][COLOR=Red][SIZE=2][COLOR=Black]
9) [/COLOR][/SIZE][/COLOR][/SIZE]```
sudo make -C /usr/src/linux-headers-`uname -r` M=`pwd` modules
```[SIZE=3][COLOR=Red][SIZE=2][COLOR=Black]
10) [/COLOR][/SIZE][/COLOR][/SIZE]```
sudo make -C /usr/src/linux-headers-`uname -r` M=`pwd`modules_install
```[SIZE=3][COLOR=Red][SIZE=2][COLOR=Black]
11) [/COLOR][/SIZE][/COLOR][/SIZE]```
sudo depmod -a
```[SIZE=3][COLOR=Red][SIZE=2][COLOR=Black]
12) Driver should be into /lib/modules/*/extra/toshiba_acpi. Copy the file toshiba_acpi.ko to /lib/modules/*/extra (replace * with your current kernel version).
[/COLOR][/SIZE][/COLOR][/SIZE]```
sudo cp /lib/modules/2.6.35-25-generic/kernel/drivers/platform/x86/toshiba_acpi.ko /lib/modules/2.6.35-25-generic/kernel/drivers/platform/x86/toshiba_acpi.ko.backup
sudo cp /lib/modules/2.6.35-25-generic/extra/toshiba_acpi.ko /lib/modules/2.6.35-25-generic/kernel/drivers/platform/x86/toshiba_acpi.ko
```[SIZE=3][COLOR=Red][SIZE=2][COLOR=Black]
remove the old module:
 [/COLOR][/SIZE][/COLOR][/SIZE]```
sudo rmmod toshiba_acpi
```[SIZE=3][COLOR=Red][SIZE=2][COLOR=Black]
and load the new module:
 [/COLOR][/SIZE][/COLOR][/SIZE]```
sudo modprobe toshiba_acpi
```[SIZE=3][COLOR=Red][SIZE=2][COLOR=Black]
(or simply reboot)
[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=2][COLOR=DarkOliveGreen]**Short solution:**[/COLOR][/SIZE]
[SIZE=3][COLOR=Red][SIZE=2][COLOR=Black]If you don't want to recompile I've done the recompile using kenel 2.6.35-25-generic so you can download the [/COLOR][/SIZE][/COLOR][/SIZE][SIZE=3][COLOR=Red][SIZE=2][COLOR=Black]toshiba_acpi.ko.patched from the attachements and do the following:
[/COLOR][/SIZE][/COLOR][/SIZE]```
sudo cp /lib/modules/2.6.35-25-generic/kernel/drivers/platform/x86/toshiba_acpi.ko /lib/modules/2.6.35-25-generic/kernel/drivers/platform/x86/toshiba_acpi.ko.backup
sudo  cp toshiba_acpi.ko.patched  /lib/modules/2.6.35-25-generic/kernel/drivers/platform/x86/toshiba_acpi.ko
```[SIZE=3][COLOR=Red][SIZE=2][COLOR=Black]
remove the old module:
 [/COLOR][/SIZE][/COLOR][/SIZE]```
sudo rmmod toshiba_acpi
```[SIZE=3][COLOR=Red][SIZE=2][COLOR=Black]
and load the new module:
 [/COLOR][/SIZE][/COLOR][/SIZE]```
sudo modprobe toshiba_acpi
```[SIZE=3][COLOR=Red][SIZE=2][COLOR=Black]
(or simply reboot)
    [/COLOR][/SIZE][/COLOR][/SIZE][SIZE=3][COLOR=Red][SIZE=2][COLOR=Black]
[/COLOR][/SIZE][/COLOR]**[COLOR=Red]Update:[/COLOR]**[/SIZE] [COLOR=Red]This modem is supported out-of-the-box in Ubuntu 9.10 Karmic Koala. You only need to use "sudo toshset -3g on" to switch it on and then use the Network Manager to connect/disconnect.[/COLOR]

Toshiba Portege R500 (and probably R600) comes with a built-in 3G HSDPA modem. Unfortunately, this does not run out of the box with ubuntu 9.04. I expect that it will run flawlessly with ubuntu 9.10. 

So until then, here is a step by step guide on how to make the 3G modem run for ubuntu 9.04. Users of other distributions can also use this guide with minor changes.

**Hardware Specs:**
The modem is a Novatel Expedite EU870D MiniCard but re-branded by Toshiba as Toshiba  Wireless Broadband (3G HSDPA) SM-Bus Minicard Status Port.

Output of lsusb for the device is:
Bus 002 Device 002: ID 0930:1302 Toshiba Corp. Wireless Broadband (3G HSDPA) SM-Bus Minicard Status Port


I am not an expert and most of the credit goes to "vals / spleen.leveller" and "Anssi Saari"who gave me the main leads on how to resolve this. [http://www.novatelwireless.com/index.php?option=com_fireboard&Itemid=0&func=view&catid=18&id=&id=305&catid=18](http://www.novatelwireless.com/index.php?option=com_fireboard&Itemid=0&func=view&catid=18&id=&id=305&catid=18)  [http://groups.google.com/group/comp.protocols.ppp/browse_thread/thread/fb3fb94d5fa887dd](http://groups.google.com/group/comp.protocols.ppp/browse_thread/thread/fb3fb94d5fa887dd)


[SIZE=3]**[COLOR=DarkOliveGreen]Step one: (Enable switching the modem on and off)[/COLOR]**[/SIZE]
Toshset version 1.75 brings support for switching on the 3G modem. 

[SIZE=2][COLOR=DarkOliveGreen]**Option One (Ubuntu 9.10 Karmic repository):**[/COLOR][/SIZE]
Download the new version of toshset from ubuntu 9.10 Karmic repositories and install it. 
```

wget https://launchpad.net/ubuntu/+source/toshset/1.75-1/+build/1089833/+files/toshset_1.75-1_i386.deb

sudo dpkg -i toshset_1.75-1_i386.deb
```[SIZE=2][COLOR=DarkOliveGreen]**Option Two (binary from toshset developers site)**[/COLOR][/SIZE]

```
wget http://www.schwieters.org/toshset/toshset.gz
gunzip toshset.gz
sudo cp  toshset /usr/bin/toshset 
```Now you can toggle the 3g modem on and off by using this command:
```
sudo toshset -3g on
sudo toshset -3g off

```[SIZE=3][COLOR=DarkOliveGreen][B]Step two: (Make the 3G recognized as a Mobile Broadband Modem)
[/B][/COLOR][/SIZE]
To get the modem to be recognized you will need to patch the "option" module and recompile the kernel (Long solution). If you do not want to recompile the kernel, you can download the modified option.ko that I have attached and replace your current file (Short solution).

[SIZE=2][COLOR=DarkOliveGreen]**Short solution:**[/COLOR][/SIZE]
(If you are not using ubuntu, most probably this will not work for you)

Download the patched binary of option module "option.ko.patched" from this thread's attachments. This was compiled on my laptop using ubuntu 9.04 kernel 2.6.28-13-generic. 
```

sudo mv /lib/modules/$(uname -r)/kernel/drivers/usb/serial/option.ko /lib/modules/$(uname -r)/kernel/drivers/usb/serial/option.ko.orig

unzip option.ko.patched.zip

sudo cp option.ko.patched /lib/modules/$(uname -r)/kernel/drivers/usb/serial/option.ko
```Now we want to make sure the option module is going to be loaded automatically when we reboot. First check if it is not already being loaded.

```
lsmod | grep option
```If the option module is already loaded you will see output similar to the following:

> option                 28292  0 
usbserial              39656  1 option
If you don't see "option" in the output, then add the option module by running the following commands:

```
sudo /bin/bash

echo "option" >> /etc/modules

```Reboot now and scroll down to "Final Touches"

[SIZE=2][COLOR=DarkOliveGreen]**Long Solution:**[/COLOR][/SIZE]
Most of the linux compilation guide is copied from "The Geek" founder of "How-To Geek". This is a link to the original article: [http://www.howtogeek.com/howto/ubuntu/how-to-customize-your-ubuntu-kernel/](http://www.howtogeek.com/howto/ubuntu/how-to-customize-your-ubuntu-kernel/)

**[COLOR=DarkOliveGreen]Re-compiling the kernel:[/COLOR]**
**Getting needed packages**:
The linux source code, the curses library and some other tools need to be installed to help us compile .
```

sudo apt-get install linux-source-2.6.17 kernel-package libncurses5-dev fakeroot
```the source will be installed to the /usr/src directory in as a compressed file.

To make things easier, we’ll put ourselves in root mode by using sudo to open a new shell. There’s other ways to do this, but I prefer this way.

```
sudo /bin/bash
```Now change directory into the source location so that we can install. Note that you may need to install the bunzip utility if it’s not installed.

```
cd /usr/src

echo $(uname -r) | bunzip2 linux-source-$(cut -c -6).tar.bz2

echo $(uname -r) | tar xvf linux-source-$(cut -c -6).tar

echo $(uname -r) | ln -s linux-source-$(cut -c -6) linux

```[B]
Patching the option module:[/B]
(based on Michele Valzelli and Greg Kroah-Hartman work here: [http://www.spinics.net/lists/linux-usb/msg18847.html](http://www.spinics.net/lists/linux-usb/msg18847.html))

```
cp /usr/src/linux/drivers/usb/serial/option.c /usr/src/linux/drivers/usb/serial/option.c.orig

gedit /usr/src/linux/drivers/usb/serial/option.c

```Ctrl+F and find this string "#define NOVATELWIRELESS_PRODUCT_EU870D"

Insert a new line after the EXPEDITE PRODUCTS section and add the following text:
 
```
/* TOSHIBA PRODUCTS */
#define TOSHIBA_VENDOR_ID            0x0930
#define TOSHIBA_PRODUCT_HSDPA_MINICARD        0x1302

```Ctrl+F and find this string "{ USB_DEVICE(0x1da5, 0x4515) }, /* BenQ H20 */" insert a new line after this line and paste the following:

```
   { USB_DEVICE(TOSHIBA_VENDOR_ID, TOSHIBA_PRODUCT_HSDPA_MINICARD ) }, /* Toshiba 3G HSDPA == Novatel Expedite EU870D MiniCard */

```save the file and close it.

**Configure the New kernel:**
Make a copy of your existing kernel configuration to use for the custom compile process. Note that the ` character is the one below the tilde ~

```
cp /boot/config-`uname -r` /usr/src/linux/.config
```Now we will launch the utility that will let us customize the kernel:

```
cd /usr/src/linux

make menuconfig

```First, go down to Load an Alternate Configuration File, and load the .config file. (just hit enter)

[IMG]http://www.howtogeek.com/wp-content/uploads/2006/12/WindowsLiveWriter/CustomizeYourKernelonUbuntu_86BF/loadaltconfig.png[/IMG]

Hit Exit and save the configuration when prompted.

**Compile the kernel:**
Now we are ready for compile. First we’ll do a make clean, just to make sure everything is ready for the compile.

```
make-kpkg clean
```Next we’ll actually compile the kernel. This will take a LONG FREAKING TIME, so go find something interesting to do.

```
fakeroot make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers

```This process will create two .deb files in /usr/src that contain the kernel. The linux-image****  file is the actual kernel image, and the other file contains the headers. You can install both with dpkg. The filenames will probably be different on your system.

Please note that when you run these next commands, this will set the new kernel as the new default kernel. This could break things! If your machine doesn’t boot, you can hit Esc at the GRUB loading menu, and select your old kernel. You can then disable the kernel in /boot/grub/menu.lst or try and compile again. 

```
dpkg -i linux-image-*-custom_*-custom-10.00.Custom_i386.deb

dpkg -i linux-headers-*-custom_*-custom-10.00.Custom_i386.deb

```Now reboot your machine. If everything works, you should be running your new custom kernel. You can check this by using uname. Note that the exact number will be different on your machine.

```
    uname -r

    2.6.28.9-ubuntu1-custom

```[SIZE=3][COLOR=DarkOliveGreen]**Final Touches**[/COLOR][/SIZE]

Now if you click on the Network Manager Applet you will find that the Mobile Broadband modem is recognized. In my case it is recognized as two modems which forces nm-applet to put the full name of the modem "Toshiba Wireless Broadband (3G HSDPA) SM-Bus Minicard Status Port". I hope this will be fixed with ubuntu 9.10. This problem is ok with me as long as I can connect now in full speed.

To connect, you will need first to run this command
```
sudo toshset -3g on

```You will see the 3G modem indicator light switched on. Now you can click on the Network Manager icon and if you have two entries for the modem choose the upper one (that's the one that works for me)

To make things easier, I have written a script that will toggle the 3g modem on and off and created a launcher icon for it in my pannel. I have also created a keyboard short cut for it.

```
sudo gedit /usr/bin/3g-toggle
```paste the following in the new file:

```
#!/bin/bash
modem_status=$(gksudo "toshset -3g")
echo $modem_status | grep "on"
if [[ $? -eq 0 ]] ; then
    gksudo "toshset -3g off"
else
    gksudo "toshset -3g on"
fi

```save the file and close it then make it executable:

```
sudo chmod +x /usr/bin/3g-toggle

```Now right-click on any free space on your panels and choose "Add to panel..." then double-click on "Custom Application Launcher" and create it as follows:

Type: Application
Name: Toggle 3G Modem
Command: 3g-toggle
Comment: Toggle 3G Modem on and off

press on the icon to choose a meaningful icon then press Close to save your new launcher.

You can also have a keyboard shortcut to toggle the 3G on and off by going to System => Preferences => Keyboard Shortcuts. Press "Add" then write "Toggle 3G Modem" as the name and 3g-toggle as the command. A new shortcut will be created under "Custom Shortcuts" named "Toggle 3G Modem". Click on the word "Disabled" and when you see "New shortcut.." press the keyboard combination of your choice. Then press "Close".

[SIZE=3][COLOR=Red]**Important Note:**[/COLOR][/SIZE]
The patched "option" kernel module will be lost on every kernel upgrade whether you used the long solution or the short solution above.
To fix this you either repeat "Step Two" or just copy the patched binary (option.ko) from your previous kernel to the new one.

For example when I upgraded today from kernel 2.6.28-13-generic to 2.6.28-14-generic I followed the following steps:

```
sudo rmmod option
sudo mv /lib/modules/$(uname -r)/kernel/drivers/usb/serial/option.ko /lib/modules/$(uname -r)/kernel/drivers/usb/serial/option.ko.orig
sudo cp /lib/modules/2.6.28-13-generic/kernel/drivers/usb/serial/option.ko /lib/modules/$(uname -r)/kernel/drivers/usb/serial/
sudo modprobe -i option
```Logout and login and you are done (or just restart nm-applet).

If you used the Long solution for patching, the location of the patched module will be in /lib/modules/2.6.*custom*/kernel/drivers/usb/serial/option.ko
so you will need to adjust the commands accordingly.

---

### Post by balingupjer on 2009-10-09
Nice How to. It took a while but worked for my Toshiba M700 with 9.04.

now my wireless broadband has stopped working... Modem light comes on, but when I click on GSM in Network Manager it tries to connect, then says "GSM dissconected"

Any ideas on how to trouble shoot?

Also every package I install after the recompile says "errors found, type 1" but everything seems to work... is this normal, and can i fix it?

---

### Post by hamidaddin on 2009-10-09
> **balingupjer said:**
> now my wireless broadband has stopped working... Modem light comes on, but when I click on GSM in Network Manager it tries to connect, then says "GSM dissconected"


Was it working before? What can you see in the list of available connections (Network Manager applet)?

---

### Post by vhf1967 on 2009-11-14
> **hamidaddin said:**
> Was it working before? What can you see in the list of available connections (Network Manager applet)?

I have the same problem with a toshiba r500. With the solution above it was working very well on 9.04, but after updating to 9.10 I have the problem described above... a solution for this problem will be very much appreciated

---

### Post by hamidaddin on 2009-11-14
Can you please explain your problem more?

Do you see your 3G modem/ISP in the Network Manager list? If so what happens when you try to connect.

In my case the 3g modem of Toshiba Portege R500 works out-of-the-box with ubuntu 9.10. You need to make sure that you are swiching the modem on by using the "sudo toshset -3g on" command as explained in the first post. you will see the blue 3g indicator light going on, just next to the yellow wifi indicator light below the touchpad.

---

### Post by vhf1967 on 2009-11-14
Hi!
Thanks very much for your reply! 

> **hamidaddin said:**
> Can you please explain your problem more?

Do you see your 3G modem/ISP in the Network Manager list?

Yes, it appears (even before I swicth on with "sudo toshset -3g on")...  and I have my ISP connection configured (with the same configuration I had before with 9.04 - I have already remade it after the updating, just in case). 

> **hamidaddin said:**
>  If so what happens when you try to connect. 

So after I'm swiching on the modem   ("sudo toshset -3g on") the blue light start blinking, but when I click on  my ISP from Network Manager list, it returns the message "the GSM network is now disconnected" (the precise message is in portuguese) and nothing happens next... 

Thanks!

> **hamidaddin said:**
>  In my case the 3g modem of Toshiba Portege R500 works out-of-the-box with ubuntu 9.10. You need to make sure that you are swiching the modem on by using the "sudo toshset -3g on" command as explained in the first post. you will see the blue 3g indicator light going on, just next to the yellow wifi indicator light below the touchpad.

---

### Post by hamidaddin on 2009-11-14
If you have dual boot to windows, does it work in Windows?
Otherwise, if you have a live CD of ubuntu, can you try to boot it and connect?

If we both have the same laptops and configuration, we should have the same results. I suspect that maybe the signal is weak?

Please try and let me know..

---

### Post by vhf1967 on 2009-11-15
> **hamidaddin said:**
> If you have dual boot to windows, does it work in Windows?
Otherwise, if you have a live CD of ubuntu, can you try to boot it and connect?

If we both have the same laptops and configuration, we should have the same results. I suspect that maybe the signal is weak?

Please try and let me know..

It works well on windows (vista)! 

Meanwhile I burned a 9.10 CD and tried... I obtained precisely the same problem!  

Regarding the signal, it is "good" (as on windows is indicated -- on a mobile phone I have all the dashes!)...

---

### Post by hamidaddin on 2009-11-15
That's very strange. The only thing I can think of now is that there is a problem is the provider's configuration file.

In my case, the provider is called STC. I boot the live CD and select it out of the country's list, run the toshset command and connect with no problems.

So, maybe the default configuration of your provider is not right?

try looking at it by opening gconf-editor and searching for "apn" (choose "search also in key names").

This is the best I can think of. I hope someone with more knowledge can help you out.

---

### Post by vhf1967 on 2009-11-19
> **hamidaddin said:**
> That's very strange. The only thing I can think of now is that there is a problem is the provider's configuration file.

In my case, the provider is called STC. I boot the live CD and select it out of the country's list, run the toshset command and connect with no problems.

So, maybe the default configuration of your provider is not right?

try looking at it by opening gconf-editor and searching for "apn" (choose "search also in key names").
It found no entry with this searching... 
However I decide to remove the pin code from the sim card and... it began working!!! 
Many thanks.

---

### Post by amrs on 2009-12-25
So, how well do things work in Ubuntu 9.10? With Fedora 12 I still have to manually patch toshiba_acpi ino the kernel. Not a problem and things work, but after suspend-to-disk or suspend-to-ram (or suspend/hibernate in Windows parlance) sometimes the modem works and sometimes it does not. 

When it does not, it seems that no amount of toggling the rfkill switch or unloading the option and/or usb-serial driver or running toshset -3g on/off just doesn't help. If I put the laptop to either sleep mode again, after wakeup the modem may work again or not. 

Another symptom after waking up is that the modem shows up as two modems and four ports (/dev/ttyUSB01-ttyUSB03). This doesn't directly mean the modem does not work, but when it doesn't, only ttyUSB03 answers to AT commands when testing with minicom, normally ttyUSB00 responds and is what NetworkManager uses.

So, how well do sleep modes and the modem in R500 work in Ubuntu land? I might just try an Ubuntu live and see for myself...

---

### Post by MagnusL on 2010-09-21
Hi!
I'm running 10.04 on my R500, and have not before used the 3G modem, but as things are developing around me it would be very useful now. 

However, I cannot get it to work. I understand it should be supported out of the box...? It turns up when doing lsusb, and I do the "sudo toshset -3g on". And insert my SIM-card, try it every way to be certain. But no modem turns up in my networkmanager. 

lsmod tells me option and usbserial are loaded. 

Anyone got more advice on what to try and check? 

Magnus L

---

### Post by hamidaddin on 2011-02-10
I've added a new update to the first post to fix the driver in ubuntu 10.10 (Maverick Meerkat)

---

### Post by skarp on 2011-07-31
Many thanks :) This thread solved my problem since years with the 3G-modem on my R500. I've tried all the major linux-distributions and none seems to support the modem out of the box.

---

### Post by hamidaddin on 2011-07-31
Glad to know it helped skarp. What version of Ubuntu are you using?

---

### Post by Weazel on 2011-10-26
Hi, 
thanks a lot for the guide

Only problem is I'm currently using natty and I'm so frustrated with the Mobile Broadband and seem to be stuck during the step by step to fix that.

> [COLOR="DarkRed"]uname -a[/COLOR]
```
[COLOR="Navy"]Linux Weazel 2.6.38-12-generic #51-Ubuntu SMP Wed Sep 28 14:25:20 UTC 2011 i686 i686 i386 GNU/Linux[/COLOR]
```

and the error is after I input this command:

> [COLOR="DarkRed"]sudo make -C /usr/src/linux-headers-`uname -r` M=`pwd` modules[/COLOR]
```
[COLOR="Navy"]make: Entering directory `/usr/src/linux-headers-2.6.38-12-generic'
  CC [M]  /usr/src/linux-source-2.6.38/drivers/platform/x86/toshiba_acpi.o
/usr/src/linux-source-2.6.38/drivers/platform/x86/toshiba_acpi.c:922:2: error: unknown field ‘ioctl’ specified in initializer
/usr/src/linux-source-2.6.38/drivers/platform/x86/toshiba_acpi.c:923:1: warning: initialization from incompatible pointer type
make[1]: *** [/usr/src/linux-source-2.6.38/drivers/platform/x86/toshiba_acpi.o] Error 1
make: *** [_module_/usr/src/linux-source-2.6.38/drivers/platform/x86] Error 2[/COLOR]
```

Help is very much appreciated !

Thanks in Advance
Weazel.

---

### Post by hamidaddin on 2012-01-24
Hello Weazel,

Please check Update 4 in the original post and see if it fixes your problem...

Regards,
Yahya

---

### Post by hamidaddin on 2012-05-04
3G stopped working after upgrade to !2.04. Had to patch toshiba_acpi and recompile it. The patched file is added to the first  post.

---

### Post by lauschi on 2012-09-04
Thanks a lot for this how to.

  	 	 	 	 	 	   Hello,
 

 Like discribed under update 5, I tried to make work my 3g modem on r500 running Linux Mint Maya (based on unbuntu 12.04).
 

 Sustituting my toshiba_acpi.ko with the pached file. I don't have the directory /lib/modules/2.6.35-25-generic/kernel/drivers/platform/x86/ so I copied it to /lib/modules/3.2.0-23-generic/kernel/drivers/platform/x86/  After the reboot the modem is not working yet.  
 

 I am an absolut linux-rookie and no native english-speaking, so I am not sure if I should use the whole instructions in this how-to (e.g. [COLOR=#556b2f][SIZE=3]**Enable switching the modem on and off; Make the 3G recognized as a Mobile Broadband Modem)**[/SIZE][/COLOR] or just the part of update 5?
 

 Well, I tried to install toshset, like discribed:
 wget [https://launchpad.net/ubuntu/+source/toshset/1.75-1/+build/1089833/+files/toshset_1.75-1_i386.deb](https://launchpad.net/ubuntu/+source/toshset/1.75-1/+build/1089833/+files/toshset_1.75-1_i386.deb)  sudo dpkg -i toshset_1.75-1_i386.deb 

 But another version is already installed:
 *toshset:i386 1.75-1 (Multi-Arch: no) is not co-installable with toshset:amd64 1.76-2 (Multi-Arch: no) which is currently installed*
 

 Trying to turn the 3g on and off with my installed version of toshset is not working:
 *required kernel toshiba support not enabled*
 

 But option modul seems to be loaded:
 *option                 25849  2  *
 *usb_wwan               20491  1 option *
 *usbserial              47077  6 option,usb_wwan*
 

 I would appreciate any help in solving this issue or advice on  my mistakes. Thanks a lot.  
 Lauschi

---

