---
title: "Video Card Problem"
date: 2009-01-17
forum: Hardware
---

### Post by jamrop on 2009-01-17
I have a Nvidia 6600LE Pci-e card

I installed Ubuntu 8.10 yesterday and am having some trouble getting the drivers for my video card . When I go to my hardware drivers, I see the option to install Nvidia drivers. When I select them and press install it asks for my root password and it says downloading and installing but nothing happens. No green light is activated when done.

I restarted the machine many times, but will not activate.

Also if i try and change the desktop effects, it tries to activate and then says it could not be enabled.

Many thanks

---

### Post by minsf on 2009-01-17
Please go to the terminal (applications>accessories>terminal) and enter ```
jockey-gtk -l
```
then post the output of this here.

---

### Post by jamrop on 2009-01-17
hey

here you go

jophiel@jophiel-desktop:~$ jockey-gtk -l
xorg:nvidia-173 - NVIDIA accelerated graphics driver (version 173) (Proprietary, Disabled, Not in use)
xorg:nvidia-96 - NVIDIA accelerated graphics driver (version 96) (Proprietary, Disabled, Not in use)
xorg:nvidia-177 - NVIDIA accelerated graphics driver (version 177) (Proprietary, Disabled, Not in use)

---

### Post by minsf on 2009-01-17
hmm... i was hoping to get only the 177 and then tell you how to install this manually. 
do you have a laptop or a dektop? what model/manufacturer?

---

### Post by jamrop on 2009-01-17
Hey

It is a custom made desktop pc

Amd 1gb 6600LE gigabyte motherboard, not sure what processor is of the top of my head

What stops it from activating?

Many thanks

---

### Post by minsf on 2009-01-17
i dont know what stops it from running and i dont know why it gives us three drivers instead of one. but i read about your card and it seems you need the 177 driver. now please post the output of the following command in the terminal
```
uname -a
```

---

### Post by RJARRRPCGP on 2009-01-17
You probably weren't patient enough! You probably cut the download off! It should move from 0 percent if you waited about another 1 minute! [-X

---

### Post by jamrop on 2009-01-17
Hey

Uname -a 

Linux jop-desktop 2.6.27-9-generic #1 SMP Thu Nov 20 21:57:00 UTC 2008 i686 GNU/Linux

as for not waiting long enough, waited 10 minutes, but it always has a window come up, saying downloading then installing, then the windows disappears, and nothing happens

---

### Post by chkh on 2009-01-17
hey,

i'm having the exact same problem with the exact same setup(ubuntu 8.10, custom desktop with amd and nvidia 6600)

When i typed "jockey-gtk -l" the same three command lines came up but mine has a slightly different result which that is version 177 is (Propriertary,Disabled, In Use) *instead of "Not in use"* 

before i couldnt boot into my desktop, i used add/remove program to install the version 177 and use hardware drivers to activate it and it told me to restart to finish installation. when i restarted, i couldnt enter anymore.

