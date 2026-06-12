---
title: "asus 1215n bluetooth not working on 10.10"
date: 2011-02-13
forum: Hardware
---

### Post by buchta on 2011-02-13
hi all,
I have asus 1215n with ubuntu 10.10 (32 bit) and cannot get the bluetooth working 
-gnome-bluetooth is installed, saying there's no adapter
-blueman is installed, saying bluez daemon's not running so it cannot work
-bluez is installed, but apparently doesn't work(?)
there's no BT icon anywhere in panels
I'd really appreciate any help as I'm complete linux noob, but I totally wanna keep it :)

UPDATE: ok, so after long hours of googling I found out it's probably caused byt the proprietary STA driver for the Broadcom 4313 chipset (02:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g LP-PHY (rev 01)). the driver enables wi-fi, but disables bluetooth. I have no idea how to fix it :/
I've read some threads about fixing the wi-fi issue with this adapter by switching to b43 fwcutter etc ([http://wireless.kernel.org/en/users/Drivers/b43#Supported_chip_types](http://wireless.kernel.org/en/users/Drivers/b43#Supported_chip_types)), but no one mentioned bluetooth

any ideas or experiences with this?

---

### Post by buchta on 2011-02-15
hi,
I have asus 1215n with Broadcom BCM4313 802.11b/g LP-PHY
It should have 802.11n wifi, but this doesn't work
It also should have Bluetooth, but this doesn't work either
I have Broadcom STA wireless driver (These package contains Broadcom 802.11 Linux STA wireless driver for use with Broadcom's BCM4311-, BCM4312-, BCM4321-, andBCM4322-based hardware.) -802.11b/g works with this
System>Preferences>Bluetooth says I have no adapters connected
System>Preferences>Bluetooth Manager (blueman) says it cannot continue cos there's no bluez-daemon running, so it won't start
I found this: [http://wiki.debian.org/brcm80211](http://wiki.debian.org/brcm80211) but have no idea what to do with it and if it will help

Anyone has same experience and knows how to solve it?
could anyone please please PLEASE help me? I'm complete noob and I'm quiet lost right now...

---

### Post by amsterdamharu on 2011-02-15
First of all, please stop posting the same question. If you can't get a reply after a day or so you can post a reply to your own thread with the text bump.

As for your current problem; could you post the output of the following commands:

```
sudo lspci -v
```
only the part of your bluetooth/wireless adapter.

```
rfkill list
```

To execute the command(s) you can press alt + F2, type gnome-terminal and click run. Then copy one command and paste it in the terminal (black screen that showed up after you clicked run). Use the mouse to paste commands in the terminal.
Then you can select all the text in the terminal, right click and select copy. When pasting it here please wrap it in code tags: &#91;code][COLOR=Red]Your pasted stuff[/COLOR]&#91;/code]

---

### Post by buchta on 2011-02-15
sorry about the double-post :/

```
 02:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g LP-PHY (rev 01)
	Subsystem: Device 1a3b:2047
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at f9ffc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [40] Power Management version 3
	Capabilities: [58] Vendor Specific Information: Len=78 <?>
	Capabilities: [48] MSI: Enable- Count=1/1 Maskable- 64bit+
	Capabilities: [d0] Express Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [13c] Virtual Channel
	Capabilities: [160] Device Serial Number 00-00-60-ff-ff-54-48-5d
	Capabilities: [16c] Power Budgeting <?>
	Kernel driver in use: wl
	Kernel modules: wl

```

```
The program 'rfkill' can be found in the following packages:
 * wireless-tools
 * rfkill
Try: sudo apt-get install <selected package>

```

---

### Post by amsterdamharu on 2011-02-15
Strange, I thought rfkill was installed by default. Could you install it and run the command again?

```
sudo apt-get install rfkill
rfkill list
```

---

### Post by buchta on 2011-02-15
I installed rfkill, but when I write the "rfkill list" command nothing happens, it just gives me another line

---

### Post by amsterdamharu on 2011-02-16
rfkill should show the status of wireless devices, some can be turned off by key combinations or by software. It should at least show your wifi status if it's turned off by software or hardware (key combinations).

Maybe re installing the drivers will work.
Could you try the following commands?
```
sudo apt-get remove firmware-b43*
sudo rmmod -v wl
```
Copy and paste the output to a text file if there are any errors. Now reboot your system, if it detects new hardware ignore it for now and open a terminal to type the following text:
```
sudo jockey-text 
```Could you post the output of that here? There might be several choises you need the driver LP-PHY or something like that.
If there is nothing could you post the output of:
```
lsmod | grep wl
```

---

### Post by buchta on 2011-02-16
so... I didn't ahave the b43 driver, so the output of the first 2 is: 
```
sudo apt-get remove firmware-b43* 
[sudo] password: 
Reading package lists... Done 
Building dependency tree        
Reading state information... Done 
Note, selecting 'firmware-b43-installer' for regex 'firmware-b43*' 
Note, selecting 'firmware-b43-lpphy-installer' for regex 'firmware-b43*' 
Note, selecting 'firmware-b43legacy-installer' for regex 'firmware-b43*' 
Package firmware-b43-installer is not installed, so not removed 
Package firmware-b43-lpphy-installer is not installed, so not removed 
Package firmware-b43legacy-installer is not installed, so not removed 
0 upgraded, 0 newly installed, 0 to remove and 458 not upgraded. 
:~$ sudo rmmod -v wl 
rmmod wl, wait=no 
``` 

anyway, I removed the Broadcom STA driver in jockey-gtk and rebooted 
it didn't detect any new hardware or at least didn't notify me about it 

next output is like this: 
```
sudo jockey-text 

Searching for available drivers... 
:~$ lsmod / grep wl 
Usage: lsmod 
```

I'm not a pro, but it seems like something's wrong...

---

### Post by buchta on 2011-02-16
I forgot to add that the only additional drivers in jockey-gtk are the Broadcom STA & nVidia driver (both disabled)

---

### Post by amsterdamharu on 2011-02-16
You can copy and paste the commands, that will prevent the typo's you made.

/ is not the same as | see /|?

I assum jocky-text and lsmod | grep wl gave no output.

Now you can re install the firmware, can you post the output of this command?

```
sudo apt-get install firmware-b43-lpphy-installer
```

Now you have the right one installed, maybe need a reboot to see what's what.

Then try rfkill  list again to see if any wifi or bluetooth shows up.

---

### Post by buchta on 2011-02-16
yeah, I tried the command with both / and | and your assumption is correct.
I tried to install the lpphy firmware but it gave me error claiming there's no compatible HW for it so it will not be installed and I have to choose either b43 or b43-legacy (I'm at work now so I can't give you full version/screenshot)
also, the wired connection started to drop after couple of minutes and needed complete reboot to connect and then dropped again.
I think I will go for fresh install later in the evening and see what happens...

edit: i wasn't allowed to install the b43 either

---

### Post by amsterdamharu on 2011-02-16
If you can find windows xp drivers for it you could try ndiswrapper:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
but your model isn't listed
[http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Category:PCI](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Category:PCI)

Maybe get the latest drivers from broadcom?
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

The readme says it has only just now support for rfkill with kernel 2.6.31 to 2.6.36
[http://www.broadcom.com/docs/linux_sta/README.txt](http://www.broadcom.com/docs/linux_sta/README.txt)

---

### Post by amsterdamharu on 2011-02-17
I just stumbled across this thread:
[http://ubuntuforums.org/showthread.php?t=1604868](http://ubuntuforums.org/showthread.php?t=1604868)

The solution to install the ppy driver is:
> **Solution**: System > Administration > Synaptic Package  Manager > Search: firmware-b43-lpphy-installer > Click Mark >  Click install > CloseI know why it fails with a message:

---

### Post by buchta on 2011-02-17
so, I re-installed the system cos I kinda messed it up. 
then I installed the broadcom driver from here:
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)
 using the instructions from read me (my first .tar.gz installation -yeeeey! :cool:)

it works fine for wifi, but still no BT
I ran the command you gave me before:
```
rfkill list
0: brcmwl-0: Wireless LAN
 Soft blocked: no
 Hard blocked: no

```
and 
```
sudo jockey-text

Searching for available drivers...
:~$ lsmod | grep wl
wl 2637607 0 
lib80211 5058 2 lib80211_crypt_tkip,wl
 
```

the new thing I discovered while I was forced to go to win7 is there are several drivers:
Broadcom Wireless Network Adapter, Publisher: AzureWave, Product version: 1.00.0000
Ralink RT2860 Wireless LAN Card, Publisher: Ralink, Product version: 1.2.0.1
WIDCOMM Bluetooth Software, Publisher: Broadcom Corp., Product version: 6.3.0.5500

I think this might mean I need separate driver for bluetooth. Or maybe not.
I haven't tried the b43 lpphy yet

---

### Post by amsterdamharu on 2011-02-17
jocky-text doesn't report anything because a driver has already been installed.

The llphy firmware might not install because you have different hardware, it is firmware and only works on certain hardware. The installer checks the following:
```
lspci -n | grep -o "14e4:[1234567890]\+"
```
The output should be something.

None of these drivers seem to mention bluetooth though.

---

### Post by buchta on 2011-02-17
it' solved... I feel kinda stupid right now, but this really dind't come to my mind...

I found this notice 
*IMPORTANT* If dual-booting Windows and Ubuntu, be sure to enable the card (wireless light is on) in Windows before booting Ubuntu, otherwise it will not work.
in here [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBroadcom](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBroadcom)
so I booted into win & checked if both wifi & bt are enabled -they have the same light & button and it was on all the time, but apparently, the BT part was disabled anyway...

so the conclusion:
if you dual-boot Win & Ubuntu and have combined wireless card with integrated BT, always check both components are enabled in Win, not only wifi

---

### Post by amsterdamharu on 2011-02-18
Well done, I didn't think of that. Could you tell me what driver and firmware you installed?
And does rfkill list show any bluetooth stuff? 
On the broadcom site I see that the newest drivers/firmware support rfkill so the one in Ubuntu repository might not support it yet.
With rfkill you could switch it on and off as well (only soft mode because hard mode is done with a key combination).

To see what packages are installed you can try the following command:
```
dpkg-query -W --showformat='${Installed-Size} ${Package}\n' | grep b43
```

It looks like everything worked "out of the box" you didn't need to manually install anything but have to switch on the card when leaving Windows.

---

### Post by buchta on 2011-02-18
here'st the rfkill output:
```

~$ rfkill list
1: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
:~$ rfkill block 2
:~$ rfkill list
1: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: hci0: Bluetooth
	Soft blocked: yes
	Hard blocked: no

```

as you can see, I can turn it off using rfkill :)

I used the package from Broadcom site: [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php) , but I think the restricted driver suggested by Additional Drivers (jockey-gtk) will work as well as it seems to be the same one - Broadcom 802.11 Linux STA wireless driver

as it's not the b43 driver, I altered it with "wl" (not sure if that's what you asked for):
```

~$ dpkg-query -W --showformat='${Installed-Size} ${Package}\n' | grep wl
64 bcmwl-modaliases

```

and yes, it seems it worked "out-of-the-box" and if anything needed to be installed, it's just the Broadcom STA driver which can be found in Ubuntu Software Center

well, the joys of dual-booting I guess :)

---

### Post by amsterdamharu on 2011-02-18
Thank you for giving that info, if someone stumbles on this thread they might find this useful.

Sorry I couldn't be of any help here but it's working now anyway. Great job to you.

---

### Post by carlos_debian on 2011-04-27
Hello everybody,

I have a similar problem... WiFi is working, but I can't get BT to work. 

> buchta: so the conclusion:
if you dual-boot Win & Ubuntu and have combined wireless card with integrated BT, always check both components are enabled in Win, not only wifiWell... I wiped windows 7 that comes factory installed (Lenovo G460, has a BCM4313) without enabling BT, so I think I won't be able to go back to windows to enable it....

Anybody knows if there is a way to enable BT without going back to windows?

Thanks!

---

### Post by srimanta on 2011-10-07
I too was facing the same problem...
if you still have the problem try upgrading to 11.04...

---

### Post by buchta on 2011-10-07
actually, I did finally upgrade to natty AND I installed it over the Win partition and everything, so the machine's MS free :D

---

