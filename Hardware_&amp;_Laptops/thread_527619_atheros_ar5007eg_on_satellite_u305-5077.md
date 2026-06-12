---
title: "atheros ar5007eg on satellite u305-5077"
date: 2007-08-16
forum: Hardware &amp; Laptops
---

### Post by ntlam on 2007-08-16
Hi all

I got problem with my wireless on my Toshiba Satellite U305-5077. Even I tried many times with solutions in several threads I got no success. 
As I looked at Windows, the information about my card is: Atheros Ar5007EG.
Some reports said that madwifi doesn't support AR5007EG (it supports most of atheros chips but not this one).
I tried using Ndiswrapper and used "net5211.inf" from XP driver (32 bit) as it is suggested in some threads. I failed ...
Here is what I did:

 Step 1: Disable ath_pci

sudo rmmod ath_pci
sudo gedit /etc/modprobe.d/blacklist-common

add the following line at the end of the file

blacklist ath_pci

Save and close

Restart computer

step 2. remove old ndiswrapper by using synaptics

Step 3: Build essentials
Use the synaptic package manager
Install the package called "build-essential" in the group called "Development"
But I already got it installed

Step 4: Install Ndiswrapper.

Go to [http://sourceforge.net/project/showf...group_id=93482](http://sourceforge.net/project/showf...group_id=93482)
Download ndiswrapper-1.47.tar.gz to folder /home/username

Code:

cd /home/username/
sudo tar xvzf ndiswrapper-1.47.tar.gz
cd /home/username/ndiswrapper-1.47/
sudo make
sudo make install

Step 5: Load drivers with ndiswrapper.
sudo ndiswrapper -i net5211.inf

installing net5211 ...

forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
........ a lot of lines like above...

then:
sudo ndiswrapper -l
net5211 : driver installed
device (168C:001C) present (alternate driver: ath_pci)

Step 6: Load ndiswrapper and check if it worked
sudo modprobe ndiswrapper

Check it:
iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

Then I did:

sudo ndiswrapper -m

After reboot I got no wireless.

I asked for help in some threads but haven't got answer yet. Hope I get some idea here. Thanks

---

### Post by ntlam on 2007-08-16
Never mind. I got it work.

Step 1:
Because I tried Madwifi before so I had to remove it:
Code:
cd /lib/modules/$(uname -r)
sudo rm -rf net
sudo rm -rf madwifi
sudo rm -rf madwifi-ng

Then:
cd /to your directory of madwifi-version, do the following:
sudo make clean (you can do this step again and again to make sure madwifi is removed completely)

Code: (Check for the existence of any wlan, ath_hal, ath_pci modules)
lsmod

Remove  existing loaded modules:
sudo rmmod (moduleName)

reboot

Step 2: (you might not have to do this step if you haven't installed ndiswrapper)

remove the installed ndiswrapper by doing:

cd /directory of ndiswrapper-1.47/

sudo rmmod ndiswrapper
sudo make distclean
sudo make -C driver clean

Go to Places-->seach for files, seach ndiswrapper, you will see a list of ndiswrapper files and folders. In the command line go to each location to delete ndiswrapper either with sudo rm (for files) or sudo rm -r (for folders).

Step 3:

Then go back to directory of ndiswrapper-1.47/
sudo make
sudo make install

Step 4:

And finally install the driver:

cd /directory of XP driver/

sudo ndiswrapper -i net5211.inf (your file would be different, something like file.inf)
ndiswrapper -l ==> if u see this message: "net5211: driver installed device (168C:001C (not same with ur )

sudo modprobe ndiswrapper

dmesg (show that the card installed)
iwlist wlan0 scan (will show all APs arround you)

sudo ndiswrapper -m

sudo reboot

And the wireless should work.

---

### Post by jediackbar on 2007-08-17
So if I haven't tried anything yet, just follow steps 1-6 on the first post?  I would also skip step 2?  In step 3, what is the 'build essentials...'?

---

### Post by ntlam on 2007-08-17
ndiswrapper was installed by default so you need to remove it and get the newest one. But the old one might work...you can try. "Build essentials" means you get everything necessary for it to work..

---

### Post by jediackbar on 2007-08-17
I followed your directions and I don't thing it worked.  I must have messed something up.  I installed ndiswrapper and then installed the XP driver, but still nothing.  When I click on the network connection on the taskbar all I see is wired network and modem.

"step 2. remove old ndiswrapper by using synaptics" - How do you do that?

"Step 3: Build essentials
Use the synaptic package manager
Install the package called "build-essential" in the group called "Development"
But I already got it installed"  

Again, what or how?

---

### Post by ntlam on 2007-08-17
go to system-->administration-->synaptic package manager--->search for what u need..

---

### Post by jediackbar on 2007-08-17
It still doesn't work.  I don't see any wireless connection under the network screen.  I think that my card still isn't working.  

"Step 5: Load drivers with ndiswrapper.
sudo ndiswrapper -i net5211.inf"

I get that the 'driver is already installed'

---

### Post by ntlam on 2007-08-18
you have to remove the driver and ndiswrapper then install fresh ones

---

### Post by ntlam on 2007-08-18
My post #2 tells you how to remove them

---

### Post by tturrisi on 2007-08-18
The issue w/ that chipset is not a linux, ubuntu or madwifi issue, it's an issue w/ HAL.
[http://madwifi.org/wiki/Compatibility/Atheros#AtherosAR5007EG](http://madwifi.org/wiki/Compatibility/Atheros#AtherosAR5007EG)

---

### Post by jediackbar on 2007-08-18
i tired those steps above and the ones you linked to but I'm still having trouble.  I think I'm missing something really simple but I don't know what.  
When I do the "iwlist wlan0 scan (will show all APs arround you)" I get a message saying that wlan doesnt support scanning.  I still think that I have trouble getting the system to recognise the card.

---

### Post by ntlam on 2007-08-19
how is your progress?

---

### Post by jediackbar on 2007-08-20
Well, I have a different wireless card than you.  I doubled checked and Vista is reporting that I have a 'Intel Wireless WiFi Link 4965AGN'.  That would explain why I have had no luck with it.

---

### Post by ntlam on 2007-08-20
sorry to hear that.

you have to search for solution for your exact wireless card.

good luck

---

### Post by jediackbar on 2007-08-20
I got it working.

[https://help.ubuntu.com/community/WifiDocs/Driver/Intel_4965_AGN_WiFi_Driver/Fiesty?highlight=%28WifiDocs%2FDriver%29](https://help.ubuntu.com/community/WifiDocs/Driver/Intel_4965_AGN_WiFi_Driver/Fiesty?highlight=%28WifiDocs%2FDriver%29)


By the way, do you know how to increase the screen resolution.  I'm stuck at 1024x768.  That is the largest it will let me go.  And how do you get the back button on the mouse to work?  These sound really trivial but I am slowly learning Linux.

Also, I have to type "sudo modprobe ndiswrapper" whenever I start up in order to get wireless.  I don't think ndiswrapper is loading but I dont know how to change it.

---

### Post by ntlam on 2007-08-20
wireless:
sudo modprobe ndiswrapper
then:
sudo ndiswrapper -m

For the resolution: try installing 915resolution by using synaptic package manager

let me know it it works

mouse:
what exactly is the problem?

---

### Post by blahquaker on 2007-08-21
I'm having trouble getting my wireless working...

I went through the instructions here and elsewhere and ndiswrapper seems to think the driver is installed correctly, but nothing else (iwconfig, iwlist, ifconfig, etc) seems to know my wireless card exists.

I tried adding wlan0 with the mac to /etc/iftab (something I found in another thread) but it's still not recognized anywhere.

any help would be appreciated.

toshiba a215-s4807, ubuntu 7.04, amd64, atheros ar5007eg.

---

### Post by ntlam on 2007-08-21
can you try removing all the drivers you've installed and re-install ndiswrapper like in post #2 in this thread?

---

### Post by ntlam on 2007-08-21
remember when you install file.inf you also need the file.sys in the same place.

---

### Post by jediackbar on 2007-08-21
when I try "sudo modprobe ndiswrapper" and then "sudo ndiswrapper -m" I get a message saying 'module configuration already contains alias directive'

As for the mouse, I have  a Logitech MX500 USB, everything works fine but the 2 buttons for the thumb that allow you to go forward and back in Firefox.

---

### Post by ntlam on 2007-08-21
> **jediackbar said:**
> when I try "sudo modprobe ndiswrapper" and then "sudo ndiswrapper -m" I get a message saying 'module configuration already contains alias directive'

As for the mouse, I have  a Logitech MX500 USB, everything works fine but the 2 buttons for the thumb that allow you to go forward and back in Firefox.

Did you reboot after doing: sudo ndiswrapper -m

so your problem is: you have to do the command: sudo modprobe ndiswrapper every time you reboot? 

I haven't experienced this problem yet...

check if you turn off the wireless button.

the mouse: Some functions of mouse and keyboard are different in linux. Such as the "Back space" on keyboard does not go back to the previous page but gets you to the head of the present page. I dont know if there is a way to get them work the same in windows. You can try searching...

---

### Post by blahquaker on 2007-08-22
ok, I got mine to recognize the interface. I just had to try a couple more drivers before I found the right one for my system.


> **jediackbar said:**
> when I try "sudo modprobe ndiswrapper" and then "sudo ndiswrapper -m" I get a message saying 'module configuration already contains alias directive'

is ndiswrapper in /etc/modules? another thread suggested you add it to make it start automatically:
```
echo "ndiswrapper" | sudo tee -a /etc/modules
```

---

### Post by Rockman4140 on 2007-08-25
> **blahquaker said:**
> ok, I got mine to recognize the interface. I just had to try a couple more drivers before I found the right one for my system.

I myself am looking to get wireless access on my laptop. It is a Toshiba Satellite A215-S4817, so I'm thinking the drivers you found may help. By chance would it be possible to post a link or give me tips? The bmartin method didn't quite work.

I'm still a Linux n00blet, and I was figuring if/when I get my wireless up and running, I could tinker with it more to work on my mouse settings and getting my card to work.

---

### Post by tturrisi on 2007-08-25
> **Rockman4140 said:**
> I myself am looking to get wireless access on my laptop. It is a Toshiba Satellite A215-S4817, so I'm thinking the drivers you found may help. By chance would it be possible to post a link or give me tips? The bmartin method didn't quite work.

I'm still a Linux n00blet, and I was figuring if/when I get my wireless up and running, I could tinker with it more to work on my mouse settings and getting my card to work.

Go to the toshiba site & download the windows wlan drivers for your laptop model.  Most are usually self extracting exe files.  If you dual boot, download them when in windows, else download on a windows pc.  Run the exe and extract the files to a any dir, preferable a new dir.  Then copy those extracted files to a usb drive, floppy or cdr so can be put onto your linux system.

---

### Post by Rockman4140 on 2007-08-25
I heard from a friend at work that when he installed it on his girlfriends computer, it was more of an issue with the Wi-Fi switch on the laptop itself than an issue with the driver. This makes more sense, because ndiswrapper never "detected" my card.

---

### Post by Rockman4140 on 2007-08-25
I downloaded it and found out that it is a self-extracting zip. I changed the .exe to .zip, but lo and behold, no .inf file.

3 EXEs 1 BIN 3 CAB 2 INI 1 HDR 1 IBT 1 INX 1 ISS 1 REG 2 TXT

I'm not sure if I should rename one of the files or what. It says to install, I should use the EXE. Would the INF be in one of the CAB files?

I checked one of my CAB files, with no luck. A Bunch of files, but no INFs, my other CAB files had absolutely nothing in them.

---

### Post by Rockman4140 on 2007-08-27
Is there some way to detect the INF file that Vista uses from the current drivers? I know ou can find the SYS file, but is there a way to link that to the INF file?

---

### Post by blahquaker on 2007-08-27
> **Rockman4140 said:**
> I myself am looking to get wireless access on my laptop. It is a Toshiba Satellite A215-S4817, so I'm thinking the drivers you found may help. By chance would it be possible to post a link or give me tips? The bmartin method didn't quite work.

I'm still a Linux n00blet, and I was figuring if/when I get my wireless up and running, I could tinker with it more to work on my mouse settings and getting my card to work.

sorry I hadn't checked the site in a couple of days. I got the drivers from [atheros.cz]("http://www.atheros.cz/"). if I remember right, the one that "worked" was the xp64 one. I installed x86_64 linux; if you installed 32-bit linux, you'd need a different one. I don't think the vista ones will work.

NOTE: after installing this, the system would no longer boot (grub wouldn't load) with the wireless card turned on, so I would have to turn the wireless card off, then boot, then turn the wireless card back on. I haven't figured out the cause as of yet, but I have to assume the driver is conflicting with something.

---

### Post by MCMcButtah on 2007-10-18
Just a heads up that wireless works out of the box with no modifications for my toshiba U305 with the new gutsy kubuntu release. I am using WPA. The only caveat is the connection will not auto re-connect if I hide the SSID. Not that big of a deal for me though.

How if I can just get suspend/resume to work and get my toshiba to stop making that really annoying fan sound I would be set. Any of you other u305 owners annoyed with your CPU fan? My fan spins up to 100% for 2 seconds every time the cpu spikes to 100%, whether or not it is actually hot.

---

### Post by MrFSL on 2007-12-02
> **Rockman4140 said:**
> I downloaded it and found out that it is a self-extracting zip. I changed the .exe to .zip, but lo and behold, no .inf file.

3 EXEs 1 BIN 3 CAB 2 INI 1 HDR 1 IBT 1 INX 1 ISS 1 REG 2 TXT

I'm not sure if I should rename one of the files or what. It says to install, I should use the EXE. Would the INF be in one of the CAB files?

I checked one of my CAB files, with no luck. A Bunch of files, but no INFs, my other CAB files had absolutely nothing in them.

If you are downloading drivers from the Toshiba site - and you want to extract them and get the ndis drivers do the following:

1) download the driver (example driver.exe)

2) Unzip it:
```
unzip driver.exe
```

3) Install unshield
```
sudo apt-get install unshield
```

4) Extract the InstallShield cab file:
```
mkdir CAB
unshield -d ./CAB x data1.cab
```

5) Open the folder, pick your language and enjoy