jamrop take a look over here.
[http://ubuntuforums.org/showthread.php?t=968723&page=2](http://ubuntuforums.org/showthread.php?t=968723&page=2)

---

### Post by minsf on 2009-01-17
JAMROP, (and only jamrop! chkh- i will answer you in a seperate post, but i do NOT think you should follow the same steps)

please follow the following steps. if something goes wrong, stop and let me know (ideally post the error here). if you get a blank screen at some point, try to use alt+ctrl+f1 to get to the terminal, or boot from the live cd, connect to the internet and let me know. 

1. before we start, please enter the following command in the terminal```
sudo lshw -C display
``` and post here the output.

by the way, if you want to get some info about your hardware (because you said you forgot what CPU you have) enter ```
sudo lshw | less
``` then you can scroll up and down and you exit it by ressing q

2. in the terminal, please enter ```
sudo apt-get install linux-generic
``` this will install a package that is required for the driver. you will be asked to enter your password. if you are asked to confirm that you want to install the package together with other packages it depends on, enter Y. most likely this package is already installed on your computer, but we have to be sure before we continue.

3. next, i need you to back up the file /etc/X11/xorg.conf
you do this by entering the following command ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old
``` please notice the capital X in X11. the case matters in all commands! this command means we copy the original file to a file with a similar name +.old
that is, if something ever goes wrong after we change the xorg.conf file, we can always go replace it with the original file by the command "sudo mv /etc/X11/xorg.conf.old /etc/X11/xorg.conf" without the quotes. cp is for copying, mv is for moving. sudo is to get the right permissions to handle this file. 

by the way, if you want to learn more about the command line interface, check [www.linuxcommand.org](www.linuxcommand.org)

4. the you need to install the driver. you do it by entering the following command ```
sudo apt-get install nvidia-glx-180
``` you may be asked to enter your password. enter Y when asked to confirm installing the package and its dependencies.

by the way, a good guide to understand installations in ubuntu is here
[http://ubuntuforums.org/showthread.php?t=781352](http://ubuntuforums.org/showthread.php?t=781352)

5. we need to enable the driver. you do this by entering the command ```
sudo nvidia-xconfig --no-composite
```

6. reboot

---

### Post by minsf on 2009-01-17
CHKH, when you reboot, do you get the ubuntu splash screen (with the bar that fills itself)? if you get a black screen after the splash screen, i want you to try CTRL+ALT+BACKSPACE. if this doesnt work try ctrl+alt+F1 to get to the command line interface. (you may be asked to login) then enter ```
sudo uname -a
``` (you may be asked for your password) and post here the output. also post here the output of ```
sudo lshw -C display
``` the latter command can be run from a live cd, but for the uname i dont think we'll get the desired result if run from a live cd

---

### Post by jamrop on 2009-01-17
Hey i tried what you said, but nothing worked

here are the results

```
sudo apt-get install linux-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-generic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package linux-generic has no installation candidate

```

Here is the driver install results

```
sudo apt-get install nvidia-glx-180
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package nvidia-glx-180

```

and here is what you asked me for

```
sudo lshw -C display
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: NV43 [GeForce 6600 LE]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0

```

many thanks

---

### Post by minsf on 2009-01-17
JAMROP:

a silly question: you are connected to the internet when you run "sudo apt-get install linux-generic", right?

assuming you are, go to System>Administration>SoftwareSources
you'll be asked for your password
in the window that opens, in the first tag ("ubuntu software" tag) make sure that the first 4 boxes are checked (that is, main universe restricted and multiverse). close the software resources window.

my guess is that at least the restricted is not currently checked, and therefore it doesnt let you download the restricted packages linux-generic and nvidia-glx-180

if i am right, then this may be the reason why "Hardware Detection" didnt finish downloading. So after checking those boxes, try hardware-detection again. if it still doesn't work, go again to the step2 in my last post (addressed to you). installing linux-generic and nvidia-glx-180 should work now.

---

### Post by chkh on 2009-01-17
yup i got the splash screen, and enter right into the command lines screen(ctrl+alt+f1) automatically.

"sudo uname -a" results:
"Linux calvin-dsesktop 2.6.27-9-generic #1 SMP Thu Nov 20 21:57:00 UTS 2008 i686 GNU/Linux

"sudo lshw -C display" results:
*-display
description : VGA compatible controller
product : NV43 [Geforce 6600]
vendor : nVidia Corporation
physical id : 0
bus info : pci@0000:02:00.0
version : a2
width : 64 bits
clock: 33MHz
capabilities : pm msi pciexpress bus_master cap_list
configuration : driver=nvidia latency=0 module=nvidia

just a newbie question, what is the live cd? is it the ubuntu os cd? :)

---

### Post by minsf on 2009-01-17
yes the "live cd" is the ubuntu installation cd. you can always use it to boot (and get internet connection, terminal, etc) but beware: it will NOT save your work (unless you mount the hard disk, but i can explain that some other time). we need you to go through the normal boot and the alt+ctrl+f1, since we want the all the settings that we do to be saved.

---

### Post by minsf on 2009-01-17
a little explanation for both of you:

you can see that in jamrop's output he has "UNCLAIMED" in his output, next to "* display". this means that jamrop has not yet installed the driver. hopefully, after he enables the restriced repositories, he'll be able to download and install the driver, and will be in the same phase as chkh.

also, you can see the chkh has already downloaded the driver, since he doesnt have the "unclaimed" and also if you look in the configuration, he has driver="nvidia".

guys i know it may be frustrating in the beginning, but i was there too- i had black screens too for some time. and remember there is no better way to learn about linux than by trying to fix things. in a month you'll be helping some other guys with black screens... :)

---

### Post by minsf on 2009-01-17
CHKH, 
1. i want to know what driver is installed on your system. to do this go to the terminal with the alt+ctrl+f1 procedure, and enter ```
aptitude search nvidia | grep "i "
```(notice the space after the i ) and post the output here.
2. as mentioned above, your driver is installed. the reason for the black screen is that the configuration file xorg.conf is not good. we will need to fix it. but before we do that, we should back up your current file, by making a copy named xorg.conf.old 
to do it run ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```note that capital X in X11 is important.
(so if there we ever want to go back to the original file we would run "sudo cp /etc/X11/xorg.conf.old /etc/X11/xorg.conf")

when i have the output from 1, i will guide you further

---

### Post by jamrop on 2009-01-18
hey

it worked :)

