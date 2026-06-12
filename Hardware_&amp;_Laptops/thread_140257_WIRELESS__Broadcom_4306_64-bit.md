---
title: "WIRELESS  Broadcom 4306 64-bit"
date: 2006-03-05
forum: Hardware &amp; Laptops
---

### Post by teixeraf on 2006-03-05
HP Pavilion running AMD 64 with Ubuntu 64 too. I tryed to install BROADCOM 4306 (wireless driver) but it just doesn't work! I did that ndiswrapper (I'm pretty new on LINUX - I have just started on it). I found the drivers too for 64-bit and after do anything I got the message: 

Warning: Driver for device wlan0 recommend version 18 of Wireless Extension,
but has been compiled with version 17, therefore some driver features
may not be available...

I just can't find anything else that haven't done already, anyone could help me please????

---

### Post by saionjik on 2006-09-10
wow im also running a ubuntu 64, and im really mad that i've done what is said under [http://www.ubuntuforums.org/showthread.php?t=201902](http://www.ubuntuforums.org/showthread.php?t=201902)
When i do it with the 64bit drivers, i leave them alone w/o changing the names, and it seems to show hardware present and driver present, when i do "sudo ndiswrapper -l"

But everytime i follow the guild but do it with my drivers,
"
sudo rmmod bcm43xx
sudo gedit /etc/modprobe.d/blacklist
# i add "blacklist bcm43xx" to the bottom
# instead of  "sudo apt-get install ndiswrapper-utils" i put in the cd and install the ndiswrapper 1.8 from the cd on my 64 bit ubuntu

sudo ndiswrapper -i ~/folder where driver is/bcmwl5.inf
# i've noticed if i dont put my 64bit drivers close to my /home/ folder (for example "/home/(username)/PUT DRIVERS HERE") I get a line 135 error, so i put "sudo ndiswrapper -i /path to drivers/driver.inf" and terminal installs it while spitting out this code:
Forcing parameter IBSSGMODEL 0 to IBSSGMODEL 2
Forcing parameter IBSSGMODEL 0 to IBSSGMODEL 2
Forcing parameter IBSSGMODEL 0 to IBSSGMODEL 2
Forcing parameter IBSSGMODEL 0 to IBSSGMODEL 2
Forcing parameter IBSSGMODEL 0 to IBSSGMODEL 2
Forcing parameter IBSSGMODEL 0 to IBSSGMODEL 2
Forcing parameter IBSSGMODEL 0 to IBSSGMODEL 2

sudo ndiswrapper -l (tells me hardware and drivers present)
sudo ndiswrapper -m
sudo modprobe ndiswrapper

I then go to System -> Administration -> Networking and all i see is modem, eth0, eth1 and my OLD eth2 which was my wireless one with the option to input a ESSID name when i click configure disapears and im like WTF!?, so i then go through all these files and change eth2 to wlan0.

"add ndiswrapper to /etc/modules
change eth1 -> wlan0 in the files below:
sudo gedit /etc/modprobe.d/ndiswrapper
sudo gedit /etc/network/interfaces
sudo gedit /etc/iftab"

I dont have a passworded network so i dont do what else the tutorial says, and i've havent put # in front of the auto, Im just really mad cause i get stuck here and dont know what to do, 
to check my eth's i type "sudo iwconfig" and it pops up the eth's and wlan0 but now everything it says that no device detected or w/e it is that its not there as opposed to when i typed "sudo iwconfig" before the tutorial i followed and "eth2" showed the linksys broadcom 4603 (rev 3). So if anyone could help me thx.

I heard some ppl also used gnome network w/e but i dont know how to get that. everything i try to get offa the http archive of ubutnu instead of "apt-get" command for my 64BIT tells me that it doesnt support "lib6*YATTAYATTAYATTA*" or i386 when its not downloaded for the 64 bit. and if it does say its supported like the FWCUTTER for bcm43xx i press unpack/install and it says failed install, then i try the newer one and it says the unsupported lib6 thing.

---

### Post by brunom9 on 2006-10-14
Well, seems there's more of us having problems with ubuntu 64 and broadcom wireless chips.

Here's my experience.

Installed ubuntu amd64-k8 on a fakeraid setup. Not an easy task, not an impossible one. Configured the entire system (wide monitor, DELL 2007WFP, not all the resolutions recognized, which is a another task to configure). Got wired network, boot sequence right, etc.

Extracted the firmware from wl_apsta.o (prefer the native linux approach rather than going the windows XP driver with ndiswrapper), went ok. Launched the network-manager applet, BUM! system hangs! Rebooted, system hanged after logon.

Went into recovery mode, uninstalled bcm43xx-fwcutter and the firmware, system back online. Tried the install again, same thing. System hangs on the network-manager. Once again, recovered the system and tried to install the card, but now extractin the firmware using bcm43xx-fwcutter on the broadcom 64-bit driver. System hanged again on the network-manager.

Did the recovery, then tried something else: boot uo the liveCD. Installed bcm43xx-fwcutter on the system running from the liveCD (ver amd64 6.06), extracted the firmware from wl_apsta.o, fine. Went into System->Administration->Network, found my card listed, went into properties, gave my ESSID, ok. Turned on the card, system hangs!

Then did the same sequence, trying this time with the ndiswrapper approach using the Broadcom 64-bit drivers. Installed ok, blacklisted, card is online and harware detected. However, cannot scan for any network, card doesn't even get listed on System->Administration->Network. Installed the network-manager, no luck, no wireless support.

Went back to the installation board, fakeraid install of 32-bit ubuntu, went ok. Got to the wireless connection, once again with the linux drivers and bcm43xx-fwcutter. Works great! 

From this experience:

1) There are problems with ubuntu 64-bit and the broadcom driver.
2) The problem arises as the card is being detected or connecting to the network (network-manager hangs, system hangs on activating).
3) Broadcom 64-bit driver has no support for the card.

FYI, the card I'm installing is a Belkin F5D7001, reported form lspci as:

Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

Hope next release has fakeraid support and Belkin or Broadcom finally gives users a 64-bit driver.

Cheers from Mexico another open-source lover,

Bruno

---

