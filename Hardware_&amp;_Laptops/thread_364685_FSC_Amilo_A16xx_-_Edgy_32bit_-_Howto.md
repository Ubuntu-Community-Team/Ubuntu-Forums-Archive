---
title: "FSC Amilo A16xx - Edgy 32bit - Howto"
date: 2007-02-18
forum: Hardware &amp; Laptops
---

### Post by damagedspline on 2007-02-18
I've written a howto and posted it at 
[http://damagedspline.blogspot.com/2007/02/fsc-amilo-a1650g-ubuntu-edgy-32bit-how.html](http://damagedspline.blogspot.com/2007/02/fsc-amilo-a1650g-ubuntu-edgy-32bit-how.html)

I've added some lines to acerhk so that the function keys / hotkeys like wireless on/off and cool-n'-quiet button will be recognized correctly.

the scripts and patch can be found on the svn I created at googlecode:
[http://fscamiloa16xx.googlecode.com/svn/trunk/Edgy/](http://fscamiloa16xx.googlecode.com/svn/trunk/Edgy/)

---

### Post by info2 on 2007-05-27
Hi,

i have an Amilo Si1520 and I extended your script.

Now it's also setting a sampling_rate to the scaling_governor and sets a throttling_rate to the processor(s).
To inform the user about weather it is activated ot deactivated i use notify-send.
That makes the funny notification-bubbles ... i love bubbles. :D


I dont know if it is working for everybody that way but i hope so.

Also I use xbindkeys to perform an action if the user press the Button.

Script setkeys.sh
```

#!/bin/sh
#this will load xbindkeys and set the c'n'q - Button to the key-nummer 200
#
#use xbindkeys-config to setup xbindkeys 
#
#xbindkeys is a tool that runs a command/script/program if the user press a certain key
#Before using xbindkeys-config you need to set the keycode (setkeycodes e074 200).
#
#If your key is not "e074" you can take a look at dmesg after pressing your Cool'n'Quiet-Key. There should be
#a message that the given value is not bound to a keynumber.
#
#this script need to be loaded before usinf fsc-setspeed.sh. Put it somewhere where it is 
#called automatically. Your sessions autostart or as an init.d - script for example.

setkeycodes e074 200
xbindkeys
```


Script fsc-cpuspeed.sh:

```

#!/bin/bash
# enable/disable cool-n'-quiet (in this case cpu scaling-governor and Throtteling state)
# you can use (among others) xbindkeys to attack this Script to a specific Keycode
#
#
for CPU in /sys/devices/system/cpu/*; do
    if test -d $CPU; then
	if test $(cat $CPU/cpufreq/scaling_governor) == "ondemand"; then
      		echo -n "conservative" > $CPU/cpufreq/scaling_governor

		#get the minimal sampling rate and append a "0" (= same like multiplication with 10)
		SAMPLINGRATE=$(cat $CPU/cpufreq/conservative/sampling_rate_min)0
		
		#test if our samplingrate is greater than the systems maximum sampling rate
		#the systems sampling_rate_max often is too big and causes the cpu running 
		#long time at a higher frequency before the governor switches back.
		#a too small sampling rate wakes up the processor too much often by governor

		if [ $SAMPLINGRATE -gt $(cat $CPU/cpufreq/conservative/sampling_rate_max) ] 
		then
		    SAMPLINGRATE=$(cat $CPU/cpufreq/conservative/sampling_rate_max)
		fi

		echo -n $SAMPLINGRATE > $CPU/cpufreq/conservative/sampling_rate

		#setting a user-limit throttling-state
		#4 is 50% on my system.
		#look at cat /proc/acpi/processor/CPU?/throttling for more values
		for ACPICPU in /proc/acpi/processor/*; do
			echo -n "0:4" > $ACPICPU/limit
		done
		MESSAGE="Activated"
	else
      		echo -n "ondemand" > $CPU/cpufreq/scaling_governor
		cat $CPU/cpufreq/ondemand/sampling_rate_min > $CPU/cpufreq/ondemand/sampling_rate

		#setting user-limit throttling-state to 0 (=no throttling)
		for ACPICPU in /proc/acpi/processor/*; do
			echo -n "0:0" > $ACPICPU/limit
		done
		MESSAGE="Deactivated"
	fi
   fi
done
#send Notification to the user that called this script
sudo -u $SUDO_USER notify-send --urgency="normal" --expire-time=5000 --icon="gtk-info" "Cool'n'Quiet" $MESSAGE

```


Have fun with it! The next cool thing would be a working fan-control...


Update1: found  error at line 19-21  - fixed.

---

### Post by damagedspline on 2007-06-17
Cool!!!

Do you use a patched version of acerhk? Are all of your buttons recognized and operational?

If you have a network card based on Atheros chipset, are you suffer from issues with NetworkManager, when using the wireless button to turn the wireless off and back on?

---

### Post by graymalkin on 2007-06-27
hi =)
can you explain how to apply patch ? thanks =)