did not have the restricted drivers clicked :( can not believe it was to do with a tick 

thanks for your help

---

### Post by minsf on 2009-01-18
JAMROP,
glad to hear it worked!
have you rebootes since then?
some people get a black screen when the reboot, after installing nvidia driver (like CHKH). If you do, come back here and i will help you edit your xorg.conf file and fix it.
otherwise- enjoy!

---

### Post by jamrop on 2009-01-18
Everything is up and running great :)

thanks again

---

### Post by chkh on 2009-01-18
1. "aptitude search nvidia | grep "i "  "  results :
The program 'i' is currently not installed. You can install it by typing: sudo apt-get install iprint
-bash: i : command not found

sorry for the late reply on this. Really appreciating your help! totally agree with you on the point that hopefully one day i'll be in your position guiding and helping others too :) 

cheers mate!

---

### Post by minsf on 2009-01-18
> **chkh said:**
> 1. "aptitude search nvidia | grep "i "  "  results :
The program 'i' is currently not installed. You can install it by typing: sudo apt-get install iprint
-bash: i : command not found

this does not make sense. the only quotes in the command are around the i+SPACE right? (that is no quotes before the aptitude, right?)

well, the idea was that the ```
aptitude search nvidia
``` shows all the available nvidia packages. those that are already installed on your system should start with "i ", so that the grep filter will throw everything else, and output only those that have been installed on your system. so try to run the aptitude command above and just tell me the packages that are installed on your system (their lines start with "i ")

---

### Post by chkh on 2009-01-18
i know.. i didnt put any quotes besides from those that u told me too :)
and yes, there is a space after the i. this is wat came out. is not right? perhaps i should try again.

---

### Post by s0rg on 2009-01-18
Same issue I am getting on the same card but I am running Intel Pentium D I tried different ones but they all come with and odd low resolution which I tried to change, and when I control+alt+backspace it goes to a weird screen giving me 3 options about the new drivers. tried different ones. :( and the desktop effects wont work either. I hope we all can find a solution.

---

### Post by minsf on 2009-01-18
> **chkh said:**
> i know.. i didnt put any quotes besides from those that u told me too :)
and yes, there is a space after the i. this is wat came out. is not right? perhaps i should try again.

basically i need you to run ```
aptitude search nvidia
``` and post here all the lines that start with i
you are going to need to be connected to the internet while you do that

another, possibly better option is 
```
sudo dpkg -l | grep nvidia
```

---