****NOTE** - I am in NO WAY guaranteeing that these drivers will work for you! --- but this is how you would extract them.**

Cheers!

---

### Post by formol on 2007-12-12
hello,

ive this wireless card too, on a toshiba a200-ah1

i got this:

root@ubuntu:/etc/ndiswrapper# ndiswrapper -l
ar5211.sys : invalid driver!
net5211 : driver installed
device (168C:001C) present (alternate driver: ath_pci)
net5211.inf : invalid driver!

can someone help me, thx

---

### Post by Donskov on 2007-12-12
The problem I had was that Ubuntu did not actually disable the Ath_HAL module.



Here are some links that helped me get my ar5007eg up and running.

[The divers work. The instructions were missing the removal of ath_hal. Everything should work after you use the code from below.]("http://docs.google.com/View?docid=dtvgpkz_46fv8dwf")


You will also want to disable ath_hal in your restricted drivers and dont forget to remove the module for ath_pci and ath_hal with.


should look something like DISABLED_MODULES="ath_hal"
```
sudo nano -w /etc/default/linux-restricted-modules-common
```


```

sudo modprobe -r ath_pci
```

__________________

---

### Post by MrFSL on 2007-12-12
I can now confirm that the drivers extracted from the Toshiba executable do not work.

---

### Post by formol on 2007-12-12
hello

