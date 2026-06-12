---
title: "NDISWRAPPER on Broadcom"
date: 2005-04-05
forum: Hardware &amp; Laptops
---

### Post by blu.gecko on 2005-04-05
I checked out the "ndiswrapper" website and they are installing the same driver in the how to directions, so Im not sure if I am doing something wrong or what but I installed ndiswrapper-utils on my Compaq Presario 2210US with a Broadcom 802.11g,  I installed the package from the cd direct and I get the

-i
-m
-this
-that

when I type in ndiswrapper xterm

I type sudo ndiswrapper -i/source/folder/file.inf

and the it just says

ndiswrapper options

-i install inf driver
-m modeprobe 
-and
-so
-on

what am I doing wrong, I love this desktop OS but im real close to windowsing my notebook.


I NEED HELP!@#$% 8-[

---

### Post by greatshape on 2005-04-05
[QUOTE=blu.gecko]
when I type in ndiswrapper xterm

I type sudo ndiswrapper -i/source/folder/file.inf

and the it just says

ndiswrapper options

-i install inf driver
-m modeprobe 
-and
-so
-on

what am I doing wrong, I love this desktop OS but im real close to windowsing my notebook.


I NEED HELP!@#$% 8-[[/QUOTE]

Try  ading a space: 
sudo ndiswrapper -i  /source/folder/file.inf

good luck

---

### Post by blu.gecko on 2005-04-05
I have tried everything

sudo ndiswrapper -i/cdrom0/swsetup/wlan/file.inf

and this is not working for me, on 5.0.4 do you have to install more than just the ndiswrapper-utils, in the discription of that application is says something about the kernel.