### Post by minsf on 2009-01-18
> **s0rg said:**
> Same issue I am getting on the same card but I am running Intel Pentium D I tried different ones but they all come with and odd low resolution which I tried to change, and when I control+alt+backspace it goes to a weird screen giving me 3 options about the new drivers. tried different ones. :( and the desktop effects wont work either. I hope we all can find a solution.

go to the command line interface (Applications>Accessories>Terminal, but if you are using kubuntu you will have to open Konsole). at the prompt, enter the command ```
sudo lshw -C display
``` cut and past the output here (to cut from the terminal, you'll use ctrl+SHIFT+c, rather then the standard ctrl+c)

---

### Post by chkh on 2009-01-18
p   nvidia-180-kernel-source   -NVIDIA binary kernel module source
p   nvidia-180-modaliases      -Modaliases for the nvidia binary X.org dri
p   nvidia-71-kernel-source    -NVIDIA binary kernel module source
i   nvidia-71-modaliases       -Modaliases for the NVIDIA binary X.org dri
p   nvidia-96-kernel-source    -NVIDIA binary kernel module source
i   nvidia-96-modaliases       -Modaliases for the NVIDIA binary X.org dri
p   nvidia-cg-toolkit          -NVIDIA Cd Toolkit Installer
i   nvidia-common              -Find obsolete NVIDIA drivers
v   nvidia-glx                 -
p   nvidia-glx-173             -NVIDIA binary Xorg driver
p   nvidia-glx-173-dev         -NVIDIA binary Xorg driver development file
i   nvidia-glx-177             -NVIDIA binary Xorg driver
p   nvidia-glx-177-dev         -NVIDIA binary Xorg driver development file
p   nvidia-glx-180             -NVIDIA binary Xorg driver
p   nvidia-glx-180-dev         -NVIDIA binary Xorg driver development file
p   nvidia-glx-71              -NVIDIA binary Xorg driver
p   nvidia-glx-71-dev          -NVIDIA binary Xorg driver development file
p   nvidia-glx-96              -NVIDIA binary Xorg driver
p   nvidia-glx-96-dev          -NVIDIA binary Xorg driver development file
v   nvidia-glx-dev             -
p   nvidia-kernel-common       -NVIDIA binary kernel module common files
v   nvidia-kernel-source       -
i A nvidia-settings            -Tool of configuring the NVIDIA graphics dr
p   nvidia-xconfig             -The NVIDIA X Configuration Tool

This is the results from aptitude search nvidia

How do i get internet connection by inserting the live cd?

---

### Post by minsf on 2009-01-18
CHKH,
have you already backed up the file xorg.conf?
if not, go ahead and do step 2 in my post #17

A)if you did, then after you get the command line interface via ctrl+alt+f1 i need you to run the following three commands:
```
sudo /etc/init.d/gdm stop
```
which will stop Gnome Desktop Manager
```
sudo apt-get install nvidia-xconfig
```
this nvidia-xconfig package generates a new xorg.conf file for nvidia drivers. usually it is installed automatically when the driver is installed. not sure why, but according to your last output it is not installed yet.
```
sudo /etc/init.d/gdm restart
```
to restart gnome. 

B) if this doesnt work, do ctrl+alt+f1 again and run the following three commands ```
sudo /etc/init.d/gdm stop
```then ```
sudo nvidia-xconfig
```and then ```
sudo /etc/init.d/gdm restart
```

c) if this still does not work, do ctrl+alt+f1 again, then 
```
sudo /etc/init.d/gdm stop
``` then we need to edit the xorg.conf file, so enter ```
sudo nano /etc/X11/xorg.conf
``` this is a simple editor. locate the "section Device" and insert the following line right before the "EndSection line 
```
Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    [COLOR="Red"]Option         "UseDisplayDevice" "DFP"[/COLOR]
EndSection

```
(the other lines may be different in your case- the important thing is to add the red line). then save with ctrl+o and exit with ctrl+x. finally enter ```
sudo /etc/init.d/gdm restart
```

hope this will help. if not, i'll still be here :)

---

### Post by geezerone on 2009-01-18
Just came across this thread and I too haven't managed to get a 6600 card working on restricted hardware drivers (black screen after Ubuntu loading screen).

Tried adding 
[COLOR=Red]Option         "UseDisplayDevice" "DFP"

[/COLOR] but still the same. I have the 169 driver I believe. Only way to get x working is via recovery mode and fix xserver option

---

### Post by minsf on 2009-01-18
GREEZERONE,
169 driver? that's weird...
ok, i'll help you, but i need more info.
please post here the output of the following command in the terminal/konsole:
```
sudo lshw -C display
```
similarly, i need the output of
```
sudo dpkg -l | nvidia
```
and the output of 
```
uname -a
```