(thx to Donskov for replying)

now i get

ar5211.sys : invalid driver!
net5211 : driver installed
        device (168C:001C) present
net5211.inf : invalid driver!


for removing the athi_pci module, i get:

root@formol-laptop:/etc/ndiswrapper# modprobe -r ath_pci
FATAL: Module ath_pci not found.

---

### Post by hoboghost on 2007-12-14
> **ntlam said:**
> Never mind. I got it work.

Step 1:
Because I tried Madwifi before so I had to remove it:
Code:
cd /lib/modules/$(uname -r)
sudo rm -rf net
sudo rm -rf madwifi
sudo rm -rf madwifi-ng

Then:
cd /to your directory of madwifi-version, do the following:
sudo make clean (you can do this step again and again to make sure madwifi is removed completely)

Code: (Check for the existence of any wlan, ath_hal, ath_pci modules)
lsmod

Remove  existing loaded modules:
sudo rmmod (moduleName)

reboot

Step 2: (you might not have to do this step if you haven't installed ndiswrapper)

remove the installed ndiswrapper by doing:

cd /directory of ndiswrapper-1.47/

sudo rmmod ndiswrapper
sudo make distclean
sudo make -C driver clean

Go to Places-->seach for files, seach ndiswrapper, you will see a list of ndiswrapper files and folders. In the command line go to each location to delete ndiswrapper either with sudo rm (for files) or sudo rm -r (for folders).

Step 3:

Then go back to directory of ndiswrapper-1.47/
sudo make
sudo make install

Step 4:

And finally install the driver:

cd /directory of XP driver/

sudo ndiswrapper -i net5211.inf (your file would be different, something like file.inf)
ndiswrapper -l ==> if u see this message: "net5211: driver installed device (168C:001C (not same with ur )

sudo modprobe ndiswrapper

dmesg (show that the card installed)
iwlist wlan0 scan (will show all APs arround you)

sudo ndiswrapper -m

sudo reboot

And the wireless should work.

I followed these instructions and it seemed to work at first.  iwlist wlan0 scan did show me APs.  But after reboot, and reloading the ndiswrapper mod which wasn't starting up, iwlist wlan0scan gives me nothing "No scan results."  When I go to system settings -> network settings, it shows an enabled eth0, which is the onboardlan, and a disabled wireless device wlan0.  When I click on admin mode to try to enable the wlan0, those two items dissapear.  Can anyone help me enable wlan0?  I feel like im really close to getting this to work :)

---

### Post by formol on 2007-12-16
thx for the answer.  next wednesday is my last exam for this session, i wil format my laptop wednesday night (he is new anyway).  i want to be sure that all the trace of madwifi will disapear, but anyway,  i will post the result here for sure.  thank again.

---

### Post by ntlam on 2007-12-21
> **hoboghost said:**
> I followed these instructions and it seemed to work at first.  iwlist wlan0 scan did show me APs.  But after reboot, and reloading the ndiswrapper mod which wasn't starting up, iwlist wlan0scan gives me nothing "No scan results."  When I go to system settings -> network settings, it shows an enabled eth0, which is the onboardlan, and a disabled wireless device wlan0.  When I click on admin mode to try to enable the wlan0, those two items dissapear.  Can anyone help me enable wlan0?  I feel like im really close to getting this to work :)

It seemed the ndiswrapper drive was not loaded. You might get the wireless work by doing:
sudo modprobe ndiswrapper 

but I'm not sure it would load the ndiswrapper permanently or not.

---

### Post by ntlam on 2007-12-21
> **ntlam said:**
> It seemed the ndiswrapper drive was not loaded. You might get the wireless work by doing:
sudo modprobe ndiswrapper 

but I'm not sure it would load the ndiswrapper permanently or not.

There's a solution you guys might want to try:
[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_fireboard/Itemid,34/func,view/id,876/catid,2/limit,6/limitstart,6/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_fireboard/Itemid,34/func,view/id,876/catid,2/limit,6/limitstart,6/)

All you have to do is:
- installing ndiswrapper then net*.* (XP driver)
- sudo modprobe ndiswrapper
- sudo ifconfig wlan0 down
- sudo ifconfig wlan0 hw ether xxxxxx (xxxxxxxxxxxx is your wireless mac address)
- sudo nano /usr/local/bin/ndis.sh
added folowing:

#!/bin/bash

`/sbin/ifconfig wlan0 down`
`/sbin/ifconfig wlan0 hw ether xxxxxxxxxxxx`


where xxxxxxxxxxxx the reall mac address of wifi card

sudo nano /etc/rc.local
added "/usr/local/bin/ndis.sh" before "exit 0"

sudo nano /etc/modules
added "ndiswrapper" after all

reboot

---

### Post by ntlam on 2007-12-22
After installing ndiswrapper and XP driver, do the following commands

sudo modprobe ndiswrapper
sudo ndiswrapper -m
echo "ndiswrapper" | sudo tee -a /etc/modules

Hope it helps.

---

### Post by formol on 2007-12-22
i think my wifi driver are okay, i make it work with that:

> **bmartin said:**
> [COLOR="Red"]Make sure you use the appropriate version of the drivers for your version of Linux. If you're using a 64-bit version of Linux, you **must** use 64-bit drivers. You can check this using the following command:
```
getconf LONG_BIT
```

I personally recommend using the [wicd]("http://blakecmartin.googlepages.com/wicd.html") program for WiFi connectivity. It boasts built-in WPA support and has been successful where other network connection manager programs have failed.
[/COLOR]

This chipset showed up on my Acer Aspire 5050-3785. The lspci program spit out the following info:
```
Atheros Unknown device 001c (rev 01)
```
It also has been incorrectly labeled as an AR5006X device, in some cases.

Here is a step by step procedure to install the drivers manually (in case you don't want to use the script I wrote, or if it doesn't work properly). Open a terminal and copy/paste the following lines:

1a. Download the ndiswrapper (v1.48) source code and AR5007EG Windows drivers:
```
wget http://wifix.sourceforge.net/software.php?title=ndiswrapper
```
1b. Download the AR5007EG Windows XP drivers:
If you're using a 32-bit version of Linux, use this command:
```
wget http://blakecmartin.googlepages.com/ar5007eg-32-0.2.tar.gz
```
For 64-bits of blazing WiFi glory, use this:
```
wget http://blakecmartin.googlepages.com/ar5007eg-64-0.2.tar.gz
```
2. Extract the archives:
```
tar xvf ar5007eg-*.tar.gz
tar xvf ndiswrapper-newest.tar.gz
```
3. Ensure you have your kernel headers and the build essential package.
```
sudo aptitude update && sudo aptitude install linux-headers-$(uname -r) build-essential
```
4. Blacklist the ath_pci kernel module (it doesn't support our chipset).
```
echo "blacklist ath_pci" | sudo tee -a /etc/modprobe.d/blacklist
```
5. Compile ndiswrapper:
```
pushd ndiswrapper-*/
sudo make uninstall
make
sudo make install
popd
```
6. Install the Windows drivers (using ndiswrapper):
```
pushd */ar5007eg/
sudo ndiswrapper -i net5211.inf
popd
```
7. Make sure ndiswrapper loads up every time we start Linux:
```
sudo modprobe ndiswrapper
echo "ndiswrapper" | sudo tee -a /etc/modules
```
8. Restart your computer.
```
sudo init 6
```

=====
FAQ
=====
Q: Linux seems to see my device now, but it can't see any networks. What can I do now?
A: This frequently happens on built-in devices. There's usually either
[LIST]
[*]A switch on your computer somewhere that toggles whether the wireless radio is on or off (BEWARE! Some of these are very unintuitive. The setting that may seem like "on" may be "on" and vice-versa.)
[*]A keyboard combination that enables/disables the wireless connection (usually Fn+F2).
[*]A setting in the BIOS that needs to be changed. This can be frustrating to track down. The BIOS is the program that loads before your OS. When your computer first boots, there's a key you can press to go into the system setup; look for a wireless setting in there that you can enable.
[/LIST]

Q: I can see wireless networks. Why can't connect to any of them?
A: There are a couple options to try here. If you're using WICD to connect and WPA encryption, under preferences, make sure that for WPA Supplicant Driver, you're using WEXT (make sure you've installed WPA_Supplicant). If you're using WEP, try putting your key in "double quotes". If you can't connect to an encrypted network, try removing they key to see if that's the problem. If you're not using WICD, try it out; many people have been successful simply after switching the wireless connection manager program to WICD.

Q: None of this worked. I'm no closer to having my wireless working than I was when I first installed my OS. What's wrong?
A: Try running **sudo modprobe ndiswrapper**; the program should run silently. If you get any output, there's a problem. If the ndiswrapper,ko file can't be found, run **sudo depmod -ae**, then try **sudo modprobe ndiswrapper** again.

If you installed your OS a long time ago, some people have had better success with a fresh install. Try installing the drivers while running from the Live CD.
=====
EDIT: I removed the instructions for using the script. It seemed to not work for anyone other than me. I checked it over several times and couldn't figure out why. The instructions and the script seem to perform the same set of operations.

---

### Post by peterleder on 2008-03-31
hello ,
i was able to install the madwifi tools which i downloaded from the madwifis site
through the commands in SIDUX. This isnt an ad. I'd like to use ubuntu (gOS) but i cant get wifi working :-\

this is how i did it in sidux
opened terminal

sudo su
# go to the unzipped dir
cd /~/madwifi....
make
make install

and thats it. had to use network-manager and network-manager-kde though.

---

### Post by Darkendes on 2008-05-08
> **ntlam said:**
> There's a solution you guys might want to try:
[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_fireboard/Itemid,34/func,view/id,876/catid,2/limit,6/limitstart,6/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_fireboard/Itemid,34/func,view/id,876/catid,2/limit,6/limitstart,6/)

All you have to do is:
- installing ndiswrapper then net*.* (XP driver)
- sudo modprobe ndiswrapper
- sudo ifconfig wlan0 down
- sudo ifconfig wlan0 hw ether xxxxxx (xxxxxxxxxxxx is your wireless mac address)
- sudo nano /usr/local/bin/ndis.sh
added folowing:

#!/bin/bash

`/sbin/ifconfig wlan0 down`
`/sbin/ifconfig wlan0 hw ether xxxxxxxxxxxx`


where xxxxxxxxxxxx the reall mac address of wifi card

sudo nano /etc/rc.local
added "/usr/local/bin/ndis.sh" before "exit 0"

sudo nano /etc/modules
added "ndiswrapper" after all

reboot

You, sir, are my personal hero. I have a Toshiba A215-S5837 (damned AR5007EG's!) and I couldn't get ANYTHING to work until I tried your delete-madwifi-and-reinstall-ndiswrapper method combined with the above script. After I tried your method, I was able to see access points, but not connect to them. Thanks to the ifconfig trick, everything is working fine and I'm posting this from my wireless adapter.

Thank you! Now I can work on regrowing all the hair I pulled out over this. :)

---

