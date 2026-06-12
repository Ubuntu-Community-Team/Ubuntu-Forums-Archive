---
title: "NIGHTMARE!!!  trying to get wireless working."
date: 2005-01-23
forum: Hardware &amp; Laptops
---

### Post by RU63 on 2005-01-23
I have a Acer Travelmate 290 with a centrino chip. I have been trying all day to get the wireless working.  I have been reading websites and people say it should work and that ipw2200 comes with warty.  Is there a newer install disk for warty?  mine had ipw2100... even when i use synaptic i only get the option of installing 2100... and i have all the repositories llisted in the guide.  


I tried to follow some instuctions on howto get the ipw220o working but now I have 'No Wireless Devices' by the icon.  Before i did this i could see my wireless device but it wouldn't work.

i was hoping someone could post a HOWTO install ipw 2200 or how to get Wireless working

thx

---

### Post by Spif on 2005-01-23
Take a look at these sites: [http://ipw2100.sourceforge.net/](http://ipw2100.sourceforge.net/) and [http://ipw2200.sourceforge.net/](http://ipw2200.sourceforge.net/)

I succesfully installed the driver for ipw2200 a few hours ago, so if you have any questions regarding the installation, please feel free to ask.

---

### Post by RU63 on 2005-01-23
Do you have a similar laptop to me?  Are you wireless now?  i think i am messed.... cus when i type iwconfig... i no longer see eth1

i don't remember what i did... i think i might reinstall ubuntu and try again... 

Could u make a HOWTO for the howto forum on what u did to get 2200 installed successfully?

---

### Post by Spif on 2005-01-23
**Intel Pro/Wireless 2200BG HowTo**

1.Before we start, make sure you have the appropriate linux-headers installed for your kernel. If you are not sure which kernel you are currently using, open a console and type

*cat /boot/grub/menu.lst*

Scroll to the bottom where you will find information regarding your kernel. For example, if you have the kernel 2.6.8.1-3-386, you will need the package *linux-headers-2.6.8.1-3-386*.

*sudo apt-get install linux-headers-2.6.8.1-3-386*
 
2.Later in this guide you will need components from the *build-essential *package. If it is not already installed, do so by typing

*sudo apt-get install build-essential*

     in the console

3.Next step is to download the iwp2200 driver: [http://prdownloads.sourceforge.net/ipw2200/ipw2200-0.21.tgz?download](http://prdownloads.sourceforge.net/ipw2200/ipw2200-0.21.tgz?download)

4.You will also need the latest version of the binary firmware. Download here: [http://prdownloads.sourceforge.net/ipw2200/ipw2200-0.21.tgz?download](http://prdownloads.sourceforge.net/ipw2200/ipw2200-0.21.tgz?download)

5.When you have finnished downloading, write

*sudo mv ipw2200-fw-2.2.tgz /usr/lib/hotplug/firmware/*

     to move the file to the correct folder, then

*cd /usr/lib/hotplug/firmware*

     to go there yourself. Now the file needs to be extracted.

*sudo tar zxf ipw2200-fw-2.2.tgz*

6.If you got to this step without any error, the firmware has been set up correctly. Now you must move the driver to /usr/scr, so type

*sudo mv ipw2200-0.21.tgz /usr/src*

     then

[I]cd /usr/src
[/I]
     and finaly

*sudo tar zxf ipw2200-0.21.tgz*

     to extract it.

7.Enter the newly extracted folder by writing

*cd /usr/src/ipw2200-0.21*

     The driver needs to be compiled. But first check for any problems by using sudo make. If it returned any errors, you have not installed the build-essential package and the appropriate linux-headers. If it on the other hand worked flawlessly, type 

*sudo make install*

8.The driver has now been installed, but in order for it to work you must restart your computer or type 
[I]
sudo modprobe ieee80211[/I]

     and

*sudo modprobe ipw2200*

     in the console. 

9.To check whether your wireless functions, write

*sudo iwconfig*

10. Enjoy your new wireless connection!

---

### Post by jerome bettis on 2005-01-23
AWESOME HOWTO SPIF

that should be stickied or in the faq section!!!!!!111

---

### Post by Spif on 2005-01-23
[QUOTE=jerome bettis]AWESOME HOWTO SPIF

that should be stickied or in the faq section!!!!!!111[/QUOTE]

Thanks :grin:

---

### Post by imightbegiant on 2005-01-23
I'm certain that I've installed both the build-essential package as well as the linux-headers for my kernel. The firmware is also in place, but when I try to make the driver I get:
-
[I]make -C /lib/modules/2.6.8.1-4-386/build SUBDIRS=/usr/src/ipw2200-0.21 MODVERDIR=/usr/src/ipw2200-0.21 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.8.1-4-386'
  Building modules, stage 2.
  MODPOST
Warning: could not find versions for .tmp_versions/ipw2200.mod
make[1]: Leaving directory `/usr/src/linux-headers-2.6.8.1-4-386'[/I]
-

make install fails with the same warning message and says 
[I]
Don't forget to copy firmware to /usr/lib/hotplug/firmware/ and have the
hotplug tools in place.[/I]


Any ideas?

---

### Post by Spif on 2005-01-23
[QUOTE=imightbegiant]I'm certain that I've installed both the build-essential package as well as the linux-headers for my kernel. The firmware is also in place, but when I try to make the driver I get:
-
[I]make -C /lib/modules/2.6.8.1-4-386/build SUBDIRS=/usr/src/ipw2200-0.21 MODVERDIR=/usr/src/ipw2200-0.21 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.8.1-4-386'
  Building modules, stage 2.
  MODPOST
Warning: could not find versions for .tmp_versions/ipw2200.mod
make[1]: Leaving directory `/usr/src/linux-headers-2.6.8.1-4-386'[/I]
-

make install fails with the same warning message and says 
[I]
Don't forget to copy firmware to /usr/lib/hotplug/firmware/ and have the
hotplug tools in place.[/I]


Any ideas?[/QUOTE]

I believe I got the exact same error as you, but *sudo make install* worked flawlessly anyway. If possible, just continue the compiling and you should be fine. The part about hotplug tools should come up not matter what.

---

### Post by imightbegiant on 2005-01-23
It seems that the driver is loaded fine, but the kill switch is always being interpreted as active. rf_kill is at level 2 - " HW based RF kill active (radio off)" I saw a similar problem in a posting that suggested trying [http://rfswitch.sourceforge.net](http://rfswitch.sourceforge.net) but I'm not sure how to use it, or if it's what I need. My laptop is the NoteMagix B50 Ultra from Velocity Micro.

---

### Post by ilari on 2005-01-23
Good HowTo, but there is a few things I would advice doing differently.

1. You can check the current kernel version by typing command 'uname -r' in terminal. It is more reliable than checking grub.lst, which can include multiple kernel versions.

2. There is no need to unpack or compile the module as root (using sudo). I would keep all the packages and source under my home directory (eg. /home/<username>/source), and extract (tar zxvf ipw2200.tar.gz) and compile it (make) as a regular user . Only use sudo when installing (sudo make install) and loading (sudo modprobe ipw2200) the module.

3. Also unpack the firmware under user home (eg. /home/<username>/firmware), and just copy the needed files using sudo (sudo cp * /usr/lib/hotplug/firmware).

However, these are just small details...

---

### Post by RU63 on 2005-01-24
i did this great howto....but it didn't work.  Then I reinstalled Ubuntu because i looked at the: /proc/modules and saw that i had 2100 in there.  So i got rid of it... then suddenly my eth1 was gone.  Well on reinstalation I noticed that my centrino wireless is a 2100... so me thinks i need to focus on getting it to work with the 2100? 

What I am about to try is downloading the AcerHK and making sure the firmware is ok... SOOO FRUSTRATING!

---

### Post by RU63 on 2005-01-24
still not working, although signal strength is 100% and when i type iwconfig, it reads my router... i will post a new thead on networking as not to take away from Spif's HOWTO.

Peace,

---

