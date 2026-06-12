---
title: "HowTo: Ubuntu on HP nx 9110 - for complete newbe!!!"
date: 2005-12-06
forum: Hardware &amp; Laptops
---

### Post by hedone on 2005-12-06
First of all... plz chek (spell) my english in this post... ;) 

what do i wanna do with this post? There is a lot of Win users who would like to have Linux on their machines, but u have to have a lot free time to find the distro that u like and then to find all of howto's to install it. 

For the start: **[COLOR="Red"]UBUNTU[/COLOR]** is my choice after trying **redhat, fedora, suse, mandrake** etc... why? best community to help you, easy installation, a lot of support for laptops.........

Ok here is the thing: about a year ago i bought HP NX9110 laptop and install windows xp pro. It's true that there was no problem with installed software but i still don't know why do i have to lose 5 to 6 days to make it work for a mounth or two and than all over again. 

I was and i belive still am preaty new to linux and i'm no expert on hardware... as u can see i'm not expert in english eader.

Let's start with hardware in NX9110:
- P4 HT 3.2 G
- 512 Mb Ram DDR
- 40 G disk
- Ati chipset
- Ati radeon 9000 IGP graphic
- Toshiba cd-rw/dvd
- 15,4' widescreen (1280x800)
- broadcom wirelless
- bluetooth by HP
- Realtek network 10/100 card