---

### Post by chkh on 2009-01-19
hey minsf,

It's still the same..hmm..its kinda disappointing dude...but i'm not willing to go back to windows yet!haha..so please let me know what info u need from me to solve my prob.

---

### Post by geezerone on 2009-01-19
```
 
sudo lshw -C display

*-display               
       description: VGA compatible controller
       product: NV43 [GeForce 6600]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-3.0 vga_controller bus_master cap_list
       configuration: driver=nvidia latency=32 maxlatency=1 mingnt=5 module=nvidia

``````
sudo dpkg -l | grep nvidia

rc  nvidia-glx                                 1:96.43.05+2.6.24.16-23.56                           NVIDIA binary XFree86 4.x/X.Org driver
ii  nvidia-glx-new                             169.12+2.6.24.16-23.56                               NVIDIA binary XFree86 4.x/X.Org 'new' driver
ii  nvidia-kernel-common                       20051028+1ubuntu8                                    NVIDIA binary kernel module common files
ii  nvidia-settings                            1.0+20080304-0ubuntu1.1                              Tool of configuring the NVIDIA graphics driver

```
```
uname -a

2.6.24-23-generic #1 SMP Thu Nov 27 18:44:42 UTC 2008 i686 GNU/Linux
```

When I try 'sudo apt-get install nvidia-glx-180' it cannot find the package.

---

### Post by minsf on 2009-01-19
CHKH
> **chkh said:**
> hey minsf,

It's still the same..hmm..its kinda disappointing dude...but i'm not willing to go back to windows yet!haha..so please let me know what info u need from me to solve my prob.
i need some more information about what you tried and did not work.
also could you please post the output of ```
ls /etc/X11
```
and the output of ```
glxinfo | grep version
```

i also need you to post the contents of the file /etc/X11/xorg.conf

dont give up!

---

### Post by chkh on 2009-01-19
oh..okay sure..here's the result from post #28

a) Err http://[COLOR="Red"]my[/COLOR].archieve.ubuntu.com intrepid/universe nvidia-xconfig 1.0+20080522-1 ubuntu1
could not resolve 'my.archieve.ubuntu.com'
Err [http://archieve.ubuntu.com](http://archieve.ubuntu.com) intrepid/universe nvidia-xconfig 1.0+20080522-1 ubuntu1
could not resolve 'archive.ubuntu.com'
failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/n/nvidia-xconfig/nvidia-xconfig_1.0+20080522-1ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/n/nvidia-xconfig/nvidia-xconfig_1.0+20080522-1ubuntu1_i386.deb) could not resolve 'archive.ubuntu.com'
E: Unable to fetch some achives, maybe run apt-get update or try with --fix-missing?

That's the error message for step a). :)


b) Using X configuration file: "/etc/X11/xorg.conf",
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

and that's the results from step b) after i restarted GNOME display manager..still tty1 screen.

c) For this, i'm still in the tty1 screen after restarting GNOME display Manager. Am i suppose to be directed straight into desktop once i restart the GNOME display manager?
Another thing, for this nano thing ryte, its saved once i press ctrl+o..then it will display 'written 66lines' to 'written 67lines' correct? :)

i was getting interested in ubuntustudio instead of standard ubuntu :) but probably the same prob should occur ryte?
What are the benefits from ubuntustudio and xubuntu?
sorry that i'm straying bit off topic..haha..but is just these questions for now. :)

---

### Post by chkh on 2009-01-19
for ls /etc/X11 :

app-defaults   xkb           Xresources
cursors        xorg.conf     Xsession
default-display-manager  xorg.conf.20090118021521  Xsession.d
fonts   xorg.conf.backup   Xsession.options
X    xorg.conf.failsafe   SvMConig
xinit    xorg.conf.old   Xwrapper.config


for  glxinfo | grep version

Error: unable to open display.

Hope this is useful. thanks!

---

### Post by minsf on 2009-01-20
> **chkh said:**
> 
for  glxinfo | grep version

Error: unable to open display.

this is weird... the driver is installed but the glxinfo is not. hmmm... also you were able to run nvidia-xconfig but it does not seem to be installed according to your output of "aptitude search nvidia" from a few posts ago. 