---

### Post by damagedspline on 2007-08-30
The auto installation script for Amilo A1650G for 32bit Ubuntus (Feisty,Gutsy) is here.

This script has been tested on my A1650G, Please send me questions/remarks/warnings/errors if you run into any.

Features:
1) Make the hotkeys work - all of them (besides change display)!
2) Notification bubbles and Cool n' Quiet - done by info2 @ubuntuforums.
3) Make wireless work - only if you have the Atheros 5005g. I'll be happy to add Broadcom if I had testers with that configuration.

Requirements:
1) 32bit Ubuntu >= 7.04
2) Amilo A1650G or similarly hotkeyd laptop
3) internet connection

HowTo:
Open a console and run:
```

wget http://fscamiloa16xx.googlecode.com/svn/trunk/fsca16xx.sh
chmod 755 fsca16xx.sh
sudo ./fsca16xx.sh setup

```

Wait a bit till it's Done.
Log out, Log back in and viola!

Please if you have a Broadcom based wireless card (which came with your A1650G), tell me how you made it work, I'll add it.

Again this only works on 32bit Ubuntus, I'll try fixing the hotkeys for 64bit's aswell. After each kernel update it should be rerun. I'll try to add autorecompile for acerhk so that it will be automatic.

I want to add additional laptops with similar hotkeys layouts. So far I'm familiar with Li1718 with the help of johntait @amilo-forums  and Si1520 with the help of info2 @ubuntu-forums (both still in early stages).

Gutsy support has been tested with the latest tribe.

Stay tuned for updates (those usualy come in daily basis...)

EDIT: the script installation instructions was updated. The script will run at each boot in check mode to make sure that the configuration is intact even after ubuntu updates - 2/11/2007

---

### Post by Graes on 2007-09-26
this worked perfect for me until i updated my ubuntu today now i can not make it work what 's wrong :(

---

### Post by damagedspline on 2007-09-27
Hi,

you can rerun the script - it should fix it.

I've made some additional upgrades to the script  and from now on, it will recheck the configuration on each boot.

I'll upload the new script in the following couple of days.

---

### Post by damagedspline on 2007-09-27
new script is out with auto checking.

4 script options:
1) setup - should be run once - this will make all the required adjustments and add the script for auto checking configuration
2) start - use for auto boot checking
3) stop - does nothing
4) upgrade - upgrade and install the latest script from svn

