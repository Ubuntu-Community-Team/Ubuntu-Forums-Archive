---
title: "Activating MadWifi / blacklisting ath5k Acer Aspire One/9.04"
date: 2009-04-29
forum: Hardware
---

### Post by DoxSearch on 2009-04-29
I am having unreliable results with using ath5k, slow speeds dropped connections etc. Previously I was using madwifi (before installing 9.04) without any issues.

I tried adding

'blacklist ath5k" to /etc/modprobe.d/blacklist.conf

and activating the madwifi drivers, but now i get this in dmesg

[    9.321139] ath_pci: 0.9.4
[    9.326045] ath_pci 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    9.326079] ath_pci 0000:03:00.0: setting latency timer to 64
[    9.374793] wifi%d: unable to attach hardware: 'Hardware revision not supported' (HAL status 13)
[    9.374836] ath_pci 0000:03:00.0: PCI INT A disabled



I would really like to get this working, I need to transfer some files so I can upgrade my desktop to 9.04 (fresh install).

---

### Post by danflash on 2009-04-29
I'm unsure myself, but...
I'm on the Acer Aspire One now, and I haven't uninstalled Linpus, but I am running Ubuntu 9.04 (Desktop) as a Live USB right now as I write this.  
The wireless works out of the box without any issues, and everything else (desktop effects, compiz, etc etc) seems to be fine.  
Have you tried booting into a Live session? 
If we were to do fresh installs, is the wifi (and other stuff) likely to stop working?

Hope that's helped you out in some way maybe

---

### Post by DoxSearch on 2009-04-29
Dan,

It works but just not as well as the madwifi drivers did under backtrack 4 (which is ubuntu/debian based) for me. Even injection etc work.

My issue is it drops and reconnects when downloading large files, and the speed isnt as fast as it was with the madwifi drivers. It doesn't even tell me it drops, but stops the download. I know it drops/reconnects because when I load up airodump on another notebook I can see a WPA handshake from the acer right after the download stops.

I am doing a fresh install today for another reason, but I would like to get madwifi working.

---

### Post by DoctorAwesome on 2009-04-30
I have this same problem and would be interested in a resolution.  Ath5k seems a lot more stable than it was in Intrepid, but madwifi is miles ahead of it and I would like to install madwifi again without having to manually build it, if possible.

---

### Post by dandnsmith on 2009-04-30
Earlier today I used 9.04 wirelessly with an AA1.
It may be that the packaging was important - I was running the UNR 9.04 from a USB stick, and it connected with less trouble than I had been having using 8.10 standard - which I had to modify to use the W* drivers with ndiswrapper to get the connection to work.

---

### Post by DoxSearch on 2009-04-30
I never tried 8.10 on the aspire.

I also noticed problems transfering large files over SSH on my local network using ath5k. The sshD is is a 8.10 box hardwired on the network. No issues transferring if i use eth0 on the acer, or boot into backtrack and use madwifi. I would really like to get madwifi working on this thing, I don't know why it doesn't work.

---

### Post by waj1122 on 2009-04-30
Has anyone found a solution to this yet? I would really like to use madwifi (it just seems to be more consistent), ath5k_pci is all over the place in speed and connectivity. When I click to activate it and reboot I lose wireless. Do I need to recompile it from source?  I've searched for a solution but so far haven't found one.

---

### Post by ebcovert3 on 2009-04-30
I too am having this problem. I just unpacked my AA1 this evening at the office. It found wireless networks (but did not connect). I threw it into hibernate mode and drove home. When I woke it up, it see no wireless networks. As I write this, I am sitting next to my access point using a wireless connection. In case you were curious, the rest of the computers in the house work fine with the wireless.

---

### Post by josarn on 2009-05-01
I use Madwifi with Jaunty following the wiki (grab the snapshot driver, and "sudo make install")  but instead of editing config files to blacklist ath5k and enable ath_pci I had to enable the madwifi propietary driver through "Administration >>> Hardware Drivers" (I am translating the menu from spanish hope you get the idea).

The problem I have now is that after suspend all connections fail (time out)

---

### Post by incandenza on 2009-05-01
Same here: the 9.04 stock installed drivers didn't work, but I got them to work by building the trunk version (see [http://madwifi-project.org]("http://madwifi-project.org")).