thanks for any assistance.  8-[ 

blu.gecko

---

### Post by acascianelli on 2005-04-05
[QUOTE=greatshape]Try  adding a space: 
sudo ndiswrapper -i  /source/folder/file.inf

good luck[/QUOTE]

....

---

### Post by kperkins on 2005-04-05
[QUOTE=blu.gecko]I have tried everything

sudo ndiswrapper -i/cdrom0/swsetup/wlan/file.inf

and this is not working for me, on 5.0.4 do you have to install more than just the ndiswrapper-utils, in the discription of that application is says something about the kernel.

thanks for any assistance.  8-[ 

blu.gecko[/QUOTE]
You need to add a space between the -i and the source file address--as greatshape said.

---

### Post by blu.gecko on 2005-04-06
I installed the ndiswrapper-utils from the 5.0.4 cd I downloaded, but it seems that I need the ndiswrapper-source, where can I get the ubuntu.deb for this?
I installed the driver but without the source my driver wont work and ndiswrapper will not fire up my Wlan.

blu.gecko :?

---

### Post by kperkins on 2005-04-07
Well ndiswrapper-source is right in the apt repositories.  Search in synaptic.
My Broadcom driver isworking fine without the ndiswrapper-source package.

---

### Post by telmo on 2005-04-07
Just do a search in this forum, and you'll find the solution! ;)

---

### Post by blu.gecko on 2005-04-08
Well ndiswrapper-source is right in the apt repositories. Search in synaptic.
My Broadcom driver isworking fine without the ndiswrapper-source package.

I did a search for ndiswrapper and all I got was NDISWRAPPER-utils

I can install the drivers, and uninstall them now just fine, but since I do not have the source files, I get "driver issue!"

I know this laptop works with linux and wireless becuse it works just fine with mandrake 10.1 dvd without any configuration.

blu.gecko

---

### Post by blu.gecko on 2005-04-09
right now I am working from my wife's laptop which is xp, so forgive me. my wi-fi isnt working yet.

I re formatted and tried this again. I installed ndiswrapper-utils
I ran sudo ndiswrapper - i /media/cdrom0/swsetup/bcmwl5.inf

I got the message "driver installed, harware installed"

I downloladed the ndiswrapper source files from ubuntu's a-z download section
[http://security.ubuntu.com/ubuntu/pool/universe/n/ndiswrapper/](http://security.ubuntu.com/ubuntu/pool/universe/n/ndiswrapper/)  
but it will not install properly, so I am stumped on how I am supposed to get the source in so I can get my wireless back up.  :-? 


I am half working, before I was just getting started.
BTW I am a linux newb so, I dont understand alot of konsole and xterm terms.
this is why I am trying to stay with deb files only.

blu.gecko

---

### Post by krrh on 2005-04-09
[QUOTE=blu.gecko]right now I am working from my wife's laptop which is xp, so forgive me. my wi-fi isnt working yet.

I re formatted and tried this again. I installed ndiswrapper-utils
I ran sudo ndiswrapper - i /media/cdrom0/swsetup/bcmwl5.inf

I got the message "driver installed, harware installed"

I downloladed the ndiswrapper source files from ubuntu's a-z download section
[http://security.ubuntu.com/ubuntu/pool/universe/n/ndiswrapper/](http://security.ubuntu.com/ubuntu/pool/universe/n/ndiswrapper/)  
but it will not install properly, so I am stumped on how I am supposed to get the source in so I can get my wireless back up.  :-? 


I am half working, before I was just getting started.
BTW I am a linux newb so, I dont understand alot of konsole and xterm terms.
this is why I am trying to stay with deb files only.

blu.gecko[/QUOTE]
 Why would you need the source files if you aren't compiling anything? (Maybe you are planning to compile something, but your previous posts don't suggest this is so.)

---

### Post by joshmachine on 2005-04-09
Yup, you don't need ndiswrapper source.  If you are getting the message that the driver installed you are almost done.  

At this point the driver is installed, but the kernel hasn't been told about it yet.  You need to type 

$ sudo modprobe ndiswrapper

this load the ndiswrapper module into the kernel.
now type 

$ ifconfig wlan0   

wlan0 is the name that will be assigned to your wireless device.

Upon reboot the portion of the system which is responsible for loading up the drivers for the hardware that you have installed (this is called hotplug) should detect it and load this at boot time.  

At this point you just need to configure the device and start your fun wireless action.

Cheers

---

### Post by gray_ru on 2005-04-10
Maybe it is same problem as mine.
I have Belkin wireless PCMCIA card F5D7010 with Broadcom chipset. It was recognized by Ubuntu and Device manager shows it right. Right after the setup of the box I installed ndiswrapper-utils and ran ndiswrapper -i bcmwl5a.inf. OK, ndiswrapper -l shows me 'bcmwl5a driver present, hardware present".
After that I ran modprobe ndiswrapper and then lsmod shows me that ndiswrapper is loaded, iwconfig shows wlan0 interface but card if not actually up - led is not up and it see no wlans when scans though of cource there is one. 
Exactly the same procedure fired up wi-fi in Gentoo without any problem.
Any ideas what to do and why ndiswrapper cannot fire up the card?

---

### Post by gray_ru on 2005-04-10
Huh, it is worth to read the forum - as for me, [this](http://www.ubuntuforums.org/showpost.php?p=116707&postcount=2)  helps.

---

### Post by jonny on 2005-04-10
Try [this](http://ubuntuforums.org/showthread.php?p=125537#post125537).

---

### Post by blu.gecko on 2005-04-11
Thanks for the help guys, I had to reload XP to read the forum on the how to since my AC97 Modem would not activate in Linux properly. I am in the process of changing over to linux, Im all about the free software state of mind.

Now all that I need to do is fix my dialup modem issue and install a good web editor.


blu.gecko

all thumbs up  hope this fix, fix's my wireless problem

---

### Post by hyde on 2005-04-11
OK, this seems to be very common problem. I had exactly same issue with my Broadcom based card.You find the solution for your problem from this link: [http://ubuntuforums.org/showthread.php?t=24988](http://ubuntuforums.org/showthread.php?t=24988)

Remember that you must be root when editing those conf files.

---

### Post by blu.gecko on 2005-04-14
Ok I got it fixed,  but I didnt have to configure any files, here's how I did it.

sudo ndiswrapper -i /media/cdrom0/swsetup/bcmlw5.inf
sudo ndiswrapper -l
driver found, hardware present
sudo modprobe ndiswrapper
goto "administrator" goto "Network" goto "Wireless Adapter" then "Activate"

"reboot"

sudo ndiswrapper -m

"reboot"

power on broadcom wireless button.

FIXED.

THANKS GUYS & GALS  :grin:

---