And for those who are lookin' for specific solution, here is the list of [COLOR="red"]known issues that I'm still working on [/COLOR]and have no solution yet:
- card reader 5 in 1
- SMP kernel (it's slow....)
- ACPI support for sleep and hibernate
- fglrx driver from Ati
- soft modem

I have to inform u that my way of installing desktop computer or laptop for my clients is without compiling kernel!!!! so, for this howto I used precompiled kernel! And my wish to Ubuntu team is to compile kernels that can support laptops (acpi, card reader etc.) from the box... (let's say linux-LT-686 or linux-LT-386...)


**[COLOR="red"]How to start (for win users)[/COLOR]**
1. Go to [http://www.ubuntulinux.org/ubuntu/]("http://www.ubuntulinux.org/ubuntu/") and get some informactions about ubuntu!!! U have to know what Ubuntu is!!!

2. Go to [http://www.ubuntulinux.org/download/]("http://www.ubuntulinux.org/download/"), pick up the download site that is nearest to you and download [COLOR="red"]PC (Intel x86) install CD[/COLOR] for tipe of machine that i us.

3. Burning? i hope that u know how to burn cd image to cd... do u??? if u don't see [This page]("http://www.govideo.com/Index.asp?GV=CDWriteHelp")

4. Boot your computer from cd and just press Enter when asked to choose install parameters

5. For disk partitioning... (i copmpletly switced to Linux...) you just have to confirm settings that Ubuntu offers as primary!! you will now have to give some info and wait for about 20 min and you are done installing Ubuntu!!! Yes it is that easy!!!!!! And yes... u were allways so afraid of unknown... didn't you?? ;)

6. Now log in with your username and pass!!! And yes... on my machine... sound, resolution, mice, touchpad, buttons, USB, Network (using DHCP) etc worked out of the box!!! 

7. now we have to choose the right kernel for our system... why? to speed things up!!! go to aplications -> accessories -> (right button) Terminal  -> add this lancher to panel.  Now open the terminal and ```
sudo apt-get install linux-686
``` password is the one you use for your user! confirm download by Y and wait apt-get to finish. For more inf u can see [this post]("http://ubuntuforums.org/showthread.php?t=85917")

8. before restarting to new kernel you may want to change your keyboard configuration. open terminal and ```
sudo gedit /etc/X11/xorg.conf
```
find ```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"si"
EndSection
```and change ```
"pc105"
``` to the right keyboard for you and ```
"si"
``` to layout you prefer.

9. now restart to new kernel (just restart ;)) and open terminal again and ```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
sudo gedit /etc/apt/sources.list
``` and put in ```
deb http://archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu breezy universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu breezy-security universe multiverse

deb http://ubuntu-backports.mirrormax.net/ breezy-extras main restricted universe multiverse

## PLF - http://wiki.ubuntu-fr.org/doc/plf
deb ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free
deb-src ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free

``` save it and close! Now in terminal go ```
sudo apt-get update
sudo apt-get upgrade
``` This will update all software on you new system!


10. Now for installing new needed software u can use two ways: With terminal or with Synaptic Package Manager witch u can find in System -> Administration

For my installation (i use Terminal) comand was:
```
sudo apt-get install j2re1.4 acroread mozilla-acroread acroread-plugins gstreamer0.8-plugins gstreamer0.8-lame gstreamer0.8-ffmpeg w32codecs lame sox ffmpeg mjpegtools vorbis-tools libdvdread3-dev mplayer-386 mplayer-fonts mozilla-mplayer rar xfonts-intl-european msttcorefonts libmultisync-plugin-all multisync gnomebaker ndiswrapper-utils gnome-bluetooth bluez-utils
``` This will install software that you will (i think) need on your machine!

11. Now we have to configer new software. Do ```
gst-register-0.8
``` to register installed codecs for audio and video!

Open MPlayer (Applications -> Sound & Video -> MPlayer), error will apear, just confirm and right click on display -> Preferences. In Video preferences select **xv** as Available driver and **OK**, exit.

To configure RAR, do: ```
sudo ln -fs /usr/bin/rar /usr/bin/unrar
```

for new fonts: ```
sudo fc-cache -f -v
```
We can say that first steps are behind us... but if u wanna have some othere software, u may wanna look at [http://ubuntuguide.squarecows.com]("http://ubuntuguide.squarecows.com")


12. Bluetooth!!!! Huh... that one did take about 10 hours first time i install it... as att to this howto u can download "Send file via bluetooth", unzipit and put it on Desktop. Now how to use it??? I have new Sony Ericsson K750i and the firs thing (to awoyd problems with PIN) u have to find your computers bluetooth true mobile phone. original PIN is "1234" and the device is in phones memory!

Now u can send files from phone to computer and from computer to phone through that desktop icon you put on Desktop. Just drag and drop files to that icon and it should work!

13. Sync phone with Evolution??? No problem... addressbook, calendar, tasks??? shure... open MultiSync (Applications ->  Accessories -> MultiSync). Klick on the New tab and as First plugin select [COLOR="red"]Ximan Evolution 2[/COLOR] and click Options where u can select source to sync!

Now as second plugin select [COLOR="red"]IrMC Mobile Device[/COLOR] and click Options. Connection type is Bluetooth and you can click on "Search for units..." button! YES U HAVE TO HAVE BLUETOOTH ENABLED ON MOBILE PHONE!!! 

You don't need to test connection, just OK and click on** SYNC**! 

I didn't bealive it eder when i was installin' bluetooth for the first time!!! But that actualy works!!!!! You don't wanna know how much time i spend in Windows to do that!!!

14. There is one more thing we need to do before we can say that our laptop works good enought to stay on Linux!!! Wirelless cards from Broadcom... don't be afraid... I realy don't know why this wouldnt work... just open Terminal and go:
```
ndiswrapper -l
``` to see if there is allready any drivers present.

Download windows drivers for your card and extract them somewere. now do ```
ndiswrapper -i /path/to/windrivers/bcmlw5.inf
``` where path is directory where u have extracted drivers from windows.

Again do ```
ndiswrapper -l
``` now u have to see your driver present and hardware present... if hardware is not presen, check if your card button is on!!!

Next do ```
ndiswrapper -m
``` to autoloud ndiswrapper at boot... but i have to add it manualy by adding ndiswrapper line to ```
sudo gedit /etc/modules
```

now you can ```
sudo modprobe ndiswrapper
```


15. to work with ndiswrapper i use NetworkManager... install it by ```
sudo apt-get install network-manager
```

When done run command ```
nm-applet
``` and restart ypour computer with function "save current setup" taht will remember nm-applet and start it every time you start your machine.

Now just click on nm-applet icon on uper panel and select network u wanna use!



That is it... 



And when u come back in a month or two for more info, here are some helpfull howto's:
[ATI]("http://ubuntuforums.org/showthread.php?t=78466")
[Bluetooth]("http://www.ubuntuforums.org/showthread.php?t=94713")
[Kernel]("http://ubuntuforums.org/showthread.php?t=85064")
[Lid button - sleep and hibernate]("http://ubuntuforums.org/showthread.php?t=87664")
[Speed]("http://ubuntuforums.org/showthread.php?t=89491")
[Touchpad]("http://ubuntuforums.org/showthread.php?t=97713")

---

### Post by daller on 2005-12-06
I'd really appreaciate if you would add your computer here:

[https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsHewlettPackard](https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsHewlettPackard)

And please copy the content of this page:

[https://wiki.ubuntu.com/LaptopTestingTeam/HPNX9105](https://wiki.ubuntu.com/LaptopTestingTeam/HPNX9105)

into:

[https://wiki.ubuntu.com/LaptopTestingTeam/HPNX9110](https://wiki.ubuntu.com/LaptopTestingTeam/HPNX9110)

...Thanks! :D

---

### Post by hedone on 2005-12-06
[QUOTE=daller]I'd really appreaciate if you would add your computer here:

[https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsHewlettPackard](https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsHewlettPackard)

And please copy the content of this page:

[https://wiki.ubuntu.com/LaptopTestingTeam/HPNX9105](https://wiki.ubuntu.com/LaptopTestingTeam/HPNX9105)

into:

[https://wiki.ubuntu.com/LaptopTestingTeam/HPNX9110](https://wiki.ubuntu.com/LaptopTestingTeam/HPNX9110)

...Thanks! :D[/QUOTE]

**It's on!!!** but i didn't use Hoary... does anyone have nx9110 and was useing Hoary on it?

---