installation instructions:
wget [http://fscamiloa16xx.googlecode.com/svn/trunk/fsca16xx.sh](http://fscamiloa16xx.googlecode.com/svn/trunk/fsca16xx.sh)
chmod 755 fsca16xx.sh
sudo ./fsca16xx.sh setup

---

### Post by Graes on 2007-09-28
when i do sudo ./fsca16xx.sh setup i get this error

[: 369: missing ]
Welcome to the Fujitsu-Siemens Amilo A16xx automated patch for Ubuntu Gutsy

This script will enable some of the laptop features such as the Special buttons such
as Wireless, Browser and Fancy Fan

cp: kan ikke udføre stat() './fsca16xx.sh': No such file or directory
ln: tilgår '/etc/init.d/fsca16xx.sh': No such file or directory
Compiling AcerHK
Compile ended successfully!
Replacing Acerhk module
Downloading additional files required by setup
Setting all features to auto-activate on startup
Adding kernel support for Special Buttons
Warning: Unknown Atheros chipset - replacing native wireless driver
Loading kernel modules for Special Buttons
Done. Please logout and relogin in order to start using the hotkeys.

i have a Li1718

---

### Post by Graes on 2007-09-29
please help i really need WiFi

---

### Post by damagedspline on 2007-09-29
> **Graes said:**
> when i do sudo ./fsca16xx.sh setup i get this error

[: 369: missing ]
Welcome to the Fujitsu-Siemens Amilo A16xx automated patch for Ubuntu Gutsy

This script will enable some of the laptop features such as the Special buttons such
as Wireless, Browser and Fancy Fan

cp: kan ikke udføre stat() './fsca16xx.sh': No such file or directory
ln: tilgår '/etc/init.d/fsca16xx.sh': No such file or directory
Compiling AcerHK
Compile ended successfully!
Replacing Acerhk module
Downloading additional files required by setup
Setting all features to auto-activate on startup
Adding kernel support for Special Buttons
Warning: Unknown Atheros chipset - replacing native wireless driver
Loading kernel modules for Special Buttons
Done. Please logout and relogin in order to start using the hotkeys.

i have a Li1718

Sorry, for the late response...

Is this the only output you'd got?

According to the output, your wireless driver is already installed, so all you need to do is just press the wireless key.

you get a very weird error which I can't figure out.

have you made any manual changes to /bin/dash?

if after reboot the wireless button does not function - don't continue further.

as a manual fix, i suggest you manually copy fsca16xx.sh to /etc/init.d (after being chmod 755)
and then run:
sudo ln  /etc/init.d/fsca16xx.sh /etc/rc5.d/S99fsca16xx

this will set a configuration check on boot that can withstand critical updates.

---

### Post by Graes on 2007-09-30
> **damagedspline said:**
> Sorry, for the late response...

Is this the only output you'd got?

According to the output, your wireless driver is already installed, so all you need to do is just press the wireless key.

you get a very weird error which I can't figure out.

have you made any manual changes to /bin/dash?

if after reboot the wireless button does not function - don't continue further.

as a manual fix, i suggest you manually copy fsca16xx.sh to /etc/init.d (after being chmod 755)
and then run:
sudo ln  /etc/init.d/fsca16xx.sh /etc/rc5.d/S99fsca16xx

this will set a configuration check on boot that can withstand critical updates.

yes that is all output i get 

no i have not made any changes tio /bin/dash

that manual fix did not work 

so i tried to remove all network by removing the wireless driver and removing ndiswrapper + the manual copied file /etc/init.d/fsca16xx.sh
and i tried runing the script again 
i got this output 

 
[: 369: missing ]
Welcome to the Fujitsu-Siemens Amilo A16xx automated patch for Ubuntu Gutsy

This script will enable some of the laptop features such as the Special buttons such
as Wireless, Browser and Fancy Fan

cp: kan ikke udføre stat() './fsca16xx.sh': No such file or directory
ln: tilgår '/etc/init.d/fsca16xx.sh': No such file or directory
Compiling AcerHK
Compile ended successfully!
Replacing Acerhk module
Downloading additional files required by setup
Setting all features to auto-activate on startup
Adding kernel support for Special Buttons
Warning: Unknown Atheros chipset - replacing native wireless driver
[: 398: ==: unexpected operator

---

### Post by damagedspline on 2007-09-30
do you have Broadcom wireless card or Atheros? this script only work on atheros based wireless cards.

if you dont know run: lsmod | grep -i atheros

if it shows something you have an atheros wireless driver

---

### Post by damagedspline on 2007-09-30
> **Graes said:**
> 
[: 398: ==: unexpected operator

I've fixed that specific issue.

Updated script is in the svn.

---

### Post by Graes on 2007-09-30
dont you mean lsmod | grep -i ath

output of lsmod | grep -i ath

ath_pci                98336  0 
wlan                  206660  1 ath_pci
ath_hal               192720  1 ath_pci

output of lspic is 

02:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)

---

### Post by Graes on 2007-09-30
i still get
[: 398: ==: unexpected operator

---

### Post by Graes on 2007-10-01
i know this is designed to work with Atheros 5005g but it used to work with AR5006EG :confused:

---

### Post by damagedspline on 2007-10-01
please send me the result of: lspci | grep -i atheros

if you have installed it once manually using ndiswrapper, where did you download the wireless driver from?

anyway, I think I know why the wireless does not work...

try:
sudo rmmod ath_pci
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper

make sure that ndiswrapper has a driver.

please tell me if it's working

---

### Post by Graes on 2007-10-01
result of: lspci | grep -i atheros

02:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)

if you have installed it once manually using ndiswrapper, where did you download the wireless driver from?

[http://www.atheros.cz/download.php?atheros=AR5006EG&system=1](http://www.atheros.cz/download.php?atheros=AR5006EG&system=1)
file  : xp32-5.3.0.56-whql.zip

sudo rmmod ath_pci
ERROR: Module ath_pci does not exist in /proc/modules

its the wifi button that dont work cant turn wifi on with the hotkeys

---

### Post by damagedspline on 2007-10-01
> **Graes said:**
> result of: lspci | grep -i atheros

02:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)

if you have installed it once manually using ndiswrapper, where did you download the wireless driver from?

[http://www.atheros.cz/download.php?atheros=AR5006EG&system=1](http://www.atheros.cz/download.php?atheros=AR5006EG&system=1)
file  : xp32-5.3.0.56-whql.zip

sudo rmmod ath_pci
ERROR: Module ath_pci does not exist in /proc/modules

its the wifi button that dont work cant turn wifi on with the hotkeys

So if I get it right, when you run: echo 1 > /proc/driver/acerhk/wirelessled
it will turn the wireless led on, but the wireless key does not work...

try this:
1) sudo rmmod acerhk
2) sudo modprobe acerhk force_series=6805 verbose=4 autowlan=1
3) press the wireless key
check dmesg tail to see if it was recognized.
if it did please check that /etc/acpi/fsc-wireless.sh exist and executable

