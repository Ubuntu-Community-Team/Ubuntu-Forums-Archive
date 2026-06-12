---
title: "Help with dell and wireless"
date: 2007-01-18
forum: Hardware &amp; Laptops
---

### Post by ovrundr on 2007-01-18
Hello everyone. 
I am having trouble getting my wireless network up and running. Her is what I have:

Dell inspiron 1150
Broadcom Corporation BCM4306 802.11b/g 
Ubuntu 6,10


I followed this post:
[http://www.ubuntuforums.org/showthread.php?t=340689&highlight=dell+wireless+BCM4306](http://www.ubuntuforums.org/showthread.php?t=340689&highlight=dell+wireless+BCM4306)
and used the ndiswrapper how-to as a reference.

step I have followed:

1> installed ndiswrapper to include ndiswrapper-utils-1.8
2> disable current driver
                     echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
3> installed the new driver 
                    sudo ndiswrapper -i bcmwl5.inf
4> ndiswrapper -l   output:
                    bcmwl5          driver installed, hardware present
5> load the new driver
                    sudo depmod -a
                    sudo modprobe ndiswrapper
6> tail /var/log/messages
                     Jan 18 08:39:50 bradbr-laptop kernel: [17180503.232000] ndiswrapper version 1.34                  loaded (preempt=no,smp=yes)
                    Jan 18 08:39:50 bradbr-laptop kernel: [17180503.324000] usbcore: registered new driver ndiswrapper
7> iwconfig output:
                   lo        no wireless extensions.

                   eth0      no wireless extensions.

                   sit0      no wireless extensions.
8> ifup wlano output:
                   Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; No such device.
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.




So it looks like I missed something along the way. Does anyone see what I missed or have any suggestion on what to look for.

Thanks

---

### Post by stalkier on 2007-01-18
Hey buddy. I have run Ubuntu 5.10 and 6.10 on my laptop which is a Compaq Pressario V2000 series with the same Broadcom WiFi card as yours. There is a  Linux Driver out now but you have to search for it. I forget where it is exactly. It took me a couple weeks to get my WiFi working right on my laptop. After all, the OS is free so there are going to be things that don't work quite right. it is really just trial and error. Just keep trying and scan the Forums. I hope it helps you.

---

### Post by stalkier on 2007-01-18
I found this on my search when I had Ubuntu installed. I hope it helps.

BCM43xx on Ubuntu Dapper
Disclaimer: These instructions should work, but I have not verified each step. They are simpler than the instructions presented below. Please contribute if you use these instructions successfully. 
Automatically Installing
The easiest way to install the Broadcom43xx drivers in Dapper is to execute a script that has already been written for this purpose. Before you execute the script, you'll need to install the bcm43xx-fwcutter package. (Note: You must be connected to the internet in order for apt-get and the script to work properly.) 
sudo apt-get install bcm43xx-fwcutter
sudo /usr/share/bcm43xx-fwcutter/install_bcm43xx_firmware.sh 
Everything should be installed properly and work now. If it doesn't work, there are some hints at the bottom of this page to help you out. 
Manually Installing
If your wireless card was inserted during the install of (or upgrade to) Dapper Drake, then once your shiny new system boots you can run 
lsmod | grep bcm43xx
to confirm that the driver is installed. 
However it doesn't work on its own: you need to extract the firmware from the Windows driver. You need the .sys file from your CD; mine was called bcmwl5.sys. You can extract the firmware using bcm43xx-fwcutter, which is available in the Universe repository. Make sure you have Universe enabled, and type 
sudo apt-get install bcm43xx-fwcutter
and once it is installed, extract the firmware from the driver: 
bcm43xx-fwcutter /path/to/bcmwl5.sys
This will create a few files in the /lib/firmware directory. 
You might want to rename your wireless interface from eth1 or whatever it defaults to. Edit the file /etc/iftab and replace eth1 with wlan0 or whatever you want to call it. 
Essentially everything should work now if you are not using security; just go into System > Administration > Networking and configure the interface, then fire it up and start surfing. 
WEP Security
WEP is fairly weak security. It can be easily configured through the Networking menu, or you could edit the file /etc/network/interfaces to include a stanza like 
auto wlan0 
iface wlan0 inet dhcp
   wireless-essid MyAccessPoint
   wireless-key 0123012345
Type man wireless at the command prompt to see information about wireless configuration. 
WPA Security
WPA is strong security for wireless networks, and many users will be using WPA-PSK (pre-shared key). You'll need to install the "supplicant" (or client) for WPA: 
sudo apt-get install wpasupplicant
You can configure your system to use WPA simply by editing your /etc/network/interfaces file to include the stanza 
auto wlan0 
iface wlan0 inet static
   wpa-ssid "MyAccessPoint"
   wpa-psk "My Secret Passphrase"
   address 192.168.1.6
   netmask 255.255.255.0
If your access point gives you an IP address through DHCP, then you don't need to have the address and netmask bits, and you should change static to dhcp. You should prevent people from reading this file if you use this method (using sudo chmod go-rwx /etc/network/interfaces) to prevent anyone from seeing your passphrase. 
The ability to configure WPA through /etc/network/interfaces is fairly new, and described in /etc/wpa_supplicant/wpa_supplicant.conf. To see all the possible commands you can issue using wpa-COMMAND, take a look at the wpa_supplicant.conf manual page. 
If this doesn't work, you can still start up wpa_supplicant yourself. Edit the file /etc/wpa_supplicant/wpa_supplicant.conf to include your ssid and passphrase, and then issue the commands 
sudo ifconfig wlan0 up 
sudo wpa_supplicant -i wlan0 -D wext -c /etc/wpa_supplicant/wpa_supplicant.conf -d
You'll get some debugging output, which should tell you if you're authenticated to your access point. You can also open up another terminal and use the wpa_cli command to see what's going on; on of the more useful things is to ask for status: sudo wpa_cli wlan0 status. 
BMC43xx has only worked with WEP and WPA since January 2006, so this is still perhaps a little experimental. Conventional wisdom has it that if you get WPA to work, you might have trouble with DHCP; try using a static IP address if you're having trouble. 
There is a GUI for wpa_supplicant which is currently available in Universe; take a look at package wpagui. 
Related manual pages: wireless, interfaces, iwconfig, wpa_supplicant, wpa_cli, wpa_supplicant.conf 
Using the ndiswrapper driver, fixing your system
If you've upgraded and your internet is broken, and you use a broadcom 43xx card, and you would like to still use ndiswrapper (because it was working, and you want it to remain working), simply do: 
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
This will make it so the bcm43xx driver doesn't load, and ndiswrapper will be happy, after you reboot your computer. To get it working without a reboot, simply run these commands: 
sudo rmmod bcm43xx
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
Using the bcm43xx driver
Now, if you would like to use this driver, first  uninstall ndiswrapper. Alternatively, (what I do), you can keep ndiswrapper installed and just blacklist it: 
echo 'blacklist ndiswrapper' | sudo tee -a /etc/modprobe.d/blacklist
Now you have two options. The first of which is to install a simple deb, the other version is extracting the firmware yourself. The first method is recommended. 
First Method: 
wget [http://ubuntu.cafuego.net/pool/bcm43xx/bcm43xx-firmware_1.0-0ubuntu1_i386.deb](http://ubuntu.cafuego.net/pool/bcm43xx/bcm43xx-firmware_1.0-0ubuntu1_i386.deb)
sudo dpkg -i bcm43xx-firmware_1.0-0ubuntu1_i386.deb
Now you're ready to skip down to the "Skip down to here!" header. 
The second method isn't as easy, or as pretty, but it's highly elite, here it is: 
Acquire the source for fwcutter by either: 
svn checkout svn://svn.berlios.de/bcm43xx/trunk/fwcutter
or by downloading and extracting the archive by: 
wget [http://download.berlios.de/bcm43xx/bcm43xx-fwcutter-003.tar.bz2](http://download.berlios.de/bcm43xx/bcm43xx-fwcutter-003.tar.bz2)
tar xjf bcm43xx-fwcutter-003.tar.bz2
Now, go into the fwcutter directory and run these commands to compile: Note, you'll probably need build-essential installed. 
make 
make install
If you have ndiswrapper working with your card previously, there is probably this file: 
/etc/ndiswrapper/bcmw15/bcmwl5.sys 
copy it to the fwcutter directory by: 
cp /etc/ndiswrapper/bcmw15/bcmwl5.sys .
If it's not there, get it by: 
wget [http://metahusky.net/~gavin/home/bcmwl5.sys](http://metahusky.net/~gavin/home/bcmwl5.sys)
Now type: 
sudo ./bcm43xx-fwcutter -w /lib/firmware/ bcmwl5.sys
Skip down to here!
Now you have your firmware installed, either by the deb or manually. 
Now, if you look at iwconfig, you should get an entry similar to: 
lo             no wireless extensions

eth0           no wireless extensions

eth1           IEEE 802.11b/g ESSID:"seekret"  Nickname:"Broadcom 4306"
               Mode: Managed  Frequency=2.462 GHz  Access Point: 13:37:be:ef:13:37
               Bit Rate=11 mB/s  Tx-Power=15 dBm
               RTS thr:off   Fragment thr: off
               Encryption key: yeah right    Security mode: open
By this time, some of you following this may have a working card, just ifconfig eth1 up, and run dhclient eth1, and you may get an address (depending on how your wireless AP is set up). 
If you have a broadcom 4318 card then you need some extra configuration 
sudo iwconfig eth1 rate 11M
sudo iwconfig eth1 ap any
If this all works then you need to add a pre-up script to your interface in '/etc/network/interfaces' 
add this line to your interfaces file: 
iface eth1 inet dhcp 
    pre-up /path/to/file/network_Startup_script
in /path/to/file/network_Startup_script my script looks like this: 
#!/bin/bash ifconfig eth1 up 
if [ `iwlist scan 2> /dev/null | grep ubc | wc -l` -ge 1 ] # this looks for my usual essid at school and connects to it if it's present, change ubc to your usual essid then 
    myEssid="ubc" ## change to your essid
else 
    myEssid="any" # finds any open essid and connects to it 
fi 
    myInterface="eth1" # typically eth1 but may be something 
else 
    iwconfig $myInterface essid $myEssid &>/dev/null 
#sudo iwconfig $myInterface ap any &>/dev/null # uncomment if you have issues with invalid access point issues 
iwconfig $myInterface rate 11M # &>/dev/null # necessary part of script for bcm4318 driver and usually bcm4306
NOTE: there are more elegant ways to do this but I haven't experimented with them 
Looking at /var/log/messages, you may see some messages concerning your card and driver. One of the bottom-most messages may say something silly like: 
ADDRCONF(NETDEV_UP): eth1: link is not ready
This means your card isn't set up correctly, and is most likely not working. 
Sometimes it's difficult to get that link to be ready -- but once it is, it'll work. Keep trying, don't give up!  
For me, running this command solved this problem: 
sudo iwconfig eth1 mode auto
sudo iwconfig eth1 rate 11M
sudo iwconfig eth1 ap any
Now, surely, this driver should work. Feel free to make changes or corrections or comments to this file. 
Troubleshooting
If you don't see your device under iwconfig or ifconfig -a, make sure you have your ndiswrapper driver unloaded: 
sudo rmmod ndiswrapper
and make sure you have the bcm43xx driver loaded: 
sudo modprobe bcm43xx
The result of the command lsmod|grep -i bcm should be similar to: 
bcm43xx             114444   0
ieee80211softmac    28544    1  bcm43xx
ieee80211           35144    2  bcm43xx,ieee80211softmac
________________________________________
Troubleshooting techniques: keep trying iwconfig commands. Perhaps explicately stating your AP might work. There's something about SoftMAC and authentication that needs to occur for your device to start working. 
________________________________________
I can see the essid but can't get an ip address
try setting your wireless card to 11M as it's the only setting that works for 4306 and 4318 broadcom cards. 
sudo iwconfig eth1 rate 11M
________________________________________
Removing wifi-radar because of driver conflict
If you can scan and see access points but can't connect, make sure you don't have wifi-radar installed! It runs a daemon that conflicts with the bcm43xx driver. 
sudo aptitude purge wifi-radar
________________________________________
==="Network down"=== If you get the "Network down" message, or other errors when your card is "recognized", and you used the first method of installation, and last but not least there are no files beginning with "bcm43xx" in /lib/firmware/, try loading the drivers manually. This only needs to be done once... 
sudo bcm43xx-fwcutter -w /lib/firmware/ bcmwl5.sys
________________________________________
Access Point: Invalid
If you get "Access Point: Invalid' like this below 
lo             no wireless extensions

eth0           no wireless extensions

eth1           IEEE 802.11b/g ESSID:"seekret"  Nickname:"Broadcom 4306"
               Mode: Managed  Frequency=2.462 GHz  Access Point: Invalid
               Bit Rate=11 mB/s  Tx-Power=15 dBm
               RTS thr:off   Fragment thr: off
               Encryption key: yeah right    Security mode: open
then you need to run this command to fix it up 
sudo iwconfig eth1 ap any
the real issue stem from not specifing a essid, so specify on in your /etc/network/interfaces file as mentioned above in the section "If you have a broadcom 4318 card then you need some extra configuration" 
Router not braodcasting it's essid
Is your router broadcasting it's essid? Some driver's have issues if the essid isn't broadcast. (i.e. bcm4306 and bcm4318) 
KISS priniciple for encrypted network troubleshooting
Finally, encypription is good, but to get wireless cards working use 'scary' un-encrypted network, then add the encryption back in once it's working.

---

### Post by ovrundr on 2007-01-18
Tried going back to the default driver (bcm43xx) and it seems to see the hardware now but maybe a problem with the access point?

iwconfig

wlan0     IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4306"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Rick

---