Approximate steps were something like (although you might want to follow the Wiki instead):

```

sudo apt-get install subversion
svn co http://svn.madwifi-project.org/madwifi/trunk madwifi
cd madwifi/scripts
sudo ./find-madwifi-modules.sh -r
cd ..
make
sudo make install

```

Then switch the driver in Administration / Hardware Drivers and reboot.

As far as the not recovering from suspend problem, I usually just run:

```

sudo /etc/init.d/NetworkManager restart

```

after resuming from suspend.  Not pretty, but it does the trick.

---

### Post by asmoore82 on 2009-05-12
> **waj1122 said:**
> When I click to activate it and reboot I lose wireless.
I was in the same boat and found that I needed to activate madwifi and
then Shut Down and Power Off; then when I powered back up madwifi was activated.

---

### Post by dad311 on 2009-05-13
I noticed a slow connection (5meg) while using the ath5k wireless drivers with my AOA .  Also after performing the LED wireless fix (Load linux-backports-modules-jaunty) my wireless connection would start to drop out under large file transfers.

I tried the building and activating the MadWifi drivers.  The MadWifi drivers worked but didn't seem to be any better.

---

### Post by waj1122 on 2009-05-14
> **asmoore82 said:**
> I was in the same boat and found that I needed to activate madwifi and
then Shut Down and Power Off; then when I powered back up madwifi was activated.

I'd already tried that. I tried again, no luck. I guess I'm stuck with ath5k. 

Thanks,
Bill

---

### Post by Manzabar on 2009-05-15
> **waj1122 said:**
> I'd already tried that. I tried again, no luck. I guess I'm stuck with ath5k. 

Thanks,
Bill
Did you try adding ath_pci to your /etc/modules file? I don't have an Acer Aspire One but I do use an Atheros based wifi card in my computer. It wasn't until I edited /etc/modules that I could get the madwifi drivers to load on boot.

---

### Post by waj1122 on 2009-05-15
> **Manzabar said:**
> Did you try adding ath_pci to your /etc/modules file? I don't have an Acer Aspire One but I do use an Atheros based wifi card in my computer. It wasn't until I edited /etc/modules that I could get the madwifi drivers to load on boot.

Tried that with the same results (did a complete reboot).

---

### Post by trozombo on 2009-05-23
worked for me nicely...
thanks for the help...

---

### Post by lorenco on 2009-06-02
Just a note to check out 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/337311/comments/8](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/337311/comments/8)

There is an update available for the ath5k that was buggy and slow....

---

### Post by beefcurry on 2009-06-05
> **DoxSearch said:**
> I am having unreliable results with using ath5k, slow speeds dropped connections etc. Previously I was using madwifi (before installing 9.04) without any issues.

I tried adding

'blacklist ath5k" to /etc/modprobe.d/blacklist.conf

and activating the madwifi drivers, but now i get this in dmesg

[    9.321139] ath_pci: 0.9.4
[    9.326045] ath_pci 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    9.326079] ath_pci 0000:03:00.0: setting latency timer to 64
[    9.374793] wifi%d: unable to attach hardware: 'Hardware revision not supported' (HAL status 13)
[    9.374836] ath_pci 0000:03:00.0: PCI INT A disabled



I would really like to get this working, I need to transfer some files so I can upgrade my desktop to 9.04 (fresh install).

I get the same dmesg when I tried to enable madwifi drivers on my Acer Aspire One, I resorted to going back to ath5k, I have no issues with speed of ath5k mainly the fact it dosn't load sometimes on startup is quite inconvenient.

---

