---
title: "Lucid Install on the Fujitsu u810"
date: 2010-08-09
forum: Hardware
---

### Post by kathleenhenri on 2010-08-09
How I got my Fujitsu u810 completely up and running in Ubuntu Lucid 10.04.   

 Thanks to Spareinfo.blogger.com's blog I was able to get my u810 running quite well in Jaunty. The only thing that didn't work were the keyboard lights. Not a really a necessity but I really wanted the satisfaction of being able to use them in the dark. There is a mod for them in Hardy and a new one that functions in Lucid &#8211; and I still am too much of a Linux Noob to be able to successfully compile the module from source. Up till now using Lucid on my machine has been a huge disappointment mainly because of the wireless connectivity issues that seem to be rampant in 10.04.
 

 But I was determined to make everything work. So after several re-installs, trials and errors, and many hours of scouring on-line for answers I have resolved most of the issues! So if you have a u810 collecting dust it's time to get it out and slap on the new distro and have a go with those keyboard lights while surfing in the dark . . . 



 Sites with invaluable information that I am forever indebted to:
 [[COLOR=#000080]_http://spareinfo.blogspot.com/2009/04/installing-linux-on-fujitsu-u810_07.html_[/COLOR]]("http://spareinfo.blogspot.com/2009/04/installing-linux-on-fujitsu-u810_07.html")
 [[COLOR=#000080]_http://exain.wordpress.com/2008/10/22/howto-fujitsu-u1010-u810-umpc-and-ubuntu-linux-804-hardy-heron/_[/COLOR]]("http://exain.wordpress.com/2008/10/22/howto-fujitsu-u1010-u810-umpc-and-ubuntu-linux-804-hardy-heron/")
 [[COLOR=#000080]_https://help.ubuntu.com/community/WifiDocs/Driver/Atheros_[/COLOR]]("https://help.ubuntu.com/community/WifiDocs/Driver/Atheros")
 [[COLOR=#000080]_http://madwifi-project.org/_[/COLOR]]("http://madwifi-project.org/")
 [[COLOR=#000080]_http://edtake.wordpress.com/2010/05/10/ubuntu-lucid-lynx-wireless-keep-dropping/_[/COLOR]]("http://edtake.wordpress.com/2010/05/10/ubuntu-lucid-lynx-wireless-keep-dropping/")


                                  
INSTALL LUCID
 

 Start with a fresh install of Ubuntu 10.04 Lucid. I downloaded and burned an ISO disc and booted it from an external DVD drive.
 My u810 has a 60G hard-drive and I have it set to dual Ubuntu and Windows 7 (everything works thanks to [[COLOR=#000080]_http://www.umpcportal.com/modules/newbb/viewtopic.php?topic_id=6218&forum=16_[/COLOR]]("http://www.umpcportal.com/modules/newbb/viewtopic.php?topic_id=6218&forum=16")) so I created a straight 15G / partition and 1.5G swap for Ubuntu.
 

 Update and then upgrade. I had to connect via ethernet cable for these steps.
 

 ```
sudo apt-get update  
 sudo apt-get upgrade
```
 Reboot.
 

                                  
SET UP WIRELESS
 

 I did all of the following. The last step may not be necessary but I kept trying things until I had a good wireless connection. There is no guarantee that what I did will work for you or won't break your computer. The u810 uses an AR242x 802.11abg wireless card &#8211; not so easy to make work well in Lucid or Karmic. Although wireless connections are visible with the default install, the computer could either not make a connection, or if it did, connections were slooooow and often dropped. Ethernet works fine however.
 

 **Step 1**
                                  
Enable backports.
                                  

```
sudo gedit /etc/apt/sources.list

sudo apt-get update
 

sudo apt-get install linux-backports-modules-lucid linux-backports-modules-wireless-lucid-generic

```Reboot.
 

 **Step 2**
 Install MadWifi Atheros Driver
 

 First modify a couple of files in the modprobe.d folder.
 ```
gksudo gedit /etc/modprobe.d/blacklist.conf
```Add the following lines
 
```

blacklist ath_hal
blacklist ath_pci
 
```Save and close
 

 ```
gksudo gedit /etc/modprobe.d/blacklist-ath_pci.conf
``` Leave this line blacklisted  
 [HTML]blacklist ath5k[/HTML] (Don't add # to the front of the line. Many sources suggest doing this but it didn't work for me.)
 

 
 Install preparatory software
 ```
sudo apt-get install automake mercurial build-essential libssl-dev linux-headers-`uname -r`
``` Download driver from here and save to desktop.
 [[COLOR=#000080]_http://snapshots.madwifi-project.org/madwifi-0.9.4/_[/COLOR]]("http://snapshots.madwifi-project.org/madwifi-0.9.4/")
 Right click to extract to the desktop and rename Madwifi.
 


 From terminal
```

cd Desktop
  
cd Madwifi
  
make  
  
sudo make install

``` WifiDocs suggest this step as well.  
 *Kernel 2.6.32.22 changed the default for the ****rfkill**** parameter of ****ath_pci**** from ****0**** to ****1****, which had the effect of killing the methods described above. You'll need to make sure that it's set back to ****0**** on system startup. To do that, edit (or create) the file ****/etc/modprobe.d/options.conf**** to include the line * 
 

 Create or modify the following file to save your efforts for the next boot:
```



sudo gedit /etc/modprobe.d/options.conf

```add  
 ```
options ath_pci rfkill=0
``` Save and close.
 Then from the menu go to
 Administration &#8594; Hardware Drivers and activate your new Atheros madwifi driver.
 


 **Step 3**
 Not sure if this matters but I did it with no ill effects.
 Modify the following file:
 

 ```
sudo gedit /etc/NetworkManager/nm-system-settings.conf  
``` and add or modify the following the file to:  
 

```

[main]
plugins=ifupdown,keyfile
 

 [ifupdown]
managed=true
 

 [ifdown]
managed=true
 

 [ifup]
managed=true

``` Reboot
 

 You should now have snappy, consistent wireless connections. If you update your kernel, you'll have to reinstall the driver.
 

 TOUCHSCREEN
 

 Some have suggested that the evtouch drivers will now work in Lucid, but I haven't tested them. I have had great luck with the modified driver from Spareinfo.


 Download
 [[COLOR=#000080]_http://sites.google.com/site/spareinfosite/Home/fujitsu-usb-touchscreen-0.3.5.tar.gz_[/COLOR]]("http://sites.google.com/site/spareinfosite/Home/fujitsu-usb-touchscreen-0.3.5.tar.gz")
 
Make sure to set your computer BIOS to use the touchscreen in 'tablet' mode.
This is the mode also used by Windows, and provides very sharp touchscreen accuracy.

Download the package file to any directory

```
mkdir fujitsu_touchscreen_driver
cd fujitsu_touchscreen_driver
wget[ http://sites.google.com/site/spareinfosite/Home/fujitsu-usb-touchscreen-0.3.5.tar.gz]("http://sites.google.com/site/spareinfosite/Home/fujitsu-usb-touchscreen-0.3.5.tar.gz")
```Extract the files
 
 ```
tar zxvf fujitsu-usb-touchscreen-0.3.5.tar.gz
cd fujitsu-usb-touchscreen-0.3.5
```Install the software
 
```
make
sudo make install
```Go to System &#8594; Preferences &#8594; Startup Applications &#8594; Add
 /usr/bin/fujitsu_touchscreen_rotate.py 


 Reboot.
 

 SPECIAL BUTTONS / // Rotate Screen
 

 From the terminal.
 Add the following repositories
 ```
sudo gedit /etc/apt/sources.list
```Add these two lines
```

deb http://ppa.launchpad.net/khnz/ppa/ubuntu lucid main
deb-src http://ppa.launchpad.net/khnz/ppa/ubuntu lucid main

``` Save and close.
 

```

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E88D7B6F
 

sudo apt-get update
 

sudo apt-get install fjbtndrv cellwriter xournal  

``` Reboot.
 

 MICROPHONE
To get the internal microphone to work.


```



sudo gedit /etc/modprobe.d/alsa-base.conf  

```and add this line to the bottom of the file
 ```
options snd-hda-intel model=toshiba-s06 
``` Save and close.
 Reboot.
 

 KEYBOARD LIGHTS


 Download the fujitsu-kbdlights-0.1.0.tar.gz to the desktop
 [[COLOR=#000080]_http://sites.google.com/site/spareinfosite/Home/fujitsu-kbdlights-0.1.0.tar.gz_[/COLOR]]("http://sites.google.com/site/spareinfosite/Home/fujitsu-kbdlights-0.1.0.tar.gz")

Right click to extract the file


 Compile and install
 From terminal type
```

cd Desktop
cd fujitsu-kbdlights-0.1.0
sudo bash
make
make install

``` From terminal or command shell, you can type any of the following 

```
fujitsu_kbdlights on

fujitsu_kbdlights off

fujitsu_kbdlights toggle

fujitsu_kbdlights 
``` XBINDKEYS
 

 To associate the keyboard lights with the / Button and cellwriter with the // Button do the following
 

 From terminal type
```

sudo apt-get install xbindykeys xbindkeys-config
 
```Then
 ```
xbindkeys --defaults > $HOME/.xbindkeysrc
sudo xbindkeys-config
``` At the bottom click New, and follow the prompts in the Edit box upper right corner.  
 Name it kbdlight or whatever you want.
 Press the Get Key.
 A little window pops up.
 Then press the  / button to get the key code.
 Then enter the command in the action box.
 In this case I chose the command fujitsu_kbdlights toggle
 Run action to make sure it works.
 At the bottom click save and give it a name.  
 

 Do the same thing for the // Button.
 Click new
 Name it.
 Get key by pressing // button
 Action is cellwriter.
 Save, give it a name, and exit.
 

 To autostart xbindkeys go to Go to System &#8594; Preferences &#8594; Startup Applications &#8594; Add  
 xbindkeys
 


 WEBCAM
 The webcam works in cheese and skype but is mirrored.
 

 Make sure the following is installed:
```
sudo apt-get install libglib2.0-dev libusb-dev build-essential gcc automake mercurial
``` Then```


hg clone http://bitbucket.org/ahixon/r5u87x/
cd r5u87x
make
sudo make install
sudo r5u87x-loader &#8211;reload
sudo apt-get install cheese

```

---