i'm thinking of reinstalling the driver. before that let's be sure that it is the correct driver. let's get some exact info on your graphic card. according to the output of lshw that you posted a couple of days ago, it sits at 0000:02:00.0 so please enter:
```
sudo lspci -ns 0000:02:00.0
```
and post the output here.

just so you know, we seem to have a problem with the refrech rate spacified in the xorg.conf so i would really like to see the screen+display+monitor sections in your /etc/X11/xorg.conf file
also, what monitor are you using? (vendor, model)
maybe wwe can google the correct rates for that model and put them in the xorg.conf

regarding your questions, since the problem seems to be with the settings in xorg.conf and since both gnome and xfce and kde use these settings, i dont think that anything will change if you move to xubuntu/kubuntu. its just a different look. i dont know much about studio.

---

### Post by minsf on 2009-01-20
also the error from step (a) suggests that you were either (i) not connected to the internet while running it or (ii) having problem with DNS resolutions or (iii) having problems with the source file. 
as for the latter, please post the non-comment lines in the file /etc/apt/sources.list you can do this with the command
```
cat /etc/apt/source.list | grep -v \#
```
so that we can be sure you dont have a problem with the enabled repositories. 

just out of curiousity, how do you connect to the internet? different computer? dual boot?

i imagine it must be very frustrating, but i think we are getting very close to identifying the problem and fixing it :)

---

### Post by chkh on 2009-01-20
for sudo lspci -ns 0000:02:00.0

---

### Post by minsf on 2009-01-20
> **chkh said:**
> for sudo lspci -ns 0000:02:00.0

you forgot to post the output...
:)

---

### Post by minsf on 2009-01-20
> **chkh said:**
> Am i suppose to be directed straight into desktop once i restart the GNOME display manager?
you are supposed to first have the graphic login screen, and then go to the desktop.
but, i assume you still have black screens when you restart gnome, right?

> **chkh said:**
> Another thing, for this nano thing ryte, its saved once i press ctrl+o..then it will display 'written 66lines' to 'written 67lines' correct? :)

seems ok to me

---

### Post by chkh on 2009-01-20
I'm using a Samsung 932 B plus. :)

Section "monitor"
identifier  "monitor0"
vendorname  "unknown"
ModelName   "unknown"
Horizsync   30.0 - 110.0
VertRefresh 50.0 - 150.0
Option      "DPMS"
End Section

Section "Screen"
Identifier   "screen0"
Device       "Device0"
Monitor      "Monitor0"
DefaultDepth 24
option       "UseDisplayDevice" DFP"
SubSection   "Display"
*Reloading Common Unix Printing System: cupsd
*Reloading system log daemon...
End SEction

for sudo lspci -ns 0000:02:00.0

02:00.0 0300: 10de:0141 (rev a2)


Oh...it's my 3yrs old desktop that doesnt have a LAN connection or built in wifi receiver. So i'm using a wifi D-link usb adapter to connect...i don't think i'm getting the connection as the light is not blinking on the adapter but when i'm in ubuntu's desktop before this prob. it can connect immediate during the first boot after installation.


cat /etc/apt/source.list | grep -v \# result:

cat: /etc/apt/source.list: No such file or directory


But Xubuntu is lighter than ubuntu right?I'm just curious of the actual benefits and disadvantages.haha.. i hope we'll almost there!haha..

---

### Post by minsf on 2009-01-20
> **chkh said:**
> 
cat /etc/apt/source.list | grep -v \# result:

cat: /etc/apt/source.list: No such file or directory


you have a little typo here- it is supposed to be "sources.list" rather than "source.list". that's why it cannot find the file

---

### Post by chkh on 2009-01-20
cat /etc/apt/sources.list | grep -v \# result:

grep: invalid option -- '#'
Usage: grep [OPTION].. Pattern [File]...
try 'grep --help' for more infomation.

sorry for typo. :)

---

### Post by minsf on 2009-01-20
> **chkh said:**
> cat /etc/apt/sources.list | grep -v \# result:

grep: invalid option -- '#'
Usage: grep [OPTION].. Pattern [File]...
try 'grep --help' for more infomation.