### Post by Sodafizz on 2009-06-06
I have installed Ubuntu Netbook Remix 9.04 onto an Acer Aspire One A110 (8GB SSD.) I have done all the Ubuntu updates. Everything (audio, video, webcam, mouse, etc.) is working. Wired internet is working fine, but I cannot get the wireless connection to work. (FWIW, the WLAN light is not working either.) I have tried turning the WLAN switch on/off, but nothing.  
   
  Hardware Drivers: Alternate Atheros ‘madwifi’ driver
   
  Rightmouse-clicking the network icon: “Enable Networking” is checked on. 
   
  When I go into the ‘Edit Connections’ of the netbook/ubuntu, “Connect Automatically” is checked on, as is “Available to All Users.” Also, in this mode: 
   
  ON THE NETBOOKS’S “WIRELESS” TAB: 
   
  SSID: (correct id name for my wifi)
  MODE: Infrastructure 
  BSSID: (blank)
  MAC address: (blank)
  MTU: automatic
   
  ON THE NETBOOK’S “WIRELESS SECURITY” TAB: 
   
  Security: WEP 40/128-bit key
  Key: (correct key for my wifi)
  WEP Index: 1
  Authentication: Open System
   
  ON THE NETBOOK’S “Ipv4 SETTINGS” TAB:
  Method: Automatic (DHCP
   
  MY LINKSYS WIFI SETTINGS: 
   
  Network Mode: Mixed
  Security Mode: WEP
  Encryption: 40/64-bit (10 hex digits)
  Wireless MAC Filter: disabled
  Standard Channel: 6
   
   
  Is anything obvious jumping out to any knowledgeable persons out there? (I am a Linux newbie.)
   
  Dave

---

### Post by Sodafizz on 2009-06-07
I ended up re-installing 9.04, this time without doing the automatic updates. The wifi is working fine...

---

### Post by Hilko on 2009-06-18
Here is how i got my atheros card working in a lenovo thinkpad. It didn't work out of the box. I copied it from this thread: [_[COLOR="DarkRed"]http://ubuntuforums.org/showthread.php?t=865971[/COLOR]_]("http://ubuntuforums.org/showthread.php?t=865971")
Hope it's helpful.

> AR242x
Here are instructions; they require an active internet connection, so walk your computer over to the router and hook up the ethernet. Open a terminal and do these commands, each in order and in turn.
Code:

sudo apt-get install build-essential linux-headers-generic
wget [http://snapshots.madwifi.org/madwifi-hal-0.10.5.6-current.tar.gz](http://snapshots.madwifi.org/madwifi-hal-0.10.5.6-current.tar.gz)
tar zxvf madwifi-hal-0.10.5.6-current.tar.gz
cd madwifi-hal-0.10.5.6-r3835-20080801/

The file name will change as the current build changes. Just watch what the file is that is extracted.
Code:

make
sudo make install
sudo modprobe ath_pci
sudo reboot

Your wireless should now be alive. Post back if you need help
Please note that when an update brings a new kernel, you will need to build this module for the new one. You will need to do:
Code:

cd madwifi-hal-0.10.5.6-r3835-20080801/  (change the filename here)
make clean
make
sudo make install
sudo modprobe ath_pci


And for resuming after suspend I tried this:
> I just upgraded to 8.10 on my Compaq Presario F700. 8.04 worked flawlessly for me. I had the same problem after the upgrade with my wireless network becoming useless after resuming from suspend.

This fixed it for me:

Open a terminal window

type: sudo gedit

then type your password

then insert this single line: SUSPEND_MODULES=ath_pci

then hit SAVE. Name the file madwifi and save it to /etc/pm/config.d

Then try suspending, resuming and see if your problem isn't fixed.

---

### Post by e_lm_70 on 2009-07-17
Hi,

 I'm new in Ubuntu. And also new with my Acer Aspire One FG5 / AOA150

 I did install Ubuntu Netbook remix ... everything at looks like to work fine but ... now for long.

 My Acer One is supposed to be up and running 24/7 connected to my WLAN at home as internal FTP server and WEB server ... but on the long run the WLAN is unstable.

 Normally after 10-15h of activity, it stop to work, and even not a reboot help.

 The only switch off the Acer One and restart, it will make WLAN to work again.

 I did upgrade the FW from 3305 to 3309, but did not help.

 I'm currently using the ath5k_pci driver that is the same that ubuntu install by default on the Acer One.

 I did try the madwifi, just a quick attempt but did not work for me.

 I also notice that the WLAN speed is always changing, every time that I ask for info is a different value, between 38 to 5Mbit, even 1Mbit sometime.

 At the moment my only solution is to connect my G730AP in the eth0, and disable the internal WLAN ... but it is not really the ideal solution.

 Anybody has same problem ? Anybody keep up the Acer One 24/7 (it consume so little power that make sense as home permanent server)

Danke

e_lm_70

---