the script you have is not updated since currently no == exist in the file

---

### Post by Graes on 2007-10-01
echo 1 > /proc/driver/acerhk/wirelessled
does nothing

1) sudo rmmod acerhk
2) sudo modprobe acerhk force_series=6805 verbose=4 autowlan=1
3) press the wireless key
check dmesg tail to see if it was recognized.
if it did please check that /etc/acpi/fsc-wireless.sh exist and executable

[  862.832000] acerhk: received key code 0x30
[  862.832000] acerhk: translated acer key code 0x30 to no key

etc/acpi/fsc-wireless.sh exist how do i check if it is executable if it is ./fsc-wireless.sh 

cat: /proc/driver/acerhk/wirelessled: Permission denied
i get a popup i the lower right corner saying wireless disabled

---

### Post by damagedspline on 2007-10-01
etc/acpi/fsc-wireless.sh exist how do i check if it is executable if it is ./fsc-wireless.sh 

ls -la /etc/acpi/fsc-wireless.sh 

it's suppose to be something like xwrx-rx-r

cat: /proc/driver/acerhk/wirelessled: Permission denied
i get a popup i the lower right corner saying wireless disabled

weird. if you try to cat  /proc/driver/acerhk/wirelessled with sudo, does it has the same results?

I've made a change to the acerhk module so that it can be read from. if even with sudo you can't read there then I guess the acerhk version you have is not with the patch I made. that also explain the reason, that the button is not set to a specific key.

did you run the script after a clean install?

---

### Post by tungdil on 2007-10-01
> **Graes said:**
> 
i have a Li1718

Hi!

I think the script won't help as it is for the 16xx series. Maybe this link can help :[http://www.amilo-forum.com/topic,1029,-Li1718-auto-installation-for-ubuntu-32bit-Testers-needed.html]("http://www.amilo-forum.com/topic,1029,-Li1718-auto-installation-for-ubuntu-32bit-Testers-needed.html")

Otherwise you might want to Google for "ubuntu wifi Li1718"

Good luck!
tungdil

---

### Post by damagedspline on 2007-10-02
> **tungdil said:**
> Hi!

I think the script won't help as it is for the 16xx series. Maybe this link can help :[http://www.amilo-forum.com/topic,1029,-Li1718-auto-installation-for-ubuntu-32bit-Testers-needed.html]("http://www.amilo-forum.com/topic,1029,-Li1718-auto-installation-for-ubuntu-32bit-Testers-needed.html")