sorry for typo. :)

are you sure that you typed it correctly? you didnt forget the last slash did you? i ask because i get the same error when i dont use the last slash. also be sure that all slashes are going in the right direction. unfortunately, its important.

if you still get an error, then basically what i was hoping to get with this command is the lines in the sources.list file that do not start with #. so you can also view the file with 
```
less /etc/apt/sources.list
```
and post here all the lines that do NOT start with #

---

### Post by minsf on 2009-01-20
> **chkh said:**
> 
Section "Screen"
Identifier   "screen0"
Device       "Device0"
Monitor      "Monitor0"
DefaultDepth 24
option       "UseDisplayDevice" DFP"
SubSection   "Display"
*Reloading Common Unix Printing System: cupsd
*Reloading system log daemon...
End SEction

are you sure this is your screen section from xorg.conf?
i bet something interrupted the output, can you check it again?
also could you post the Device section?

---

### Post by chkh on 2009-01-21
sorry for that, i must have miss out a slash or direction of slash.

here's the results :
deb [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) intrepid main restricted

deb [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb-src [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted

deb [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) intrepid universe
deb-src [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) intrepid-updates universe
deb-src [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) intrepid-updates universe

deb [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb-src [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse
deb-src [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse



deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse

---

### Post by chkh on 2009-01-21
Yeah, i'm sure, i just double checked!:)

Section "Screen"
Identifier "screen0"
Device "Device0"
Monitor "Monitor0"
DefaultDepth 24
option "UseDisplayDevice" DFP"
SubSection "Display"
Depth 24

EndSection

Section "device"
identifier  "device0"
driver  "nvidia"
vendorName "NVIDIA Corporation"
option  "UseDisplayDevice" "DFP"
End Section

---

### Post by minsf on 2009-01-21
> **chkh said:**
> sorry for that, i must have miss out a slash or direction of slash.

here's the results :
deb [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) intrepid main restricted

deb [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb-src [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted

deb [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) intrepid universe
deb-src [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) intrepid-updates universe
deb-src [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) intrepid-updates universe

deb [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb-src [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse
deb-src [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse



deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse

this looks good to me. no worries about the typo :)

---

### Post by minsf on 2009-01-21
before we reinstall the driver, i want to try to edit the xorg.conf file a bit more.
i couldnt find "932B plus" but i did find some specifications for samsung's 932B, so i hope they'll work. if you have the monitors specifications in your user manual or somewhere else, then definitely let me know. especially, we need your horizontal and vertical refresh rates, and the native or maximum resolutions.

to edit your xorg.conf, you enter the command ```
sudo nano /etc/X11/xorg.conf
```

according to the specifications that i found, you should change your xorg.conf file so that it looks like this:
```

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
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
    VendorName     "Samsung"
    ModelName      "932B"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    Option         "UseDisplayDevice" "DFP"
EndSection

Section "Screen"

    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

```

especially notice that the UseDisplayDevice option is in the device section, not in the screen section. pay special attention to the display subsection inside the screen section- i think it's the source of our problems. also notice the change in refresh rates in the monitor section.
save aith ctrl+o, exit with ctrl+x, and restart gnome with
```
sudo /etc/init.d/gdm restart
```

just a reminder to be very precise when editing, double check for typos.

i really hope this will work and we will not need to reinstall the driver :)

---

### Post by minsf on 2009-01-21
i forgot to mention: do not touch the keyboard and mouse sections. i posted them here just so you have an idea how they look like, but they may be a bit different in yours. at any rate, they are not related to our problem, so we should not touch them.

---

### Post by chkh on 2009-01-22
done the steps that u've told me too..dude..after i restart it's still the same. i didnt get anywhere. still in the same old black screen. but the screen did blink for a few secs..haha..otherwise no diff. god...this is miserable..haha..

---

### Post by minsf on 2009-01-22
I finally found your monitor's user manual:

if this link does not work, go to samsung's website, choose "support" then choose "download center" and then type "932BPLUS" in option 1 and click "search. then you can download the user manual in pdf. near the end, page 68 i believe, you can see the refresh rates.

in page 70 they say that in some syetems vertical refrech rates may actually be a bit more than 75, so i suggest you try to change the 75 to 76 in the xorg.conf
dont forget to save the file and restart gnome with "sudo /etc/init.d/gdm restart". did it help?

another thing: try to comment out the option "UseDisplayDevice" "DFP".
you do this by inserting # before the entire line. 
i am not sure if this option is good or bad for you, so you should play with it every once in a while... dont forget to save and restart gnome.

if this still does not help, my next post will explain how to reinstall your driver...

---

### Post by minsf on 2009-01-22
to uninstall the driver, enter
```
sudo apt-get purge nvidia-glx-177
```
and
```
sudo apt-get autoremove
```

after you do this i want the output of 
```
sudo dpkg -l |grep nvidia
```
to be sure that you no longer have the nvidia driver installed
then i will explain how to install the latest driver.

to prepare for the installation i want you to run
```
sudo apt-get install gcc linux-headers-generic build-essential pkg-config xserver-xorg-dev
```
this will install some packages needed for a successful installation of the driver

---

### Post by angliski on 2009-01-22
I had a similar problem Hardware drivers said driver was installed but it wouldn't work except at low res.

I fixed it by the following:

applications >add/remove >system tools then type nvidia in search box and look at the nvidia drivers to install the one you want. Worked a treat for me.

Hope this helps


Steve

---

### Post by minsf on 2009-01-22
> **angliski said:**
> applications >add/remove >system tools then type nvidia in search box and look at the nvidia drivers to install the one you want.
thanks steve.
however, this doesnt seem to be relevant, since this guy has a blank screen after boot, so he cannot get to the desktop and choose "system"... besides, his driver is installed as can be seen in the output of lshw that he posted (i think on page 2) and in the output of "aptitude search nvidia" that he posted (somewhere around page 4 of the thread).
thanks anyway :)

---

### Post by chkh on 2009-01-23
hey minsf,

The problem has been resolved already! but its cause i change a new grahic card. ATi 4670 for 300bucks. oh well..it's working like a charm now. but thank you so so much! you've been so helpful and patient with my 4yrs old ancient pc..sorry for the trouble dude! Your help is much appreciated!

---

### Post by minsf on 2009-01-24
> **chkh said:**
> hey minsf,

The problem has been resolved already! but its cause i change a new grahic card. ATi 4670 for 300bucks. oh well..it's working like a charm now. but thank you so so much! you've been so helpful and patient with my 4yrs old ancient pc..sorry for the trouble dude! Your help is much appreciated!

glad it's working!
enjoy :)

---

### Post by Mellifluous on 2009-01-24
I'm having exactly the same problem as the OP! I'm a complete newb to Linux. I just installed Ubuntu 8.10 on my laptop. Unfortunately my wireless card won't connect for some reason and I have this problem with the nvidia drivers. Here is the output of the jockey thing:

xorg:nvidia-173 - NVIDIA accelerated graphics driver (version 173) (Proprietary, Disabled, Not in use)
kmod:wl - wl (Proprietary, Enabled, In use)
xorg:nvidia-177 - NVIDIA accelerated graphics driver (version 177) (Proprietary, Disabled, Not in use)

The driver downloads but then nothing happens. Help!

---

### Post by minsf on 2009-01-24
> **Mellifluous said:**
> I'm having exactly the same problem as the OP! I'm a complete newb to Linux. I just installed Ubuntu 8.10 on my laptop. Unfortunately my wireless card won't connect for some reason and I have this problem with the nvidia drivers. Here is the output of the jockey thing:

xorg:nvidia-173 - NVIDIA accelerated graphics driver (version 173) (Proprietary, Disabled, Not in use)
kmod:wl - wl (Proprietary, Enabled, In use)
xorg:nvidia-177 - NVIDIA accelerated graphics driver (version 177) (Proprietary, Disabled, Not in use)

The driver downloads but then nothing happens. Help!
check the following thread that i opened for you:
[http://ubuntuforums.org/showthread.php?p=6611158#post6611158](http://ubuntuforums.org/showthread.php?p=6611158#post6611158)
this way people can help you without reading 6 pages of this thread :)

---