Otherwise you might want to Google for "ubuntu wifi Li1718"

Good luck!
tungdil

You are partially correct. I initially wrote this script for amilo a1650g, but then several people said that it was also working on li1718, so I modded the script to officially support it. I also opened the thread at amilo-forums to seek testers.

---

### Post by Graes on 2007-10-02
ls -la /etc/acpi/fsc-wireless.sh

-rwxr-xr-x


weird. if you try to cat /proc/driver/acerhk/wirelessled with sudo, does it has the same results?

today i have no popup 
cat: /proc/driver/acerhk/wirelessled: Permission denied

sudo cat /proc/driver/acerhk/wirelessled nothing happens

i think i might have to try it from a clean install again

---

### Post by Terbit on 2007-10-02
Problem with fsca16xx.sh
Loading ok, chmod ok, but running script says:

lotta@lotta-laptop:~$ sudo ./fsca16xx.sh setup
Welcome to the Fujitsu-Siemens Amilo A16xx automated patch for Ubuntu Gutsy

This script will enable some of the laptop features such as the Special buttons such
as Wireless, Browser and Fancy Fan

cp: cannot stat `./fsca16xx.sh': No such file or directory
ln: accessing `/etc/init.d/fsca16xx.sh': No such file or directory
fscamiloa16xx has already been setup, nothing to do.

Amilo A1650G and Atheros

---

### Post by Graes on 2007-10-03
ok so i reinstalled ubuntu gutsy and still i can not get i working so i thought i give it a go a ubuntu Edgy and yes theres wifi so i guess this script dont work on gutsy :(

---

### Post by damagedspline on 2007-10-03
> **Graes said:**
> ok so i reinstalled ubuntu gutsy and still i can not get i working so i thought i give it a go a ubuntu Edgy and yes theres wifi so i guess this script dont work on gutsy :(

Terbit & Graes:
I've fixed it, please download and use the latest script from the svn trunk.

I use it on Gutsy here.

---

### Post by Graes on 2007-10-03
> **damagedspline said:**
> Terbit & Graes:
I've fixed it, please download and use the latest script from the svn trunk.

I use it on Gutsy here.

Welcome to the Fujitsu-Siemens Amilo A16xx automated patch for Ubuntu Fiesty

This script will enable some of the laptop features such as the Special buttons such
as Wireless, Browser and Fancy Fan

Downloading additional files required by setup
Setting all features to auto-activate on startup
Adding kernel support for Special Buttons
Warning: Unknown Atheros chipset - replacing native wireless driver
Downloading atheros driver
wget: invalid option -- u
Brug: wget [FLAG]... [URL]...

Prøv 'wget --help' for flere flag.
Error: Unable to download xp32-5.3.0.56-whql.zip

---

### Post by damagedspline on 2007-10-03
> **Graes said:**
> 
Prøv 'wget --help' for flere flag.
Error: Unable to download xp32-5.3.0.56-whql.zip


fixed. latest script is in the svn trunc.

---

### Post by Graes on 2007-10-04
ok we are getting there :)

Welcome to the Fujitsu-Siemens Amilo A16xx automated patch for Ubuntu Fiesty

This script will enable some of the laptop features such as the Special buttons such
as Wireless, Browser and Fancy Fan

Downloading additional files required by setup
Setting all features to auto-activate on startup
Adding kernel support for Special Buttons
Warning: Unknown Atheros chipset - replacing native wireless driver
Installing atheros driver
**couldn't open net5211.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 174.**
Error: ndisdriver driver installation failed, setup will continue non-the-less but wireless is not likely to work...;
Error:...please try to install the driver manually using 'sudo ndiswrapper -i <driver inf file name>'
Loading kernel modules for Special Buttons
Done. Please logout and relogin in order to start using the hotkeys.

---

### Post by damagedspline on 2007-10-04
> **Graes said:**
> 
** couldn't open net5211.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 174.**
Error: ndisdriver driver installation failed, setup will continue non-the-less but wireless is not likely to work...;
Error:...please try to install the driver manually using 'sudo ndiswrapper -i <driver inf file name>'


errr.... I was not able to trace that here so I've added some additional debugging echos.

On another note, the upgrade feature was removed and instead a 'remove' feature was added.

remove does not return the machine to it's previous state. it only removes the scripts and the hotkeys definition file. 

sudo /etc/init.d/fsca16xx.sh remove

As always the latest is in the svn trunk.

I'll address the non working cool-n'-quiet when all bugs are gone.

---

### Post by Graes on 2007-10-04
seems to work on Feisty now i'll try reinstalling Gutsy later today only wierd problem i have now is that graphical ndis shows me : Hardware Present : NO but the WI-FI works

---

### Post by Graes on 2007-10-04
installed gutsy and this is what i get and no i have not installed the script the hotkeys dont work 

[: 376: missing ]
Welcome to the Fujitsu-Siemens Amilo A16xx automated patch for Ubuntu Gutsy

This script will enable some of the laptop features such as the Special buttons such
as Wireless, Browser and Fancy Fan

fscamiloa16xx has already been setup, nothing to do.


tried this to 

sudo ./fsca16xx.sh start
[: 376: missing ]
 * Checking for proper configuration for Fujistu-Siemens laptops              
  Missing some required files... I you haven't run the setup yet, you should. If you have, you should try remove and run setup again.
                                                                         [fail]
                                                                         [ OK ]

and this 

sudo /etc/init.d/fsca16xx.sh remove
[: 376: missing ]


and this 
sudo ./fsca16xx.sh remove
[: 376: missing ]

WIFI hotkey dont work but i have sound

---

### Post by damagedspline on 2007-10-04
> **Graes said:**
> 
[: 376: missing ]


bahh this is annoying... I was not able to find where it might be missing.

i've: 
cat fsca16xx.sh | grep "[[]" | grep -v "[]]"

and it returned no results....
I'll reseek it again later

---

### Post by J-B1985 on 2007-10-08
Hi, 

i have upgrade from Feisty to Gusty. But now my Wlan is not working good.

All my hotskeys are working fine. But if i boot my Ubuntu Gusty system the wireless lan is not starting automaticlly. I must to put it on via hotkey.

I have on /etc/modprobe.d/optons

```

options acerhk autowlan=1

```

But i don't know why this do not work. (On Feisty it worked fine)

Any idea?

*** Edit

```

$ sudo /etc/init.d/fsca16xx.sh start
 * Checking for proper configuration for Fujistu-Siemens laptops                
Missing some required files... I you haven't run the setup yet, you should. If you have, you should try remove and run setup again.
                                                                         [fail]
                                                                         [ OK ]

```

Why?

---

### Post by damagedspline on 2007-10-09
> **J-B1985 said:**
> Hi, 

i have upgrade from Feisty to Gusty. But now my Wlan is not working good.

All my hotskeys are working fine. But if i boot my Ubuntu Gusty system the wireless lan is not starting automaticlly. I must to put it on via hotkey.

I have on /etc/modprobe.d/optons

```

options acerhk autowlan=1

```

But i don't know why this do not work. (On Feisty it worked fine)

Any idea?


You should download the latest from the svn and retry setup. It should auto activate the wireless on startup.

autowlan does not auto activate the wireless on module load.

---

### Post by Count Doofus on 2007-10-21
had the same problem with my Marvell card. Looked for every kind of solution that concerned hardware interface on the PCI bus.

The Real Problem was every time I issued the 
blablabla:~$ sudo ndiswrapper -i mrv8000c.inf 
I got - No such file or directory at /usr/sbin/ndiswrapper-1.9 line 174

Until I typed the filename with the correct CASE - Mrv8000c.INF - 

GRRRRRRRRR!%@$#$###!$!@@!$@!@#! 

CASE SENSITIVE !@%#$@$@%#$% I HATE CASE SENSITIVE !!!!!!!!:mad:

---

### Post by damagedspline on 2007-11-02
I've made some changes to the script so that it will be easier to trace issues.
The old version must be removed before the new one will be setup.


therefore:
```

sudo /etc/init.d/fsca16xx.sh remove
wget http://fscamiloa16xx.googlecode.com/svn/trunk/fsca16xx.sh
chmod 755 fsca16xx.sh
sudo ./fsca16xx.sh setup

```

---

